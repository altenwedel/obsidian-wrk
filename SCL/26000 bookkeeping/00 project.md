---
klant: SCL
projectnummer: 26000
projectnaam: bookkeeping
volledige_naam: SCL 26000 bookkeeping
status: actief
gestart: 2025-01-01
projectleider: Sicko van Dijk
tags: [project, actief, financieel]
---

# SCL 26000 bookkeeping

Facturatie-administratie van Studio Claro BV. Zie [[dashboard]] voor het volledige overzicht.

---

## Actie nodig

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}
function kort(d) {
    if (!d) return "—";
    if (typeof d === "string") { let p = d.split("-"); return p[2] + "-" + p[1]; }
    return String(d.day).padStart(2,'0') + "-" + String(d.month).padStart(2,'0');
}
function dagen(d) {
    let dt = typeof d === "string" ? new Date(d) : d.toJSDate();
    return Math.floor((Date.now() - dt.getTime()) / 86400000);
}

const files = dv.pages().where(p => p.file.name.startsWith("facturen-") && p.facturen);
let alle = [];
for (let file of files) { for (let f of file.facturen) alle.push(f); }

let over = alle.filter(f => (f.status === "openstaand" || f.status === "herinnering") && dagen(f.datum) > f.termijn);
over.sort((a, b) => dagen(b.datum) - dagen(a.datum));

let bijna = alle.filter(f => f.status === "openstaand" && dagen(f.datum) <= f.termijn && dagen(f.datum) >= f.termijn - 5);

if (over.length > 0) {
    dv.table(["Factuur", "Datum", "Totaal", "Dagen over"],
        over.map(f => [f.nr, kort(f.datum), eur(f.totaal), (dagen(f.datum) - f.termijn) + "d"])
    );
}
if (bijna.length > 0) {
    dv.paragraph("Bijna over termijn: " + bijna.map(f => f.nr).join(", "));
}
if (over.length === 0 && bijna.length === 0) {
    dv.paragraph("Geen openstaande acties.");
}
```

---

## Stand van zaken

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const thisYear = dv.page("facturen-2026");
const lastYear = dv.page("facturen-2025");

if (!thisYear || !thisYear.facturen) { dv.paragraph("*Geen data.*"); } else {
    let facts = thisYear.facturen.filter(f => f.type !== "creditnota");
    let totalExcl = facts.reduce((s, f) => s + f.subtotaal, 0);
    let openBedrag = facts.filter(f => f.status === "openstaand" || f.status === "herinnering").reduce((s, f) => s + f.totaal, 0);
    
    let now = new Date();
    let maanden = now.getMonth() + 1;
    let gem = totalExcl / maanden;
    let prognose = gem * 12;
    
    let lastYearSP = 0;
    if (lastYear && lastYear.facturen) {
        lastYearSP = lastYear.facturen.filter(f => f.type !== "creditnota").filter(f => {
            let m = typeof f.datum === "string" ? parseInt(f.datum.split("-")[1]) : f.datum.month;
            return m <= maanden;
        }).reduce((s, f) => s + f.subtotaal, 0);
    }
    let groei = lastYearSP > 0 ? ((totalExcl - lastYearSP) / lastYearSP * 100) : 0;

    dv.table(["", ""], [
        ["Omzet YTD", eur(totalExcl)],
        ["Jaarprognose", eur(prognose)],
        ["vs 2025", (groei >= 0 ? "+" : "") + groei.toFixed(1) + "%"],
        ["Openstaand", eur(openBedrag)],
    ]);
}
```

---

## In deze map

| Folder | Inhoud |
|---|---|
| `bronnen/` | PDF-facturen en bankafschriften |
| `overzichten/` | [[dashboard]], jaarlijkse facturenoverzichten |
