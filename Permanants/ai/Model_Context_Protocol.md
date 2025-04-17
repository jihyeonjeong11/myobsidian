---
tags:
  - type/note
  - type/technical
  - theme/ai
aliases: 
lead: Understanding Model Context Protocol (MCP)
visual: "![[diagram.png]]"
created: 2024-03-21
modified: 2024-03-21
template_type: Note
template_version: "1.35"
license: © 2024 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-16T21:01
---

# Model Context Protocol

```dataviewjs
dv.paragraph(dv.current().visual);
```

<small>_Zoom: [[]] | Edit: [[]]_</small>

> [!Summary]
> Model Context Protocol (MCP) is a framework for agentic AI that enables better context handling and tool integration, primarily supported by Claude.

**Details**

<!-- Main content in body of my note  -->

## 1. Context is all.

기존 생성형 ai들은 제공하는 컨텍스트의 한계가 있었다.
이런 쿼리를 생각해 보면

```
Have a look at my SQLite database and make sure that the sum of all the orders is correct and matches what's in my presentation.
```

기존 생성형 ai에서는 데이터베이스를 보는 것 자체가 불가능하기 때문에 위 프롬프트에 대한 답을 정확해 낼 수 없을 것이다.

LLM -> SQLite -> Presentation Implementation 순으로 접근해야 한다는 것

여기서 mcp의 역할은 해당 모델에 위 db와 presentation코드 즉 context를 제공하는 역할이 된다.

![diagram](diagram.png)

구조도는 다음과 같다. 하나의 mcp 클라이언트에서 데이터 소스 하나 당 서버를 하나씩 돌리는 것.
위에서는 두개의 서버가 필요할 것이다. 만약 인터넷 연결이 필요하다면 세개.

## 2. Context Type

1. Tools
   모델이 해당 컨텍스트에 접근할 수 있게 해주는 펑션.
2. Resources
   모델이 직접 분석하는 컨텍스트 ex)프레젠테이션 파일들
3. Sampling
   모델이 다른 모델에게 쿼리할 수 있는 것?
4. Prompts
   1,2,3을 합쳐서 클라이언트가 모델에게 요청하는 것

![diagram2](diagram2.png)

## 3. Protocol

![diagram3](diagram3.png)

mcp 클라와 서버 통신간에 사용

### 3-1. Reflection Request를 핸들링하기 위해 사용(json-RPC)

간단하게 말하면 클라이언트가 프롬프트를 생성하기 위해 서버에 컨텍스트에 관한 툴과 리소스를 요청하는 것

### 3-2. Mcp Transport

https://modelcontextprotocol.io/docs/concepts/transports

기존 graphQL, REST GRPC와는 다른 방식을 사용

위 링크에서 소개하는 두 가지의 빌트인은 아래 두가지이다

- Standard Input/Output (stdio) 기존 폼을 사용한 전통적인 통신
- Server-Sent Events (SSE) 요청받은 컨텍스트를 클라이언트에 쏴주기 위한 서버에서 invoke하는 응답

## 4. 서버 직접 만들기?

## 5. 프로토콜 비교

- graphQL: Reflection은 있지만 Tool을 커스텀으로 적용해야 함
- REST, GRPC: Reflextion이 없음 Tool도 커스텀으로 적용해야함

## 6. 유의점

- mcp는 기존 백엔드를 대체하는 용도가 아닌 모델 활용을 위해 첨가하는 용도이다. 다른 프로토콜을 대체하지 못한다.
- 하나의 용도로 사용할 수 있도록 유즈 케이스를 정립하라
- 추상화시켜 사용하자.
  -> 위와 같은 프롬프트를 사용할경우, 서버에서 디비의 풀 액세스를 주는 대신 필요한 테이블 하나만을 제공하는 식으로 사용.

**Supporting Content**

<!-- Supporting content in tail of my note  -->



---

# Back Matter

**Source**

<!-- Always keep a link to the source- -->

- based_on:: [Jack Herrington's MCP Video](https://www.youtube.com/watch?v=VChRPFUzJGA&t=176s&ab_channel=JackHerrington)

**References**

<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->

- see:: [Model Context Protocol Quickstart](https://modelcontextprotocol.io/quickstart/server)

**Terms**



**Target**


- used_in:: 

---

**Tasks**



- [ ] Add implementation examples
- [ ] Research more use cases
- [ ] Compare with other context management solutions

**Questions**

<!-- What remains for you to consider? -->

- question:: How to implement MCP in existing projects?
- question:: What are the performance implications of using MCP?

---

**Template Help**

<!-- Links to external help pages on GitHub. -->

- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)
- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)
- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)
- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)
- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)
- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)
