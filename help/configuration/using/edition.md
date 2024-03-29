---
product: campaign
title: Navigationsstruktur von Campaign Explorer bearbeiten
description: Navigationsstruktur von Campaign Explorer bearbeiten
feature: Application Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

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
