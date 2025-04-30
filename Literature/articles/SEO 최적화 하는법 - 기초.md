---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: 이 기초로 NextJS 최적화를 직접 해볼 수 있음
visual: "![[seo.jpg]]"
created: 2025-04-26, 13:51
modified: 2025-04-26, 13:51
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-26T15:57
---
[[SEO 기초]]

# SEO 최적화 하는법

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>



> [!Summary]
> `= this.lead`

**Details**

## Keyword Research(키워드 분석)

- 키워드 분석은 당신의 웹페이지를 유저들이 어떤 검색어로 찾아오는지 확인하는 과정이다.
- 유저들이 어떤 단어를 찾았을 때 당신의 페이지가 나왔는지 확인해서, 해당 검색어와 연관된 더 많은 컨텐츠를 추가하는 식으로 늘려갈 수 있다.
- 예를 들어, 커피샵 페이지를 가진 사람은 '최고의 커피샵'이라는 키워드가 효과적일 수 있지만, 또한 같은 유저들이 '밀크 라떼 파는 곳' 혹은 '근처 커피샵'이라는 검색어 역시 검색했을 수 있기 때문이다.
- 이것을 Search Intent라고 하며 이 것과 연관된 컨텐츠를 추가하는 방식이다. 
- [Keyword Magic tool](https://www.semrush.com/analytics/keywordmagic/start) 툴로 테스트 할 수 있다.

## Quality Content(질좋은 컨텐츠)

- 위 단계에서 유저의 Search intent 및 연관 검색어를 찾았다면 이에 관련한 컨텐츠를 추가해야 한다.

### 검색자는 무엇을 보기 원하는가?

- Search intent의 보충 설명이다.
- 유저가 검색 결과로 이 페이지는 '쓸만하다'라는 느낌을 주는 것을 아래 가이드로 확인할 수 있다.
- [구글 Search Intent 가이드라인](https://services.google.com/fh/files/misc/hsw-sqrg.pdf)에 따르면 유저는 총 4가지의 검색 의도를 가짐
  1. know: 유저는 검색어에 대해 정보를 얻고 싶음
  2. do: 유저는 검색어를 직접 해보고 싶음
  3. website: 유저는 특정 사이트를 찾고 있음
  4. visit-in-person: 유저는 특정한 비즈니스 혹은 카테고리에 방문하고 싶음.

- SEO 관련 종사자들은 이 4가지 카테고리로 나눔
  1. Informational: 정보를 위한 검색
  2. Commercial: 구매를 위해 비교하기 위한 검색
  3. Navigational: 특정한 페이지, 사이트를 찾는 검색
  4. Transactional: 어떤 액션을 위한 검색(무언가를 사기 위해?)

- 이러한 Search Intent를 분류하기 위한 방법은 해당 키워드의 탑 랭킹 페이들을 분석함으로써 알 수 있다.([SERP Analysis](https://www.semrush.com/blog/serp-analysis/)라고 불림.)

- 예를 들어서, how to make a latte at home” 라고 검색했을때의 결과는 다음과 같다.

![latte](latterathome.webp)


- 여기서 탑 랭킹 페이지들과 비슷한 포맷으로 컨텐츠를 추가하는 것이 랭킹 향상에 좋을 것이다.

### 그렇다면 어떻게 하이 퀄리티 컨텐츠를 만들까?

[Hign-Quality content](https://www.semrush.com/blog/quality-content/)란 정확하고, 도움이 되고 레퍼런스가 정확하고, 검색어에 연관되며 유저친화적이면 된다.

- 주제에 잘 맞음
- 컨텐츠 스트럭쳐가 정확함
- 최신화되어 있음
- 학술적인 소스에서 정보를 전개함
- 그림 활용 잘함
- 오류가 없어야함
- 모바일에 맞는 포맷이어야 함

[SEO Writing Assistant](https://www.semrush.com/swa/) 을 통해 테스트 가능.

### Above the Fold 컨텐츠 최적화하기

- Above the Fold란 유저가 사이트에 들어가서 처음 보는 화면을 이야기 함. 페이지의 첫 인상을 결정함
  1. 메인 키워드에 대한 정보가 바로 있을 것
  2. 1. 내용이 쓸만해야 할 것
  3. 정확하고 간단해야 할 것
  4. 불쾌하지 않아야 할것

아래는 예시이다.
   
![first](abovethefold.webp)

## User Experience

- 유저 경험 역시 구글이 평가하는 항목이다. 

### 설득력 있는 CTA

- CTA(Call to Action) 방문자가 실제로 어떤 행동을 하도록 유도하는 것이다. 구독이나, 데모를 받거나, 구매를 하는 방식이다.
- 밸류를 강조하는 방식으로 해야 한다.

- "Click here" 보다는, "Get your free SEO checklist"가 더 효율적이다. 아래 예시를 참조할 것

![cta](CTAexample.webp)

## Avoid Walls of Text

- 컨텐츠를 효과적으로 청크 단위로 쪼개기
  1. 짦은 문장, 문단
  2. 문단 사이에 한칸 띄우기(white space)
  3. 200-300 단어 이후에 그림 띄우기
  4. 설득력있는 서브헤딩 넣기

- 아래 예를 참고하자.
![notwall](wallsoftext.webp)

### Bullets, Numbered Lists, Short Paragraphs

- 위 엘리먼트들을 효과적으로 사용하자.

- 긴 문단은 불렛 포인트로 쪼갠다.
- 리스트 아이템은 주제어로 시작함
- 불렉 포인트 스타일은 하나로 통일함
- 단계별은 숫자 리스트로 넣는다.
- 위 내용을 다양하게 써서 일종의 내 리듬을 만든다.

![elements](elements.webp)

## On-Page SEO

- On-Page SEO란 페이지의 html 컨텐츠들을 최적화 하는 방법이다. UX 및 랭킹을 개선할 수 있다.

#### Title Tags

- Stay between 50-60 characters
- Include a target keyword
- Clearly describe the page
- Write a unique title tag for each page

Next에서 페이지별로 타이틀을 만들 수 있겠다

#### Meta Descriptions
- Stick to 105 characters or fewer
- Include the target keyword naturally
- Highlight the page's value 
- Include a clear CTA
- Write a unique meta description for each page

### 헤딩 태그

- Include one [H1](https://www.semrush.com/blog/h1-tag/) tag per page
- Use your target keyword in the H1
- Structure main topics with H2s and subtopics with H3s and smaller
- Keep headings descriptive and clear

### Page URLS

- /shoes/278649
- /red-shoes
- 이 중 후자가 더 점수가 높다고 볼수 있을 것이다. 빨간 신발에서 product id를 슬러그로 넣어도 충분하다.

- Keep them descriptive but concise
- Use your primary keyword
- Separate words with hyphens
- Remove unnecessary words (“a,” “the,” “and.” etc.)
- Avoid special characters

### images

- 검색 엔진은 이미지를 볼 수 없으므로 아래 규칙으로 할 수 있음

- Use descriptive file names (mountain-hiking-gear.jpg—not IMG001.jpg)
- Add relevant [alt text](https://www.semrush.com/blog/alt-text/) to describe each image (include your keyword when it makes sense)
- Compress files to improve loading speed with tools like [TinyPNG](https://tinypng.com/)
- Choose the right file format (WebP is often best, but you can also use JPG for photos and PNG for graphics)

### Internal Links

- 본인 사이트에서 다른 페이지로 이동하게 만드는 것도 역시 검색 엔진에게 구조를 이해시키는게 도움이 된다.
- Use descriptive [anchor text](https://www.semrush.com/blog/anchor-text/) (the clickable, linked text)
- Add relevant internal links to new pages
- Audit and fix broken internal links regularly

## Technical SEO

- 여기는 Nextjs SEO와 함께 할것이므로 간단하게만 작성함

### Robots.txt 활용
- 검색 엔진의 크롤러에 크롤링 전략을 제시하는 파일

### Core Web Vitals

- 라이트하우스로 체크한다.
- **Largest Contentful Paint (LCP)**: Measures how long it takes for the largest element on your page to load
- **Interaction to Next Paint (INP)**: Assesses how quickly a webpage responds to user interactions
- **Cumulative Layout Shift (CLS)**: Measures much the elements on a page unexpectedly shift as the page loads

### Use Https

- Purchase an SSL certificate (many hosts offer them for free)
- Set up [301 redirects](https://www.semrush.com/blog/301-redirects/) from HTTP to HTTPS
- Update any links and assets that are still using HTTP
- Update your property in Google Search Console and submit a new sitemap

### Mobile SEO

- Prioritize quick load times
- Use a responsive website layout that automatically adapts to the user’s screen
- Optimize title tags and meta descriptions for mobile SERPs
- Keep paragraphs short and use plenty of white space
- Avoid intrusive pop-ups
- Make all your buttons and text accessible and readable





**Supporting Content**
<!-- Supporting content in tail of my note  -->
- [[SEO 기초]]
- [[SEO - Nextjs]]

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::[Semrush blog](https://www.semrush.com/blog/seo-basics/)

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see::  [구글 Search Intent 가이드라인](https://services.google.com/fh/files/misc/hsw-sqrg.pdf)

**Terms**
<!-- Links to definition pages. -->
- [키워드 분석](https://www.semrush.com/blog/keyword-research/)

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