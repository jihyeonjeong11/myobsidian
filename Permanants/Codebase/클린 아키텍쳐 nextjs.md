---
tags:
  - type/sketchnote
  - type/note
  - theme/structure
aliases: 
lead: 클린 아키텍쳐를 수용한 프로젝트 템플릿을 통해 앞으로의 사이드 프로젝트의 개발 속도를 높일 수 있다.
visual: "![[clean-structure.jpg]]"
created: 2025-04-17, 19:16
modified: 2025-04-17, 19:16
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-11T20:21
---


# Clean architecture nextjs

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>


> [!Summary]
> `= this.lead`

**Details**
<!-- Main content in body of my note  -->
## 1. clean architecture란 무엇인가?

  

![clean-structure](clean-structure.jpg)

  

"클린 아키텍처는 **Robert C. Martin(일명 Uncle Bob)**이 제창한 개념으로,

비즈니스 로직과 프레임워크를 분리하여 유지보수성을 높이는 설계 방식이다.

핵심 원칙은 **'의존성 방향을 뒤집어(DIP, Dependency Inversion Principle) 핵심 로직을 보호하는 것'**이다."

처음 소규모 프로젝트를 개발한다면 생각할 것이 많지는 않을 것이다. Docs에 따라 api를 정의하고, 데이터베이스와 연결점을 만든 뒤 프론트엔드를 만들어나가는데... 점점 기능이 많아질 수록 이러한 문제들이 발생하게 될 것이다.

1. 컴포넌트 내부에 비즈니스 로직이 방치된다.

2. 프레임워크를 핸들링하는 것과 비즈니스 로직이 합쳐져  재사용이 힘들다.

3. 1,2 때문에 테스팅하는 시간이 길어진다.

4. 팀원 간의 의사소통이 힘들어진다.


이 문제를 해결하기 위해 Clean Architecture가 필요해진다. 코드를 계층화함으로써

  

✅ Seperation of Concerns를 통해 유지보수가 쉽다.

✅ Scale 조정을 하기 용의하다.

✅ 비즈니스 로직을 최대한 고립하여 둠으로써 테스팅이 쉬워진다.

  

위의 사항을 염두에 두면서 위 프로젝트를 스터디해보기로 하였다.

## 2. 폴더 구조

  

위 다이어드램에 따라 프로젝트의 폴더 구조와 어떤 레이어가 있는지 확인해 보자.

  

```

src/ // app router를 사용하고 있지만 구분을 용이하게 하기 위해 사용

├─app

│  ├─api

│  │  └─auth

│  │      └─[...nextauth]

│  ├─dashboard

│  │  └─_actions

│  └─new

├─components

│  └─ui

├─data-access

│  └─items

├─db

├─lib

└─use-cases

    └─items

```

  

1. db - Data-access 레이어. db의 테이블 스키마와 db 인스턴스를 구동하는 로직.

2. data-access - Data-access 레이어. db와 use-case간의 데이터 전달을 담당.

3. use-cases - Business layer. 비즈니스 로직. data-access와 next 서버 액션 간의 데이터 전달을 담당.

4. app - Presentation layer. UI부분 및 유저의 액션으로 일어나는 요청, 서버 액션을 담당

5. components - presentation layer. 재사용되는 UI 쪽의 컴포넌트들

6. lib - 외부 라이브러리 사용 코드 및 하나가 하나의 모듈이 될 수 있는 코드들

7. api - 외부 api를 사용하는 부분(OAuth, 결제 등등...)

으로 나누어져 있다.

만약 nextjs에서 db 연결을 하지 않고 react-query를  사용한다면, lib 식에 추가하는 식으로 할 수 있을 것이다.

## 3. 데이터 플로우

  

![data-flow](data-flow.webp)

  

위 구조로부터 파생되는 데이터 플로우는 다음과 같다.


1. 리액트 컴포넌트(presentation layer)로부터 유저의 액션이 일어난다.

2. 컴포넌트 내부에서 서버 액션을 호출한다.

3. 서버 액션에서는 유저의 인풋을 validate 후 비즈니스 레이어의 use-case를 호출한다.

```typescript

// app\(main)\(auth)\sign-in\email\actions.ts

import { getCurrentUser, setSession } from "@/lib/session"; // 개발자님은 세션 핸들링은 추후 deploy 시 외부 클라우드에서 핸들링할 가능성이 높으므로, lib에서 사용했다.

import { signInUseCase } from "@/use-cases/users"; // 비즈니스 로직 호출

...

export const signInAction = unauthenticatedAction

  .createServerAction()

  .input(

    z.object({

      email: z.string().email(),

      password: z.string().min(8),

    })

  )

  .handler(async ({ input }) => {

    await rateLimitByKey({ key: input.email, limit: 3, window: 10000 });

    const user = await signInUseCase(input.email, input.password);

    await setSession(user.id);

    redirect(afterLoginUrl);

  });

  

```

4. use-case 펑션에서 data-access 내부의(data-access layer)의 펑션을 호출, DB 조회를 포함한 비즈니스 로직을 수행한다.

```typescript

// \use-cases\users.tsx

import {

  getUserByEmail,

  verifyPassword,

} from "@/data-access/users"; // session은 lib에서 다루지만 user는 자체 데이터이므로 data-access 레이어에서 선언되었다.

...

export async function signInUseCase(email: string, password: string) {

  const user = await getUserByEmail(email);

  

  if (!user) {

    throw new LoginError();

  }

  

  const isPasswordCorrect = await verifyPassword(email, password);

  

  if (!isPasswordCorrect) {

    throw new LoginError();

  }

  

  return { id: user.id }; // use-case와 액션 간 DTO 형식으로 소통

}

...

```


```typescript

// \data-access\users.ts

import { database } from "@/db";

import { users } from "@/db/schema";

...

export async function getUserByEmail(email: string) {

  const user = await database.query.users.findFirst({

    where: eq(users.email, email),

  });

  // data-access 레이어에서는 디비 호출하는 로직만을 선언한다. 유저 데이터 검사는 business layer인 유즈케이스 내부에서 실행한다.

  return user;

}

...

```

5. 4,5의 과정을 거쳐서 받은 리턴값을 validate한 뒤 서버 액션에서 컴포넌트로 리턴한다.

6. 컴포넌트에서 해당 데이터를 드로우한다.

유의할 점은 다음과 같다.

1. presentation layer의 서버 액션에서는 데이터 자체의 타입을 검사한다.(validation)
2. business layer에서는 해당 앱에서 규정한 규칙을 검사한다. e.g.)로그인 조건은 해당 앱의 특수한 비즈니스 로직이라고 볼 수 있으므로 use-case 내부에서 체크한다.
3. [DTO - Data transfer object](https://en.wikipedia.org/wiki/Data_transfer_object)의 사용.

- 데이터를 각 레이어에서 필요한 정보만 포함하는 형식으로 변환하여 전달하는 방식이다. 이는 불필요한 데이터 전달을 방지하고, API와 유즈케이스 간 의존성을 줄이는 역할을 한다.

## 6. 결론

  

개발자 이 템플릿은 1인 개발로 Saas를 만들기 위해 설계되었다. 앞으로 해당 템플릿을 직접 사용하면서 실제 생산성에 어떤 영향을 미치는지 확인해보도록 할 예정이다.



**Supporting Content**
<!-- Supporting content in tail of my note  -->
- [DTO - Data transfer object](https://en.wikipedia.org/wiki/Data_transfer_object)

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::[WDC-Starter-kit](https://github.com/webdevcody/wdc-saas-starter-kit)

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see:: [Uncle Bob's clean structure](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
  https://gumroad.com/d/d4921cd7dd380c6757b47058f5be99d0

**Terms**
<!-- Links to definition pages. -->
-  [DTO - Data transfer object](https://en.wikipedia.org/wiki/Data_transfer_object)

**Target**
<!-- Link to project note or externaly published content. -->
- used_in:: [Ai-chatbot](https://ai-gemini-chatbot-pearl.vercel.app/chat)

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