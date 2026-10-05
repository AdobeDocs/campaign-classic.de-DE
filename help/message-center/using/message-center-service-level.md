---
product: campaign
title: Message Center-Dienstqualität
description: Weitere Informationen über den Bericht „Message Center-Dienstqualität“
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
TQID: 'https://experienceleague.adobe.com/v9s-xydUk-4cNxNYSAj1HLCOOscZhpQDP-bSJt9mUzg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 100%
---
# Message Center-Dienstqualität {#message-center-service-level}



Dieser Bericht zeigt die Versandstatistiken im Zusammenhang mit Transaktionsnachrichten sowie die Fehleraufschlüsselung an. Sie können auf einen Fehlertyp klicken, um dessen Details anzuzeigen.

Auf diesen Bericht, der sich an technische Administratoren richtet, kann auch über den Tab **[!UICONTROL Monitoring]** der Kontrollinstanz zugegriffen werden.

![](assets/mc_reports_1.png)

In diesem Bericht können Sie entweder die Gesamtstatistik oder die Statistiken einer bestimmten Ausführungsinstanz anzeigen. Sie können die Daten auch nach Kanal und nach einem bestimmten Zeitraum filtern.

Die im Bereich **[!UICONTROL Kennzahlen über den Zeitraum]** angezeigten Indikatoren werden für den ausgewählten Zeitraum berechnet:

* **[!UICONTROL Eingehend (Ereignis/Std.)]**: Durchschnittliche Anzahl der pro Stunde neu in die Message-Center-Warteschlange eingereihten Ereignisse.
* **[!UICONTROL Eingehend (Ereignisanz.)]**: Anzahl der neuen Ereignisse in der Warteschlange.
* **[!UICONTROL Ausgehend (Durchsatz/Std.)]**: Durschnittliche Anzahl der pro Stunde erfolgreich aus Message Center entlassenen Ereignisse (über einen Versand).
* **[!UICONTROL Ausgehend (Nachrichtenanz.)]**: Anzahl der erfolgreich aus Message Center entlassenen Nachrichten (über einen Versand).
* **[!UICONTROL Durchschnittliche Sendungsdauer (Sekunden)]**: Durchschnittliche Dauer, die erfolgreich verarbeitete Ereignisse in Message Center verbringen. Die Berechnung berücksichtigt die Verarbeitungszeit und MTA-Versanddauer.
* **[!UICONTROL Fehlerrate]** : Anzahl der Ereignisse mit Fehlern im Vergleich zur Anzahl der Ereignisse, die in die Warteschlange von Message Center eingereiht wurden. Folgende Fehler werden berücksichtigt: Routing-Fehler, abgelaufene Ereignisse (Ereignis verbleibt zu lange in der Warteschlange), Versandfehler, vom Versand ignorierte Ereignisse (Quarantäne usw.).

>[!NOTE]
>
>Die Hinweis- und Warnschwellen (orange bzw. rot) der Kennzahlen können im Bereitstellungassistenten konfiguriert werden. Siehe [Überwachungsschwellen](../../message-center/using/additional-configurations.md#monitoring-thresholds).
