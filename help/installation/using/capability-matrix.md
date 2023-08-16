---
product: campaign
title: Funktionsmatrix für On-Premise-, Hybrid- und gehostete Campaign-Versionen
description: Wichtige Unterschiede zwischen gehosteten und On-Premise-Implementierungen
feature: Installation, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 48%

---

# Funktionsmatrix pro Modell{#capability-matrix-per-model}



Adobe Campaign Classic bietet verschiedene Module und Optionen. Die Verfügbarkeit dieser Module und ihre Verwendung können von der Art der Bereitstellung Ihrer Installation abhängen. In diesem Artikel werden einige Details zu den Hauptunterschieden bei bestimmten Funktionen zwischen vollständig gehosteten (Managed Services) und On-Premise-Bereitstellungen vorgestellt.

Auf dieser Seite werden die Hauptunterschiede zwischen gehosteten (Managed Services) und On-Premise-Implementierungen erläutert. Die Besonderheiten hybrider Bereitstellungen hängen von den Elementen ab, die von Adobe gehostet und in Ihren Räumlichkeiten gehostet werden.

Die verschiedenen Hosting-Modelle werden eingeführt [in diesem Abschnitt](../../installation/using/hosting-models.md).

## Verfügbarkeit pro Bereitstellungsmodell {#capability-matrix}

| Funktion | Gehostet | Hybrid | On-Premise | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Campaign-Server konfigurieren | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../installation/using/the-server-configuration-file.md) |
| E-Mail-BCC | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../installation/using/email-archiving.md) |
| Message Center-Ausführungsinstanz verwalten | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../message-center/using/about-transactional-messaging.md) |
| Verwalten der Mid-Sourcing-Plattform | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../installation/using/mid-sourcing-server.md) |
| Inbox Rendering über Litmus | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../delivery/using/inbox-rendering.md) |
| Integration mit IMS (Adobe ID) | On-Demand | On-Demand | On-Demand | [Weitere Informationen](../../integrations/using/about-adobe-id.md) |
| Verschlüsseln/Entschlüsseln von Daten für Dateiübertragungen | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../platform/using/unzip-decrypt.md) |
| Dateien komprimieren/dekomprimieren | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../platform/using/unzip-decrypt.md) |
| Delegation von Domänennamen | On-Demand | On-Demand | Nicht verfügbar | [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=de) |
| SpamAssassin installieren | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../delivery/using/spamassassin.md) |
| Auf Zustellbarkeitsberichte zugreifen | Verfügbar | On-Demand | Verfügbar | [Weitere Informationen](../../delivery/using/monitoring-deliverability.md) |
| LDAP-Authentifizierung konfigurieren | Nicht verfügbar | Verfügbar | Verfügbar | [Weitere Informationen](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern. [Weitere Informationen](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Kompatible externe Datenbanksysteme hängen von Ihrem Hosting-Modell ab. Weitere Informationen finden Sie unter [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).
>

**Siehe auch**

* [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md)
* [Versionshinweise](../../rn/using/latest-release.md)
* [Campaign Classic-Upgrades](../../rn/using/rn-overview.md)
* [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard]-Versionen](../../rn/using/gold-standard.md)
