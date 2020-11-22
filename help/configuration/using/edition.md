---
solution: Campaign Classic
product: campaign
title: Bearbeitung
description: Bearbeitung
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 2%

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

