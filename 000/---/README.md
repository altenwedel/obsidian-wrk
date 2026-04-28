---
type: index
gemaakt: 2026-04-27
laatste_update: 2026-04-27
tags: [dashboard, cross-project]
---

# WRK, cross-project dashboards

Centrale overzichten over projecten heen. Project-specifieke dashboards staan in `80 dashboards/` van het betreffende project zelf.

## Bestanden

| Bestand | Doel |
|---|---|
| [[000]] | Centraal taakdashboard, dynamisch gevoed door de Tasks-plug-in. Toont vandaag, achterstallig, deze week, komende twee weken, per project, zonder deadline, en recent afgevinkt |
| [[kanban-actief]] | Vervangen, kan via Verkenner weg. Was de eerste poging tot een statische Kanban; vervangen door `taken.md` |

## Werkwijze taakbeheer

Taken leven in de oplegnotitie of `00 project.md` van het project zelf. Daar worden ze geschreven met de volgende structuur:

`- [ ] Taakomschrijving #task #project/CODE 📅 YYYY-MM-DD`

De Tasks-plug-in haalt deze automatisch op in `taken.md` via queryblokken. Afvinken in een query schrijft direct door naar het bron-bestand. Geen handmatige synchronisatie nodig.

## Bron-pagina's per actief project

- [[BCM/26276 kwaliteitsprogramma/26276 kwaliteitsprogramma|26276 kwaliteitsprogramma (oplegnotitie)]]
- [[VRK/26277 subsidie aanvraag/26277 subsidie aanvraag|26277 subsidie aanvraag (oplegnotitie)]]
- [[BCM/26284 Ravenstein Ooievaarshoek/00 project|26284 Ravenstein Ooievaarshoek (00 project)]]

## Plug-in vereisten

| Plug-in | Doel | Status |
|---|---|---|
| Tasks | Taken aggregeren en afvinken via queries | Geïnstalleerd, default settings |
| Dataview (optioneel) | Bredere overzichten over projecten en bestanden | Nog niet vereist |
| Bases (optioneel) | Database-achtige views op notities en properties | Nog niet vereist |
| Kanban (optioneel) | Visuele kaartweergave per status, indien gewenst als alternatieve weergave | Niet nodig nu, kan later worden toegevoegd |
