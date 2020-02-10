---
title: Verarbeitungsdauer
seo-title: Verarbeitungsdauer
description: Verarbeitungsdauer
seo-description: null
page-status-flag: never-activated
uuid: 06aca2c2-33c0-4839-bee4-fd838c49ce76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: d1f591d2-95e8-4d99-bc60-955c96b532eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Verarbeitungsdauer{#message-center-processing-time}

Dieser Bericht zeigt die wichtigsten Indikatoren für die Echtzeitwarteschlange an. Dieser Bericht, der an technische Administratoren gerichtet ist, kann auch über das **[!UICONTROL Monitoring]** Universum in der Kontrollinstanz aufgerufen werden.

![](assets/mc_reports_2.png)

Genau wie im **[!UICONTROL Message Center service level]** Bericht können Sie die Gesamtstatistik oder die Statistiken im Verhältnis zu einer bestimmten Ausführungsinstanz anzeigen. Sie können die Daten auch nach Kanal und über einen bestimmten Zeitraum filtern. Die im **[!UICONTROL Indicators over the period]** Abschnitt angezeigten Indikatoren werden über den ausgewählten Zeitraum berechnet:

* **[!UICONTROL Average queuing time]** : die durchschnittliche Zeit, mit der im Message Center verbrachte Ereignisse erfolgreich verarbeitet wurden. Nur die Verarbeitungszeit wird berücksichtigt.
* **[!UICONTROL Average message sending time (s)]** : die durchschnittliche Zeit, mit der im Message Center verbrachte Ereignisse erfolgreich verarbeitet wurden. Nur die Datenbereitstellungszeit wird berücksichtigt.
* **[!UICONTROL Average processing time (s)]** : die durchschnittliche Zeit, mit der im Message Center verbrachte Ereignisse erfolgreich verarbeitet wurden. Bei der Berechnung werden die Verarbeitungszeit und die Sendezeit berücksichtigt.
* **[!UICONTROL Maximum number of queued events]** : maximale Anzahl von Ereignissen, die sich zu einem bestimmten Zeitpunkt in der Warteschlange des Nachrichtenzentrums befinden.
* **[!UICONTROL Minimum number of queued events]** : Mindestanzahl von Ereignissen, die zu einem bestimmten Zeitpunkt in der Warteschlange des Nachrichtenzentrums vorhanden sind.
* **[!UICONTROL Average number of queued events]** : durchschnittliche Anzahl von Ereignissen, die zu einem bestimmten Zeitpunkt in der Warteschlange des Nachrichtenzentrums vorhanden sind.

>[!NOTE]
>
>Die Schwellenwerte für Warnung (orange) und Warnung (rot) können im Adobe Campaign-Bereitstellungsassistenten konfiguriert werden. Siehe [Überwachungsschwellenwerte](../../message-center/using/monitoring-thresholds.md).

