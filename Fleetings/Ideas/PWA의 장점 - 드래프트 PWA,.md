---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: PWA는 앞으로도 더욱 발전할 것이다. 과연 React Native처럼 어느 정도 자리를 잡을 지 기대가 된다. 이미 PWA를 앱의 형태로 감싸는 [PWA-builder](https://www.pwabuilder.com/)라는 툴이 나와서 화제다. 내 개인적으로도, 간단한 빌드로 휴대폰 및 컴퓨터에서 가능하고 호스팅 역시 간편하다는 것이 개인 개발을 하기에 최적이라는 생각이 든다.
visual: "![[what-is-pwa-img.png]]"
created: 2025-06-05, 23:55
modified: 2025-06-05, 23:55
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-06-06T11:46
---
# PWA의 장점

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>



> [!Summary]
> `= this.lead`

**Details**

User Story

- 더 싸게, 더 빠르게 서비스를 만들고 더 많은 플랫폼에 공유하고 싶다?
- RN으로 개발해오면서 이런 장점이 있고 이런 단점이 있었음
- PWA는 RN의 단점에 대해 이런 장점이 있지만 이런 한계가 있음. 나름 최신 기술임
- 계속해서 스터디하면 좋을 것 같음.

최근 PWA에 대해 굉장히 흥미로운 아티클을 읽었기에 따라하면서 정리해 보았음.


### PWA

처음 개발자로써의 커리어를 React Native 앱 개발로 시작하며 간간히 생각하는 화두는 "앱을 개발하는데 있어서 비용과 시간을 얼마나 줄일 수 있을까?"이다. 이 방향으로 사용처가 확대되기도 하고, 내가 아는 개발자 지인 중에서도 RN을 개인적으로 만져 보았거나 회사 스택에 추가하게 되는 경우를 본 적이 있다.

물론 RN이 만능의 해결책은 결코 아니라고 생각한다. 지금까지 0.5x 버전부터 개발을 해 왔던 내 기억을 더듬어 본다면 계속해서 일어나는 메모리 누수와 튕김, 코코아포드 첫 지원 버전업을 하면서 일어났던 네이티브 이슈들... 쉽지 않은 부분이 있었다.

그럼에도 불구하고 React Native의 장점은 명확하다.
- 커뮤니티 라이브러리가 지원한다는 전제 하에, 웹 개발자 한 명이 android, ios 개발자 두 명의 역할을 할 수 있다.
- 마이크로소프트가 서버 공간을 지원하는 OTA 방식의 코드푸시 기능으로 덕에 앱의 버전업과 심사 없이 JS 번들만을 업데이트 할 수 있다.
### RN codepush is dead

하지만, 2025년 3월을 기점으로 코드푸시는 서비스를 종료했다. [한 레딧 포스트](https://www.reddit.com/r/reactnative/comments/1j9h76y/list_of_codepush_alternatives/)에 따르면 숨고에서는 코드푸시 서버를 자체 호스팅하면서 한달에 200여 달러를 지불한다고 한다. 대략 20만~30만 원인 셈이다. Man-hour에 대해서는 알 수 없지만... 자체 모듈을 개발하는 시간이 꽤 걸렸을 거라고 생각한다. 

### 여기서 PWA가 등장한다.

PWA는 브라우저를 런타임으로 가지는 웹 앱이니 만큼, 웹과 동일하게 사용자가 해당 URL로 접속하는 순간 업데이트 여부를 판별한다.

![PWA 업데이트](pwa-update.png)

유저가 앱에 진입 시 네트워크에 연결되어 있다면 백엔드와의 연결을 통해 컨텐츠를 렌더링하고 캐시를 업데이트하고,

![pwa-update2](pwa-update2.png)

Images from Chrome for developers - [Beyond SPAs](https://developer.chrome.com/blog/beyond-spa)

네트워크에 연결되어 있지 않다면, 서비스 워커에서는 캐시 api에서 저장된 캐시를 호출해 렌더링하게 된다.

이 뜻은, PWA는 브라우저에서 빌드된 앱을 다운로드해서 데스크탑이나 모바일에서 '앱'처럼 사용할 수 있는 것과 동시에, 앱을 호스팅할 수 있는 공간만 있다면 앱을 간편하게 호스팅할 수 있다는 것이다. 코드푸시 같은 제 3자가 필요없으면서도 앱처럼 사용할 수 있게되는 것이다.

나 역시 vite 번들러를 사용해 PWA를 윈도우, 맥OS 및 모바일에서 다운로드 해 보고, 업데이트를 직접 해보면서 정말 간편하다고 느꼈다.

### PWA의 단점

물론 PWA는 이제 피어나는 기술이다. 당연히 RN과 같은 문제가 많을 것이라고 생각한다.

>RN으로 개발할 때를 생각해 보자. 카메라를 활용하는 커뮤니티 프로젝트가 갑작스런 OS 업데이트를 통해 1주 정도 사용하지 못하게 되었을 때, 이를 해결할 수 있었는지? CS 적으로 업데이트를 해당 기간 자제해달라는 공지를 올리면서 해결했다. 
>웹 개발자인 내가 ios와 안드로이드 네이티브 카메라 코드를 건드리기에 일주일은 너무 짧았다.
>
>PWA의 경우에는? 카메라를 사용하지는 않겠지만... 어떤 문제가 생긴다면 윈도우와 맥os의 코드를 쳐다봐야 하는 경우가 생길 수 있지 않을까?
>

### 그럼에도 불구하고, 배울 가치가 있다고 생각한다.

PWA는 앞으로도 더욱 발전할 것이다. 과연 React Native처럼 어느 정도 자리를 잡을 지 기대가 된다. 이미 PWA를 앱의 형태로 감싸는 [PWA-builder](https://www.pwabuilder.com/)라는 툴이 나와서 화제다. 내 개인적으로도, 간단한 빌드로 휴대폰 및 컴퓨터에서 가능하고 호스팅 역시 간편하다는 것이 개인 개발을 하기에 최적이라는 생각이 든다.

### Progressive Web App은 앱의 형태로 존재하지만 켜는 것만으로도 업데이트를 할 수 있다.
어떻게 업데이트를 처리하는지? 
- RN
- 앱 진입 -> 코드푸시 서버와 접속 -> 업데이트 있다면 strategy에 따라 업데이트

- PWA
- 앱 진입 -> 서비스 워커에서 업데이트 확인 -> 있다면 업데이트 필요 표시

### React native의 가장 큰 문제점 - 업그레이드가 힘듬.
[reddit post - hard to upgrade React Native version](https://www.reddit.com/r/reactnative/comments/15ztadx/what_are_the_hardest_most_difficult_tasks_that/)
PWA는 이에 대해서 자유로움

### PWA의 단점: 뭐가 가능한지 아직 잘 모름

[Challenges using PWA](https://www.reddit.com/r/PWA/comments/1gw4mol/why_is_native_development_still_so_common/)
- 비디오 컴프레싱이 안됨.
- 더 많은 스터디가 필요함. 해볼만한 가치 있음

### PWA builder - PWA 앱 래퍼을 통해서 앱도 만들 수 있다?

### 결론

PWA는 RN처럼 나같은 비전공자, 생계형 개발자에게 흥미로운 화두를 제공해준다.
하나의 서비스를 얼마나 빠르게, 얼마나 싸게 개발할 수 있는지?
PWABuilder와 같은 더 흥미로운 툴들이 있으니 앞으로 얼마나 더 성장할지 계속 확인하는 것이 흥미로울 것이다.


#### Github Page로 PWA를 호스팅할 수 있다?

일반적인 웹 앱의 경우, 

**Supporting Content**

- 

---
# Back Matter

**Source**

- based_on::

**References**

- see:: 
- [[PWA vs Electron]] [[WASM-PWA]] [[PWA의 장점 - 드래프트 PWA,]]
- [PWA in Vue Vite](https://dev.to/adefam/pwa-in-vue-vite-53a3)
- [PWA Vite to GH Pages](https://dev.to/iamfranco/deploy-react-vite-pwa-to-github-pages-35i)
- [my pwa-github page testing app](https://github.com/jihyeonjeong11/pwa-github-page)
- [reddit post about react native codepush alternatives](https://www.reddit.com/r/reactnative/comments/1j9h76y/list_of_codepush_alternatives/)

**Terms**

- 

**Target**

- used_in::

---
**Tasks**

- 

**Questions**

- question::
