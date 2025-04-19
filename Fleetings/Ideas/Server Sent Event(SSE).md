---
tags:
  - type/sketchnote
  - type/note
  - theme/http
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[image.jpg]]"
created: 2025-04-18, 21:06
modified: 2025-04-18, 21:06
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-18T21:38
---
[[Keep-Alive]] [[Server Sent Event(SSE)]] [[Websocket Protocol]] [[Understanding Server-Sent Events with Node.js]]

# Server Sent Event(SSE)



```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

- [Stack overflow](https://stackoverflow.com/questions/33265773/http-1-1-message-protocol-and-server-sent-events)의 내용에 따라 HTTP/1.x의 경우 SSE를 구현하기 위해선 별도의 URI를 통해  Connection 필드를 keep-alive로 해줘야 했다.```

```

HGet / http/1.1
HeaderField(Host, localhost:8080)
HeaderField(User-Agent, Mozilla/5.0 (X11; Ubuntu; Linux x86_64;rv:41.0)     Gecko/20100101 Firefox/41.0)
HeaderField(Accept, text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8)
HeaderField(Accept-Language, en-GB,en;q=0.5)
HeaderField(Accept-Encoding, gzip, deflate)
HeaderField(Connection, keep-alive)

```

## HTTP/2의 경우는

- 웹 워커를 통해 멀티쓰레딩을 구현한 뒤 거기서 받아서 본 앱에 전달하라고 MDN에서는 권장하고 있음.

>[!from MDN]
>
>Traditionally, a web page has to send a request to the server to receive new data; that is, the page requests data from the server. With server-sent events, it's possible for a server to send new data to a web page at any time, by pushing messages to the web page. These incoming messages can be treated as _[Events](https://developer.mozilla.org/en-US/docs/Web/API/Event) + data_ inside the web page.
>
>EventSource객체를 이용해서 프론트에서 받는다.



**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::[Stack Overflow](https://stackoverflow.com/questions/33265773/http-1-1-message-protocol-and-server-sent-events) [MDN reference](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events) 

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see:: [MDN Web Workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API) [Using Server sent event with NodeJS](https://itsfuad.medium.com/understanding-server-sent-events-sse-with-node-js-3e881c533081)

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