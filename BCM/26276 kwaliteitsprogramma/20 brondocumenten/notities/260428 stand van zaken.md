---
type: stand
datum: 2026-04-28
opgesteld: ochtend
auteur: Claude (in opdracht van Sicko)
tags: [stand, voortgang, werkstand, kwaliteitsprogramma]
---

# Stand van zaken, 28 april ochtend

> Werknotitie aan het eind van een lange ochtendsessie waarin veel parallel is gedaan: Linda-update, vault-architectuur, Tasks-pivot, terminologievastlegging, projecthistorie-import en doorontwikkeling van de beoordelingstool naar v05. Dit is de bondige snapshot zodat een volgende chat met volle context kan beginnen.

## Hoogtepunten

**De beoordelingstool v05 is in actieve ontwikkeling op claude.ai via de Remix-functie.** Inhoudelijk is hij intern volledig op v04 gebracht met expliciete bron-attributie (Michels, Factor C, IAP2, BPKV, CASI), één scherpe toetsvraag per criterium, voetnoot-informatie verwerkt, NR=−1 gehandhaafd. UI is uitgebreid met een pre-assessment-stap voor de drie knock-out-vragen, een toelichtingsveld voor type-plan en accenten, en het label TOOL V05. API-call is aangepast: `max_tokens` naar 16000, prompt strakker (één zin onderbouwing), partial parser ingebouwd voor robuustheid bij afgekapte responses. Sicko heeft een testrun gedaan met het Ooievaarshoek-plan; resultaat moet vergeleken worden met de bestaande v04-beoordeling in `10 beoordelingen/`.

**Een onverwachte learning kwam naar voren tijdens v05-ontwikkeling.** Het oorspronkelijke artifact dat als "MATRIX V02" gepubliceerd stond, was eigenlijk nooit volledig op v02-niveau. Drie van de vijf bronnen (Michels, Factor C, BPKV) ontbraken al in de embedded prompt. De tool scoorde dus criteria zonder de structurele verankering die de matrix kenmerkt. Pas met de v05-update is de tool inhoudelijk verankerd zoals bedoeld. Dat verklaart mogelijk een deel van eerdere inconsistenties.

**Het twee-cirkel-model is herzien naar een hybride werkwijze.** Cowork live artifacts blijken niet deelbaar met collega's; Anthropic werkt eraan maar het is nog toekomstmuziek. Dat dwingt tot: ontwikkelen in Cowork (directe bestandstoegang, lokale data), publiceren via claude.ai (gepubliceerde artifact met openbare link). Beaumont heeft een Pro-account, dus publicatie is altijd openbaar (iedereen met de link); Team-upgrade is een afweging voor het vervolgvoorstel.

## Vandaag opgeleverd

In de WRK-vault:

- Coverpagina `26276 kwaliteitsprogramma.md` aangelegd in oplegnotitie-format
- `00 project.md` van 26276 uitgebreid met framework drie niveaus AI en validiteit/betrouwbaarheid
- WRK-README naar versie 0.3, met cross-project `80 dashboards/`, subfolders voor `20 brondocumenten/`, oplegnotitie expliciet in structure, aangescherpte versiebeheer-passage en Teams-naar-WRK-mapping
- `taken.md` als centraal Tasks-plug-in dashboard in `80 dashboards/`
- `kanban-actief.md` omgebouwd tot deprecated-verwijzing
- `vergelijkingsmateriaal/` hernoemd naar `materiaal/` met `vergelijking/` als subfolder
- Stand-notitie van 26 april verplaatst naar `20 brondocumenten/notities/`
- Drie-niveau-framework-referentienotitie in `20 brondocumenten/literatuur/`
- Schone matrix v04 in `30 deliverables/beoordelingsmatrix/`
- Coverpagina `30 deliverables/beoordelingstool/README.md` met architectuur-trajectory en sharing-architectuur
- Geparkeerde projectprompt v0 in archief
- Chat-transcript Tool-architectuur (28 april) en Leiderdorp-beoordeling (10 maart) als notities
- Learning log van 10 maart (twee logs, plantoetser plus PvA-voorbereiding) als notitie
- Intake-historische-bestanden.md als log voor inkomende externe bestanden

In het projectgeheugen:

- Office@Work afweging voor memo Linda
- Validiteit en betrouwbaarheid als kernprincipes
- Drie-niveau-framework AI met canonical vakterminologie
- Linda's leesgedrag en beslisstijl (max 10 min, max 1.500 woorden, één besluit tegelijk)
- Lida's 3x ROI-regel
- Studio Claro 12-element briefing-format (reference)
- Twee-cirkel-model bijgewerkt naar hybride Cowork/claude.ai

## In uitvoering

**Beoordelingstool v05.** Sicko heeft een testrun gedaan op claude.ai. Wachten op het delen van het testresultaat met deze Cowork-omgeving om de score te vergelijken met de bestaande Ooievaarshoek-beoordeling (25/63 = 40% Redelijk in `10 beoordelingen/Ooievaarshoek-20260426.md`). Vervolgstap zodra dat klopt: publiceren als artifact en de link delen met Simone (eerst) voor herbeoordeling van haar bug-trigger, daarna een update aan Linda met de nieuwe versie.

**Print/PDF-knop in v05.** Werkt niet in de claude.ai-preview iframe. Voor de testfase opent Sicko de artifact in een nieuwe tab, of publiceert. Voor de definitieve versie kan de print-functie aangepast worden naar een fallback (apart venster genereren).

## Geparkeerd tot na v05

In de oplegnotitie van 26276 staan deze als taken met de tag `#parkeerd-tot-na-v05`:

- Geëxporteerde claude.ai-chats systematisch importeren in `20 brondocumenten/notities/`
- Projectgeschiedenis chronologisch reconstrueren via geïmporteerde chats en archiefdocumenten
- Verificatie van twee bekende inconsistenties (Zeilschool-score 25 versus 26, Leiderdorp-label "Goed" of "Redelijk") bij hertoets op v04
- Office@Work-check uitvoeren en verwerken in vervolgvoorstel fase 2 (open vraag van Linda sinds 19 februari)
- Bevindingen-samenvatting en sjablonenadvies voor fase 2
- Vervolgvoorstel fase 2 inclusief business case (toets aan Lida's 3x ROI) en fasering

## Open ontwerpvragen

**Billing-model van de tool.** Bij open van de claude.ai-Remix-code via `</>` checken of er een embedded API-key in de HTML staat (Model A, kosten via Sicko's API-account) of dat `window.claude.complete()` wordt gebruikt (Model B, kosten naar bezoeker). Voor publiek gepubliceerde tools is Model B veiliger. Aandachtspunt voordat de gepubliceerde link breed verspreid raakt.

**Pro versus Team-plan.** Parkeren tot model uitontwikkeld is. Team biedt organisatie-interne sharing, Pro alleen openbaar publiceren. Voor de validatiefase met meerdere parallelle reviewers is Team logischer.

**Begrijpelijkheid als 25e criterium.** Open ontwerpvraag voor de matrix, te beslissen na validatie met meerdere plannen door zowel AI als menselijke beoordelaars.

## Verborgen werkjes voor de Verkenner

Windows-permissies blokkeren via shell:

- Doublures in `20 brondocumenten/materiaal/vergelijking/intern-BCM/`, `/extern-Buhrs/` en `/extern-DeWijdeBlik/` (drie .md-bestanden)
- Vier lege mappen op project-root van 26276 (`beoordelingen/`, `dashboards/`, `projecten/`, `templates/`)
- Het deprecated bestand `D:\NOT\WRK\80 dashboards\kanban-actief.md`

Verwijderen via Windows Verkenner zodra je tijd hebt.

## Afspraken voor schrijven richting Linda

Bij elke memo of update aan Linda:

- Maximaal 1.500 woorden, circa 4 A4
- Eén besluit tegelijk, geen lijst van keuzes
- Krap begroten met expliciete tolerantie
- Spreek de taal van grip en controle
- Toets aan Lida's 3x ROI als business case in beeld komt

## Voor de volgende chat

Begin met het kort lezen van de oplegnotitie `26276 kwaliteitsprogramma.md`, deze stand-notitie, en het centrale `taken.md`. De memory-laag biedt de impliciete grond. Belangrijkste vervolgstap: het testresultaat van v05 Ooievaarshoek vergelijken met de bestaande beoordeling, en bij groen licht publiceren voor Simone. Daarna richten op de update aan Linda en het oplossen van de geparkeerde acties.
