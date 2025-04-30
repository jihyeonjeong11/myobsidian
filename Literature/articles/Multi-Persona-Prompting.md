---
tags:
  - type/sketchnote
  - type/note
  - theme/ai
  - type/material
aliases: 
lead: 기존의 Single Persona Prompting의 한계를 극복하기 위한 Multi-Persona 접근법의 장점과 실제 적용 사례 분석
visual: "![[personamask.jpg]]"
created: 2025-04-21, 10:12
modified: 2025-04-21, 10:12
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-21T19:17
---

[[Agentic AI와 MCP]] [[single-agent ai vs multi agent ai]]

# Multi-Persona-0

```dataviewjs
dv.paragraph(dv.current().visual);
```

Photo by [Llanydd Loyd](https://unsplash.com/@llanydd) / [Unsplash](https://unsplash.com/?utm_source=ghost&utm_medium=referral&utm_campaign=api-credit)

> [!Summary] > `= this.lead`

**Details**

이미 1년~2년 정도 된 개념이기는 하지만 Multi-Persona-Prompting에 대해서 먼저 정리를 해둔다. 추후 이 개념을 기반으로 MCP 사용에 관해 더 확장시킬 수 있다.

- 일반적으로 사용하는 LLM은(Single Persona Prompting) 유저와 AI로 나뉘어져 유저의 인풋을 받아 AI가 무언가를 생성하는 방식,
- 이와는 다르게 유저와, 유저의 인풋을 하나가 아닌 여러 개의 인격이 처리하는 것을 말한다.
- 해당 인격은 유저가 설정하기 나름이다. 과학자, 소설가... 원하는대로 설정할 수 있다.

## 핵심 개념

1. Single vs Multi Persona 비교
2. 작동 원리
3. 실제 사용 사례

## 장점과 한계

1. 장점
   - 다각적 분석
   - 편향성 감소
   - 깊이 있는 토론
2. 한계
   - 리소스 소비
   - 복잡성 증가
   - 일관성 관리

> [!만드는 예시]
>
> Save this entity and act as that.
>
> [structure]
> description:
> traits:
> Example Prompt:
> Use cases:
>
> [!Persona Examples] >
> **프롬프트 엔지니어**
> Description: Interested in the latest tech trends, gadgets, software, and breakthroughs in the tech industry.
> Traits: Curious, Tech-Savvy, Forward-Thinking
> Example Prompt: Act as a Tech Enthusiast: Summarize the key advancements in AI over the past decade.
> Use Cases: Product Reviews, Tech News Summary, Software Recommendations, Gadgets Unboxing, Coding Tutorials
>
> 1.  **시스템 아키텍트**
>
> - Description: 시스템 설계 전문가
> - Traits: 분석적, 구조적 사고, 확장성 중시
> - Use Case: 아키텍처 리뷰, 기술 스택 선정
>
> 2.  **보안 전문가**
>
> - Description: 사이버 보안 전문가
> - Traits: 의심많은, 세부적, 위험 중심
> - Use Case: 보안 취약점 분석, 위험 평가
>
> 3.  **UX 리서처**
>
> - Description: 사용자 경험 전문가
> - Traits: 공감적, 사용자 중심, 관찰력
> - Use Case: 사용성 평가, 사용자 피드백

**Supporting Content**

<!-- Supporting content in tail of my note  -->

- ***

# Back Matter

**Source**

<!-- Always keep a link to the source- -->

- based_on::

**References**

<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->

- see::
[Illinois University Study](https://arxiv.org/pdf/2307.05300)
[Article from PromptHub](https://www.prompthub.us/blog/exploring-multi-persona-prompting-for-better-outputs)
[Medium article](https://medium.com/@neonforge/supercharged-ai-assistant-multi-personas-prompting-in-chatgpt-expert-tip-for-custom-20ec573a1d8d)
[Reddit post](https://www.reddit.com/r/ChatGPTPro/comments/11v04tw/collection_of_chatgpt_persona_prompts/)
**Terms**
<!-- Links to definition pages. -->
- **Target**

<!-- Link to project note or externaly published content. -->

- used_in::

---

**Tasks**

<!-- What remains to be done with this note? -->

- **Questions**

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
