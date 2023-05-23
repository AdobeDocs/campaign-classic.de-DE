---
product: campaign
title: Zu wartende Tabellen
description: Zu wartende Tabellen
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 3%

---

# Zu wartende Tabellen{#tables-to-maintain}



Die Liste der zu pflegenden Tabellen hängt von Ihrer Adobe Campaign-Version, ihrer Verwendung und der Konfiguration des Datenmodells ab.

Die folgende Liste enthält nur die Tabellen, die am stärksten fragmentiert sind. Die Auswirkungen lauten wie folgt:

* Überbelegung von Speicherplatz, was sich auf den Datenbankzugriff auswirkt,
* nicht regelmäßig aktualisierte Indizes, was die Abfrageleistung verlangsamt.

## Adobe Campaign-Tabellen {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Tabellenname </strong><br /> </th> 
   <th> <strong>Größe</strong><br /> </th> 
   <th> <strong>Haupttyp der Aktivität</strong><br /> </th> 
   <th> <strong>Erklärung</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Pro Versandaktion ist ein Datensatz vorhanden. Ein einzelner Datensatz kann mehrmals aktualisiert werden, um den Versandfortschritt widerzuspiegeln. Die Indizes in dieser Tabelle neigen daher dazu, schnell zu fragmentieren. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Arbeitstabelle, in welche Datensätze bei der Versandvorbereitung eingefügt werden. Diese werden dann während des Versands aktualisiert und nach Abschluss des Versands gelöscht.<br /> Diese Tabelle neigt dazu, schnell zu fragmentieren, obwohl ihre durchschnittliche Größe recht begrenzt ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Diese Tabelle enthält die Informationen, die zum Generieren personalisierter Mirrorseiten erforderlich sind. Es enthält ein Memo-Feld (CLOB) und ist daher in der Regel sehr groß. Das Volumen ist direkt proportional zum Verlauf der Mirrorseiten, die gespeichert werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Diese Tabelle enthält Statistiken zum Versandprozess. Ihre Aufzeichnungen werden regelmäßig aktualisiert. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Aktualisierungen, Einfügungen<br /> </td> 
   <td> Diese Tabelle enthält Informationen zu E-Mail-Adressen. Sie wird im Rahmen des Quarantänevorgangs häufig aktualisiert (Datensätze werden beim ersten Versandfehler erstellt, bei Änderung der Zähler aktualisiert und nach erfolgreichem Versand gelöscht). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Pro Workflow-Instanz gibt es einen Datensatz, also nur sehr wenige Datensätze. Die Tabelle wird jedoch regelmäßig aktualisiert, um Status und Fortschritt widerzuspiegeln.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Jede Ausführung einer Workflow-Aktivität führt zur Erstellung eines Datensatzes in dieser Tabelle. Der Bereinigungsmechanismus löscht sie, sobald sie abgelaufen sind.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Jede Transition, die zwischen Aufgaben in einem Workflow aktiviert wird, führt zur Erstellung eines Datensatzes in dieser Tabelle. Der Bereinigungsmechanismus löscht sie, sobald sie abgelaufen sind. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Sehr klein <br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Diese Tabelle ist spezifisch für die Workflow-Engine. Dies ermöglicht das Senden von Befehlen an Workflows (z. B. Start, Stopp, Pause). Diese Tabelle ist zwar klein, wird aber bei der Bereinigung der mit Workflows verknüpften Transaktionstabellen berücksichtigt.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Größter<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Dies ist die größte Tabelle im System. Pro gesendeter Nachricht wird ein Datensatz gesendet. Diese Datensätze werden eingefügt, aktualisiert, um den Versandstatus zu verfolgen, und beim Löschen des Verlaufs gelöscht. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Trackinglogs werden eingefügt und gelöscht, wenn der Verlauf bereinigt wird, sie werden jedoch nicht aktualisiert. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Diese Tabelle enthält Informationen zum Qualifizieren von SMTP-Fehlern. Sie ist relativ klein, wird jedoch massiv aktualisiert, sodass Indizes auf dieser Tabelle häufig schnell fragmentiert werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Diese Tabelle enthält die Aggregate für SMTP-Fehler, sortiert nach Domain. Er enthält zunächst detaillierte Informationen, die von der Bereinigungsaufgabe aggregiert werden, sobald sie veraltet ist. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (auf einer Mid-Sourcing-Instanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Nur wenn die Instanz 5.10 (oder höher) als Mid-Sourcing-Instanz verwendet wird. Dies ist eine der größten Tabellen in der Datenbank. Pro gesendeter Nachricht wird ein Datensatz gesendet. Diese Datensätze werden eingefügt, aktualisiert, um den Versandstatus zu verfolgen, und beim Löschen des Verlaufs gelöscht. Bei der Verwendung von Mid-Sourcing besteht die Empfehlung darin, den Verlauf zu begrenzen (in der Regel weniger als zwei Monate). Daher bleibt diese Tabelle im Hinblick auf die Größe vernünftig (weniger als 30 Go for 60 Millionen rows, data+index). Es ist jedoch sehr wichtig, sie von Zeit zu Zeit neu zu erstellen. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (wenn die NmsRecipient-Tabelle verwendet wird) <br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Dies ist die größte Tabelle im System. Pro gesendeter Nachricht wird ein Datensatz gesendet. Diese Datensätze werden eingefügt, aktualisiert, um den Versandstatus zu verfolgen, und beim Löschen des Verlaufs gelöscht. Beachten Sie, dass diese Tabelle in Version 5.10 kleiner ist als die Entsprechung in Version 4.05 (NmsBroadLog), da der SMTP-Nachrichtentext in der Tabelle NmsBroadLogMsg in Version 5.10 faktorisiert ist. Es ist jedoch nach wie vor wichtig, diese Tabelle regelmäßig neu zu indizieren (alle zwei Wochen zu Beginn) und sie von Zeit zu Zeit (einmal im Monat oder bei beeinträchtigter Leistung) vollständig neu zu erstellen. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXx (wenn eine externe Empfängertabelle verwendet wird)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Entspricht NmsBroadLogRcp aber mit einer externen Empfängertabelle. Passen Sie YYY und XXX an die Werte in Ihrem Versand-Mapping an. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (wenn die NmsRecipient-Tabelle verwendet wird) <br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Trackinglogs werden eingefügt und gelöscht, wenn der Verlauf bereinigt wird, sie werden jedoch nicht aktualisiert. Das Volumen hängt von der Dauer der Datenaufbewahrung ab. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXx (wenn die externe Empfängertabelle verwendet wird)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Entspricht NmsTrackingLogRcp, aber mit einer externen Empfängertabelle. Passen Sie YYY und XXX an die Werte an, die in Ihrem Versand-Mapping verwendet werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Ähnlich wie bei anderen Broadlog-Tabellen, jedoch mit dem NmsRtEvent anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Ähnlich wie bei anderen trackingLog -Tabellen, jedoch mit der NmsRtEvent -Tabelle anstelle von NmsRecipient .<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Tabelle, die die Message-Center-Ereigniswarteschlange enthält. Der Status dieser Ereignisse wird von Message Center bei der Verarbeitung aktualisiert. Löschungen werden während der Bereinigung durchgeführt. Wir empfehlen Ihnen, den Index dieser Tabelle regelmäßig neu zu erstellen und neu zu erstellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (Message Center-Kontrollinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Ähnlich wie NmsRtEvent. Diese Tabelle archiviert alle Ereignisse aus allen Ausführungsinstanzen. Sie wird nicht in Echtzeit, sondern nur von Berichten verwendet.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Sehr klein<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Tabellen mit Mobile Apps und deren Konfiguration.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen<br /> </td> 
   <td> Tabelle mit den Kennungen der Mobilgeräte (Adressen), die zum Senden der Benachrichtigung verwendet werden (ähnlich wie bei einer Empfängertabelle).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Ähnlich wie bei anderen Broadlog-Tabellen, jedoch mit NmsappSubscriptionRcp anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Ähnlich wie bei anderen trackingLog-Tabellen, jedoch mit der Tabelle NmsappSubscriptionRcp anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Tabelle mit Benutzersitzungen. Die Anzahl der Einfügungen und Löschungen ist sehr wichtig.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Kundentabellen {#customer-tables}

Zusätzlich zur obigen Liste können auch Tabellen, die von Kunden erstellt wurden (die nicht im Adobe Campaign-Datenmodell vorhanden sind), während der Plattformeinrichtung fragmentiert werden, insbesondere wenn sie häufig während der Datenladevorgänge oder Synchronisierungsvorgänge aktualisiert werden. Diese Tabellen können Teil des standardmäßigen Adobe Campaign-Datenmodells sein (z. B. **NmsRecipient**). In diesem Fall ist es Sache des Administrators der Adobe Campaign-Plattform, eine Prüfung seines spezifischen Datenbankmodells durchzuführen, um diese benutzerdefinierten Tabellen zu finden. Diese Tabellen werden nicht unbedingt in unseren Wartungsverfahren explizit erwähnt.
