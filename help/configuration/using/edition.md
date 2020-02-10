---
title: Edition
seo-title: Edition
description: Edition
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Edition{#edition}

Auf den Bildschirm zum Erstellen und Konfigurieren der Konfigurationsdokumente für die Navigationshierarchie kann über den **[!UICONTROL Administration > Configuration > Navigation hierarchies]** Knoten zugegriffen werden:

![](assets/d_ncs_integration_navigation_arbo.png)

Die Konfiguration der Navigationshierarchie ist auf mehrere XML-Dokumente aufgeteilt. Es funktioniert nach einem ähnlichen Prinzip wie Schemaerweiterung: alle Dokumente zusammengeführt werden, um ein einziges Dokument zu erstellen, das die gesamte Konfiguration enthält. Dieses Dokument kann nicht bearbeitet werden und wird über die Registerkarte &quot;Vorschau&quot;angezeigt.

Das Bearbeitungsfeld enthält den Inhalt des XML-Dokuments:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Mit dem Bearbeitungssteuerelement &quot;Name&quot;können Sie den Dokumentschlüssel eingeben, der aus dem Namen und dem Namespace besteht. Die Attribute &quot;name&quot;und &quot;namespace&quot;des **`<navtree>`** Elements werden automatisch im XML-Bearbeitungsfeld des Schemas aktualisiert.

Die Vorschau generiert automatisch das zusammengeführte Dokument mit der vollständigen Konfiguration:

![](assets/d_ncs_integration_navigation_preview.png)

