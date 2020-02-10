---
title: Über die Ereignisverarbeitung
seo-title: Über die Ereignisverarbeitung
description: Über die Ereignisverarbeitung
seo-description: null
page-status-flag: never-activated
uuid: 6c3e02b3-0d4d-4661-952a-e4915ca9ef92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: a78c9986-7c49-47db-99a0-9f0949c4dee7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c2c53041d8a19a491b8ec4da12a8a0ced25cf9a

---


# Über die Ereignisverarbeitung{#about-event-processing}

Im Zusammenhang mit Transaktionsnachrichten wird ein Ereignis von einem externen Informationssystem generiert und über die **[!UICONTROL PushEvent]** und **[!UICONTROL PushEvents]** Methoden an Adobe Campaign gesendet (siehe [Ereignisbeschreibung](../../message-center/using/event-description.md)). Es enthält Daten, die mit dem Ereignis verknüpft sind, wie z. B. den Typ (z. B. Bestellbestätigung oder Kontoerstellung auf einer Website), die E-Mail-Adresse oder die Mobiltelefonnummer sowie weitere Informationen, mit denen Sie die Transaktionsnachricht vor der Lieferung bereichern und personalisieren können. Dies können Kundenkontaktinformationen, die Sprache der Nachricht oder das E-Mail-Format sein.

Beispiel für Ereignisdaten:

![](assets/messagecenter_events_request_001.png)

Die Verarbeitung von Transaktionsnachrichten-Ereignissen findet in folgenden Etappen statt:

1. Ereignisabruf,
1. Anreicherung des Ereignisses, bevor es zu einer Nachrichtenvorlage weitergeleitet wird (nur mit der für das Transaktionsnachrichten-Modul von Campaign verfügbaren Anreicherungsoption möglich),
1. Weiterleitung des Ereignisses zu einer Nachrichtenvorlage,
1. Anreicherung des Ereignisses mit Personalisierungsdaten,
1. Versand der Transaktionsnachrichten,
1. Recycling der Ereignisse, deren zugeordneter Versand fehlgeschlagen ist (mithilfe eines Adobe-Campaign-Workflows möglich).

## Ereignisstatus {#event-statuses}

Der **Ereignisverlauf** gruppiert alle verarbeiteten Ereignisse unter **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** in einer einzigen Ansicht. Sie können nach Ereignistyp oder **Status** kategorisiert werden. Diese Status sind:

* **Ausstehend**:

   * ein Ereignis, das gerade erfasst wurde und noch nicht verarbeitet wurde. Die **[!UICONTROL Number of errors]** Spalte zeigt den Wert 0 an. Die E-Mail-Vorlage wurde noch nicht verknüpft.
   * ein verarbeitetes Ereignis, dessen Bestätigung jedoch fehlerhaft ist. Die **[!UICONTROL Number of errors]** Spalte zeigt einen Wert an, der nicht 0 ist. Wenn Sie wissen möchten, wann dieses Ereignis erneut verarbeitet wird, lesen Sie die **[!UICONTROL Process requested on]** Spalte.

* **Versand ausstehend**: Ereignis, das verarbeitet und dem eine Versandvorlage zugeordnet wurde. Die E-Mail ist versandbereit und der Standard-Versandprozess wird angewendet. Details können direkt im Versand eingesehen werden. Weiterführende Informationen hierzu finden Sie im [Delivery](../../delivery/using/about-message-tracking.md)-Handbuch.
* **Gesendet**, **Ignoriert** und **Versandfehler**: Versandstatus, die vom **updateEventsStatus**-Workflow abgerufen werden. Details können direkt im entsprechenden Versand eingesehen werden.
* **Ereignis wurde nicht berücksichtigt**: Die Message-Center-Routing-Phase ist fehlgeschlagen. Beispielsweise konnte Adobe Campaign die dem Ereignis entsprechende E-Mail-Vorlage nicht finden.
* **Ereignis ist abgelaufen**: Die maximale Anzahl an Versandversuchen wurde erreicht. Das Ereignis wird als nichtig angesehen.
