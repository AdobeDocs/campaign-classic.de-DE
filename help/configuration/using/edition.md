---
product: campaign
title: Navigationsbaum in Campaign Explorer bearbeiten
description: Navigationsbaum in Campaign Explorer bearbeiten
feature: Application Settings
role: Data Engineer, Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '135'
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
