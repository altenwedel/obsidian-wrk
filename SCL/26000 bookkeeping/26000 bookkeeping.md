---
klant: SCL
projectnummer: 26000
projectnaam: bookkeeping
volledige_naam: SCL 26000 bookkeeping
status: actief
gestart: 2025-01-01
projectleider: Sicko van Dijk
teams_pad: SCL - 26000 bookkeeping
tags: [project, actief, financieel]
---

# SCL 26000 bookkeeping

Facturatie-administratie van Studio Claro BV.

---

## Open

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}
function kort(d) {
    if (!d) return "—";
    if (typeof d === "string") return d.slice(5);
    return String(d.month).padStart(2,'0') + "-" + String(d.day).padStart(2,'0');
}

const files = dv.pages().where(p => p.file.name.startsWith("facturen-") && p.facturen);
let open = [];
for (let file of files) {
    for (let f of file.facturen) {
        if (f.status === "openstaand" || f.status === "herinnering") {
            open.push(f);
        }
    }
}
open.sort((a, b) => dv.compare(a.datum, b.datum));

if (open.length === 0) {
    dv.paragraph("*Alles betaald!*");
} else {
    let totaal = open.reduce((sum, f) => sum + f.totaal, 0);
    dv.table(
        ["Factuur", "Datum", "Totaal", "⏱"],
        open.map(f => {
            let dagen;
            if (typeof f.datum === "string") {
                dagen = Math.floor((Date.now() - new Date(f.datum).getTime()) / 86400000);
            } else {
                dagen = Math.floor((Date.now() - f.datum.toJSDate().getTime()) / 86400000);
            }
            let late = dagen > f.termijn;
            let status = late ? "🔴 " + (dagen - f.termijn) + "d over" : (dagen + "/" + f.termijn + "d");
            return [f.nr, kort(f.datum), eur(f.totaal), status];
        })
    );
    dv.paragraph(`**Totaal open: ${eur(totaal)}**`);
}
```

---

## Hoe gaat het met de zaak?

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const thisYear = dv.page("facturen-2026");
const lastYear = dv.page("facturen-2025");

if (!thisYear || !thisYear.facturen) {
    dv.paragraph("*Geen data voor huidig jaar.*");
} else {
    let facts = thisYear.facturen.filter(f => f.type !== "creditnota");
    let totalExcl = facts.reduce((s, f) => s + f.subtotaal, 0);
    let totalIncl = facts.reduce((s, f) => s + f.totaal, 0);
    let openBedrag = facts.filter(f => f.status === "openstaand" || f.status === "herinnering").reduce((s, f) => s + f.totaal, 0);
    let betaaldBedrag = facts.filter(f => f.status === "betaald").reduce((s, f) => s + f.totaal, 0);
    
    let now = new Date();
    let maanden = now.getMonth() + 1;
    let maandgemiddelde = totalExcl / maanden;
    let prognoseJaar = maandgemiddelde * 12;
    
    let lastYearTotal = 0;
    let lastYearSamePeriod = 0;
    if (lastYear && lastYear.facturen) {
        let lyFacts = lastYear.facturen.filter(f => f.type !== "creditnota");
        lastYearTotal = lyFacts.reduce((s, f) => s + f.subtotaal, 0);
        lastYearSamePeriod = lyFacts.filter(f => {
            let m = typeof f.datum === "string" ? parseInt(f.datum.split("-")[1]) : f.datum.month;
            return m <= maanden;
        }).reduce((s, f) => s + f.subtotaal, 0);
    }
    
    let groei = lastYearSamePeriod > 0 ? ((totalExcl - lastYearSamePeriod) / lastYearSamePeriod * 100) : 0;
    let groeiIcon = groei >= 0 ? "📈" : "📉";
    
    let klanten = {};
    for (let f of facts) {
        if (!klanten[f.klant]) klanten[f.klant] = 0;
        klanten[f.klant] += f.subtotaal;
    }
    let topKlant = Object.entries(klanten).sort((a,b) => b[1] - a[1])[0];
    let concentratie = topKlant ? (topKlant[1] / totalExcl * 100) : 0;
    
    let betaaldeFacts = thisYear.facturen.filter(f => f.betaaldatum && f.betaaldatum !== "");
    let gemTermijn = 0;
    if (betaaldeFacts.length > 0) {
        let totDagen = 0;
        for (let f of betaaldeFacts) {
            let facDatum = typeof f.datum === "string" ? new Date(f.datum) : f.datum.toJSDate();
            let betDatum = typeof f.betaaldatum === "string" ? new Date(f.betaaldatum) : f.betaaldatum.toJSDate();
            totDagen += Math.floor((betDatum - facDatum) / 86400000);
        }
        gemTermijn = Math.round(totDagen / betaaldeFacts.length);
    }

    dv.header(4, "Kerngetallen 2026");
    dv.table(["", ""], [
        ["Omzet YTD (excl. BTW)", eur(totalExcl)],
        ["Maandgemiddelde", eur(maandgemiddelde)],
        ["Jaarprognose (x12)", eur(prognoseJaar)],
        [groeiIcon + " t.o.v. 2025 (zelfde periode)", (groei >= 0 ? "+" : "") + groei.toFixed(1) + "%"],
        ["Openstaand", eur(openBedrag)],
        ["Gem. betaaltermijn", gemTermijn + " dagen"],
    ]);

    dv.header(4, "Risico-indicatoren");
    let risicoItems = [];
    if (concentratie > 60) {
        risicoItems.push("⚠️ **Klantconcentratie:** " + topKlant[0] + " is " + concentratie.toFixed(0) + "% van je omzet");
    }
    if (openBedrag > maandgemiddelde * 1.5) {
        risicoItems.push("⚠️ **Openstaand bedrag** is meer dan 1,5x je maandgemiddelde");
    }
    if (gemTermijn > 30) {
        risicoItems.push("⚠️ **Trage betalers:** gemiddeld " + gemTermijn + " dagen — overweeg herinneringen");
    }
    
    let gezondItems = [];
    if (concentratie <= 60) {
        gezondItems.push("✅ Klantspreiding is gezond (" + concentratie.toFixed(0) + "% bij grootste klant)");
    }
    if (groei > 0) {
        gezondItems.push("✅ Omzet groeit t.o.v. vorig jaar");
    }
    if (gemTermijn <= 30) {
        gezondItems.push("✅ Betalingen komen gemiddeld binnen " + gemTermijn + " dagen");
    }
    
    if (risicoItems.length > 0) dv.paragraph(risicoItems.join("\n\n"));
    if (gezondItems.length > 0) dv.paragraph(gezondItems.join("\n\n"));

    if (lastYearTotal > 0) {
        dv.header(4, "Jaarvergelijking");
        dv.table(["", "2025 (heel jaar)", "2026 (t/m nu)", "Prognose 2026"], [
            ["Omzet excl. BTW", eur(lastYearTotal), eur(totalExcl), eur(prognoseJaar)],
        ]);
    }
}
```

---

## In deze map

```dataview
LIST
FROM "SCL/26000 bookkeeping"
WHERE file.name != this.file.name AND !contains(file.name, "foldernote")
SORT file.folder ASC, file.name ASC
```

| Folder | Inhoud |
|---|---|
| `bronnen/` | PDF-facturen en bankafschriften |
| `overzichten/` | Dashboard en jaarlijkse rolling reports |

---

*Bron: Teams-folder `SCL - 26000 bookkeeping`*
