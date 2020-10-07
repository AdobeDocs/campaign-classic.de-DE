---
title: Zu pflegende Tabellen
seo-title: Zu pflegende Tabellen
description: Zu pflegende Tabellen
seo-description: null
page-status-flag: never-activated
uuid: 1085e929-65cc-48fa-9c31-0508a14b4704
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 6ec4e566-7116-4d7f-835d-cb0f3c3a6a7a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 1%

---


# Zu pflegende Tabellen{#tables-to-maintain}

Die Liste der zu pflegenden Tabellen hängt von Ihrer Version des Adobe Campaigns, von der Art der Verwendung und von der Datenmodellkonfiguration ab.

Die folgende Liste enthält nur die Tabellen, die am häufigsten fragmentiert werden. Die Auswirkungen sind wie folgt:

* Überbelegung des Festplattenspeicherplatzes, was sich auf den Datenbankzugriff auswirkt,
* -Indizes, die nicht regelmäßig aktualisiert wurden, was die Abfrage verlangsamt.

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
   <td> Pro Versand-Aktion ist ein Datensatz vorhanden. Ein einzelner Datensatz kann mehrere Male aktualisiert werden, um den Fortschritt des Versands widerzuspiegeln, sodass Indizes in dieser Tabelle häufig schnell fragmentiert werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Arbeitstabelle, in die Datensätze während der Vorbereitung des Versands eingefügt werden. Sie werden dann während des Versands aktualisiert und nach Abschluss des Versands gelöscht.<br /> Diese Tabelle neigt dazu, schnell zu fragmentieren, obwohl ihre durchschnittliche Größe ziemlich begrenzt ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Löschen<br /> </td> 
   <td> Diese Tabelle enthält die Informationen, die zum Generieren personalisierter Mirrorseiten erforderlich sind. Es enthält ein Memo-Feld (CLOB), und als solche wird es tendenziell sehr groß sein. Das Volumen ist direkt proportional zur Vorgeschichte der Mirrorseiten aufbewahrt. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Diese Tabelle enthält Statistiken zum Versand. Die Aufzeichnungen werden regelmäßig aktualisiert. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Aktualisierungen, Einfügungen<br /> </td> 
   <td> Diese Tabelle enthält Informationen zu E-Mail-Adressen. Es wird häufig im Rahmen der Quarantäne aktualisiert (Datensätze werden beim ersten Versand-Fehler erstellt, aktualisiert, wenn sich die Zähler ändern und gelöscht, sobald der Versand erfolgreich ist). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Pro Workflow-Instanz ist ein Datensatz vorhanden, sodass nur sehr wenige Datensätze vorhanden sind. Die Tabelle wird jedoch regelmäßig aktualisiert, um Status und Fortschritt widerzuspiegeln.<br /> </td> 
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
   <td> Jede Transition, die in einem Workflow zwischen Aufgaben aktiviert wird, führt zur Erstellung eines Datensatzes in dieser Tabelle. Der Bereinigungsmechanismus löscht sie, sobald sie abgelaufen sind. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Sehr klein <br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Diese Tabelle ist spezifisch für das Workflow-Engine. Es ermöglicht das Senden von Befehlen an Workflows (z. B. Beginn, Stopp, Pause). Obwohl es klein ist, wird diese Tabelle bei der Bereinigung von mit Workflows verknüpften Transaktionstabellen berücksichtigt.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Größter<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Das ist der größte Tisch im System. Pro gesendeter Nachricht wird ein Datensatz gesendet. Diese Datensätze werden eingefügt, aktualisiert, um den Status des Versands zu verfolgen, und gelöscht, wenn der Verlauf bereinigt wird. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Löschen<br /> </td> 
   <td> Trackinglogs werden beim Bereinigen des Verlaufs eingefügt und gelöscht, jedoch nicht aktualisiert. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Klein<br /> </td> 
   <td> Aktualisierungen<br /> </td> 
   <td> Diese Tabelle enthält Informationen zum Qualifizieren von SMTP-Fehlern. Es ist relativ klein, wird aber massiv aktualisiert, sodass Indizes auf dieser Tabelle tendenziell schnell fragmentiert werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Mittel<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Diese Tabelle enthält die Aggregat zu SMTP-Fehlern, die nach Domäne sortiert sind. Ursprünglich enthält er detaillierte Informationen, die von der Bereinigungs-Aufgabe aggregiert werden, sobald sie veraltet ist. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (auf einer Mid-Sourcing-Instanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Nur, wenn die Instanz 5.10 (oder höher) als Mid-Sourcing-Instanz verwendet wird. Dies ist eine der größten Tabellen in der Datenbank. Pro gesendeter Nachricht wird ein Datensatz gesendet. Diese Datensätze werden eingefügt, aktualisiert, um den Status des Versands zu verfolgen, und gelöscht, wenn der Verlauf bereinigt wird. Bei der Verwendung von Mid-Sourcing wird empfohlen, den Verlauf zu beschränken (normalerweise weniger als zwei Monate). Diese Tabelle bleibt daher in Bezug auf die Größe angemessen (weniger als 30 Go für 60 Millionen Zeilen, data+index), es ist jedoch sehr wichtig, sie von Zeit zu Zeit neu zu erstellen. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (wenn die NmsRecipient-Tabelle verwendet wird) <br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Das ist der größte Tisch im System. Pro gesendeter Nachricht wird ein Datensatz gesendet. Diese Datensätze werden eingefügt, aktualisiert, um den Status des Versands zu verfolgen, und gelöscht, wenn der Verlauf bereinigt wird. Beachten Sie, dass diese Tabelle in 5.10 kleiner ist als die Entsprechung in 4.05 (NmsBroadLog), da der SMTP-Nachrichtentext in der NmsBroadLogMsg-Tabelle in der Version 5.10 faktorisiert ist. Es ist jedoch nach wie vor unerlässlich, diese Tabelle regelmäßig neu zu indizieren (jede zweite Woche bis zum Beginn) und sie von Zeit zu Zeit (einmal monatlich oder bei Leistungsbeeinträchtigung) vollständig neu zu erstellen. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx (wenn eine externe Empfänger-Tabelle verwendet wird)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Wie NmsBroadLogRcp, aber mit einer externen Empfänger-Tabelle. Bitte passen Sie YYY und XXXX an die Werte in Ihrer Versand-Zuordnung an. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (wenn die NmsRecipient-Tabelle verwendet wird) <br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Löschen<br /> </td> 
   <td> Trackinglogs werden beim Bereinigen des Verlaufs eingefügt und gelöscht, jedoch nicht aktualisiert. Das Volumen hängt von der Länge der Datenspeicherung ab. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx (wenn die externe Empfänger-Tabelle verwendet wird)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Löschen<br /> </td> 
   <td> Wie NmsTrackingLogRcp, aber mit einer externen Empfänger-Tabelle. Bitte passen Sie YYY und XXXX an die Werte an, die in Ihrer Versand-Zuordnung verwendet werden. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Ähnlich wie die anderen Breitlog-Tabellen, aber mit dem NmsRtEvent anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Löschen<br /> </td> 
   <td> Ähnlich wie bei anderen trackingLog-Tabellen, jedoch mit der NmsRtEvent-Tabelle anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (Message Center-Ausführungsinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Tabelle mit der Message Center-Ereignisschlange. Der Status dieser Ereignis wird vom Message Center während der Verarbeitung aktualisiert. Während der Bereinigung werden Löschungen durchgeführt. Wir empfehlen Ihnen, den Index dieser Tabelle regelmäßig neu zu erstellen und neu zu erstellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto (Message Center-Kontrollinstanz)<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Ähnlich wie NmsRtEvent. Diese Tabelle archiviert jedes Ereignis aus allen Ausführungsinstanzen. Es wird nicht in Echtzeit, sondern nur von Berichten verwendet.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Sehr klein<br /> </td> 
   <td> Einfügen, Aktualisieren, Löschen<br /> </td> 
   <td> Tabellen mit mobilen Anwendungen und deren Konfiguration.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Groß<br /> </td> 
   <td> Einfügungen, Aktualisierungen<br /> </td> 
   <td> Tabelle mit den IDs von Mobilgeräten (Adressen), die zum Senden der Benachrichtigung verwendet werden (ähnlich wie bei einer Empfänger-Tabelle).<br /> </td> 
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
   <td> Einfügen, Löschen<br /> </td> 
   <td> Ähnlich wie bei anderen trackingLog-Tabellen, jedoch mit der NmsappSubscriptionRcp-Tabelle anstelle von NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Klein<br /> </td> 
   <td> Einfügen, Löschen<br /> </td> 
   <td> Tabelle mit Benutzersitzungen. Die Anzahl der Einfügungen und Löschungen ist sehr wichtig.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Benutzerdefinierte Tabellen {#customer-tables}

Zusätzlich zu der oben stehenden Liste können Tabellen, die von Kunden erstellt wurden (die nicht im Adobe Campaign-Datenmodell vorhanden sind), während der Plattformeinrichtung auch fragmentiert werden, insbesondere wenn sie während des Ladevorgangs oder der Synchronisierung häufig aktualisiert werden. Diese Tabellen können Teil des Standarddatenmodells des Adobe Campaigns sein (z. B. **NmsRecipient**). In diesem Fall ist es Sache des Administrators der Adobe Campaign-Plattform, eine Prüfung des jeweiligen Datenbankmodells durchzuführen, um diese benutzerdefinierten Tabellen zu finden. Diese Tabellen werden nicht unbedingt explizit in unseren Wartungsverfahren erwähnt.
