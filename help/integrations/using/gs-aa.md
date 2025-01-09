---
product: campaign
title: Arbeiten mit Adobe Campaign und Adobe Analytics
description: Arbeiten mit Adobe Campaign und Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: ht
source-wordcount: '200'
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

Weitere Informationen dazu, wie Sie mit Adobe Campaign und Adobe Analytics arbeiten können, finden Sie in der [Dokumentation zu Adobe Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
