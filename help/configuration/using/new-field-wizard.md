---
product: campaign
title: Assistent für neue Felder
description: Assistent für neue Felder
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 4%

---

# Assistent für neue Felder{#new-field-wizard}


Über einen Assistenten, auf den Sie über **[!UICONTROL Tools > Erweitert > Neue Felder hinzufügen]** zugreifen können, können Sie einer Tabelle in der Datenbank ein oder mehrere Felder hinzufügen.

Durch Validierung des Assistenten wird das Erweiterungsschema der zu erweiternden Tabelle aktualisiert und das SQL-Skript gestartet, um die physische Struktur der Datenbank zu ändern.

Dieser Assistent bietet den Vorteil, dass ein Feld schnell hinzugefügt werden kann, ohne dass die Struktur eines Datenschemas kennengelernt werden muss.

Der Hauptnachteil besteht in der Beschränkung der Daten und der Eigenschaften, die erweitert werden sollen.

Die Bildschirme des Assistenten umfassen die folgenden Schritte:

1. Auf der ersten Seite können Sie den Namen des zu erweiternden Schemas und den Namespace des Erweiterungsschemas eingeben, in dem die Änderungen gespeichert werden:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. Auf der nächsten Seite können Sie die Eigenschaften des Felds eingeben, das hinzugefügt werden soll.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Um die Änderungen zu bestätigen, klicken Sie auf die Schaltfläche **[!UICONTROL Beenden]** .

In unserem Beispiel wird automatisch eine Erweiterungsdatei mit dem Namen &quot;cus:recipient&quot;erstellt und das entsprechende SQL-Skript wird ausgeführt:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Standardmäßig werden die hinzugefügten Felder mit der Eigenschaft **user** deklariert (mit dem Wert &quot;true&quot;). Auf diese Weise können Sie das Feld im Formular des erweiterten Schemas mithilfe eines Steuerelements vom Typ &quot;treeEdit&quot; anzeigen und bearbeiten (siehe Formular).
