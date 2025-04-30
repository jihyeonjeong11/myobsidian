---
tags:
  - type/sketchnote
  - type/note
  - theme/xyz
aliases: 
lead: Three Pillars of Optimization 부분의 Technical 부분을 정리하기로 함.
visual: "![[image.jpg]]"
created: 2025-04-26, 15:34
modified: 2025-04-26, 15:34
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-27T13:39
---


# SEO - Nextjs



```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

>[!From Next docs]
>
>The process of optimizing a website can be divided into three main pillars:
>
>- **Technical**: Optimize your website for crawling and web performance.
>- **Creation**: Create a content strategy to target specific keywords.
>- **Popularity**: Boost your site's presence online so search engines know you are a trusted source. > This is done through the use of [backlinks](https://moz.com/learn/seo/backlinks), third-party sites that link back to your site.
>
>따라서, 여기서는 개발자로써 NextJS 기준 Technical 부분을 정리하도록 할 것임.


## Meta tags

- 검색 엔진이 크롤링을 하며 가져가는 <Head> 안의 정보들

기본 메타 태그

- **title**
- **description**
- **keywords**
- **robots**
- **viewport**
- **charSet**

오픈그래프(메타) 메타 태그:

- **og:site_name**
- **og:locale**
- **og:title**
- **og:description**
- **og:type**
- **og:url**
- **og:image**
- **og:image:alt**
- **og:image:type**
- **og:image:width**
- **og:image:height**
- **article:published_time**
- **article:modified_time**
- **article:author**

X 메타 태그(Still, not changed):

- **twitter:card**
- **twitter:site**
- **twitter:creator**
- **twitter:title**
- **twitter:description**
- **twitter:image**
  
>
> og:image와 twitter:image의 경우 png, jpg로 사용함.

### Pages Router Meta tags

**pages/[slug].tsx**

```javascript

import Head from "next/head";
 
export default function Page() {
  return (
    <Head>
      <title>
        Next.js SEO: The Complete Checklist to Boost Your Site Ranking
      </title>
      <meta
        name="description"
        content="Learn how to optimize your Next.js website for SEO by following this complete checklist."
      />
      <meta
        name="keywords"
        content="nextjs seo complete checklist, nextjs seo tutorial"
      />
      <meta name="robots" content="index, follow" />
      <meta name="googlebot" content="index, follow" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <meta charSet="utf-8" />
      <meta property="og:site_name" content="Blog | Minh Vu" />
      <meta property="og:locale" content="en_US" />
      <meta
        property="og:title"
        content="Next.js SEO: The Complete Checklist to Boost Your Site Ranking"
      />
      <meta
        property="og:description"
        content="Learn how to optimize your Next.js website for SEO by following this complete checklist."
      />
      <meta property="og:type" content="website" />
      <meta property="og:url" content="https://dminhvu.com/nextjs-seo" />
      <meta
        property="og:image"
        content="https://ik.imagekit.io/dminhvu/assets/nextjs-seo/thumbnail.png?tr=f-png"
      />
      <meta property="og:image:alt" content="Next.js SEO" />
      <meta property="og:image:type" content="image/png" />
      <meta property="og:image:width" content="1200" />
      <meta property="og:image:height" content="630" />
      <meta
        property="article:published_time"
        content="2024-01-11T11:35:00+07:00"
      />
      <meta
        property="article:modified_time"
        content="2024-01-11T11:35:00+07:00"
      />
      <meta
        property="article:author"
        content="https://www.linkedin.com/in/dminhvu02"
      />
      <meta name="twitter:card" content="summary_large_image" />
      <meta name="twitter:site" content="@dminhvu02" />
      <meta name="twitter:creator" content="@dminhvu02" />
      <meta
        name="twitter:title"
        content="Next.js SEO: The Complete Checklist to Boost Your Site Ranking"
      />
      <meta
        name="twitter:description"
        content="Learn how to optimize your Next.js website for SEO by following this complete checklist."
      />
      <meta
        name="twitter:image"
        content="https://ik.imagekit.io/dminhvu/assets/nextjs-seo/thumbnail.png?tr=f-png"
      />
    </Head>
  );
}
```

### App router의 경우

앱 라우터에서는 metadata를 통해 스태틱 메타데이터를,  generateMetadata로 다이나믹한 메타데이터를 넣을 수 있음.

**app/layout.tsx**

정적인 메타데이터의경우

```javascript
import type { Viewport, Metadata } from "next";
 
export const viewport: Viewport = {
  width: "device-width",
  initialScale: 1,
  themeColor: "#ffffff"
}; // next의 경우 viewport는 자동생성되기에 안넣어도 됨.
 
export const metadata: Metadata = {
  metadataBase: new URL("https://dminhvu.com"),
  openGraph: {
    siteName: "Blog | Minh Vu",
    type: "website",
    locale: "en_US"
  },
  robots: {
    index: true,
    follow: true,
    "max-image-preview": "large",
    "max-snippet": -1,
    "max-video-preview": -1,
    googleBot: "index, follow"
  },
  alternates: {
    types: {
      "application/rss+xml": "https://dminhvu.com/rss.xml"
    }
  },
  applicationName: "Blog | Minh Vu",
  appleWebApp: {
    title: "Blog | Minh Vu",
    statusBarStyle: "default",
    capable: true
  },
  verification: {
    google: "YOUR_DATA",
    yandex: ["YOUR_DATA"],
    other: {
      "msvalidate.01": ["YOUR_DATA"],
      "facebook-domain-verification": ["YOUR_DATA"]
    }
  },
  icons: {
    icon: [
      {
        url: "/favicon.ico",
        type: "image/x-icon"
      },
      {
        url: "/favicon-16x16.png",
        sizes: "16x16",
        type: "image/png"
      }
      // add favicon-32x32.png, favicon-96x96.png, android-chrome-192x192.png
    ],
    shortcut: [
      {
        url: "/favicon.ico",
        type: "image/x-icon"
      }
    ],
    apple: [
      {
        url: "/apple-icon-57x57.png",
        sizes: "57x57",
        type: "image/png"
      },
      {
        url: "/apple-icon-60x60.png",
        sizes: "60x60",
        type: "image/png"
      }
      // add apple-icon-72x72.png, apple-icon-76x76.png, apple-icon-114x114.png, apple-icon-120x120.png, apple-icon-144x144.png, apple-icon-152x152.png, apple-icon-180x180.png
    ]
  }
};
```

**mdn example**

```javascript
export const metadata: Metadata = {
  title: "What's in the head? Web page metadata - Learn web development | MDN",
  description:
    "The head of an HTML document is the part that is not displayed in the web browser when the page is loaded. It contains metadata information such as the page <title>, links to CSS (if you choose to style your HTML content with CSS), links to custom favicons, and other metadata (data about the HTML, such as the author, and important keywords that describe the document).",
  themeColor: "rgb(255, 255, 255)",
  manifest: "https://developer.mozilla.org/manifest.f42880861b394dd4dc9b.json",
  icons: {
    icon: [
      {
        url: "https://developer.mozilla.org/favicon-48x48.bc390275e955dacb2e65.png",
        sizes: "48x48",
        type: "image/png",
      },
    ],
    apple: [
      {
        url: "https://developer.mozilla.org/apple-touch-icon.528534bba673c38049c2.png",
        sizes: "180x180",
        type: "image/png",
      },
    ],
  },
  alternates: {
    canonical:
      "https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
    types: {
      "application/rss+xml":
        "https://developer.mozilla.org/en-US/blog/rss.xml",
    },
    languages: {
      de: "https://developer.mozilla.org/de/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      es: "https://developer.mozilla.org/es/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      fr: "https://developer.mozilla.org/fr/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      ja: "https://developer.mozilla.org/ja/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      ko: "https://developer.mozilla.org/ko/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      pt: "https://developer.mozilla.org/pt-BR/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      ru: "https://developer.mozilla.org/ru/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      "zh-CN":
        "https://developer.mozilla.org/zh-CN/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      "zh-Hant":
        "https://developer.mozilla.org/zh-TW/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
      en: "https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
    },
  },
  openGraph: {
    url: "https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata",
    title: "What's in the head? Web page metadata - Learn web development | MDN",
    type: "website",
    locale: "en_US",
    description:
      "The head of an HTML document is the part that is not displayed in the web browser when the page is loaded. It contains metadata information such as the page <title>, links to CSS (if you choose to style your HTML content with CSS), links to custom favicons, and other metadata (data about the HTML, such as the author, and important keywords that describe the document).",
    images: [
      {
        url: "https://developer.mozilla.org/mdn-social-share.d893525a4fb5fb1f67a2.png",
        type: "image/png",
        width: 1920,
        height: 1080,
        alt: "The MDN Web Docs logo, featuring a blue accent color, displayed on a solid black background.",
      },
    ],
    siteName: "MDN Web Docs",
  },
  twitter: {
    card: "summary_large_image",
    creator: "@MozDevNet",
  },
};
```

**app/[slug]/page.tsx**

다이나믹한 경우

```javascript
import type { Metadata, ResolvingMetadata } from "next";
 
type Params = {
  slug: string;
};
 
type Props = {
  params: Params;
  searchParams: { [key: string]: string | string[] | undefined };
};
 
export async function generateMetadata(
  { params, searchParams }: Props,
  parent: ResolvingMetadata
): Promise<Metadata> {
  const { slug } = params;
 
  const post: Post = await fetch(`YOUR_ENDPOINT`, {
    method: "GET",
    next: {
      revalidate: 60 * 60 * 24
    }
  }).then((res) => res.json());
 
  return {
    title: `${post.title} | dminhvu`,
    authors: [
      {
        name: post.author || "Minh Vu"
      }
    ],
    description: post.description,
    keywords: post.keywords,
    openGraph: {
      title: `${post.title} | dminhvu`,
      description: post.description,
      type: "article",
      url: `https://dminhvu.com/${post.slug}`,
      publishedTime: post.created_at,
      modifiedTime: post.modified_at,
      authors: ["https://dminhvu.com/about"],
      tags: post.categories,
      images: [
        {
          url: `https://ik.imagekit.io/dminhvu/assets/${post.slug}/thumbnail.png?tr=f-png`,
          width: 1024,
          height: 576,
          alt: post.title,
          type: "image/png"
        }
      ]
    },
    twitter: {
      card: "summary_large_image",
      site: "@dminhvu02",
      creator: "@dminhvu02",
      title: `${post.title} | dminhvu`,
      description: post.description,
      images: [
        {
          url: `https://ik.imagekit.io/dminhvu/assets/${post.slug}/thumbnail.png?tr=f-png`,
          width: 1024,
          height: 576,
          alt: post.title
        }
      ]
    },
    alternates: {
      canonical: `https://dminhvu.com/${post.slug}`
    }
  };
}
```

> charSet, viewPort는 넥스트에서 자동으로 넣어주기 때문에 넣을 필요가 없다.

## JSON-LD Schema

> page, app 라우터 둘 다 사용 가능.

JSON Linked-data 포맷으로(왜 쓰는지는? 추가로 적을 필요가 있음)

```javascript

const jsonLd = {
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  mainEntityOfPage: {
    "@type": "WebPage",
    "@id": "https://dminhvu.com/nextjs-seo"
  },
  headline: "Next.js SEO: The Complete Checklist to Boost Your Site Ranking",
  description:
    "Learn how to optimize your Next.js website for SEO by following this complete checklist.",
  image:
    "https://ik.imagekit.io/dminhvu/assets/nextjs-seo/thumbnail.png?tr=f-png",
  dateCreated: "2024-01-11T11:35:00+07:00",
  datePublished: "2024-01-11T11:35:00+07:00",
  dateModified: "2024-01-11T11:35:00+07:00",
  author: {
    "@type": "Person",
    name: "Minh Vu",
    url: "https://www.linkedin.com/in/dminhvu02"
  },
  publisher: {
    "@type": "Person",
    name: "Minh Vu",
    logo: {
      "@type": "ImageObject",
      url: "https://dminhvu.com/avatar_zoom.jpg"
    }
  },
  inLanguage: "en-US",
  isFamilyFriendly: "true"
};

import Head from "next/head";
 
export default function Page() {
  return (
    <div>
      {/* other parts */}
      <script
        type="application/ld+json"
        dangerouslySetInnerHTML={{ __html: JSON.stringify(jsonLd) }}
      />
    </div>
  );
}

```

## Sitemap

 - 사이트맵은 검색 엔진이 크롤링하고 인덱싱하는데 도움을 주는 uri 모음임.
- docs에서는 작은 규모에서는 그냥 때려넣고, 큰 규모 앱에서는 next-sitemap으로 만들어서 넣으라고 함.

여기서는 작은 규모만을 설명할 예정.

**app/sitemap.xml**

```javascript

<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://acme.com</loc>
    <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    <changefreq>yearly</changefreq>
    <priority>1</priority>
  </url>
  <url>
    <loc>https://acme.com/about</loc>
    <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
  <url>
    <loc>https://acme.com/blog</loc>
    <lastmod>2023-04-06T15:02:24.021Z</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.5</priority>
  </url>
</urlset>

```

## robots.tsx

- 이 파일은 어떤 페이지를 크롤링하고 중요하지 않은 페이지는 넘어가도록 해주는 역할을 함.

### page 라우터일 경우

```javascript
User-agent: *
`Sitemap: https://dminhvu.com/sitemap.xml`
Disallow: /search?q=
Disallow: /admin
```

### app 라우터일 경우

**app/robots.ts**

```javascript

import { MetadataRoute } from "next";
 
export default function robots(): MetadataRoute.Robots {
  return {
    rules: {
      userAgent: "*",
      allow: ["/"],
      disallow: ["/search?q=", "/admin/"]
    },
    sitemap: ["https://dminhvu.com/sitemap.xml"]
  };
}

```
해당 값으로 만들어진 public 내부의 robots.txt는 다음과 같음

```
User-agent: *
Allow: /
Disallow: /search?q=
Disallow: /admin
 
Sitemap: https://dminhvu.com/sitemap.xml
```

## Link tags

- 여기서 다루는 meta 항목은 다음과 같음.

- **canonical**
- **alternate**
- **icon**
- **apple-touch-icon**
- **manifest**

### page 라우터인 경우

```javascript
import Head from "next/head";
 
export default function Page() {
  return (
    <Head>
      {/* other parts */}
      <link
        rel="alternate"
        type="application/rss+xml"
        href="https://dminhvu.com/rss.xml"
      />
      <link rel="icon" href="/favicon.ico" type="image/x-icon" />
      <link rel="apple-touch-icon" sizes="57x57" href="/apple-icon-57x57.png" />
      <link rel="apple-touch-icon" sizes="60x60" href="/apple-icon-60x60.png" />
      {/* add apple-touch-icon-72x72.png, apple-touch-icon-76x76.png, apple-touch-icon-114x114.png, apple-touch-icon-120x120.png, apple-touch-icon-144x144.png, apple-touch-icon-152x152.png, apple-touch-icon-180x180.png */}
      <link
        rel="icon"
        type="image/png"
        href="/favicon-16x16.png"
        sizes="16x16"
      />
      {/* add favicon-32x32.png, favicon-96x96.png, android-chrome-192x192.png */}
    </Head>
  );
}
```

```javascript

import Head from "next/head";
 
export default function Page() {
  return (
    <Head>
      {/* other parts */}
      <link rel="canonical" href="https://dminhvu.com/nextjs-seo" />
    </Head>
  );
}

```

### app 라우터인 경우

위의 메타와 마찬가지로 metadata, generateMetaData를 사용한다.

```javascript
export const metadata: Metadata = {
  // other parts
  alternates: {
    types: {
      "application/rss+xml": "https://dminhvu.com/rss.xml"
    }
  },
  icons: {
    icon: [
      {
        url: "/favicon.ico",
        type: "image/x-icon"
      },
      {
        url: "/favicon-16x16.png",
        sizes: "16x16",
        type: "image/png"
      }
      // add favicon-32x32.png, favicon-96x96.png, android-chrome-192x192.png
    ],
    shortcut: [
      {
        url: "/favicon.ico",
        type: "image/x-icon"
      }
    ],
    apple: [
      {
        url: "/apple-icon-57x57.png",
        sizes: "57x57",
        type: "image/png"
      },
      {
        url: "/apple-icon-60x60.png",
        sizes: "60x60",
        type: "image/png"
      }
      // add apple-icon-72x72.png, apple-icon-76x76.png, apple-icon-114x114.png, apple-icon-120x120.png, apple-icon-144x144.png, apple-icon-152x152.png, apple-icon-180x180.png
    ]
  }
};
```

```javascript

export const metadata: Metadata = {
  // other parts
  alternates: {
    canonical: "https://dminhvu.com"
  }
};

```

## Script optimization

### 페이지 라우터의 경우

- gtag와 같이 스크립트로 무언가를 등록할 경우 사용한다.

```javascript
import Head from "next/head";
import Script from "next/script";
 
export default function Page() {
  return (
    <Head>
      {/* other parts */}
      {process.env.NODE_ENV === "production" && (
        <>
          <Script async strategy="afterInteractive" id="analytics">
            {`
              window.dataLayer = window.dataLayer || [];
              function gtag(){dataLayer.push(arguments);}
              gtag('js', new Date());
              gtag('config', 'G-XXXXXXXXXX');
            `}
          </Script>
        </>
      )}
    </Head>
  );
}

```

### app 라우터의 경우

```javascript
import { GoogleTagManager } from "@next/third-parties/google";
import { GoogleAnalytics } from "@next/third-parties/google";
import Head from "next/head";
 
export default function Page() {
  return (
    <html lang="en" className="scroll-smooth" suppressHydrationWarning>
      {process.env.NODE_ENV === "production" && (
        <>
          <GoogleAnalytics gaId="G-XXXXXXXXXX" />
          {/* other scripts */}
        </>
      )}
      {/* other parts */}
    </html>
  );
}
```


**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::[nextjs docs](https://nextjs.org/learn/seo)
- [blog](https://dminhvu.com/post/nextjs-seo)
- 

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