# Magenmorsellen — Project Context for AI Collaboration

**Purpose of this file:** Self-contained summary of the Stern's Magenmorsellen web relaunch project.

**Last updated:** 2026-06-27

---

## 1. What the Project Is

**Stern's Magenmorsellen** (magenmorsellen.ch) is a traditional Basel specialty sweets business dating back to 1899 (original Apotheker recipe). Operated by **Familie Stern** as a **seasonal family entrepreneurship project**.

**Family (ab 2026):** Hanspeter Stern (58), Suela (38), Mia (21), Jamila (17), Leila (11). **Nicole Jost is completely out of the project.**

**Business model (seasonal):**
- Physical sales primarily at two big Basel events:
  - Basler Herbstmesse (Petersplatz, ~18 days end of October)
  - Basler Weihnachtsmarkt (end of November – 23 December)
- Online shop open seasonally (roughly October to mid-January)
- Limited year-round presence — site stays attractive off-season

The project is a **complete web relaunch** of the brand's online presence + future e-commerce.

**Current status (June 2026):** Analysis and architecture complete. **Next:** design brief / moodboard, then product photography. No Astro code yet ("Nichts bauen, bis Hanspeter es explizit sagt").

---

## 2. Main Goals of the Relaunch

- Modern, clean, fast website that represents the traditional yet approachable brand.
- Seasonal shop (~48 items, 4 categories) — introduce kids to entrepreneurship via family project.
- Good experience for fair customers and online buyers.
- Low ongoing maintenance (seasonal business).
- Move away from WordPress/WooCommerce patching burden.

**Phase approach:**
- Phase 1: Core web presence (info, products, seasonal banner, markets)
- Phase 2: Stripe Payment Links MVP (Hostpoint-compatible, no host migration needed)

---

## 3. Technology & Architecture

**Stack (decided):**
- **Astro** static site (Markdown + JSON in repo)
- **Hostpoint** — keep domain + email, deploy static build only
- **Stripe Payment Links** for Phase 2 shop MVP
- **Git:** `git@github.com:pinknoiseag/magenmorsellen.ch.git` (like jpstern.com)

**Season control:** `site-config.json` (`shopOpen`, `season`, `markets`) + redeploy 2–4×/year.

**Reference implementation:** `~/factory/jpstern/web` (Astro patterns, image pipeline).

---

## 4. Current State

- Ist-Analyse ✅ (`03-ist-analyse-magenmorsellen.md`)
- Hosting ✅ Hostpoint + static (`07-hosting-entscheidung.md`)
- Design brief / moodboard ⏳ next
- Product shoot ⏳ after shot list
- WordPress export ⏳
- `web/` Astro project ❌ not started

---

## 5. Key Documents

| File | Focus |
|------|-------|
| `01-arbeitsweise.md` | Family Stern, seasonal model, priorities |
| `03-ist-analyse-magenmorsellen.md` | Live site audit |
| `06-vorschlag-architektur.md` | Astro, Stripe, page structure |
| `07-hosting-entscheidung.md` | Hostpoint decision |
| `04-grok-und-entwicklung.md` | Grok workflow, GitHub |

**Readiness gate before «bau»:** design brief, P1 photos, content export, legal drafts, Hostpoint access documented.

---

## 6. Development Approach

- Planning-first; explicit «bau» before code.
- Content in git repo; Grok + Familie Stern maintain.
- Verify with `npm run build` once `web/` exists.
- Deploy: SFTP build output to Hostpoint `public_html`.

---

## 7. Related Projects

- **jpstern.com** — visual quality bar, same Astro + Hostpoint + GitHub pattern
- **pinknoise.ch** — portfolio sibling, later relaunch
- Part of Pink Noise web family under Hostpoint

For any work: read `01`, `03`, `06`, `07` first.