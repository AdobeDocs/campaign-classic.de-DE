---
solution: Campaign Classic
product: campaign
title: Verarbeitungsdauer
description: Verarbeitungsdauer
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '248'
ht-degree: 100%

---

# Verarbeitungsdauer{#message-center-processing-time}

Dieser Bericht zeigt die wichtigsten Indikatoren für die Echtzeit-Warteschlange an. Auf diesen Bericht, der sich an technische Administratoren richtet, kann auch über den Tab **[!UICONTROL Monitoring]** in der Kontrollinstanz zugegriffen werden.

![](assets/mc_reports_2.png)

Wie auch im Bericht **[!UICONTROL Message Center Dienstqualität]** können entweder allgemeine oder auf eine bestimmte Ausführungsinstanz bezogene Statistiken angezeigt werden. Die im Bereich **[!UICONTROL Kennzahlen über die Periode]** angezeigten Kennzahlen werden entsprechend dem gewählten Zeitraum gefiltert:

* **[!UICONTROL Durchschnittliche Verweildauer in der Warteschlange (s)]**: Durchschnittliche Dauer, die erfolgreich verarbeitete Ereignisse in Message Center verbringen. Es wird nur die Verarbeitungsdauer berücksichtigt.
* **[!UICONTROL Durchschnittliche Sendungsdauer (s)]**: Durchschnittliche Dauer, die erfolgreich verarbeitete Ereignisse in Message Center verbringen. Es wird nur die Dauer des Versands durch die MTAs berücksichtigt.
* **[!UICONTROL Durchschnittliche Verarbeitungsdauer (s)]**: Durchschnittliche Dauer, die erfolgreich verarbeitete Ereignisse in Message Center verbringen. Die Berechnung berücksichtigt die Verarbeitungs- und MTA-Versanddauer.
* **[!UICONTROL Maximale Anzahl an Ereignissen in der Warteschlange]**: Maximale Anzahl der zum gleichen Zeitpunkt in der Message-Center-Warteschlange vorhandenen Ereignisse.
* **[!UICONTROL Minimale Anzahl an Ereignissen in der Warteschlange]**: Minimale Anzahl der zum gleichen Zeitpunkt in der Message-Center-Warteschlange vorhandenen Ereignisse.
* **[!UICONTROL Durchschnittliche Anzahl an Ereignissen in der Warteschlange]**: Durchschnittliche Anzahl der zum gleichen Zeitpunkt in der Message-Center-Warteschlange vorhandenen Ereignisse.

>[!NOTE]
>
>Die Hinweis- und Warnschwellen (orange bzw. rot) der Kennzahlen können im Software-Verteilungs-Assistenten von Adobe Campaign konfiguriert werden. Siehe [Überwachungsschwellen](../../message-center/using/monitoring-thresholds.md).
