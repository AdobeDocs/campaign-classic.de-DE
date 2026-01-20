---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 24%

---
# Neustrukturierung der Dokumentation zu 📊 v7 - Übersicht

**Erstellt**: 13.01.2026\
**Ordner insgesamt**: 21\
**Dateien insgesamt**: ~1.500

---

## 📈 Zusammenfassung

| Metrik | Count | Prozentsatz |
|--------|-------|------------|
| 📄 **Dateien insgesamt** | 1.500 | 100 % |
| ✅ **BEIBEHALTEN (V7-spezifisch)** | 400 | 27 % |
| 🗑️ **DELETE (in v8)** | 800 | 53 % |
| ➡️ **VERSCHIEBEN (zu v8)** | 200 | 13 % |
| 🔍 **ÜBERPRÜFUNG (unklar)** | 100 | 7 % |

**🎯geschätzte**: 60-75 % (1.500 → 400-600 Dateien)

---

## 📁 nach Priorität

### 🟢 Priorität 1: 100 % beibehalten - Nur v7-Funktionen

| Ordner | Dateien | Grund | v8-Status | Aktion |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | On-Premise-/Hybrid-Setup | Nur Cloud in v8 | ✅ ALLE BEIBEHALTEN + Abzeichen |
| 📂 `/mrm/` | 5 | Marketing-Ressourcen-Management | NICHT in FFDA | ✅ ALLE BEIBEHALTEN + Abzeichen |
| 📂 `/surveys/` | 8 | Online-Umfragen | NICHT in FFDA | ✅ ALLE BEIBEHALTEN + Abzeichen |
| 📂 `/distributed/` | 7 | Verteiltes Marketing | NICHT in FFDA | ✅ ALLE BEIBEHALTEN + Abzeichen |
| 📂 `/response/` | 5 | Reaktionsverwaltung | Status unklar | 🔍 ÜBERPRÜFEN UND DANN BEIBEHALTEN |
| 📂 `/migration/` | 8 | Migration von v6.1 → v7 | v7-spezifisch | ✅ ALLE BEIBEHALTEN |
| **INSGESAMT** | **108** | **7%** | - | **Badge as v7-only** |

---

### 🔴 2: 60-70 % DELETE - Hohe Duplizierung

| Ordner | Gesamt | BEHALTEN | DELETE | VERSCHIEBEN | ÜBERPRÜFUNG | Anmerkungen |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (16 %) | 67 (60 %) | 8 (7 %) | 18 (17 %) | E-Mail/SMS/Push in v8 |
| 📂 `/workflow/` | 121 | 24 (20 %) | 60 (50 %) | 12 (10 %) | 25 (20 %) | Häufige Aktivitäten in v8 |
| 📂 `/reporting/` | 32 | 3 (10 %) | 22 (70 %) | 2 (6 %) | 5 (14 %) | In v8 neu gestaltete Berichte |
| 📂 `/platform/` | 61 | 12 (20 %) | 34 (55 %) | 5 (8 %) | 10 (17 %) | Allgemeine Funktionen in v8 |
| 📂 `/campaign/` | 11 | 2 (18 %) | 7 (64 %) | 1 (9 %) | 1 (9 %) | Kampagnen-Management in v8 |
| **INSGESAMT** | **$** | **£** | **190** | **28** | **£** | **Hohes Reduktionspotenzial** |

---

### 🟡 3: 30-50 % GEMISCHT - detaillierte Analyse erforderlich

| Ordner | Gesamt | % BEIBEHALTEN | DELETE % | Anmerkungen |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65 % | 22 % | Schema-/DB-Konfigurationen (hauptsächlich v7) |
| 📂 `/production/` | 43 | 65 % | 23 % | Serververwaltung (hauptsächlich v7) |
| 📂 `/integrations/` | 37 | 40 % | 40 % | Verfügbarkeit des Connectors überprüfen |
| 📂 `/interaction/` | 39 | 51 % | 31 % | Angebotsmodul (Version 8 überprüfen) |
| 📂 `/web/` | 26 | 92 % | 8 % | Web-Apps > Landingpages v8 |
| 📂 `/message-center/` | 16 | 60 % | 30 % | Transaktionsnachrichten |
| **INSGESAMT** | **230** | **~55%** | **~25%** | **Erfordert eine Überprüfung je Ordner** |

---

## 🎯 Quick Wins - Woche 1

### Löschungen mit hoher Konfidenz (Übereinstimmung von 95-100 % mit v8)

| Ordner | Zu löschende Dateien | Auswirkung | Aufwand |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 Dateien | 🔥🔥🔥 hoch | 2 Tage |
| 📂 `/workflow/` | 60 Dateien | 🔥🔥🔥 hoch | 2 Tage |
| 📂 `/reporting/` | 22 Dateien | 🔥🔥 Medium | 1 Tag |
| 📂 `/platform/` | 34 Dateien | 🔥🔥 Medium | 1 Tag |
| 📂 `/campaign/` | 7 Dateien | 🔥 niedrig | 0,5 Tag |
| **INSGESAMT** | **190 Dateien** | **53 %** | **6,5 Tage** |

**Beispiele**:
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (Workflow) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

---

## 📋 Ordneraufschlüsselung

### 📂 (`/help/delivery/using/`) - 111 Dateien

| Kategorie | Dateien | BEHALTEN | DELETE | VERSCHIEBEN | ÜBERPRÜFUNG | Anmerkungen |
|----------|-------|------|--------|------|--------|-------|
| Erste Schritte | 8 | 0 | 7 | 0 | 1 | Grundlagen in v8 |
| E-Mail | 18 | 0 | 16 | 0 | 2 | Vollständig in v8 |
| SMS | 7 | 1 | 5 | 0 | 1 | Mid-Sourcing = Beibehalten |
| Push | 9 | 0 | 8 | 0 | 1 | Vollständig in v8 |
| Briefpost | 4 | 0 | 4 | 0 | 0 | In v8 |
| Personalisierung | 8 | 1 | 6 | 0 | 1 | Coupons = BEIBEHALTEN |
| Vorlagen | 6 | 0 | 6 | 0 | 0 | In v8 |
| A/B-Tests | 11 | 0 | 10 | 0 | 1 | In v8 |
| Monitoring | 14 | 0 | 12 | 1 | 1 | Hauptsächlich in v8 |
| Fehlerbehebung | 9 | 2 | 4 | 2 | 1 | Tipps vor Ort beibehalten |
| Zustellbarkeit | 8 | 3 | 4 | 0 | 1 | SpamAssassin = KEEP |
| Fortgeschritten | 9 | 11 | 5 | 5 | 8 | Gemischt |
| **INSGESAMT** | **111** | **18** | **£** | **8** | **18** | **60% können gelöscht werden** |

**Muss Folgendes**:
- ✅ `personalized-coupons.md` - NICHT in v8 FFDA
- ✅ `sms-set-up-mid.md` - Mid-Sourcing (lokal)
- ✅ `spamassassin.md` - Spam-Filterung vor Ort

**Beispiele für Schnelllöschungen**:
- 🗑️ `about-email-channel.md` → 95 % in `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95 % in `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90 % in `campaign-web/v8/msg/send-sms`

---

### 📂 Workflow (`/help/workflow/using/`) - 121 Dateien

| Kategorie | Dateien | BEHALTEN | DELETE | VERSCHIEBEN | ÜBERPRÜFUNG | Anmerkungen |
|----------|-------|------|--------|------|--------|-------|
| Erste Schritte | 12 | 2 | 9 | 0 | 1 | Grundlagen in v8 |
| Zielgruppenbestimmung | 18 | 3 | 12 | 1 | 2 | Abfrage/Aufspaltung in v8 |
| Flusskontrolle | 15 | 2 | 10 | 1 | 2 | Häufig in v8 |
| Aktionsaktivitäten | 24 | 4 | 16 | 2 | 2 | Die meisten in v8 |
| Ereignisaktivitäten | 8 | 1 | 6 | 0 | 1 | In v8 |
| MRM-Aktivitäten | 5 | 5 | 0 | 0 | 0 | NICHT in FFDA |
| Technisch | 16 | 4 | 8 | 2 | 2 | Gemischt |
| Fortgeschritten | 12 | 3 | 4 | 3 | 2 | Nützliche Muster |
| Anwendungsfälle | 11 | 0 | 5 | 3 | 3 | Gute Beispiele |
| **INSGESAMT** | **121** | **24** | **60** | **12** | **25** | **50% können gelöscht werden** |

**Muss Folgendes**:
- ✅ Alle MRM-Aktivitäten (5 Dateien) - NICHT in v8 FFDA
- ✅ On-Premise-Konfigurationen
- Erweiterte technische Workflows ✅

**Beispiele für Schnelllöschungen**:
- 🗑️ `query.md` → 95 % in `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95 % in `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95 % in `campaign/v8/automation/workflow/enrichment`

---

### 📂 (`/help/installation/using/`) - 75 Dateien

| Kategorie | Dateien | Aktion | Anmerkungen |
|----------|-------|--------|-------|
| Server-Installation | 18 | ✅ | Nur On-Premise |
| Datenbank-Setup | 12 | ✅ | Nur On-Premise |
| Konfiguration | 15 | ✅ | nlserver usw. |
| Netzwerk | 8 | ✅ | Sicherheitszonen |
| Integration | 10 | ✅ | LDAP usw. |
| Fehlerbehebung | 8 | ✅ | On-Premise |
| Generische Dokumente | 4 | 🗑️ DELETE | In v8-Starthandbuch |
| **INSGESAMT** | **£** | **71 KEEP / 4 DELETE** | **95 % v7-spezifisch** |

**Grund**: v8 ist nur in der Cloud verfügbar, alle Dokumente zur On-Premise-Einrichtung sind v7-spezifisch.

---

### 📂 Web (`/help/web/using/`) - 26 Dateien

| Kategorie | Dateien | BEHALTEN | DELETE | Anmerkungen |
|----------|-------|------|--------|-------|
| Web-Apps | 14 | 14 | 0 | Erweiterte Funktionen nicht in v8 |
| Web Forms | 8 | 8 | 0 | Mehr als v8-Landingpages |
| Landingpages | 2 | 0 | 2 | Grundlegende Seiten in v8 |
| HTML-Editor | 2 | 2 | 0 | Anders als v8 |
| **INSGESAMT** | **26** | **24** | **2** | **92 % v7-spezifisch** |

**Grund**: v7 verfügt über ein vollständiges Web-Anwendungs-Framework, v8 bietet vereinfachte Landingpages.

---

## ✅ Aktionsplan

### Woche 1: Schwerwiegende Löschungen
- [ ] `/delivery/`: 67 Dateien löschen (E-Mail, SMS, Push-Grundlagen)
- [ ] `/workflow/`: Löschen von 60 Dateien (allgemeine Aktivitäten)
- [ ] `/reporting/`: 22 Dateien löschen (Standardberichte)
- [ ] `/platform/`: Löschen von 34 Dateien (allgemeine Funktionen)
- [ ] `/campaign/`: 7 Dateien löschen (Kampagnenverwaltung)
- **Insgesamt**: 190 Dateien gelöscht (13 % Reduktion)

### Woche 2: V7-spezifische Badging-Funktionen
- [ ] `/installation/`: Badge 71-Dateien als „v7 nur On-Premise“
- [ ] `/mrm/`: Badge 5-Dateien als „In v8 FFDA nicht verfügbar“
- [ ] `/surveys/`: Badge 8-Dateien als „In v8 FFDA nicht verfügbar“
- [ ] `/distributed/`: Badge 7-Dateien als „In v8 FFDA nicht verfügbar“
- [ ] `/web/`: Badge 24-Dateien als „v7 Web Applications“
- **Insgesamt**: 115 Dateien mit Badge

### Woche 3: Inhaltsmigration
- [ ] Tipps zur Fehlerbehebung von `/delivery/` auf v8 migrieren
- [ ] Best Practices für die Migration von Workflows zu v8
- [ ] Migrieren von erweiterten Mustern von `/platform/` zu v8
- **Insgesamt**: 40 Dateien migriert und dann gelöscht

### Woche 4: Manuelle Überprüfung
- [ ] Überprüfen `/configuration/` gemischten Inhalten
- [ ] Überprüfen der Verfügbarkeit `/integrations/` Connectors
- [ ] Überprüfen `/interaction/` Angebotsmodul-Abdeckung
- [ ] Überprüfen `/response/` Funktionsstatus
- **Insgesamt**: 50 Dateien geprüft und entschieden

---

## 📊 Ergebnisse erwartet

| Phase | Betroffene Dateien | Kumulativ % |
|-------|----------------|--------------|
| Woche 1: Löschungen | 190 | 13 % |
| Woche 2: Abzeichen | 115 | 20 % |
| Woche 3: Migration | 40 | 23 % |
| Woche 4: Überprüfung | 50 | 26 % |
| **INSGESAMT** | **$** | **26 % verarbeitet** |

**Verbleibend**: ~1.100 Dateien, die in nachfolgenden Phasen verarbeitet werden sollen

**Endziel**: 1.500 → 400-600 Dateien (Reduzierung um 60-73 %)

---

## 🎯 Erfolgsmetriken

| Metrik | Zielgruppe | Status |
|--------|--------|--------|
| Dateien gelöscht | 800+ (53 %) | ⏳ ausstehend |
| Dateien mit Badge | 200+ (13 %) | ⏳ ausstehend |
| Migrierte Dateien | 200+ (13 %) | ⏳ ausstehend |
| Beschädigte Links | 0 | ⏳ ausstehend |
| Genehmigung durch Stakeholder | ✅ | ⏳ ausstehend |

---

**Zuletzt aktualisiert**: 13.01.2026\
**Nächste Überprüfung**: Nach Woche 1 Ausführung

