---
product: campaign
title: Webtracking-Modus
description: Erfahren Sie, wie Sie den Webtracking-Modus auswählen
feature: Instance Settings
role: Data Engineer, Developer
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 1%

---

# Webtracking-Modus{#web-tracking-mode}



Mit Adobe Campaign können Sie einen Webtracking-Modus auswählen, der definiert, wie Trackinglogs in der Anwendung verarbeitet werden.

Es gibt drei verfügbare Webtracking-Modi: **&quot;Sitzungs-Tracking&quot;**,**&quot;Dauerhaftes Tracking&quot;** und **&quot;Anonymes Tracking&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Jeder Modus weist bestimmte Eigenschaften auf. Der permanente Webtracking-Modus umfasst die Eigenschaften des Webtracking-Modus &quot;Sitzung&quot;, während der Modus &quot;anonym&quot; die Eigenschaften der Modi &quot;dauerhaft&quot; und &quot;Sitzung&quot; enthält.

>[!IMPORTANT]
>
>Der Webtracking-Modus &quot;anonym&quot; ist standardmäßig aktiviert, wenn das Package &quot;Leads&quot; aktiviert ist. In allen anderen Fällen ist der Webtracking-Modus &quot;Sitzung&quot;standardmäßig aktiviert.
>
>Der Standardmodus kann jederzeit im Instanzbereitstellungsassistenten geändert werden.

Beachten Sie, dass bei Verwendung des Tracking-Modus **permanenter Web** oder **anonymous** der Spalte &quot;sourceID&quot;(uuid230) in den Tracking-Tabellen (trackingLogXXX) ein Index hinzugefügt werden muss:

1. Identifizieren Sie die vom permanenten Tracking betroffenen Tracking-Tabellen.
1. Erweitern Sie die Schemata, die diesen Tabellen entsprechen, indem Sie die folgenden Zeilen hinzufügen:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

Die Webtracking-Modi **Dauerhaft** und **Anonym** enthalten zwei Optionen: **Erzwungener Versand** und **Letzter Versand**.

Mit der Option **Erzwungener Versand** können Sie die Versandkennung (@jobid) während des Trackings angeben.

Mit der Option **Letzter Versand** können Sie das aktuelle Trackinglog mit dem letzten verfolgten Versand verknüpfen.

**Eigenschaften des Sitzungs-Webtrackings:**

Dieser Modus erstellt ein Trackinglog für Personen mit einem Sitzungs-Cookie. Hierbei handelt es sich um Personen, die in einer von Adobe Campaign gesendeten E-Mail auf eine URL geklickt haben, sodass wir die folgenden Informationen verfolgen können:

* Versandkennung
* Kontakt-ID
* Versandlog
* permanentes Cookie (uuid230)
* Tracking-URL
* Datum des Trackinglogs

Mit diesem Webtracking-Modus wird in der Anwendung kein Trackinglog erstellt, wenn ein Teil der Informationen fehlt.

Dieser Modus ist kostengünstig in Bezug auf das Volumen (begrenzte Anzahl von Datensätzen in der Tabelle trackingLog) und die Berechnung (keine Abstimmung).

**Eigenschaften des permanenten Webtracking-Modus:**

Mit diesem Webtracking-Modus können Sie ein Trackinglog erstellen, das auf dem permanenten Cookie uuid230 basiert. Wenn ein Besucher seine Sitzung schließt, verwendet Adobe Campaign das permanente Cookie, um Informationen zu ihm aus vorherigen Trackinglogs abzurufen. Adobe Campaign fügt ein Trackinglog erneut ein, wenn die uuid230 der aktuellen Sitzung denselben Wert wie eine uuid230 aufweist, die bereits in der Tracking-Tabelle gespeichert ist.

Das bedeutet, dass der Besucher zuvor in Adobe Campaign (über einen Versand) identifiziert werden muss, um eine Abstimmung der uuid230-Werte zu ermöglichen.

Standardmäßig werden Suchvorgänge in vorherigen Trackinglogs in der Tabelle &quot;trackingLog&quot;durchgeführt. Wenn das Leads-Paket aktiviert ist, sucht Adobe Campaign vor der Suche in der Tabelle &quot;trackingLog&quot; in der Tabelle &quot;incomingLead&quot;nach vorherigen Trackinglog-Datensätzen.

Dieser Modus ist bei der Berechnung während der Protokollabstimmung kostspielig.

**Eigenschaften des anonymen Web-Tracking-Modus:**

Mit diesem Webtracking-Modus können Sie ein Trackinglog abrufen, das mit dem anonymen Browsen in Adobe Campaign verknüpft ist. Für jeden Klick auf eine getrackte URL wird automatisch ein Trackinglog erstellt. Dieses Protokoll hat nur den Wert von uuid230. Während einer Marketing-Kampagne wird automatisch ein Trackinglog mit allen Identifizierungsinformationen erstellt (siehe Sitzungs-Tracking). Adobe Campaign sucht in den vorherigen Logs automatisch nach einem &quot;uuid230&quot;-Wert, der dem Wert aus dem Trackinglog für diese Marketing-Kampagne entspricht. Wenn identische Werte gefunden werden, werden alle vorherigen Trackinglogs mit allen Informationen aus dem Trackinglog der Marketing-Kampagne eingegeben.

Dieser Modus ist in Bezug auf Berechnung und Volumen am teuersten.

>[!NOTE]
>
>Wenn das Paket **[!UICONTROL Leads]** installiert ist, müssen Sie dasselbe für die Aktivitätstabelle tun (**crm:incomingLead**).

Das folgende Schema fasst die Funktionen aller drei Webtracking-Modi zusammen:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Beispiel für permanentes Webtracking basierend auf dem letzten Versand:**

Florenz erhält einen Versand, öffnet die E-Mail, klickt auf den Link, durchsucht die Retail-Website, tätigt aber keine Käufe. Am nächsten Tag kehrt Florenz zur Retail-Website zurück, durchsucht sie und tätigt einen Kauf. Da permanentes Webtracking (letzter Versand) aktiviert ist, werden alle Protokolle für ihren zweiten Besuch mit dem Versand verknüpft, der ihr am Vortag gesendet wurde.
