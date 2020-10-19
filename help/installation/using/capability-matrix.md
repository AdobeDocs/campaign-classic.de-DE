---
title: Funktionsmatrix für Kampagne vor Ort, Hybrid- und Hosted
description: Lernen Sie die wichtigsten Unterschiede zwischen gehosteten und lokalen Bereitstellungen kennen.
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 20%

---


# Funktionsmatrix pro Hostmodell {#capability-matrix-per-model}

Adobe Campaign Classic verfügt über eine Reihe von Modulen und Optionen. Die Verfügbarkeit dieser Module und ihre Verwendung können von der Art der Bereitstellung Ihrer Installation abhängen. In diesem Artikel werden einige Details zu den Hauptunterschieden zwischen vollständig gehosteten Managed Services-Bereitstellungen und lokalen Bereitstellungen erläutert.

Diese Seite zeigt die wichtigsten Unterschiede zwischen gehosteten (Managed Services) und lokalen Bereitstellungen. Spezifische Merkmale für Hybridbereitstellungen hängen von den Elementen ab, die von der Adobe gehostet und in Ihren Räumlichkeiten gehostet werden.

Die verschiedenen Hosting-Modelle werden [in diesem Abschnitt](../../installation/using/hosting-models.md)vorgestellt.

## Funktionsmatrix{#capability-matrix}

| Funktion | gehostet | Hybrid | Vor-Ort | Details |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Kampagne-Server konfigurieren | On-Demand | Verfügbar | Verfügbar | Die[Serverkonfigurationsdatei](../../installation/using/the-server-configuration-file.md)kann nur für gehostete Kunden durch Adobe geändert werden. |
| E-Mail-BCC | On-Demand | On-Demand | Verfügbar | Bei gehosteten und hybriden Architekturen wenden Sie sich an Ihren Kundenbetreuer, um E-Mail BCC zu aktivieren. Befolgen Sie bei lokalen Installationen die Richtlinien der Dokumentation. [mehr dazu](../../installation/using/email-archiving.md) |
| Message Center-Ausführungsinstanz verwalten | On-Demand | On-Demand | Verfügbar | Bei gehosteten Bereitstellungen können bestimmte Einstellungen, z. B. das Erstellen von Benutzern auf Ausführungsinstanz, nur von der Adobe ausgeführt werden. [mehr dazu](../../message-center/using/about-transactional-messaging.md) |
| Verwalten der Mid-Sourcing-Plattform | On-Demand | On-Demand | Verfügbar | Mid-Sourcing-Plattformen, die von der Adobe gehostet werden, können nur von der Adobe konfiguriert werden. |
| Inbox-Rendering über Litmus | On-Demand | On-Demand | Verfügbar | Du brauchst ein Litmus-Konto. Sie müssen zur Adobe gehen, um die erforderlichen Details zu erhalten oder die Inbox-Renderingkonfiguration durchzuführen. [mehr dazu](../../delivery/using/inbox-rendering.md) |
| Integration mit dem IMS (Adobe ID) | On-Demand | On-Demand | On-Demand | Die IMS-Bereitstellung erfolgt durch Adobe. Diese Integration ist eine Voraussetzung für Adobe Experience Cloud-Integrationen. [mehr dazu](../../integrations/using/about-adobe-id.md) |
| Daten für Dateiübertragungen verschlüsseln/entschlüsseln | On-Demand | Verfügbar | Verfügbar | Um die Dateivorbereitung oder -nachverarbeitung zu aktivieren, muss das erforderliche Dienstprogramm auf dem Adobe Campaign-Server installiert werden. Gehostete Kunden können die Systemsteuerung der Kampagne verwenden. [mehr dazu](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Dateien komprimieren/entzippen | On-Demand verfügbar | Verfügbar | Um die Dateivorbereitung oder -nachverarbeitung zu aktivieren, muss das erforderliche Dienstprogramm auf dem Adobe Campaign-Server installiert werden. Gehostete Kunden können die Systemsteuerung der Kampagne verwenden. [mehr dazu](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Domänennamendelegation | On-Demand | On-Demand | Nicht verfügbar | [mehr dazu](https://helpx.adobe.com/de/campaign/kb/domain-name-delegation.html) |
| SpamAssassin installieren | On-Demand | Verfügbar | Verfügbar | Für die Installation von SpamAssassin muss die Serverkonfigurationsdatei bearbeitet werden. [mehr dazu](../../delivery/using/spamassassin.md) |
| Zugriff auf Bereitstellungsberichte | Verfügbar | On-Demand | Verfügbar | Bei bestimmten Hybrid-Bereitstellungen kann von der Marketing-Instanz aus nicht auf Bereitstellungsberichte zugegriffen werden. |
| LDAP-Authentifizierung konfigurieren | Nicht verfügbar | Verfügbar | Verfügbar | Die LDAP-Konfiguration ist nur für lokale oder hybride Installationen möglich. [mehr dazu](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access - FDA{#fda}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern. [mehr dazu](../../platform/using/about-fda.md)

>[!CAUTION]
>
>Accessing an external database via FDA is only possible for on-premise or hybrid installations, except with the [Snowflake connector](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**Siehe auch**

* [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md)
* [Versionshinweise](../../rn/using/latest-release.md)
* [Campaign Classic-Upgrades](../../rn/using/rn-overview.md)
* [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md)
* [Gold Standard-Versionen](../../rn/using/gold-standard.md)
* [Gold Standard-Programm](https://helpx.adobe.com/de/campaign/kb/gold-standard.html).
