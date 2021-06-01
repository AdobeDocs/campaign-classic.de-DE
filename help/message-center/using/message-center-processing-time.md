---
solution: Campaign Classic
product: campaign
title: Message Center-Verarbeitungsdauer
description: Erfahren Sie mehr über den Verarbeitungszeitbericht für Message Center.
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 67%

---

# Verarbeitungsdauer {#message-center-processing-time}

Dieser Bericht zeigt die wichtigsten Indikatoren für die Echtzeit-Warteschlange an.

Der für technische Administratoren bestimmte Bericht ist auch über den Tab **[!UICONTROL Monitoring]** der Kontrollinstanz zugänglich.

![](assets/mc_reports_2.png)

Genau wie im Bericht **[!UICONTROL Message Center Dienstebene]** können Sie die Gesamtstatistik oder die Statistiken, die sich auf eine bestimmte Ausführungsinstanz beziehen, anzeigen. Sie können die Daten auch nach Kanal und einem bestimmten Zeitraum filtern.

Die im Abschnitt **[!UICONTROL Indikatoren über den Zeitraum]** angezeigten Indikatoren werden über den ausgewählten Zeitraum berechnet:

* **[!UICONTROL Durchschnittliche Verweildauer in der Warteschlange (s)]**: Durchschnittliche Dauer, die erfolgreich verarbeitete Ereignisse in Message Center verbringen. Es wird nur die Verarbeitungsdauer berücksichtigt.
* **[!UICONTROL Durchschnittliche Sendungsdauer (s)]**: Durchschnittliche Dauer, die erfolgreich verarbeitete Ereignisse in Message Center verbringen. Es wird nur die Dauer des Versands durch die MTAs berücksichtigt.
* **[!UICONTROL Durchschnittliche Verarbeitungsdauer (s)]**: Durchschnittliche Dauer, die erfolgreich verarbeitete Ereignisse in Message Center verbringen. Die Berechnung berücksichtigt die Verarbeitungs- und MTA-Versanddauer.
* **[!UICONTROL Maximale Anzahl an Ereignissen in der Warteschlange]**: Maximale Anzahl der zum gleichen Zeitpunkt in der Message-Center-Warteschlange vorhandenen Ereignisse.
* **[!UICONTROL Minimale Anzahl an Ereignissen in der Warteschlange]**: Minimale Anzahl der zum gleichen Zeitpunkt in der Message-Center-Warteschlange vorhandenen Ereignisse.
* **[!UICONTROL Durchschnittliche Anzahl an Ereignissen in der Warteschlange]**: Durchschnittliche Anzahl der zum gleichen Zeitpunkt in der Message-Center-Warteschlange vorhandenen Ereignisse.

>[!NOTE]
>
>Die Hinweis- und Warnschwellen (orange bzw. rot) der Kennzahlen können im Software-Verteilungs-Assistenten von Adobe Campaign konfiguriert werden. Siehe [Überwachungsschwellen](../../message-center/using/additional-configurations.md#monitoring-thresholds).
