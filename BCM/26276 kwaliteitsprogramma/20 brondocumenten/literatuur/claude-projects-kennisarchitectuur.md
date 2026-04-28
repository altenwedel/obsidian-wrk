---
type: literatuur
onderwerp: kennisarchitectuur Claude Projects
bron: mat/01. projectarchitectuur/BCM26276-projectarchitectuur.md
tags: [literatuur, claude-projects, kennisarchitectuur]
---

# Kennisarchitectuur voor Claude Projects: een complete methodologie

**Claude Projects is het krachtigste platform voor kennisintensief consultancywerk**, mits je de kennisarchitectuur bewust opzet. Dit rapport biedt een compleet raamwerk voor Nederlandse freelance consultants en onderzoekers die Claude als persistent AI-assistent willen inzetten bij langlopende projecten. De kern: behandel je Claude Project niet als chatvenster, maar als een **levend kennissysteem** met structuur, versioning en onderhoudscycli — vergelijkbaar met hoe je een persoonlijke kennisbank (PKM) zou opzetten, maar dan AI-native.

De methodologie combineert inzichten uit de Claude-community, PKM-frameworks (Zettelkasten, PARA, Building a Second Brain), en ervaringen van professionele consultants die Claude Projects dagelijks inzetten. Het resultaat is een kant-en-klare template die je direct kunt toepassen.

---

## Hoe je kennisbestanden structureert in een Claude Project

Claude Projects ondersteunt PDF, DOCX, CSV, TXT, HTML, Markdown en codebestanden tot **30 MB per bestand**. Uit tests blijkt dat Markdown (.md) en plain text (.txt) de meest token-efficiënte formaten zijn — HTML gebruikt dubbel zoveel tokens door de tags. Bij betaalde plannen (Pro/Max/Team) schakelt Claude automatisch over naar **RAG-modus** wanneer de context vol raakt, wat de effectieve capaciteit circa 10x vergroot.

De optimale bestandsarchitectuur voor een consultancyproject bevat zes kernbestanden, georganiseerd op **functie** (niet op onderwerp):

**`00-project-context.md`** — Projectachtergrond, doelstellingen, stakeholders, scope, beperkingen en domeinspecifiek jargon. Dit is het "wie, wat, waarom" van het project. Bevat een terminologietabel zodat Claude consistent de juiste termen gebruikt.

**`01-system-prompt.md`** — Backup/versie van je masterprompt (de eigenlijke instructies voer je in via het "Set project instructions"-veld). Bewaar hier ook eerdere versies met datum en rationale voor wijzigingen.

**`02-domain-knowledge.md`** — Domeinkennis, frameworks, referentiemodellen en vakinhoudelijke context. Denk aan sectorspecifieke regelgeving, methodologieën, of klantspecifieke bedrijfsprocessen.

**`03-style-guide.md`** — Schrijfstijl, tone of voice, voorkeuren voor output-formaat, taalgebruik (Nederlands/Engels), en concrete voorbeelden van gewenste en ongewenste output.

**`04-learning-log.md`** — Accumulerende inzichten uit eerdere sessies: correcties, ontdekkingen, beslissingen met rationale, en patronen die Claude moet onthouden. Dit bestand groeit mee met het project en vormt het "geheugen" dat sessies overbrugt.

**`05-document-registry.md`** — Index van alle geüploade bestanden met korte beschrijving, datum van laatste update en versienummer. Fungeert als kaart van de kennisbank zodat zowel jij als Claude snel het juiste bestand vindt.

Voor naamgeving geldt: gebruik **genummerde prefixen** (`00-`, `01-`) voor laadvolgorde, **kebab-case** voor leesbaarheid, en neem bij klantprojecten een klantprefix op: `acme-brand-guidelines.md`. Claude's zoekfunctie gebruikt prefix-matching, dus zet het belangrijkste woord vooraan.

---

## Sessies scheiden per werktype binnen één project

Een cruciaal inzicht: **chats binnen een Claude Project delen géén context met elkaar**. Alleen de project-instructies en kennisbestanden worden in elke chat geladen. Dit betekent dat je bewust moet nadenken over sessie-scoping.

De effectiefste strategie voor consultants is **scope per werktype** met beschrijvende namen:

- **Analysesessies**: `2026-03-10 Marktanalyse Q1` — gericht op data-interpretatie en onderbouwde conclusies
- **Schrijfsessies**: `Rapport hoofdstuk 3: Bevindingen` — gericht op contentcreatie met de juiste tone of voice
- **Planningsessies**: `Projectplanning fase 2` — gericht op structuur, tijdlijnen, risico's
- **Onderzoekssessies**: `Desk research concurrentieanalyse` — gericht op informatie verzamelen en samenvatten
- **Parkeerplaats-sessie**: Eén generieke chat voor losse vragen die geen eigen context verdienen

Begin elke sessie met een duidelijke doelstelling in je eerste bericht: *"In deze sessie gaan we [specifiek doel]. Gebruik [specifiek kennisbestand] als uitgangspunt."* Dit helpt Claude direct de juiste bestanden te raadplegen.

**Het brugmechanisme tussen sessies** is de kennisbank zelf. Na een belangrijke sessie werk je `04-learning-log.md` bij met nieuwe inzichten en beslissingen. Zo bouw je een "geëxternaliseerd geheugen" op dat alle toekomstige sessies informeert. Freelance consultant Matt Stockton beschrijft dit als een **compounding knowledge loop**: elke sessie maakt de volgende waardevoller.

Wanneer maak je een nieuw **Project** aan versus een nieuwe **chat**? Gebruik aparte Projects wanneer je een andere kennisbasis, andere persona, of ander vertrouwelijkheidsniveau nodig hebt. Gebruik aparte chats (binnen hetzelfde Project) wanneer je dezelfde kennisbasis benut maar een ander type werk doet.

---

## PKM-frameworks vertaald naar AI-workflows

De drie dominante PKM-methoden bieden elk unieke inzichten voor het opzetten van Claude Projects.

**Zettelkasten → atomaire kennisbestanden.** Het principe van "één idee per notitie" vertaalt direct naar modulaire contextbestanden. Lange, allesomvattende documenten dwingen Claude om door irrelevante content te waden. **Korte, gefocuste bestanden** (elk over één concept) stellen Claude's RAG-systeem in staat om precies de relevante stukken te vinden. Paul Kruchoski formuleerde het kernprincipe: "Breaking knowledge into focused, linkable atomic notes means Claude can quickly find and connect exactly the pieces needed." Voor consultants betekent dit: maak per deelonderwerp een apart kennisbestand in plaats van één megadocument.

**PARA → organisatie op actie, niet op onderwerp.** Tiago Forte's PARA-methode (Projects, Areas, Resources, Archives) mapt natuurlijk op Claude Projects. Een actief consultancyproject krijgt eigen kennisbestanden (Projects), doorlopende verantwoordelijkheden zoals klantrelatiebeheer worden Areas, referentiemateriaal wordt Resources, en afgeronde projecten worden gearchiveerd. De kernles: organiseer op **actionability**. Bestanden die je dagelijks raadpleegt staan bovenaan; achtergrondmateriaal onderaan.

**Building a Second Brain → progressive summarization.** Forte's CODE-framework (Capture, Organize, Distill, Express) werkt krachtig met Claude. Het "Distill"-principe — gelaagde compressie van informatie — vertaalt naar het bijhouden van zowel volledige bronbestanden als beknopte samenvattingen in je kennisbank. Forte's concept van **Intermediate Packets** (herbruikbare werkfragmenten zoals vergadernotities, onderzoekssamenvattingen, concept-analyses) wordt in Claude Projects de bouwstenen waarmee Claude grotere outputs assembleert. Hoe meer Intermediate Packets in je kennisbank, hoe rijker en specifieker Claude's output wordt.

De **emergente best practice** in de community is een hybride aanpak: Zettelkasten voor atomaire structuur, PARA voor organisatielogica, en BASB's progressive summarization voor het beheren van informatiediepte. Meerdere onafhankelijke practitioners zijn op dezelfde stack uitgekomen: **Obsidian (lokale Markdown-bestanden) + Claude Code/Projects + Git** als het AI-native PKM-fundament.

---

## Een effectieve masterprompt schrijven

De masterprompt (project-instructies) is het "brein" van je Project — het bepaalt hoe Claude zich gedraagt in élke chat. Anthropic's eigen richtlijn: *"Think of Claude as a brilliant but new employee who lacks context on your norms."*

Een bewezen template-structuur voor consultancyprojecten:

```markdown
# Rol & Identiteit
Je bent [specifieke rol] met expertise in [domeinen]. Je werkt als 
[relatie tot gebruiker, bijv. "senior research partner voor een 
Nederlandse managementconsultant"].

# Kerndoelen
[Primair doel van dit project in 1-2 zinnen]

# Kennisbank-instructies
Raadpleeg altijd eerst de kennisbestanden voordat je algemene kennis 
gebruikt:
- `00-project-context.md` voor projectachtergrond en scope
- `04-learning-log.md` voor eerdere beslissingen en inzichten
- `03-style-guide.md` voor schrijfstijl en taalvoorkeuren

# Werkwijze
- Analysemodus: [specifiek outputformaat voor analyses]
- Schrijfmodus: [aanpak voor content, inclusief taal en stijl]
- Planningsmodus: [framework voor planningsopdrachten]

# Gedragsregels
- Schrijf in het Nederlands tenzij anders gevraagd
- Verwijs altijd naar specifieke bronnen uit de kennisbank
- Geef geen generiek advies — baseer alles op onze projectcontext
- Bij onzekerheid: benoem expliciet wat je niet weet

# Wat je NIET moet doen
- Geen corporate jargon zonder inhoud ("synergy", "leverage")
- Nooit "het hangt ervan af" zeggen zonder de variabelen te benoemen
- Geen aannames over stakeholder-voorkeuren zonder in de context te checken

# Outputformaat
[Gewenste structuur, lengte, taal]
```

**Vijf cruciale principes** uit Anthropic's documentatie en community-ervaring:

Gebruik **XML-tags** (`<context>`, `<examples>`, `<instructions>`) voor ondubbelzinnige structurering van complexe instructies. Geef **concrete voorbeelden** — 3 tot 5 voorbeelden in `<example>`-tags verbeteren consistentie dramatisch. Leg het **waarom** uit achter instructies: "We gebruiken opsommingen omdat onze klant documenten in 30 seconden scant" werkt beter dan alleen "gebruik opsommingen." Plaats **data bovenaan en de vraag onderaan** — Anthropic's tests tonen tot 30% betere resultaten bij complexe multi-document inputs. En ten slotte: **itereer**. Begin eenvoudig, test, en voeg detail toe alleen waar Claude's output afwijkt van je verwachting.

---

## GitHub als versiebeheersysteem voor projectkennis

GitHub biedt een krachtige backing store voor Claude Project-kennis, met volledige versiebeheer, diffs, blame en rollback. Claude.ai heeft een **native GitHub-integratie**: klik op "+" in de kennissectie, selecteer "GitHub", en kies specifieke bestanden of mappen. Synchronisatie is handmatig (klik "Sync now") en haalt alleen bestandsnamen en -inhoud op van één specifieke branch.

Een aanbevolen repositorystructuur:

```
project-ai-knowledge/
├── README.md                    # Repo-overzicht
├── CHANGELOG.md                 # Versiegeschiedenis
├── knowledge/                   # Primaire kennisbestanden
│   ├── 00-project-context.md
│   ├── 01-system-prompt.md
│   ├── 02-domain-knowledge.md
│   ├── 03-style-guide.md
│   ├── 04-learning-log.md
│   └── 05-document-registry.md
├── prompts/                     # Geversioneerde prompttemplates
│   ├── system/
│   │   ├── main_v1.0.0.md
│   │   └── main_v1.1.0.md
│   └── templates/
│       └── analysis_v1.0.0.md
└── archives/                    # Vervangen kennisbestanden
    └── deprecated-file.md
```

Voor **promptversioning** past de community Semantic Versioning (SemVer) toe: **MAJOR** (2.0.0) bij fundamentele herstructurering of outputformaatwijzigingen, **MINOR** (1.1.0) bij verbeterde instructies of nieuwe voorbeelden, **PATCH** (1.0.1) bij typo's en kleine verduidelijkingen. Houd een `CHANGELOG.md` bij met datum, wijziging en rationale. Gebruik Git-tags (`git tag prompt-v1.1.0`) om releases te markeren.

De **dagelijkse workflow**: werk met Claude in het Project → vang nieuwe inzichten op → werk kennisbestanden lokaal bij → commit en push → klik "Sync now" in Claude. Voor geautomatiseerde sync bestaan tools als **ClaudeSync** (Python, één-weg sync) en **claude-pyrojects** (CLI met GitHub App-integratie), al zijn dit onofficiële tools.

---

## Herijkingsprotocol: kennis onderhouden over tijd

Kennisbestanden die niet worden onderhouden degraderen snel. Een gelaagd reviewsysteem voorkomt dit:

**Per sessie** leg je nieuwe inzichten direct vast in `04-learning-log.md`. Noteer correcties in het format: "❌ Eerder aangenomen: [X]. ✅ Werkelijkheid: [Y]. Gecorrigeerd: [datum]." Flag inconsistenties die je opvalt voor latere review.

**Wekelijks** (15 minuten) consolideer je losse inzichten uit de learning log in gestructureerde kennisbestanden. Controleer of high-impact bestanden nog actueel zijn. Dit is het moment om Intermediate Packets (vergadernotities, onderzoeksfragmenten) te verwerken.

**Maandelijks** (30 minuten) doe je een spot-check van alle kennisbestanden. Controleer of externe afhankelijkheden zijn veranderd, of terminologie consistent is, en of referenties nog kloppen. Werk versienummers bij.

**Per kwartaal** (1-2 uur) voer je een volledige **herijking** uit — het equivalent van een formele hervalidatie:

1. **Accuratesse-audit**: controleer alle kennisbestanden tegen de huidige realiteit
2. **Consistentiecheck**: kruisreferentie tussen bestanden op tegenstrijdigheden
3. **Relevantie-snoei**: archiveer content die >90 dagen niet is geraadpleegd (verplaats naar `archives/` met datumsuffix)
4. **Gapanalyse**: identificeer ontbrekende kennis op basis van recente sessiepatronen
5. **Effectiviteitsbeoordeling**: worden Claude's antwoorden beter of slechter? Welke bestanden zijn het meest/minst effectief?

Een kernprincipe uit de community: **archiveer, verwijder niet**. Verplaats verouderde bestanden naar een archiefmap met datumsuffix. Zo behoud je Git-historie en kun je altijd terugvallen. En: **prefereer verwijzingen boven kopieën** — embed geen fragmenten die snel verouderen, maar verwijs naar het bronbestand.

---

## Claude Projects vergeleken met alternatieven

Voor kennisintensief consultancywerk is Claude Projects de sterkste keuze, maar de juiste tool hangt af van het werktype. Claude Projects biedt een **200K token contextvenster** (versus 128K bij ChatGPT en 64K bij Microsoft Copilot), superieure nauwkeurigheid bij het citeren uit geüploade documenten, en de beste samenvattingskwaliteit in vergelijkende tests. Een 30-daagse ontwikkelaarstest toonde dat Claude Projects 18 van 24 taken won versus ChatGPT — niet door een slimmer model, maar door betere **infrastructuur voor kennisbeheer**.

**Google NotebookLM** (gratis) is complementair: het is strikt brongebonden en weigert buiten je bronnen te antwoorden, wat het ideaal maakt voor source-grounded research. De aanbevolen workflow is: gebruik NotebookLM voor brongebonden analyse, en kanaliseer bevindingen naar Claude Projects voor redenering en uitvoering. **Notion AI** is optimaal wanneer je team al in Notion werkt — het doorzoekt je hele workspace inclusief gekoppelde apps — maar het mist Claude's diepte in analyse en redenering. **ChatGPT Projects** wint op veelzijdigheid (beeldgeneratie, spraak, web search) maar verliest op contextcapaciteit en bronbetrouwbaarheid.

Voor een Nederlandse freelance consultant die primair analyse- en onderzoekswerk doet, is de aanbevolen stack: **Claude Projects** als primaire werkruimte, **NotebookLM** voor brongebonden research, **GitHub** voor versiebeheer van kennisbestanden, en **Obsidian** (optioneel) als lokale kenniseditor met Markdown-bestanden die direct naar Claude en GitHub synchroniseren.

---

## Quickstart-template: nieuw consultancyproject opzetten

Gebruik dit stappenplan wanneer je een nieuw Claude Project start voor een research- of analyseopdracht:

**Stap 1 — Project aanmaken.** Geef het project een beschrijvende naam met klantprefix: `Klant X | Marktanalyse Energietransitie | 2026-Q1`. Vermijd generieke namen.

**Stap 2 — Masterprompt invullen.** Gebruik de template uit de sectie hierboven. Begin minimaal (rol + kerndoel + 3 gedragsregels) en breid uit naarmate je patronen ontdekt in Claude's output.

**Stap 3 — Kennisbestanden uploaden.** Start met drie kernbestanden: `00-project-context.md` (achtergrond en scope), `03-style-guide.md` (stijl en taal), en `04-learning-log.md` (begint leeg, groeit mee). Voeg domeinkennis en document-registry toe zodra je bronmateriaal hebt.

**Stap 4 — GitHub-repo initialiseren.** Maak een repo aan met de aanbevolen directorystructuur. Verbind via Claude's GitHub-integratie. Commit initiële bestanden met tag `v0.1.0`.

**Stap 5 — Eerste sessies starten.** Open aparte chats per werktype. Begin elke chat met een expliciete doelstelling. Na afloop: werk de learning log bij met nieuwe inzichten.

**Stap 6 — Itereren en herijken.** Volg het wekelijkse/maandelijkse/kwartaalse reviewprotocol. Laat je kennisbank meegroeien met het project in plaats van alles vooraf te willen vastleggen.

---

## Conclusie

De sleutel tot effectief gebruik van Claude Projects voor consultancywerk is niet de technologie, maar de **discipline van kennisarchitectuur**. De community is geconvergeerd op een duidelijk patroon: modulaire Markdown-bestanden georganiseerd op functie, een masterprompt die gedrag en kennisgebruik expliciet definieert, sessies gescheiden per werktype met de kennisbank als brugmechanisme, en Git als versiebeheersysteem met een gelaagd herijkingsprotocol.

Het meest onderschatte inzicht uit het onderzoek: **je learning log is het waardevolste bestand** in je hele project. Het is het mechanisme waarmee Claude daadwerkelijk "leert" over sessies heen — niet door geheugen, maar doordat jij de feedback loop expliciet maakt. Consultants die dit bestand consequent bijhouden, rapporteren dat Claude's output na enkele weken merkbaar specifieker en relevanter wordt.

Tot slot: bouw je kennissysteem **agent-agnostisch** op. Markdown-bestanden in een Git-repo zijn niet gebonden aan Claude — ze werken morgen net zo goed met een ander AI-platform. Dat maakt je investering in kennisarchitectuur toekomstbestendig, ongeacht welk model of platform de standaard wordt.