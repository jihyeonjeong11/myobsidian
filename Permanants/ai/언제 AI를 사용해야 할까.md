---
tags:
  - type/sketchnote
  - type/note
  - theme/ai
aliases: 
lead: 계속해서 논쟁이 되고 있는 주제이고, 자신의 경험에 따라 쓰는 것이 좋겠지만 여기서는 화자의 경험에 따라, 쓰지 말아야 하는 경우를 정리함.
visual: "![[AIBUILDS.jpg]]"
created: 2025-05-25, 10:43
modified: 2025-05-25, 10:43
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-25T14:35
---

[[When should you let AI write your code]]
# 개발자는 언제 AI를 사용해야 할까?

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>



> [!Summary]
> `= this.lead`

**Details**

최근 사이드 프로젝트를 진행하며 AI의 도움을 받아 MVP 사양을 설정하고, 실제 코딩을 진행한 적이 있다. 나로써는 아주 큰 도움이 되었다.
하지만 AI에게 의존하는 개발자는 어떤가? 문제를 해결해야 하는 사람이 그 문제를 AI에게 떠넘긴다면?

관련 주제를 조사하며 나와 비슷한 고민을 가진 다른 개발자의 의견을 정리하며 괜찮은 경우와 괜찮지 않은 경우를 나누어 보았다.

**AI 사용 여부를 고려할 우선 사항**

- 팀적으로 사용한다면 사용 범위를 합의해야 한다. 

### AI를 사용해도 괜찮은 경우

- 개발자가 이미 구조를 이해하고 있다면, AI가 생성한 코드를 개발자가 직접 리뷰할 수 있을 때.

>- 프롬프트:
>  간단한 로그인 폼 예제를 하나 만들어 보자. react hook form과 zod validation을 사용하고 이메일 형태의 id와 10~12자의 길이에 대문자, 소문자 알파벳이 필요한 비밀번호 스트링 두 가지를 받을거야. 인풋 둘과 제출 버튼이 있고 인풋 아래에는 처음 상태에서는 밸리데이션이 실패할때까지 보이지 않는 에러 메시지가 있어....

- 결과물이 개발자의 이해를 돕고 흥미를 돋구어 주는 경우 (당연하지만 크로스체킹이 필요하다.)
> - 프롬프트:
> 자바스크립트로 간단한 게임을 만들고 싶어. 마리오와 같은 플랫포머 게임을 만들고 싶은데, 그렇다면 먼저 2d 화면에 캐릭터와 오브젝트가 필요하고, 캐릭터의 상하좌우 움직임이 필요할 것 같아. 이 외에도 무엇이 필요한지 알려줄 수 있어?

### 괜찮지 않은 경우

- 구현하고자 하는 기능에 대한 이해가 없을 때
- 코딩의 즐거움을 뺏어가는 경우
- 보안상 위험이 있을 경우

 개발자의 '흥미'와 '이해'를 돕는다면 AI는 최고의 툴이 될 수 있다고 생각한다. 도구를 어떻게 쓰는지는 결국 인간에게 달려 있다.


**Supporting Content**

- 

---
# Back Matter

**Source**

- based_on::

**References**

- see:: [When should you let AI write your code](https://www.youtube.com/watch?v=ADF_4PAqWrI&t=22s&ab_channel=WebDevCody)
- [# AI is tremendously helpful but it’s taking the joy out of programming](https://www.reddit.com/r/webdev/comments/1ffw9lh/ai_is_tremendously_helpful_but_its_taking_the_joy/)

**Terms**

- 

**Target**

- used_in::

---
**Tasks**

- 

**Questions**

- question::

---
**Template Help**

- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)
- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)
- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)
- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)
- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)
- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)