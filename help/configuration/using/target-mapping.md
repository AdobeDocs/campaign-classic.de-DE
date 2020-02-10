---
title: Target mapping
seo-title: Target mapping
description: Target mapping
seo-description: null
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8b3ab02d1fd90c3f14314508a8fa7d99df82436c

---


# Target mapping{#target-mapping}

Die Erstellung der Zielzuordnung ist in zwei Fällen erforderlich:

* wenn Sie eine andere als die von Adobe Campaign bereitgestellte Empfängertabelle verwenden,
* wenn Sie eine Filterdimension konfigurieren, die sich von der standardmäßigen Targeting-Dimension im Anzeigebereich der Zielzuordnung unterscheidet.

Der Assistent zum Erstellen von Zielzuordnungen hilft Ihnen, alle Schemata zu erstellen, die zur Verwendung Ihrer benutzerdefinierten Tabelle erforderlich sind.

## Erstellen und Konfigurieren von mit der benutzerdefinierten Tabelle verknüpften Schemata {#creating-and-configuring-schemas-linked-to-the-custom-table}

Bevor Sie eine Zielzuordnung erstellen, sind mehrere Konfigurationen erforderlich, damit Adobe Campaign mit einem neuen Empfängerdatenschema arbeiten kann.

Gehen Sie hierzu wie folgt vor:

1. Erstellen Sie ein neues Datenschema, das die Felder der benutzerdefinierten Tabelle, die Sie verwenden möchten, integriert.

   Weitere Informationen finden Sie in der [Schemareferenz (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   In unserem Beispiel erstellen wir ein Kundenschema, eine sehr einfache Tabelle mit den folgenden Feldern: ID, Vorname, Nachname, E-Mail-Adresse, Handynummer. Ziel ist es, E-Mail- oder SMS-Warnungen an die in dieser Tabelle gespeicherten Personen senden zu können.

   Beispielschema (cus:individuell)

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

1. Deklarieren Sie Ihr Schema als externe Ansicht mit dem Attribut =&quot;true&quot;. Siehe [Das Attribut](../../configuration/using/schema-characteristics.md#the-view-attribute)view.

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Wenn Sie eine E-Mail-Adresse hinzufügen müssen, verwenden Sie bitte die folgende Struktur:

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

1. Klicken Sie auf die **[!UICONTROL Administration > Campaign management > Target mappings]** Node.
1. Klicken Sie auf die Schaltfläche **Neu** , um den Assistenten zum Erstellen der Zielzuordnung zu öffnen.
1. Geben Sie das Feld **Bezeichnung** ein und wählen Sie das Schema aus, das Sie soeben im Feld **Targeting-Dimension** erstellt haben.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Wählen Sie im Fenster **Adressformulare** bearbeiten die Felder des Schemas aus, die den verschiedenen Zustelladressen entsprechen. Hier können wir die Felder **@email** und **@mobile** zuordnen.

   ![](assets/mapping_diffusion_wizard_2.png)

1. Geben Sie im folgenden **Speicherfenster** das **Suffix des Erweiterungsschemas** ein, um die neuen Schemas von den von Adobe Campaign bereitgestellten Standardschemas zu unterscheiden.

   Klicken Sie auf **[!UICONTROL Define new additional fields]** , um die Dimension auszuwählen, die Sie in Ihrer Bereitstellung als Ziel auswählen möchten.

   Standardmäßig wird die Ausschlussverwaltung in denselben Tabellen wie Nachrichten gespeichert. Markieren Sie das Feld Speicherschema zur Verfolgung **** erstellen, wenn Sie Speicher für die mit Ihrer Zielzuordnung verknüpfte Verfolgung konfigurieren möchten.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!CAUTION]
   >
   >Adobe Campaign unterstützt nicht mehrere Empfängerschemata, die als Targeting-Schemata bezeichnet werden und mit denselben Broadlog- und/oder Trackinglog-Schemata verknüpft sind. Andernfalls kann dies zu Anomalien bei der Datenabstimmung im Anschluss führen. Weitere Informationen hierzu finden Sie auf der Seite [Empfehlung und Einschränkungen](../../configuration/using/about-custom-recipient-table.md) .

1. Wählen Sie im Fenster &quot; **Erweiterungen** &quot;die optionalen Schemata aus, die Sie erstellen möchten (die Liste der verfügbaren Schemata hängt von den auf der Adobe Campaign-Plattform installierten Modulen ab).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Click the **Save** button to close the wizard.

   Der Assistent verwendet das Startschema, um alle anderen Schemata zu erstellen, die erforderlich sind, damit die neue Zielzuordnung funktioniert.

   ![](assets/mapping_schema_list.png)

## Verwenden der Zielzuordnung {#using-target-mapping}

Es gibt zwei Möglichkeiten, das neue Schema als Ziel einer Bereitstellung zu verwenden:

* Erstellen Sie eine oder mehrere Bereitstellungsvorlagen basierend auf der Zuordnung
* Wählen Sie beim Erstellen einer Bereitstellung die Zuordnung direkt während der Zielauswahl aus, wie unten dargestellt:

![](assets/mapping_selection_ciblage.png)

**Verwandtes Thema**

* [Reagieren Sie schnell auf Kundenanfragen, um auf ihre Daten zuzugreifen](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)