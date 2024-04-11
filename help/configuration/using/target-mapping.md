---
product: campaign
title: Zielgruppen-Mapping
description: Erfahren Sie, wie Sie ein Zielgruppen-Mapping erstellen
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 38333669-5598-4811-a121-b677c1413f56
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 3%

---

# Zielgruppen-Mapping{#target-mapping}



Die Erstellung von Zielgruppen-Mappings ist in zwei Fällen erforderlich:

* wenn Sie eine andere als die von Adobe Campaign bereitgestellte Empfängertabelle verwenden,
* wenn Sie im Zielgruppen-Mapping-Bildschirm eine von der Standard-Zielgruppendimension abweichende Filterdimension konfigurieren.

Mit dem Assistenten zur Zielgruppen-Mapping-Erstellung können Sie alle Schemas erstellen, die zur Verwendung Ihrer benutzerdefinierten Tabelle erforderlich sind.

## Schemata erstellen und konfigurieren, die mit der benutzerdefinierten Tabelle verknüpft sind {#creating-and-configuring-schemas-linked-to-the-custom-table}

Bevor Sie ein Zielgruppen-Mapping erstellen, sind mehrere Konfigurationen erforderlich, damit Adobe Campaign mit einem neuen Empfängerdatenschema arbeiten kann.

Gehen Sie hierzu wie folgt vor:

1. Erstellen Sie ein neues Datenschema, das die Felder der benutzerdefinierten Tabelle integriert, die Sie verwenden möchten.

   Weitere Informationen finden Sie unter [Schemareferenz (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   In unserem Beispiel erstellen wir ein Kundenschema, eine sehr einfache Tabelle mit den folgenden Feldern: ID, Vorname, Nachname, E-Mail-Adresse, Mobiltelefonnummer. Ziel ist es, E-Mail- oder SMS-Warnungen an die in dieser Tabelle gespeicherten Personen senden zu können.

   Beispielschema (cus:einzeln)

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

1. Deklarieren Sie Ihr Schema als externe Ansicht mit dem Attribut =&quot;true&quot;. Siehe Abschnitt [Das Ansichtsattribut](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Wenn Sie eine Briefpost-Adresse hinzufügen müssen, verwenden Sie die folgende Struktur:

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

1. Klicken Sie auf **[!UICONTROL Administration > Kampagnenverwaltung > Zielgruppen-Mappings]** Knoten.
1. Klicken Sie auf **Neu** -Schaltfläche, um den Assistenten zur Zielgruppen-Mapping-Erstellung zu öffnen.
1. Geben Sie die **Titel** und wählen Sie das Schema aus, das Sie gerade im **Zielgruppendimension** -Feld.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Im **Adressformulare bearbeiten** -Fenster die Felder des Schemas auswählen, die den verschiedenen Versandadressen entsprechen. Hier können wir die **@email** und **@mobile** -Felder.

   ![](assets/mapping_diffusion_wizard_2.png)

1. Im Folgenden **Speicherung** -Fenster, geben Sie die **Suffix der Erweiterungsschemas** , um die neuen Schemata von den von Adobe Campaign bereitgestellten nativen Schemata zu unterscheiden.

   Klicks **[!UICONTROL Neue zusätzliche Felder definieren]** um die Dimension auszuwählen, die Sie in Ihrem Versand als Ziel auswählen möchten.

   Standardmäßig wird die Ausschlussverwaltung in derselben Tabelle wie Nachrichten gespeichert.

   Überprüfen Sie die **Speicherschema für Tracking generieren** aktivieren, wenn Sie die Speicherung für das mit Ihrem Zielgruppen-Mapping verknüpfte Tracking konfigurieren möchten.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign unterstützt nicht mehrere Empfängerschemata, so genannte Zielgruppenschemas, die mit denselben Broadlog- und/oder Trackinglog-Schemata verknüpft sind. Dies kann andernfalls zu Anomalien bei der Datenabstimmung später führen. Weitere Informationen hierzu finden Sie im Abschnitt [Empfehlungen und Einschränkungen](../../configuration/using/about-custom-recipient-table.md) Seite.

1. Im **Erweiterungen** die optionalen Schemata, die Sie erstellen möchten (die Liste der verfügbaren Schemata hängt von den auf der Adobe Campaign-Plattform installierten Modulen ab).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Klicken Sie auf **Speichern** -Schaltfläche, um den Assistenten zu schließen.

   Der Assistent verwendet das Startschema, um alle anderen Schemata zu erstellen, die für die Funktionsfähigkeit des neuen Zielgruppen-Mappings erforderlich sind.

   ![](assets/mapping_schema_list.png)

## Zielgruppen-Mapping verwenden {#using-target-mapping}

Es gibt zwei Möglichkeiten, das neue Schema als Zielgruppe eines Versands zu verwenden:

* Erstellen einer oder mehrerer Versandvorlagen basierend auf dem Mapping
* Wählen Sie beim Erstellen eines Versands direkt das Mapping während der Zielgruppenauswahl aus, wie unten dargestellt:

![](assets/mapping_selection_ciblage.png)
