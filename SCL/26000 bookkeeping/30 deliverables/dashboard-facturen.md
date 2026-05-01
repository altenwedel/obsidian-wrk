# Dashboard Facturen Studio Claro

Dit dashboard haalt factuurgegevens op uit de jaarbestanden (`facturen-YYYY.md`) via DataviewJS. Werk de status en betaaldatum bij in het betreffende jaarbestand — het dashboard past zich automatisch aan.

---

## Openstaande facturen

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const files = dv.pages().where(p => p.file.name.startsWith("facturen-") && p.facturen);
let openstaand = [];
for (let file of files) {
    for (let f of file.facturen) {
        if (f.status === "openstaand" || f.status === "herinnering") {
            openstaand.push(f);
        }
    }
}
openstaand.sort((a, b) => dv.compare(a.datum, b.datum));

if (openstaand.length === 0) {
    dv.paragraph("*Geen openstaande facturen.*");
} else {
    let totaal = openstaand.reduce((sum, f) => sum + f.totaal, 0);
    dv.table(
        ["Nr", "Datum", "Klant", "Betreft", "Totaal", "Status"],
        openstaand.map(f => [
            f.nr,
            f.datum,
            f.klant,
            f.betreft,
            eur(f.totaal),
            f.status === "herinnering" ? "🟡 herinnering" : "🔴 openstaand"
        ])
    );
    dv.paragraph(`**Totaal openstaand: ${eur(totaal)}**`);
}
```

---

## Recent betaald (laatste 10)

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const files = dv.pages().where(p => p.file.name.startsWith("facturen-") && p.facturen);
let betaald = [];
for (let file of files) {
    for (let f of file.facturen) {
        if (f.status === "betaald") {
            betaald.push(f);
        }
    }
}
betaald.sort((a, b) => dv.compare(b.datum, a.datum));
betaald = betaald.slice(0, 10);

dv.table(
    ["Nr", "Datum", "Klant", "Totaal", "Betaald op"],
    betaald.map(f => [
        f.nr,
        f.datum,
        f.klant,
        eur(f.totaal),
        f.betaaldatum || "—"
    ])
);
```

---

## Omzet per kwartaal (huidig jaar)

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const file = dv.page("facturen-2026");
if (!file || !file.facturen) {
    dv.paragraph("*Geen data voor 2026.*");
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
        ["Kwartaal", "Omzet excl. BTW", "Aantal facturen"],
        [
            ["Q1 (jan-mrt)", eur(q[1]), qCount[1]],
            ["Q2 (apr-jun)", eur(q[2]), qCount[2]],
            ["Q3 (jul-sep)", eur(q[3]), qCount[3]],
            ["Q4 (okt-dec)", eur(q[4]), qCount[4]],
            ["**Totaal**", eur(q[1]+q[2]+q[3]+q[4]), qCount[1]+qCount[2]+qCount[3]+qCount[4]]
        ]
    );
}
```

---

## Omzet per klant (huidig jaar)

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const file = dv.page("facturen-2026");
if (!file || !file.facturen) {
    dv.paragraph("*Geen data voor 2026.*");
} else {
    let klanten = {};
    for (let f of file.facturen) {
        if (f.type === "creditnota") continue;
        if (!klanten[f.klant]) klanten[f.klant] = {subtotaal: 0, count: 0};
        klanten[f.klant].subtotaal += f.subtotaal;
        klanten[f.klant].count++;
    }
    let rows = Object.entries(klanten)
        .sort((a, b) => b[1].subtotaal - a[1].subtotaal)
        .map(([klant, data]) => [klant, eur(data.subtotaal), data.count]);
    
    dv.table(["Klant", "Omzet excl. BTW", "Facturen"], rows);
}
```

---

## Jaarvergelijking

```dataviewjs
function eur(n) {
    return '<span style="display:inline-block;width:100%;text-align:right">€ ' + n.toLocaleString('nl-NL', {minimumFractionDigits: 2, maximumFractionDigits: 2}) + '</span>';
}

const files = dv.pages().where(p => p.file.name.startsWith("facturen-") && p.facturen);
let jaren = [];
for (let file of files) {
    let totExcl = 0, totIncl = 0, count = 0;
    for (let f of file.facturen) {
        totExcl += f.subtotaal;
        totIncl += f.totaal;
        count++;
    }
    jaren.push([file.jaar, eur(totExcl), eur(totIncl), count]);
}
jaren.sort((a, b) => a[0] - b[0]);
dv.table(["Jaar", "Omzet excl. BTW", "Omzet incl. BTW", "Facturen"], jaren);
```

---

## Hoe te gebruiken

**Status bijwerken:** Open het betreffende jaarbestand (bijv. `facturen-2026.md`) en pas in de frontmatter de `status` aan van `openstaand` naar `betaald`. Vul eventueel de `betaaldatum` in.

**Nieuwe factuur toevoegen:** Voeg in de frontmatter een nieuw item toe aan de `facturen`-lijst en voeg een leesbare entry toe in de body van het document.

**Mogelijke statuswaarden:** `openstaand`, `herinnering`, `betaald`, `verrekend`

**Nieuw jaar starten:** Maak een kopie van een bestaand jaarbestand, pas het jaar aan in de frontmatter, en wis de facturenlijst.
