---
product: campaign
title: Erste Schritte mit Federated Data Access
description: Erfahren Sie, wie Sie Daten in einer externen Datenbank aufrufen und verarbeiten können
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 164
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

