---
product: campaign
title: Zugriff auf externe Datenbanken
description: Erfahren Sie, wie Sie Daten in einer externen Datenbank aufrufen und verarbeiten können
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 50%

---

# Erste Schritte mit Federated Data Access {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

## Voraussetzungen {#operating-principle}

Mit der FDA-Option können Sie Ihr Datenmodell in einer Drittanbieterdatenbank erweitern. Sie erkennt automatisch die Struktur der ausgewählten Tabellen und verwendet Daten aus den SQL-Quellen.

Um diese Funktion nutzen zu können, sind im Folgenden die Voraussetzungen aufgeführt:

* **Konfiguration**: außer zum Snowflake benötigen Sie eine **On-Premise** oder **hybrid** Hostingmodell zum Einrichten von Federated Data Access. [Weitere Informationen](../../installation/using/hosting-models.md)
* **Externe Datenbankversion**: benötigen Sie eine externe Datenbank, die mit dem FDA-Modul von Adobe Campaign kompatibel ist. Die Liste der Datenbanksysteme und kompatiblen Versionen finden Sie in Campaign . [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).
* **Berechtigungen**: -Benutzer müssen auch über [erforderliche Berechtigungen](../../installation/using/remote-database-access-rights.md) in Adobe Campaign und in der externen Datenbank.

