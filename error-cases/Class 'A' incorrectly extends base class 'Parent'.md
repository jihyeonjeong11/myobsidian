---
tags:
  - type/sketchnote
  - type/note
  - theme/error
  - theme/typescript
  - theme/class
aliases: 
lead: 해당 에러는 클래스가 부모에게서 상속받을 때 가져오는 Props의 키값과 선언한 스테이트의 키값이 중복되어서 발생함.
visual: "![[err1.png]]"
created: 2025-05-02, 14:02
modified: 2025-05-02, 14:02
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-05-02T14:11
---


# Class 'A' incorrectly extends base class 'Parent'

```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**

```
Class 'WebSocketHibernationServer' incorrectly extends base class 'DurableObject<unknown>'.  
Property 'env' is private in type 'WebSocketHibernationServer' but not in type 'DurableObject<unknown>'.ts(2415)

```

```

export class WebSocketHibernationServer extends DurableObject {

    private env: Env;

    constructor(private state: DurableObjectState, env: Env) {

        super(state, env);

        this.env = env;

    }
 }

```

- DurableObject 상속 시 가지고 있는 env props를 private로 자체적으로 덮어씌우려고 하기 때문에 문제가 발생함.
- private을 지우거나 protected, 혹은 public을 써줘서 에러 해결가능

**Supporting Content**

- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::
- ChatGPT

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
