---
title: Neuer Feldassistent
seo-title: Neuer Feldassistent
description: Neuer Feldassistent
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Neuer Feldassistent{#new-field-wizard}

Mit einem Assistenten, auf den Sie zugreifen können, **[!UICONTROL Tools > Advanced > Add new fields]** können Sie einer Tabelle in der Datenbank ein oder mehrere Felder hinzufügen.

Beim Überprüfen des Assistenten wird das Erweiterungsschema der zu erweiternden Tabelle aktualisiert und das SQL-Skript zum Ändern der physischen Struktur der Datenbank gestartet.

Dieser Assistent hat den Vorteil, dass er schnell ein Feld hinzufügen kann, ohne die Struktur eines Datenschemas kennen zu müssen.

Der Hauptnachteil ist die Beschränkung der Daten und der Eigenschaften, die erweitert werden sollen.

Die Bildschirme des Assistenten enthalten die folgenden Schritte:

1. Auf der ersten Seite können Sie den Namen des zu erweiternden Schemas und den Namespace des Erweiterungsschemas eingeben, in dem die Änderungen gespeichert werden:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. Auf der nächsten Seite können Sie die Eigenschaften des hinzuzufügenden Felds eingeben.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Um die Änderungen zu bestätigen, klicken Sie auf die **[!UICONTROL Finish]** Schaltfläche.

In unserem Beispiel wird automatisch eine Erweiterungsdatei mit der Bezeichnung &quot;cus:empfänger&quot;erstellt und das entsprechende SQL-Skript ausgeführt:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Standardmäßig werden die hinzugefügten Felder mit dem **Benutzer** der Eigenschaft deklariert (mit dem Wert &quot;true&quot;). Auf diese Weise können Sie das Feld im Eingabeformular des erweiterten Schemas mit einem Steuerelement vom Typ &quot;treeEdit&quot;anzeigen und bearbeiten (siehe Eingabedatei).

