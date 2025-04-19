---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: 제텔카스텐 방식을 실험적으로 사용해보려 한다.
visual: "![[paper pile.avif]]"
created: 2025-04-17, 19:58
modified: 2025-04-17, 19:58
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-19T19:22
---
[[Zettelkasten use-cases]]

플로우 -> 
집중력을 유지할 것이 필요하다 명상, 금연보다 더욱
How to take smart note 책을 봄
생산성의 비밀: 하나의 태스크를 끈질기게 보는 것보다, 흥미가 떨어지면 다음 것으로 이동하되 다시 돌아왔을 때 시간 낭비 없이 그 태스크에 곧바로 돌아올 수 있도록 한다.
제텔카스텐 방식.
지금까지 나는 뭔가를 기록하는 것을 좋아하지 않았음. 
하지만, 개발에도 앞으로 계속해서 살아남을 무언가가 있을 것임. 내 생각에는 OOP와 같은 프로그래밍 원칙들임. 우리가 시간을 많이 소비하는 것은 결국 OOP의 기반에서 쓰여지는 유즈케이스이므로 뼈대에 대한 개념을 잘 잡는다면 이런 부품들을 적용한 내용을 기록한 것을 업데이트 하는 것은 얼마 걸리지 않을 것임

이후에 직접 옵시디언에서 사용한 방식.

# Zettelkasten-blogging

### 1. 슬럼프를 극복하기 위한 노력

개발자로써 슬럼프를 극복하기 위한 나의 도전은 계속되고 있다. 자신감 및 집중력을 되찾기 위해 여러 시도를 하며 많은 부분 나아졌다고 생각하지만 언제나 새로운 것을 실험하는 것은 언제나 도움이 된다고 생각하기 때문에 이에 대해 고민 중 개발자로써 나 자신의 가장 큰 단점에 대해 다시 돌아보기로 했다.

### 2. 메모하지 않고 커뮤니케이션이 안되는 개발자

다시 고백하자면, 지금까지 나는 개발자로써 무언가를 기록으로 남긴다는 것을 시간낭비라고 생각했다. 경력 대부분 혼자서 개발해 왔기 때문에, 회사의 자산으로 무언가 코드베이스를 남기기보다는 무언가 재작업을 할 때 인터넷에서 최신 예제를 찾아서 돌리면 된다고 생각했기 때문이다. 그 결과, 개발 속도는 빨라졌지만, 팀원들이 생기고 이들과 소통을 할 때 ***내가 개발한 이 프로젝트를 내가 설명하지 못하는 문제가 발생했다. 

지금은 반성하고 최대한 클린 스트럭쳐에 맞게 몇 가지 사이드를 끝마치고 보니, 개발자로써 무언가를 기록하는 방법을 조금 알 것 같은 생각이 든다. 

### 3. 뼈대는 영원하다, 부품만 바뀔 뿐.

OOP, SOLID, Clean Architecture와 같은 개념들은 앞으로도 계속 살아있을 것이다. 개발자가 만드는 앱이라는 것도 결국 이러한 개념을 토대로 쌓아올리는 게 아닌가? 그렇다면, 개발자 나 자신이 해당 개념만 확실히 하면, 그 이하 유즈케이스들(어떻게 SOLID를 만족하는 컴포넌트 구조를 만드는지, 비즈니스 레이어에서 어떤 비즈니스 룰을 가지고 있을지)와 같은 것들은 언제든지 최신화된 무언가로 갈아끼울 수 있는 부품이라고 생각한다. 그렇다면 개발자인 나 자신은 변하지 않는 이 개념과 각각의 유즈 케이스 문서들을 언제든지 업데이트할 준비만 하면 되는 것이 아닐까?

### 4. How to take smart notes

이러한 고민을 하던 중 아래 책에 대해 알게 된다.


![Book cover](smart-note-cover.webp)

이틀 전에는 How to take a smart note 라는 책을 알게 되었다. 해당 책은 [니클라스 루만](https://ko.wikipedia.org/wiki/%EB%8B%88%ED%81%B4%EB%9D%BC%EC%8A%A4_%EB%A3%A8%EB%A7%8C) 이라는 독일의 사회학자에 대한 이야기로 시작한다.

그는 자신만의 생각 기록법으로 독일의 공무원 생활을 하다 교수의 추천을 받고 하버드에서 수학, 이후 사회학 박사 및 교수로써 여러 걸작들을 발표했다고 한다. 해당 책은 이 사람이 어떤 메모 방식을 사용하였는지에 대한 이야기이다.

지금까지 읽은 내용 중 가장 흥미로웠던 내용은 이렇다.

>[!Paragraph]
>
>Luhmann was able to focus on the important things right in front of him, pick up quickly where he left off and stay in control of the process because the structure of his work allowed him to do this.
>
>그는 모든 일을 가장 중요한 순서대로 처리했는데, 그가 정해 놓은 방식 덕분에 멈춰 놓은 일을 다시 시작하는 것이 빨랐고 방향을 잃어버리는 일이 없었다.
>
>The best way to maintain the feeling of being in control is to stay in control. And to stay in control, it's better to keep your options open during the writing process rather than limit yourself to your first idea.
>
>여러 일을 처리하며 길을 잃지 않는 방법은 한 가지 생각에 매몰되지 않는 것이다. 바로 여러 해결책에 대 옵션을 열어 놓고 해당 아이디어들을 실험하는 것이다.
>
>

그리고 저자는 루만이 우선순위를 선정하는 방법은 바로 '흥미'였다고 얘기한다. 이것은 한 가지 아이디어만을 고집해서 해당 방법으로 문제를 해결하지 못하는 경우, 자신에 대한 자신감이 떨어지게 되는 [가면 증후군](https://ko.wikipedia.org/wiki/%EA%B0%80%EB%A9%B4%ED%98%84%EC%83%81)을 유발하게 되어 최대한 삼가라고 권하고 있다.

결국 이 책에서 권하는 작업 방식 및 루만의 기록법, Zettelkasten 방식은:

1. 흥미도가 높은 작업부터 시작한다.
2. 흥미가 떨어졌거나, 내 자신의 이해가 부족하다고 생각한다면 해당 부분을 기록해 놓고 다음 아이디어를 서치한다.
3. 다시 1번부터 반복한다.

인데, 해당 책에서는 '해당 부분을 기록'을 어떻게 효율적으로 하는지에 대해 설명하고 있다.

### 2. 옵시디언을 통한 제텔카스텐 방식.

아직 책을 다 읽지 않았지만 1장의 내용을 따라서 내가 시도해볼 만한 방법은 이렇다.:
1. 떠오르는 아이디어는 Fleeting 노트로 기록한다.
2. 무언가를 읽으며 본 인상깊은 정보는 Literature 노트로 기록한다.
3. 1,2를 계속 확인하며 쓸모있는 것을 추려 서치 후 Permanant 노트로 기록한다.
4. Permanant를 기반으로 연결할 수 있는 아이디어를 연결해서 Menuscript로 작성한다.


유의점은 다음과 같다.

1.  하나의 메모는 하나의 아이디어만을 담아야 한다
2. 해당 아이디어에 대한 나의 유니크한 의견이 반드시 필요하다.
3. 아이디어의 연결과 결합을 중요시한다.

기본 스트럭쳐 및 방향성은 다음과 같고, 여기서는 제텔카스텐 방식을 시도하기 위해서 옵시디언 앱을 채택했다.

```
myobsidian
├─Fleetings // 떠오르는 아이디어를 메모
│  ├─Ideas
├─Kanban
├─life
├─Literature // 아티클, 책 관련 메모
├─Permanants // 위 메모에서 서치를 거친 노트
│  ├─ai
│  ├─architecture
│  ├─Codebase
│  └─Zettelkasten
├─Showcases // 옵시디언 사용 예
├─Templates // 옵시디언 템플릿
│  └─unsorted
└─visuals // 노트의 이미지

```

현재 선택한 구조는 위와 같다.

### 4. 결론.

기존에 생각하지 못했던, 노트와 노트간의 연관성을 연결하는 과정을 통해 플로우를 잡고 여기서 새로운 아이디어를 파생한다는 개념이 아주 흥미롭다. 몇 가지 노트를 작성해 보았지만 도입한지 얼마 안된 지금으로써는 아주 재밋게 작성하고 있다. 다만 노트의 숫자가 많으면 많을 수록 시너지가 나는 방식이기 때문에 조급해하지 않고 하루하루 사과나무를 심는다고 생각하고 계속 풍부하게 늘려나가보려고 한다.


플리팅 노트 + 리터러쳐 노트 + 퍼머넌트 노트에 연결

MCP 연결 + MCP 브레인스토밍

https://github.com/jihyeonjeong11/Obsidian-Templates?tab=readme-ov-file 에서 참고,.

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**
<!-- Main content in body of my note  -->
- 

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
- see:: []

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