---
product: campaign
title: Erste Schritte mit Federated Data Access
description: Erfahren Sie, wie Sie Daten in einer externen Datenbank aufrufen und verarbeiten können
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: 'https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '164'
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

