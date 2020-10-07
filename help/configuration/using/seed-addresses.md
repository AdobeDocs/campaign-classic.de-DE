---
title: Testadressen
seo-title: Testadressen
description: Testadressen
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 3%

---


# Testadressen{#seed-addresses}

Wenn es sich bei der Tabelle &quot;Empfänger&quot;um eine benutzerdefinierte Tabelle handelt, sind zusätzliche Konfigurationen erforderlich. Das Schema **[!UICONTROL nms:seedMember]** muss verlängert werden. Zu den Testadressen zur Festlegung der entsprechenden Felder wird eine zusätzliche Registerkarte hinzugefügt, wie nachfolgend gezeigt:

![](assets/s_ncs_user_seedlist_new_tab.png)

Weitere Informationen zur Verwendung von Testadressen finden Sie in [diesem Abschnitt](../../delivery/using/about-seed-addresses.md).

## Implementierung{#implementation}

Das **nms:seedMember** -Schema und das verknüpfte Formular, das sofort einsatzbereit ist, sollen für die Kundenkonfiguration erweitert werden, um alle erforderlichen Felder zu referenzieren. Die Schema-Definition enthält Kommentare zum Konfigurationsmodus.

Definition des erweiterten Schemas der Tabelle &quot;Empfänger&quot;:

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

1. Erstellen Sie eine Erweiterung des **nms:seedMember** -Schemas. Weitere Informationen finden Sie unter [Erweitern eines Schemas](../../configuration/using/extending-a-schema.md).
1. Fügen Sie in dieser neuen Erweiterung ein neues Element im Stammverzeichnis von **[!UICONTROL seedMember]** mit den folgenden Parametern hinzu:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Dieses Element muss die zum Exportieren der Kampagnen erforderlichen Felder enthalten. Diese Felder sollten denselben Namen haben wie die entsprechenden Felder im externen Schema. Wenn das Schema beispielsweise **[!UICONTROL cus:person]** lautet, sollte das Schema **[!UICONTROL nms:seedMember]** wie folgt erweitert werden:

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
   >Die Verlängerung des **nms:seedMember** -Schemas muss den Strukturen einer Kampagne und eines Versands in Adobe Campaign entsprechen.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Während der Erweiterung müssen Sie einen **SQL-Namen (@sqlname)** für das Feld &#39;email&#39; angeben. Der SQL-Name muss sich von der sEmail unterscheiden, die für das Empfänger-Schema reserviert ist.
   >    * Sie müssen die Datenbankstruktur mit dem Schema aktualisieren, das beim Erweitern von **nms:seedMember** erstellt wurde.
   >    * In der Erweiterung **nms:seedMember** muss das Feld mit der E-Mail-Adresse **name=&quot;email&quot;** als Attribut haben. Der SQL-Name muss sich von &#39;sEmail&#39; unterscheiden, das bereits für das Empfänger-Schema verwendet wird. Dieses Attribut muss sofort unter dem **`<element name="custom_cus_person" />`** Element deklariert werden.


1. Ändern Sie das Formular **[!UICONTROL sampleMember]** entsprechend, um eine neue Registerkarte &quot;Interner Empfänger&quot;im Fenster **[!UICONTROL Testadressen]** zu definieren. For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

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

Wenn nicht alle Attribute der Seed-Adresse eingegeben werden, ersetzt Adobe Campaign automatisch die Profil: sie werden während der Personalisierung automatisch mit Daten aus einem vorhandenen Profil eingegeben.
