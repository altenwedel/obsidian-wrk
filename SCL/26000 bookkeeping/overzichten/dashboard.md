# Dashboard Studio Claro

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

// Over termijn
let over = alle.filter(f => (f.status === "openstaand" || f.status === "herinnering") && dagen(f.datum) > f.termijn);
over.sort((a, b) => dagen(b.datum) - dagen(a.datum));

// Bijna over termijn (binnen 5 dagen)
let bijna = alle.filter(f => f.status === "openstaand" && dagen(f.datum) <= f.termijn && dagen(f.datum) >= f.termijn - 5);

// Betaald zonder betaaldatum
let geenDatum = alle.filter(f => f.status === "betaald" && (!f.betaaldatum || f.betaaldatum === ""));

if (over.length > 0) {
    dv.header(4, "Over betalingstermijn");
    dv.table(["Factuur", "Datum", "Totaal", "Dagen over"],
        over.map(f => [f.nr, kort(f.datum), eur(f.totaal), (dagen(f.datum) - f.termijn) + " dagen"])
    );
}

if (bijna.length > 0) {
    dv.header(4, "Bijna over termijn");
    dv.table(["Factuur", "Datum", "Totaal", "Nog"],
        bijna.map(f => [f.nr, kort(f.datum), eur(f.totaal), (f.termijn - dagen(f.datum)) + " dagen"])
    );
}

if (geenDatum.length > 0) {
    dv.header(4, "Betaald zonder betaaldatum");
    dv.paragraph("Bij " + geenDatum.length + " facturen ontbreekt de betaaldatum. Dit vertekent de gemiddelde betaaltermijn.");
}

if (over.length === 0 && bijna.length === 0 && geenDatum.length === 0) {
    dv.paragraph("Geen openstaande acties.");
}
```

---

## Liquiditeit

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}
function dagen(d) {
    let dt = typeof d === "string" ? new Date(d) : d.toJSDate();
    return Math.floor((Date.now() - dt.getTime()) / 86400000);
}

const files = dv.pages().where(p => p.file.name.startsWith("facturen-") && p.facturen);
let open = [];
for (let file of files) {
    for (let f of file.facturen) {
        if (f.status === "openstaand" || f.status === "herinnering") open.push(f);
    }
}

let totaalOpen = open.reduce((s, f) => s + f.totaal, 0);
let teLaat = open.filter(f => dagen(f.datum) > f.termijn).reduce((s, f) => s + f.totaal, 0);
let verwachtBinnen14 = open.filter(f => dagen(f.datum) <= f.termijn && f.termijn - dagen(f.datum) <= 14).reduce((s, f) => s + f.totaal, 0);
let verwachtLater = open.filter(f => dagen(f.datum) <= f.termijn && f.termijn - dagen(f.datum) > 14).reduce((s, f) => s + f.totaal, 0);

dv.table(["", ""], [
    ["Totaal openstaand", eur(totaalOpen)],
    ["Waarvan te laat", eur(teLaat)],
    ["Verwacht binnen 14 dagen", eur(verwachtBinnen14)],
    ["Verwacht later", eur(verwachtLater)],
]);

// Interpretatie
let beoordeling;
if (teLaat === 0 && totaalOpen < 5000) {
    beoordeling = "**Rustig.** Geen achterstallige betalingen en het openstaande bedrag is beheersbaar.";
} else if (teLaat > 0 && teLaat < 3000) {
    beoordeling = "**Opletten.** Er staat een beperkt bedrag achterstallig open. Stuur een herinnering.";
} else if (teLaat >= 3000 || totaalOpen > 15000) {
    beoordeling = "**Actie nodig.** Het achterstallige bedrag is substantieel. Neem contact op met de betreffende klanten.";
} else {
    beoordeling = "**Opletten.** Houd de betalingen in de gaten.";
}
dv.paragraph(beoordeling);
```

---

## Omzet per maand

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const thisYear = dv.page("facturen-2026");
const lastYear = dv.page("facturen-2025");
if (!thisYear || !thisYear.facturen) { dv.paragraph("*Geen data.*"); } else {
    let maanden = ["jan", "feb", "mrt", "apr", "mei", "jun", "jul", "aug", "sep", "okt", "nov", "dec"];
    let mOmzet = Array(12).fill(0);
    let mOmzetVJ = Array(12).fill(0);
    
    for (let f of thisYear.facturen) {
        if (f.type === "creditnota") continue;
        let m = (typeof f.datum === "string" ? parseInt(f.datum.split("-")[1]) : f.datum.month) - 1;
        mOmzet[m] += f.subtotaal;
    }
    
    if (lastYear && lastYear.facturen) {
        for (let f of lastYear.facturen) {
            if (f.type === "creditnota") continue;
            let m = (typeof f.datum === "string" ? parseInt(f.datum.split("-")[1]) : f.datum.month) - 1;
            mOmzetVJ[m] += f.subtotaal;
        }
    }
    
    let now = new Date();
    let huidigeMaand = now.getMonth(); // 0-indexed
    let actieveMaanden = huidigeMaand + 1;
    let totaal = mOmzet.reduce((s, v) => s + v, 0);
    let gemiddelde = totaal / actieveMaanden;
    let max = Math.max(...mOmzet.filter((v, i) => i <= huidigeMaand));
    
    // Tekstuele staafjes
    function balk(waarde, maximum) {
        if (maximum === 0) return "";
        let len = Math.round((waarde / maximum) * 20);
        return "█".repeat(len) + "░".repeat(20 - len);
    }
    
    let rows = [];
    for (let i = 0; i <= huidigeMaand; i++) {
        let delta = mOmzetVJ[i] > 0 ? ((mOmzet[i] - mOmzetVJ[i]) / mOmzetVJ[i] * 100) : 0;
        let deltaStr = mOmzetVJ[i] > 0 ? ((delta >= 0 ? "+" : "") + delta.toFixed(0) + "%") : "—";
        rows.push([maanden[i], balk(mOmzet[i], max), eur(mOmzet[i]), deltaStr]);
    }
    rows.push(["**gem.**", "", eur(gemiddelde), ""]);
    
    dv.table(["Maand", "", "Excl. BTW", "vs 2025"], rows);
    
    // Koersbeoordeling
    let totaalVJzp = mOmzetVJ.slice(0, actieveMaanden).reduce((s, v) => s + v, 0);
    let koers = totaalVJzp > 0 ? ((totaal - totaalVJzp) / totaalVJzp * 100) : 0;
    let prognose = gemiddelde * 12;
    
    if (koers >= 5) {
        dv.paragraph("**Op koers.** De omzet ligt " + koers.toFixed(0) + "% hoger dan dezelfde periode vorig jaar. Jaarprognose: " + eur(prognose) + ".");
    } else if (koers >= -5) {
        dv.paragraph("**Stabiel.** De omzet is vergelijkbaar met vorig jaar (" + (koers >= 0 ? "+" : "") + koers.toFixed(0) + "%). Jaarprognose: " + eur(prognose) + ".");
    } else {
        dv.paragraph("**Onder koers.** De omzet ligt " + Math.abs(koers).toFixed(0) + "% lager dan vorig jaar. Jaarprognose: " + eur(prognose) + ". Overweeg of dit een tijdelijke dip is of bijsturing nodig is.");
    }
}
```

---

## Klantafhankelijkheid

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const file = dv.page("facturen-2026");
if (!file || !file.facturen) { dv.paragraph("*Geen data.*"); } else {
    let klanten = {};
    for (let f of file.facturen) {
        if (f.type === "creditnota") continue;
        if (!klanten[f.klant]) klanten[f.klant] = 0;
        klanten[f.klant] += f.subtotaal;
    }
    let total = Object.values(klanten).reduce((s, v) => s + v, 0);
    let sorted = Object.entries(klanten).sort((a, b) => b[1] - a[1]);
    
    // Top 3
    let top3 = sorted.slice(0, 3);
    let top3Aandeel = top3.reduce((s, k) => s + k[1], 0) / total * 100;
    
    dv.table(["Klant", "Omzet excl. BTW", "Aandeel"],
        sorted.map(([klant, bedrag]) => [klant, eur(bedrag), (bedrag/total*100).toFixed(0) + "%"])
    );
    
    // Interpretatie
    let topAandeel = sorted[0][1] / total * 100;
    let topNaam = sorted[0][0];
    
    if (topAandeel > 70) {
        dv.paragraph("**Hoog risico.** " + topNaam + " vertegenwoordigt " + topAandeel.toFixed(0) + "% van de omzet. Als deze klant wegvalt, ontstaat direct een probleem. Actief werken aan diversificatie is verstandig.");
    } else if (topAandeel > 50) {
        dv.paragraph("**Aandachtspunt.** " + topNaam + " is goed voor " + topAandeel.toFixed(0) + "% van de omzet. Dat is een stevige afhankelijkheid. Probeer de andere klantrelaties te versterken.");
    } else {
        dv.paragraph("**Gezonde spreiding.** De grootste klant (" + topNaam + ") vertegenwoordigt " + topAandeel.toFixed(0) + "% van de omzet. Geen directe zorg.");
    }
}
```

---

## Werksoort

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const file = dv.page("facturen-2026");
if (!file || !file.facturen) { dv.paragraph("*Geen data.*"); } else {
    let types = {};
    for (let f of file.facturen) {
        let t = f.type || "overig";
        if (!types[t]) types[t] = {subtotaal: 0, count: 0};
        types[t].subtotaal += f.subtotaal;
        types[t].count++;
    }
    let total = Object.values(types).reduce((s, t) => s + t.subtotaal, 0);
    
    let labels = {"werkzaamheden": "Werkzaamheden", "onkosten": "Onkosten", "gemengd": "Gemengd", "creditnota": "Creditnota", "overig": "Overig"};
    let rows = Object.entries(types)
        .sort((a, b) => b[1].subtotaal - a[1].subtotaal)
        .map(([type, data]) => [labels[type] || type, eur(data.subtotaal), (data.subtotaal/total*100).toFixed(0) + "%", data.count]);
    
    dv.table(["Type", "Excl. BTW", "Aandeel", "Facturen"], rows);
    
    let werkPct = (types["werkzaamheden"]?.subtotaal || 0) / total * 100;
    let onkPct = (types["onkosten"]?.subtotaal || 0) / total * 100;
    
    if (werkPct > 70) {
        dv.paragraph("Het overgrote deel van de omzet komt uit inhoudelijk werk. De doorbelaste kosten zijn relatief beperkt.");
    } else if (onkPct > 30) {
        dv.paragraph("Een aanzienlijk deel (" + onkPct.toFixed(0) + "%) bestaat uit doorbelaste onkosten. Check of de marge daarop voldoende is.");
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
if (!file || !file.facturen) { dv.paragraph("*Geen data.*"); } else {
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

## Maandnotitie

Vul hieronder per maand kort in. Kost twee minuten, levert veel op als je later terugkijkt.

### Januari
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### Februari
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### Maart
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### April
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### Mei
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### Juni
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### Juli
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### Augustus
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### September
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### Oktober
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### November
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

### December
- **Wat valt op?**
- **Waar stuur ik op?**
- **Actie komende maand:**

---

## Gebruik

**Maandelijks onderhoud (max 10 min):**
1. Voeg nieuwe facturen toe aan de frontmatter van `facturen-2026.md`
2. Werk betaalstatussen bij: `status: betaald` + `betaaldatum: YYYY-MM-DD`
3. Vul desgewenst de maandnotitie in

**Statuswaarden:** `openstaand` · `herinnering` · `betaald` · `verrekend`
