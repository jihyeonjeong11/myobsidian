---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: MVC으로 만든 클리커 파밍 게임
visual: "![[farmgame.png]]"
created: 2025-06-01, 21:17
modified: 2025-06-01, 21:17
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-06-02T00:11
---
<!--  See "Template Help" below for using properties -->

# FarmGameJS
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
### 1. 폴더구조

```
ROOT
└─src
    ├─element
    │  ├─elements
    │  └─element_actions
    ├─game
    ├─game_manager
    └─view
        ├─buttons
        └─menus

```


- Model: element 폴더
- View: view 폴더 내부.
- Controller: game_manager 폴더의 listener, 및 game 폴더 내부
- Static assets: game_manager 안의 값들.

### 2. 모델

### 3. 실행순서

1. main.html 시작. 시작 세팅값으로 시작함
```javascript
// main.js

document.getElementById("buttonPlay").addEventListener("click", function (e) {

  console.log("buttonplay", e);

  preLoadGame();

  document.getElementsByClassName("menu")[0].remove();

  e.target.removeEventListener("click", this, false);

  loadGame();

});

```

2. preloadGame

```javascript

export async function preLoadGame() {

    defineGameSettings(); // 게임 시작 전 설정된 값 받아옴.

    new Player(); // 플레이어 클래스 인스턴스 형성, 마우스 위치, 커서 아이콘, 돈 및 메소드

    loadResources(); // 자원 인스턴스 형성, 과일 씨앗 돌 나무 잎 -> 플레이어 인벤
    loadElements(); // 엘리먼트 클래스 인스턴스 형성, -> 맵에 위치하는 인터랙터블

    loadButtons(); // 버튼 클래스 인스턴스 이외 게임 메뉴들 

    await loadMenus(); // 메뉴 클래스 인스턴스 아래 메뉴 추가.

    document.getElementById("menus").addEventListener("click", function(event) {

        const button = Button.tryToGetButtonFromTarget(event.target);

        if (!button)

            return;

        button.executor(event.target); // 버튼 클래스의 메소드 실행함

    });

    document.getElementById("menus").addEventListener("input", function(event) {

        const value = event.target.value;

        const output = event.target.parentElement.querySelector("output");

        output.value = output.alt * value; // 구메 메뉴에서 구배 판매 수량을 바꾸며 ㄴ나오는 것으로 확인. output 태그가 있다.

    })

}

```

3. loadGame

```javascript

export default function loadGame() {

  loadListeners(); // 리스너 로드

  new Map(); // 맵 그리기 시작
   

function loadListeners() {
  document.addEventListener("contextmenu", (event) => {
    event.preventDefault(); // 오른쪽 버튼 비활성화
  });
  
  document.addEventListener("animationend", (event) => {
    if (event.target.classList.contains("resourceCollectedAnimation"))
      return event.target.remove(); // 자원 표시 뜨고 없애기
  });
  
  document
    .getElementsByClassName("left-item")[0]
    .addEventListener("click", function () {
      Menu.getMenu("menu-settings.html").displayMenu();
    }); // 메뉴 띄우기
    
  document
    .getElementsByClassName("right-item")[0]
    .addEventListener("click", function () {
      Menu.getMenu("menu-shop.html").build().displayMenu();

    }); // 상점 메뉴 띄우기

  document.addEventListener("mousemove", Listeners.mouseMove);
  document.addEventListener("mousedown", Listeners.mouseDown);
  // 마우스 컨트롤 이벤트

  TOOLBAR_CATEGORY.CROP.addEventListener(
    "mousedown",
    Listeners.mouseDownToolBar // 작물모양으로 커서 바꾸기
  );
  TOOLBAR_CATEGORY.FENCE.addEventListener(
    "mousedown",
    Listeners.mouseDownToolBar // 펜스 모양으로 커서 바꾸기
  );
  }
}

```

4. new Map()

```javascript

// 맵 크기에 따라 스퀘어의 숫자를 정하는 방식. 다음에 쓸만함.
constructor{
  let result = getPercent(screen.width, mapWidth);

        Map.map.style.width = result - (result % globalSize) + "px";

        result = getPercent(screen.height, mapHeight);

        Map.map.style.height = result - (result % globalSize) + "px";

  

        this.squaresPerRow = Math.floor(Map.map.clientWidth / globalSize);

        this.numRows = Math.floor(Map.map.clientHeight / globalSize);
        
        this.#mapGenerator()
}



```

```javascript

#mapGenerator() {

        const start = performance.now(); // 오래 걸릴만한 것 시간 측정.

        const naturalSpawnableElement = Element.elements.filter((elem) => elem.naturalSpawnChance);

        for (let x = 0; x < this.numRows; x++) {

            for (let y = 0; y < this.squaresPerRow; y++) {

                const square = document.createElement('div');

                square.classList.add('square');

                if (this.#isCorner(x, y))

                    addImgToSquare(square, Element.getElementFromId("ground_corner").getImage());

                else if (this.#isBorderOfMap(x, y))

                    addImgToSquare(square, Element.getElementFromId("ground_side").getImage());

                else {

                    addImgToSquare(square, Element.getElementFromId("ground").getImage());

                    if (Math.random() * 100 <= naturalGeneration) {

                        this.#generateElement(square, [...naturalSpawnableElement]);

                    }

                }

                const img = square.querySelector('img');

                img.style.transform = this.#rotateCalculation(x, y);

                this.#addSquare(square);

            }

        }

        console.log(`Time to load the map: ${performance.now() - start} ms`);

    }

    
```

**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::
- [GamerFarmerJS](https://github.com/AliHaine/GameFarmerJS)

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see:: 

**Terms**

- [output 태그](https://www.w3schools.com/tags/tag_output.asp) -  input에 의한 계산 결과를 보여주기 위한 semantic tag
- [contextmenu 이벤트](https://developer.mozilla.org/en-US/docs/Web/API/Element/contextmenu_event) 오른쪽 버튼으로 나오는 컨텍스트 메뉴 이벤트 리스너라고함
- [마우스이벤트 모던js](https://ko.javascript.info/mouse-events-basics) 여기서 확인해볼 것

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
**