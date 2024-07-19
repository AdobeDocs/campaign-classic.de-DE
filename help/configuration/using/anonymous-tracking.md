---
product: campaign
title: Anonym-Tracking
description: Erfahren Sie, wie Sie das anonyme Tracking einrichten.
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---

# Anonym-Tracking{#anonymous-tracking}

Mit Adobe Campaign können Sie die erfassten Web-Tracking-Informationen einem Empfänger zuordnen, wenn dieser Ihre Site anonym besucht. Wenn ein Benutzer die getaggten Seiten Ihrer Website durchsucht, werden diese Informationen erfasst, sodass er, sobald er in eine von Adobe Campaign gesendete E-Mail klickt, identifiziert und die Informationen automatisch mit ihm verknüpft werden.

>[!IMPORTANT]
>
>Durch die Einrichtung eines anonymen Trackings auf einer Website kann die Erfassung einer beträchtlichen Anzahl von Trackinglogs Trigger werden, was sich auf den Datenbankbetrieb auswirkt. Konfigurieren Sie es mit Vorsicht.\
>Trackinglogs werden in der Datenbank gespeichert, bis die Tracking-Daten bereinigt wurden. Konfigurieren Sie mithilfe des Softwareverteilungs-Assistenten die Bereinigungshäufigkeit. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md#purging-data).

Um das anonyme Webtracking in Ihrer Instanz zu aktivieren, müssen die folgenden Elemente konfiguriert werden:

* Der Parameter **trackWebVisitors** des Elements **redirection** der Datei **serverConf.xml** des Tracking-Servers muss auf &quot;**true**&quot; gesetzt werden, damit ein permanentes Cookie (**uid230**) in den Browsern unbekannter Internetbenutzer platziert wird, die die Site besuchen.
* Der Modus **Anonymes Web-Tracking** muss im Tracking-Konfigurationsbildschirm des Softwareverteilungs-Assistenten ausgewählt werden.

  ![](assets/webtracking_anonymous_set.png)

* Webformulare müssen veröffentlicht und auf dem Trackingserver ausgeführt werden. Die entsprechende Option muss im Softwareverteilungs-Assistenten ausgewählt werden.

  ![](assets/webtracking_publication_set_for_webapps.png)
