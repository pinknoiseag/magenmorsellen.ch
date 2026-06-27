# Ist-Analyse — magenmorsellen.ch

Stand: **13. Juni 2026** (Live-Abruf der öffentlichen Site)

## Kurzfazit

WordPress + WooCommerce von **~2015**, punktuell gepflegt. **Inhalt und Geschichte stark**, **Design/UX/Shop schwach**. Relaunch lohnt sich; Substanz für Migration ist vorhanden.

### Gesamtnote (subjektiv)

| Kriterium | Note | Kommentar |
|-----------|------|-----------|
| Inhalt / Story | 8/10 | Sehr gut, untergenutzt auf Startseite |
| Design | 3/10 | Veraltet (Enfold-Ära) |
| UX / Navigation | 4/10 | Unklar, Facebook dominiert |
| Shop | 5/10 | Funktional, alt, Datenfehler |
| Mobile | ~5/10 | Responsive vermutlich, nicht überzeugend |
| SEO / Technik | 4/10 | `beispiel-seite`, Duplikate |
| Saison-Fit | 6/10 | Konzept da (`/noshop`), Umsetzung roh |

---

## Technik

| Aspekt | Befund |
|--------|--------|
| **CMS** | WordPress |
| **Shop** | WooCommerce |
| **Theme** | Enfold (`avia_extended_shop_select`) |
| **SEO** | Yoast SEO |
| **Page Builder** | Elementor-Seite existiert (`elementor-6339/`), ungenutzt/alt |
| **Plugins (sichtbar)** | Yoast, Jetpack (`stats.wp.com`), Instagram/Facebook-Einbettung |
| **Server** | Apache, Hostpoint |
| **Sitemap** | `sitemap.xml` via Yoast |

### Shop-Struktur

- **URL Shop:** `/shop/`
- **4 Kategorien**, ~**48 Produkte** gesamt:
  - Magenmorsellchen (20)
  - Geschenksäckli (4)
  - Magenmorsellen mit Alkohol (4)
  - Magenmorsellen nach Wunsch (20)
- **Preisbeispiel:** CHF 8.00 (Magenmorsellchen)
- **Produktbilder:** überwiegend Uploads **2015–2017**

---

## Seiten-Inventar (Sitemap)

| URL | Letzte Änderung | Anmerkung |
|-----|-----------------|-----------|
| `/` → intern `beispiel-seite` | 2025-12-27 | ⚠️ Canonical zeigt auf `/beispiel-seite/` |
| `/geschichte-der-magenmorsellen/` | 2020-10-24 | ✅ Starke Story |
| `/unsere-sorten/` | 2020-10-24 | ✅ Sortimentsgeschichte |
| `/die-sorten/` | 2020-10-22 | Duplikat/Alt zu Sorten |
| `/fragen-und-antworten/` | 2020-10-24 | FAQ |
| `/noshop/` | 2021-01-03 | Shop-geschlossen-Hinweis |
| `/news/` | 2015-11-10 | Verwaist |
| `/elementor-6339/` | 2024-12-01 | Ungenutzter Entwurf |
| `/shop/` + Produkt-URLs | 2025-12-14 | WooCommerce |

**404 bei erwarteten URLs:** `/ueber-uns/`, `/produkte/`

---

## Startseite — Probleme

1. **Slug `beispiel-seite`** — nie fertig konfigurierte Demo-Startseite, SEO-Schaden
2. **Facebook-Feed** dominiert den sichtbaren Bereich (langsam, DSGVO, fremdes UI)
3. Wenig eigene **Hero-/Produktfotografie**; Logo von **2018**
4. Text ok, aber:
   - Tippfehler: **«Unnser»**
   - Kein klarer **CTA** (Shop / Sorten / Geschichte)
   - Viel «Liken Sie uns auf Facebook» (veraltet)
5. Saison-Text auf **2026** aktualisiert (Herbstmesse / Weihnachtsmarkt) — gut, aber versteckt im Fliesstext

---

## Shop — Probleme

### Datenfehler (konkret)

- **«Mango Magenmorsellchen»** verlinkt auf `/produkt/pistazie-magenmorsellchen/` mit Pistazie-Bild — falscher Slug + falsches Bild (Pistazie wurde 2020 durch Mango ersetzt laut Sorten-Seite)

### UX

- Generisches WooCommerce-Grid
- Produktseiten **dünn** (wenig Beschreibung pro Sorte)
- Sortier-/Paginierungs-UI von Enfold — funktional, nicht modern
- `/noshop/` für geschlossene Saison — roh, aber vorhanden

---

## Content — Stärken (behalten / migrieren)

### Geschichte (`/geschichte-der-magenmorsellen/`)

- Apotheker A. Thon, 1899, Grossvater Emil Stern 1931
- Familientradition, Handarbeit, Rezept-Übernahme 2012
- Herstellungsprozess beschrieben (Erfahrung, Rühren, Giessen, Brechen)
- Standorte: **Petersplatz** (Herbstmesse), **Münsterplatz** (Weihnachtsmarkt)
- Signatur: Nicole Jost & Hanspeter Stern *(Ist-Zustand Live-Site; Relaunch: Familie Stern — Nicole nicht mehr beteiligt)*

### Sorten (`/unsere-sorten/`)

- 12 traditionelle Sorten seit Jahrzehnten
- Erweiterung 2013 auf 20 Sorten, Cassis 2014, alkoholisch 2017, Mango statt Pistazie 2020
- Liste: Pfefferminze, Vanille, Zitrone, Banane, Bergamotte, Ananas, Aprikose, Blutorange, Erdbeere, Himbeere, Kirsche, Cassis, Zwetschge, Polareis, Mango, Apfel, Anis, Ingwer, Original, Chocolat + Whisky, Absinth, Gin, Baileys

### Facebook (extern)

- Aktive Posts: Herbstmesse-Start, Weihnachtsmarkt Barfüserplatz, Bestellfrist 27. Dezember
- Gute **Live-Bilder** vom Stand — für neue Galerie/News nutzbar, nicht als Homepage-Ersatz

---

## Sprache / Konsistenz

- Durchgängig **Sie**-Form (passt zur Zielgruppe)
- Inkonsistenz: **Änis** vs **Anis** (Sorten-Seite vs Shop)
- Teils informelle Smileys in Shop-Texten — Stilfrage für Relaunch

---

## Was die neue Site braucht (aus Analyse, noch kein Plan)

1. Echte Startseite mit Story, Sorten-Teaser, Saison-Status
2. Markt-Seite (Daten, Orte, Öffnungslogik)
3. Sorten-Übersicht + optional Detail pro Sorte
4. Eigene News/Galerie (Facebook-Inhalte kuratieren)
5. Saisonaler Shop-Schalter (Phase 2)
6. SEO: Canonical, keine Duplikate, saubere URLs
7. Einheitliche **Produktfotografie** (eigene Fotos, jpstern-Qualität)
8. Datenbereinigung WooCommerce vor Shop-Relaunch

---

## Vergleich jpstern.com

| | jpstern.com | magenmorsellen.ch |
|--|-------------|-------------------|
| Assets | 2026 | 2015–2018 |
| Design | Modern | Veraltet |
| Social | Instagram integriert | Facebook dominiert Homepage |
| Potenzial | — | Inhalt da, Präsentation fehlt |