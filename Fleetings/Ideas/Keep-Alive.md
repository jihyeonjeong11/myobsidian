---
tags:
  - type/sketchnote
  - type/note
  - theme/http
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[image.jpg]]"
created: 2025-04-18, 21:38
modified: 2025-04-18, 21:38
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-18T21:39
---
<!--  See "Template Help" below for using properties -->

# Keep-Alive
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

http 프로토콜의 keep alive connection헤더는 http/1.x 시절의 것으로 2, 3에서 사용하는 것은 그밎되어 있음.

**❌ Disallowed in HTTP/2:**

- `Connection`
    
- `Keep-Alive`
    
- `Proxy-Connection`
    
- `Transfer-Encoding`
    
- `Upgrade`

## 이유는

- http/2는 양방향, 멀티플렉싱이 되는 프로토콜
- 프로토콜 자체에서 커넥션 매니징, 스트림 컨트롤 네고시에이션을 자체 프레임에서 진행함
- HTTP/1.x처럼 위와 같은 헤더를 필요로 하지 않음.

## 예외사항

- TE 헤더는 허용함
```
TE: trailers

```
오직 저 값만 받는데, 트레일링 헤더를 쓴다는 뜻임.



**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::

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