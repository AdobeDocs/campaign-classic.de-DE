---
product: campaign
title: Assistent für neue Felder
description: Assistent für neue Felder
feature: Schema Extension
role: Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
TQID: 'https://experienceleague.adobe.com/dr6UMSb0vKU7Fne9uso4IYSJLHSyNqDQHX5V-r-qhcE'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 4%
---
# Assistent für neue Felder{#new-field-wizard}


Mit einem Assistenten, auf den Sie über **[!UICONTROL Tools > Erweitert > Neue Felder hinzufügen]** zugreifen können, können Sie ein oder mehrere Felder zu einer Tabelle in der Datenbank hinzufügen.

Durch die Validierung des Assistenten wird das Erweiterungsschema der zu erweiternden Tabelle aktualisiert und das SQL-Script zur Änderung der physischen Struktur der Datenbank gestartet.

Dieser Assistent bietet den Vorteil, dass ein Feld schnell hinzugefügt werden kann, ohne die Struktur eines Datenschemas kennen zu müssen.

Der Hauptnachteil ist die Beschränkung der Daten und der zu erweiternden Eigenschaften.

Die Assistenten-Bildschirme enthalten die folgenden Schritte:

1. Auf der ersten Seite können Sie den Namen des zu erweiternden Schemas und den Namespace des Erweiterungsschemas eingeben, in dem die Änderungen gespeichert werden:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. Auf der nächsten Seite können Sie die Eigenschaften des hinzuzufügenden Felds eingeben.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Um die Änderungen zu bestätigen, klicken Sie auf die Schaltfläche **[!UICONTROL Beenden]**.

Eine Erweiterungsdatei mit dem Namen „cus:recipient wird in unserem Beispiel automatisch erstellt und das entsprechende SQL-Script wird ausgeführt:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Standardmäßig werden die hinzugefügten Felder mit der Eigenschaft **Benutzer“ deklariert** mit dem Wert „true„). Auf diese Weise können Sie das Feld im Eingabeformular des erweiterten Schemas mithilfe eines Steuerelements vom Typ „treeEdit“ anzeigen und bearbeiten (siehe Eingabeformular).
