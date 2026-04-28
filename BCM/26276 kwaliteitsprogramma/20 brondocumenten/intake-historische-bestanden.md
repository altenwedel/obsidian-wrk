---
type: intake
status: lopend
gemaakt: 2026-04-28
laatste_update: 2026-04-28
tags: [intake, brondocumenten, historische-bestanden, log]
---

# Intake historische bestanden in Obsidian

> Werklog van bestanden die uit GitHub, Teams, oude Claude-projecten of andere bronnen worden binnengehaald en in de juiste plek in WRK landen. Sicko levert ze één voor één aan met toelichting; per bestand legt deze pagina vast waar het is geplaatst en wat de relatie is tot bestaande bestanden in de vault.

## Werkwijze

1. Sicko levert een bestand aan met korte toelichting (datum, herkomst, doel)
2. Claude bepaalt de juiste plek in de vault op basis van WRK-conventies
3. Plaatst het bestand of registreert dat het duplicaat is
4. Werkt deze pagina bij met datum aanlevering, herkomst, plek, en eventuele bijzonderheden

## Inkomende bestanden

| # | Aangeleverd op | Bestandsnaam aangeleverd | Herkomst | Datum bron | Inhoud | Geplaatst op | Beslissing |
|---|---|---|---|---|---|---|---|
| 1 | 2026-04-28 | `09-beoordelingsmatrix-v04.md` | GitHub | 2026-03-24 | Beoordelingsmatrix v04 met 24 criteria, pre-assessment, NR levert −1 punt op, vijf bronnen (Michels, Factor C, IAP2, BPKV, CASI) | [`30 deliverables/beoordelingsmatrix/beoordelingsmatrix-v04.md`](../30%20deliverables/beoordelingsmatrix/beoordelingsmatrix-v04.md) | **Duplicaat-verificatie**. Inhoud identiek aan reeds geplaatste schone v04 (geplaatst 2026-04-28, eerder vandaag). De "09-" prefix in de bestandsnaam komt uit de GitHub-bestandsordening, niet relevant voor de WRK-plaatsing. Geen actie nodig op het bestand zelf; aangeleverde versie bevestigt dat de WRK-versie correct is. |
| 2 | 2026-04-28 | `04-learning-log.md` | GitHub | 2026-03-10 (primair) en 2026-02 (secundair) | Twee learning logs gecombineerd in één bestand: (1) Plantoetser-ontwerpbeslissingen uit sessie 1-10 maart 2026 met methodologie, rubric-ontwerp, projectarchitectuur, beoordelingslogica en open vragen voor v2.0; (2) PvA-voorbereidings-learnings uit februari 2026 met strategische inzichten over Beaumont, opdrachtgever, team, AI-tooling, voorstelproces, begroten en PRINCE2-elementen | [`20 brondocumenten/notities/260310-learning-log.md`](notities/260310-learning-log.md) | **Nieuwe plaatsing**. Geen bestaande tegenhanger in vault. Beide documenten in één bestand bewaard zoals in GitHub, met intake-notitie aan het begin die de tweedelige structuur uitlegt. Frontmatter beschrijft beide datums en bevat-veld benoemt de twee deelinhouden expliciet. Inhoud raakt veel project-aspecten en is rijk genoeg om in volgende sessies opnieuw te raadplegen. |
| 3 | 2026-04-28 | `BUB Herontwikkeling Zeilschool - Claude.md` | claude.ai chat-export | 2026-03-10 | Chat-export waarvan de titel naar Zeilschool verwijst maar de geëxporteerde inhoud alleen de Leiderdorp-beoordeling bevat (30/66, 45%, "Goed" volgens v1.0-normering). Bevestigt eerder gemelde label-discussie en de discrepantie tussen Zeilschool-scores 25 vs 26 op 66 | [`20 brondocumenten/notities/260310-chat-claudeai-leiderdorp-beoordeling.md`](notities/260310-chat-claudeai-leiderdorp-beoordeling.md) | **Nieuwe plaatsing als projecthistorie**. Bewaard als notitie/chat-transcript. Inhoudelijk rapport leeft als single source of truth in `10 beoordelingen/Leiderdorp-OudeGemeentehuis-20260310.md`; deze chat-export is de bron-trace. Frontmatter linkt expliciet naar het canonieke beoordelingsbestand. Bevestigt twee bekende inconsistenties (Leiderdorp-label en Zeilschool-score) die bij hertoets op v04 opgehelderd kunnen worden. |

## Bevindingen tot nu toe

Na twee bestanden: de matrix v04 in de WRK-vault loopt gelijk met de GitHub-bron van 24 maart. Het learning log van 10 maart is een nieuwe aanwinst voor de vault en bevat zowel ontwerpbeslissingen rond de Plantoetser als bredere PvA-voorbereidings-inzichten. Patroon dat zich aftekent: de inhoudelijk waardevolle documentatie zit verspreid in GitHub (en wellicht oude Claude-projecten) en wordt nu één voor één naar één centrale WRK-vault gehaald.

## Wat nog komt

Sicko levert volgende bestanden één voor één aan, met steeds een korte toelichting (waar het vandaan komt en wanneer). Per bestand wordt deze tabel aangevuld met de plaatsing en eventuele dubbel-detectie.

## Verbeterpunten voor de werkwijze

(Wordt aangevuld als tijdens de intake patronen of obstakels naar boven komen die in een vervolgproces meegenomen moeten worden.)
