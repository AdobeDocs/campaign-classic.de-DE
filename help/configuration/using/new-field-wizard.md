---
title: Assistent für neue Felder
seo-title: Assistent für neue Felder
description: Assistent für neue Felder
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 5%

---


# Assistent für neue Felder{#new-field-wizard}

Mit einem Assistenten, der über **[!UICONTROL Tools > Erweitert > Hinzufügen neuen Felder]** aufgerufen werden kann, können Sie einer Tabelle in der Datenbank ein oder mehrere Felder hinzufügen.

Beim Überprüfen des Assistenten wird das Erweiterungsschema der zu erweiternden Tabelle aktualisiert und das SQL-Skript zum Ändern der Datenbankstruktur gestartet.

Diese Assistenzkraft hat den Vorteil, dass Sie schnell ein Schema hinzufügen können, ohne die Struktur eines Datenfelds kennen zu müssen.

Der Hauptnachteil ist die Beschränkung der Daten und der Eigenschaften, die erweitert werden sollen.

Die Bildschirme des Assistenten enthalten die folgenden Schritte:

1. Auf der ersten Seite können Sie den Namen des zu verlängernden Schemas und den Namensraum des Erweiterungsschemas eingeben, in dem die Änderungen gespeichert werden:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. Auf der nächsten Seite können Sie die Eigenschaften des hinzuzufügenden Felds eingeben.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Um die Änderungen zu bestätigen, klicken Sie auf die Schaltfläche **[!UICONTROL Fertig stellen]** .

In unserem Beispiel wird automatisch eine Erweiterungsdatei mit dem Namen &quot;cus:Empfänger&quot;erstellt und das entsprechende SQL-Skript ausgeführt:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Standardmäßig werden die hinzugefügten Felder mit dem **Benutzer** der Eigenschaft deklariert (mit dem Wert &quot;true&quot;). Auf diese Weise können Sie das Feld im Eingabefeld des erweiterten Schemas mit einem Steuerelement vom Typ &quot;treeEdit&quot;anzeigen und bearbeiten (siehe Eingabedatei).

