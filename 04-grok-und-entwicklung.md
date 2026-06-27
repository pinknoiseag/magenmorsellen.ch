# Grok Build & Entwicklung — Erkenntnisse

Stand: Juni 2026. Relevant für spätere Umsetzung des Relaunchs.

## Grok Build (CLI)

| | Wert |
|--|------|
| **Aktuelle Version** | 0.2.51 (Stand Installierung Hanspeter) |
| **Update-Check** | Beim `grok`-Start via `factory-grok-update` in `~/.zshrc` |
| **Release Notes** | Nach Update aus `~/.grok/CHANGELOG.md` |
| **Überspringen** | `grok --no-update` |

Changelog online (x.ai/build/changelog) war zum Prüfzeitpunkt hinter der installierten Version.

## Modelle

| Modell | Rolle |
|--------|-------|
| **grok-composer-2.5-fast** | Default in `~/.grok/config.toml` — schnell, Agenten/Edits |
| **grok-build** | Alternative — klassischer Coding-Agent, mehr Tiefe |

Wechsel: `/model grok-build`, `Ctrl+M`, oder `default` in config.toml.

## Fable vs. Grok (E-Commerce / UI)

**Claude Fable 5** (Video-Kontext): stark bei one-shot UI / Vibe-Coding. Zugang bei Anthropic temporär eingeschränkt (Meldung 12. Juni 2026).

**Grok kann ähnliche Ergebnisse**, aber iterativer:

| | Grok |
|--|------|
| Frontend (React, Vite, HTML/CSS) | ✅ |
| Bilder (`/imagine`, image_gen) | ✅, einzeln |
| Videos | ✅ `/imagine-video` |
| Deploy/Hosting | ❌ selbst |
| Payment/Backend | ❌ implementieren |
| One-shot-Polish wie Fable | ⚠️ eher mehrere Runden |

Für **Magenmorsellen** passt Grok gut zu **Phase 1** (statische/modernisierte Site) und später **Phase 2** (Shop-Integration), wenn Plan und Hosting stehen.

## Factory-Workflow

```bash
grok              # Update → Projektliste → Dev-Server → Grok im Projekt
grok magenmorsellen  # sobald Ordner existiert und in factory-pick sichtbar
grok --no-update  # ohne Versions-Check
```

**Regel für Agenten (pn-tracker Agents.md):** Kein `npm run dev` ohne Nutzerwunsch — Verifikation via `npm run build`.

## Git / GitHub

Wie jpstern.com — eigenes Repo unter **pinknoiseag**:

| | |
|--|--|
| **Remote** | `git@github.com:pinknoiseag/magenmorsellen.ch.git` |
| **Vorbild** | `~/factory/jpstern` → `git@github.com:pinknoiseag/jpstern.com.git` |

**Warum GitHub jetzt schon (vor «bau»):**
- Planungsdocs versioniert und gesichert
- Content-Migration (`docs/content/`, `products.json`) diffbar
- Später `web/` im gleichen Repo — ein Push, klare Historie
- Optional: GitHub Actions → SFTP Deploy auf Hostpoint (Phase 2 des Workflows)

**Noch nicht im Repo:** `web/node_modules/`, `web/dist/`, grosse Rohbilder (siehe `.gitignore`).

---

## Entschieden (Entwicklung)

- **Kein WordPress** — Astro-Statik im Repo
- **Shop Phase 2** — Stripe Payment Links MVP (Hostpoint-kompatibel)
- **Hosting** — Hostpoint, Statik-Deploy — siehe [07-hosting-entscheidung.md](./07-hosting-entscheidung.md)
- **Betrieb** — Familie Stern + Grok