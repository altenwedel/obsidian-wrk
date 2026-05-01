---
tags: [foldernote]
---

# Bronnen

PDF-facturen en bankafschriften. Deze bestanden dienen als bron voor de overzichten.

## Inhoud

```dataview
TABLE file.mtime AS "Laatst gewijzigd"
FROM "SCL/26000 bookkeeping/bronnen"
WHERE file.name != this.file.name
SORT file.name DESC
```

## Aanleveren

Plaats hier de PDF's van verzonden facturen en gedownloade bankafschriften. Gebruik Claude om ze te verwerken naar het facturenoverzicht.
