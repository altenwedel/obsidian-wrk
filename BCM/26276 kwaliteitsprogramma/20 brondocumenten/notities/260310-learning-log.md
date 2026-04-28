---
type: notitie
soort: learning-log
datum_primair: 2026-03-10
datums_secundair: [2026-02]
herkomst: GitHub
aangeleverd_op: 2026-04-28
bron_bestandsnaam: 04-learning-log.md
bevat:
  - learnings-plantoetser-1maart-tot-10maart-2026
  - learnings-kwaliteitsprogramma-februari-2026
tags: [notitie, learning-log, ontwerpbeslissingen, kwaliteitsprogramma, plantoetser]
---

> **Intake-notitie.** Dit bestand bevat twee learning logs die op GitHub gecombineerd in één bestand stonden. Voor de duidelijkheid zijn ze hieronder als aparte secties weergegeven. Eerste log gaat over de Plantoetser-ontwikkeling (1-10 maart 2026); tweede log gaat over de bredere PvA-voorbereiding (februari 2026).

# Learnings — Beaumont Plantoetser
**Sessie: 1 maart – 10 maart 2026 | Versie 1.0**

Dit document bevat de lessen, ontwerpbeslissingen en inzichten uit de eerste ontwikkelsessies van het Beaumont plantoetser-project. Bedoeld als kennisgeheugen voor toekomstige iteraties.

---

## 1. Methodologie en inhoud

### 1.1 Michels als structurele basisstandaard
- Het boek bevat geen kant-en-klare beoordelingslijst maar verspreid wel expliciete normen.
- De sterkste kwaliteitseis van Michels: interne consistentie. Is er één logische lijn van analyse via inzichten, strategie en concept naar uitvoering?
- Michels benoemt vier rationele beoordelingscriteria die als samenhangende set gelden: **Consistentie, Relevantie, Meerwaarde, Haalbaarheid**.
- "Een strategie die iedereen meteen acceptabel vindt, inspireert niemand." Expliciete keuzes zijn een kwaliteitscriterium.
- Michels mist: participatiespecifieke eisen, gedragsverandering als doeltype, juridisch kader voor overheidsplannen.

### 1.2 Factor C als overheidsstandaard
- Factor C is de leidende methodiek binnen de Rijksoverheid en veel decentrale overheden.
- Kernonderscheid: de opgave formuleren vanuit de **leefwereld van de burger**, niet vanuit de systeemwereld van de organisatie.
- Het verhaal begint altijd met **Luisteren**, dan pas Antwoorden. Een overheidsboodschap die start met wat de organisatie wil zeggen, voldoet niet aan de standaard.
- De vijf pijlers: Opgave → Omgeving → Strategie → Verhaal → Aanpak.
- De omgevingsanalyse gaat verder dan een stakeholderlijst: actoren worden gewogen op belangen, machtspositie en onderlinge relaties via krachtenveldanalyse en sociogram.

### 1.3 IAP2 en de participatieparadox
- Het IAP2-spectrum (informeren / consulteren / adviseren / coproduceren / meebeslissen) is de standaard voor het expliciteren van participatieniveaus.
- **Kernrisico zonder IAP2:** de participatieparadox — burgers worden uitgenodigd mee te denken maar ervaren dat hun inbreng niets veranderd heeft aan een reeds vaststaande uitkomst. Dit ondermijnt draagvlak én juridische houdbaarheid.
- Het participatieniveau moet de belofte aan de deelnemer bevatten: "Wij zullen uw aanbevelingen zoveel mogelijk integreren" is iets anders dan "Wij houden u op de hoogte."
- Expliciet benoemen van het participatieniveau is door de Nationale Ombudsman benoemd als vereiste voor behoorlijk bestuur.

### 1.4 BPKV-scoringsschaal
- De BPKV-schaal (Rijkswaterstaat aanbestedingen) biedt een legitieme vijfpuntsschaal met overheidsgezag: 3 (Zeer goed) / 2 (Goed) / 1 (Redelijk) / 0 (Neutraal) / NR (Nadelig).
- Kwaliteitswaarden: 100% / 60% / 25% / 0% / -50%.
- **Cruciale kanttekening:** de BPKV-schaal beoordeelt meerwaarde ten opzichte van minimumeisen. Ze werkt alleen als de minimumeisen eerst helder zijn — dat is de rubric.
- Het M.A.R.K.-systeem (ook in het aanbestedingsdocument) is bruikbare beoordelingslogica: plans onderscheiden op *waarom* (verklaringen) versus *hoe weten we dat het werkt* (onderbouwingen). Beweren is niet hetzelfde als onderbouwen.

### 1.5 Aanvullingen op Michels voor overheidsplannen
- **Juridische houdbaarheid:** een participatieplan is in de overheidscontext een juridisch document. Motiveringsplicht (Omgevingswet), zorgvuldigheidsbeginsel (Awb) en kennisgevingsplicht zijn harde eisen. Tekortschietende participatie of motivering kan leiden tot vernietiging van het besluit door de bestuursrechter.
- **Terugkoppeling als zelfstandig criterium:** niet alleen of iets met inbreng is gedaan, maar ook *waarom* bepaalde suggesties niet zijn overgenomen. Dit ontbreekt in de praktijk het vaakst.
- **Inclusiviteit:** een plan is onvolledig als het niet beschrijft hoe moeilijk bereikbare groepen worden betrokken. Taalniveau B1, mix van digitale én fysieke kanalen.
- **KPI's voor effect én bereik:** standaardvalkuil is alleen bereik meten (kwantitatief). Effectmeting (is de boodschap begrepen? is houding veranderd?) is apart vereist.
- **Gedragsvraag als activerend principe:** ook bij doelen als draagvlak of betrokkenheid helpt het om het gewenste gedrag expliciet te benoemen — ook als gedragsverandering niet het primaire doel is.

### 1.6 Bronnen bewust niet opgenomen
- **ISO 44001:** beoordeelt kwaliteit van samenwerkingsrelaties tussen organisaties, niet de inhoud van een plan. Niet plantoetsend.
- **WCAG 2.1:** technische uitvoeringsstandaard voor digitale kanalen, geen plannorm.
- **Communicatiekompas Markdown-exports:** al volledig verwerkt in de rubric. Webscrapes zijn niet de gezaghebbende bron.

---

## 2. Rubric-ontwerp

### 2.1 Structuurkeuzes
- De rubric volgt de vijf-fasenstructuur (Intake / Analyse / Strategie / Aanpak / Borging), niet de twaalf Michels-bouwstenen. Reden: de fasestructuur is herkenbaarder voor planschrijvers en klanten.
- 24 criteria in totaal, gelijk gewogen in versie 1.0 (max. 72 punten).
- Criteria 3 (Gedragsvraag) en 16 (Interventies) zijn optioneel — alleen verplicht bij expliciete gedragsdoelen.
- Criterium 8 (IAP2-niveau) staat in de **analysefase**, niet bij de intake. Reden: intake en analyse zijn iteratief — het participatieniveau kan worden bijgesteld als de stakeholderanalyse daartoe aanleiding geeft.

### 2.2 Speciale status overkoepelende criteria
- De overkoepelende criteria 21–24 (Consistentie, Relevantie, Meerwaarde, Haalbaarheid) hebben een drempelstatus: een NR op één ervan vraagt altijd om herschrijving van het plan, ongeacht de totaalscore.
- Reden: deze criteria meten of het plan als geheel klopt. Een plan dat intern onsamenhangend is of het werkelijke probleem niet oplost, is onbruikbaar ongeacht de scores op onderdelen.

### 2.3 Gelijke weging in v1.0
- Alle 24 criteria tellen gelijk mee. Gedifferentieerde weging (bijv. overkoepelende criteria dubbel tellen) is uitgesteld tot er praktijkervaring is met de huidige versie.
- Normering: 60–72 = Zeer goed | 42–59 = Goed | 24–41 = Redelijk | < 24 = Onvoldoende.

---

## 3. Projectarchitectuur

### 3.1 Twee omgevingen
- **Ontwikkelomgeving** (dit Claude-project + GitHub): rubric bouwen, testen, itereren. Experimenten horen hier.
- **Productieomgeving** (Claude-sessie met masterprompt + rubric als context): plannen beoordelen, rapporten exporteren voor Linda en Simone. Stabiele versies horen hier.
- Het onderscheid vroeg maken voorkomt dat experimentele versies in gebruik worden genomen voor serieuze beoordelingen.

### 3.2 Single source of truth
- De rubric (`rubric-v1.md`) is de enige bron waaruit Claude beoordeelt. Alle andere documenten zijn contextdocumenten of afleidingen.
- Als de rubric wordt aangepast, wordt de versie verhoogd en wordt de wijziging gelogd in `versiehistorie`.
- De rubric als Markdown in het Claude-project zorgt dat Claude hem altijd beschikbaar heeft zonder uploads per sessie.

### 3.3 Wat in Claude-project hoort vs. wat in GitHub
| In Claude-projectfiles | In GitHub |
|---|---|
| `rubric-v1.md` (actuele versie) | Alle versies met versiehistorie |
| `masterprompt.md` (actuele versie) | Testlogs en beoordelingsresultaten |
| `projectprompt.md` | Ontwerpbeslissingen |
| Michels PDF (primaire bron) | README en documentindex |
| `Beoordelingen_plannen.pdf` (BPKV) | Geanonimiseerde voorbeeldbeoordelingen |

### 3.4 Productieomgeving werkt al
- Niveau 1 (Claude Projects met projectprompt + rubric) is de snelste weg en al beschikbaar.
- Niveau 2 (een zelfstandige artifact of agent met interface) bouwen als de rubric stabiel is na de eerste testbeoordelingen.

---

## 4. Beoordelingslogica

### 4.1 Kernprincipes voor Claude als beoordelaar
- Beoordeel wat er **staat**, niet wat er bedoeld lijkt te zijn. Een intentie zonder uitwerking scoort maximaal een 1.
- Maak onderscheid tussen **beweren** en **onderbouwen**. "Wij betrekken alle stakeholders" zonder concretisering scoort lager dan een plan dat beschrijft hoe, wanneer en via welke methode.
- Constructief maar eerlijk: benoem wat ontbreekt én geef een concrete aanwijzing hoe het versterkt kan worden.

### 4.2 NR als signaalscore
- NR is niet "slecht" maar "risicovol of ontbrekend". Het activeert een harde drempel bij criteria 21–24.
- NR telt mee als -50% van de maximale waarde van dat criterium in de totaalscore.

### 4.3 Beoordelingsvarianten
- **Volledige beoordeling:** alle 24 criteria in volgorde, totaalscore, eindoordeel, drie prioritaire verbeterpunten.
- **Snelle scan:** alleen criteria 21–24 (overkoepelend), plus aanwijzing welke drie onderdelen meest urgent zijn.
- **Persona-review:** aanvullend op de rubric, vanuit het perspectief van een specifieke stakeholder (bijv. bezorgde omwonende of sceptische wethouder).

---

## 5. Werkwijze en proceservaringen

### 5.1 Iteratief proces
- Intake en analyse zijn iteratief in de praktijk. Het is normaal dat je in de analyse ontdekt dat de intakevraag te smal was gesteld. De rubric volgt deze logica.
- Hetzelfde geldt voor de rubric zelf: versie 1.0 is een werkend startpunt, geen eindproduct. Bijstellen op basis van testbeoordelingen is een bewuste keuze.

### 5.2 Documentformaten per gebruik
- **Markdown (.md):** werkformaat voor Claude, versiebeheer, GitHub. Altijd beschikbaar als projectbestand.
- **Word (.docx):** deelformaat voor Linda en Simone. Leesbaar, printbaar, bewerkbaar.
- **Conversie:** de Word-rubric is een export van de Markdown; de Markdown is de bron. Niet andersom.

### 5.3 Scope-discipline
- Het project heeft expliciete grenzen: fase 1 = methodologie ontwikkelen en testen. Fase 2 = implementeren bij collega's. Fase 3 = bredere AI-tooling.
- ISO 44001 en WCAG zijn bewust geparkeerd. Risico van te brede rubric: verlies van scherpte en bruikbaarheid voor dagelijkse toepassing.

---

## 6. Open vragen en volgende iteraties

### Voor rubric v2.0 (na testfase)
- Moeten de overkoepelende criteria (21–24) dubbel tellen in de score?
- Welke criteria zijn het meest onderscheidend gebleken in de testbeoordelingen?
- Hoe gaan we om met plannen die meerdere deelplannen bevatten (bijv. communicatieplan met apart participatieluik)?
- Is gedifferentieerde weging wenselijk nadat er praktijkervaring is?

### Voor de volgende sessie
- Eerste testbeoordelingen uitvoeren op Beaumont-plannen en/of openbaar beschikbare gemeentelijke plannen.
- Testlog aanmaken (`testlog.md`) met bevindingen.
- Evalueren of de toelichtingen per criterium voldoende concreet zijn voor consistente scoring door anderen.

---

## Versiehistorie

| Versie | Datum | Wijziging |
|---|---|---|
| 1.0 | 10 maart 2026 | Eerste versie op basis van sessie 1 maart – 10 maart 2026 |

---
---

# Learnings — Kwaliteitsprogramma Werkprocessen Beaumont

*Vastgelegd: februari 2026*
*Bron: chatsessie voorbereiding PvA*

---

## Strategische inzichten

### Beaumont wil Client Intimacy, niet alleen efficiëntie
Linda's strategie voor 2026 draait om klantpartnerschap. Het kwaliteitsprogramma is geen losstaand verbeterproject maar een onderdeel van die bredere ambitie. Positioneer het altijd in die context — niet als "we gaan processen fixen" maar als "we gaan beter werk leveren."

### Drie kernvraagstukken hangen samen maar zijn niet gelijk
AI-implementatie, werkproces-standaardisering en kwaliteitsbewustzijn zijn drie verschillende dingen. De volgorde is belangrijk: eerst standaardisering, dan AI als ondersteuning, dan kwaliteitsontwikkeling. AI zonder gestandaardiseerd proces levert niets op.

### Het bureau staat onder druk
Tarieven staan onder druk, de markt krimpt, relevantie moet je verdienen. Dit is geen luxeproject — het gaat over de toekomstbestendigheid van het bureau. Dat geeft urgentie aan het voorstel.

### Focus op operations
Linda's strategiemodel heeft vier kwadranten: operations, marketing, netwerk, HR & talent. Het advies is om uitsluitend op operations te focussen. De andere kwadranten zijn apart en komen niet aan bod. Dat voorkomt scope creep en houdt het beheersbaar.

---

## Inzichten over de opdrachtgever

### Linda denkt in grip en controle
Ze waarschuwde expliciet voor het eerdere AI-programma dat uit de hand liep. SMART-afspraken, scope-bewaking en kostenbeheersing zijn voor haar geen bijzaak maar voorwaarde. Het voorstel moet die taal spreken.

### Linda heeft maximaal 10 minuten leestijd
Als directeur van een bureau met 25 mensen zit ze in aanbestedingen, strategie en aansturing. Ze scant documenten, ze leest ze niet. Alles boven de 1.500 woorden (circa 4 A4) is te veel.

### De 3x-vuistregel
Lida (mede-oprichter) hanteert de regel dat iedere geïnvesteerde euro minimaal drie euro moet opleveren. Bij €2.189 investering betekent dat: het vooronderzoek moet aantoonbaar leiden tot minimaal €6.500-€7.000 aan waarde. Dit is de toetssteen voor de business case in het definitieve PvA.

### Linda wil één besluit tegelijk
Ze hoeft nu alleen te beslissen over fase 1 (32 uur). Het vervolgtraject is een doorkijk met een bandbreedte, geen commitment. Geef haar niet drie keuzes als er maar één besluit nodig is.

---

## Inzichten over het team

### Simone en Jacqueline zijn al actief
Ze werken aan standaardisering van de omgevingsanalyse en het intake-proces. Via het Operations-kanaal loopt een uitvraag voor voorbeeldplannen. Dit is essentieel: het traject is geen extern opgelegd plan maar bouwt voort op initiatief van binnenuit.

### Eerste voorbeelddocumenten zijn binnen
Via de uitvraag zijn al drie documenten gedeeld: samenvatting Nieuwenhuysenbuurt, communicatiestrategie Nieuwenhuysenbuurt, communicatieplan Hoogwoud. Dit is het startmateriaal voor de analyse.

### Iedereen doet het op zijn eigen manier
Dat geldt voor plannen, Miro-borden, omgevingsanalyses. Er zijn wel schablonen voor offertes, maar niet voor plannen of analyses. De uitdaging is om van "ieder zijn eigen manier" naar een gedeeld werkproces te komen zonder creativiteit te doden.

---

## Inzichten over AI-tooling

### CoPilot als werkpaard (80%), Claude voor zwaar werk (20%)
Dit is de voorgestelde verdeling. CoPilot werkt binnen de beschermde Microsoft 365-omgeving en voelt context aan in Teams. Claude is sterker bij projecten met grote contextvensters en rijke bronmaterialen. De ironie: Microsoft gebruikt zelf Claude voor ontwikkelingswerk.

### RAG is een kansrijke toepassing
Retrieval Augmented Generation — het verwerken van bronmateriaal (omgevingsanalyse, beleidsdocumenten, intakegegevens) richting een gestructureerd plan — is gedemonstreerd aan Linda en Simone. Beide waren geïnteresseerd. Dit wordt een van de proof-of-concepts in fase 1.

### Persona-reviews als kwaliteitstoets
Simone opperde het idee om plannen te laten reviewen door fictieve persona's (wethouder, bezorgde omwonende, raadslid). Dit is een derde AI-toepassing naast RAG en planvorming. Adversarial model usage — je eigen plan kritisch laten beoordelen door AI.

### AI is het instrument, niet het doel
Kwaliteitsbewustzijn en gestandaardiseerde processen komen eerst. Je kunt niet blind vertrouwen op technologie. De kennis om een goed plan te beoordelen blijft essentieel. Net als met de magnetron: het instrument heeft een beperkt toepassingsgebied.

### AI-geletterdheid wordt een verplichting
Sinds 2 februari 2025 verplicht de AI-verordening organisaties om werk te maken van AI-geletterdheid. Een basiscertificaat voor alle 25 medewerkers kost intern €3.267, extern €6.000. Dit staat los van het huidige voorstel maar is een parallel traject.

---

## Learnings over het voorstelproces

### Begin bij het denkwerk, niet bij het document
De eerste versies van het PvA (13 secties, 2.500+ woorden) waren nodig om het denken te structureren. Maar dat werkdocument is niet wat de opdrachtgever krijgt. Het verschil tussen jouw voorbereiding en haar beslisdocument is cruciaal.

### Compact slaat beter aan dan compleet
Het definitieve voorstel is circa 700 woorden. Dat is een kwart van het eerste PvA. Alles wat weg kon is weg: de business case op basis van schattingen, kwaliteitscriteria voor toekomstige fases, twee scenario's voor iets wat nog niet bestaat. Minder tekst = meer impact.

### Oplegvel en PvA zijn twee documenten met twee doelen
Het oplegvel (of compact voorstel) is het beslisdocument: wat, hoeveel, wat moet ik doen? Het uitgewerkte PvA is het achtergronddocument voor wie de details wil. Niet iedereen hoeft alles te lezen.

### Schrijf vanuit het besluit, niet vanuit het onderzoek
Linda moet beslissen: geeft ze 32 uur vrij, ja of nee? Alles in het voorstel moet naar dat besluit toeleiden. Secties die daar niet aan bijdragen, horen er niet in.

### Fasering met go/no-go is de sleutel
Fase 1 los definiëren als afgebakend product met vaste prijs. Fases 2-4 als doorkijk met bandbreedte (44-78 uur, €3.000-€5.300). Geen blanco cheque, geen automatisch vervolg. Dit geeft Linda grip en jou bescherming.

### Het uurtarief bepaalt de toon
€68,40 per uur is een intern tarief. Bij 32 uur is het totaal €2.189. Dat is minder dan wat één communicatieplan een klant kost. Zet de investering altijd in perspectief van wat het oplevert, niet van wat het kost.

---

## Learnings over begroten

### Krap begroten en transparant zijn over de marge
32 uur met 10% tolerantie (plafond 35 uur / €2.394) is beter dan 42 uur met lucht. Het signaleert aan de opdrachtgever dat je scherp begroot en dat je aan de bel trekt als het uitloopt. De afspraak is: melden vóórdat je doorgaat.

### AI versnelt maar garandeert niets
Een deel van het onderzoekswerk gaat met AI-tooling. Dat versnelt het proces maar is geen garantie dat alles snel gaat. Benoem dat eerlijk in het voorstel.

### Weet waar het risico zit
De analyse van bestaande plannen (8 uur) en de RAG-test (6 uur) zijn de onderdelen waar je het eerst uitloopt. Als bronmateriaal laat binnenkomt of plannen erg divers zijn, kost het meer tijd. De concurrentieanalyse en afstemming zijn voorspelbaarder.

### Heb een terugvalscenario
Als Linda het te breed vindt, zijn er drie routes: alleen de analyse (12 uur / €820), één pilotplan als proof of concept (8-10 uur), of de vier onderzoeken als losse blokken aanbieden. Niet verdedigen maar doorvragen: "wat zou voor jou een goede eerste stap zijn?"

---

## Learnings over PRINCE2

### Volledig PRINCE2 is overdreven voor dit traject
Maar lichtgewicht elementen voegen waarde toe. Wat er al in zit: manage by stages (fases met go/no-go), defined roles, risk management, learn from experience, focus on products.

### Drie elementen die het sterker maken
Een business case (maar pas met echte cijfers in fase 1, niet op basis van schattingen). Kwaliteitscriteria per fase (wanneer is een product goedgekeurd?). Toleranties (hoeveel mag je afwijken voordat je escaleert?).

### Wat je kunt overslaan
Formeel change control, apart communicatieplan voor het project, highlight reports, gescheiden management en delivery stages. Dat is apparaat voor een groter project.

---

## Referentiemateriaal

### Bronnen uit de gesprekken
Het communicatiecanvas is afgeleid van Wil Michels (Beaumont/Babbage-versie). Linda noemde Publiec en Factor C als mogelijke referenties voor de sector. Babbage heeft een eigen AI-toepassing ontwikkeld (men is er niet helemaal blij mee). Marlijn Wessels van Babbage is gesprekspartner geweest.

### Studio Claro briefing-format
De 12 elementen (achtergrond, doelstelling, doelgroepen, inzicht, propositie, bewijs, mogelijke richting, toonzetting, opdracht, budget, timing, proces) zijn bruikbaar als inspiratie voor een intake-checklist. Niet letterlijk overnemen, maar de structuur van achtergrond via doelstelling naar concrete opdracht is precies het soort gestandaardiseerd denkproces dat we zoeken.

### Voorbeelddocumenten
Samenvatting resultaten werksessie communicatie Nieuwenhuysenbuurt, Communicatiestrategie en aanpak Nieuwenhuysenbuurt, Communicatieplan Hoogwoud 2025-2026. Deze zijn gedeeld via het Operations-kanaal.

---

## Actiepunten

| # | Actie | Wie | Status |
|---|---|---|---|
| 1 | Voorstel versturen aan Linda via Teams | Sicko | Gereed |
| 2 | Mail naar Simone om document omgevingsanalyse op te vragen | Sicko | Open |
| 3 | Uitvraag communicatieplannen bij collega's | Linda/Simone | Loopt |
| 4 | Go/no-go Linda op fase 1 | Linda | Wacht op voorstel |
| 5 | Teams-omgeving inrichten voor project | Sicko | Na akkoord Linda |
| 6 | Tussentijdse afstemming plannen | Sicko | Week 10 |
| 7 | PvA opleveren | Sicko | Week 11 |
