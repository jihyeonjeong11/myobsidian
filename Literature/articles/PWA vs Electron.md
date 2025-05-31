---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
visual: "![[electron.png]]"
created: 2025-05-31, 18:17
modified: 2025-05-31, 18:17
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-31T22:45
lead: |-
  Electron은 운영 체제 관련 api를 사용할 때 가장 좋음(fs나 시스템 알림)
  PWA는 앱을 깔지 않고 사용할 수 있는점이 가장 큰 메리트임. 웹 앱이지만 로우 레벨 하드웨어를 제어해야 할 경우 좋음.
---


# PWA vs Electron



```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>



> [!Summary]
> `= this.lead`

**Details**

PWA와 Electron은 비슷한 테크 스택을 공유하지만, 다른 목적을 가지고 있음. PWA는 브라우저에서 돌아가는 웹 앱이지만, 인스톨할 필요가 없음.
Electron은 웹 테크로 데스크탑 앱을 만드는 것임. 

여기서는 두 기술의 장점과 단점, 어떤 상황에서 사용하는지 확인할 것임. 

### 1. PWA란 무엇인지?

Progressive Web App이란 최신 웹 기술로 데스크탑과 모바일 기기에서 네이티브와 같은 경험을 제공하기 위한 기술이다. 구글에서 스폰서하고 있고 회사의 컨버전율과 UX 향상을 목적으로 함. 최근에는 트위터 라이트, 핀터레스트, 틴더, 스포티파이, 트리바고에서 사용중이다.

PWA는 웹사이트를 만드는 느낌으로 html css js로 빌드됨. SEO도 먹힘. 하지만 다른 웹사이트와는 다르게 오프라인에서도 동작해야 하고, 어느정도의 시스템 알림과 같은 운영 체제 API를 사용 가능하다.

### 1-2. PWA는 어떻게 동작하나?

PWA는 서비스 워커로 동작함. 오프라인 실행을 보장해야 하기 때문에 데이터를 서비스 워커 단에서 저장해야 한다. 이를 위해서 서비스 워커에는 네트워크 응담을 인터셉트해서 캐싱했다가, 오프라인시 사용, 온라인 시 업데이트 하는 식으로 돌아감.

이 서비스 워커를 프록시라고 생각하는것이 편함. 

또한 백그라운드 싱킹, 백그라운드 푸시 알림과 같은 것도 만들게 됨. 이게 웹 앱과의 가장 큰 차이점으로 백그라운드에서 돌아간다는 것이 가장 큰 차이임.

메인 쓰레드에서 이렇게 서비스 워커 사용

```javascript
if ('serviceWorker' in navigator) {
    window.addEventListener('load', function() {
      navigator.serviceWorker.register('/sw.js').then(function(registration) {
        console.log('Service Worker registered:', registration.scope);
      }, function(err) {
        console.log('Service Worker registration failed:', err);
      });
    });
  }
```

그리고 서비스 워커는 이런 식으로 구성됨.

```javascript
  // Register an event listener for the 'fetch' event on the service worker
self.addEventListener('fetch', function(event) {
 
    // Log the URL of the requested resource to the console
    console.log('URL requested: ', event.request.url);
  
  
    // Use the 'respondWith' method to handle the fetch event
    event.respondWith(
      // Open the cache named 'my-cache'
      caches.open('my-cache').then(function(cache) {
        // Try to find a match for the requested resource in the cache
        return cache.match(event.request).then(function(response) {
          // If a match is found in the cache
          if (response) {
            // Log that the response was retrieved from the cache
            console.log('Response retrieved from cache: ', event.request.url);
            // Return the cached response
            return response;
          } else {
            // If no match is found in the cache, fetch the resource from the network
            return fetch(event.request).then(function(networkResponse) {
              // Add the network response to the cache
              cache.put(event.request, networkResponse.clone());
              // Log that the response was added to the cache
              console.log('Response added to cache: ', event.request.url);
              // Return the network response
              return networkResponse;
            });
          }
        });
      })
    );
  });
```

### 1-3. PWA의 장점

- **빠른 개발**

js 코드 구조로 개발하므로 네이티브 앱에 비해 빌드 밑 디플로이가 아주 빠름. 소규모 비즈니스에 적합

- **빌드가 편함**

네이티브 앱에 비해서 개발, 유지비가 얼마들지 않음. 브라우저가 런타임이기 때문에 운영체제를 덜 탄다. 또한 앱 스토어가 아니라 서치 엔진이라 SEO가 더 간편함.

- **UI/UX상 이점**

웹 앱의 단점을 개선해 심리스한 경험을 선사하므로 웹 페이지에 비해 이득이 있다. 오프라인에서도 잘 작동, 시스템 푸시 알림, 빠른 로딩 타임 등. 유저의 리텐션에 이득이 있다. 그러면서도 아이콘, 네이티브 앱 과 같은 경험 등 웹 사이트에 비해 이점이 있다.

- **퍼포먼스 이점**

웹 페이지에 비해 퍼포먼스 상으로도 이득이 있다. 백그라운드에서 도는 서비스 워커로 멀티쓰레딩을 전제로 하기 때문에 로딩 타임, 데이터 사용량, 전체적인 퍼포먼스 상으로 더 좋다. 

### 1-4. PWA의 단점

- **하이브리드 앱의 한계**

상대적으로 최신 기술이므로 아직 지원하지 않는 기능이 있을 수 있음. PWA의 유저들의 인식이 얼마 없어서 혼선을 줄 수 있음. PWA에 거부감을 가질 ㅅ도 있음

- **호환성 이슈**

모든 브라우저가 PWA의 모든 기능을 지원하지 않으므로 문제가 있을 수 있음

- **IOS 푸시 알림이 최근에 추가되었음**

IOS 16.4 기준 푸시 알림 기능이 가능해졌음. 

### 2-1. Electron이란?

일렉트론은 하이브리드 데스크탑 앱을 만들기 위한 프레임워크이다. 자체 API로 시스템 noti, fs 등을 브리징해서 사용함

### 2-2. Electron 원리

데스크탑 앱 래퍼 안에 웹뷰를 띄우는 식으로 함. 실행은 크로미움 브라우저 인스턴스로 실행해서 브라우저와 같은 모든 기능을 사용한다. 메인 프로세스에서 크로미움 브라우저 인스턴스로 웹뷰를 띄우고 메인 윈도를 보여준다. 
그 이외에 renderer 프로세스라는 것이 있어서 여기에 웹 페이지를 띄운다. 멀티쓰레딩 방식이며 이를 IPC라고 부른다??? **이거 뭔소리?**

IPC는 웹 워커처럼 심플 메시지 방식으로 동작함. 모듈 이름은 ipcMain, ipcRenderer라고 불림. 코드 예시는 이렇다.

```javascript
// Main Process
const { ipcMain } = require('electron');


ipcMain.on('message-from-render-process', (event, arg) => {
  console.log(arg);  // prints "ping"


  // send a reply message to the render process
  event.reply('message-from-main-process', 'pong');
});


// Render Process
const { ipcRenderer } = require('electron');


// send a message to the main process
ipcRenderer.send('message-from-render-process', 'ping');


// listen for messages from the main process
ipcRenderer.on('message-from-main-process', (event, arg) => {
  console.log(arg);  // prints "pong"
});
`````

### 2-3. 일렉트론의 장점

- 크로스 플랫폼 개발
RN과 마찬가지로 윈도우 맥 리눅스 개발이 가능하다.
- PWA에 비해 커뮤니티가 크다
- 성숙한 프레임워크
- 라이브러리가 많음
- 웹페이지 코드와 돌려 쓸 수 있음

### 3-1. PWA vs Electron

- 퍼포먼스
PWA가 근소하게 우세. (서비스 워커로 코드를 나눠서 쓰므로)
또한 브라우저 인스턴스로 돌아가므로 최적화가 더 잘되어 있음

- 보안
PWA 우세. 브라우저와 같은 시스템 그대로 적용 됨. 
엘렉트론은 zero-day exploits나 운영체제 별 공격방식에 노출 가능함

- 모바일친화성
PWA가 크게 우세. 단순히 웹페이지를 띄운다고 생각하기 때문에...

- 데스크탑 친화성
일렉트론 우세. 슬렉, 마이크로소프트 팀즈, vscode에서 엘렉트론으로 개발 중임.

- 업데이트 및 CI/CD
PWA 우세. 코드를 업데이트해서 네트웍으로 받으면 업데이트 된다. 일렉트론은 앱 업데이트 과정이 필요하다.

### 3-2. 따라서

PWA는 앱이 설치되지 않는 환경에서 적합함. 일렉트론은 데스크탑 느낌을 주는데에 적합하다.

**Supporting Content**

- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::
- [base blod](https://cleancommit.io/blog/pwa-vs-electron-which-architecture-wins/)
- [PWA 설명](https://cleancommit.io/blog/benefits-of-progressive-web-applications-pwa/?ref=blog.cleancommit.io)

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