---
solution: Campaign Classic
product: campaign
title: Zugriff auf externe Datenbanken
description: Erfahren Sie, wie Sie Daten in einer externen Datenbank aufrufen und verarbeiten können
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 50%

---

# Erste Schritte mit Federated Data Access {#about-federated-data-access}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

## Voraussetzungen {#operating-principle}

Mit der FDA-Option können Sie Ihr Datenmodell in einer Drittanbieterdatenbank erweitern. Sie erkennt automatisch die Struktur der ausgewählten Tabellen und verwendet Daten aus den SQL-Quellen.

Um diese Funktion nutzen zu können, sind die Voraussetzungen unten aufgeführt:

* **Konfiguration**: außer zum Snowflake, benötigen Sie ein  **On-** Premise- oder  **** Hybridhosting-Modell, um Federated Data Access einzurichten. [Mehr dazu](../../installation/using/hosting-models.md)
* **Externe Datenbankversion**: Sie benötigen eine externe Datenbank, die mit dem Adobe Campaign FDA Modul kompatibel ist. Die Liste von Datenbanksystemen und kompatiblen Versionen ist in Kampagne [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA) beschrieben.
* **Berechtigungen**: Die Benutzer müssen auch über die  [erforderlichen ](../../installation/using/remote-database-access-rights.md) Berechtigungen in Adobe Campaign und in der externen Datenbank verfügen.

