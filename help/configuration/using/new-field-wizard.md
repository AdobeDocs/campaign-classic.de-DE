---
product: campaign
title: Neuer Feldassistent
description: Neuer Feldassistent
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: ec774cc10a69a694b3c2bf5a6f662afd12a1435a
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Neuer Feldassistent{#new-field-wizard}


Ein Assistent, der über **[!UICONTROL Tools > Erweitert > Neue Felder hinzufügen]** aufgerufen werden kann, ermöglicht das Hinzufügen eines oder mehrerer Felder zu einer Tabelle in der Datenbank.

Durch die Validierung des Assistenten wird das Erweiterungsschema der zu erweiternden Tabelle aktualisiert und das SQL-Skript gestartet, um die physische Struktur der Datenbank zu ändern.

Dieser Assistent bietet den Vorteil, dass ein Feld schnell hinzugefügt werden kann, ohne dass die Struktur eines Datenschemas kennengelernt werden muss.

Der Hauptnachteil besteht in der Beschränkung der Daten und der Eigenschaften, die erweitert werden sollen.

Die Assistenten-Bildschirme umfassen die folgenden Schritte:

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
