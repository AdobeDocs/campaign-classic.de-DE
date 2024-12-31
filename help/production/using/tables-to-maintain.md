---
product: campaign
title: Zu wartende Tabellen
description: Zu wartende Tabellen
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 1%

---

# Zu wartende Tabellen{#tables-to-maintain}



Die Liste der beizubehaltenden Tabellen hängt von Ihrer Adobe Campaign-Version, deren Verwendung und der Datenmodellkonfiguration ab.

Die folgende Liste enthält nur die Tabellen, die am häufigsten fragmentiert sind. Dies hat folgende Auswirkungen:

* übermäßiger Verbrauch von Festplattenspeicher, wodurch der Datenbankzugriff beeinträchtigt wird,
* Indizes, die nicht regelmäßig aktualisiert wurden, wodurch die Abfrageleistung verlangsamt wird.

## Adobe Campaign-Tabellen {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Tabellenname </strong><br /> </th> 
   <th> <strong>size</strong><br /> </th> 
   <th> <strong>Haupttätigkeitstyp</strong><br /> </th> 
   <th> <strong>Erklärung</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Pro Versandaktion gibt es einen Datensatz. Ein einzelner Datensatz kann mehrmals aktualisiert werden, um den Versandfortschritt widerzuspiegeln, sodass Indizes in dieser Tabelle in der Regel schnell fragmentiert werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Arbeitstabelle, in die während der Versandvorbereitung Datensätze eingefügt werden. Sie werden dann während des Versands aktualisiert und schließlich gelöscht, sobald der Versand abgeschlossen ist.<br /> Diese Tabelle neigt dazu, schnell zu fragmentieren, obwohl ihre durchschnittliche Größe ziemlich begrenzt ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Diese Tabelle enthält die Informationen, die zum Generieren personalisierter Mirror-Seiten erforderlich sind. Es enthält ein Memo-Feld (CLOB) und ist daher tendenziell sehr groß. Das Volumen ist direkt proportional zur Historie der beibehaltenen Mirror-Seiten. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Diese Tabelle enthält Statistiken zum Versandprozess. Seine Aufzeichnungen werden regelmäßig aktualisiert. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Aktualisierungen, Einfügen<br /> </td> 
   <td> Diese Tabelle enthält Informationen zu E-Mail-Adressen. Sie wird im Rahmen der Quarantäne häufig aktualisiert (Datensätze werden beim ersten Versandfehler erstellt, aktualisiert, wenn sich die Zähler ändern, und gelöscht, sobald der Versand erfolgreich war). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Pro Workflow-Instanz gibt es einen Datensatz, sodass nur sehr wenige Datensätze vorhanden sind. Die Tabelle wird jedoch regelmäßig aktualisiert, um den Status und den Fortschritt widerzuspiegeln.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Jede Ausführung einer Workflow-Aktivität führt zur Erstellung eines Datensatzes in dieser Tabelle. Der Bereinigungsmechanismus löscht sie, sobald sie abgelaufen sind.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Jede Transition zwischen Aufgaben in einem Workflow führt zur Erstellung eines Datensatzes in dieser Tabelle. Der Bereinigungsmechanismus löscht sie, sobald sie abgelaufen sind. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Sehr kleine <br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Diese Tabelle ist spezifisch für die Workflow-Engine. Es ermöglicht das Senden von Befehlen an Workflows (z. B. Starten, Stoppen, Pause). Diese Tabelle ist zwar klein, wird aber bei der Bereinigung der mit Workflows verknüpften Transaktionstabellen berücksichtigt.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Größte<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Dies ist die größte Tabelle im System. Pro gesendeter Nachricht wird ein Datensatz verwendet. Diese Datensätze werden eingefügt, aktualisiert, um den Versandstatus zu verfolgen, und gelöscht, wenn der Verlauf bereinigt wird. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Trackinglogs werden eingefügt und gelöscht, wenn der Verlauf bereinigt wird. Sie werden jedoch nicht aktualisiert. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Diese Tabelle enthält Informationen, die zur Qualifizierung von SMTP-Fehlern verwendet werden. Er ist relativ klein, wird aber massiv aktualisiert, sodass Indizes auf dieser Tabelle tendenziell schnell fragmentiert werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Medium<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Diese Tabelle enthält die Aggregate für SMTP-Fehler, sortiert nach Domain. Sie enthält zunächst detaillierte Informationen, die von der Bereinigungsaufgabe aggregiert werden, sobald sie veraltet ist. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (auf einer Mid-Sourcing-Instanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Nur wenn die Instanz 5.10 (oder höher) als Mid-Sourcing-Instanz verwendet wird. Dies ist eine der größten Tabellen in der Datenbank. Pro gesendeter Nachricht wird ein Datensatz verwendet. Diese Datensätze werden eingefügt, aktualisiert, um den Versandstatus zu verfolgen, und gelöscht, wenn der Verlauf bereinigt wird. Bei der Verwendung von Mid-Sourcing wird empfohlen, den Verlauf zu begrenzen (in der Regel weniger als zwei Monate), sodass diese Tabelle hinsichtlich der Größe angemessen bleibt (weniger als 30 Vorgänge für 60 Millionen Zeilen, data+index), aber es ist sehr wichtig, sie von Zeit zu Zeit neu zu erstellen. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (wenn die NmsRecipient-Tabelle verwendet wird) <br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Dies ist die größte Tabelle im System. Pro gesendeter Nachricht wird ein Datensatz verwendet. Diese Datensätze werden eingefügt, aktualisiert, um den Versandstatus zu verfolgen, und gelöscht, wenn der Verlauf bereinigt wird. Beachten Sie, dass diese Tabelle in Version 5.10 kleiner ist als die Entsprechung in Version 4.05 (NmsBroadLog), da der SMTP-Nachrichtentext in der NmsBroadLogMsg-Tabelle in Version 5.10 berücksichtigt wird. Es ist jedoch weiterhin wichtig, diese Tabelle regelmäßig neu zu indizieren (zunächst jede zweite Woche) und sie von Zeit zu Zeit (einmal monatlich oder bei Leistungseinbußen) vollständig neu zu erstellen. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (wenn eine externe Empfängertabelle verwendet wird)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Wie NmsBroadLogRcp, jedoch mit einer externen Empfängertabelle. Bitte passen Sie JJJJ und XXX an die Werte in Ihrem Versand-Mapping an. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (wenn die NmsRecipient-Tabelle verwendet wird) <br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Trackinglogs werden eingefügt und gelöscht, wenn der Verlauf bereinigt wird. Sie werden jedoch nicht aktualisiert. Das Volumen hängt von der Länge der Datenaufbewahrung ab. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxxx (wenn die externe Empfängertabelle verwendet wird)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Wie NmsTrackingLogRcp, jedoch mit einer externen Empfängertabelle. Bitte passen Sie JJJJ und XXX an die Werte an, die in Ihrem Versand-Mapping verwendet werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Ähnlich wie bei den anderen Broadlog-Tabellen, aber mit NmsRtEvent anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent(Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Ähnelt den anderen trackingLog-Tabellen, jedoch mit der NmsRtEvent-Tabelle anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Tabelle, die die Message-Center-Ereigniswarteschlange enthält. Der Status dieser Ereignisse wird von Message Center während der Verarbeitung aktualisiert. Während der Bereinigung werden Löschvorgänge durchgeführt. Wir empfehlen Ihnen, den Index dieser Tabelle regelmäßig neu zu erstellen und neu zu erstellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (Message Center-Kontrollinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Ähnlich wie NmsRtEvent. Diese Tabelle archiviert jedes Ereignis aus allen Ausführungsinstanzen. Es wird von keinem Echtzeit-Prozess, sondern nur von Berichten verwendet.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Sehr klein<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Tabellen, die Mobile Apps und deren Konfiguration enthalten.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren<br /> </td> 
   <td> Tabelle, die die Kennungen der Mobilgeräte (Adressen) enthält, die zum Senden der Benachrichtigung verwendet werden (ähnlich einer Empfängertabelle).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen, Löschungen<br /> </td> 
   <td> Ähnlich wie bei den anderen Broadlog-Tabellen, aber mit NmsappSubscriptionRcp anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Löschungen<br /> </td> 
   <td> Ähnlich wie bei den anderen trackingLog-Tabellen, aber mit der NmsappSubscriptionRcp-Tabelle anstelle von NmsRecipient.<br /> </td> 
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

Zusätzlich zu der obigen Liste können Tabellen, die von Kunden während der Plattformeinrichtung erstellte (nicht im Adobe Campaign-Datenmodell vorhandene) Tabellen enthalten, auch der Fragmentierung unterliegen, insbesondere wenn sie während des Ladens oder Synchronisierens von Daten häufig aktualisiert werden. Diese Tabellen können Teil des standardmäßigen Adobe Campaign-Datenmodells sein (z. B. **NmsRecipient**). In diesem Fall ist es Aufgabe des Administrators der Adobe Campaign-Plattform, eine Prüfung seines spezifischen Datenbankmodells durchzuführen, um diese benutzerdefinierten Tabellen zu finden. Diese Tabellen werden in unseren Wartungsverfahren nicht unbedingt explizit erwähnt.
