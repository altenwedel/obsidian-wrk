---
type: versiecover
onderwerp: beoordelingstool
huidige_versie: HTML v0X (productie), v05 in voorbereiding
laatste_update: 2026-04-28
eigenaar: Sicko van Dijk
tags: [versiecover, beoordelingstool]
---

# Beoordelingstool, versiebeheer

De beoordelingstool is het AI-instrument dat de Beoordelingsmatrix toepast op een aangeleverd communicatie- of participatieplan. Deze pagina houdt de versies en architectuurkeuzes bij.

## Architectuur-trajectory

Sicko's hypothese tijdens het schrijven van deze pagina: de nul-versie verwees naar een online aanwezig document met inhoud, terwijl de nieuwere versie alleen verwijst naar de kennis. Klopt grotendeels, met één nuance.

**v0 (projectprompt-v0.md, gearchiveerd).** Een prompt voor een Claude-project met meerdere bestanden in de bibliotheek: rubric, masterprompt, plan-van-aanpak, werkplan, plus PDFs van Michels en BPKV. Gebruik via chat. De context van de Plantoetser zat in het project zelf, niet in de prompt. Op het [drie-niveau-framework](../../20%20brondocumenten/literatuur/drie-niveau-framework-ai.md) is dit niveau 2 (context engineering, werkomgeving-AI). Term gebruikt: "rubric".

**Huidige HTML-tool (productie, geen versie-nummer maar UI-label "Matrix V02").** Standalone HTML-pagina met directe Anthropic API-call, max_tokens 8000, model claude-sonnet-4. De matrix-kennis zit in de prompt zelf (geen verwijzing naar externe bestanden). De plantekst wordt door de gebruiker geplakt en de tool levert per-criterium scores, fasescores, totaaloordeel en prioritaire verbeterpunten. Dit is nog steeds niveau 2, maar met een verschoven leveringsmodel: van project-met-bibliotheek naar formulier-met-embedded-prompt. Term gebruikt: "matrix".

**v05 (in voorbereiding, niet gerealiseerd).** UI-redesign volgens de mockup van 28 april (clean form, "Plan aanleveren", optionele plannaam, plantekst, twee opties voor gedragsverandering en creatief concept, één primary action "Beoordeling starten"). Belangrijk aandachtspunt: het MATRIX-label in de tool staat op v02, terwijl de actuele matrix v04 is. Bij v05 moet die uitlijning hersteld zijn.

## De architectonische verschuiving

De kern van de evolutie van v0 naar de huidige tool zit in drie verschuivingen die los van elkaar gebeurd zijn.

| Aspect | v0 (projectprompt) | Huidige HTML-tool |
|---|---|---|
| **UI-paradigma** | Chat (open dialoog) | Formulier (gestructureerde invoer) |
| **Kennisplaatsing** | Externe bestanden in projectbibliotheek | Embedded in de prompt |
| **Doelgroep** | Sicko zelf, ontwikkelpartner-modus | Linda en Simone, eindgebruikers |
| **Output-vorm** | Vrij tekst, volgens werkwijze | Gestructureerd JSON, opgemaakt in HTML |
| **Beheerbaarheid** | Files in Claude-project of GitHub | Code-wijziging in HTML-bestand |

Niveau in het AI-framework blijft hetzelfde (context engineering, niveau 2). Wat verandert is de **toegankelijkheid voor eindgebruikers**: van een AI-werkomgeving voor de bouwer (Sicko) naar een tool voor de operator (Linda, Simone).

## Versiehistorie

| Versie | Datum | Wijziging | Auteur | Status |
|---|---|---|---|---|
| HTML productie (label "Matrix V02") | 2026-04 | Eerste werkende standalone HTML-tool met directe API-call, JSON-output, embedded matrix-kennis | Sicko | actueel, met openstaande JSON-bug (zie diagnose) |
| v0 | 2026-03 | Projectprompt voor Claude-project, verwijzend naar rubric-v1, masterprompt, en literatuur in projectbibliotheek | Sicko | gearchiveerd, in `---/projectprompt-v0.md` |

## Sharing-architectuur, vastgesteld 2026-04-28

Cowork live artifacts zijn op dit moment **niet deelbaar** met collega's. Sharing staat wel op de Anthropic-roadmap maar is nog toekomstmuziek. Voor het bereikbaar maken van de tool voor Linda, Simone en anderen is dus claude.ai met een gepubliceerde artifact de werkbare route.

Beaumont heeft een Pro-account, wat betekent dat publiceren altijd openbaar is (iedereen met de link kan de artifact openen, niet vindbaar via zoekmachines). Echte organisatie-interne sharing vraagt om een Team-plan.

**Werkwijze die hieruit volgt:**

- **Ontwikkeling**: in Cowork, met directe toegang tot de WRK-vault en Beaumont-bestandsstructuur
- **Publicatie voor collega's**: via claude.ai, als gepubliceerde artifact in een Claude Project
- **Iteratie**: bij doorontwikkeling republishen vanuit dezelfde claude.ai-chat, zodat de URL constant blijft en Linda en Simone één vaste link houden
- **Discipline**: Cowork-versie is het werkbestand, claude.ai-publicatie is de afgeleide momentopname

Voor de matrix v04 (niet de tool) ligt publicatie laag-risico, want hij is gebaseerd op publieke bronnen. Voor de tool zelf ligt het iets gevoeliger gegeven huisstijl en bedrijfsspecifieke prompts; bewust beslissen samen met Linda.

Volledige achtergrond in [chat-transcript van 28 april 2026](../../20%20brondocumenten/notities/260428-chat-claudeai-tool-architectuur.md).

## Open punten richting v05

- JSON-parsefout fixen volgens [bug-diagnose](../beoordelingstool-bug-diagnose.md) (max_tokens naar 16000, prompt strakker, partial-parser)
- MATRIX-label in de tool synchroniseren met actuele matrix-versie (nu v04)
- UI-redesign op basis van de mockup van 28 april 2026
- Tool uitbreiden met de pre-assessment uit matrix v04 (knock-out, gedragsverandering, creatief concept)
- Oorspronkelijke claude.ai-chat terugvinden waarin de tool is gemaakt, zodat republish vanaf dezelfde URL mogelijk blijft
- Bespreken met Linda: blijft Pro voldoende of upgraden naar Team voor de validatiefase met meerdere parallelle reviewers
- Architectuurkeuze: blijft de tool gepubliceerde claude.ai-artifact, of bewegen we naar externe hosting (SharePoint, Beaumont-server) voor strakkere IP-controle

## Bronnen broncode

De HTML-broncode van de huidige tool staat **niet** in deze Obsidian-vault. De bug-diagnose meldt: "broncode is niet in Teams te vinden... HTML-tool moet ergens lokaal bij Sicko staan." Bij v05 wordt de broncode in deze map opgenomen, eventueel met een eigen submap voor `assets/` (CSS, fonts) en een `bron/` voor de HTML.

## Archief

Eerdere versies staan in [---/](---/).
