---
project: BCM 26276 kwaliteitsprogramma
opdrachtgever: Beaumont Communicatie & Management (intern)
projectleider: Sicko van Dijk
gestart: 2026-02-19
status: fase 1 in uitvoering
fase: 1 van 4
budget_uren: 32 + 10% marge (max 35)
besteed_uren: 18
tarief: 68.40
tags: [project, kwaliteitsprogramma, intern]
---

# BCM 26276, Kwaliteitsprogramma werkprocessen

## Aanleiding

Beaumont werkt in 2026 aan een strategie van Client Intimacy. De kwaliteit van communicatie- en participatieplannen verschilt te sterk per collega. Er bestaan geen eenduidige sjablonen en het proces van analyse naar plan is niet gestandaardiseerd. Tegelijkertijd wordt verkend of AI kan helpen om processen te ondersteunen en de kwaliteit te verbeteren.

## Opdracht fase 1

Vooronderzoek en plan van aanpak. Zes onderdelen:

1. Analyse 8-10 bestaande plannen (8 uur)
2. Concurrentieanalyse (4 uur)
3. Verkenning AI-mogelijkheden (6 uur)
4. Testen AI-toepassingen, RAG en persona-review (6 uur)
5. Bevindingen samenvatten (4 uur)
6. Afstemming Simone en Linda (4 uur)

Totaal 32 uur, plafond 35 uur, € 2.394 inclusief marge.

Aanvullende vraag van Linda bij het akkoord op 19 februari: check op wat Office@Work kan, en aandacht voor sjablonen, modellen en figuren.

## Betrokkenen

| Rol | Naam |
|---|---|
| Opdrachtgever | Linda Troost |
| Projectleider en uitvoerder | Sicko van Dijk |
| Inhoudelijk klankbord | Simone Schouten |
| Meedenker standaardisering | Jacqueline van Reijsen |
| Toegevoegd 2026-04 | Leon Batenburg |

## Deliverables

- Beoordelingsmatrix Communicatie- en Participatieplannen v04
- Werkende beoordelingstool (HTML met directe Anthropic API call)
- Presentatie AI in de praktijk (20 slides)
- Plan van Aanpak (in concept)
- Planbeoordelingen (in `10 beoordelingen/`)

## Status per onderdeel (stand 2026-04-26)

| # | Onderdeel | Status | Toelichting |
|---|---|---|---|
| 1 | Analyse interne plannen | In uitvoering | Eerste plan beoordeeld (Ooievaarshoek). Interne plannen worden via beoordelingsmatrix doorgewerkt. |
| 2 | Concurrentieanalyse | Gedaan | Plannen verzameld. Beoordeling volgt. |
| 3 | Verkenning AI-mogelijkheden | Gedaan | Verwerkt in presentatie en in werkende tool. |
| 4 | Testen AI-toepassingen | Gedaan | Beoordelingstool gebouwd en getest. JSON-bug nog open. |
| 5 | Bevindingen samenvatten | Open | Bevindingen worden verwerkt in update voor Linda (dinsdagochtend). |
| 6 | Afstemming Simone en Linda | Gedeeltelijk | Tussentijdse mails. Update aan Linda dinsdagochtend. |

## Open punten

- JSON-parsefout in beoordelingstool oplossen (gemeld door Simone op 2026-04-23)
- Interne plannen verzamelen voor batch-beoordeling
- Office@Work-check uitvoeren (vraag Linda 2026-02-19)
- Update aan Linda: deadline dinsdagochtend 2026-04-28

## Framework drie niveaus AI op de werkplaats

Het AI-gesprek binnen het kwaliteitsprogramma is per 2026-04-28 georganiseerd langs drie vaste niveaus, met een tijdelijke stop op nieuwe tooling. De niveaus beschrijven een glijdende schaal van menselijke sturing naar systeem-uitvoering.

| Niveau | Vakterm | Werknaam | Concrete tooling |
|---|---|---|---|
| 1 | Ad-hoc prompting | Promptgesprek | Single shot prompting in Copilot of Claude Web |
| 2 | Context engineering | Werkomgeving-AI | Online Claude-project met GitHub-koppeling |
| 3 | Agentisch werken | Uitvoerende AI | Claude Cowork (desktopomgeving) |

Deze terminologie is leidend in alle interne en externe communicatie van het kwaliteitsprogramma. Het tweede niveau is het stille middenstuk waar voor Beaumont de meeste praktische winst zit. Volledige toelichting in de referentie-notitie [drie-niveau-framework-ai](20%20brondocumenten/literatuur/drie-niveau-framework-ai.md).

## Validiteit en betrouwbaarheid

Twee meettheoretische principes vormen de toetsstenen voor de matrix en de tool: **validiteit** (meet je wat je wilt meten) en **betrouwbaarheid** (komt er iedere keer hetzelfde uit). Beide worden expliciet als ontwerpcriteria gehanteerd en als ankers gebruikt in de memo aan Linda en in elk afwegingsmoment van het vervolgvoorstel fase 2.

## Learnings

- Een NR op overkoepelende criteria 21-24 dwingt tot herschrijving, ongeacht de totaalscore. Dat is een architecturale keuze.
- Optionele criteria 3 en 16 (gedragsverandering) tellen niet mee in de totaalscore als gedragsverandering geen expliciet doel is. Maximumscore varieert daardoor per plan.
- De pivot van zes PvA-onderdelen naar matrix plus tool is inhoudelijk verdedigbaar (compounding kennis, herhaalbare beoordeling) maar moet eerlijk worden teruggekoppeld aan Linda omdat het afwijkt van het oorspronkelijke voorstel.
- Schrijfstijl: korte alinea's, één hoofdboodschap per zin, bullets alleen aan het eind, geen em-dashes.

## Folderstructuur

| Folder | Inhoud |
|---|---|
| `10 beoordelingen/` | Planbeoordelingen (intern en extern) volgens matrix v04 |
| `20 brondocumenten/` | Bronmateriaal vanuit Teams of andere kanalen, geconverteerd naar markdown |
| `30 deliverables/` | Eindproducten: matrix, tool, presentatie, PvA, updates |
| `80 dashboards/` | Overzichten binnen dit project |
| `90 templates/` | Hergebruikbare templates voor planbeoordelingen en versiebeheer |

## Links

- [Dashboard alle beoordelingen](80%20dashboards/alle-beoordelingen.md)
- [Template planbeoordeling](90%20templates/template-planbeoordeling.md)
- [Template versiecover](90%20templates/template-versiecover.md)
