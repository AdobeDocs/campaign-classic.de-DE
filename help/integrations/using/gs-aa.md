---
product: campaign
title: Arbeiten mit Adobe Campaign und Adobe Analytics
description: Arbeiten mit Adobe Campaign und Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
TQID: https://experienceleague.adobe.com/YuvP0m31wL-WlocUXU3rWovOiwLiA5XrEsnBLlW3nY8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 212
ht-degree: 100%

---

# Arbeiten mit Adobe Campaign und Adobe Analytics {#adobe-analytics-connector-gs}

Der Adobe Analytics-Connector ermöglicht die Interaktion von Adobe Campaign und Adobe Analytics über das Package **[!UICONTROL Web-Analytics-Connectoren]**. Er übermittelt Daten zum Benutzerverhalten im Anschluss an eine Kampagne in Form von Segmenten an Adobe Campaign. Umgekehrt sendet er Indikatoren und Attribute von Kampagnen, die von Adobe Campaign bereitgestellt werden, an Adobe Analytics.

## Leitlinien und Voraussetzungen {#adobe-analytics-connector-guardrails}

Bevor Sie damit beginnen, mit dem Adobe Analytics-Connector von Adobe Campaign zu arbeiten, sollten Sie die folgenden Leitlinien und Voraussetzungen beachten.

* Für diese Integration ist eine Verbindung zu Campaign mit dem Adobe Identity Management System (IMS) erforderlich. [Weitere Informationen](../../integrations/using/about-adobe-id.md).

* Der Adobe Analytics-Connector ist nicht kompatibel mit Transaktionsnachrichten (Message Center).

* Das Add-on „Web Analytics-Connector“ muss über das dedizierte Paket in Ihrer Umgebung installiert werden.

   * Bei Hybrid- und On-Premise-Implementierungen müssen Sie die auf [dieser Seite](adobe-analytics-provisioning.md) beschriebenen Bereitstellungsschritte ausführen.
   * Als Hoster oder Managed Cloud Services-Benutzende kontaktieren Sie Adobe, wenn Sie Campaign mit Adobe Experience Cloud-Services und -Lösungen verbinden möchten.


## Konfiguration und Verwendung {#adobe-analytics-connector-usage}

Um diese Integration zu ermöglichen, müssen Sie Ihr technisches Adobe-Konto erstellen, wie auf [dieser Seite](oauth-technical-account.md) beschrieben.

Weitere Informationen zum Arbeiten mit Adobe Campaign und Adobe Analytics finden Sie in der [Dokumentation zu Adobe Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
