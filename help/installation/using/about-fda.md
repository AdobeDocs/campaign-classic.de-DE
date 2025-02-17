---
product: campaign
title: Erste Schritte mit Federated Data Access
description: Erfahren Sie, wie Sie Daten in einer externen Datenbank aufrufen und verarbeiten können
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 47%

---

# Erste Schritte mit Federated Data Access {#about-federated-data-access}



Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

## Voraussetzungen {#operating-principle}

Mit der FDA-Option können Sie Ihr Datenmodell in einer Drittanbieterdatenbank erweitern. Sie erkennt automatisch die Struktur der ausgewählten Tabellen und verwendet Daten aus den SQL-Quellen.

Um diese Funktion verwenden zu können, müssen folgende Voraussetzungen erfüllt sein:

* **Konfiguration**: Die Liste kompatibler externer Datenbanken hängt von Ihrem [Hosting-Modell](../../installation/using/hosting-models.md) ab.
* **Externe Datenbankversion**: Sie benötigen eine externe Datenbank, die mit dem Adobe Campaign FDA-Modul kompatibel ist.

  Die Liste der Datenbanksysteme und kompatiblen Versionen pro Hosting-Modell wird in der Campaign-Kompatibilitätsmatrix [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **Berechtigungen**: Benutzende müssen auch über die [erforderlichen Berechtigungen](../../installation/using/remote-database-access-rights.md) in Adobe Campaign und in der externen Datenbank verfügen.

