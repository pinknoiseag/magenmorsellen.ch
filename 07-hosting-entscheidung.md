# Hosting-Entscheidung — Kosten & Empfehlung

Stand: Juni 2026

## Betrieb

- **Familie Stern** — saisonales Familienprojekt (Hanspeter, Suela, Mia, Jamila, Leila)
- **Nicole Jost** ist komplett aus dem Projekt (keine Beteiligung mehr)
- Verkäuferinnen am Marktstand; Website-Pflege: Familie Stern + Grok via Git-Repo

---

## Die zwei Varianten im Vergleich

### Variante A: Hostpoint behalten — WordPress raus, Statik rein

| | |
|--|--|
| **Website** | `public_html` (o.ä.) leeren, nur Astro-Build-Output pro Domain |
| **PHP/MySQL** | Nicht mehr nötig → **kein WordPress-Patching** mehr |
| **E-Mail** | **Bleibt** — kein Umzug, keine MX-Änderung, keine Handy/Outlook-Neukonfiguration |
| **Domains** | Bleiben im bestehenden Hostpoint-Account |
| **Aufwand einmalig** | Mittel: WP pro Site deinstallieren/löschen, Statik hochladen, DNS prüfen |
| **Aufwand laufend** | Minimal: 2–4×/Jahr Saison-Deploy |

### Variante B: Wechsel zu Infomaniak (alle 3 Domains)

| | |
|--|--|
| **Website** | Statik auf einem Infomaniak-Webhosting (bis 20 Sites) |
| **E-Mail** | **Komplett umziehen** — MX, Postfächer, Geräte, ggf. Ausfallfenster |
| **Domains** | Transfer oder Nameserver-Umzug für magenmorsellen.ch, pinknoise.ch, jpstern.com |
| **Aufwand einmalig** | **Hoch** — der mühsame Teil ist E-Mail, nicht die Website |
| **Aufwand laufend** | Minimal (wie Variante A) |

---

## Kosten (Richtwerte, exkl. MwSt., Stand Web-Recherche Juni 2026)

### Hostpoint (bleiben)

| Paket | CHF/Monat | Reicht für 3× Statik + Mail? |
|-------|-----------|------------------------------|
| **Standard** | **15.90** | ✅ Ja — 100 GB, bis 10 Domains, unbegrenzt Mailboxes à 5 GB |
| Smart | 17.90 | Overkill (500 GB) |
| Business | 29.90 | **Definitiv Overkill** (1000 GB, 2× Power) |

**Jahr Standard:** ~**CHF 191**

Domains: meist über Hostpoint verwaltet; `.ch`-Renewal typisch ~CHF 12–15/Jahr pro Domain (im Panel prüfen).  
`.com` (jpstern.com) separat ~CHF 15–20/Jahr.

**Gesamt realistisch (4 Domains inkl. escuela bis Übergabe + Standard-Hosting):** ~**CHF 250–290/Jahr**

Nach Übergabe Escuela (Ende Juni 2026): eine Domain weniger im Account, oder Käufer übernimmt escuela-ad-astra.com separat.

Wenn heute **Business (29.90)** läuft: Downgrade auf Standard spart **~CHF 168/Jahr** — ohne Hoster-Wechsel.

### Infomaniak (neu)

| Paket | CHF/Monat | Inhalt |
|-------|-----------|--------|
| Web Hosting | ab **10.91** | 1 Mail, 20 Websites, 250 GB |
| **Web + Mail** | ab **13.20** | **5 Mail-Adressen**, empfohlen für Umzug |

**Jahr Web+Mail:** ~**CHF 158**

Domains (bei Infomaniak registriert/verlängert): `.ch` typisch ~**CHF 10–12/Jahr**, `.com` ~**CHF 15/Jahr**  
→ 3 Domains ~**CHF 35–45/Jahr** extra (wenn nicht im Hosting inklusive)

**Gesamt realistisch:** ~**CHF 195–210/Jahr**

### Kostendifferenz

| | ~CHF/Jahr |
|--|-----------|
| Hostpoint Standard (bleiben) | 230–260 |
| Infomaniak Web+Mail (neu) | 195–210 |
| **Ersparnis Wechsel** | **~CHF 20–50/Jahr** |

➡️ **Preislich fast gleich.** Der Wechsel lohnt sich **nicht wegen Geld**, sondern nur wenn Hostpoint inhaltlich stört oder das Paket nicht downgradebar ist.

---

## WordPress-Patching — dein Punkt

Du hast recht: **das Mühsame ist nicht das Hochladen der Statik**, sondern:

- WordPress-Core-Updates
- Plugin-Updates (WooCommerce, Yoast, …)
- Theme-Updates
- Sicherheitslücken **ganzjährig**, obwohl Shop 8 Monate zu ist

**Statik eliminiert das komplett.** Kein PHP, keine Datenbank, nichts zu patchen — nur HTML/CSS/JS-Dateien.

Das geht auf **Hostpoint genauso gut** wie auf Infomaniak. Der Hoster ist dafür fast egal.

---

## Empfehlung (klar)

### ✅ Variante A: Hostpoint behalten

1. Im Panel prüfen: welches Paket läuft? → auf **Standard (15.90)** downgraden falls Smart/Business
2. Pro Domain: WordPress-Verzeichnis sichern (Backup WXR + DB), dann **Webroot leeren**
3. Astro-Build nach `public_html` (FTP/SFTP/SSH)
4. E-Mail **unverändert** — grösster Gewinn ohne Aufwand
5. Später pinknoise.ch + jpstern.com gleiches Muster (eigene Factory-Projekte)

### Wann trotzdem Infomaniak?

- Hostpoint-Kündigung geplant oder Preiserhöhung
- Support/Panel stört dich nachhaltig
- Du willst **bewusst** alles bei einem Anbieter neu ordnen und hast 1–2 Tage für E-Mail-Umzug

### Was ich **nicht** empfehle

- Bei Hostpoint **weiter WordPress** nur „weil es schon läuft“
- **Business-Paket** für 3 kleine Statik-Sites
- Hoster-Wechsel **nur** um CHF 20–50/Jahr zu sparen — der E-Mail-Umzug kostet mehr Nerven als das einspart

---

## Praktischer Ablauf Magenmorsellen (wenn «bau» kommt)

```
1. Backup WordPress (Export + Bilder)
2. Astro-Site lokal bauen + testen
3. Hostpoint: magenmorsellen.ch Webroot leeren
4. dist/ hochladen
5. SSL prüfen (Let's Encrypt sollte automatisch bleiben)
6. Alte WP-DB optional löschen (Speicher + Sicherheit)
```

Kein MX-Umzug. Kein neues Mail-Passwort auf dem Handy.

---

## Offen (einmal im Hostpoint-Panel prüfen)

- [x] Aktuelles Paket: **Smart Webhosting** (JP, Juni 2026) — CHF 17.90/Mt., 500 GB, bis 50 Domains
- [ ] Wie viele CHF/Jahr zahlen wir heute wirklich (mit Domains)?
- [ ] SSH/SFTP-Zugang vorhanden?
- [ ] Welche E-Mail-Postfächer pro Domain aktiv?
- [ ] jpstern.com — gleicher Account oder separat?

---

## Entscheidungsmatrix

| Kriterium | Hostpoint + Statik | Infomaniak |
|-----------|-------------------|------------|
| Kosten | ≈ gleich | ≈ gleich |
| E-Mail-Aufwand | **Keiner** | Hoch |
| WP-Patching weg | ✅ | ✅ |
| 3 Sites | ✅ Standard | ✅ 1 Hosting |
| Schweiz | ✅ | ✅ |
| **Empfehlung** | **✅ Ja** | Nur bei gutem Grund |