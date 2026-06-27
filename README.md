# Magenmorsellen — Web-Relaunch

Projektordner für Analyse, Planung und spätere Umsetzung von **magenmorsellen.ch**.

## Status

| Phase | Status |
|-------|--------|
| Ist-Analyse | ✅ erledigt (Juni 2026) |
| Hosting | ✅ Hostpoint + Statik |
| Relaunch-Plan (Design + Inhalt) | ⏳ Moodboard + Fotos als Nächstes |
| E-Commerce (Shop) | ⏳ Phase 2 — Stripe Payment Links |
| Git / GitHub | ⏳ Repo `pinknoiseag/magenmorsellen.ch` vorbereitet |

## Arbeitsweise

- **Nichts bauen**, bis Hanspeter es explizit sagt.
- Zuerst **klarer Plan**, dann Umsetzung.
- **Betrieb ab 2026:** Familie Stern (saisonales Familienprojekt) — siehe [01-arbeitsweise.md](./01-arbeitsweise.md).
- **Nächstes:** Design-Brief / Moodboard, dann Produkt-Shoot.

## GitHub

Wie [jpstern.com](https://github.com/pinknoiseag/jpstern.com): eigenes Repo unter **pinknoiseag**.

| | |
|--|--|
| **Remote** | `git@github.com:pinknoiseag/magenmorsellen.ch.git` |
| **Inhalt** | Planungsdocs, später `web/` (Astro), Content, `site-config.json` |
| **Deploy** | Manuell SFTP → Hostpoint; optional später GitHub Actions |

Repo auf GitHub anlegen (falls noch nicht vorhanden), dann:

```bash
cd ~/factory/magenmorsellen
git remote add origin git@github.com:pinknoiseag/magenmorsellen.ch.git
git push -u origin main
```

## Dokumente

| Datei | Inhalt |
|-------|--------|
| [01-arbeitsweise.md](./01-arbeitsweise.md) | Vorgehen, Prioritäten, Saison-Modell |
| [02-portfolio-webseiten.md](./02-portfolio-webseiten.md) | Alle Web-Projekte im Überblick |
| [03-ist-analyse-magenmorsellen.md](./03-ist-analyse-magenmorsellen.md) | Technik, UX, Content, Fehlerliste |
| [04-grok-und-entwicklung.md](./04-grok-und-entwicklung.md) | Grok Build, Modelle, Limitationen |
| [05-hosting.md](./05-hosting.md) | Hosting — Entscheidungen, offene Punkte |
| [06-vorschlag-architektur.md](./06-vorschlag-architektur.md) | Empfehlung: Astro, Stripe |
| [07-hosting-entscheidung.md](./07-hosting-entscheidung.md) | **Kostenvergleich, Empfehlung: Hostpoint + Statik** |

## Kurzüberblick Marke

**Stern's Magenmorsellen** — traditionelle Basler Zuckerspezialität seit 1899 (Apothekerrezept). Betrieb durch **Familie Stern** (saisonales Familienprojekt). Verkauf an **Basler Herbstmesse** (Petersplatz, ~18 Tage Ende Oktober) und **Basler Weihnachtsmarkt** (ab Ende November bis 23. Dezember). Online-Shop saisonal (Oktober bis Mitte Januar).