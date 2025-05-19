---
tags:
  - type/sketchnote
  - type/note
  - theme/websocket
  - type/draft
aliases: 
lead: 클라우드플레어의 소켓 기능을 통해 편하게 구현함
visual: "![[image.jpg]]"
created: 2025-05-17, 12:09
modified: 2025-05-17, 12:09
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-18T13:04
---
1. 이전부터 웹소켓 다뤄보고 싶었음
2. 가장 문제는 deploy였음. -> 버셀은 간편하지만 소켓서버를 지원하지 않기때문에
3. 마침 클라우드플레어에서 가능하다는 이야기를 들었는데 해봄
4. hibernation 기능으로 따로 최적화 코드를 집어넣지 않고 시도해서 잘됨
5. 프론트에서는 리커넥트정도가 있음
6. 보안에 대해서 생각할 점이 있음 - 웹소켓 url 노출

# Websocket with Cloudflare worker

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

> [!Summary]
> `= this.lead`

**Details**

이전부터 클라우드플레어의 프리 요금제로 무언가를 만들어보고 싶다고 생각했다. 

## Cloudflare worker

- Cloudflare의 서버리스 플랫폼인 Worker는 **Nextjs의 Function과는 다르게 웹소켓을 자체적으로 지원**한다고 해서 한번 구현해 보았다.

- Vercel의 [공식 Docs](https://vercel.com/guides/do-vercel-serverless-functions-support-websocket-connections)에서는 스테이트를 구현하기 위해 서드 파티 스토리지와의 사용을 권장한다.
- Cloudflare의 Worker에서는 Websocket 인스턴스를 자체적으로 '어딘가에' 저장해주기 때문에 Websocket 서버로 활용할 수 있다고 한다.

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

- 위 공식 예시를 본다면, new WebSocket()이 아니라 new WebSocketPair라는 자체적인 인스턴스를 열어서 Worker가 어떤 방식으로든 인스턴스 자체를 저장해 소켓을 유지시킨다고 알 수 있겠다.
- 이렇게까지만 구현하더라고, 토이 수준에서는 문제가 없을 수 있다... 하지만 소켓 자체는 앞으로도 활용도가 무궁무진하다고 생각하기 때문에 여기서 더욱 나가보는 것도 좋겠다.
### 비용?
- 스타트업 업계에서 일하면서 깨달은 것 하나는 서버는 숨만 쉬는데 비용이 청구된다는 것이다.
- 그렇다면 웹소켓은? 기본적인 stateless의 서버 역시 켜놓는데도 청구되는 비용이 있다. 이를 줄일 수 있다면 도움이 될 것이다.

## Websocket Hibernation API
- 위 WebSocketPair에 더해서 클라우드플레어에서는 Durable objects라는 자체 데이터 스토리지를 활용한 Hibernation API를 제공한다.
- 이를 사용하기 위해서는 코드 내부에서 저장된 웹소켓 인스턴스를 직접 참조할 수 있어야 한다. 이것을 가능하게 하는 것이 [Durable Storage](https://developers.cloudflare.com/durable-objects/)이다.

```javascript

import { DurableObject } from "cloudflare:workers";

// Durable Object

export class WebSocketHibernationServer extends DurableObject {

async fetch(request) {

// Creates two ends of a WebSocket connection.

const webSocketPair = new WebSocketPair();

const [client, server] = Object.values(webSocketPair);

// Calling `acceptWebSocket()` informs the runtime that this WebSocket is to begin terminating

// request within the Durable Object. It has the effect of "accepting" the connection,

// and allowing the WebSocket to send and receive messages.

// Unlike `ws.accept()`, `state.acceptWebSocket(ws)` informs the Workers Runtime that the WebSocket

// is "hibernatable", so the runtime does not need to pin this Durable Object to memory while

// the connection is open. During periods of inactivity, the Durable Object can be evicted

// from memory, but the WebSocket connection will remain open. If at some later point the

// WebSocket receives a message, the runtime will recreate the Durable Object

// (run the `constructor`) and deliver the message to the appropriate handler.

this.ctx.acceptWebSocket(server);

return new Response(null, {

status: 101,

webSocket: client,

});

}

```

```toml

name = "websocket-hibernation-server"

[[durable_objects.bindings]]

name = "WEBSOCKET_HIBERNATION_SERVER"

class_name = "WebSocketHibernationServer"

[[migrations]]

tag = "v1"

new_sqlite_classes = ["WebSocketHibernationServer"]

```

- Docs에 따라, DurableObject를 상속받고 config 파일에서 db를 사용하도록 조정해주면 쉽게 적용할 수 있었다.


- 해당 웹소켓은 현재 Stock-dashboard 토이프로젝트에 적용되어 있다. 웹소켓은 앞으로도 실시간 기능을 구현하는데 필수적이니 만큼, 앞으로도 활용가능성이 무궁무진할 것이라고 생각한다.
- Vercel에 Nextjs를, 웹소켓 서버를 Cloudflare에 무료로 등록할 수 있어 더욱 더 무언가를 만들 수 있는 폭이 넓어졌다.

**Supporting Content**

- 

---
# Back Matter

**Source**

- based_on::

**References**

- see:: - [Cloudflare docs - Websocket](https://developers.cloudflare.com/network/websockets/)
- [Cloudflare docs - Durable Objects](https://developers.cloudflare.com/durable-objects/)
- [Cloudflare docs - Hibernation websocket](https://developers.cloudflare.com/durable-objects/examples/websocket-hibernation-server/)
- [DurableObject socket example](https://github.com/upstash/examples/blob/main/examples/cloudflare-websockets/worker/src/index.ts)
- [Vercel docs - Websocket connection](https://vercel.com/guides/do-vercel-serverless-functions-support-websocket-connections)
- [Vercel functions](https://vercel.com/docs/functions)

**Terms**

- 

**Target**

- used_in::

---
**Tasks**

- 

**Questions**

- question:: 보안에 대해서 생각해볼것? 웹소켓 url 노출?

---
**Template Help**
<!-- Links to external help pages on GitHub. -->
- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)
- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)
- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)
- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)
- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)
- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)