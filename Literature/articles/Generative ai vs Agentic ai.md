---
tags:
  - type/sketchnote
  - type/note
  - theme/ai
  - type/material
aliases: 
lead: 생성형 AI는 컨텐츠를 만들고 요원형은 특정한 태스크를 처리하는 용도
visual: "![[AIBUILDS.jpg]]"
created: 2025-04-21, 14:14
modified: 2025-04-21, 14:14
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-21T19:17
---

[[Multi-Persona-Prompting]] [[Agentic AI와 MCP]]

# 생성형 ai, 요원형 ai 차이

```dataviewjs
dv.paragraph(dv.current().visual);
```

A photo by [Gerard Siderius](https://unsplash.com/@siderius_creativ) from [Unsplash](https://unsplash.com/)

> [!Summary] > `= this.lead`

**핵심 정리**

- Agentic AI - 의사결정, 자동화에 사용
- Generative AI - 컨텐트 생성에 사용

**Agentic AI란?**

AI 모델의 한 종류이다. 특정한 액션을 자율적으로 하는 것이 중점이다.,
생성형 AI는 글, 이미지 와 같은 컨텐츠를 만들어주지만, Agentic ai는 특정한 목표가 주어지면 주어진 자원을 사용해 이것을 해결하는데 도움을 주게 된다. 인간의 인풋은 목표로만 작용하고, 문제를 해결하는 과정은 AI가 직접 진행한다. 인간은 이 설정값을 수정해서 이 과정을 바꿀 수 있다.

**Agentic AI의 특징**

- Autonomy: 해당 목적을 자율적으로 수행한다. 생성형과는 다르게, 인풋을 바꾸면서 조정할 필요가 없다.
- Goal-oriented behavior: 특정한 목적을 수행하기 위해 존재한다. 생성형처럼 모든 인풋을 다 처리할 수는 없고 정의된 목적에 대해서만 사용가능하다
- Interactivity: 주어진 자원에 따라 다른 반응이 나온다.

> [!Fun Facts] > **Fun fact:** Unlike traditional AI models that passively respond to inputs, agentic AI can actively plan, take actions, and adapt to new information, almost like a digital intern that never sleeps!💡

**Agentic AI 예시**

- 시리, 알렉사와 같은 AI는 인풋만을 기다리는 것이 아니라 특정한 자극에 반응하고 결정을 내려서 유저를 돕는다.
- Robotics: 헬스케어와 같은 분야에서 로보틱스는 유저의 상태가 변경하는 것을 캐치해 필요한 행동을 수행한다.
- 자율주행: 자율주행 차량 역시 Agentic AI의 부분이다.

**Generative AI**

기존 AI 모델이 데이터 처리를 위한 것이었다면(빅쿼리) 생성형 AI는 인간의 창의성을 대체하기 위해 만들어짐. 텍스트 이미지 뮤직 비디오 등, 전통적으로 엄청난 양의 데이터를 주어진 스트럭쳐에 맞게 학습하는 식으로 만들어진다.

**Generative AI 특징**

- 컨텐츠 제작: 주어진 컨텍스트에 따라 여러 형태의 컨텐츠를 만든다.
- DALLE와 같은 DLLM은 텍스트 인풋으로 이미 가지고 있는 이미지 데이터를 활용 이미지를 만들엊냄
- Adaptability: 유저 인풋, 피드백을 통해 더 학습해서 더 정확해진다.

**Generative AI 예시**

- Chatgpt
- DALLE
- Stable Difussion

**Generative vs Agentic AI**

Let's take a closer look at the key differences between agentic AI vs generative AI:

| Aspect             | Generative AI                                                                                                                             | Agentic AI                                                                                                                 |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Definition         | <br>창의적인 컨텐츠를 만드는 역할, 텍스트 이미지 뮤직 비디오                                                                              | AI that performs goal-driven tasks, makes decisions, and acts autonomously in dynamic environments.                        |
| Primary Purpose    | The main goal is to generate content that resembles human-made creations, often used for artistic or communicative purposes.              | Its purpose is to execute tasks, make decisions, and achieve specific objectives, without requiring constant human input.  |
| Core Functionality | Uses large datasets to learn patterns and create new, original content based on those learned patterns.                                   | Analyzes the environment, makes decisions, and adapts actions to meet goals. It's focused on completing tasks efficiently. |
| Technologies Used  | Relies on Generative Adversarial Networks (GANs), and Transformer Models (e.g., GPT, BERT) to produce content.                            | It uses reinforcement learning, decision trees, robotics frameworks, and sensor fusion to interact and perform tasks.      |
| Output Type        | Produces creative content such as articles, music, images, and more. It's output is generally non-functional, meant to inspire or inform. | Delivers functional outputs like navigation decisions, task executions, or problem-solving actions based on context.       |
| Interaction Style  | Generally collaborative, as it works based on prompts, instructions, and input from users to generate content.                            | Fully autonomous; once set up, it acts on its own and doesn't need continuous interaction with humans.                     |
| Strengths          | Excellent at creativity, content automation, and enhancing human innovation by producing large amounts of content.                        | Known for its efficiency, autonomy, and ability to scale in complex, dynamic environments that require decision-making.    |
| Limitations        | Dependent on the quality and range of training data; can produce biased or nonsensical outputs in some cases.                             | Complex to implement and requires careful ethical considerations and safeguards to ensure it makes appropriate decisions.  |

---

# Back Matter

**Source**

<!-- Always keep a link to the source- -->

- based_on::
- [Forbes article](https://www.forbes.com/sites/bernardmarr/2025/02/03/generative-ai-vs-agentic-ai-the-key-differences-everyone-needs-to-know/)
- [Simplilearn](https://www.simplilearn.com/agentic-ai-vs-generative-ai-article)

**References**

<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->

- see::

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
