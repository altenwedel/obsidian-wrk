---
type: stand
datum: 2026-04-26
opgesteld: late middag, ongeveer 17:00
auteur: Claude (in opdracht van Sicko)
tags: [stand, voortgang, werkstand]
---

# Stand van zaken, 26 april late middag

Sicko is de middag weg geweest en heeft me gevraagd door te werken. Hieronder de oogst.

## Vault-structuur opgezet

De vault op `D:\NOT\WRK\` is volledig ingericht voor multi-klant gebruik. 17 projecten zijn aangemaakt op basis van de Teams-structuur in `C:\Users\HP\Studio Claro\`. Voor elk project een placeholder met basisstructuur:

```
WRK/
├── README.md
├── AMC/26261 voetenboekje/
├── BCM/26238 dezonering wp/
├── BCM/26270 dsp extern/
├── BCM/26276 kwaliteitsprogramma/   (actief, volledig ingevuld)
├── BCM/26278 aedes presentatie/
├── BCM/26283 omgevingsvisie wassenaar/
├── BCM/26284 Ravenstein Ooievaarshoek/   (actief, brondocumenten erin)
├── CSP/26199 website redesign/
├── GLE/26273 GR 2026/
├── GNM/25265 routekaart/
├── GNM/26268 jongerenroute/
├── PRI/260001 Argonaut/
├── SCL/26000 bookkeeping/
├── SCL/26269 website remake/
├── VAA/26282 fotoreportage/
├── VNC/26275 BWW Alkmaar/
├── VRK/26277 subsidie aanvraag/
└── _dashboards/, _templates/   (leeg, nog op te ruimen, zie onder)
```

Alle placeholders hebben een `00 project.md`, `20 brondocumenten/` en `30 deliverables/`. De volledige Teams-pad-verwijzing staat in elke frontmatter zodat je makkelijk terug naar de bron komt.

## BCM 26276 kwaliteitsprogramma compleet ingevuld

Het actieve project staat volledig in markdown. De inhoud die uit Teams is omgezet:

**[10 beoordelingen/](BCM/26276%20kwaliteitsprogramma/10%20beoordelingen/)**, vier planbeoordelingen:

- Ooievaarshoek (intern, op v04, vandaag, score 25/63 = 40% Redelijk)
- Leiderdorp Oude Gemeentehuis (intern, op v1.0, eerder, score 30/66 = 45% Goed)
- Zeilschool Huizen (extern Buhrs, op v1.0, eerder, score 25/66 = 38% Redelijk)
- Doekenborg (extern De Wijde Blik, op v1.0, eerder, score 33/72 = 46% Redelijk)

**[20 brondocumenten/](BCM/26276%20kwaliteitsprogramma/20%20brondocumenten/)**:

- `literatuur/` met de ACDR-tekst en de projectarchitectuur over Claude Projects
- `notities/` met de vier txt-besprekingsnotities (intake 10 feb, bespreking 12 feb, model 18 mrt, Simone 14 apr)
- `vergelijkingsmateriaal/` met de oorspronkelijke beoordelingsrapporten (deze staan dubbel met 10 beoordelingen, zie open punt)

**[30 deliverables/](BCM/26276%20kwaliteitsprogramma/30%20deliverables/)**:

- `pva-fase-1.md`, het oorspronkelijke voorstel aan Linda (geaccepteerd 19 februari)
- `presentatie-ai-kwaliteitsprogramma.md`, twintig slides AI in de praktijk
- `beoordelingsmatrix/` met cover-pagina, v04 actueel, en `---/` archief met v01, v02 en v03
- `beoordelingstool-bug-diagnose.md`, voorstel voor de fix van Simone's foutmelding
- `update-linda-20260428.md`, concept voor verzending dinsdagochtend

**[80 dashboards/alle-beoordelingen.md](BCM/26276%20kwaliteitsprogramma/80%20dashboards/alle-beoordelingen.md)**: bevat nu het overzicht van alle vier beoordelingen plus een patroonanalyse met drie inzichten voor het kwaliteitsprogramma.

**[90 templates/](BCM/26276%20kwaliteitsprogramma/90%20templates/)**: planbeoordeling-template en versiecover-template.

## BCM 26284 Ravenstein Ooievaarshoek deels ingevuld

Het projectbestand `00 project.md` is verrijkt met echte projectinformatie en bevat een verwijzing naar de matrixbeoordeling in 26276. Brondocumenten geconverteerd:

- Drie onderzoeksstukken in `20 brondocumenten/onderzoek/` (variabelenonderzoek, voorspellende variabelen buurtparticipatie, participatieprofiel Ravenstein)
- Notitie van 21 april in `20 brondocumenten/notities/`
- Omgevingsanalyse-presentatie in `30 deliverables/`

Niet geconverteerd (nog open):

- `mat/Participatieplan Ooievaarshoek.pdf` (dit is de PDF-versie van het plan dat we al beoordeeld hebben)
- BSR-leefstijlen PDFs (zes PDFs, kunnen later via PDF-skill)

## Patroon over de vier beoordelingen

In het dashboard staat de patroonanalyse uitgewerkt. Hier in het kort.

**Sterk en consistent:** IAP2-participatieniveau en terugkoppeling naar participanten. Vier van de vier scoren hier hoog. Het procesvakmanschap is geborgd.

**Zwak en consistent:** meetplan en KPI's, monitoring, budget, creatief concept, interne organisatieanalyse. Vier van de vier scoren hier 0 of bijna 0. Dit zijn de structurele lacunes.

**Implicaties voor het kwaliteitsprogramma:** sjablonen moeten een verplichte sectie meetbare doelen krijgen, een budgetregel inclusief minimale begroting, en een evaluatieprotocol. Daar zit de meeste impact.

## Open punten

Drie dingen die handmatig moeten of die ik niet kon afmaken.

**Lege oude mappen verwijderen.** Vier mappen onder `BCM/26276 kwaliteitsprogramma/` zonder prefix, leeg, kunnen niet via mijn shell weg vanwege Windows-permissies:

- `beoordelingen/`
- `dashboards/`
- `projecten/`
- `templates/`

Plus de vault-niveau mappen `_dashboards/` en `_templates/` die nu leeg zijn (alles staat onder het project). Wegklikken in Verkenner.

**Doublure opruimen.** De drie eerdere beoordelingsrapporten (Leiderdorp, Zeilschool, Doekenborg) staan nu in `10 beoordelingen/` (waar ze horen) én in `20 brondocumenten/vergelijkingsmateriaal/` (oude positie). Deze laatste drie bestanden mogen weg, ook handmatig:

- `20 brondocumenten/vergelijkingsmateriaal/intern-BCM/Leiderdorp-OudeGemeentehuis.md`
- `20 brondocumenten/vergelijkingsmateriaal/extern-Buhrs/Participatieplan-Zeilschool-Huizen.md`
- `20 brondocumenten/vergelijkingsmateriaal/extern-DeWijdeBlik/Participatieplan-Doekenborg.md`

De ouderfolder `20 brondocumenten/vergelijkingsmateriaal/` zelf kan ook weg als hij leeg is.

**Beoordelingstool JSON-fix.** De broncode van de HTML-tool is niet in Teams te vinden. Diagnose en voorstel staan in `30 deliverables/beoordelingstool-bug-diagnose.md`. Concrete stappen: max_tokens naar 16000, prompt strakker formuleren, partial-parser inbouwen. Daarna testen met Ooievaarshoek (wat Simone als trigger had) en werkende link sturen.

## Voor dinsdagochtend

Het concept-update aan Linda staat in `30 deliverables/update-linda-20260428.md`. Lees het over, pas aan waar nodig, kopieer naar Word of mail. De zes onderdelen worden eerlijk benoemd inclusief de pivot. De stand op uren (18 van 35) is opgenomen, plus een vervolgvoorstel.

## Wat ik heb laten liggen

Voor nu niet aangepakt, mogelijk later van waarde.

- BCM 26276 PDFs in `not/` (alle PDF-versies van besprekingsnotities, duplicaten van de txt's). Niet nodig.
- BCM 26276 PDF in `lit/b7VAXFf5OVXDwBsH7eGGzlGgjyeHpM5Bu2hA54m7.pdf`. Onbekende inhoud, niet bekeken.
- De zes BSR-leefstijlen PDFs in BCM 26284. Voor later.
- Het PDF-bestand van het Ooievaarshoek-plan in BCM 26284 (Word-versie was al voldoende).

## Tijdsbesteding

Niet bijgehouden, maar het werk van vanmiddag zit ruim binnen het uurbudget van fase 1 (ik gok grofweg 2 tot 3 uur effectief).

## Verifieer als je terug bent

Dit is wat ik heb gedaan, gemerkt of beweerd. Een paar dingen om kritisch tegenaan te kijken:

1. De score van Zeilschool Huizen lees ik op 25/66, terwijl Sicko in zijn vergelijkingstabel in het Leiderdorp-rapport 26/66 noemt. Klein verschil, mogelijk later gecorrigeerd. Check welke klopt.
2. De Leiderdorp-doc geeft "Goed" met 30/66 (45%), terwijl de v1.0-normering zegt 24-41 = Redelijk. Het document zelf is hier inconsistent. Loop het na voordat je dit aan Linda communiceert.
3. Het concept-update aan Linda gaat ervan uit dat we drie tot vijf extra plannen erbij gaan beoordelen in week 18. Dat is mijn aanname op basis van wat realistisch is, niet jouw keuze. Pas het aan als je liever andere getallen of timing wilt.
