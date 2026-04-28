---
type: deliverable
categorie: presentatie
onderwerp: AI in de praktijk, Beaumont
datum_versie: 2026-04
aantal_slides: 21
status: gepresenteerd
bron: ppt/26276 13 ai kwaliteitsprogramma [01].pptx
tags: [deliverable, presentatie, AI]
---

# AI in de praktijk, Beaumont 2026

*Inhoud van de presentatie als markdown. Voor visuele weergave de oorspronkelijke .pptx in Teams.*

## Slide 1


AI in de praktijk

Beaumont Communicatie & Management
Voorjaar 2026

## Slide 2

AI IN DE PRAKTIJK

Aanleiding: twee sporen één vraagTeam AI en Team Kwaliteit trekken samen op. Toewerken naar concrete toepassing.
Hoe gaan we werken met AIDrie niveau’s van werken met AI, welke gebruiken we wanneer
Prototype beoordelingsmatrix communicatie- en participatieplannerZo hebben we hem samengesteld, gebouwd en getest.
Toolstrategie en business vaseVoorgestelde AI-architectuur: Copilot + Claude. Over kosten, ROI en fasering.
Tijdlijn en volgende stappenWerking agent(s) verbeteren voor andere documenttypen (offertes, omgevingsplannen, etc.). Werkprocessen automatiseren. Besluit over tooling en training.

AI IN DE PRAKTIJK: BEAUMONT 2026

## Slide 3

AI IN DE PRAKTIJK

Kwaliteit: Standaardisering omgevingsanalyseSimone en Jacqueline werken aan standaardisering van de omgevingsanalyse.
Kwaliteit: communicatie- en participatieplannen beneden de maatManagement constateert te grote wisselende kwaliteit bij planvorming (bijsturen nodig)
AI: integratie AI en verbetering van werkprocessen Leon, Linda, Arjati & Sicko verkennen mogelijkheden, beperkingen
Verbindende vraag: Kan AI helpen om werk te versnellen en verbeteren

TWEE SPOREN ÉÉN VRAAG

## Slide 4





AI IN DE PRAKTIJK

HUIDIG AANBOD

1.000.000 tokens is ongeveer 750.000 woorden. Dus een heel dossier, tientallen rapporten tegelijk. Gemini biedt de grootste context van de grote vier, met tot 2 miljoen tokens en native verwerking van tekst, audio, afbeeldingen en video.

## Slide 5

AI IN DE PRAKTIJK

CO-PILOT EN RAG

Retrieval-Augmented Generation
In plaats van alleen te antwoorden vanuit wat het model weet, zoekt Copilot eerst relevante stukken op uit jouw eigen organisatiedata
Daarvoor gebruikt het de vraag als basis voor het antwoord.
Je vraagt iets, Copilot zoekt, selecteert en genereert vanuit de data die je opslaat.
Het reservoir: Teams + SharePoint + OneDrive
Copilot haalt relevante tekstfragmenten op uit SharePoint, OneDrive en Exchange via de Microsoft Graph. Daarvoor hoeft data niet opnieuw geïndexeerd of beveiligd in een apart systeem. Teams-gesprekken, vergadernotities, e-mails en documenten vormen samen het kennisreservoir.

EXTRA

## Slide 6

AI IN DE PRAKTIJK

PRO EN CON COPILOT RAG [MOMENTEEL]

Voordelen
Werkt op data van de organisatie zelf
Antwoorden komen uit echte documenten, niet uit algemene trainingsdata
Werkt zonder dat je documenten hoeft te uploaden of te kopiëren
Respecteert bestaande rechtenstructuren. Je ziet alleen wat jij mag zien
Doorzoekt automatisch e-mail, Teams, SharePoint en OneDrive
Copilot-prompts koppelen aan SharePoint-lijsten of -sites voor gerichtere antwoorden
Schaalbaar naar de volledige kennisbasis
Zwaktes
Copilot selecteert relevante fragmenten maar weegt bronnen niet. Verouderde data kan even zwaar meetellen als nieuwste versie
Nieuwe of gewijzigde documenten worden niet real-time geïndexeerd. Soms is er vertraging tussen opslaan en beschikbaar zijn
Bij rommelige SharePoint-structuur haalt Copilot inconsistente informatie op
Afbeeldingen, video's en niet-tekstuele content worden grotendeels genegeerd
De effectieve promptruimte is beperkt tot circa 128K tokens. Bij grote dossiers selecteert het systeem, niet de gebruiker

EXTRA

## Slide 7

AI IN DE PRAKTIJK

WERKEN MET AI IN DRIE NIVEAUS

AD HOC PROMPTING
Losse vragen stellen
Je typt een vraag, je krijgt een antwoord.
Geen voorbereiding, geen geheugen.
✓ Laagdrempelig, snel aan de slag
✗ Geen consistentie, geen geheugen, resultaat sterk afhankelijk van hoe je vraagt

CONTEXT ENGINEERING
Werken met kaders & richtlijnen
Je geeft AI instructies, achtergrondkennis en spelregels
AI werkt vanuit dezelfde basis
✓ Consistente output, minder uitleg nodig, schaalbaar
✗ Vraagt voorbereiding en onderhoud; werkt alleen binnen één sessie of project

AGENTIC AI
AI beheert kaders & richtlijnen
Je geeft de AI een doel
Inrichten van verschillende (sub)agents om doel te bereiken
✓ Complexe meerstaps taken zelfstandig uitvoeren
✗ Vraagt technische inrichting, toezicht blijft nodig

## Slide 8

AI IN DE PRAKTIJK

De bestanden in dit project geven de AI een vaste basis voor elk gesprek:
Masterprompt — wie is de AI, wat zijn de spelregels, hoe communiceert hij?
Contextsamenvatting — wat is het project, wie zijn de betrokkenen?
Learnings — wat heeft de AI al geleerd van eerdere sessies?
Documentenlijst — welke bronnen zijn beschikbaar?
Verslagen — wat is er al geproduceerd?

CONTEXT ENGINEERING

## Slide 9

AI IN DE PRAKTIJK

CONTEXT ENGINEERING

Voorbeeld kennisbundelingStructureert alle bronnen, betrokkenen en doelen van het project. De AI weet daardoor altijd de context zonder dat je het opnieuw hoeft uit te leggen.

Voorbeeld geleerde lessenLegt vast wat werkte, wat niet werkte en welke ontwerpkeuzes zijn gemaakt. Zo bouwt kennis zich op over sessies heen.

Voorbeeld masterpromptVertelt de AI wie hij is, wat het project inhoudt en hoe hij moet werken. Dit is de vaste basis voor elke sessie.

## Slide 10

AI IN DE PRAKTIJK

MULTI-AGENTIC WORKING

Claude Agents De Claude Agent SDK laat zien hoe een agent zelfstandig werkt: hij zoekt informatie op, verdeelt taken over sub-agents, controleert zijn eigen output en bouwt kennis op over sessies heen.
Voor de gebruiker voelt het als één opdracht geven. Op de achtergrond coördineert de AI een heel werkproces en past kaders aan tijdens het proces. Je werkt met 10 Claudes tegelijkertijd.

## Slide 11

AI IN DE PRAKTIJK

Logische eerste stap vanaf ad-hoc prompting
Een enkelvoudige agent. Geen complex systeem. Eén agent met een vaste taak: een document beoordelen aan de hand van vooraf bepaalde criteria.
Beoordelingsmatrix gebruikt criteria, scoringslogica en toetsvragen. Een consultant laadt een plan in en de agent levert een gestructureerd oordeel.
Wat dit oplevert ten opzichte van ad hoc prompting:
Elke beoordeling volgt dezelfde lat
Geen afhankelijkheid van hoe je de vraag formuleert
Resultaat is herhaalbaar en vergelijkbaar

AGENT 1: PLAN KWALITEITSCONTROLEUR

## Slide 12

Het Beaumont canvas als basis
De matrix is gebouwd op het bestaande werkproces van Beaumont: van intake tot borging. Geen nieuw raamwerk, maar een vertaling van wat goede planvorming bij ons al inhoudt.
Elk onderdeel van het canvas is omgezet naar concrete toetsvragen. Zo ontstond een instrument dat herkenbaar is voor collega's én objectief genoeg voor een eerlijke beoordeling.

AI IN DE PRAKTIJK

## Slide 13

AI IN DE PRAKTIJK

Factor C Omgevingsgericht werken als toetscriterium. Is de opgave geformuleerd vanuit de leefwereld van betrokkenen, niet de systeemwereld van de organisatie?
CASI (gedragswetenschappelijk) Criterium 3 en 16: alleen verplicht als gedragsverandering een expliciet doel is. Zijn gedragsbelemmeringen geanalyseerd en sluiten interventies aan op de gedragsbepalers van de doelgroep?
BPKV Rijkswaterstaat (Beste Prijs KwaliteitsVerhouding)De scoringssystematiek: 0–3 plus NR (nadelig, −1 punt). Ontleend aan kwaliteitsbeoordeling in de aanbestedingspraktijk.
IAP2-participatiespectrumCriterium 8: Is het participatieniveau expliciet benoemd en is de belofte aan deelnemers consistent met de aanpak? Criterium 19: Is terugkoppeling naar participanten geborgd?
Overkoepelende kwaliteitscriteria (Michels/BPKV)Criteria 21–24: Consistentie, Relevantie, Meerwaarde, Haalbaarheid. Een NR op één van deze vier vereist altijd herschrijving — ongeacht de totaalscore.

AANVULLENDE CRITERIA

## Slide 14

AI IN DE PRAKTIJK

24 TOETSVRAGEN VIER NIVEAUS

## Slide 15

AI IN DE PRAKTIJK

Functionaliteit
Plantekst plakken + naam opgeven
Twee opties aanvinken: gedragsverandering en creatief concept (beoordeling criteria 3, 13 en 16)
Volledige beoordeling op alle 24 criteria via de Beaumont matrix v02
Score per criterium (3/2/1/0/NR) met onderbouwing en verbeterpunt
Totaalscore, eindoordeel én fasescores in 1 overzicht
NR-waarschuwing overkoepelende criteria (21–24)
Prioritaire verbeterpunten (max. 5)
Afdrukken als PDF via de browser
Ten opzichte van de vorige versie
Matrix v02 als basis (was v01)
Criteria 3, 13 en 16 correct als optioneel gemarkeerd
Robuustere JSON-parsing bij afgekapte responses
max_tokens: 8000 voor langere plannen

CHANGES IN VERSIE 2

## Slide 16

AI IN DE PRAKTIJK

We laden een bestaand communicatieplan in en stellen één vraag. De agent beoordeelt het plan op alle 24 criteria, geeft een score per onderdeel en formuleert verbeterpunten.
Wat je zo meteen ziet is een werkend prototype — geen eindproduct. De methodiek is solide, de technische omgeving wordt nog doorontwikkeld.
LET OP:
Beoordeling is een hulpmiddel, geen vervanging van professioneel oordeel
Kwaliteit van output hangt af van kwaliteit van het ingevoerde plan
AI kan nuance missen die een ervaren adviseur wel ziet
Versie 0.1:
Beaumont Communication Plan Assessment Tool | Claude

DEMO: AGENT IN ACTIE (1)

## Slide 17

AI IN DE PRAKTIJK

We laden een bestaand communicatieplan in en stellen één vraag. De agent beoordeelt het plan op alle 24 criteria, geeft een score per onderdeel en formuleert verbeterpunten.
Wat je zo meteen ziet is een werkend prototype — geen eindproduct. De methodiek is solide, de technische omgeving wordt nog doorontwikkeld.
LET OP:
Beoordeling is een hulpmiddel, geen vervanging van professioneel oordeel
Kwaliteit van output hangt af van kwaliteit van het ingevoerde plan
AI kan nuance missen die een ervaren adviseur wel ziet
Versie 0.2:
Beoordelingstool Communicatieplannen (2)

DEMO: AGENT IN ACTIE

## Slide 18

AI IN DE PRAKTIJK

Rol Copilot uit naar in de hele organisatie.
Onderdeel van bekende Microsoft 365-omgeving
Voldoet volledig aan AVG en EU-datavereisten
Per direct inzetbaar in Word, Teams, Outlook en PowerPoint.
Advies: zet basistraining AI (+ certificaat) in voor alle medewerkers
Claude inzetten voor de zwaardere projecten
Claude wordt nu al via Microsoft Copilot Cowork steeds beter geïntegreerd in dezelfde beveiligingsomgeving. De keuze voor Copilot is ook een keuze voor Claude.
Eén ecosysteem. Twee niveaus van werken.

TOOLSTRATEGIE EN COMPLIANCE

## Slide 19

AI IN DE PRAKTIJK

KOSTENVERGELIJKING & ROI

Wanneer iedere consultant gemiddeld 2 uur per week bespaart
25 consultants × 2 uur × 47 weken = 2.350 uur per jaar. Tegen interne kostprijs: €164.500 aan capaciteitswinst. Terugverdientijd licentiekosten: minder dan 2 maanden.
Copilot versnelt het werk. Claude verbetert de kwaliteit van de uitkomst. Samen bepalen ze of AI bij Beaumont een kostenpost is of een concurrentievoordeel.

## Slide 20

AI IN DE PRAKTIJK

FASERING – TIJDLIJN – VOLGENDE STAPPEN

Voor de zomer 2026De beoordelingsagent wordt verder doorontwikkeld en getest met collega's. Eerste ervaringen met kwaliteitsgestuurde AI worden gedeeld binnen het team. Simone en Jacqueline R. zijn betrokken we bij de validatie. Ook inzet voor omgevingsplan
Rond de zomer 2026Besluit over uitrol Copilot voor de hele organisatie. Claude voor power users. Governance, spelregels en training worden ingeregeld.
2027De agent wordt uitgebreid naar andere documenttypen: offertes, omgevingsplannen, projectplannen. Werkprocessen worden stapsgewijs geautomatiseerd.
VandaagGeen besluit. We willen laten zien waar we aan werken, wat er al staat, en vragen of je wilt meedenken over de volgende stappen.

## Slide 21
