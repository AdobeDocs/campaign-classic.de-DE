---
product: campaign
title: Funktionsmatrix für On-Premise-, Hybrid- und gehostete Campaign-Versionen
description: Wichtige Unterschiede zwischen gehosteten und On-Premise-Implementierungen
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 45%

---

# Funktionsmatrix pro Modell{#capability-matrix-per-model}

Adobe Campaign Classic bietet verschiedene Module und Optionen. Die Verfügbarkeit dieser Module und ihre Verwendung können von der Art der Bereitstellung Ihrer Installation abhängen. In diesem Artikel werden einige Details zu den Hauptunterschieden bei bestimmten Funktionen zwischen vollständig gehosteten (Managed Services) und On-Premise-Bereitstellungen vorgestellt.

Auf dieser Seite werden die Hauptunterschiede zwischen gehosteten (Managed Services) und On-Premise-Implementierungen erläutert. Die Besonderheiten hybrider Bereitstellungen hängen von den Elementen ab, die von der Adobe gehostet und in Ihren Räumlichkeiten gehostet werden.

Die verschiedenen Hosting-Modelle werden [in diesem Abschnitt](../../installation/using/hosting-models.md) eingeführt.

## Verfügbarkeit pro Bereitstellungsmodell {#capability-matrix}

| Funktion | Gehostet | Hybrid | On-Premise | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Campaign-Server konfigurieren | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../installation/using/the-server-configuration-file.md) |
| E-Mail-BCC | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../installation/using/email-archiving.md) |
| Message Center-Ausführungsinstanz verwalten | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../message-center/using/about-transactional-messaging.md) |
| Verwalten der Mid-Sourcing-Plattform | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../installation/using/mid-sourcing-server.md) |
| Inbox Rendering über Litmus | On-Demand | On-Demand | Verfügbar | [Mehr dazu](../../delivery/using/inbox-rendering.md) |
| Integration mit IMS (Adobe ID) | On-Demand | On-Demand | On-Demand | [Mehr dazu](../../integrations/using/about-adobe-id.md) |
| Verschlüsseln/Entschlüsseln von Daten für Dateiübertragungen | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../platform/using/unzip-decrypt.md) |
| Dateien komprimieren/dekomprimieren | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../platform/using/unzip-decrypt.md) |
| Delegation von Domänennamen | On-Demand | On-Demand | Nicht verfügbar | [Mehr dazu](https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html) |
| SpamAssassin installieren | On-Demand | Verfügbar | Verfügbar | [Mehr dazu](../../delivery/using/spamassassin.md) |
| Auf Zustellbarkeitsberichte zugreifen | Verfügbar | On-Demand | Verfügbar | [Mehr dazu](../../delivery/using/monitoring-deliverability.md) |
| LDAP-Authentifizierung konfigurieren | Nicht verfügbar | Verfügbar | Verfügbar | [Mehr dazu](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern. [Mehr dazu](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Der Zugriff auf eine externe Datenbank über FDA ist nur für On-Premise- oder Hybridinstallationen möglich, mit Ausnahme des [Snowflake-Connectors](../../installation/using/configure-fda-snowflake.md).


**Siehe auch**

* [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md)
* [Versionshinweise](../../rn/using/latest-release.md)
* [Campaign Classic-Upgrades](../../rn/using/rn-overview.md)
* [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard]-Versionen ](../../rn/using/gold-standard.md)
* [[!DNL Gold Standard]-Programm](../../rn/using/gs-overview.md)
