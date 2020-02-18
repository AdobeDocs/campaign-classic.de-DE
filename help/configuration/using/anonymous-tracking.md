---
title: Anonyme Verfolgung
seo-title: Anonyme Verfolgung
description: Anonyme Verfolgung
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Anonyme Verfolgung{#anonymous-tracking}

Mit Adobe Campaign können Sie erfasste Web-Verfolgungsinformationen mit einem Empfänger verknüpfen, wenn dieser Ihre Site anonym besucht. Wenn ein Benutzer die getaggten Seiten Ihrer Website durchsucht, werden diese Browserinformationen gesammelt, sodass nach dem Klicken in eine von Adobe Campaign gesendete E-Mail diese identifiziert und automatisch mit den Informationen verknüpft werden.

>[!IMPORTANT]
>
>Das Einrichten einer anonymen Verfolgung auf einer Website kann die Erfassung einer erheblichen Menge von Verfolgungsprotokollen auslösen und dadurch den Datenbankvorgang beeinträchtigen. Konfigurieren Sie es mit Vorsicht.\
>Verfolgungsprotokolle werden bis zum Bereinigen der Verfolgungsdaten in der Datenbank gespeichert. Konfigurieren Sie die Bereinigungshäufigkeit mithilfe des Bereitstellungsassistenten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md#purging-data).

Um die anonyme Web-Verfolgung auf Ihrer Instanz zu aktivieren, müssen die folgenden Elemente konfiguriert werden:

* Der Parameter **trackWebVisitors** des **redirect** -Elements der Datei &quot; **serverConf.xml** &quot;des Tracking-Servers muss auf &quot;**true**&quot;gesetzt werden, damit ein permanentes Cookie (**uuid230**) in den Browsern unbekannter Internetbenutzer platziert wird, die die Site besuchen.
* Der **Anonyme Web-Tracking** -Modus muss im Anzeigebereich &quot;Verfolgungskonfiguration&quot;des Bereitstellungsassistenten ausgewählt werden.

   ![](assets/webtracking_anonymous_set.png)

* Web-Formulare und Umfragen müssen auf dem Tracking-Server veröffentlicht und ausgeführt werden. Die entsprechende Option muss im Bereitstellungsassistenten ausgewählt werden.

   ![](assets/webtracking_publication_set_for_webapps.png)

