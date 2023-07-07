---
product: campaign
title: Erste Schritte mit Federated Data Access
description: Erfahren Sie, wie Sie Daten in einer externen Datenbank aufrufen und verarbeiten können
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 47%

---

# Erste Schritte mit Federated Data Access {#about-federated-data-access}



Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

## Voraussetzungen {#operating-principle}

Mit der FDA-Option können Sie Ihr Datenmodell in einer Drittanbieterdatenbank erweitern. Sie erkennt automatisch die Struktur der ausgewählten Tabellen und verwendet Daten aus den SQL-Quellen.

Um diese Funktion nutzen zu können, sind im Folgenden die Voraussetzungen aufgeführt:

* **Konfiguration**: Die Liste kompatibler externer Datenbanken hängt von Ihrer [Hosting-Modell](../../installation/using/hosting-models.md).
* **Externe Datenbankversion**: benötigen Sie eine externe Datenbank, die mit dem FDA-Modul von Adobe Campaign kompatibel ist.

  Die Liste der Datenbanksysteme und kompatiblen Versionen je Hosting-Modell finden Sie in Campaign . [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Berechtigungen**: -Benutzer müssen auch über [erforderliche Berechtigungen](../../installation/using/remote-database-access-rights.md) in Adobe Campaign und in der externen Datenbank.

