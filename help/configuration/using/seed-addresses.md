---
product: campaign
title: Testadressen
description: Testadressen
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 3%

---

# Testadressen{#seed-addresses}

![](../../assets/v7-only.svg)

Wenn es sich bei der Empfängertabelle um eine benutzerdefinierte Tabelle handelt, sind zusätzliche Konfigurationen erforderlich. Das Schema **[!UICONTROL nms:seedMember]** muss erweitert werden. Den Testadressen wird ein zusätzlicher Tab zur Definition der entsprechenden Felder hinzugefügt, wie unten dargestellt:

![](assets/s_ncs_user_seedlist_new_tab.png)

Weiterführende Informationen zur Verwendung von Testadressen finden Sie in [diesem Abschnitt](../../delivery/using/about-seed-addresses.md).

## Implementierung {#implementation}

Das Schema **nms:seedMember** und das verknüpfte Formular, das vorkonfiguriert erscheint, sollen für die Kundenkonfiguration erweitert werden, um alle erforderlichen Felder zu referenzieren. Die Schemadefinition enthält Kommentare zum Konfigurationsmodus.

Definition des erweiterten Empfängerschemas der Empfängertabelle:

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

Gehen Sie wie folgt vor:

1. Erstellen Sie eine Erweiterung des Schemas **nms:seedMember** . Weitere Informationen hierzu finden Sie unter [Erweitern eines Schemas](../../configuration/using/extending-a-schema.md).
1. Fügen Sie in dieser neuen Erweiterung ein neues Element am Stammverzeichnis von **[!UICONTROL seedMember]** mit den folgenden Parametern hinzu:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Dieses Element muss die Felder enthalten, die zum Export der Kampagnen erforderlich sind. Diese Felder sollten denselben Namen haben wie die entsprechenden Felder im externen Schema. Wenn das Schema beispielsweise **[!UICONTROL cus:person]** ist, sollte das Schema **[!UICONTROL nms:seedMember]** wie folgt erweitert werden:

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >Die Erweiterung des Schemas **nms:seedMember** muss den Strukturen einer Kampagne und eines Versands in Adobe Campaign entsprechen.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Während der Erweiterung müssen Sie einen **SQL-Namen (@sqlname)** für das Feld &#39;email&#39; angeben. Der SQL-Name muss sich von der &#39;sEmail&#39; unterscheiden, die für das Empfängerschema reserviert ist.
   >    * Sie müssen die Datenbankstruktur mit dem Schema aktualisieren, das beim Erweitern von **nms:seedMember** erstellt wurde.
   >    * In der Erweiterung **nms:seedMember** muss das Feld, das die E-Mail-Adresse enthält, das Attribut **name=&quot;email&quot;** aufweisen. Der SQL-Name muss sich von &quot;sEmail&quot;unterscheiden, der bereits für das Empfängerschema verwendet wird. Dieses Attribut muss sofort unter dem Element **`<element name="custom_cus_person" />`** deklariert werden.


1. Ändern Sie das Formular **[!UICONTROL seedMember]** entsprechend, um einen neuen Tab &quot;Interner Empfänger&quot;im Fenster **[!UICONTROL Testadressen]** zu definieren. Weitere Informationen hierzu finden Sie unter [Formularstruktur](../../configuration/using/form-structure.md).

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

Wenn nicht alle Attribute der Testadresse eingegeben wurden, ersetzt Adobe Campaign automatisch die Profile: sie werden automatisch während der Personalisierung mit Daten aus einem existierenden Profil eingegeben.
