---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: webRTC 프로토콜을 활용한 클라이언트 간 통신 예시 여기서는 맥북 내장 웹캠 -> 시그널링 서버 -> 다른 클라이언트(윈도우컴퓨터의 브라우저)로 연결하는 과정을 다룸.
visual: "![[image.jpg]]"
created: 2025-05-28, 10:47
modified: 2025-05-28, 10:47
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-28T11:43
---

<!--  See "Template Help" below for using properties -->

# WebRTC Step to Step guide
<!--  Clear and descriptive title -->

<!-- My sketchnote if available -->
```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

옵션 1: 맥북의 웹캠 피드를 다른 기기에서 rct연결로 보이기
옵션 2: chatGPT에 따르면 브라우저의 두 탭으로 다른 앱을 사용해서 시뮬레이션 가능하다고 함.

|Component|Description|
|---|---|
|`getUserMedia()`|Capture webcam|
|`RTCPeerConnection`|WebRTC peer object|
|Signaling Server|Exchange offers/answers/candidates|
|STUN/TURN Server|Deal with NAT/firewalls|
|Video Element|Render video in browser|
### 1. getUserMedia()

내장 웹켐이므로 기본 browser api로 웹캠 내용을 잡을 수 있음.

```javascript

<body>

<h1>Webcam Preview</h1>

<video id="localVideo" autoplay playsinline></video>

  

<script>

const video = document.getElementById('localVideo');

  

async function startWebcam() {

try {

const stream = await navigator.mediaDevices.getUserMedia({

video: true,

});

video.srcObject = stream;

} catch (err) {

console.error('Error accessing webcam:', err);

}

}

  

startWebcam();

</script>

</body>


```


**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::[medium post](https://medium.com/@pranjal.3vyas/step-by-step-guide-to-building-a-webrtc-application-bda84fd566b3)

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