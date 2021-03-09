---
solution: Campaign Classic
product: campaign
title: Bearbeitung
description: Bearbeitung
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: d6993725ed4060f2affce98c4a8a5211bda03bdf
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 1%

---


# Kampagne Explorer-Navigationsstruktur bearbeiten{#edition}

Der Bildschirm zum Erstellen und Konfigurieren der Konfigurationshierarchie-Dokumente ist über den Knoten **[!UICONTROL Administration > Konfiguration > Navigationshierarchien]** verfügbar:

![](assets/d_ncs_integration_navigation_arbo.png)

Die Konfiguration der Navigationshierarchie ist auf mehrere XML-Dokumente aufgeteilt. Sie verfolgt einen ähnlichen Grundsatz wie die Ausweitung des Schemas: alle Dokumente zusammengeführt werden, um ein Dokument zu generieren, das die gesamte Konfiguration enthält. Dieses Dokument kann nicht bearbeitet werden und wird über die Registerkarte &quot;Vorschau&quot;angezeigt.

Das Bearbeitungsfeld enthält den Inhalt des XML-Dokuments:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Mit dem Bearbeitungssteuerelement &quot;Name&quot;können Sie den Dokument-Schlüssel eingeben, der aus Name und Namensraum besteht. Die Attribute &quot;name&quot;und &quot;Namensraum&quot;des Elements **`<navtree>`** werden automatisch im XML-Bearbeitungsfeld des Schemas aktualisiert.

Die Vorschau generiert automatisch das zusammengeführte Dokument mit der vollständigen Konfiguration:

![](assets/d_ncs_integration_navigation_preview.png)

