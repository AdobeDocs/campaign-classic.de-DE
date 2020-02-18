---
title: Webverfolgungsmodus
seo-title: Webverfolgungsmodus
description: Webverfolgungsmodus
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Webverfolgungsmodus{#web-tracking-mode}

Mit Adobe Campaign können Sie einen Web-Tracking-Modus auswählen, der die Verarbeitung von Verfolgungsprotokollen in der Anwendung definiert.

Es gibt drei verfügbare Web-Verfolgungsmodi: **&quot;Sitzungsverfolgung&quot;**,**&quot;Dauerhafte Verfolgung&quot;** und **&quot;Anonyme Verfolgung&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Jeder Modus hat bestimmte Eigenschaften. Der &quot;permanente&quot;Web-Tracking-Modus beinhaltet die Eigenschaften des &quot;Session&quot;-Web-Tracking-Modus, während der &quot;anonyme&quot; Modus die Eigenschaften der &quot;permanent&quot;- und &quot;session&quot;-Modus enthält.

>[!IMPORTANT]
>
>Der &quot;anonyme&quot;Webverfolgungsmodus ist standardmäßig aktiviert, wenn das Paket &quot;Interessenten&quot;aktiviert ist. In allen anderen Fällen ist der Web-Tracking-Modus &quot;Sitzung&quot;standardmäßig aktiviert.
>
>Der Standardmodus kann jederzeit im Instanzbereitstellungsassistenten geändert werden.

Beachten Sie, dass Sie bei Verwendung des **permanenten Web** - oder **anonymen** Verfolgungsmodus der Spalte &quot;sourceID&quot;(uuid230) in den Verfolgungstabellen (trackingLogXXX) einen Index hinzufügen müssen:

1. Identifizieren Sie die Verfolgungstabelle(n), die von der permanenten Verfolgung betroffen sind.
1. Erweitern Sie die Schemata, die diesen Tabellen entsprechen, um die folgenden Zeilen hinzuzufügen:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Die Modi für die dauerhafte** und **anonyme** Web-Verfolgung umfassen zwei Optionen: Erzwungene **Auslieferung** und **letzte Auslieferung**.

Mit der Option &quot; **Erzwungene Auslieferung** &quot;können Sie die ID der Auslieferung (@jobid) während der Verfolgung angeben.

Mit der Option &quot; **Letzte Bereitstellung** &quot;können Sie das aktuelle Verfolgungsprotokoll mit der zuletzt verfolgten Bereitstellung verknüpfen.

**Merkmale der Sitzungs-Web-Verfolgung:**

Dieser Modus erstellt ein Verfolgungsprotokoll für Personen mit einem Sitzungs-Cookie. Dies sind Personen, die in einer E-Mail, die von Adobe Campaign gesendet wurde, auf eine URL geklickt haben, sodass wir die folgenden Informationen verfolgen können:

* Versandkennung
* Kontakt-ID
* Auslieferungsprotokoll
* ständiges Cookie (uuid230)
* Tracking-URL
* Datum des Verfolgungsprotokolls

Bei diesem Web-Tracking-Modus wird kein Verfolgungsprotokoll in der Anwendung erstellt, wenn ein Teil der Informationen fehlt.

Dieser Modus ist sowohl hinsichtlich der Lautstärke (begrenzte Anzahl von Datensätzen in der Tabelle trackingLog) als auch der Berechnung (kein Abgleich) wirtschaftlich.

**Merkmale des permanenten Web-Tracking-Modus:**

Mit diesem Web-Tracking-Modus können Sie ein Verfolgungsprotokoll erstellen, das auf dem Vorhandensein des permanenten uuid230-Cookies basiert. Wenn ein Besucher seine Sitzung schließt, verwendet Adobe Campaign das permanente Cookie, um Informationen zu ihnen aus vorherigen Verfolgungsprotokollen wiederherzustellen. Adobe Campaign fügt ein Verfolgungsprotokoll erneut ein, wenn uuid230 der aktuellen Sitzung denselben Wert wie uuid230 hat, der bereits in der Verfolgungstabelle gespeichert ist.

Das bedeutet, dass der Besucher zuvor in Adobe Campaign identifiziert werden muss (über eine Bereitstellung), um eine Absöhnung bei uuid230-Werten zu ermöglichen.

Standardmäßig werden Suchvorgänge in vorherigen Verfolgungsprotokollen in der Tabelle &quot;trackingLog&quot;durchgeführt. Wenn das Leads-Paket aktiviert ist, sucht Adobe Campaign vor dem Durchsuchen der Tabelle &quot;trackingLog&quot; nach vorherigen Trackingprotokolldatensätzen in der Tabelle &quot;eingehendesLead&quot;.

Dieser Modus ist im Hinblick auf die Berechnung während der Protokollabstimmung teuer.

**Eigenschaften des anonymen Web-Tracking-Modus:**

Mit diesem Web-Tracking-Modus können Sie ein Verfolgungsprotokoll abrufen, das mit dem anonymen Browsen in Adobe Campaign verknüpft ist. Für jeden Klick auf eine verfolgte URL wird automatisch ein Verfolgungsprotokoll erstellt. Dieses Protokoll hat nur den Wert von uuid230. Während einer Marketingkampagne wird automatisch ein Verfolgungsprotokoll mit allen Identifizierungsinformationen erstellt (siehe Sitzungsverfolgung). Adobe Campaign sucht automatisch nach vorherigen Protokollen nach einem &quot;uuid230&quot;-Wert, der dem Wert aus dem Verfolgungsprotokoll für diese Marketing-Kampagne entspricht. Wenn identische Werte gefunden werden, werden alle vorherigen Verfolgungsprotokolle mit allen Informationen aus dem Marketingkampagnen-Verfolgungsprotokoll eingegeben.

Dieser Modus ist hinsichtlich Berechnung und Volumen am teuersten.

>[!NOTE]
>
>Wenn das **[!UICONTROL Leads]** Paket installiert ist, müssen Sie dasselbe für die Aktivitätstabelle tun (**crm:eingehendesLead**)

Das folgende Schema fasst die Funktionen aller drei Web-Verfolgungsmodi zusammen:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Beispiel für eine permanente Webverfolgung basierend auf der letzten Bereitstellung:**

Florenz erhält eine Lieferung, öffnet die E-Mail, klickt auf den Link, surft auf der Retail-Site, aber macht keine Käufe. Am nächsten Tag kehrt Florenz zur Retail-Site zurück, sucht und kauft ein. Da die permanente Webverfolgung (letzte Auslieferung) aktiviert ist, werden alle Protokolle für ihren zweiten Besuch mit der Auslieferung verknüpft, die ihr am Vortag gesendet wurde.
