---
type: index
gemaakt: 2026-04-26
laatste_update: 2026-04-27
versie: 0.3
eigenaar: Sicko van Dijk
---

# WRK, centrale werkmap

Eén plek waar alle projecten samenkomen. Markdown is de hoofdregel: alle inhoud in deze vault staat zoveel mogelijk in markdown, ook bestanden die origineel als Word, PDF of PowerPoint zijn aangeleverd.

## Klanten en projecten

| Klant | Projectnummer | Project | Status |
|---|---|---|---|
| AMC | 26261 | voetenboekje | placeholder |
| BCM | 26238 | dezonering wp | placeholder |
| BCM | 26270 | dsp extern | placeholder |
| BCM | 26276 | kwaliteitsprogramma | actief |
| BCM | 26278 | aedes presentatie | placeholder |
| BCM | 26283 | omgevingsvisie wassenaar | placeholder |
| BCM | 26284 | Ravenstein Ooievaarshoek | placeholder |
| CSP | 26199 | website redesign | placeholder |
| GLE | 26273 | GR 2026 | placeholder |
| GNM | 25265 | routekaart | placeholder |
| GNM | 26268 | jongerenroute | placeholder |
| PRI | 260001 | Argonaut | placeholder |
| SCL | 26000 | bookkeeping | placeholder |
| SCL | 26269 | website remake | actief |
| VAA | 26282 | fotoreportage | placeholder |
| VNC | 26275 | BWW Alkmaar | placeholder |
| VRK | 26277 | subsidie aanvraag | actief |

## Structuur

```
WRK/
├── README.md                                  Dit bestand
├── 80 dashboards/                             Cross-project dashboards (taken, status, etc.)
├── 90 templates/                              Cross-project templates (zodra van toepassing)
└── [klantcode]/                               Per klant een eigen folder
    └── [projectnummer projectnaam]/
        ├── 00 project.md                      Projectcontext, status, learnings
        ├── [projectnummer projectnaam].md     Oplegnotitie (coverpagina): samenvatting, te-doen, brondocumenten op datum, belangrijke data, visuele kern
        ├── 10 beoordelingen/                  Planbeoordelingen (alleen waar relevant)
        ├── 20 brondocumenten/                 Brondocumenten, geconverteerd naar markdown
        │   ├── notities/                      Vergader-, intake- en transcriptnotities, plus werkstanden
        │   ├── literatuur/                    Vakliteratuur en referentiematerialen
        │   └── materiaal/                     Klantmateriaal (huisstijl, publicaties, vergelijking)
        ├── 30 deliverables/                   Eindproducten, gegroepeerd per deliverable met versiecover
        ├── 80 dashboards/                     Overzichten binnen dit project
        └── 90 templates/                      Hergebruikbare templates voor dit project
```

De cross-project map `80 dashboards/` op vault-niveau bevat dashboards die over projecten heen gaan, zoals het centrale taakoverzicht. Project-specifieke dashboards (bijvoorbeeld een dashboard van planbeoordelingen) blijven in het project zelf.

## Naamgeving

| Onderdeel | Conventie | Voorbeeld |
|---|---|---|
| Klantfolder | Afkorting in hoofdletters | `BCM` |
| Projectfolder | Projectnummer en korte naam | `26276 kwaliteitsprogramma` |
| Subfolders binnen project | Tweecijferige prefix voor sortering | `10 beoordelingen` |
| Brondocumenten | `yymmdd-titel.md` (datum als prefix, sorteert chronologisch) | `260423-verslag-tussentijdsoverleg.md` |
| Versiebestanden | `[onderwerp]-vXX.md` | `beoordelingsmatrix-v04.md` |

Tweecijferige prefixes zorgen dat folders in een logische volgorde staan in plaats van alfabetisch. Hoofdwerk staat in de tien-reeks, brondocumenten en deliverables in de twintig- en dertig-reeks, dashboards en templates in de tachtig- en negentig-reeks (ondersteunend, dus onderaan).

## Onderscheid brondocumenten en deliverables

Het verschil tussen `20 brondocumenten/` en `30 deliverables/` is wie de afzender is.

| Folder | Inhoud | Voorbeelden |
|---|---|---|
| `20 brondocumenten/` | Materiaal dat van klant of derde naar Studio Claro komt | Mails, briefings, transcripten, feedback, referentiebeelden, huisstijlen |
| `30 deliverables/` | Werkproducten die Studio Claro maakt en oplevert | Script, storyboard, conceptfilm, definitieve animatie, rapport, ontwerp |

Een storyboard hoort dus in `30 deliverables/`, ook al is het in PDF-vorm aangeleverd: het is ons werkproduct dat we ter review aanbieden, niet input van de klant.

## Archief, klaar met een document

Wanneer een brondocument is verwerkt en niet meer actief geraadpleegd wordt, verhuist het naar de `---/` submap binnen de map waar het stond. Dat houdt de hoofdmap overzichtelijk en sorteert het archief altijd onderaan, omdat `---` alfabetisch achteraan staat. De inhoud blijft beschikbaar voor naslag, maar valt niet meer op tussen de actuele stukken.

De projectleider geeft aan wanneer een document "klaar" is voor archivering. Standaard blijft een brondocument in de hoofdmap totdat de signalen zijn verwerkt in de projectstukken of in een nieuwe versie van een deliverable.

## Versiebeheer

Documenten waarvan meerdere versies bestaan krijgen een eigen submap binnen `30 deliverables/`, met:

- Een `README.md` als cover-pagina met versietabel
- De huidige versie in de submap zelf
- Een `---/` map voor het archief

Een nieuwe versie krijgt altijd een hoger versienummer en wordt in de cover-pagina toegevoegd. De voorgaande versie verhuist naar `---/`. De template voor de cover-pagina staat in `90 templates/template-versiecover.md` van het betreffende project (bij BCM 26276).

Op deze manier wonen concepten en eindversies van een deliverable samen in één submap, met de cover-pagina als ingang. Een aparte concepten-folder is niet nodig.

## Teams-naar-WRK mapping

De Teams-werkomgeving onder `C:\Users\HP\Studio Claro\` ordent op vorm en herkomst, met drie-letter-prefixes in lowercase. WRK ordent op conceptuele rol. Deze mapping is leidend bij intake.

| Teams | WRK | Toelichting |
|---|---|---|
| `doc/` | `30 deliverables/` | Word-documenten die Studio Claro maakt en oplevert |
| `lit/` | `20 brondocumenten/literatuur/` | Vakliteratuur en referentiestukken van derden |
| `mat/` | `20 brondocumenten/materiaal/` | Klantmateriaal: huisstijl, publicaties, vergelijking. Verder verbijzonderd in subfolders zodra zinvol (`vergelijking/`, `huisstijl/`, `publicaties/`) |
| `mdf/` | n.v.t. | In WRK is alles standaard markdown, geen aparte folder nodig |
| `not/` | `20 brondocumenten/notities/` | Vergader-, intake- en transcriptnotities, plus werkstanden |
| `ppt/` | `30 deliverables/` | Presentaties als deliverable, samen met andere eindproducten |

Bij intake van een nieuw project wordt brondocumentatie uit Teams geconverteerd naar markdown en geplaatst in de WRK-folder volgens deze mapping. De originele Teams-locatie wordt vermeld in de Bron-sectie of frontmatter van het document.

## Markdown als hoofdregel

Word, PDF en PowerPoint die in een project worden aangeleverd, worden geconverteerd naar markdown bij intake en geplaatst in `20 brondocumenten/`. Voor PDF en PowerPoint zijn er aparte conversieskills. Voor Word gebruiken we pandoc of mammoth. Beelden komen in een aparte `assets/` submap binnen het onderwerp.

Bij oplevering converteren we vanuit markdown terug naar het format dat de ontvanger verwacht (Word voor Linda, PDF voor archief).

## Bron van waarheid

De originele Teams-bestanden staan in `C:\Users\HP\Studio Claro\[klantcode] - [klantcode] [projectnummer] [projectnaam]\`. Deze vault is een gestructureerde, markdown-eerste werkkopie. Bij elke conversie wordt de originele Teams-locatie vermeld in de frontmatter of in een Bron-sectie van het document.
