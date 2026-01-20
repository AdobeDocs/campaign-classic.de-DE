---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 DEMO-EINGABEAUFFORDERUNG - Dokumentationsanalyse von v7 zu v8

**Kopieren Sie die gesamte Eingabeaufforderung in Cursor/ChatGPT, um einen beliebigen v7-Ordner zu analysieren**

---

## 📋 DER EINGABEAUFFORDERUNG (VON HIER KOPIEREN) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

---

## 🎯 DEMO-ANWEISUNGEN

### Schritt 1: Eingabeaufforderung anzeigen
1. Diese Datei öffnen (`DEMO-PROMPT-STANDALONE.md`)
2. Scrollen Sie zum Abschnitt „AUFFORDERUNG“
3. Sagen Sie: *„Dies ist unsere automatisierte Analyseaufforderung“*

### &#x200B;2. Schritt: Eingabeaufforderung kopieren
1. Alles von „Dokumentationsanalyse zu Campaign v7“ bis zum Ende auswählen
2. In Zwischenablage kopieren
3. Sprich: *„Ich kopiere einfach die gesamte Eingabeaufforderung…“*

### Schritt 3: Einfügen und ausführen
1. Cursor öffnen
2. Eingabeaufforderung einfügen
3. Sagen Sie: &quot;*&quot;…und fügen Sie es in den Cursor ein“*
4. Enter drücken

### Schritt 4: Ergebnisse anzeigen
1. Auf Generierung warten (~30-60 Sekunden)
2. Scrollen Sie durch den generierten Bericht
3. Wichtige Abschnitte hervorheben:
   - Zusammenfassungsstatus 📊
   - Datei-für-Datei-Tabelle 📋
   - ✅ muss Abschnitt behalten
   - 🗑️ Quick Wins
   - 🎯 Ausführungsplan

### Schritt 5: Wow Moment
1. Markdown-Vorschau anzeigen
2. Verweisen Sie auf:
   - *„111 Dateien werden automatisch analysiert“*
   - *„67 Dateien können sicher gelöscht werden (Reduzierung um 60 %)“*
   - *„18 v7-spezifische Dateien identifiziert“*
   - *„Ausführungsplan mit Zeitplänen abschließen“*

---

## TIPPS ZUR 💡

### Interaktiv machen
**Fragen Sie die**: *„Welchen Ordner sollten wir analysieren?“*
- ✅ (111 Dateien - beeindruckend)
- Workflow-✅ (121 Dateien - noch größer)
- Web-✅ (26 Dateien - Schnelldemo)
- ✅ (32 Dateien - FAST)

### Anpassen im laufenden Betrieb
**Flexibilität anzeigen**: Ändern des Ordnerpfads in der Eingabeaufforderung:

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Wichtige Funktionen hervorheben
1. **Automation**: *„Keine manuelle Arbeit erforderlich“*
2. **Genauigkeit**: *„Verwendet v8-Dokumentation zum Vergleich“*
3. **Aktionable**: *„Ready-to-Execute-Plan mit Kontrollkästchen“*
4. **Smart**: *„Identifiziert v7-spezifische Funktionen automatisch“*

### Zeitvergleich
**Vorher**: *„Manuelle Analyse = 2-3 Tage pro Ordner“*\
**After**: *„Automatisierte Analyse = 30 Sekunden pro Ordner“*

**ROI**: *„21 Ordner × 2 Tage = 42 Tage → 15 Minuten“*

---

## VORSCHAU DER ERWARTETEN AUSGABE 📊

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

---

## 🎬 DEMOSKRIPT

**Öffnen**:
> „Heute zeige ich Ihnen, wie wir die Neuorganisation der v7-Dokumentation mithilfe von KI automatisiert haben. Das dauerte früher Wochen, jetzt dauert es Minuten.“

**Problem**:
> „Wir haben über 1.500 v7-Dokumentationsdateien. Viele werden in v8 dupliziert. Wir müssen ermitteln, was beibehalten, gelöscht oder migriert werden soll.“

**Lösung**:
> „Wir haben eine intelligente Eingabeaufforderung erstellt, die jeden Ordner analysiert und umsetzbare Empfehlungen generiert.“

**Demo**:
> „Ich zeige es Ihnen. Ich analysiere den Ordner &#39;delivery&#39; mit 111 Dateien…“
> 
> [Eingabeaufforderung kopieren, einfügen, ausführen]
> 
> &quot;…und in 30 Sekunden erhalten wir eine vollständige Analyse.“

**Ergebnisse**:
> „Schauen Sie sich das an:
> - 67 Dateien zu löschen (Reduzierung um 60 %)
> - 18 v7-spezifische Dateien identifiziert
> - 8 zu migrierende Dateien
> - 3-wöchigen Ausführungsplan abschließen
> 
> Alles automatisiert. Alles genau.“

**Schließen**:
> „Derselbe Prozess funktioniert für alle 21 Ordner. Was früher 6 Wochen gedauert hat, dauert jetzt 15 Minuten.“

---

## 🚀 BEREIT ZUR DEMO!

**Nur**:
1. Diese Datei öffnen
2. Eingabeaufforderung kopieren
3. In Cursor einfügen
4. Den magischen ✨ anzeigen

**Demozeit insgesamt**: 3-5 Minuten\
**Wow-Faktor**: 🔥🔥🔥

