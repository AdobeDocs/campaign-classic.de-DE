---
product: campaign
title: Campaign On-Premise-, Hybrid- und Hosted-Funktionsmatrix
description: Die wichtigsten Unterschiede zwischen gehosteten und On-Premise-Bereitstellungen
feature: Installation, Architecture
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
TQID: https://experienceleague.adobe.com/kHWVPyk02eyH47xBzGgik3fq6BSHGKpDXPMrEuVaYM8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 323
ht-degree: 43%

---

# Funktionsmatrix pro Modell{#capability-matrix-per-model}



Adobe Campaign Classic bietet verschiedene Module und Optionen. Die Verfügbarkeit dieser Module und ihre Verwendung können von der Art der Bereitstellung Ihrer Installation abhängen. In diesem Artikel werden einige Details zu den wichtigsten Unterschieden bei bestimmten Funktionen zwischen vollständig gehosteten (Managed Services) und On-Premise-Bereitstellungen erläutert.

Auf dieser Seite werden die Hauptunterschiede zwischen gehosteten (Managed Services) und On-Premise-Bereitstellungen angezeigt. Die Besonderheiten von Hybridbereitstellungen hängen von den Elementen ab, die von Adobe gehostet und in Ihren -Standorten gehostet werden.

Die verschiedenen Hosting-Modelle werden [in diesem Abschnitt) ](../../installation/using/hosting-models.md).

## Verfügbarkeit pro Bereitstellungsmodell {#capability-matrix}

| Funktion | Gehostet | Hybrid | On-Premise | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Campaign-Server konfigurieren | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../installation/using/the-server-configuration-file.md) |
| E-Mail-BCC | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../installation/using/email-archiving.md) |
| Message Center-Ausführungsinstanz verwalten | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../message-center/using/about-transactional-messaging.md) |
| Mid-Sourcing-Plattform verwalten | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../installation/using/mid-sourcing-server.md) |
| Inbox Rendering über Litmus | On-Demand | On-Demand | Verfügbar | [Weitere Informationen](../../delivery/using/inbox-rendering.md) |
| Integrieren mit IMS (Adobe ID) | On-Demand | On-Demand | On-Demand | [Weitere Informationen](../../integrations/using/about-adobe-id.md) |
| Verschlüsseln/Entschlüsseln von Daten für Dateiübertragungen | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../platform/using/unzip-decrypt.md) |
| Komprimieren/Dekomprimieren von Dateien | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../platform/using/unzip-decrypt.md) |
| Delegation von Domain-Namen | On-Demand | On-Demand | Nicht verfügbar | [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=de) |
| Installieren von SpamAssassin | On-Demand | Verfügbar | Verfügbar | [Weitere Informationen](../../delivery/using/spamassassin.md) |
| Zugreifen auf Zustellbarkeitsberichte | Verfügbar | On-Demand | Verfügbar | [Weitere Informationen](../../delivery/using/about-delivery-monitoring.md#deliverability-monitoring) |
| Konfigurieren der LDAP-Authentifizierung | Nicht verfügbar | Verfügbar | Verfügbar | [Weitere Informationen](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern. [Weitere Informationen](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Kompatible externe Datenbanksysteme hängen von Ihrem Hosting-Modell ab. Weitere Informationen finden Sie in [Campaign-Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).
>

**Siehe auch**

* [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md)
* [Versionshinweise](../../rn/using/latest-release.md)
* [Campaign Classic-Upgrades](../../rn/using/rn-overview.md)
* [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md)
* [Versionen [!DNL Gold Standard]](../../rn/using/gold-standard.md)
