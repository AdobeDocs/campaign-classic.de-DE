---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# Dokumentations-Reorganisations-Kit für 📚 v7

**2 Eingabeaufforderungen für Analyzer und Réorganisator für DOC v7 → v8**

---

## 📁 Fichiers

### 🔍 (Anweisungen)

| Fichier | Beschreibung | Ausgabe |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analyse der Details des UN-Ordners in % Übereinstimmung | `[folder]-detailed-analysis.md` |

---

## 🚀

### 1️⃣ Vue d&#39;Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**genère** :
- 📊 Zusammenfassung (stats globales)
- 📁 Analysieren der 21 Ordner
- 🎯 Matrice de priorization
- ✅ Aktionselemente
- ⚠️ Risiken
- 📈 Metriken

**Taille** : ~50-60 Seiten Markdown

---

### 2️⃣ Analysieren der Details zum Ordner

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**genère** :
- 📊 des Ordners „Statistiken“
- 📋 Tableau détaillé organisé comme Experience League
- 🔗 Liens Cliquables (v7 + Experience League)
- 📈 Jusqu&#39;à 3 Treffer v8 par fichier avec %
- 📄 Recap-Datei par-Datei
- 🎯
- ✅ Checkboxes für das Tracking

**Taille** : Markdown für ~30-40 Seiten

---

## 📊 Beispiel für die Ausgabe

### Eingabeaufforderung 1 (Übersicht)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Eingabeaufforderung 2 (Ordner „Detailed„)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

---

## 🎯 Workflow-Empfehlung

### Semaine 1 : Vue d&#39;ensemble
1. **Eingabeaufforderung 1** → obtenir `v7-reorganization-overview.md`
2. Priorisierung der Ordner ohne Kennung
3. Partner hat Stakeholder

### Semaine 2-4 : Details analysieren
1. Schachtel-Ordner-Prioritätsstufe :
   - Ausführen **Eingabeaufforderung 2**
   - `[folder]-detailed-analysis.md`
   - Validieren von Entscheidungen
   - Starterlose Aktionen

### Semaine 5+ : Ausführung
1. Supprimer les fichiers identifiés (DELETE)
2. Badger les fichiers v7-only (KEEP)
3. Migrant le contenu manquant (MOVE)
4. Reviewer les cas ambius (REVIEW)

---

## 💡 Tipps

### Keine Eingabeaufforderungen
- ✅ Copier/Coller l&#39;intégralité du prompt
- ✅ Ne pas-Modifikator le format
- ✅ Adapter seulement le chemin du folder (Eingabeaufforderung 2)

### Ausgänge ohne Strom
- 📝 Output en Markdown (Pas HTML)
- 🔗 Liens cliquables automatiques
- ✅ Checkboxes für das Tracking
- 📊
- 🎨 Emojis et icônes

### Analyse
- 🎯 Ordner des Typs „Anfänger ohne Arbeit“ (Versand, Workflow)
- ⚡ Prioriser les quick wins (95-100% Übereinstimmung)
- 🔍 Prüfer-Handbuch les cas ambius (&lt;70% Übereinstimmung)
- ✅ Valider avec SME Avant-Unterdrückung massiv

---

## ⚠️ wichtig

### Avant de supprimer
1. ✅ v8-Version
2. ✅ Verifier qu&#39;il n&#39;y a pas de contenu v7-specific
3. ✅ Mettre à jour `redirects.csv`
4. ✅ Valider avec un expert (pour les premiers)

### Nur für Fischers v7
1. ✅ Ajouter un badge au debüt du fichier
2. ✅ Expliquer pourquoi c&#39;est v7-only
3. ✅ Lien vers les limits v8

---

## 🆘

**Fragen** ?
- Prompt ne fonctionne pas → Vérifier les chemins des repos
- Output trop long → Demander un résumé
- Besoin d&#39;aide → Ping l&#39;équipe doc

---

**Dernière mise à jour** : 13.01.2026

