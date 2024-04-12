---
product: campaign
title: Navigationsstruktur von Campaign Explorer bearbeiten
description: Navigationsstruktur von Campaign Explorer bearbeiten
feature: Application Settings
role: Data Engineer, Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Navigationsstruktur von Campaign Explorer bearbeiten{#edition}

Auf den Bildschirm zum Erstellen und Konfigurieren der Navigationshierarchiekonfigurationsdokumente kann über das **[!UICONTROL Administration > Konfiguration > Navigationshierarchien]** node:

![](assets/d_ncs_integration_navigation_arbo.png)

Die Konfiguration der Navigationshierarchie ist auf mehrere XML-Dokumente aufgeteilt. Es folgt einem ähnlichen Prinzip wie die Schemaerweiterung: Alle Dokumente werden zusammengeführt, um ein einzelnes Dokument zu generieren, das die gesamte Konfiguration enthält. Das Dokument kann nicht bearbeitet werden und wird im Tab &quot;Vorschau&quot; angezeigt.

Das Bearbeitungsfeld stellt den Inhalt des XML-Dokuments bereit:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Das Eingabefeld &quot;Name&quot; ermöglicht die Eingabe des Dokumentschlüssels, der aus Name und Namespace besteht. Die Attribute &quot;name&quot;und &quot;namespace&quot;der **`<navtree>`** -Element automatisch im XML-Bearbeitungsfeld des Schemas aktualisiert.

Die Vorschau generiert automatisch das zusammengeführte Dokument mit der vollständigen Konfiguration:

![](assets/d_ncs_integration_navigation_preview.png)
