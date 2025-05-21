---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: 계속해서 논쟁이 되고 있는 주제이고, 자신의 경험에 따라 쓰는 것이 좋겠지만 여기서는 화자의 경험에 따라, 쓰지 말아야 하는 경우를 정리함.
visual: "![[cody.png]]"
created: 2025-05-21, 09:59
modified: 2025-05-21, 09:59
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-21T10:42
---



# When should you let AI write your code



```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>



> [!Summary]
> `= this.lead`

**Details**

**화자가 생각하는 AI를 써도 괜찮을 때**

- 본인이 어떻게 만들 수 있는지 알고 있을 때. 
>- 유저 스토리 -> p태그를 클릭하면 텍스트 에디터가 나오고, 수정하면 success토스트가 나오면서 다시 p 태그로 돌아감.
>- 따라서 AI 코드를 보고 설명이 가능하고 로지컬하면 괜찮음

- 해당 코드가 코어 로직이 아닌 경우
> - 충분히 간단하고, 거기보다 코어 로직을 직접 구현하는데 시간을 쓰는 것이 좋기 때문에

- 보안 관련해서 걱정이 없을 때
- 알고리즘일 경우, 잘 알려진 경우
> - [A* search algotithm](https://en.wikipedia.org/wiki/A*_search_algorithm) 의 경우 몇십년간 검증되었으므로 AI 구현이 문제 없음.
>   화자의 경우 이미 배워왔고 다시 배우는데 문제가 없다고 생각하기 때문에 AI로 게임 알고리즘을 구현하였음

- 코드베이스가 충분히 SOLID할 경우.
> 레이어별 분리가 충분히 되어 있다면 AI코드를 집어넣었을 때 그 스타일에 맞춰서 적어주기 때문(커서같은걸 사용할 때임) 이 경우 [커서 룰](https://tilnote.io/pages/6788859d30f0d55845fbc180)을 넣어주자
> https://github.com/webdevcody/the-writing-platform/blob/main/.cursor/rules/tanstack.mdc 

**내가 생각하는 괜찮을때**

- 아예 모를때 처음부터 시작할 때
- ai로 돌아가는 코드를 받아놓고 docs와 비교하는 것이 괜찮았음




**AI를 쓰면 안될 때**
- 따라서 구현하고자 하는 부분의 로우 레벨 적인 지식이 부족할 때.
- 3d 이펙트를 구현하고 싶은데, 여기서 어떤 라이브러리를 쓰는지 해당 라이브러리가 어떤 알고리즘으로 3d를 구현하는지 몰라서 화자는 60번정도 리프롬프팅을했다고 한다.

**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::
- [Video from Web Dev Cody](https://www.youtube.com/watch?v=ADF_4PAqWrI&ab_channel=WebDevCody)

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