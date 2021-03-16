---
solution: Campaign Classic
product: campaign
title: Über Adobe Experience Cloud Triggers
description: Erste Schritte mit der Implementierung von Adobe Experience Cloud Triggers.
audience: integrations
content-type: reference
translation-type: ht
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: ht
source-wordcount: '228'
ht-degree: 100%

---


# Erste Schritte mit Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] ist eine Integration zwischen Adobe Campaign und Adobe Analytics mithilfe der Pipeline. Die Pipeline ruft Aktionen oder Auslöser der Benutzer von Ihrer Website ab. Ein Beispiel für einen Auslöser ist ein Warenkorbabbruch. Trigger werden in Adobe Campaign verarbeitet, um in nahezu Echtzeit E-Mails zu senden.

>[!CAUTION]
>
>Diese Funktion ist im Lieferumfang des Produkts nicht verfügbar. Die Implementierung erfordert die Einbindung von Adobe Consulting. Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um weitere Informationen zu erhalten

[!DNL Triggers] führen nach der Aktion eines Benutzers in einem kurzen Zeitraum Marketing-Aktionen aus. Die typische Reaktionszeit beträgt weniger als eine Stunde.

Dadurch werden flexiblere Integrationen möglich, da der Konfigurationsaufwand minimal ist und keine Drittanbieter beteiligt sind.
Unterstützt werden auch große Traffic-Volumen, ohne dass die Performance von Marketing-Aktivitäten leidet. Beispielsweise kann die Integration eine Million Auslöser pro Stunde verarbeiten.

## [!DNL Triggers]-Architektur {#triggers-architecture}

Der [!DNL pipelined]-Prozess wird auf dem Adobe Campaign-Marketing-Server kontinuierlich ausgeführt. Er stellt eine Verbindung zur Pipeline her, ruft die Ereignisse ab und verarbeitet sie sofort.

![](assets/triggers_2.png)

Der [!DNL pipelined]-Prozess meldet sich mit einem Authentifizierungsdienst bei Experience Cloud an und sendet einen privaten Schlüssel. Der Authentifizierungsdienst gibt ein Token zurück. Das Token dient beim Abrufen der Ereignisse zum Authentifizieren.

Weitere Informationen zum Thema Authentifizierung finden Sie auf [dieser Seite](../../integrations/using/configuring-adobe-io.md).
