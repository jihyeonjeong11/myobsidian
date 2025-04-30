---
tags:
  - type/sketchnote
  - type/note
  - theme/ai
  - type/material
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[image.jpg]]"
created: 2025-04-21, 16:36
modified: 2025-04-21, 16:36
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-21T18:24
---

<!--  See "Template Help" below for using properties -->

Agentic 시스템이 대두하는 이유

- llm이 더욱 발전하고 있다
  그럼에도 Agentic ai 기업레벨이 없는 이유

- 90% 정도의 정확성이 필요하지만, 아직 여기까지 도달하지 못함
- 필요한 컨텍스트가 방대해서 이를 인간만큼 처리하지 못함
- 기업 데이터는 대부분 정리가 되어있지 않음, ai가 잘 처리하지 못함
- 위 문제로 에이전트가 점점 커지면 이를 핸들링하지 못하게 됨

두번째 링크에서는 마이크로소프트 개발자가 직접 multi agent level의 프로그램을 만들었음
여기서는 4개의 에이전트가 사용되는데

- question answerer
- answer checker
- link checker
- manger
  유저 인풋 ->
  질문 답변하는 사람은 인터넷에서 답을 생성함 -> 엔서 채커는 해당 답이 확실한지 인터넷에서 더블체크함
  링크 체커는 발췌한 정보의 링크가 확실한지 체크함
  매니저는 마지막 답변이 괜찮은지 체크함

여기서 핵심은 에이전트간의 논쟁임. 피드백하는 과정을 확인할 수 있음 그리고 매니저 에이전트는 이를 다시 쓰도록 함.

25개의 인터랙션이 맥스도록 조절했음. 일반적으로 한번, 두번의 iterations에서 앤서가 확정 됨

이걸 곧바로 만들기에는 무리

따라서 간단한 레벨로 만들어 볼만함. -> 뭘 만들지?

# Multi agent systems

<!--  Clear and descriptive title -->

<!-- My sketchnote if available -->

```dataviewjs
dv.paragraph(dv.current().visual);
```

<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary] > `= this.lead`

**Details**

최근 LLM의 급격한 발전으로 인해 Agentic AI 역시도 화두에 오르고 있다.
앞선 포스트에서 확인했듯 Agentic AI의 목적은 어떠한 복잡한 문제를 간단하게 쪼개어서, 태스크 하나하나를 에이전트가 해결하는 방식이다.

지금까지는 생성형 AI ChatGPT와 같은 콘솔을 통해서 개발자들은 human-in-the-loop 방식을 사용해 문제를 해결해 왔고 직접 모델을 다루는 경우라면 파인 튜닝으로 해결했을 것이다.

```

나 - 리액트로 카운터 앱을 만들어줘
AI - 코드베이스
나 - 스타일은 테일윈즈를 사용하는 것으로 바꿔줘
AI - 수정된 코드베이스
나 - 이 스테이트 로직은 훅으로 다른 파일로 빼줘
AI - 수정된 코드베이스
...

이런식으로 반복된다!

```

하지만 Agentic AI의 개념이 대두되면서 위에서 인간이 명령을 내리는 것을 에이전트가 대신할 수 있지 않을까? 하는 기대감이 대두되고 있다.

**한계점**

그럼에도 불구하고 여전히 아직 복잡한 문제에 대해 Agent AI를 적용하기에는 몇 가지 문제점이 존재한다.

1. 90% 정확성 더 높은 정확성이 필요한 문제일 때,
2. 기업에 특화된 데이터를 컨텍스트로 추가할 경우, 효율성이 급감함
3. 기업 데이터는 대부분 정리가 되어있지 않음, ai가 잘 처리하지 못함
4. 위 문제로 에이전트가 점점 커지면 스케일링하기가 힘들어짐.

**어떻게 하는게 좋은가(여러 이론 중에서)**

인간이 loop에 참여하는 비효율을 제거하기 위해서 여기서는 subdomain에 최적화된 subagent를 제안한다. 분업화된 현대의 회사 시스템과 같다.

subAgent를 자세히 설명한다면

- 그들이 관장하는 subdomain을 추상화하는 방안을 가진다.(software engineer 에이전트는 코드베이스의 컴플렉시티를, account executive 에이전트는 특정한 계정들이 유발하는 컴플렉시티 정보를 가진다.)
- 해당 정보를 가지고 subagents들은 서로 소통하게 된다. 이 과정은 자연어로, 인간이 볼 수 있어야 한다.(ticket이나 미팅과 같은 형태로)
- 제출된 해답이 전체 시스템을 교란해서는 안된다(퍼포먼스 리뷰, 멘토쉽, 터미네이션 부분에서)

이런 특성은 위에 설명한 이슈들을 크게 개선해주게 된다

- 복잡한 데이터를 subagent가 처리하면서(하나의 큰 문제를 큰 프롬프트로 처리하는 것보다 여러개의 짧은 프롬프트로 처리하는 것이 더 효율적이다) 사람이 할 시간에 다른 일을 할 수 있게 됨.
- Reliability 모듈화된 subagent로 문제가 발생했을때 돌아갈 수 있고 평가시스템을 통해 subagent가 실패할 가능성이 높은 해결책을 제시하는 것을 막을 수 있다.

이 다음부터 패턴에 따라 작성함 여기서는 하나만 다룸.

![어셈블리 라인 에이전트](Assembly.webp)
**어셈블리 라인 방식**

서브에이전트를 순차적으로 놔두며 하나씩 통과하면서 답을 찾아가는 식.

장점 - 간편함
단점 - 순차적실행이라 중간에서 실패하는 경우 잡아내기 힘들다. 아래 피드백 내용 참조

**예시**

- A basic prompt-to-website builder. The system works in stages, first writing a PRD, then building the site one by one. The final subagents must ensure quality and the right user presentation.
    
    - [user prompt] → Build Site Requirements → Build Frontend Components → Build Frontend → Build Backend Schemas → Build Backend → Perform QA → Documentation → [website]
        
- [Anthropic’s Prompt Chaining, Parallelization](https://www.anthropic.com/research/building-effective-agents)
    
- [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352)
    
- [CrewAI Sequential](https://docs.crewai.com/how-to/sequential-process)
    

**피드백**

- Early stopping — 다음 순차적 처리를 막아주는 개념
    
- Parallelism — 순차적이 아니라 서브에이전트가 동시에 돌아가도록 하는 개념
    
- Self-consistency — 동시에 여러 답변을 생성하고 최고를 선택하도록 하는 것

**추가적인 고려사항**

- 돈이 얼마나 들것인지?
- 이 시스템을 만드려면 어떤 툴과 프레임워크가 필요할까?
- 만약 새로운 개념이 도달했을 경우 바꾸는데 얼마나 들것인가?



**Supporting Content**

<!-- Supporting content in tail of my note  -->

-

---

# Back Matter

**Source**

<!-- Always keep a link to the source- -->

- based_on::[Blog post](https://blog.sshh.io/p/building-multi-agent-systems)
- https://techcommunity.microsoft.com/blog/aiplatformblog/the-future-of-ai-exploring-multi-agent-ai-systems/4226593

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
