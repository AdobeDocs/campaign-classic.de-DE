---
solution: Campaign Classic
product: campaign
title: Funktionsmatrix für Kampagne vor Ort, Hybrid- und Hosted
description: Lernen Sie die wichtigsten Unterschiede zwischen gehosteten und lokalen Bereitstellungen kennen.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 46%

---


# Funktionsmatrix pro Modell{#capability-matrix-per-model}

Adobe Campaign Classic bietet verschiedene Module und Optionen. Die Verfügbarkeit dieser Module und ihre Verwendung können von der Art der Bereitstellung Ihrer Installation abhängen. In diesem Artikel werden einige Details zu den Hauptunterschieden zwischen vollständig gehosteten Managed Services-Bereitstellungen und lokalen Bereitstellungen erläutert.

Diese Seite zeigt die wichtigsten Unterschiede zwischen gehosteten (Managed Services) und lokalen Bereitstellungen. Spezifische Merkmale für Hybridbereitstellungen hängen von den Elementen ab, die von der Adobe gehostet und in Ihren Räumlichkeiten gehostet werden.

Die verschiedenen Hostingmodelle werden in [in diesem Abschnitt](../../installation/using/hosting-models.md) eingeführt.

## Verfügbarkeit pro Bereitstellungsmodell {#capability-matrix}

| Funktion | gehostet | Hybrid | On-Premise | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Campaign-Server konfigurieren | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../installation/using/the-server-configuration-file.md) |
| E-Mail-BCC | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../installation/using/email-archiving.md) |
| Message Center-Ausführungsinstanz verwalten | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../message-center/using/about-transactional-messaging.md) |
| Verwalten der Mid-Sourcing-Plattform | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../installation/using/mid-sourcing-server.md) |
| Inbox-Rendering über Litmus | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../delivery/using/inbox-rendering.md) |
| Integration mit dem IMS (Adobe ID) | On-Demand | On-Demand | On-Demand | [Mehr dazu](../../integrations/using/about-adobe-id.md) |
| Daten für Dateiübertragungen verschlüsseln/entschlüsseln | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../platform/using/unzip-decrypt.md) |
| Dateien komprimieren/entzippen | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../platform/using/unzip-decrypt.md) |
| Domänennamendelegation | On-Demand | On-Demand | Nicht verfügbar | [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html) |
| SpamAssassin installieren | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../delivery/using/spamassassin.md) |
| Zugriff auf Bereitstellungsberichte | Verfügbar | On-Demand | Verfügbar | [Mehr dazu](../../delivery/using/monitoring-deliverability.md) |
| LDAP-Authentifizierung konfigurieren | Nicht verfügbar | Verfügbar | Verfügbar | [Mehr dazu](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access - FDA{#fda}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern. [Mehr dazu](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Der Zugriff auf eine externe Datenbank über FDA ist nur bei lokalen oder hybriden Installationen möglich, mit Ausnahme des [Snowflake Connector](../../installation/using/configure-fda-snowflake.md).


**Siehe auch**

* [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md)
* [Versionshinweise](../../rn/using/latest-release.md)
* [Campaign Classic-Upgrades](../../rn/using/rn-overview.md)
* [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md)
* [Gold Standard-Versionen](../../rn/using/gold-standard.md)
* [Gold Standard-Programm](https://helpx.adobe.com/de/campaign/kb/gold-standard.html)
