---
title: Bearbeitung
seo-title: Bearbeitung
description: Bearbeitung
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 3%

---


# Bearbeitung{#edition}

Auf den Bildschirm zum Erstellen und Konfigurieren der Konfigurationshierarchie-Dokumente kann über den Knoten **[!UICONTROL Administration > Konfiguration > Navigationshierarchien]** zugegriffen werden:

![](assets/d_ncs_integration_navigation_arbo.png)

Die Konfiguration der Navigationshierarchie ist auf mehrere XML-Dokumente aufgeteilt. Sie verfolgt einen ähnlichen Grundsatz wie die Ausweitung des Schemas: alle Dokumente zusammengeführt werden, um ein Dokument zu generieren, das die gesamte Konfiguration enthält. Dieses Dokument kann nicht bearbeitet werden und wird über die Registerkarte &quot;Vorschau&quot;angezeigt.

Das Bearbeitungsfeld enthält den Inhalt des XML-Dokuments:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Mit dem Bearbeitungssteuerelement &quot;Name&quot;können Sie den Dokument-Schlüssel eingeben, der aus Name und Namensraum besteht. Die Attribute &quot;name&quot;und &quot;Namensraum&quot;des **`<navtree>`** Elements werden automatisch im XML-Bearbeitungsfeld des Schemas aktualisiert.

Die Vorschau generiert automatisch das zusammengeführte Dokument mit der vollständigen Konfiguration:

![](assets/d_ncs_integration_navigation_preview.png)

