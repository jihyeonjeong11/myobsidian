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
updated: 2025-05-28T17:55
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
// 첫 클라이언트 + 엔트리 포인트 맥북의 내장 웹캠
navigator.mediaDevices.getUserMedia({ video: true, audio: true })

```

### 2. RTCPeerConnection

- 클라이언트간의 연결을 Peer로 정의함.

```javascript
const pc = new RTCPeerConnection();
stream.getTracks().forEach(track => pc.addTrack(track, stream));

```

### 3. Create and send offer from peer A

- sdp 연결의 시작. 먼저 client A에서 오퍼를 생성해서 B로 보냄.
- 생성된 오퍼는 localDescription으로 저장함.
- Generate an **SDP offer** and send it to the other peer.

```

const offer = await pc.createOffer(); await pc.setLocalDescription(offer); // send offer.sdp to Peer B
```

### 4. Receive and answer offer from Peer B

- 받은 오퍼(remote offer)를 통해 SDP answer를 생성함.

```javascript

await pc.setRemoteDescription(offerFromPeerA);
const answer = await pc.createAnswer();
await pc.setLocalDescription(answer);
// send answer.sdp to Peer A

```


### 5. Set Remote Answer from Peer A

- B로부터 받은 answer는 remoteDescription으로 저장됨.

```javascript

await pc.setRemoteDescription(answerFromPeerB);

```

### 6. Exchange ICE Candidates from Peer A,B

- SDP 연결이 합의 되었다면, peer간의 연결을 위한 path를 잡는데 이것이 ICE이고 여러 path 중 최선을 찾는 것이므로 candidate라고 한다. 여기서 Stun server, turn 서버가 사용됨.

```javascript

pc.onicecandidate = e => {
  if (e.candidate) sendToPeer(e.candidate);
};


await pc.addIceCandidate(candidateFromPeer);


```

**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::[medium post](https://medium.com/@pranjal.3vyas/step-by-step-guide-to-building-a-webrtc-application-bda84fd566b3)
- [웹소켓 webrtc 예제](https://github.com/nnmer/webrtc-ws-example)

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see:: 

**Terms**
- **WebRTC**  
    Web Real-Time Communication — a browser API that enables peer-to-peer audio, video, and data transfer without plugins.
    
- **Peer**  
    A peer is any device or browser instance participating in a direct connection with another.
    
- **P2P (Peer-to-Peer)**  
    A direct connection between devices without routing media through a central server.
    
- **MediaStream**  
    A stream of audio and/or video tracks captured from devices like a webcam or microphone.
    
- **`getUserMedia()`**  
    API to request access to media devices. Returns a `MediaStream`.
    
- **Track**  
    A single audio or video input within a `MediaStream`.
    
- **RTCPeerConnection**  
    The core object for setting up a WebRTC connection. Manages media transport and ICE negotiation.
    
- **SDP (Session Description Protocol)**  
    A text-based format that describes media capabilities like codecs, resolution, and network details for negotiation. For exchanging multimedia
    
- **Offer**  
    The initiating peer’s proposed connection details (SDP).
    
- **Answer**  
    The responding peer’s accepted connection details (SDP).
    
- **`setLocalDescription()`**  
    Sets your own SDP (offer or answer) in the peer connection.
    
- **`setRemoteDescription()`**  
    Applies the other peer’s SDP to your connection.
    
- **ICE (Interactive Connectivity Establishment)**  
    A process to find the best network path between peers.
    
- **ICE Candidate**  
    A potential network route (IP + port) discovered by the browser for peer connection.
    
- **`onicecandidate`**  
    Event fired when a new ICE candidate is available.
    
- **`addIceCandidate()`**  
    Adds a remote ICE candidate to the local connection.
    
- **STUN Server**  
    A public server that helps a device discover its public IP address.
    
- **TURN Server**  
    A relay server that forwards media/data when a direct connection cannot be established.
    
- **`addTrack()`**  
    Attaches a video/audio track from a `MediaStream` to an `RTCPeerConnection`.
    
- **`ontrack`**  
    Event fired when a media track from the remote peer is received.
    
- **RTCDataChannel**  
    WebRTC feature that allows sending arbitrary text or binary data (e.g., chat, files) directly between peers.

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