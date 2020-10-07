---
title: Anonym-Tracking
seo-title: Anonym-Tracking
description: Anonym-Tracking
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 7%

---


# Anonym-Tracking{#anonymous-tracking}

Mit Adobe Campaign können Sie erfasste Webtracking-Informationen mit einem Empfänger verknüpfen, wenn dieser Ihre Site anonym durchsucht. Wenn ein Benutzer die getaggten Seiten Ihrer Website durchsucht, werden diese Browserinformationen erfasst, sodass nach dem Klicken in eine per Adobe Campaign gesendete E-Mail diese automatisch identifiziert und mit den Informationen verknüpft werden.

>[!IMPORTANT]
>
>Das Einrichten eines Anonym-Trackings auf einer Website kann die Erfassung einer erheblichen Anzahl von Trackinglogs auslösen und dadurch den Datenbankvorgang beeinträchtigen. Konfigurieren Sie es mit Vorsicht.\
>Trackinglogs werden bis zum Bereinigen der Verfolgungsdaten in der Datenbank gespeichert. Konfigurieren Sie die Bereinigungshäufigkeit mithilfe des Bereitstellungsassistenten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md#purging-data).

Um das anonyme Webtracking auf Ihrer Instanz zu aktivieren, müssen die folgenden Elemente konfiguriert werden:

* Der Parameter **trackWebVisitors** des **redirect** -Elements der Datei &quot; **serverConf.xml** &quot;des Tracking-Servers muss auf &quot;**true**&quot;gesetzt werden, damit ein permanentes Cookie (**uuid230**) in den Browsern unbekannter Internetbenutzer platziert wird, die die Site besuchen.
* Der **Anonyme Webtracking** -Modus muss im Anzeigebereich &quot;Verfolgungskonfiguration&quot;des Bereitstellungsassistenten ausgewählt werden.

   ![](assets/webtracking_anonymous_set.png)

* Webformulare und Umfragen müssen auf dem Tracking-Server veröffentlicht und ausgeführt werden. Die entsprechende Option muss im Bereitstellungsassistenten ausgewählt werden.

   ![](assets/webtracking_publication_set_for_webapps.png)

