# Vorschlag — Architektur & Hosting (freie Hand)

Stand: Juni 2026. Architektur **beschlossen**; Hosting: **Hostpoint + Statik** (siehe [07-hosting-entscheidung.md](./07-hosting-entscheidung.md)).

---

## Kurzantwort

**WordPress ist für diesen Relaunch nicht nötig.** Du hast recht: Das Plugin/Theme-Ökosystem war früher ein grosser Hebel, heute können wir dieselbe Site (besser) als **moderne statische Website** bauen — Inhalt in Dateien im Factory-Repo, Shop später mit **Stripe** statt WooCommerce.

**Hosting:** Schweizer All-in-one für **Domain + E-Mail + HTTPS**, Website als **statische Dateien** (kein PHP, kein WordPress-Wartungsstress).

---

## Brauchen wir WordPress noch?

| Früher (dein HTML von Hand) | WordPress-Ära | Heute mit Grok |
|----------------------------|---------------|----------------|
| Alles selbst coden, jede Seite | Themes, Plugins, WooCommerce | Code im Repo, Grok pflegt/erweitert |
| Shop selbst bauen = enormer Aufwand | WooCommerce «fertig» | Stripe Checkout + schlanke Produktliste |
| Kein CMS | WP-Backend für Nicht-Entwickler | Markdown/JSON im Git-Repo — Updates via Grok + Familie Stern |

**WordPress lohnt sich noch, wenn:**
- Jemand **ohne Entwickler** täglich Inhalte im Browser ändert
- Man **100+ Plugins-Ökosystem** braucht (Mitglieder, komplexe Mehrsprachigkeit, …)
- Man den **bestehenden WooCommerce-Shop** nur «schön machen» will (minimaler Eingriff)

**Bei euch passt das nicht:**
- Sowieso **Komplett-Neuaufbau** (Theme, Datenfehler, `beispiel-seite`, …)
- **Saisonales** Geschäft — WP + WooCommerce muss ganzjährig gepatcht werden, auch wenn der Shop 8 Monate zu ist
- Du hast **Grok + Factory** — das ersetzt viel vom früheren «HTML von Hand», ohne Plugin-Chaos
- Produktanzahl **überschaubar** (~48 Artikel, 4 Kategorien)

**Korrektur:** WordPress ist nicht «falsch», aber für **dieses** Projekt ist es **überdimensioniert und wartungsintensiver** als nötig.

---

## Mein Vorschlag in einem Satz

**Astro-Website** im Git-Repo (`pinknoiseag/magenmorsellen.ch`) → deploy auf **Hostpoint** als Statik → **Phase 2:** Stripe **Payment Links** (MVP), optional später Checkout Sessions — alles Hostpoint-kompatibel, kein Hoster-Umzug nötig.

---

## Phase 1 — Website (Inhalt + Design)

### Technik

| Komponente | Wahl | Warum |
|------------|------|-------|
| Framework | **Astro** | Ideal für Content-Sites: schnell, SEO-stark, wenig JS, Komponenten für wiederkehrende Blöcke |
| Styling | **CSS** (evtl. minimal Tailwind) | Volle Design-Kontrolle, kein Theme-Zwang |
| Inhalt | **Markdown + JSON** in `src/content/` | Geschichte, Sorten, FAQ, Märkte als Dateien — versioniert, diffbar |
| Bilder | Eigene Fotos (jpstern-Qualität), optimiert (WebP/AVIF) | Kein 2015-Stock mehr |
| Saison-Modus | `site-config.json` z. B. `{ "shopOpen": false, "season": "off", "markets": [...] }` | Ein Schalter steuert Banner, CTAs, Shop-Link |

### Seitenstruktur (Vorschlag)

```
/                     Start (Hero, Saison-Banner, Story-Teaser, Sorten, Märkte)
/geschichte           Familie Stern, 1899, Handwerk
/sorten               Alle Sorten mit Kurzbeschreibung
/maerkte              Herbstmesse + Weihnachtsmarkt, Karte, Daten
/galerie              Kuratierte Fotos (statt Facebook-Homepage)
/kontakt              E-Mail, evtl. einfaches Formular
/shop                 Phase 2 — bis dahin «ab Herbst wieder geöffnet»
```

### Was du von WordPress **mitnimmst** (einmalig exportieren)

- Texte von Geschichte, Sorten, FAQ
- Produktliste (Name, Preis, Kategorie, Bilder-URLs) → bereinigen (Mango/Pistazie-Fix etc.)
- **Nicht** mitnehmen: Theme, Plugins, Enfold-Settings, Facebook-Widget

---

## Phase 2 — Shop (nach Design)

### Technik

| Komponente | Wahl | Warum |
|------------|------|-------|
| Zahlung | **Stripe Checkout** | TWINT + Karten in der Schweiz, wenig eigener PCI-Aufwand |
| Produkte | JSON oder Stripe Products | ~48 Artikel — kein Datenbank-Monster |
| Warenkorb | Leichtgewicht (eigene UI oder Stripe Payment Links zum Start) | Saison: `shopOpen: false` → Checkout deaktiviert |
| Versand | Konfiguration CH-Post / Abholung Messe | In Checkout-Metadaten oder feste Versandzonen |
| Rechnungen | Stripe + E-Mail | Kein WooCommerce nötig |

**Alternativen**, falls Stripe zu technisch für den Familien-Alltag:
- **Snipcart** (ein Script, teurer bei Volumen)
- **Ecwid** Embed (schnell, UI schwächer)
- **Shopify Buy Button** nur saisonal — zweites System

**Empfehlung:** Stripe — passt zu schlanker Statik-Site und CH-Zahlungsarten.

### Saison-Logik Shop

```
Off-Season (Feb–Sep):  Site live, Shop-Seite erklärt «ab Oktober», kein Checkout
Herbstmesse:           Banner «Wir sind am Petersplatz», Shop optional schon offen
Weihnachtsmarkt:       Banner + Bestellfrist (z. B. bis 27.12.)
Nach Saison:           Ein Eintrag in site-config.json → redeploy (oder später kleines Admin-UI)
```

Redeploy dauert ~1 Minute — für 2–4 Saison-Umschaltungen pro Jahr völlig ok. Optional später **Decap CMS** (Git-basiert) — falls Familie Inhalte ohne Grok ändern will; nicht Phase 1.

---

## Hosting — konkrete Empfehlung

Du brauchst drei Dinge:

1. **Domain** (magenmorsellen.ch)
2. **E-Mail** (info@magenmorsellen.ch, …)
3. **Website** (HTML/CSS/JS nach Build)

HTTPS ist heute bei allen seriösen Hostern inklusive (Let's Encrypt).

### Gewählt: **Hostpoint behalten**

| | |
|--|--|
| **Warum** | Domain/Mail laufen bereits; E-Mail-Umzug wäre der mühsame Teil; Statik deploy genauso gut wie bei Infomaniak |
| **Website** | Ordner `public_html` mit Astro-Build-Output, kein WordPress mehr |
| **Vorteil** | Kein MX-Umzug, kein neues Mail-Passwort auf dem Handy |

### Alternative (nicht gewählt): **Infomaniak**

| | |
|--|--|
| **Warum** | Schweizer All-in-one, sinnvoll nur bei bewusstem Neustart inkl. E-Mail-Umzug |
| **Kosten** | ~CHF 20–50/Jahr günstiger — Aufwand E-Mail-Umzug lohnt sich kaum |

### Empfehlung 3 (nur Website, Domain woanders): **Cloudflare Pages**

| | |
|--|--|
| **Warum** | Sehr schnell, gratis Tier, Git-Deploy |
| **Aber** | E-Mail braucht trotzdem Infomaniak/Hostpoint/Google Workspace — zwei Anbieter |

**Entscheidung:** **Hostpoint** — Statik deployen, E-Mail unverändert lassen.

---

## Entwicklungs-Workflow (Factory)

```
~/factory/magenmorsellen/
  docs/           ← diese Erkenntnisse (bereits da)
  web/            ← Astro-Projekt (wenn du «bau» sagst)
    src/content/  ← Texte, Sorten, Produkte
    public/       ← Bilder
    site-config.json
```

- Lokal: `npm run dev` / `npm run build`
- Grok baut und pflegt im Repo
- Deploy: Build-Ordner → Hoster (manuell oder später GitHub Actions)

---

## Was wir **nicht** machen sollten

- WordPress neu installieren «weil man das so macht»
- Page Builder (Elementor, …) — gleiche Schulden, anderer Name
- Facebook-Feed als Homepage-Kern
- Shopify für 48 Saisonprodukte (Kosten + zweites Login), ausser du willst bewusst «fertigen» Shop ohne Code

---

## Risiken & ehrliche Grenzen

| Risiko | Mitigation |
|--------|------------|
| Familie will Inhalte ohne Grok ändern | Später Decap CMS oder einfache «Saison»-Oberfläche |
| TWINT/PostFinance ohne Stripe | Stripe unterstützt TWINT CH; PostFinance direkt = mehr Integration |
| Bestehende WooCommerce-Kunden/Orders | Export für Archiv; neuer Shop = Neustart (saisonal ok?) |
| jpstern.com bleibt WordPress | Unabhängig — Magenmorsellen nicht davon abhängig machen |

---

## Entscheidungsvorschlag für dich

| Frage | Empfehlung |
|-------|------------|
| WordPress? | **Nein** — für Relaunch |
| Technik Site | **Astro + Markdown/JSON** |
| Shop Phase 2 | **Stripe Checkout** |
| Hoster | **Hostpoint** (Statik, Mail behalten) |
| Wer pflegt? | Familie Stern + Grok; Git-Repo `pinknoiseag/magenmorsellen.ch` |

---

## Phase 2 Shop — Hostpoint-kompatibel (kein späterer Umzug)

| Stufe | Was | Server nötig? |
|-------|-----|---------------|
| **MVP** | Stripe Payment Links, `shopOpen` in `site-config.json` | Nein — 100 % Statik |
| **Upgrade** | Stripe Checkout Sessions + Warenkorb | Optional 1 PHP-Skript auf Hostpoint oder Cloudflare Worker |

## Nächste Schritte (noch nicht «bau»)

1. ~~Hoster-Entscheid~~ ✅ Hostpoint
2. Design-Brief / Moodboard (`08-design-brief.md`)
3. Shot List + Produkt-Shoot
4. WordPress-Export (WXR + Produkt-CSV)
5. Readiness Gate → «bau» → Astro in `web/`