---
solution: Campaign Classic
product: campaign
title: Datenschutz und Einverständniserklärung
description: Weitere Informationen zu Datenschutz und Zustimmung
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 28%

---


# Datenschutz FAQ {#privacy-faq}

Im Folgenden finden Sie einige der häufig gestellten Fragen zum Datenschutz und zur Zustimmung bei der Verwendung von Adobe Campaign.

## Schlüsselbegriffe {#key-terms}

**Was sind die Schlüsselbegriffe zum Datenschutz?**

Die unten aufgelisteten Elemente verlinken zu den wichtigsten Begriffen und Begriffen im Zusammenhang mit Datenschutz und Zustimmung in Adobe Campaign:

* [Vorschriften zum Datenschutzmanagement](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Persönliche Daten und Personas](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Recht auf Zugriff und Recht auf Vergessenwerden](../../platform/using/privacy-management.md#right-access-forgotten)
* [Einverständnis, Datenbeibehaltung und Benutzerrollen](../../platform/using/privacy-management.md#consent-retention-roles)

## Einhaltung der Datenschutzbestimmungen {#privacy-regulations-readiness}

**Was schlägt Adobe Campaign vor, die neuesten Datenschutzbestimmungen einzuhalten?**

Adobe bietet keine Rechtsberatung. Sie sollten mit Ihrem eigenen Rechtsbeistand zusammenarbeiten, um sicherzustellen, dass diese alle notwendigen Schritte in Richtung GDPR, CCPA, PDPA, LGPD oder anderer relevanter Regulierungsbereitschaft unternehmen.

**Vorbereiten für Datenzugriffs- und Löschanforderungen**

* Identifizieren Sie einen Prozess, der auf Anfragen zu Data Subject antwortet, einschließlich der Benennung eines Datenschutzbeauftragten.

* Überprüfen Sie die in Adobe Campaign gespeicherten Kundendaten und vergeben Sie eindeutige Kennungen (wahrscheinlich ist mehr als eine nötig).

* Bestimmen Sie eine Validierungs-/Authentifizierungsrichtlinie und einen Prozess für die Identitätsbestätigung des Datenbetreibers.

* Achten Sie darauf, dass die Antwort an Datensubjekte einfach verständlich ist.

**Zustimmung erwägen**

* Liste und erforderlichenfalls Aktualisierung aller Berührungspunkte für die Datenerfassung für GDPR (z. B. Sprach-, Zustimmungs- und Zustimmungsprotokolle).

* Achten Sie darauf, dass alle Marketing-E-Mails Abmelde-Links enthalten.

* Überdenken Sie die globale Strategie für das E-Mail-Marketing, um landesspezifische Implementierungen festzulegen.

**Daten analysieren**

* Überprüfen Sie alle Datenimportquellen und erfassen Sie Quellen, aus denen Daten in Adobe Campaign fließen, sowie Dokument, welche Felder für Ihre Marketingbemühungen verwendet werden.

* Entfernen Sie nicht genutzte Datenattribute aus der Adobe-Campaign-Datenbank.

* Verwenden Sie die in Adobe Campaign verfügbaren Daten zu dem Zweck, zu dem sie erfasst wurden, und bieten Sie Ihren Kunden stärker personalisierte Erlebnisse.

* Überarbeiten und aktualisieren Sie Datenzugriffsgenehmigungen, um sicherzustellen, dass Benutzer von Adobe Campaign nur die für ihre Kampagnen benötigten Daten verwenden, aber darüber hinaus auf keine weiteren Daten zugreifen können.

* Vergewissern Sie sich, dass jeder Benutzer von Adobe Campaign über die entsprechenden Zugriffsrechte verfügt, um die erforderlichen Aufgaben auszuführen, aber keine anderen Rechte zur Durchführung zusätzlicher Aufgaben hat.

## Benutzerbindung beibehalten {#preserve-user-engagement}

**Wie können Datenverantwortliche das Einverständnis ihrer Kunden erlangen, ohne die Benutzerinteraktion zu beeinträchtigen?**

In den Fällen, in denen die Zustimmung für bestimmte Aktivitäten erforderlich sein wird, muss die Zustimmung des Verbrauchers aktiv sein (d. h. keine Schweigepflicht als Zustimmungs- oder Kontrollkästchen), entbündelt werden und darf nicht davon abhängig gemacht werden, dass die Dienstleistungen angeboten werden.

Es kann sogar Fälle geben, in denen bestimmte Zustimmungen aktualisiert werden müssen, damit die Daten in Zukunft weiter verwendet werden können.

Anstatt diese erweiterten Zustimmungsanforderungen als Risiko für das marktfähige Universum zu betrachten, könnten Marketingfachleute sie als echten Indikator für Markenbindung und -loyalität sowie Kundenzufriedenheit und Vertrauen einsetzen.

## Zustimmung verwalten {#manage-consent}

**Wie können Datenkontrolleure die Zustimmung in Adobe Campaign verwalten?**

Adobe Campaign bietet bereits Funktionen zur Verwaltung von Einwilligungen auf mehr Ebenen als die meisten Marketingexperten über benutzerdefinierte Datenfelder oder über einen oder mehrere Dienste.

Marketingexperten sollten sich mit ihrem Rechtsbeistand beraten lassen, wie sie vorgehen, und dann die bereits in Adobe Campaign integrierten Funktionen nutzen.

Beispielsweise die Ausweitung des Datenmodells in Adobe Campaign auf die Verfolgung nicht nur, wenn sich Personen für eine Teilnahme entschieden haben, sondern auch den Zeitstempel des Opt-in und eine Art von Indikator, der den genauen Umfang der Zustimmung erfasst.

## Löschen von Daten {#data-deletion}

**Welche Daten können Datenkontrolleure im Adobe Campaign löschen, wenn ein Datenbetreff eine Kundenanfrage stellt?**

Alle mit dem Datenfach verknüpften Daten werden gelöscht, einschließlich vordefinierter und benutzerdefinierter Tabellen.

Technisch gesehen werden alle Daten, die mit dem Datenfach verbunden `integrity="own"` sind, gelöscht.

Als Data Controller haben Sie die Möglichkeit, diese Einstellung anzupassen, indem Sie die Integrität der in den Data Schemas definierten Links ändern (z. B. wenn Sie eine geschäftliche Begründung haben, um bestimmte Daten nicht zu löschen).

**Wie wirkt sich die Löschung von Versand- und Trackinglogs auf Berichte aus?**

Berichte in Adobe Campaign basieren auf Indikatoren, die von aggregierten Daten aus Versand- und Trackinglogs berechnet werden. Deshalb sollte das Entfernen von einzelnen Logs keine Auswirkungen auf die in den Berichten dargestellten Metriken haben.

## Daten erneut importieren {#re-import-data}

**Im Adobe Campaign werden Datensätze häufig aus einer externen Datenquelle hochgeladen. Muss ich darauf achten, dass Daten zu einem späteren Zeitpunkt erneut importiert werden?**

Als Datenverantwortlicher müssen Sie sicherstellen, dass beim Erhalt einer Löschungsanfrage alle entsprechenden Daten des Datensubjekts aus allen Ihren Systemen gelöscht werden.

## Opt-in {#opt-in-again}

**Kann sich ein Datensubjekt, dessen Daten aus Adobe Campaign gelöscht wurde, zu einem späteren Zeitpunkt noch einmal anmelden?**

Eine betroffene Person kann sich erneut anmelden oder als neuer Empfänger hinzugefügt werden, nachdem ihre Daten aus dem Adobe Campaign gelöscht wurden.

Sie können den Prüfpfad verwenden, in dem Details zum Zeitpunkt des vorherigen Löschens und zum Zeitpunkt der Erstellung des neuen Empfängers aufgeführt sind.