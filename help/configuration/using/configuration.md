---
product: campaign
title: Navigationsstruktur von Campaign Explorer konfigurieren
description: Erfahren Sie, wie Sie den Navigationsbaum von Campaign Explorer konfigurieren
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 2%

---

# Navigationsstruktur von Campaign Explorer konfigurieren{#configuration}

![](../../assets/v7-only.svg)

Erfahrene Benutzer können Ordner im Explorer-Baum hinzufügen und anpassen.

Erfahren Sie mehr über den Campaign-Explorer und die Navigationshierarchie [in diesem Abschnitt](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

Die von der Navigationsliste verwendeten Ordnertypen werden in einem XML-Dokument beschrieben, das der Grammatik der **xtk:navtree** Schema.

Das XML-Dokument ist wie folgt strukturiert:

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

Das XML-Dokument enthält die **`<navtree>`** Stammelement mit **name** und **namespace** -Attribute, um den Dokumentnamen und den Namespace anzugeben. Der Name und der Namespace bilden den Identifizierungsschlüssel des Dokuments.

Die globalen Befehle der Anwendung werden im Dokument aus dem **`<commands>`** -Element.

Die Deklaration von Dateitypen ist im Dokument mit den folgenden Elementen strukturiert: **`<model>`** und **`<nodemodel>`**.

## Globale Befehle {#global-commands}

Mit einem globalen Befehl können Sie eine Aktion starten. Diese Aktion kann ein Eingabeformular oder ein SOAP-Aufruf sein.

Globale Befehle können über die Hauptmenge aufgerufen werden **[!UICONTROL Instrumente]** Menü.

Die Konfigurationsstruktur des Befehls sieht wie folgt aus:

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

Die Beschreibung eines globalen Befehls wird im **`<command>`** -Element mit den folgenden Eigenschaften:

* **name**: Interner Name des Befehls: der Name muss eingegeben werden und eindeutig
* **label**: Titel des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **Formular**: Formular, das gestartet werden soll: der einzugebende Wert ist der Identifikationsschlüssel des Formulars (z. B. &quot;cus:recipient&quot;)
* **rights**: Liste der spezifischen Berechtigungen (durch Kommas getrennt), die den Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Berechtigungen ist über den Link **[!UICONTROL Administration > Zugriffe > Spezifische Berechtigungen]** Ordner.
* **quickLabel**: zeigt vor Ausführung des Befehls ein Bestätigungsfeld an.

A **`<command>`** Element kann enthalten **`<command>`** untergeordneten Elemente. In diesem Fall können Sie über das übergeordnete Element ein Untermenü mit diesen untergeordneten Elementen anzeigen.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument deklariert.

Mithilfe eines Befehlstrennzeichens können Sie eine Trennleiste zwischen Befehlen anzeigen. Sie wird durch die Variable **&#39;-&#39;** -Wert, der in der Befehlsbeschriftung enthalten ist.

Die optionale Präsenz der **`<soapcall>`** -Tag mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zur SOAP-API finden Sie unter [Dokumentation zu Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Der Formularkontext kann bei der Initialisierung aus dem **`<enter>`** -Tag. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zu Formularen.

**Beispiel**:

* Deklaration eines globalen Befehls zum Starten des Formulars &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Auf dem Zeichen &quot;I&quot;wird ein Tastaturbefehl durch das Vorhandensein von **&amp;** in der Befehlsbeschriftung.

* Beispiel eines Untermenüs mit einem Trennzeichen:

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* Ausführung einer SOAP-Methode:

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## Ordnertyp {#folder-type}

Über einen Ordnertyp können Sie auf die Daten eines Schemas zugreifen. Die mit dem Ordner verknüpfte Ansicht besteht aus einer Liste und einem Eingabeformular.

Die Konfigurationsstruktur des Ordnertyps sieht wie folgt aus:

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

Die Deklaration des Ordnertyps muss unter einer **`<model>`** -Element. Mit diesem Element können Sie eine hierarchische Organisation definieren, die über die **[!UICONTROL Neuen Ordner hinzufügen]** Menü. A **`<model>`** -Element muss enthalten **`<nodemodel>`** Elemente und andere **`<model>`** -Elemente.

Die **name** und **label** -Attribute füllen den internen Namen des Elements und die in der **[!UICONTROL Neuen Ordner hinzufügen]** Menü.

Die **`<nodemodel>`** -Element enthält die Beschreibung des Ordnertyps mit den folgenden Eigenschaften:

* **name**: interner Name
* **label**: -Beschriftung, die in der **[!UICONTROL Neuen Ordner hinzufügen]** und als Standardbeschriftung beim Einfügen eines Ordners.
* **img**: Standardbild beim Einfügen von Ordnern.
* **hiddenCommands**: Liste der Befehle (durch Kommas getrennt), die maskiert werden sollen. Mögliche Werte: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot;und &quot;adbdup&quot;.
* **newFolderShortCuts**: Liste der Tastaturbefehle für Modelle (**`<nodemodel>`** durch Kommas getrennt) bei der Ordnererstellung.
* **insertRight**, **editRight**, **deleteRight**: Berechtigungen zum Einfügen, Bearbeiten und Löschen von Ordnern.

Die **`<view>`** Element unter **`<nodemodel>`** -Element enthält die Konfiguration der Liste, die mit der Ansicht verknüpft ist. Das Schema der Liste wird im **schema** -Attribut **`<view>`** -Element.

Um die Datensätze der Liste zu bearbeiten, wird implizit das Formular mit demselben Namen wie das Listenschema verwendet. Die **type** -Attribut auf **`<view>`** -Element wirkt sich auf die Anzeige des Formulars aus. Mögliche Werte:

* **listdet**: zeigt das Formular unten in der Liste an.
* **Liste**: zeigt nur die Liste an. Das Formular wird durch Doppelklick oder über die Option &quot;Öffnen&quot; im Menü zur Auswahl der Liste gestartet.
* **Formular**: zeigt ein schreibgeschütztes Formular an.
* **editForm**: zeigt ein Formular im Bearbeitungsmodus an.

>[!NOTE]
>
>Der Name des Formulars kann durch Eingabe der Variablen **Formular** -Attribut im **`<view>`** -Element.

Die Standardkonfiguration der Listenspalten erfolgt über die **`<columns>`** -Element. Eine Spalte wird auf einer **`<node>`** -Element, das die **xpath** -Attribut mit dem Feld, auf das im Schema als Wert verwiesen werden soll.

**Beispiel**: Deklaration eines Ordnertyps im Schema &quot;nms:recipient&quot;.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

Das entsprechende Menü zum Einfügen von Ordnern:

![](assets/d_ncs_integration_navigation_exemple2.png)

Filtern und Sortieren können beim Laden der Liste angewendet werden:

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### Tastaturbefehle {#shortcut-commands}

Mit einem Tastaturbefehl können Sie eine Aktion bei der Auswahl der Liste starten. Die Aktion kann ein Eingabeformular oder ein SOAP-Aufruf sein.

Befehle können über die **[!UICONTROL Aktion]** der Liste oder der zugehörigen Menüschaltfläche.

Die Konfigurationsstruktur des Befehls sieht wie folgt aus:

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

Die Beschreibung eines Befehls wird im **`<command>`** -Element mit den folgenden Eigenschaften:

* **name**: Interner Name des Befehls: der Name muss eingegeben und eindeutig sein.
* **label**: Titel des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **Formular**: Formular, das gestartet werden soll: der einzugebende Wert ist der Identifikationsschlüssel des Formulars (z. B. &quot;cus:recipient&quot;).
* **rights**: Liste der spezifischen Berechtigungen (durch Kommas getrennt), die den Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Berechtigungen ist über den Link **[!UICONTROL Administration > Zugriffe > Spezifische Berechtigungen]** Ordner.
* **quickLabel**: zeigt vor Ausführung des Befehls ein Bestätigungsfeld an
* **monoSelection**: erzwingt die Einmalauswahl (standardmäßig mehrere Auswahlmöglichkeiten).
* **refreshView**: erzwingt das erneute Laden der Liste nach Ausführung des Befehls.
* **enabledIf**: aktiviert den Befehl entsprechend dem eingegebenen Ausdruck.
* **img**: gibt ein Bild ein, das den Zugriff auf den Befehl in der Symbolleiste der Liste ermöglicht.

A **`<command>`** Element kann enthalten **`<command>`** untergeordneten Elemente. In diesem Fall können Sie über das übergeordnete Element ein Untermenü mit diesen untergeordneten Elementen anzeigen.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument deklariert.

Mithilfe eines Befehlstrennzeichens können Sie eine Trennleiste zwischen Befehlen anzeigen. Sie wird durch die Variable **&#39;-&#39;** -Wert, der in der Befehlsbeschriftung enthalten ist.

Die optionale Präsenz der **`<soapcall>`** -Tag mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zu SOAP-APIs finden Sie unter [Dokumentation zu Campaign JSAPI](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Der Formularkontext kann bei der Initialisierung über die **`<enter>`** -Tag. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zum Formular.

**Beispiel**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### Verknüpfte Ordner {#linked-folder}

Es gibt zwei Arten von Vorgängen zur Ordnerverwaltung:

1. Der Ordner ist eine Ansicht: Die Liste zeigt alle Datensätze an, die mit dem Schema verknüpft sind, mit der Möglichkeit, das System in die Ordnereigenschaften zu filtern.
1. Der Ordner ist verknüpft: Die Datensätze in der Liste werden implizit nach dem Ordner-Link gefiltert.

Bei verknüpften Ordnern wird die **folderLink** -Attribut auf **`<nodemodel>`** -Element gefüllt werden. Dieses Attribut enthält den Namen des Links im Ordner, der im Datenschema konfiguriert ist.

Beispiel einer Deklaration eines verknüpften Ordners im Datenschema:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Die Konfiguration der **`<nodemodel>`** im Link des Ordners &quot;Ordner&quot;wie folgt aussehen:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
