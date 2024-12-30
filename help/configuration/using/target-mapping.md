---
product: campaign
title: Zielgruppen-Mapping
description: Informationen zum Erstellen eines Zielgruppen-Mappings
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: f469689f9e8a4d805fb95a1ae120ccd35aba3731
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 3%

---

# Zielgruppen-Mapping{#target-mapping}

Die Erstellung eines Zielgruppen-Mappings ist in zwei Fällen erforderlich:

* Wenn Sie eine andere Empfängertabelle als die von Adobe Campaign bereitgestellte verwenden,
* Wenn Sie eine Filterdimension konfigurieren, die sich von der Standard-Zielgruppendimension auf dem Zielgruppen-Mapping-Bildschirm unterscheidet.

Der Assistent zur Erstellung von Zielgruppen-Mappings hilft Ihnen bei der Erstellung aller Schemata, die für die Verwendung Ihrer benutzerdefinierten Tabelle erforderlich sind.

## Mit der benutzerdefinierten Tabelle verknüpfte Schemata erstellen und konfigurieren {#creating-and-configuring-schemas-linked-to-the-custom-table}

Bevor Sie ein Zielgruppen-Mapping erstellen, sind mehrere Konfigurationen erforderlich, damit Adobe Campaign mit einem neuen Empfängerdatenschema arbeiten kann.

Gehen Sie hierzu wie folgt vor:

1. Erstellen Sie ein neues Datenschema, das die Felder der benutzerdefinierten Tabelle integriert, die Sie verwenden möchten.

   Weitere Informationen finden Sie unter [Schemareferenz (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   In unserem Beispiel erstellen wir ein Kundenschema, eine sehr einfache Tabelle mit den folgenden Feldern: ID, Vorname, Nachname, E-Mail-Adresse, Mobiltelefonnummer. Ziel ist es, E-Mail- oder SMS-Warnungen an die in dieser Tabelle gespeicherten Personen senden zu können.

   Beispielschema (cus:individual)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. Deklarieren Sie Ihr Schema mithilfe des Attributs =„true“ als externe Ansicht. Siehe [Das Attribut view](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Wenn Sie eine Briefpost-Adresse hinzufügen müssen, verwenden Sie bitte den folgenden Strukturtyp:

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. Klicken Sie auf **[!UICONTROL Knoten Administration > Kampagnen-Management > Zielgruppen]** .
1. Klicken Sie auf **Neu**, um den Assistenten zur Erstellung von Zielgruppen-Mappings zu öffnen.
1. Geben Sie das **Titel** ein und wählen Sie im Feld **Zielgruppendimension** das soeben erstellte Schema aus.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Im Fenster **Adressformulare bearbeiten** wählen Sie die Schemafelder aus, die den verschiedenen Versandadressen entsprechen. Hier können wir die Felder **@email** und **@mobile**.

   ![](assets/mapping_diffusion_wizard_2.png)

1. Geben Sie im folgenden **Speicher** das Feld **Suffix der Erweiterungsschemata** ein, um die neuen Schemata von den von Adobe Campaign bereitgestellten vordefinierten Schemata zu unterscheiden.

   Klicken Sie **[!UICONTROL Neue zusätzliche Felder definieren]**, um die Dimension auszuwählen, die Sie in Ihrem Versand ansprechen möchten.

   Standardmäßig wird die Ausschlussverwaltung in derselben Tabelle wie Nachrichten gespeichert.

   Aktivieren Sie das **Generieren eines Speicherschemas für das Tracking**, wenn Sie die Speicherung für das Tracking konfigurieren möchten, das mit Ihrem Zielgruppen-Mapping verknüpft ist.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign unterstützt nicht mehrere Empfängerschemata, so genannte Zielgruppenschemata, die mit denselben Broadlog- und/oder Trackinglog-Schemata verknüpft sind. Dies kann ansonsten zu Anomalien bei der späteren Datenabstimmung führen. Weiterführende Informationen dazu finden Sie auf der Seite [Empfehlung und Einschränkungen](../../configuration/using/about-custom-recipient-table.md) .

1. Wählen Sie im **Erweiterungen** die optionalen Schemata aus, die Sie generieren möchten. (Die Liste der verfügbaren Schemata hängt von den auf der Adobe Campaign-Plattform installierten Modulen ab.)

   ![](assets/mapping_diffusion_wizard_4.png)

1. Klicken Sie auf **Speichern**, um den Assistenten zu schließen.

   Der Assistent verwendet das Startschema, um alle anderen Schemata zu erstellen, die für die Funktionsweise des neuen Zielgruppen-Mappings erforderlich sind.

   ![](assets/mapping_schema_list.png)

## Zielgruppen-Mapping verwenden {#using-target-mapping}

Es gibt zwei Möglichkeiten, das neue Schema als Zielgruppe eines Versands zu verwenden:

* Erstellen Sie eine oder mehrere Versandvorlagen basierend auf der Zuordnung.
* Wählen Sie beim Erstellen eines Versands die Zuordnung direkt während der Zielgruppenauswahl aus, wie unten dargestellt:

![](assets/mapping_selection_ciblage.png)
