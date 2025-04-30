---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[image.jpg]]"
created: 2025-04-29, 16:26
modified: 2025-04-29, 16:26
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-29T17:50
---
<!--  See "Template Help" below for using properties -->
여기서 필요한 것만 가져와서 블로깅할거임
# Checkbot SEO guide - for developer!
<!--  Clear and descriptive title -->

<!-- My sketchnote if available -->
```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

### Page titles

- 모든 페이지에는 해당 페이지가 무엇인지를 설명하는 확실하고 유니크한 제목이 있어야 함.

> [Google - Create good titles and snippets in Search Results](https://support.google.com/webmasters/answer/35624?hl=en)
> 
> Titles are critical to giving users a quick insight into the content of a result and why it's relavant to their query.

- 여기에는 헤드에 `<title>` 태그가 있어야 한다.
- 구글에서는 10자 60자의 길이를 권장
- 모든 페이지의 타이틀은 유니크해야 한다.

### Page Headings

- `<h>` 태그를 통해 컨텐츠에 일종의 구조를 잡아줘야 한다. 서치 엔진의 이해를 돕는다

> [Google - Similar to writing an outline for a large paper, put some thought into what the main points and sub-points of the content on the page will be and decide where to use heading tags appropriately.](https://developers.google.com/search/docs/fundamentals/seo-starter-guide?hl=en&visit_id=638815092476810907-3025190914&rd=1)
> 
>  Similar to writing an outline for a large paper, put some thought into what the main points and sub-points of the content on the page will be and decide where to use heading tags appropriately. 

- 페이지 하나 당 `<h1>` 태그는 하나씩 쓰는 것을 권장한다.
- `<h1>`태그의 길이는 70자를 넘지 않는 것이 베스트. 또한 유니크해야 한다.
- 이후 주제어의 경중에 따라 h 숫자를 바꿔가면서 쓰는 것이 좋다.

### Page descriptions

- 모든 페이지는 간단하고 확실한 소개문이 있어야 한다.
> [**Google**, “Create good titles and snippets in Search Results”](https://support.google.com/webmasters/answer/35624?hl=en)
>
 Google will sometimes use the meta description of a page in search results snippets, if we think it gives users a more accurate description than would be possible purely from the on-page content. 

- 모든 페이지의 헤드에 유니크한 `<meta name="description" content="Page description.">`을 넣는다.
- description은 100자에서 320자가 베스트
- 모든 description은 유니크해야 한다. 중복되는 것은 좋지 않음.

### Duplicate Content

- 중복되는 내용은 되도록 피해야 한다. 서치 엔진에 혼란을 줄 수 있어 랭킹을 떨어뜨림

>[**Google**, “Consolidate duplicate URLs”](https://support.google.com/webmasters/answer/139066?hl=en)
>
 If you have a single page accessible by multiple URLs … Google sees these as duplicate versions of the same page. Google will choose one URL as the canonical version and crawl that, and all other URLs will be considered duplicate URLs and crawled less often. 

- Canonical URL을 설정하자.
  - `<link rel="canonical" href="...">` 을 통해 같은 내용이지만 다른 URL의 경우 올바른 오리지널 URL 페이지에 이 메타데이터를 넣어서 서치 엔진의 혼란을 줄일 수 있다.
  -  ex) https://mypage.com/recipes/2013 와 https://mypage.com/recipes/2013?utm_source=twitter 두 페이지는 같은 내용이지만, 어디서 왔냐에 따라 다음 패리미터가 붙어서 검색 엔진에서는 다른 페이지로 취급한다 이 경우 전자에 `<link rel="canonical" href="https://mypage.com/recipes/2013">` 이 메타데이터를 넣어서 트위터에서 온 페이지가 불렸을 때도 검색 엔진은 오리지널 페이지의 조회수가 오른 것으로 취급해서 랭킹을 올려주게 된다.
- 그러니 페이지 자체의 컨텐츠도 중복을 최대한 피해야 한다.

### Page Content 

- 페이지 컨텐츠는 고품질이어야 함.
- 이미지의 alt text를 꼭 넣자.
- 모바일 스케일링도 하자. 기본적으로 `<meta name="viewport" content="width=device-width, initial-scale=1">` 요것은 무조건 넣어주자. 모바일로 봤을 때 줌 레벨을 100%로 만들어 준다.
- 해당 페이지를 보기 위해서 특정한 플러그인을 요청하지 말자.

### URL Names

- 모든 페이지는 유니크한 URL 주소를 가져야 한다. 해당 주소는 인간이 읽기 쉬워야 함.
- 짧고 정확한 주소를 주자.
- URL에 언더스코어를 쓰지 말자. `example.com/pc_laptop_reviews` 보다, 하이픈으로 연결하자. `example.com/pc-laptop-reviews`
- 옛날 방식처럼 파일확장자를 URL에 넣지 말자. .html 이런거 다 빼기
- 되도록이면 Query string을 다 빼자. `~com?topic=chicken` 대신에 `example.com/topic/chicken`과 같이 Route Parameter를 쓰자
- URL에 알파벳 의외는 쓰지 말자.
- 대문자 쓰지 말자.
- deep하게 네스트하지 말자. `example.com/community/forum/subforum/food` 이렇게 ㄴㄴ

### Code validation

- HTML, CSS, JS를 제대로 쓰자. 에러 다 제거하기

### Links

- 404 에러 페이지를 만들자. 더 나은 방법은 404 페이지가 나올 일을 없게 하자.
- 외부 링크 확인해서 안나오는 걸 고치자
- css, js 이미지 등 에셋이 에러나는 걸 고치자

### Robots.txt

- Robots.txt에 모든 서브도메인을 체크하자. 사이트맵이 어디있는지도 설정 가능하다.
- 또한 사이트맵의 위치도 이 파일에서 정해줄 수 있다.

### Redirects

- redirect 역시 서치 랭킹에 연관이 있다.
- 302 temporary redirects, 307을 301 permanant redirects로 바꾸자. 그 말은 '임시'적으로 하지 말아야 한다는 것
- meta redirects를 피하자. `<meta http-equiv="refresh" content="5;http://example.com/destination">` 메타데이터에서 이동하도록 하지 말자.


**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::[Checkbot](https://www.checkbot.io/guide/seo/)

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