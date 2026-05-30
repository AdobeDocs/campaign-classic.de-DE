---
product: campaign
title: Navigationsbaum in Campaign Explorer bearbeiten
description: Navigationsbaum in Campaign Explorer bearbeiten
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
TQID: https://experienceleague.adobe.com/k8LhZvPSYchAxnQew5eknkDbxHDznzPefl032auuYLc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 135
ht-degree: 0%

---

# Navigationsbaum in Campaign Explorer bearbeiten{#edition}

Der Bildschirm zum Erstellen und Konfigurieren der Konfigurationsdokumente für die Navigationshierarchie ist über den Knoten **[!UICONTROL Administration > Konfiguration > Navigationshierarchien]** zugänglich:

![](assets/d_ncs_integration_navigation_arbo.png)

Die Konfiguration der Navigationshierarchie ist auf mehrere XML-Dokumente aufgeteilt. Es funktioniert nach einem ähnlichen Prinzip wie die Schemaerweiterung: Alle Dokumente werden zusammengeführt, um ein einziges Dokument zu erzeugen, das die gesamte Konfiguration enthält. Dieses Dokument kann nicht bearbeitet werden und wird über die Registerkarte „Vorschau“ angezeigt.

Das Bearbeitungsfeld stellt den Inhalt des XML-Dokuments bereit:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Mit dem Bearbeitungssteuerelement „Name“ können Sie den Dokumentschlüssel eingeben, der aus dem Namen und dem Namespace besteht. Die Attribute „name“ und „namespace“ des **`<navtree>`** werden automatisch im XML-Bearbeitungsfeld des Schemas aktualisiert.

Die Vorschau generiert automatisch das zusammengeführte Dokument, das die vollständige Konfiguration enthält:

![](assets/d_ncs_integration_navigation_preview.png)
