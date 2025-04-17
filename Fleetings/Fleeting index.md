---
created: 2025-04-16T13:22
updated: 2025-04-16T16:39
---

```dataviewjs
const pages = dv.pages('"Fleetings"').sort(p => p.file.name);
for (let page of pages) {
  dv.list([page.file.link]);
}
```
