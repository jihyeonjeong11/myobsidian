---
tags:
  - type/sketchnote
  - type/note
  - theme/websocket
  - theme/cloudflare
aliases: 
lead: 클라우드플레어로 공짜로 웹소켓 구조를 구현해 본다. [Stock dashboard](https://stock-dashboard-swart.vercel.app/) 앞으로 채팅, 실시간 협업 및 게임과 같은 앱에서 활용할 수 있을 것이다.
visual: "![[websocket.jpg]]"
created: 2025-04-20, 16:50
modified: 2025-04-20, 16:50
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-19T11:49
---

[[드래프트)Cloudflare worker - Hibernation Websocket]]

```dataviewjs
dv.paragraph(dv.current().visual);
```

A photo by [Sherwin Ker](https://unsplash.com/@sherwinker) from [Unsplash](https://unsplash.com/)

> [!Summary] > `= this.lead`

## Websocket으로 무언가를 만들어 보고 싶다.

웹 개발자에게 있어 '실시간' 개념 구현은 언제나 설레는 일이다.

예전에 WebRTC 클라이언트를 구현하며 데이터스트림을 핸들링하고 에러 케이스를 잡으면서도 아주 흥미로웠다. 따라서 예전에 한 번 시도했지만 성공하지 못했던 웹소켓 구조를 한 번 다시 만들어보려고 했다. 간단히 주식 정보를 실시간 대쉬보드 앱을 통해서 구현해 보기로 한다.

예전에는 Vercel에 Nextjs 앱을 디플로에하고 하나의 서버에서웹소켓 서버까지를 처리하려고 했지만 
1. 서빙하는 메인서버와 웹소켓 서버는 따로 존재한다.
2. Vercel의 디플로이 공간인 [Vercel functions](https://vercel.com/docs/functions)에서는 스테이트가 필요한 웹소켓을 지원하지 않는다. 추가적인 데이터 스토리지와의 연동 구현이 필요하다.

따라서 Nextjs에는 앱을 올리게 된다면 웹소켓 자체는 다른 공간에 존재해야 할 필요가 있겠다. 

## Cloudflare에서는 가능하다고 하던데..

- Cloudflare의 서버리스 플랫폼인 Worker는 **Nextjs의 Function과는 다르게 웹소켓을 자체적으로 지원**한다고 해서 한번 확인해 보기로 한다.

> [Wokrer docs에 따르면]
> WebSockets utilize an event-based system for receiving and sending messages, much like the Workers runtime model of responding to events.
> 
> 워커의 런타임은 웹 스탠더드에 맞는 이벤트 방식을 사용하고 있으므로 같은 방식인 웹소켓과 사용이 가능하다.
> 

```javascript
async function handleRequest(request) {

const webSocketPair = new WebSocketPair();

const [client, server] = Object.values(webSocketPair);

server.accept();

server.addEventListener('message', event => {

console.log(event.data);

});

return new Response(null, {

status: 101,

webSocket: client,

});

}
```


- 공식 docs의 예제에서 확인할 수 있는 것은, WebSocketPair라는 워커의 자체적인 인스턴스를 사용한다는 것이다.
- 해당 인스턴스는 클라이언트와 서버를 동시에 리턴하고 서버는 그대로 워커에서 사용, 클라이언트는 요청으로 주며 클라이언트에서는 해당 요청을 기반으로 이벤트리스너를 붙이는 방향으로 진행할 수 있었다.

## 세션 & Hibernation

하지만, 주식 대쉬보드에서는 요청하는 종목이 하나가 아니다. 따라서 존재하는 클라이언트의 수만큼 웹소켓 워커가 필요하다는 이야기가 되는데 이를 위해서는 Durable Object 라고 해서 워커에서 지원하는 스테이트가 필요했다. Docs에서는 '유니크한 세션ID 하나 당 싱글턴 인스턴스를 하나씩 유지'해 준다고 한다.

또한 지금 주식 대쉬보드의 유즈 케이스에서는 필요없지만, 앞으로 무조건 필요할 듯한 것까지 구현하였다. 웹소켓과 같은 실시간 기능을 구현하는 경우 가장 쉽게 생각할 수 있는 유저 스토리는 바로 이럴 것이다:

1. 유저가 웹소켓 연결을 시작한다.
2. 유저는 오랜 기간 동안 아무 행동을 하지 않는다.

위 경우에 대해 확인해볼 가치는 충분하다고 생각한다. 이 경우 리소스적인 부하는 어떨까? 클라우드에서 서비스하는 앱의 경우 연결을 유지하는 것의 **가격은 얼마정도일까?** 

- Cloudflare에서는 이러한 케이스를 해결하기 위해서 [Hibernation api](https://developers.cloudflare.com/durable-objects/examples/websocket-hibernation-server) 라는 것을 제공한다.
- 해당 api는 위의 Durable object를 사용한다.

```javascript

import { DurableObject } from "cloudflare:workers";

// Durable Object

export class WebSocketHibernationServer extends DurableObject {

async fetch(request) {

// Creates two ends of a WebSocket connection.

const webSocketPair = new WebSocketPair();

const [client, server] = Object.values(webSocketPair);


this.ctx.acceptWebSocket(server);

return new Response(null, {

status: 101,

webSocket: client,

});

}

async webSocketMessage(ws, message) {

// Upon receiving a message from the client, reply with the same message,

// but will prefix the message with "[Durable Object]: " and return the

// total number of connections.

ws.send(

`[Durable Object] message: ${message}, connections: ${this.ctx.getWebSockets().length}`,

);

}

async webSocketClose(ws, code, reason, wasClean) {

// If the client closes the connection, the runtime will invoke the webSocketClose() handler.

ws.close(code, "Durable Object is closing WebSocket");

}

}

```

- 거의 Docs 내용을 그대로 사용해서 개발을 해볼 수 있었다.
- 인스턴스 세션 및 하이버네이션의 경우 클라우드플레어로 아주 간단하게 해결할 수 있었다. 직접 만들 경우 꽤 오래 걸리지 않을까?
- 이외에도 생각해야 할 것들이 꽤 있을 것으로 보인다. 보안과 관련된 경우는 어떨까? 엔드포인트가 노출될 수 밖에 없으므로 그 부분을 생각해야 할 것 같다.


#### References

- [Vercel functions](https://vercel.com/docs/functions)
- [Cloudflare docs - Durable Objects](https://developers.cloudflare.com/durable-objects/)
- [Cloudflare docs - Hibernation websocket](https://developers.cloudflare.com/durable-objects/examples/websocket-hibernation-server/)

---

# Back Matter

**Source**

<!-- Always keep a link to the source- -->

- based_on::

**References**

<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->

- see:: [multi-agent llm](https://www.superannotate.com/blog/multi-agent-llms)
- [reddit post](https://www.reddit.com/r/LocalLLaMA/comments/14t072j/best_approach_to_multiparty_conversions/)
- [Generative ai vs Agentic ai](https://www.ibm.com/think/topics/agentic-ai-vs-generative-ai)

**Terms**

<!-- Links to definition pages. -->

- AI Model
- MCP
- Generative AI
- Agentic AI
- LLM

**Target**

<!-- Link to project note or externaly published content. -->

- used_in::

---

**Tasks**



- **Questions**





---

**Template Help**

<!-- Links to external help pages on GitHub. -->

- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)
- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)
- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)
- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)
- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)
- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)
