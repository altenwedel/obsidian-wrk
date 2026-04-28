---
type: dashboard
soort: taken
gemaakt: 2026-04-27
laatste_update: 2026-04-27
tags:
  - dashboard
  - taken
  - cross-project
---

# Taken

Centraal taakdashboard. De taken zelf leven in de oplegnotitie of `00 project.md` van elk project; de queries hieronder halen ze dynamisch op via de Tasks-plug-in. Afvinken in een query schrijft door naar het bron-bestand.

## Vandaag

```tasks
not done
due today
sort by priority
```

## Achterstallig

```tasks
not done
due before today
sort by due
```

## Deze week

```tasks
not done
due before in 7 days
sort by due
```

## Komende twee weken

```tasks
not done
due after in 7 days
due before in 21 days
sort by due
```

## Per project

### 26276 kwaliteitsprogramma

```tasks
not done
tags include #project/26276
sort by due
```

### 26277 subsidie aanvraag

```tasks
not done
tags include #project/26277
sort by due
```

### 26284 Ravenstein Ooievaarshoek

```tasks
not done
tags include #project/26284
sort by due
```

## Zonder deadline

```tasks
not done
no due date
group by tag
```

## Recent afgevinkt

```tasks
done
sort by done reverse
limit 10
```

## Werking

Taken hebben de volgende structuur in de bron:

`- [ ] Taakomschrijving #task #project/CODE 📅 YYYY-MM-DD`

De `#task`-tag is geen verplichting (Tasks-plug-in pakt standaard alle `- [ ]` op), maar wel handig om "echte" taken te onderscheiden van checkbox-bullets in andere contexten. De `#project/CODE`-tag maakt filtering per project mogelijk. Het kalender-emoji is de deadline.

Een taak afronden:

`- [x] Taakomschrijving #task #project/CODE ✅ YYYY-MM-DD`

Dat ✅-emoji wordt door Tasks automatisch gezet bij afvinken in een query, wanneer "Set done date on every task" in de plugin-instellingen aanstaat.

## Bron-pagina's

- [[BCM/26276 kwaliteitsprogramma/26276 kwaliteitsprogramma|26276 kwaliteitsprogramma (oplegnotitie)]]
- [[VRK/26277 subsidie aanvraag/26277 subsidie aanvraag|26277 subsidie aanvraag (oplegnotitie)]]
- [[BCM/26284 Ravenstein Ooievaarshoek/00 project|26284 Ravenstein Ooievaarshoek (00 project)]]
