---
tags:
  - type/sketchnote
  - type/note
  - theme/web
  - theme/seo
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[seo.jpg]]"
created: 2025-04-26, 12:23
modified: 2025-04-26, 12:23
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-26T15:25
---


# SEO 기초

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

## SEO란?

- SEO란 검색 엔진에서 연관성있는 검색어를 사용했을 때 타겟 웹사이트가 나오는 빈도를 늘리는 과정을 말한다.

- 예를 들어 베스트 커피 메이커를 검색하였을 때 내 홈페이지가 여기 상위 결과에 노출되는 것을 말함. 검색 엔진은 자체적으로 크롤링한 사이트의 메타태그에 점수를 매겨 이 순위를 정하게 된다.

![coffee](coffemaker.webp)

## SEO는 왜 중요한가?

SEO는 광고가 아닌 경우에 내 홈페이지를 상위에 노출시키기 떄문에 비용을 줄이고 트래픽을 늘리는데 필수적이다.

유저들 역시 대부분의 페이지 유입이 검색엔진으로 일어난다. 누군가 어떤 프로덕트, 서비스, 정보가  필요하다면 먼저 네이버나 구글에서 검색할 것이다. 거기에 내 홈페이지가 노출된다면 트래픽으로 연결될 것이다. 더해서 유저들은 이 결과를 광고 결과보다 더 신용하기 때문에 실제 인터랙션이 더욱 증가하게 된다.

따라서 이 organic search result의 상위에 드는 것이 잠재적 소비자를 늘리는데 큰 도움이 될 것이다.

결론은: 돈을 안쓰고 organic한 유저를 유입시키는 것이 광고보다 더 중요함.

## 그렇다면 SEO는 어떻게 하나?

- 첫 번째는 검색 엔진이 홈페이지를 크롤링하고 인덱스의 코드에 접근하게 해야 한다.
- 구글의 경우 spider라고 불리는 크롤러를 통해 페이지를 찾고 컨텐츠를 읽는다. 
- 아래 그림에 간단한 프로세스가 묘사되어 있다.

![crawling](crawling.webp)

당신의 홈페이지가 어떻게 크롤링되었는지 보고싶다면 GSC(Google Search Console)에서 확인할 수 있다. 무료 툴이고 여기서 내 SEO가 어떻게 평가되는지 확인 가능하다.

[GSC](https://search.google.com/search-console/about)

여기서 XML sitemap을 만들어서 검색엔진이 이해하기 쉽도록 하게 할 수 있음.

![sitemap](sitemap.webp)

- ai chatbot의 사이트맵
- [xml-sitemaps generator](https://www.xml-sitemaps.com/)

```
<?xml version="1.0" encoding="UTF-8"?>

<urlset

      xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"

      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

      xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9

            http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">

<!-- created with Free Online Sitemap Generator www.xml-sitemaps.com -->

  
  

<url>

  <loc>https://ai-gemini-chatbot-pearl.vercel.app/</loc>

  <lastmod>2025-04-26T04:31:40+00:00</lastmod>

  <priority>1.00</priority>

</url>

<url>

  <loc>https://ai-gemini-chatbot-pearl.vercel.app/sign-in</loc>

  <lastmod>2025-04-26T04:31:40+00:00</lastmod>

  <priority>0.80</priority>

</url>

<url>

  <loc>https://ai-gemini-chatbot-pearl.vercel.app/sign-in/email</loc>

  <lastmod>2025-04-26T04:31:40+00:00</lastmod>

  <priority>0.64</priority>

</url>

<url>

  <loc>https://ai-gemini-chatbot-pearl.vercel.app/sign-in/forgot-password</loc>

  <lastmod>2025-04-26T04:31:40+00:00</lastmod>

  <priority>0.51</priority>

</url>

<url>

  <loc>https://ai-gemini-chatbot-pearl.vercel.app/sign-up</loc>

  <lastmod>2025-04-26T04:31:40+00:00</lastmod>

  <priority>0.51</priority>

</url>

  
  

</urlset>

```

- 사이트맵이란 웹사이트를 검색 엔진이 이해하기 쉽게 만든 것임. 모든 중요한 페이지 정보를 포함함.
- GSC의 페이지 항목에서 당신의 웹페이지가 indexed 되었는지, 랭킹이 얼마인지 확인할 수 있다.

**Supporting Content**
<!-- Supporting content in tail of my note  -->
- [[SEO 최적화 하는법 - 기초]]
- [[SEO - Nextjs]]

---
# Back Matter

**Source**

- based_on::[semrush blog](https://www.semrush.com/blog/seo-basics/)

**References**

- see:: [semrush blog]([_How to Get Your Website Indexed by Google_](https://www.semrush.com/blog/google-index/))

**Terms**
<!-- Links to definition pages. -->
- [SEO](https://www.semrush.com/blog/what-is-seo/) 검색엔진이 타겟 웹사이트를 얼마나 노칠시킬 것인지 결정하는 프로세스. 광고는 여기 적용되지 않는다. SEO 마케팅, SEO 최적화 혹은 organic 서치 마케팅으로 불린다.
- GSC
- Sitemap

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