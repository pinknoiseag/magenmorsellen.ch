# Hosting — magenmorsellen.ch & Portfolio

Stand: Juni 2026

## Entscheidung Hanspeter

- **Nicht an Hostpoint gebunden** — kann überall gehostet werden
- Braucht trotzdem: **Domain, E-Mail, HTTPS, Website**
- **WordPress-Verzicht** erwünscht, wenn Grok die Site komplett bauen kann
- Früher: HTML von Hand → WordPress/Themes/Plugins als Hilfe → heute vermutlich **nicht mehr nötig**

→ Ausführlicher Vorschlag: **[06-vorschlag-architektur.md](./06-vorschlag-architektur.md)**

---

## Kurzempfehlung (Agent)

| Thema | Vorschlag |
|-------|-----------|
| **CMS** | Kein WordPress — **Astro** + Markdown/JSON im Factory-Repo |
| **Shop (Phase 2)** | **Stripe Checkout** statt WooCommerce |
| **Hoster** | **Hostpoint behalten** — nur Website auf Statik umstellen (entschieden) |
| **Saison** | `site-config.json` + Redeploy (Shop an/aus, Markt-Banner) |

WordPress ist **nicht falsch**, aber für einen Komplett-Relaunch mit ~8 Seiten und ~48 Saisonprodukten **überdimensioniert** und ganzjährig wartungsintensiv.

---

## Bekanntes (Ist)

| Punkt | Info |
|-------|------|
| **Bisheriger Hoster** | hostpoint.ch |
| **Domains** | magenmorsellen.ch, pinknoise.ch; jpstern.com separat |
| **Aktueller Stack** | WordPress + WooCommerce, Apache |
| **Zugang Hostpoint** | Noch nicht dokumentiert (FTP, SSH, Panel) |

---

## Offene Punkte (vor Umsetzung)

### Hoster

- [x] **Hostpoint behalten** — WordPress raus, Statik rein (siehe [07-hosting-entscheidung.md](./07-hosting-entscheidung.md))
- [ ] Liegen Domain + MX-Records schon bei Hostpoint? Umzug nötig?
- [ ] Welche E-Mail-Postfächer aktiv? (info@magenmorsellen.ch, …)

### Shop / Business

- [ ] Stripe-Account vorhanden oder anlegen?
- [ ] Alte WooCommerce-Bestellungen archivieren — ok?
- [ ] Wer schaltet Saison um: Hanspeter (+ Familie Stern / Grok bei Bedarf)

### Rechtliches CH

- [ ] Impressum/Datenschutz (neu schreiben für Statik-Site)
- [ ] MwSt./Kleinunternehmer — Shop-Phase 2

---

## Hosting-Optionen (bewertet)

| Option | Pro | Contra | Empfehlung |
|--------|-----|--------|------------|
| Hostpoint + WP modernisieren | Bekannt | Schulden, Wartung | ❌ |
| Hostpoint + **Statik** | Kein Umzug, Mail bleibt | Statik-Deploy selbst einrichten | ✅ **gewählt** |
| **Infomaniak** All-in-one | CH, Domain+Mail+Site | Umzug einmalig | ⚠️ nicht gewählt |
| Cloudflare Pages + Mail woanders | Schnell, gratis Site | Zwei Anbieter | ⚠️ ok |
| Shopify | Fertiger Shop | Kosten, Overkill | ❌ für 48 Produkte |

---

## Notizen aus Gesprächen

**Juni 2026:** Hanspeter bevorzugt Neuaufbau ohne WordPress. HTML-Handarbeit früher zu aufwendig; WP war damals richtig. Mit Grok + modernem Stack ist **statische Site + später Stripe** der schlankere Weg. Details in `06-vorschlag-architektur.md`.

**Juni 2026 (Hosting):** Betrieb durch **Familie Stern** (saisonales Familienprojekt) + Verkäuferinnen am Stand. Content-Pflege via Git-Repo + Grok/Hanspeter.

**Empfehlung nach Kostenvergleich:** Hostpoint **behalten**, Paket **downgraden**, WordPress **entfernen**, Statik deployen — **kein** Hoster-Wechsel, weil E-Mail-Umzug für 3 Domains der mühsame Teil ist und die Preisdifferenz minimal.

Siehe [07-hosting-entscheidung.md](./07-hosting-entscheidung.md).