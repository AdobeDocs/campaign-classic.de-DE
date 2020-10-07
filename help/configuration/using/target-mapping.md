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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 3%

---


# Target mapping{#target-mapping}

Die Erstellung von Zielgruppen-Mappings ist in zwei Fällen erforderlich:

* wenn Sie eine andere als die von Adobe Campaign bereitgestellte Empfänger-Tabelle verwenden,
* wenn Sie eine Filterdimension konfigurieren, die sich von der standardmäßigen Zielgruppendimension im Bildschirm &quot;Zielgruppen-Mapping&quot;unterscheidet.

Der Assistent zum Erstellen von Zielgruppen-Mappings hilft Ihnen, alle Schema zu erstellen, die zur Verwendung Ihrer benutzerdefinierten Tabelle erforderlich sind.

## Erstellen und Konfigurieren von mit der benutzerdefinierten Tabelle verknüpften Schemas {#creating-and-configuring-schemas-linked-to-the-custom-table}

Bevor Sie ein Zielgruppen-Mapping erstellen, sind mehrere Konfigurationen erforderlich, damit Adobe Campaign mit einem neuen Empfänger-Daten-Schema arbeiten kann.

Gehen Sie hierzu wie folgt vor:

1. Erstellen Sie ein neues Schema, das die zu verwendenden Felder der benutzerdefinierten Tabelle integriert.

   Weitere Informationen finden Sie in der [Schema-Referenz (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   In unserem Beispiel erstellen wir ein Schema für Kunden, eine sehr einfache Tabelle mit den folgenden Feldern: ID, Vorname, Nachname, E-Mail-Adresse, Handynummer. Ziel ist es, E-Mail- oder SMS-Warnungen an die in dieser Tabelle gespeicherten Personen senden zu können.

   Schema (cus:single)

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

1. Deklarieren Sie Ihr Schema als externe Ansicht mit dem Attribut =&quot;true&quot;. Siehe [Das Attribut](../../configuration/using/schema-characteristics.md#the-view-attribute)Ansicht.

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

1. Klicken Sie auf den Knoten **[!UICONTROL Administration > Kampagnenverwaltung > Zielgruppen-Mappings]** .
1. Klicken Sie auf die Schaltfläche **Neu** , um den Assistenten zum Erstellen von Zielgruppen-Mappings zu öffnen.
1. Geben Sie das **Beschriftungsfeld** ein und wählen Sie das soeben erstellte Schema im Feld &quot; **Zielgruppendimension** &quot;aus.

   ![](assets/mapping_diffusion_wizard_1.png)

1. Wählen Sie im Fenster **Adressformulare** bearbeiten die Felder des Schemas aus, die den verschiedenen Versand-Adressen entsprechen. Hier können wir die Felder **@email** und **@mobile** zuordnen.

   ![](assets/mapping_diffusion_wizard_2.png)

1. Geben Sie im folgenden Fenster **Datenspeicherung** das Feld **Suffix des Erweiterungsschemas** ein, um die neuen Schema von den von Adobe Campaign bereitgestellten vordefinierten Schemas zu unterscheiden.

   Klicken Sie auf **[!UICONTROL Neue zusätzliche Felder]** definieren, um die Dimension auszuwählen, die Sie in Ihrem Versand Zielgruppe haben möchten.

   Standardmäßig wird die Ausschlussverwaltung in denselben Tabellen wie Nachrichten gespeichert. Markieren Sie das Schema &quot;Datenspeicherung zur Verfolgung **** generieren&quot;, wenn Sie die Datenspeicherung für die mit Ihrem Zielgruppen-Mapping verknüpfte Verfolgung konfigurieren möchten.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign unterstützt nicht mehrere Empfänger-Schema, die als Targeting-Schema bezeichnet werden und mit denselben Broadlog- und/oder Trackinglog-Schemas verknüpft sind. Andernfalls kann dies zu Anomalien bei der Datenabstimmung im Anschluss führen. Weitere Informationen hierzu finden Sie auf der Seite [Empfehlung und Einschränkungen](../../configuration/using/about-custom-recipient-table.md) .

1. Wählen Sie im Fenster &quot; **Erweiterungen** &quot;die optionalen Schema aus, die Sie erstellen möchten (die Liste der verfügbaren Schema hängt von den auf der Adobe Campaign-Plattform installierten Modulen ab).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Click the **Save** button to close the wizard.

   Der Assistent verwendet das Beginn-Schema, um alle anderen Schema zu erstellen, die erforderlich sind, damit das neue Zielgruppen-Mapping funktioniert.

   ![](assets/mapping_schema_list.png)

## Zielgruppen-Mapping verwenden {#using-target-mapping}

Es gibt zwei Möglichkeiten, das neue Schema als Zielgruppe eines Versands zu verwenden:

* Erstellen Sie eine oder mehrere Versandvorlagen basierend auf der Zuordnung
* Wählen Sie beim Erstellen eines Versands die Zuordnung direkt während der Auswahl der Zielgruppe aus, wie nachfolgend gezeigt:

![](assets/mapping_selection_ciblage.png)

**Verwandtes Thema**

* [Reagieren Sie schnell auf Kundenanfragen, um auf ihre Daten zuzugreifen](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)