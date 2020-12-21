---
solution: Campaign Classic
product: campaign
title: Datenschutz und Einverständniserklärung
description: Weitere Informationen zu Datenschutz und Einverständniserklärung.
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 98%

---


# Häufig gestellte Fragen zum Datenschutz {#privacy-faq}

Im Folgenden finden Sie einige häufig gestellte Fragen zu Datenschutz und Einverständniserklärung bei der Verwendung von Adobe Campaign.

## Schlüsselbegriffe {#key-terms}

### Was sind die Schlüsselbegriffe zum Datenschutz?

Die unten aufgelisteten Elemente verlinken zu den wichtigsten Begriffen und Konzepten im Zusammenhang mit Datenschutz und Einverständniserklärung in Adobe Campaign:

* [Verordnungen zur Datenschutzverwaltung](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Personenbezogene Daten und Personas](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Recht auf Zugriff und Recht auf Vergessenwerden](../../platform/using/privacy-management.md#right-access-forgotten)
* [Einverständnis, Datenbeibehaltung und Benutzerrollen](../../platform/using/privacy-management.md#consent-retention-roles)

## Vorbereitung auf Datenschutzverordnungen{#privacy-regulations-readiness}

### Was empfiehlt Adobe Campaign, um die neuesten Datenschutzverordnungen einzuhalten?

Adobe bietet keine Rechtsberatung. Sie sollten mit Ihrer eigenen Rechtsabteilung zusammenarbeiten, um sicherzustellen, dass alle notwendigen Schritte für DSGVO, CCPA, PDPA, LGPD oder andere relevante Vorschriften unternommen werden.

**Vorbereitung auf Datenzugriffs- und Datenlöschanfragen**

* Legen Sie ein Verfahren für den Empfang/die Beantwortung von Anfragen durch betroffene Personen fest und ernennen Sie einen Datenschutzbeauftragten.

* Überprüfen Sie die in Adobe Campaign gespeicherten Kundendaten und vergeben Sie eindeutige Kennungen (wahrscheinlich ist mehr als eine nötig).

* Bestimmen Sie eine Richtlinie und einen Prozess zur Validierung bzw. zur Authentifizierung, um die Identität von betroffenen Personen zu bestätigen.

* Achten Sie darauf, dass die Antwort an betroffene Personen einfach verständlich ist.

**Überarbeitung des Einverständnisprozesses**

* Nennen und aktualisieren Sie alle für die DSGVO relevanten Kontaktpunkte der Datenerfassung (z. B.: Sprache, Verfahren zur Erteilung des Einverständnisses und Einverständnisprotokolle).

* Achten Sie darauf, dass alle Marketing-E-Mails Abmelde-Links enthalten.

* Überdenken Sie die globale Strategie für das E-Mail-Marketing, um landesspezifische Implementierungen festzulegen.

**Analyse der Daten**

* Überprüfen Sie alle Quellen für den Datenimport und die Datenerfassung, aus denen Daten in Adobe Campaign übertragen werden, und dokumentieren Sie, welche Felder für Ihre Marketing-Zwecke verwendet werden.

* Entfernen Sie nicht genutzte Datenattribute aus der Adobe Campaign-Datenbank.

* Verwenden Sie die in Adobe Campaign verfügbaren Daten zu dem Zweck, zu dem sie erfasst wurden, und bieten Sie Ihren Kunden stärker personalisierte Erlebnisse.

* Überarbeiten und aktualisieren Sie Datenzugriffsgenehmigungen, um sicherzustellen, dass Benutzer von Adobe Campaign nur die für ihre Kampagnen benötigten Daten verwenden, aber darüber hinaus auf keine weiteren Daten zugreifen können.

* Achten Sie darauf, dass jeder Benutzer von Adobe Campaign die entsprechenden Zugriffsberechtigungen für die Durchführung seiner Aufgaben hat, aber keine darüber hinausreichenden Rechte.

## Benutzerinteraktion aufrecht erhalten{#preserve-user-engagement}

### Wie können Datenverantwortliche das Einverständnis ihrer Kunden erlangen, ohne die Benutzerinteraktion zu beeinträchtigen?

In den Fällen, in denen das Einverständnis für bestimmte Marketing-Aktivitäten erforderlich ist, muss eine aktive Einverständniserklärung vom Verbraucher gegeben werden (d. h. kein Schweigen als Einverständnis oder vorab markierte Kontrollkästchen). Diese Einverständniserklärung muss außerdem ungebündelt erfolgen und darf nicht davon abhängig gemacht werden, dass Dienstleistungen angeboten werden.

Es kann sogar Fälle geben, in denen bestimmte Einverständniserklärungen aktualisiert werden müssen, damit die Daten in Zukunft weiterverwendet werden können.

Anstatt diese zusätzlichen Anforderungen als Gefahr für die Werbewirtschaft zu erachten, könnten Marketing-Experten sie als echten Indikator für Markeninteraktion und -loyalität sowie Kundenzufriedenheit und Vertrauen nutzen.

## Einverständnis verwalten{#manage-consent}

### Wie können Datenverantwortliche das Einverständnis in Adobe Campaign verwalten?

Adobe Campaign bietet bereits Funktionen zur Einverständnisverwaltung auf mehr Ebenen, als die meisten Marketing-Experten nutzen: über benutzerdefinierte Datenfelder oder über einen oder mehrere Dienste.

Marketing-Experten sollten sich von ihrer Rechtsabteilung beraten lassen und dann die bereits in Adobe Campaign integrierten Funktionen nutzen.

So kann zum Beispiel das Datenmodell in Adobe Campaign erweitert werden, um nicht nur zu verfolgen, ob sich Personen für ein Einverständnis entschieden haben, sondern auch um den Zeitstempel des Einverständnisses und eine Art Indikator zu tracken, der den genauen Umfang des Einverständnisses erfasst.

## Datenlöschung {#data-deletion}

### Welche Daten werden von Datenverantwortlichen in Adobe Campaign gelöscht, wenn sie eine Kundenanfrage einer betroffenen Person erhalten?

Alle mit der betroffenen Person verknüpften Daten werden gelöscht, einschließlich vordefinierter und benutzerdefinierter Tabellen.

Technisch gesehen werden alle Daten gelöscht, die mit der betroffenen Person mit `integrity="own"` verknüpft sind.

Als Datenverantwortlicher haben Sie die Möglichkeit, diese Einstellung anzupassen, indem Sie die Integrität der in den Datenschemata definierten Links ändern (z. B. wenn Sie einen geschäftlichen Grund haben, bestimmte Daten nicht zu löschen).

### Wie wirkt sich die Löschung von Versand- und Trackinglogs auf Berichte aus?

Berichte in Adobe Campaign basieren auf Indikatoren, die von aggregierten Daten aus Versand- und Trackinglogs berechnet werden. Deshalb sollte das Entfernen von einzelnen Logs keine Auswirkungen auf die in den Berichten dargestellten Metriken haben.

## Daten erneut importieren {#re-import-data}

### Muss ich darauf achten, dass Daten zu einem späteren Zeitpunkt möglicherweise erneut importiert werden?

In Adobe Campaign werden Datensätze häufig aus einer externen Datenquelle hochgeladen.

Als Datenverantwortlicher müssen Sie sicherstellen, dass beim Erhalt einer Löschanfrage alle entsprechenden Daten der betroffenen Person aus allen Ihren Systemen gelöscht werden.

## Erneuter Opt-in {#opt-in-again}

**Kann ein Datensubjekt, dessen Daten aus Adobe Campaign gelöscht wurden, später Opt-in?**

Eine betroffene Person kann sich erneut anmelden oder als neuer Empfänger hinzugefügt werden, nachdem ihre Daten aus Adobe Campaign gelöscht wurden.

Sie können das Audit-Protokoll verwenden, in dem angegeben wird, wann die vorherige Löschung durchgeführt und der neue Empfänger angelegt wurde.