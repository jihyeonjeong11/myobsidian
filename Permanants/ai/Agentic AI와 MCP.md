---
tags:
  - type/sketchnote
  - type/note
  - theme/ai
  - type/draft
  - type/experiment
aliases: 
lead: 실험적으로 Agentic AI 개념을 도입해 본다. 얼마나 발전할까?
visual: "![[AIBUILDS.jpg]]"
created: 2025-04-20, 16:50
modified: 2025-04-20, 16:50
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-23T14:21
---

[[Model_Context_Protocol]]

# AI brainstorming - draft

```dataviewjs
dv.paragraph(dv.current().visual);
```

A photo by [Gerard Siderius](https://unsplash.com/@siderius_creativ) from [Unsplash](https://unsplash.com/)

> [!Summary] > `= this.lead`

최근 Agentic AI, MCP가 화제다. 소프트웨어 개발 방식을 근본적으로 바꿀 수 있는 기술이라고 한다. 지금 사용하고 있는 방식만으로는 부족한 것일까? MCP 프레임워크를 통해 Agentic AI를 사용해보며 얼마나 혁신적인지, 생산성을 끌어올릴 수 있는지 확인해 보자.

내가 처음 LLM를 사용했을 때가 기억난다, 베타 서비스 중인 chatGPT에 접속해 리액트로 카운터 앱을 만들어달라고 프롬프트를 넣고 결과에 신기해 했었던 것이 바로 몇 년 전이다.

그러나 최근에는 AI의 뉴스를 볼 때마다 이런 게 가능하다고? 라고 생각할 정도가 되었다. 최근의 MCP와 Agentic AI에 관한 소식도 그렇다.

**Agentic AI, MCP란?**

> [Nvidia 블로그](https://blogs.nvidia.com/blog/what-is-agentic-ai/)에 따르면
> Agentic AI - Which uses sophisticated reasoning and iterative planning to autonomously solve complex, multi-step problems.
>
> Agentic AI - 복잡한 추론 과정과 반복적인 계획을 통해 복잡하고, 여러 단계의 문제를 자율적으로 해결하는 인공지능
>
> MCP - Agentic AI를 사용하기 위한 프레임워크

여기서 핵심은 '자율적으로' 여러 단계를 자체적으로 해결해 주는 AI라고 생각한다.

기존 LLM을 쓰는 방식과 비교해보자.

> [!생성형 AI(Generative) 와 Human in Loop 스타일]
>
> 나 - 리액트로 카운터 앱을 만들어줘
> AI - 코드베이스
> 나 - 스타일은 테일윈즈를 사용하는 것으로 바꿔줘
> AI - 수정된 코드베이스
> 나 - 이 스테이트 로직은 훅으로 다른 파일로 빼줘
> AI - 수정된 코드베이스
> 이런식으로 반복된다!

따라서 이렇게 프롬프트를 인간이 조정해줄 필요가 없다는 것인데, 지금 상황에서 얼마나 사용할 만 할까?


참고로 이 프로젝트에서 모든 프롬프트는 영어로 작성했다.

1. 기술 용어: 'WebSocket', 'Real-time Updates' 핵심 용어들은 영어로 진행하는 것이 연관된 서치를 진행하는 데 수월하다.

2. AI 모델의 이해도: 한글로 프롬프팅하는 것도 퀄리티가 많이 개선되었지만 여전히 영어가 더 나은 답변을 제공한다.

**Sequential Thinking**

현재 MCP 중 가장 인기있다는, 구조적인 사고를 대신해준다는 Sequential Thinking을 통해 직접 체험해 보자. 카운터 앱보다는 좀 더 복잡한 예시를 보기 위해서 리얼 타임으로 변하는 주식 가격 대쉬보드를 의뢰해보기로 했다.

> [!prompt]
> Describe me the process to build real time stock dashboard and code snippet. I will use typescript.
> [!answer]
>
> 1.  Real-time Updates
>
> - WebSocket, SSE service for live price updates
> - Efficient subscription management
> - Automatic cleanup on component unmount
>
> 2.  State Management
>
> - Centralized Redux store
> - Type-safe actions and reducers
> - Efficient updates with Redux Toolkit
>
> 3.  Interactive Charts
>
> - Professional-grade charting with TradingView
> - Responsive design
> - Candlestick chart with customizable timeframes
>
> 4.  Watchlist Management
>
> - Add/remove symbols
> - Real-time price updates
> - Visual price change indicators
>
> 5. Modern UI
>
> - Clean, dark theme design
> - Responsive layout
> - Loading states and error handling

웹소켓, SSE를 제시함으로써 코어 기능을 충분히 파악할 수 있는 것은 좋다. 하지만 프론트엔드의 시각만 존재한다는 점이 아쉽다. 조금 더 다양한 시각에서 조언을 들을 수 있다면 더 좋을 것 같다.

**Memory**

해당 MCP는 사용자의 컴퓨터 로컬 공간에 참고할 만한 컨텍스트를 생성하고, 저장한 뒤 조회하는 기능을 한다. 처음 이 기능에 대해서 들었을 때는 [Multi-Persona prompting]()(https://www.prompthub.us/blog/exploring-multi-persona-prompting-for-better-outputs)을 사용할 때 좋을 거라고 생각했다.

Multi-Persona prompting이란, AI 역시 하나의 복잡한 문제를 해결하는 것 보다는 그 문제를 자잘하게 쪼갠 여러 개의 작은 문제를 더 쉽게 해결한다는 개념에서 출발해서 대답하는 개체를 하나 이상으로 추가하는 것이다.

```
'이제부터 너는 풀스택 개발자야. 하나의 MVP 앱을 만들어 보자. AWS의 EC2 공간에 장고 프로젝트를 하나 만들어서 올리는거야. DB는 RDS로, 파일시스템은 S3를 사용하고 프론트엔드는 리액트로 하자 이걸 한 3일 정도의 스크럼을 진행하도록 시간 단위로 태스크를 짜줄 수 있을까?'
```

이런 식으로 사용하는 법에 익숙해졌지만, 메모리를 통해서 하나 이상의 롤을 사용할 수 있다면 어떨까?

![memory](memory.png)

현재 컴퓨터에 저장된 롤들은 6개이다. 데브옵스, 디자이너, 프론트엔드, 백엔드, 프로덕트 메니저, 테크 라이터인데, 위의 프롬프트를 조금 수정해서 해당 페르소나가 생각하기에 필요한 것들을 나열해 달라고 할 수 있다.

> Prompt: List tasks need to be done by roles to make MVP version of real time stock dashboard project.
> 
> 1.Product Manager Tasks
>  **Define MVP requirements and success metrics**
> - Specify minimum viable stock data points needed
> - Define core user stories and acceptance criteria
> - Set performance benchmarks (e.g., max acceptable latency)
> ...
> 
> 2. Frontend Developer Tasks
> 
> Set up React + TypeScript project structure
>
> Implement core components:
>
> - Real-time stock price display component
> - Basic time-series chart using D3.js
> - Authentication forms
>
> Implement WebSocket connection using Socket.io-client
> ...
>3. Backend Developer Tasks
 - Set up TimescaleDB for time-series data:  
 >- Basic schema design  
 - Essential indexes
>...
>5. Security
>- API rate limiting 
>...



Sequential thinking만을 사용했을 때보다 더 다양한 시각으로 프로젝트를 쪼갤 수 있었다. 실제로 해당 방식으로 앱을 만들어낼 수 있는지 확인하는것도 흥미로울 것이다.

과연 처음 ChatGPT가 소개되었을 때의 호들갑처럼, 하나의 프롬프트만으로 완성된 앱을 만드는 것이 가능해지는 시대가 올까?

---

# Back Matter

**Source**

<!-- Always keep a link to the source- -->

- based_on::

**References**

<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->

- see:: [multi-agent llm](https://www.superannotate.com/blog/multi-agent-llms)
- [reddit post](https://www.reddit.com/r/LocalLLaMA/comments/14t072j/best_approach_to_multiparty_conversions/)
- [Generative ai vs Agentic ai](https://www.ibm.com/think/topics/agentic-ai-vs-generative-ai)

**Terms**

<!-- Links to definition pages. -->

- AI Model
- MCP
- Generative AI
- Agentic AI
- LLM

**Target**

<!-- Link to project note or externaly published content. -->

- used_in::

---

**Tasks**

<!-- What remains to be done with this note? -->

- **Questions**

<!-- What remains for you to consider? -->

- question:: 아니 퍼플렉시티와 같이 완성품이 있는데, 굳이 연구해서 MCP를 써야 하나?
  -> 내가 커스텀할 수 있는 것이 중요한 게 아닐까/

---

**Template Help**

<!-- Links to external help pages on GitHub. -->

- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)
- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)
- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)
- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)
- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)
- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)
