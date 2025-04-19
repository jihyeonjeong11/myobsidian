---
tags:
  - type/sketchnote
  - type/note
  - theme/http
aliases: 
lead: SSE는 HTTP 연결로 시작되고, 서버는 메시지를 보내기만 하며 클라는 받기만 한다.
visual: "![[sse.webp]]"
created: 2025-04-18, 21:37
modified: 2025-04-18, 21:37
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-18T22:49
---
[[SSE with Node.js]]

# Understanding Server-Sent Events with Node.js


```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

-라이브 스포츠 업데이트, 스톡 프라이스, 채팅, 뉴스 피드 같은 것들을 만드려면 숏 폴링이나 웹소켓이 필요하다. 그 중 저자에 따르면 SSE 가 가장 간편하다고 한다.

## SSE란 무엇인가?

- 서버와 클라이언트의 일방통행 통로를 개설하는 것이라고 볼 수 있다. Websocket과 다르게, 이중 구조가 아니라는 것을 유념하자. 서버가 업데이트를 보내기만 하며 클라이언트는 받기만 한다.

> [!How it works]
> 1. 클라이언트가 서버에 일반적인 http 요청을 보냄
> 2. 서버는 해당 요청을 끊지 않으며, 업데이트가 일어날 때 클라이언트에 응답을 보냄
> 3. 클라이언트는 해당 응답을 받을 때마다 실시간 처리 함.

이러한 SSE는 라이브 뉴스, 주식 업데이트, 스포츠 스코어, 리얼타임 모니터링 대쉬보드에 사용할 수 있다.

## SSE와 다른 기술을 비교하면?

### 1. SSE vs WebSockets

- Websocket은 풀 듀플렉스 의사소통을 함으로 클라이언트와 서버가 같이 메시지를 보내고 받을 수 있다. 채팅 및 멀티플레이어 게임에 적합하다.
- SSE는 서버에서만 메시지를 보내고 클라이언트는 받기만 한다. 따라서 웹소켓보다 더 간단하고 더 가볍다.
### SSE vs Polling

- 롱 폴링은 클라이언트가 반복해서 서버에 요청을 보내 새 데이터가 있는지를 체크하는 방식이다. 새 데이터가 없어도 어쩃든 요청이 보내지기 때문에 일반적으로 비효율적.
- SSE는 연결을 계속 가지고 있기 때문에 더 효율적이라고 볼 수 있다.

따라서 SSE는
- 클라이언트가 서버에 데이터를 받기만 하면 되는 경우
- 서버 상태에 따라 일시적인 지연 상황이 일어나도 괜찮은 경우
- 퍼포먼스, 자원 절약이 중요할 경우 
의 경우에 고려할 만 하다.

## SSE는 어떻게 동작하는가?

- HTTP 연결로 시작한다. 헤더의 content type 및 포맷이 SSE에 맞게 설정되어야 하고 서버는 text/event-stream content type으로 보내준다. 데이터의 포맷은:

- ID: 재접속할 시 클라이언트가 끊어진 세션을 찾기 위한 세션 아이디
- Event: 이벤트 타입
- Data: 각 메시지는 여러개의 데이터르 가질 수 있다. 하나의 메시지는 두개의 뉴라인으로 끝나게 되고 데이터 필드 사이는 하나의 뉴라인으로 구분됨(\n)
```
id: 123  
event: message  
data: Hello World  
data: This is another message line
```


**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on:: https://itsfuad.medium.com/understanding-server-sent-events-sse-with-node-js-3e881c533081

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see:: 

**Terms**
<!-- Links to definition pages. -->
- 

**Target**
<!-- Link to project note or externaly published content. -->
- used_in::

---
**Tasks**
<!-- What remains to be done with this note? --> 
- 

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