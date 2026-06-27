# Arbeitsweise & Projekt-Prioritäten

Stand: Juni 2026

## Familie Stern — Betrieb ab 2026

**Nicole Jost ist komplett aus dem Projekt.** Stern's Magenmorsellen wird von der **Familie Stern** als **saisonales Familienprojekt** betrieben — auch um die Kinder schrittweise ins Unternehmertum einzuführen.

| Person | Alter | Rolle (grob) |
|--------|-------|--------------|
| Hanspeter Stern | 58 | Leitung, Website mit Grok, Produktion |
| Suela | 38 | Familie Stern, Mitbetrieb |
| Mia | 21 | Mitwirkung am Familienprojekt |
| Jamila | 17 | Mitwirkung am Familienprojekt |
| Leila | 11 | Mitwirkung am Familienprojekt |

Am Markt unterstützen weiterhin **Verkäuferinnen am Stand**. Website und Saison-Umschaltung: Hanspeter + Grok; ältere Kinder können mit Anleitung mithelfen (z. B. `site-config.json`, Deploy).

## Grundregeln

1. **Kein Bauen ohne expliziten Auftrag** — auch keine „Vorbereitung“ im Code, solange nicht gesagt.
2. **Plan vor Umsetzung** — Struktur, Design-Richtung, Hosting, Migration klären, dann bauen.
3. **Zwei Phasen für Magenmorsellen:**
   - **Phase 1:** Inhalt + Design (neue Präsentation, Story, Sorten, Märkte, Saison-Infos)
   - **Phase 2:** E-Commerce-Shop (Stripe Payment Links MVP, Hostpoint-kompatibel)

## Saisonales Geschäftsmodell

| Zeitraum | Aktivität |
|----------|-----------|
| **Ende Oktober** | Basler Herbstmesse, Petersplatz, ~18 Tage |
| **Ende Nov. – 23. Dez.** | Basler Weihnachtsmarkt (Barfüserplatz / Münsterplatz) |
| **Oktober – Mitte Januar** | Online-Shop typischerweise geöffnet |
| **Rest des Jahres** | Produktion/Shop zu; Website soll trotzdem attraktiv bleiben (Geschichte, Sorten, «bald wieder da») |

### Anforderungen für die neue Site (aus Saison-Logik)

- **Saison-Status-Banner** (Shop offen / geschlossen / wir sind am Markt)
- **Markt-Kalender** mit Orten und Daten
- **Bestellfristen** klar auf der eigenen Site (nicht nur Facebook)
- **Off-Season-Modus** ohne leere/tote Shop-Erfahrung
- Weniger Abhängigkeit von **Facebook** als primärer «Homepage-Inhalt»

## Geplante Planungsblöcke (noch nicht ausgearbeitet)

1. **Inventar** — Seiten, Produkte, Bilder, Texte aus WordPress exportieren; Fehlerliste
2. **Informationsarchitektur** — Start, Sorten, Geschichte, Märkte, Saison-Shop, Kontakt
3. **Design-Richtung** — warm, handwerklich, Basler Tradition, festlich im Winter; Qualitätsmassstab: jpstern.com (Fotografie)

## Nächste Schritte

1. **Design-Brief / Moodboard** — siehe Relaunch-Plan (08, in Arbeit)
2. **Shot List + Produkt-Shoot** — jpstern-Qualität
3. **Content-Export** aus WordPress
4. **Readiness Gate** — dann explizit «bau»

Hosting: **entschieden** — Hostpoint + Statik, siehe [07-hosting-entscheidung.md](./07-hosting-entscheidung.md).