---
product: campaign
title: Datenschemata
description: Erste Schritte mit Campaign-Datenschemata
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: d4446035-3988-4d89-b7df-7b8528c2e371
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 67%

---

# Datenschemata{#data-schemas}

## Grundsätze {#principles}

Um Schemata zu bearbeiten, zu erstellen und zu konfigurieren, klicken Sie in der Client-Konsole von Adobe Campaign auf den Knoten **[!UICONTROL Administration > Konfiguration > Datenschemas]**.

>[!NOTE]
>
>Native Schemata können nur von einem Administrator Ihrer Adobe Campaign Classic-Konsole verwaltet werden.

![](assets/d_ncs_integration_schema_navtree.png)

Das Bearbeitungsfeld zeigt den XML-Inhalt des Quellschemas an:

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>Mit dem Bearbeitungssteuerelement &quot;Name&quot; können Sie den Schemaschlüssel, bestehend aus Name und Namespace, eingeben. Die Attribute &quot;Name&quot; und &quot;Namespace&quot; des Stammelements des Schemas werden automatisch im XML-Bearbeitungsbereich des Schemas aktualisiert.

Die Vorschau generiert automatisch das erweiterte Schema:

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>Beim Speichern des Quellschemas wird die Generierung des erweiterten Schemas automatisch gestartet.

Wenn Sie die gesamte Struktur eines Schemas überprüfen müssen, können Sie den Vorschau -Tab verwenden. Wenn das Schema erweitert wurde, können Sie alle seine Erweiterungen visuell darstellen. Ergänzend zeigt die Registerkarte Dokumentation alle Schema-Attribute und -Elemente sowie deren Eigenschaften (SQL-Feld, Typ/Länge, Bezeichnung, Beschreibung) an. Die Registerkarte Dokumentation gilt nur für generierte Schemata. Weitere Informationen hierzu finden Sie im Abschnitt [Regenerieren von Schemata](../../configuration/using/regenerating-schemas.md) Abschnitt.

## Beispiel: Erstellen einer Vertragstabelle {#example--creating-a-contract-table}

Im folgenden Beispiel möchten wir eine neue Tabelle für **Aufträge** im Datenbankmodell der Adobe Campaign-Datenbank. In dieser Tabelle können Sie Vor- und Nachnamen sowie E-Mail-Adressen von Inhabern und Mitinhabern für jeden Vertrag speichern.

Dazu müssen Sie das Schema der Tabelle erstellen und die Datenbankstruktur aktualisieren, um die entsprechende Tabelle zu erstellen. Folgende Schritte sind dazu nötig:

1. Bearbeiten Sie den Knoten **[!UICONTROL Administration > Konfiguration > Datenschemata]** in der Adobe Campaign-Struktur und klicken Sie auf **[!UICONTROL Neu]** .
1. Wählen Sie die **[!UICONTROL Erstellen einer neuen Tabelle im Datenmodell]** und klicken Sie auf **[!UICONTROL Nächste]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. Geben Sie einen Tabellennamen und einen Namespace an.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >Standardmäßig werden von Benutzern erstellte Schemata im Namespace &#39;cus&#39; gespeichert. Weitere Informationen hierzu finden Sie unter [Identifizierung eines Schemas](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. Erstellen Sie den Inhalt der Tabelle. Es wird empfohlen, den Eintragsassistenten zu verwenden, um sicherzustellen, dass keine Einstellungen fehlen. Klicken Sie dazu auf **[!UICONTROL Einfügen]** und wählen Sie die Art der Einstellung, die hinzugefügt werden soll.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. Legen Sie die Einstellungen für die Tabelle mit den Verträgen fest:

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   Fügen Sie den Vertragstyp hinzu und fügen Sie einen Index auf die Vertragsnummer ein.

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. Speichern Sie das Schema, um die Struktur zu erstellen:

   ![](assets/s_ncs_configuration_structure.png)

1. Aktualisieren Sie die Datenbankstruktur, um die Tabelle zu erstellen, mit der das Schema verknüpft werden soll. Weitere Informationen hierzu finden Sie unter [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).
