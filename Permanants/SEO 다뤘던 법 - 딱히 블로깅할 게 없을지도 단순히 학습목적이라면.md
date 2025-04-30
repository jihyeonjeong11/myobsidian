---
tags:
  - type/sketchnote
  - type/note
  - theme/business-insight
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[seo2.jpg]]"
created: 2025-04-28, 08:44
modified: 2025-04-28, 08:44
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-30T11:15
---

# SEO 다뤘던 법

<!-- My sketchnote if available -->

```dataviewjs
dv.paragraph(dv.current().visual);
```

A Photo by [Myriam Jessier](https://unsplash.com/@mjessier?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash) on [Unsplash](https://unsplash.com/photos/person-using-macbook-air-on-white-table-VHXiGXxwOQ4)

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary] > `= this.lead`

**Details**

- 주로 RN 개발을 메인으로 해왔었기 때문에 상대적으로 웹 개발에서 제대로 고민해보지 않은 분야, SEO에 대해서 정리해보려고 한다.

### SEO란 무엇인가?

> [!MDN]
>
> SEO(Search Engine Optimization)이란 검색 엔진의 검색 결과에 자신의 웹 사이트를 더욱 자주 노출시키기 위한 프로세스이며, Improving Search Rankings라고도 불린다.

- 앱 개발에서는 ASO(App Store Optimization)이라는 개념이 존재한다. 주로 구글의 Play Console과 App Store Connect에서 메타데이터를 수정할 수 있었는데, 아무래도 사용자 친화적인 위 콘솔 혹은 파이어베이스에서 변경할 수 있다보니 몇몇 영역, 내가 기억하기로는 딥 링크와 관련된 것들을 제외하면 개발자의 역할이 크지 않았다.

- 이와는 다르게 웹에서는 개발자의 역할이 중요하다고 생각한다. 검색 엔진에서 사이트의 Search Ranking을 관여하는 요소들 중:
  1. Content Quality
  2. **Title, Headings** - 컨텐츠에서 적절한 타이틀, 헤딩 등의 사용.
  3. Backlinks
  4. **User Experience** - 퍼포먼스, 모바일 친화성, 내비게이션 로직
  5. **Technical SEO** - HTML Semantic tag 적절한 사용, Structured data의 제공
  6. Domain Authority
  7. Social Signals
  8. User Engagement Metrics
  9. **Security**

에서 코딩과 떨어질 수 없는 요소들이 존재하기 때문이다. 여기서는 앞으로의 과제로 할 수 있게 개발자가 좋은 어떻게 SEO에 기여할 수 있는지 확인해보고 싶다. 

### Title, Headings

- 모든 페이지가 유니크한 `<title>` 과 `<meta name="description">` 값을 가지도록 하자.
- 특히나 NextJS의 dynamic한 페이지에는 generateMetadata를 이용해서 다이나믹한 데이터를 가지는 제목 및 페이지 설명을 붙여주자.
- `<h1>`은 페이지 당 한번, 그리고 경중에 따라 h 태그를 사용하자.

### User Experience

- Lighthouse 검사를 철저히 하자. 
- Web Vitals 관련 지표인 FCP, LCP, TBT, CLS를 개선한다. 이 부분은 설명하려면 따로 포스트가 있어야 할 것이다.
- NextJS의 이미지 규칙처럼 width, height를 정해줘서 CLS를 최대한 낮추자.
- Accesibility - a11y 규칙을 따르자. 
- 모바일 친화적으로 코딩한다. 모바일 뷰포트 설정, srcset을 통한 모바일용 이미지 서빙 등... 역시 따로 포스트가 있어야 할 듯 하다.
- 사람이 읽기 쉬운 짧은 URL을 사용하자. URL의 nesting을 피하자.

### Technical SEO

- robots.txt를 사용한다. 모든 서브도메인의 크롤링 규칙을 정해준다.
- robots.txt에 sitemap.xml의 주소를 추가해주는 것을 잊지 말자.
- Canonical 메타데이터를 추가해서, 중복된 컨텐츠이지만 다른 URL의 페이지 크롤링을 막아준다.
- `<main>` `<nav>` `<article>` `<aside>` 등의 Semantic 태그를 상황에 맞게 사용하자
- Json-LD 포맷을 사용한 **Structured data**를 제공한다.

### Security

- 필수적으로 https 프로토콜을 사용하자.
- 보안 관련 최신 이슈를 확인하고 대응하자.

모든 항목에 예시를 달 수 없는 것은 실제로 해보지 않았던 것들이 꽤 있기 때문이다. 당연히 앞으로 해나가야 할 과제라고 생각한다.



**Supporting Content**

<!-- Supporting content in tail of my note  -->

- [[SEO 기초]]
- [[SEO - Nextjs]]
- [[SEO 최적화 하는법 - 기초]]

---

# Back Matter

**Source**

<!-- Always keep a link to the source- -->

- based_on::

**References**

- see:: [Quora - How do search engines determine the ranking of websites in search results?](https://www.quora.com/How-do-search-engines-determine-the-ranking-of-websites-in-search-results)
- [Checkbot guide](https://www.checkbot.io/guide/seo/)
- [[SEO 기초]]
- [[SEO - Nextjs]]
- [[SEO 최적화 하는법 - 기초]]
- [[Checkbot SEO guide - for developer!]]
- 

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
