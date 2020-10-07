---
title: Webtracking-Modus
seo-title: Webtracking-Modus
description: Webtracking-Modus
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---


# Webtracking-Modus{#web-tracking-mode}

Mit Adobe Campaign können Sie einen Web-Verfolgungsmodus auswählen, der definiert, wie Trackinglogs in der Anwendung verarbeitet werden.

Es gibt drei verfügbare Webtracking-Modi: **&quot;Sitzungsverfolgung&quot;**,**&quot;Dauerhafte Verfolgung&quot;** und **&quot;Anonym-Tracking&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Jeder Modus hat bestimmte Eigenschaften. Der &quot;permanente&quot; Webtracking-Modus beinhaltet die Eigenschaften des &quot;Session&quot;-Webtracking-Modus, während der &quot;anonyme&quot; Modus die Eigenschaften der &quot;permanent&quot; und &quot;session&quot;-Modus beinhaltet.

>[!IMPORTANT]
>
>Der Webtracking-Modus &quot;anonym&quot;ist standardmäßig aktiviert, wenn das Paket &quot;Interessenten&quot;aktiviert ist. In allen anderen Fällen ist der Webtracking-Modus &quot;session&quot;standardmäßig aktiviert.
>
>Der Standardmodus kann jederzeit im Instanzbereitstellungsassistenten geändert werden.

Beachten Sie, dass Sie bei Verwendung des **permanenten Web** - oder **anonymen** Verfolgungsmodus der Spalte &quot;sourceID&quot;(uuid230) in den Verfolgungstabellen (trackingLogXXX) einen Index hinzufügen müssen:

1. Identifizieren Sie die Verfolgungstabelle(n), die von der permanenten Verfolgung betroffen sind.
1. Erweitern Sie die Schemas, die mit diesen Tabellen übereinstimmen, um die folgenden Zeilen hinzuzufügen:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Die Modi &quot;Dauerhaft** &quot;und &quot; **Anonym** &quot;umfassen zwei Optionen: **Erzwungener Versand** und **letzter Versand**.

Mit der Option &quot; **Erzwungener Versand** &quot;können Sie die Kennung des Versands (@jobid) während der Verfolgung angeben.

Mit der Option &quot; **Letzter Versand** &quot;können Sie das aktuelle Verfolgungsprotokoll mit dem zuletzt verfolgten Versand verknüpfen.

**Merkmale des Webtrackings:**

Dieser Modus erstellt ein Verfolgungsprotokoll für Personen mit einem Sitzungs-Cookie. Dies sind Personen, die in einer per Adobe Campaign gesendeten E-Mail auf eine URL geklickt haben, sodass wir die folgenden Informationen verfolgen können:

* Versandkennung
* Kontakt-ID
* versand-Protokoll
* ständiges Cookie (uuid230)
* Tracking-URL
* Datum des Verfolgungsprotokolls

Bei diesem Webtracking-Modus wird kein Verfolgungsprotokoll in der Anwendung erstellt, wenn ein Teil der Informationen fehlt.

Dieser Modus ist sowohl hinsichtlich der Lautstärke (begrenzte Anzahl von Datensätzen in der Tabelle trackingLog) als auch der Berechnung (kein Abgleich) kostengünstig.

**Merkmale des Dauermodus des Webtrackings:**

In diesem Webtracking-Modus können Sie ein Verfolgungsprotokoll erstellen, das auf dem Vorhandensein des permanenten uuid230-Cookies basiert. Wenn ein Besucher die Sitzung schließt, verwendet Adobe Campaign das permanente Cookie, um Informationen zu ihnen aus vorherigen Trackinglogs wiederherzustellen. Adobe Campaign fügt ein Verfolgungsprotokoll erneut ein, wenn uuid230 der aktuellen Sitzung denselben Wert wie uuid230 hat, der bereits in der Verfolgungstabelle gespeichert ist.

Das bedeutet, dass der Besucher zuvor in Adobe Campaign (über einen Versand) identifiziert werden muss, um eine Absöhnung bei uuid230-Werten zu ermöglichen.

Standardmäßig werden Suchvorgänge in vorherigen Trackinglogs in der Tabelle &quot;trackingLog&quot;durchgeführt. Wenn das Leads-Paket aktiviert ist, sucht Adobe Campaign vor dem Durchsuchen der Tabelle &quot;trackingLog&quot; in der Tabelle &quot;eingehendesLead&quot; nach vorherigen Verfolgungsprotokolldatensätzen.

Dieser Modus ist im Hinblick auf die Berechnung während der Protokollabstimmung teuer.

**Merkmale des anonymen Webtracking-Modus:**

In diesem Webtracking-Modus können Sie ein Verfolgungsprotokoll abrufen, das mit dem anonymen Browsen in Adobe Campaign verknüpft ist. Für jeden Klick auf eine verfolgte URL wird automatisch ein Verfolgungsprotokoll erstellt. Dieses Protokoll hat nur den Wert von uuid230. Während einer Marketing-Kampagne wird automatisch ein Verfolgungsprotokoll mit allen Identifizierungsinformationen erstellt (siehe Sitzungsverfolgung). Adobe Campaign sucht automatisch nach vorherigen Protokollen nach einem &quot;uuid230&quot;-Wert, der dem Wert aus dem Verfolgungsprotokoll für diese Marketing-Kampagne entspricht. Wenn identische Werte gefunden werden, werden alle vorherigen Trackinglogs mit allen Informationen aus dem Marketing-Kampagnen-Verfolgungsprotokoll eingegeben.

Dieser Modus ist hinsichtlich Berechnung und Volumen am teuersten.

>[!NOTE]
>
>Wenn das **[!UICONTROL Interessentenpaket]** installiert ist, müssen Sie dasselbe für die Aktivität tun (**crm:eingehendesLead**)

Im folgenden Schema werden die Funktionalitäten aller drei Webtracking zusammengefasst:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Beispiel für eine dauerhafte Webverfolgung auf der Grundlage des letzten Versands:**

Florenz erhält einen Versand, öffnet die E-Mail, klickt auf den Link, surft auf der Retail-Site, kauft aber nicht. Am nächsten Tag kehrt Florenz zur Retail-Site zurück, sucht und kauft ein. Da die permanente Web-Verfolgung (letzter Versand) aktiviert ist, werden alle Protokolle für ihren zweiten Besuch mit dem Versand verknüpft, der ihr am Vortag gesendet wurde.
