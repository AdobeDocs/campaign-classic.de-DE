---
solution: Campaign Classic
product: campaign
title: Assistent für neue Felder
description: Assistent für neue Felder
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 4%

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

