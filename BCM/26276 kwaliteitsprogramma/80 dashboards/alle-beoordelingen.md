---
type: dashboard
gemaakt: 2026-04-26
laatste_update: 2026-04-26
tags: [dashboard, planbeoordelingen]
---

# Alle planbeoordelingen

Overzicht van alle plannen die binnen dit kwaliteitsprogramma door de Beaumont beoordelingsmatrix zijn gehaald, intern en extern.

## Overzicht

| Plan | Type | Herkomst | Bureau | Score | % | Eindoordeel | Matrix | Datum |
|---|---|---|---|---|---|---|---|---|
| [Ooievaarshoek](../10%20beoordelingen/Ooievaarshoek-20260426.md) | Participatieplan | Intern | Beaumont | 25/63 | 40% | Redelijk | v04 | 2026-04-26 |
| [Leiderdorp Oude Gemeentehuis](../10%20beoordelingen/Leiderdorp-OudeGemeentehuis-20260310.md) | Communicatie- en participatieplan | Intern | Beaumont | 30/66 | 45% | Goed | v1.0 | 2026-03-10 |
| [Zeilschool Huizen](../10%20beoordelingen/Zeilschool-Huizen-20260301.md) | Participatieplan | Extern | Bureau Buhrs | 25/66 | 38% | Redelijk | v1.0 | 2026-03-01 |
| [Doekenborg](../10%20beoordelingen/Doekenborg-20260301.md) | Participatieplan | Extern | De Wijde Blik | 33/72 | 46% | Redelijk | v1.0 | 2026-03-01 |

Vier plannen, twee intern (Beaumont) en twee extern (Buhrs, De Wijde Blik). Drie zijn beoordeeld op v1.0, één op v04.

## Patroon op hoofdlijnen

Alle plannen scoren in de bandbreedte 38-46%. Geen enkel plan haalt de drempel "Goed" met overtuiging. Het verschil tussen interne en externe plannen is klein: geen van beide is structureel beter.

**Wat consistent goed gaat:**

- IAP2-participatieniveau (criterium 8): drie van de vier plannen scoren een 3, het vierde een 2. Dit is een sterk punt van het vakgebied.
- Terugkoppeling naar participanten (criterium 19): drie van de vier scoren een 3.

**Wat consistent ontbreekt:**

- Meetplan en KPI's (criterium 17): vier keer een 0.
- Monitoring en bijsturing (criterium 18): vier keer een 0.
- Budget (deel van criterium 15): in alle vier plannen volledig afwezig.
- Creatief concept (criterium 13): meestal afwezig of niet relevant geacht.
- Interne organisatieanalyse (criterium 6): zwak in alle vier plannen.

**Wat varieert:**

- Kernboodschap en sub-boodschappen: Leiderdorp scoort 2, anderen 0 of 1.
- Strategische keuzes: Leiderdorp en Ooievaarshoek scoren 2, anderen 1.
- SMART-doelen: nergens hoger dan 1.

## Inzichten voor het kwaliteitsprogramma

Drie observaties die direct relevant zijn voor sjabloon- en werkwijzerontwikkeling.

**Procesvakmanschap is sterk, strategische diepgang zwak.** De plannen excelleren in het denken over participatieproces (wie betrek je hoe, wat beloof je) maar blijven onderontwikkeld in de strategische verankering (wat is de kernboodschap, wat zijn de meetbare doelen). Dat is opvallend constant over de bureaus heen, niet alleen Beaumont.

**Borging is een sectorbreed probleem.** KPI's, monitoring en kennisdeling ontbreken structureel. De sjablonen die het kwaliteitsprogramma straks oplevert, kunnen hier de meeste impact hebben: een verplichte sectie met meetindicatoren en een evaluatieprotocol.

**Budget hoort er gewoon in.** Geen van de vier plannen heeft een begroting. Voor opdrachtgevers is dat onmogelijk om afwegingen te maken. Een minimale begroting moet onderdeel worden van het sjabloon.

## Met Obsidian Dataview

Als de Dataview-plug-in is geactiveerd, vervangt onderstaande query straks de handmatige tabel.

````
```dataview
TABLE
    type AS "Type",
    herkomst AS "Herkomst",
    bureau AS "Bureau",
    totaalscore + "/" + maximumscore AS "Score",
    eindoordeel AS "Oordeel",
    matrix_versie AS "Matrix",
    datum_beoordeling AS "Datum"
FROM #planbeoordeling
SORT datum_beoordeling DESC
```
````

## Met Python (zonder Dataview)

Als je geen Dataview gebruikt, kan een klein Python-script dit dashboard genereren door de hele vault af te zoeken op bestanden met de tag `planbeoordeling`. Het script staat klaar zodra we het bouwen.

## Open vraag voor herijking

De drie eerste beoordelingen zijn op v1.0 gedaan, Ooievaarshoek op v04. Voor strikt vergelijkbaar materiaal zouden de eerdere plannen ook door v04 gehaald moeten worden. Voor patroonherkenning is dat niet noodzakelijk omdat de criteria-set vrijwel identiek is en de scores op vergelijkbare schaal zitten.
