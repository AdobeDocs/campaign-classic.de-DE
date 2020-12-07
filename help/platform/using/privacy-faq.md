---
solution: Campaign Classic
product: campaign
title: Datenschutz und Einverständniserklärung
description: Weitere Informationen zu Datenschutz und Einverständniserklärung.
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: ht
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: ht
source-wordcount: '808'
ht-degree: 100%

---


# Häufig gestellte Fragen zum Datenschutz {#privacy-faq}

Im Folgenden finden Sie einige der häufig gestellten Fragen zum Datenschutz und zum Einverständnis bei der Verwendung von Adobe Campaign.

## Schlüsselbegriffe {#key-terms}

**Was sind die Schlüsselbegriffe zum Datenschutz?**

Die unten aufgelisteten Elemente verlinken zu den wichtigsten Begriffen und Konzepten im Zusammenhang mit Datenschutz und Einverständniserklärungen in Adobe Campaign:

* [Bestimmungen zur Datenschutzverwaltung](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Persönliche Daten und Personas](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Recht auf Zugriff und Recht auf Vergessenwerden](../../platform/using/privacy-management.md#right-access-forgotten)
* [Einverständnis, Datenbeibehaltung und Benutzerrollen](../../platform/using/privacy-management.md#consent-retention-roles)

## Einhaltung der Datenschutzbestimmungen {#privacy-regulations-readiness}

**Welche Maßnahmen werden empfohlen, um in Adobe Campaign die neuesten Datenschutzbestimmungen einzuhalten?**

Adobe bietet keine Rechtsberatung. Sie sollten mit Ihrer eigenen Rechtsabteilung zusammenarbeiten, um sicherzustellen, dass diese alle notwendigen Schritte zur Einhaltung der DSGVO, CCPA, PDPA, LGPD oder anderer jeweils geltender Bestimmungen unternimmt.

**Vorbereitungen für Datenzugriffs- und Löschanfragen**

* Arbeiten Sie einen Prozess für den Eingang / die Bearbeitung von Anfragen betroffener Personen aus. Benennen Sie dabei auch einen Datenschutzbeauftragten als Ansprechpartner.

* Überprüfen Sie die in Adobe Campaign gespeicherten Kundendaten und vergeben Sie eindeutige Kennungen (wahrscheinlich ist mehr als eine nötig).

* Bestimmen Sie eine Richtlinie, nach der die Validierung und Authentifizierung geregelt wird, sowie einen Prozess für die Bestätigung der Identität betroffener Personen.

* Achten Sie darauf, dass die Antwort an die betroffene Person einfach verständlich ist.

**Einverständnis berücksichtigen**

* Führen Sie alle für die DSGVO relevanten Kontaktpunkte der Datenerfassung auf und aktualisieren Sie sie nach Bedarf (d. h. berücksichtigen Sie die Sprache, das Verfahren zur Mitteilung des Einverständnisses und die Einverständnisprotokolle).

* Achten Sie darauf, dass alle Marketing-E-Mails die Links zum Beenden des Abos enthalten.

* Überdenken Sie die globale Strategie für das E-Mail-Marketing, um landesspezifische Implementierungen festzulegen.

**Ihre Daten verstehen**

* Verschaffen Sie sich ein Bild aller Datenquellen, aus denen via Import oder Erfassung Daten an Adobe Campaign übermittelt werden, und dokumentieren Sie, welche Felder Sie für Ihre Marketing-Maßnahmen verwenden.

* Entfernen Sie alle nicht genutzten Datenattribute aus Ihrer Adobe Campaign-Datenbank.

* Verwenden Sie die in Adobe Campaign verfügbaren Daten zu dem Zweck, zu dem sie erfasst wurden, und bieten Sie Ihren Kunden stärker personalisierte Erlebnisse.

* Überarbeiten und aktualisieren Sie Datenzugriffsgenehmigungen in einer Weise, die sicherstellt, dass Benutzer von Adobe Campaign nur die für ihre Kampagnen benötigten Daten verwenden können, aber darüber hinaus auf keine weiteren Daten zugreifen können.

* Stellen Sie sicher, dass jeder Benutzer von Adobe Campaign über seinem jeweiligen Aufgabenbereich entsprechende Zugriffsrechte verfügt, jedoch über keine darüber hinausgehende.

## Aufrechterhalten der Interaktion mit Benutzern {#preserve-user-engagement}

**Wie können Datenverantwortliche das Einverständnis ihrer Kunden erlangen, ohne die Benutzerinteraktion zu sehr zu beeinträchtigen?**

In Fällen, in denen Marketing-Aktivitäten das Einverständnis des Verbrauchers bedürfen, muss dieser sein Einverständnis aktiv erklären, d. h., weder stillschweigend oder durch vorab aktivierte Kontrollkästchen, noch im Rahmen einer andere Sachverhalte betreffenden Erklärung. Ferner darf das Einverständnis nicht an das Angebot der Services gebunden sein.

Auch gibt es Fälle, in denen eine weitere Nutzung der Daten erst nach erneuter Erteilung des Einverständnisses der betroffenen Person gestattet ist.

Diese verschärften Anforderungen für das Einholen von Einverständnis sollten Marketer jedoch nicht als Risiko in Bezug auf die Kundenansprache ansehen. Denn tatsächlich können sie sie als Mittel verstehen, das ihnen präzise Erkenntnisse zu Interaktionsumfang und Markentreue sowie zu Kundenzufriedenheit und -vertrauen verschafft.

## Verwalten des Einverständnisses {#manage-consent}

**Wie können Datenverantwortliche das Einverständnis in Adobe Campaign verwalten?**

Adobe Campaign bietet Funktionen zur Einverständnisverwaltung, die bereits mehr Ebenen abdecken, als die meisten Marketing-Experten nutzen, die hierfür auf individuell angepasste Datenfelder oder einen oder mehrere Services zurückgreifen.

Marketer sollten ihr weiteres Vorgehen in Konsultation mit der Rechtsabteilung bestimmen und für die Umsetzung die bereits in Adobe Campaign integrierten Funktionen verwenden.

Ein in diesem Zusammenhang mögliches Szenario wäre etwa, das Datenmodell von Adobe Campaign dahingehend zu erweitern, dass nicht nur die Anmeldung einer bestimmten Person erfasst wird, sondern auch der diesem Opt-in zugehörige Zeitstempel sowie bestimmte Messgrößen, die Aufschluss über den genauen Umfang des Einverständnisses geben.

## Löschung von Daten {#data-deletion}

**Inwieweit lassen sich in Adobe Campaign die Daten von Personen löschen, die eine entsprechende Anfrage einreichen?**

Alle Daten, die mit der betroffenen Person verknüpft sind, können gelöscht werden. Dies gilt für vordefinierte ebenso wie für benutzerdefinierte Tabellen.

Aus technischer Sicht wird die Löschung auf alle Daten angewendet, die der betroffenen Person über `integrity="own"` zugeordnet sind.

Als Datenverantwortlicher können Sie dies über die Integrität der in den Datenschemata definierten Verknüpfungen anpassen (z. B. für den Fall, dass Sie aufgrund eines berechtigten geschäftlichen Interesses nicht verpflichtet sind, bestimmte Daten zu löschen).

**Wie wirkt sich die Löschung von Versand- und Trackinglogs auf Berichte aus?**

Berichte in Adobe Campaign basieren auf Indikatoren, die von aggregierten Daten aus Versand- und Trackinglogs berechnet werden. Deshalb sollte das Entfernen von einzelnen Logs keine Auswirkungen auf die in den Berichten dargestellten Metriken haben.

## Erneutes Importieren von Daten {#re-import-data}

**Adobe Campaign erhält Daten häufig über Uploads aus externer Quelle. Ist Vorsicht dahingehend geboten, dass es zu einem Zeitpunkt zu erneuten Daten-Importen kommen könnte?**

Als Datenverantwortlicher müssen Sie sicherstellen, dass beim Erhalt einer Löschungsanfrage alle entsprechenden Daten der betroffenen Person aus allen Ihren Systemen gelöscht werden.

## Erneuter Opt-in {#opt-in-again}

**Kann eine betroffene Person, deren Daten aus Adobe Campaign gelöscht wurden, zu einem späteren Zeitpunkt noch einmal ein Opt-In vornehmen?**

Eine betroffene Person, deren Daten aus Adobe Campaign gelöscht wurden, kann einen erneuten Opt-in vornehmen oder als neuer Empfänger hinzugefügt werden.

Im Audit-Protokoll finden Sie Details dazu, zu welchem Zeitpunkt die ursprüngliche Löschung vorgenommen und der neue Empfänger hinzugefügt wurde.