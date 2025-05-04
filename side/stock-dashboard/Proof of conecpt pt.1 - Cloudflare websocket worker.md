---
tags:
  - type/sketchnote
  - type/note
  - theme/side-project
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[putMyWork.jpg]]"
created: 2025-04-30, 21:09
modified: 2025-04-30, 21:09
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-01T00:12
---
해당 노트의 목적은 사이드 프로젝트 제작 중 스택이 가능한가?를 판별하기 위한 기록임.

# Proof of conecpt



```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

- 이전에 TRPC 챗 사이드 프로젝트를 NextJS 앱 내부에서 소켓 서버/클라이언트까지 클로닝하여 Vercel에 업로드하려했지만 Vercel에서는 웹소켓을 지원하지 않아 실패했음 그렇기 때문에 Cloudflare에서 websocket을, vercel에서 풀스택 넥스트 앱을 올려서 둘이 소통하는 방식으로 진행하려 함.

- 파트 1은 클라우드플레어가 웹소켓을 돌릴 수 있는지임.
- 여러 example로 확인해보았고 최종적으로 Durable object와 Hibernation을 적용한 websocket으로 결정함.



### Durable Objects

- A **Durable Object** is a **serverless, stateful singleton** that:
- 서버리스의 한계인 stateless를 해결하는 singleton 패턴.


> [!From docs](https://developers.cloudflare.com/durable-objects/)
> 
> SQLite-backed Durable Objects are now available on the Workers Free plan with these [limits](https://developers.cloudflare.com/durable-objects/platform/pricing/).
> [SQLite storage](https://developers.cloudflare.com/durable-objects/best-practices/access-durable-objects-storage/) and corresponding [Storage API](https://developers.cloudflare.com/durable-objects/api/storage-api/) methods like `sql.exec` have moved from beta to general availability. New Durable Object classes should use wrangler configuration for [SQLite storage](https://developers.cloudflare.com/durable-objects/best-practices/access-durable-objects-storage/#wrangler-configuration-for-sqlite-durable-objects).
> 
> 공식 docs의 내용에 따르면 Durable Objects는 내부의 Storage API를 써서 SQLite에 스테이트를 저장하는 역할을 하고 유저는 wrangler config으로 조정 가능함.


> [!From docs](https://developers.cloudflare.com/durable-objects/)
> 
   A Durable Object is a special kind of [Cloudflare Worker](https://developers.cloudflare.com/workers/) which uniquely combines compute with storage. Like a Worker, a Durable Object is automatically provisioned geographically close to where it is first requested, starts up quickly when needed, and shuts down when idle
> 
> 독스 내용에 따르면, 자동으로 시작할때 켜주고 닫히는 기능도 존재함
> 역시 웹소켓에 있어 아주 좋은 기능일 것임.


### Durable objects - websocket

- 여기서는 두가지 종류의 websocket이 있다.

> [! from official docs](https://developers.cloudflare.com/durable-objects/best-practices/websockets/#websocket-hibernation-api)
>
>1. Native Durable Object WebSocket API, which allows your Durable Object to hibernate without disconnecting clients when not actively doing work **(recommended)**.
>2. Web Standard WebSocket APIs, using the familiar `addEventListener` event pattern. 
>   
>   워커에서 사용하는 Durable Object 웹소켓. hibernation 기능을 사용하기 위해 사용함(권장사항)
>   혹은 그냥 웹 사양으로 사용할 수 있다.
>   여기서는 1번을 설명한다.
>   

- 상술했듯 Cloutflare Worker는 Serverless이다. 그 말은 세션을 저장하지 못하기 때문에 Durable Objects로 hibernation을 적용한 웹소켓을 작성하는 것이 권장된다.
- 더 확인하고 싶다면  [Cloudflare Edge Chat Demo ↗](https://github.com/cloudflare/workers-chat-demo) 여기를 확인해 보자.
- Hibernation API의 가장 큰 장점은, 연결이 끊어지면 알아서 껏다 켜주기 때문에 비용절약이 된다는 것이다. 
- 해당 api는 클라우드플레어의 고유 개념이라, 스테이트 역시  [DurableObjectState](https://developers.cloudflare.com/durable-objects/api/state) interface 고유값을 사용함.

>Note
>Hibernation is only supported when a Durable Object acts as a WebSocket server. Currently, outgoing WebSockets cannot hibernate.
>
>해당 워커를 다른 웹소켓에 연결하는 클라이언트로 사용하면 Hibernation 기능을 사용할 수 없음.



### Hibernation Websocket Server

**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see:: 
- [Cloudflare docs - Websocket](https://developers.cloudflare.com/network/websockets/)
- [Cloudflare docs - Durable Objects](https://developers.cloudflare.com/durable-objects/)
- [Cloudflare docs - Hibernation websocket](https://developers.cloudflare.com/durable-objects/examples/websocket-hibernation-server/)

**Terms**
<!-- Links to definition pages. -->
- Singleton - 

**Target**
<!-- Link to project note or externaly published content. -->
- used_in::
- 

---
**Tasks**
<!-- What remains to be done with this note? --> 
- 웹소켓에 외부 api를 쓰는게 가능한가? - 가능한것으로 보임. 환경변수로 api key 넣고 다시쓸것

**Questions**
<!-- What remains for you to consider? --> 
- question::

---
**Template Help**
<!-- Links to external help pages on GitHub. -->
- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)
- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)
- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)
- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)
- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)
- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)