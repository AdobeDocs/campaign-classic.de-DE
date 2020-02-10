---
title: Validierung
seo-title: Validierung
description: Validierung
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# Validierung{#validating}

Globale Konzepte bei der Validierung einer Bereitstellung werden in [diesem Abschnitt](../../delivery/using/steps-validating-the-delivery.md)vorgestellt.

Die Ausgabedatei einer Direktversand wird während der Zustellanalyse generiert. Der Inhalt der Datei hängt von den ausgewählten Ausgabespalten ab (siehe [Extrahierungsdatei](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>Die Analysephase ist im Abschnitt [Analyse der Bereitstellung](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)ausführlich beschrieben.

Bei der Erzeugung der Datei werden keine Empfängerinformationen (z. B. Versandlogs) aktualisiert. Der Vorgang kann daher problemlos unterbrochen werden.

Check the result of the analysis and the content of the output file before clicking **[!UICONTROL Confirm delivery]**. A confirmation message lets you launch the delivery.

Mit der Absendebestätigung wird die Extraktion der Daten in die angegebene Datei gestartet.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

You can then close the wizard and look at the delivery logs via the **[!UICONTROL Delivery]** tab, accessible via the delivery details.

You can configure the delivery logs retrieval mode from the **[!UICONTROL Analysis]** tab of the delivery properties.

Dabei stehen zwei Modi zur Verfügung:

* **[!UICONTROL Messages are considered sent after validation]** (Standardmodus): In diesem Funktionsmodus werden alle Broadlogs aktualisiert, wenn der Operator den Sende bestätigt (ihr Status wird von &#39;Ausstehende Lieferung&#39; auf &#39;Versand&#39; übergeben) und die Auslieferung automatisch auf **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : In diesem Modus können Sie die Erweiterungen über eine externe Datei aktualisieren, die vom Service Provider gesendet wird. In diesem Fall muss ein Arbeitsablauf zur Verarbeitung dieser Informationen verwendet werden, um den Status des Breitbandprotokolls zu aktualisieren.

   >[!NOTE]
   >
   >In this case, the delivery&#39;s status also needs to be changed to **[!UICONTROL Finished]** by the user as soon as the broadlogs are updated.
