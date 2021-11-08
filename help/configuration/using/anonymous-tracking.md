---
product: campaign
title: Anonym-Tracking
description: Anonym-Tracking
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# Anonym-Tracking{#anonymous-tracking}

![](../../assets/v7-only.svg)

Mit Adobe Campaign können Sie die erfassten Web-Tracking-Informationen einem Empfänger zuordnen, wenn dieser Ihre Site anonym besucht. Wenn ein Benutzer die getaggten Seiten Ihrer Website durchsucht, werden diese Informationen erfasst, sodass er, sobald er in eine von Adobe Campaign gesendete E-Mail klickt, identifiziert und die Informationen automatisch mit ihm verknüpft werden.

>[!IMPORTANT]
>
>Durch die Einrichtung eines anonymen Trackings auf einer Website kann die Erfassung einer beträchtlichen Anzahl von Trackinglogs Trigger werden, was sich auf den Datenbankbetrieb auswirkt. Konfigurieren Sie es mit Vorsicht.\
>Trackinglogs werden in der Datenbank gespeichert, bis die Tracking-Daten bereinigt wurden. Konfigurieren Sie mithilfe des Softwareverteilungs-Assistenten die Bereinigungshäufigkeit. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md#purging-data).

Um das anonyme Webtracking in Ihrer Instanz zu aktivieren, müssen die folgenden Elemente konfiguriert werden:

* Die **trackWebVisitors** Parameter der **Umleitung** -Element **serverConf.xml** -Datei des Tracking-Servers auf &quot;**true**&quot;, um ein permanentes Cookie (**uuid230**) in den Browsern unbekannter Internetbenutzer, die die Site besuchen.
* Die **Anonym Web Tracking** muss im Bildschirm zur Tracking-Konfiguration des Softwareverteilungs-Assistenten ausgewählt werden.

   ![](assets/webtracking_anonymous_set.png)

* Webformulare müssen veröffentlicht und auf dem Trackingserver ausgeführt werden. Die entsprechende Option muss im Softwareverteilungs-Assistenten ausgewählt werden.

   ![](assets/webtracking_publication_set_for_webapps.png)
