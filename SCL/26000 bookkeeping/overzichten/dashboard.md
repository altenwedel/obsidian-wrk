# Facturen Dashboard

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
    
    // Maanden verstreken (jan=1 t/m huidige maand)
    let now = new Date();
    let maanden = now.getMonth() + 1; // 1-indexed
    let maandgemiddelde = totalExcl / maanden;
    let prognoseJaar = maandgemiddelde * 12;
    
    // Vergelijking met vorig jaar
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
    
    // Klantconcentratie
    let klanten = {};
    for (let f of facts) {
        if (!klanten[f.klant]) klanten[f.klant] = 0;
        klanten[f.klant] += f.subtotaal;
    }
    let topKlant = Object.entries(klanten).sort((a,b) => b[1] - a[1])[0];
    let concentratie = topKlant ? (topKlant[1] / totalExcl * 100) : 0;
    
    // Gemiddelde betaaltermijn (werkelijke dagen)
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

    // Vergelijking vorig jaar
    if (lastYearTotal > 0) {
        dv.header(4, "Jaarvergelijking");
        dv.table(["", "2025 (heel jaar)", "2026 (t/m nu)", "Prognose 2026"], [
            ["Omzet excl. BTW", eur(lastYearTotal), eur(totalExcl), eur(prognoseJaar)],
        ]);
    }
}
```

---

## Per kwartaal

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const file = dv.page("facturen-2026");
if (!file || !file.facturen) {
    dv.paragraph("*Geen data.*");
} else {
    let q = {1: 0, 2: 0, 3: 0, 4: 0};
    let qCount = {1: 0, 2: 0, 3: 0, 4: 0};
    for (let f of file.facturen) {
        if (f.type === "creditnota") continue;
        let month = typeof f.datum === "string" ? parseInt(f.datum.split("-")[1]) : f.datum.month;
        let quarter = Math.ceil(month / 3);
        q[quarter] += f.subtotaal;
        qCount[quarter]++;
    }
    dv.table(
        ["Kwartaal", "Omzet excl. BTW", "Facturen"],
        [
            ["Q1", eur(q[1]), qCount[1]],
            ["Q2", eur(q[2]), qCount[2]],
            ["Q3", eur(q[3]), qCount[3]],
            ["Q4", eur(q[4]), qCount[4]],
            ["**Totaal**", eur(q[1]+q[2]+q[3]+q[4]), qCount[1]+qCount[2]+qCount[3]+qCount[4]]
        ]
    );
}
```

---

## Per klant

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const file = dv.page("facturen-2026");
if (!file || !file.facturen) {
    dv.paragraph("*Geen data.*");
} else {
    let klanten = {};
    for (let f of file.facturen) {
        if (f.type === "creditnota") continue;
        if (!klanten[f.klant]) klanten[f.klant] = {subtotaal: 0, count: 0};
        klanten[f.klant].subtotaal += f.subtotaal;
        klanten[f.klant].count++;
    }
    let total = Object.values(klanten).reduce((s, k) => s + k.subtotaal, 0);
    let rows = Object.entries(klanten)
        .sort((a, b) => b[1].subtotaal - a[1].subtotaal)
        .map(([klant, data]) => [klant, eur(data.subtotaal), (data.subtotaal/total*100).toFixed(0) + "%", data.count]);
    
    dv.table(["Klant", "Omzet excl. BTW", "Aandeel", "Facturen"], rows);
}
```

---

## Gebruik

**Status bijwerken:** Open `facturen-2026.md`, pas in de frontmatter `status` aan naar `betaald` en vul `betaaldatum` in.

**Nieuwe factuur:** Voeg een item toe aan de `facturen`-lijst in de frontmatter van het jaarbestand.

**Statuswaarden:** `openstaand` · `herinnering` · `betaald` · `verrekend`
