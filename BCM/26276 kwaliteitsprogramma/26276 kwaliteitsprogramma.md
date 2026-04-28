---
type: oplegnotitie
klant: BCM
projectnummer: 26276
status: actief
laatste_update: 2026-04-27
---

# 26276 kwaliteitsprogramma

> Oplegnotitie. Snelle ingang tot het project. Voor de volledige projectcontext, zie [[BCM/26276 kwaliteitsprogramma/00 project]].

## Samenvatting

Intern professionaliseringsprogramma bij Beaumont Communicatie & Management. Doel is de kwaliteit van communicatie- en participatieplannen gelijkmatiger en hoger te krijgen, met sjablonen, een gestandaardiseerd werkproces, en AI-ondersteuning. Vertrekpunt is de bedrijfsstrategie 2026 (Client Intimacy), gericht op operations.

Centraal instrument is de Beoordelingsmatrix Communicatie- en Participatieplannen, gebouwd op vijf bronnen: Michels, Factor C, IAP2, BPKV en CASI. Aanvullend levert het project een werkende beoordelingstool (HTML met directe Anthropic API-call) en een presentatie *AI in de praktijk*.

Opdrachtgever is Linda Troost. Inhoudelijk klankbord is Simone Schouten, met Jacqueline van Reijsen als meedenker op standaardisering. Fase 1 (vooronderzoek en plan van aanpak) loopt; 18 van de 35 uren besteed. Eerstvolgende mijlpaal is de tussenstand-update aan Linda op dinsdag 28 april. Daarna afronding fase 1 en vervolgvoorstel voor fase 2.

## Te doen

- [ ] Update Linda overlezen, drie verificatiepunten checken (Zeilschool-score, Leiderdorp-label, week 18-aanname) en verzendklaar maken #task #project/26276 📅 2026-04-27⏫ ⏳ 2026-04-27 
- [ ] JSON-parsefout in beoordelingstool oplossen volgens diagnose (max_tokens 16000, prompt strakker, partial-parser) #task #project/26276 📅 2026-05-03
- [ ] Beoordelingstool hertesten met Ooievaarshoek-plan #task #project/26276 📅 2026-05-03
- [ ] Werkende link beoordelingstool naar Simone sturen #task #project/26276 📅 2026-05-03
- [ ] Drie tot vijf interne plannen door matrix v04 halen #task #project/26276 📅 2026-05-03
- [ ] Externe plannen (Buhrs, De Wijde Blik) hertoetsen op v04 voor zuivere vergelijking #task #project/26276 📅 2026-05-10
- [ ] Office@Work-check uitvoeren en verwerken in vervolgvoorstel #task #project/26276 📅 2026-05-10
- [ ] Bevindingen-samenvatting en sjablonenadvies voor fase 2 schrijven #task #project/26276 📅 2026-05-10
- [ ] Vervolgvoorstel fase 2 inclusief business case en fasering opleveren #task #project/26276 📅 2026-05-10
- [ ] Lege oude mappen via Verkenner verwijderen (`beoordelingen/`, `dashboards/`, `projecten/`, `templates/`) #task #project/26276
- [ ] Doublures in `20 brondocumenten/materiaal/vergelijking/` weghalen via Verkenner #task #project/26276
- [ ] Open ontwerpvraag: wel of niet *begrijpelijkheid* als 25e criterium toevoegen aan de matrix #task #project/26276
- [ ] Geëxporteerde claude.ai-chats systematisch verzamelen en plaatsen in `20 brondocumenten/notities/`, met intake-log bijgewerkt #task #project/26276 #parkeerd-tot-na-v05
- [ ] Projectgeschiedenis reconstrueren via geïmporteerde chats en archiefdocumenten: chronologische tijdlijn samenstellen van besluiten, versies en learnings #task #project/26276 #parkeerd-tot-na-v05
- [ ] Verificatie en opheldering van twee bekende inconsistenties bij hertoets op v04: Zeilschool-score (25 versus 26 op 66) en Leiderdorp-label ("Goed" of "Redelijk" bij 30/66) #task #project/26276

## Bestanden

| Bestand of map | Doel |
|---|---|
| [[BCM/26276 kwaliteitsprogramma/00 project]] | Volledige projectcontext: aanleiding, opdracht, betrokkenen, deliverables, status, learnings |
| `10 beoordelingen/` | Vier planbeoordelingen (Ooievaarshoek, Leiderdorp, Zeilschool, Doekenborg) |
| `20 brondocumenten/` | Notities, literatuur en materiaal (klantmateriaal en vergelijking) |
| `30 deliverables/` | Matrix v04, beoordelingstool (versiecover plus archief), bug-diagnose, presentatie, PvA, update Linda |
| `80 dashboards/` | Overzichten over de planbeoordelingen |
| `90 templates/` | Hergebruikbare templates voor planbeoordelingen en versiecovers |

## Brondocumenten op datum

| Datum | Bestand |
|---|---|
| 10-02-2026 | [[260210 intake bespreking Linda]] |
| 12-02-2026 | [[260212 bespreking met Simone]] |
| 18-03-2026 | [[260318-bespreking Jacqueline R]] |
| 14-04-2026 | [[260414 bespreking Simone]] |
| n.v.t. | [[ACDR-waarden-mensen-beweging]] |
| n.v.t. | [[claude-projects-kennisarchitectuur]] |

## Belangrijke data

| Datum | Wat |
|---|---|
| 14 januari 2026 | Eerste gesprek Linda over Client Intimacy |
| 10 februari 2026 | Notitie Linda met concrete opdracht |
| 19 februari 2026 | Akkoord op plan van aanpak fase 1 |
| 1 maart 2026 | Eerste twee externe planbeoordelingen |
| 10 maart 2026 | Interne planbeoordeling Leiderdorp |
| 18 maart 2026 | Bespreking model |
| 14 april 2026 | Bespreking Simone |
| 23 april 2026 | Simone meldt JSON-parsefout |
| 26 april 2026 | Vierde planbeoordeling (Ooievaarshoek), eerste op v04 |
| **28 april 2026** | **Tussenstand-update aan Linda** |
| Week 18-19 | Afronding fase 1, vervolgvoorstel fase 2 |

## Visuele kern

| Element | Keuze |
|---|---|
| Aantal criteria matrix | 24 (waarvan 2 optioneel: 3 en 16) |
| Scoringsschaal | 0, 1, 2, 3 plus NR (-1 punt) |
| Drempel "Goed" | Vanaf circa 65% |
| Drempel "Zeer goed" | Vanaf circa 80% |
| NR-regel | NR op criteria 21-24 forceert herschrijving, ongeacht totaalscore |
| Bronnen matrix | Michels, Factor C, IAP2, BPKV, CASI |
| Toetsstenen instrument | Validiteit (meet je wat je wilt meten) en betrouwbaarheid (komt er iedere keer hetzelfde uit) |
| Werktaal | Nederlands, professioneel toegankelijk |
| Toolstrategie | Copilot voor dagelijks werk (80%), Claude voor projectwerk (20%) |

## Drie niveaus AI op de werkplaats

| Niveau | Vakterm | Werknaam | Tooling |
|---|---|---|---|
| 1 | Ad-hoc prompting | Promptgesprek | Single shot prompting (Copilot, Claude Web) |
| 2 | Context engineering | Werkomgeving-AI | Online Claude-project met GitHub |
| 3 | Agentisch werken | Uitvoerende AI | Claude Cowork |

Volledige toelichting: [[BCM/26276 kwaliteitsprogramma/20 brondocumenten/literatuur/drie-niveau-framework-ai|drie-niveau-framework-ai]].

## Bron van waarheid

Originele Teams-folder: `C:\Users\HP\Studio Claro\BCM - BCM 26276 kwaliteitsprogramma`
