---
title: Website Content Overzicht
type: dashboard
laatst_gewijzigd: 2026-04-28
---

# Website Content Overzicht

Dit dashboard toont alle berichten van studioclaro.nl, geïmporteerd op 2026-04-28.

## Samenvatting

| Status | Aantal |
|--------|--------|
| Live | 75 |
| Archief | 161 |
| **Totaal** | **236** |

---

## Live content

Alle berichten die nog gepubliceerd zijn of als 'behouden' zijn gemarkeerd.

```dataview
TABLE WITHOUT ID
  file.link AS "Artikel",
  actie AS "Actie",
  thema AS "Thema",
  klant AS "Klant",
  date AS "Datum",
  type AS "Type"
FROM "SCL/26269 website remake/30 deliverables/website/live"
WHERE status != null
SORT thema ASC, date DESC
```

---

## Actie: Behouden (sterartikelen & referenties)

```dataview
TABLE WITHOUT ID
  file.link AS "Artikel",
  thema AS "Thema",
  klant AS "Klant",
  type AS "Type",
  vimeo AS "Vimeo"
FROM "SCL/26269 website remake/30 deliverables/website"
WHERE actie = "behouden"
SORT thema ASC, date DESC
```

---

## Actie: Twijfel

Berichten die nog beoordeeld moeten worden.

```dataview
TABLE WITHOUT ID
  file.link AS "Artikel",
  thema AS "Thema",
  klant AS "Klant",
  status AS "Status",
  date AS "Datum"
FROM "SCL/26269 website remake/30 deliverables/website"
WHERE actie = "twijfel"
SORT thema ASC, date DESC
```

---

## Actie: Depubliceren

```dataview
TABLE WITHOUT ID
  file.link AS "Artikel",
  thema AS "Thema",
  status AS "Status",
  date AS "Datum"
FROM "SCL/26269 website remake/30 deliverables/website"
WHERE actie = "depubliceren"
SORT date DESC
```

---

## Per thema

```dataview
TABLE WITHOUT ID
  thema AS "Thema",
  length(rows) AS "Aantal",
  length(filter(rows, (r) => r.actie = "behouden")) AS "Behouden",
  length(filter(rows, (r) => r.actie = "twijfel")) AS "Twijfel",
  length(filter(rows, (r) => r.actie = "depubliceren")) AS "Depubliceren"
FROM "SCL/26269 website remake/30 deliverables/website"
WHERE thema != null
GROUP BY thema
SORT thema ASC
```

---

## Per klant

```dataview
TABLE WITHOUT ID
  klant AS "Klant",
  length(rows) AS "Aantal",
  length(filter(rows, (r) => r.status = "gepubliceerd")) AS "Gepubliceerd"
FROM "SCL/26269 website remake/30 deliverables/website"
WHERE klant != "" AND klant != null
GROUP BY klant
SORT length(rows) DESC
```

---

## Met Vimeo-video

```dataview
TABLE WITHOUT ID
  file.link AS "Artikel",
  thema AS "Thema",
  klant AS "Klant",
  actie AS "Actie"
FROM "SCL/26269 website remake/30 deliverables/website"
WHERE vimeo = true
SORT thema ASC, date DESC
```

---

## Recent gewijzigd

```dataview
TABLE WITHOUT ID
  file.link AS "Artikel",
  laatst_gewijzigd AS "Gewijzigd",
  actie AS "Actie"
FROM "SCL/26269 website remake/30 deliverables/website"
WHERE laatst_gewijzigd != null
SORT laatst_gewijzigd DESC
LIMIT 20
```

## Log

- **2026-04-28** — Dashboard aangemaakt bij import van 236 WordPress berichten
