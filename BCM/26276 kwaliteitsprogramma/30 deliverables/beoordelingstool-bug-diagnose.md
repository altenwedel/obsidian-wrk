---
type: diagnose
onderwerp: JSON-parsefout in beoordelingstool
gemeld_door: Simone Schouten
gemeld_op: 2026-04-23
status: open
prioriteit: hoog
tags: [bug, beoordelingstool, simone]
---

# Diagnose JSON-parsefout in beoordelingstool

## Wat Simone meldde

Op donderdag 23 april meldde Simone dat de Claude-tool een foutmelding gaf na het analyseren van een plan, vlak voordat de resultaten zouden worden weergegeven. Twee meldingen:

1. `Unterminated string in JSON at position 12119 (line 194 column 26)`
2. `Unexpected end of JSON input`

## Waarschijnlijke oorzaak

De Anthropic API-response wordt afgekapt voordat de JSON-output volledig is. Beide foutmeldingen passen bij dit beeld: bij melding 1 stopt de stream midden in een string, bij melding 2 stopt de stream voordat het object goed is afgesloten.

Twee mechanismen die hierbij spelen:

**`max_tokens: 8000` is te krap voor sommige plannen.** De huidige prompt vraagt om scoring per criterium (24 stuks) plus onderbouwing en verbeterpunten. Bij langere plannen of uitvoeriger onderbouwingen loopt de output gemakkelijk tegen de limiet aan. Het Ooievaarshoek-plan zat al in die buurt.

**De salvage-fallback redt niet wat half binnenkomt.** De huidige tool heeft een `try/catch` rond `JSON.parse()` maar geen partial-parsing. Zodra het object niet sluit, faalt de hele weergave.

## Voorgestelde fix

Drie ingrepen in de HTML-tool, in volgorde van impact.

**Verhoog `max_tokens` naar 16000.** Het model (`claude-sonnet-4`) kan dat aan en de extra ruimte voorkomt afkappen bij vrijwel alle plannen. Eenvoudigste fix, hoogste impact.

**Maak de prompt instrueert kort waar mogelijk.** Vraag om "korte onderbouwing per criterium (één zin)" in plaats van vrije tekst. Dat houdt de output compact en voorspelbaar.

**Bouw een echte partial-parser.** Voor het geval het toch fout gaat, een functie die de tekst doorloopt en alle volledig binnen gekomen criterium-objecten extraheert, ook als het laatste object onaf is. Werkwijze:

```javascript
function salvagePartialJSON(text) {
  // Zoek alle complete criterium-objecten in de stream
  const pattern = /\{\s*"criterium"\s*:\s*\d+[^{}]*\}/g;
  const matches = [...text.matchAll(pattern)];
  return matches.map(m => {
    try { return JSON.parse(m[0]); }
    catch { return null; }
  }).filter(Boolean);
}
```

Combineer met een waarschuwing aan de gebruiker dat het resultaat partieel is.

## Waar de broncode staat

Op de Teams-locatie `BCM - BCM 26276 kwaliteitsprogramma\cla\` of `\obs\` staat momenteel niets. De HTML-tool moet ergens lokaal bij Sicko staan. Bij oppakken van deze fix: tool ophalen, fixes doorvoeren, testen met een lang plan, terugkoppelen aan Simone.

## Vervolgactie

1. HTML-broncode lokaliseren (Sicko)
2. `max_tokens` aanpassen
3. Prompt aanscherpen
4. Salvage-functie inbouwen
5. Testen met Ooievaarshoek-plan (was de trigger)
6. Werkende link sturen naar Simone

## Bron

Foutmeldingen geverifieerd via screenshots van Simone, gedeeld in chat op 2026-04-23.
