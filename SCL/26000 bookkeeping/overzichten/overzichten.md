---
tags: [foldernote]
---

# Overzichten

Financiële overzichten en het facturen-dashboard voor Studio Claro.

## Inhoud

```dataview
TABLE file.mtime AS "Laatst gewijzigd"
FROM "SCL/26000 bookkeeping/overzichten"
WHERE file.name != this.file.name
SORT file.name ASC
```
