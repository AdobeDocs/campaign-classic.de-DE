---
title: Datenpackages
seo-title: Datenpackages
description: Datenpackages
seo-description: null
page-status-flag: never-activated
uuid: 867b2702-dbc4-4b71-a385-a2c7fd09d25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 42867665-d0ca-486e-9110-91716c0d5c57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Datenpackages{#working-with-data-packages}

## Über Datenpackages {#about-data-packages}

Adobe Campaign ermöglicht den Export oder Import von Plattformkonfigurationen und Daten mithilfe eines Package-Systems. Packages können unterschiedliche Konfigurationen und gefilterte oder ungefilterte Elemente enthalten.

Datenpackages ermöglichen den Austausch von Entitäten innerhalb der Adobe-Campaign-Datenbank über XML-Dateien. Jede in einem Package enthaltene Entität wird mit der Gesamtheit ihrer Daten dargestellt.

Das Prinzip der **Datenpackages** besteht darin, eine Datenkonfiguration zu exportieren und in ein anderes Adobe Campaign-System zu integrieren. Weiterführende Informationen zur Gewährleistung eines einheitlichen Sets von Datenpackages finden Sie in dieser [Technote](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_How_to_maintain_a_consistent_set_of_data_packages.pdf).

### Typen von Packages {#types-of-packages}

Es gibt drei Arten exportierbarer Packages: Benutzer-Packages, Plattform-Packages und Admin-Packages.

* **Benutzer-Package**: Ermöglicht es, die Liste der zu exportierenden Entitäten auszuwählen. Dieser Packagetyp verwaltet Abhängigkeiten und überprüft Fehler.
* **Plattform-Package**: Enthält alle hinzugefügten (nicht standardmäßigen) technischen Ressourcen: Schemata, JavaScript-Code etc.

   ![](assets/ncs_datapackage_package_platform.png)

* **Admin-Package**: Enthält alle hinzugefügten (nicht standardmäßigen) Vorlagen und fachlichen Ressourcen: Vorlagen, Bibliotheken etc.

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>Die **Plattform**- und **Admin**-Typen enthalten eine vordefinierte Liste von zu exportierenden Entitäten. Jeder exportierbaren Entität sind Filterbedingungen zugeordnet, die es ermöglichen, die Standard-Ressourcen aus dem erstellten Package auszuschließen.

## Datenstruktur {#data-structure}

Die Beschreibung eines Datenpackages ist ein strukturiertes XML-Dokument, das die Grammatik des **xrk:navtree**-Datenschemas einhält.

Datenpackage-Beispiel:

```
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

Das XML-Dokument muss mit dem **`<package>`** Element beginnen und enden. Alle **`<entities>`** nachfolgenden Elemente verteilen die Daten nach Dokumenttyp.

An **`<entities>`** element contains the data of the package in the format of the data schema entered in the **schema** attribute.

Die Daten eines Packages dürfen keine internen Schlüssel enthalten, die nicht zwischen Datenbanken kompatibel sind, wie beispielsweise automatisch generierte Schlüssel (Option **autopk**).

In unserem Beispiel wurden die Joins der &quot;folder&quot;- und &quot;company&quot;-Relation durch High-Level-Keys in den Zieltabellen ersetzt:

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

The **`operation`** attribute with the value &quot;none&quot; defines a reconciliation link.

Ein Datenpackage kann manuell über einen beliebigen Texteditor erstellt werden. Es muss nur sichergestellt werden, dass die Struktur des XML-Dokuments mit dem &quot;xtk:navtree&quot;-Datenschema übereinstimmt. Die Adobe-Campaign-Konsole ist mit einem Modul zum Import und Export von Datenpackages ausgestattet.

## Packages exportieren {#exporting-packages}

### Über den Package-Export {#about-package-export}

Für den Export von Packages gibt es drei Möglichkeiten:

* Mit **[!UICONTROL Package Export Wizard]** dieser Option können Sie einen Satz von Objekten in ein einzelnes Paket exportieren. Weitere Informationen hierzu finden Sie unter [Exportieren einer Gruppe von Objekten in einem Paket](#exporting-a-set-of-objects-in-a-package)
* A **single object** can be exported in a package directly by right-clicking on it and selecting **[!UICONTROL Actions > Export in a package]**.
* **Mit Paketdefinitionen** können Sie eine Paketstruktur erstellen, in der Sie Objekte hinzufügen, die später in ein Paket exportiert werden. Weitere Informationen hierzu finden Sie unter [Verwalten von Paketdefinitionen](#managing-package-definitions)

Nachdem ein Package exportiert wurde, können Sie das Package und alle hinzugefügten Entitäten in eine andere Campaign-Instanz importieren.

### Objekte in ein Package exportieren {#exporting-a-set-of-objects-in-a-package}

The package export wizard is accessible via the **[!UICONTROL Tools > Advanced > Export package...]** menu of the Adobe Campaign client console.

![](assets/ncs_datapackage_typepackage.png)

Der Assistent weist für alle drei Packagetypen die gleichen Schritte auf:

1. Geben Sie die zu exportierenden Entitätstypen an:

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >Wenn Sie einen **[!UICONTROL Offer category]**-, **[!UICONTROL Offer environment]**- **[!UICONTROL Program]** oder **[!UICONTROL Plan]** Typordner exportieren, wählen Sie niemals den Ordner **xtk:folder** , da einige Daten verloren gehen können. Wählen Sie die Entität aus, die dem Ordner entspricht: **nms:offerCategory** für Angebotskategorien, **nms:offerEnv** für Angebotsumgebungen, **nms:programme** für Programme und **nms:plan** für Pläne.

   Mithilfe der Listenverwaltung können Sie Entitäten für den Export aus der Konfiguration hinzufügen oder löschen. Klicken Sie auf **[!UICONTROL Add]** , um eine neue Entität auszuwählen.

   Über die Schaltfläche **[!UICONTROL Detail]** kann die ausgewählte Konfiguration bearbeitet werden.

   >[!NOTE]
   >
   >Der Abhängigkeitsmechanismus steuert die Entitäts-Exportsequenz. For more on this, refer to [Managing dependencies](#managing-dependencies).

1. Im Eingabebildschirm der Entitätenkonfiguration wird die Filterabfrage des zu extrahierenden Dokumenttyps bestimmt.

   Hier muss die Filterbedingung der Datenextraktion angegeben werden.

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >Der Abfrageeditor wird in [diesem Abschnitt](../../platform/using/about-queries-in-campaign.md) beschrieben.

1. Click **[!UICONTROL Next]** and select the sorting columns to order the data during extraction:

   ![](assets/ncs_datapackage_export5.png)

1. Überprüfen Sie die Vorschau der zu extrahierenden Daten, bevor Sie den Export starten.

   ![](assets/ncs_datapackage_export6.png)

1. Auf der letzten Seite des Paketexportassistenten können Sie den Export starten. Die Daten werden in der im **[!UICONTROL File]** Feld angegebenen Datei gespeichert.

   ![](assets/ncs_datapackage_export7.png)

### Abhängigkeitsverwaltung {#managing-dependencies}

Der Exportmechanismus ermöglicht es Adobe Campaign, die Relationen zwischen den exportierten Elementen zu verfolgen.

Der Mechanismus wird durch zwei Regeln bestimmt:

* Die über eine Relation mit einer Integrität vom Typ **own** oder **owncopy** verbundenen Objekte werden im gleichen Package exportiert wie das exportierte Objekt.
* Die über eine Relation mit einer Integrität vom Typ **neutral** oder **define** (definierte Relation) verbundenen Objekte müssen separat exportiert werden.

>[!NOTE]
>
>Mit Schemaelementen verknüpfte Integritätstypen werden in [diesem Abschnitt](../../configuration/using/database-mapping.md#links--relation-between-tables) definiert.

#### Kampagne exportieren {#exporting-a-campaign}

Im Folgenden finden Sie ein Beispiel für den Export einer Kampagne. Die zu exportierende Marketingkampagne enthält eine Aufgabe (Titel: &quot;MyTask&quot;) und einen Workflow (Titel: &quot;CampaignWorkflow&quot;) im Ordner &quot;MyWorkflow&quot; (Knoten: Administration > Betreibung > Technische Workflows > Kampagnenprozesse > MyWorkflow).

Die Aufgabe und der Workflow werden im gleichen Package wie die Kampagne exportiert, da die entsprechenden Schemata über Relationen vom Integritätstyp &quot;own&quot; verbunden sind.

Packageinhalt:

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="6.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

Die Zugehörigkeit zu einem Packagetyp wird in einem Schema mit dem Attribut **@pkgAdmin und @pkgPlatform** bestimmt. Diese beiden Attribute erhalten einen XTK-Ausdruck, der die Bedingungen der Zugehörigkeit zum Package festlegt.

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

Schließlich können über das Attribut **@pkgStatus** die Exportregeln für diese Elemente oder Attribute bestimmt werden. Entsprechend dem Wert des Attributs wird das Element oder das Attribut im exportierten Package vorhanden sein. Die drei für das Attribut @pkgStatus möglichen Werte sind:

* **never**: exportiert das Feld/die Relation nicht
* **always**: forciert den Export dieses Felds
* **preCreate**: lässt die Erstellung der verbundenen Entität zu

>[!NOTE]
>
>Der Wert **preCreate** ist nur für Elemente vom Typ Relation zugelassen. Er lässt die Erstellung oder den Verweis auf eine Entität zu, die noch nicht in das exportierte Package geladen wurde.

## Package-Definitionen verwalten {#managing-package-definitions}

### Über Package-Definitionen {#about-package-definitions}

Mithilfe von Package-Definitionen können Sie eine Package-Struktur erstellen, in der Sie Entitäten hinzufügen, die später als einzelnes Package exportiert werden. Sie können dann dieses Package und alle hinzugefügten Entitäten in eine andere Campaign-Instanz importieren.

**Verwandte Themen:**

* [Package-Definitionen erstellen](#creating-a-package-definition)
* [Entitäten zu einer Package-Definition hinzufügen](#adding-entities-to-a-package-definition)
* [Erzeugung von Package-Definitionen konfigurieren](#configuring-package-definitions-generation)
* [Packages über eine Package-Definition exportieren](#exporting-packages-from-a-package-definition)

### Package-Definitionen erstellen {#creating-a-package-definition}

Paketdefinitionen können über das **[!UICONTROL Administration > Configuration > Package management > Package definitions]** Menü aufgerufen werden.

To create a package definition, click the **[!UICONTROL New]** button, then fill in the package definition general information.

![](assets/packagedefinition_create.png)

Anschließend können Sie Entitäten zur Package-Definition hinzufügen und diese in ein XML-Datei-Package exportieren.

**Verwandte Themen:**

* [Entitäten zu einer Package-Definition hinzufügen](#adding-entities-to-a-package-definition)
* [Erzeugung von Package-Definitionen konfigurieren](#configuring-package-definitions-generation)
* [Packages über eine Package-Definition exportieren](#exporting-packages-from-a-package-definition)

### Entitäten zu einer Package-Definition hinzufügen {#adding-entities-to-a-package-definition}

Klicken Sie auf der **[!UICONTROL Content]** Registerkarte auf die **[!UICONTROL Add]** Schaltfläche, um die Entitäten auszuwählen, die mit dem Paket exportiert werden sollen. Bewährte Verfahren bei der Auswahl von Entitäten werden im Abschnitt [Exportieren eines Objektsatzes in einem Paket](#exporting-a-set-of-objects-in-a-package) beschrieben.

![](assets/packagedefinition_addentities.png)

Entitäten können direkt über ihren Speicherort in der Instanz zu einer Package-Definition hinzugefügt werden. Gehen Sie dazu wie folgt vor:

1. Klicken Sie mit der rechten Maustaste auf die gewünschte Entität und wählen Sie **[!UICONTROL Actions > Export in a package]**.

   ![](assets/packagedefinition_singleentity.png)

1. Wählen Sie **[!UICONTROL Add to a package definition]** die Paketdefinition aus, der Sie die Entität hinzufügen möchten.

   ![](assets/packagedefinition_packageselection.png)

1. Die Entität wird der Paketdefinition hinzugefügt und wird mit dem Paket exportiert (siehe [Exportieren von Paketen aus einer Paketdefinition](#exporting-packages-from-a-package-definition)).

   ![](assets/packagedefinition_entityadded.png)

### Erzeugung von Package-Definitionen konfigurieren {#configuring-package-definitions-generation}

Die Paketerstellung kann über die **[!UICONTROL Content]** Registerkarte &quot;Paketdefinition&quot;konfiguriert werden. To do this, click the **[!UICONTROL Generation parameters]** link.

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**: enthält die derzeit in der Paketdefinition verwendete Definition.
* **[!UICONTROL Include an installation script]**: können Sie ein Javascript-Skript hinzufügen, das beim Paketimport ausgeführt wird. Wenn diese Option aktiviert ist, wird eine **[!UICONTROL Script]** Registerkarte im Bildschirm &quot;Paketdefinition&quot;hinzugefügt.
* **[!UICONTROL Include default values]**: fügt dem Paket die Werte aller Entitätsattribute hinzu.

   Diese Option ist standardmäßig nicht ausgewählt, um lange Exporte zu vermeiden. Dies bedeutet, dass Attribute mit Standardwerten (&quot;Leerstring&quot;, &quot;0&quot; und &quot;false&quot;, wenn im Schema nichts anderes definiert ist) von Entitäten nicht zum Package hinzugefügt und deshalb nicht exportiert werden.

   >[!CAUTION]
   >
   >Durch Deaktivieren dieser Option werden möglicherweise lokale und importierte Versionen zusammengeführt.
   >
   >Wenn die Instanz, in der das Package importiert wird, identische Entitäten wie das Package enthält (z. B. mit derselben externen ID), werden die zugehörigen Attribute nicht aktualisiert. Dies kann passieren, wenn die Attribute der vorherigen Instanz Standardwerte aufweisen, da sie nicht im Package enthalten sind.
   >
   >In that case, selecting the **[!UICONTROL Include default values]** option would prevent versions merging, as all attributes from the former instance would be exported with the package.

### Packages über eine Package-Definition exportieren {#exporting-packages-from-a-package-definition}

Gehen Sie wie folgt vor, um ein Package über eine Package-Definition zu exportieren:

1. Wählen Sie die zu exportierende Paketdefinition aus, klicken Sie auf die **[!UICONTROL Actions]** Schaltfläche und wählen Sie **[!UICONTROL Export the package]**.
1. Standardmäßig wird eine dem exportierten Package entsprechende XML-Datei ausgewählt. Ihr Name entspricht dem Namensraum und dem Namen der Package-Definition.
1. Once the package name and location defined, click the **[!UICONTROL Start]** button to launch the export.

   ![](assets/packagedefinition_packageexport.png)

## Packages importieren {#importing-packages}

### Über den Package-Import {#about-package-import}

The package import wizard is accessible via the main menu **[!UICONTROL Tools > Advanced > Package import...]** of the Adobe Campaign client console.

Sie können ein Package von einem zuvor durchgeführten Export, zum Beispiel aus einer anderen Adobe-Campaign-Instanz, oder abhängig von Ihren Lizenzbedingungen ein Standard-Package importieren.

![](assets/ncs_datapackage_import.png)

### Package-Installation ausgehend von einer Datei {#installing-a-package-from-a-file}

To import an existing data package, select the XML file and click **[!UICONTROL Open]**.

![](assets/ncs_datapackage_import_1.png)

Der Inhalt des zu importierenden Packages wird daraufhin im mittleren Bereich des Assistenten angezeigt.

Klicken Sie auf **[!UICONTROL Next]** und **[!UICONTROL Start]** , um den Import zu starten.

![](assets/ncs_datapackage_import_2.png)

### Standard-Package installieren {#installing-a-standard-package}

Standard-Packages werden installiert, wenn Adobe Campaign konfiguriert wird. Abhängig von Ihren Berechtigungen und Ihrem Bereitstellungsmodell können Sie neue Standard-Packages importieren, wenn Sie neue Optionen oder Add-ons erwerben oder wenn Sie ein Upgrade auf ein neues Angebot durchführen.

Entnehmen Sie Ihrem Lizenzvertrag, welche Packages Sie installieren können.

Weitere Informationen zu Standard-Packages finden Sie in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md).
