---
product: campaign
title: Navigationsstruktur von Campaign Explorer konfigurieren
feature: Application Settings
description: Erfahren Sie, wie Sie den Navigationsbaum von Campaign Explorer konfigurieren
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 1%

---

# Navigationsstruktur von Campaign Explorer konfigurieren{#configuration}

Erfahrene Benutzer können Ordner im Explorer-Baum hinzufügen und anpassen.

Weitere Informationen zum Campaign-Explorer und zur Navigationshierarchie [finden Sie in diesem Abschnitt](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

Die von der Navigationsliste verwendeten Ordnertypen werden in einem XML-Dokument beschrieben, das der Grammatik des Schemas **xtk:navtree** folgt.

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

Das XML-Dokument enthält das Stammelement **`<navtree>`** mit den Attributen **name** und **namespace**, um den Dokumentnamen und den Namespace anzugeben. Der Name und der Namespace bilden den Identifizierungsschlüssel des Dokuments.

Die globalen Befehle der Anwendung werden im Dokument aus dem Element **`<commands>`** deklariert.

Die Deklaration der Dateitypen ist im Dokument mit den folgenden Elementen strukturiert: **`<model>`** und **`<nodemodel>`**.

## Globale Befehle {#global-commands}

Mit einem globalen Befehl können Sie eine Aktion starten. Diese Aktion kann ein Eingabeformular oder ein SOAP Aufruf sein.

Auf globale Befehle kann über das Hauptmenü **[!UICONTROL Tools]** zugegriffen werden.

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

Die Beschreibung eines globalen Befehls wird im Element **`<command>`** mit den folgenden Eigenschaften eingegeben:

* **name**: Interner Name des Befehls: Der Name muss eingegeben und eindeutig sein.
* **label**: Titel des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **form**: Formular, das gestartet werden soll: Der einzugebende Wert ist der Identifikationsschlüssel des Formulars (z. B. &quot;cus:recipient&quot;)
* **rights**: Liste der spezifischen Berechtigungen (durch ein Komma getrennt), die den Zugriff auf diesen Befehl ermöglichen. Auf die Liste der verfügbaren Berechtigungen kann über den Ordner **[!UICONTROL Administration > Zugriffe > Spezifische Berechtigungen]** zugegriffen werden.
* **anLabelLabel**: zeigt vor Ausführung des Befehls ein Bestätigungsfeld an.

Ein Element **`<command>`** kann **`<command>`** Unterelemente enthalten. In diesem Fall können Sie über das übergeordnete Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument deklariert.

Mithilfe eines Befehlstrennzeichens können Sie eine Trennleiste zwischen Befehlen anzeigen. Sie wird durch den in der Befehlsbeschriftung enthaltenen Wert **&#39;-&#39;** identifiziert.

Das optionale Vorhandensein des **`<soapcall>`** -Tags mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zur SOAP-API finden Sie in der [JSAPI-Dokumentation für Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Der Formularkontext kann bei der Initialisierung vom Tag **`<enter>`** aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zu Formularen.

**Beispiel**:

* Deklaration eines globalen Befehls zum Starten des Formulars &quot;xtk:import&quot;:

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  Auf dem I-Zeichen wird ein Tastaturbefehl durch das Vorhandensein von **&amp;** in der Befehlsbeschriftung deklariert.

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

* Ausführung einer SOAP Methode:

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

Die Deklaration des Ordnertyps muss unter einem **`<model>`** -Element eingegeben werden. Mit diesem Element können Sie eine hierarchische Organisation definieren, die im Menü **[!UICONTROL Neuen Ordner hinzufügen]** angezeigt wird. Ein **`<model>`** -Element muss **`<nodemodel>`** -Elemente und andere **`<model>`** -Elemente enthalten.

Die Attribute **name** und **label** füllen den internen Namen des Elements und die im Menü **[!UICONTROL Ordner hinzufügen]** angezeigte Bezeichnung aus.

Das Element **`<nodemodel>`** enthält die Beschreibung des Ordnertyps mit den folgenden Eigenschaften:

* **name**: interner Name
* **label**: Beschriftung, die im Menü **[!UICONTROL Ordner hinzufügen]** und beim Einfügen eines Ordners als Standardbeschriftung verwendet wird.
* **img**: Standardbild beim Einfügen von Ordnern.
* **hiddenCommands**: Liste der Befehle (durch ein Komma getrennt), die maskiert werden sollen. Mögliche Werte: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot;und &quot;adbdup&quot;.
* **newFolderShortCuts**: Liste der Tastaturbefehle für Modelle (**`<nodemodel>`** getrennt durch ein Komma) bei der Ordnererstellung.
* **insertRight**, **editRight**, **deleteRight**: Rechte zum Einfügen, Bearbeiten und Löschen von Ordnern.

Das Element **`<view>`** unter dem Element **`<nodemodel>`** enthält die Konfiguration der Liste, die mit der Ansicht verknüpft ist. Das Schema der Liste wird im Attribut **schema** des Elements **`<view>`** eingegeben.

Um die Datensätze der Liste zu bearbeiten, wird implizit das Formular mit demselben Namen wie das Listenschema verwendet. Das Attribut **type** für das Element **`<view>`** wirkt sich auf die Anzeige des Formulars aus. Mögliche Werte:

* **listdet**: zeigt das Formular unten in der Liste an.
* **list**: zeigt nur die Liste an. Das Formular wird durch Doppelklick oder über die Option &quot;Öffnen&quot; im Menü zur Auswahl der Liste gestartet.
* **form**: zeigt ein schreibgeschütztes Formular an.
* **editForm**: zeigt ein Formular im Bearbeitungsmodus an.

>[!NOTE]
>
>Der Name des Eingabeformulars kann überschrieben werden, indem das Attribut **form** im Element **`<view>`** eingegeben wird.

Die Standardkonfiguration der Listenspalten erfolgt über das Element **`<columns>`** . Eine Spalte wird für ein **`<node>`** -Element deklariert, das das Attribut **xpath** enthält, wobei das Feld als Wert im Schema referenziert werden soll.

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

Mit einem Tastaturbefehl können Sie eine Aktion bei der Auswahl der Liste starten. Die Aktion kann ein Eingabeformular oder ein SOAP Aufruf sein.

Befehle können über das Menü **[!UICONTROL Aktion]** der Liste oder die zugehörige Menüschaltfläche aufgerufen werden.

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

Die Beschreibung eines Befehls wird im Element **`<command>`** mit den folgenden Eigenschaften eingegeben:

* **name**: Interner Name des Befehls: Der Name muss eingegeben und eindeutig sein.
* **label**: Titel des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **form**: Formular, das gestartet werden soll: Der einzugebende Wert ist der Identifikationsschlüssel des Formulars (z. B. &quot;cus:recipient&quot;).
* **rights**: Liste der spezifischen Berechtigungen (durch ein Komma getrennt), die den Zugriff auf diesen Befehl ermöglichen. Auf die Liste der verfügbaren Berechtigungen kann über den Ordner **[!UICONTROL Administration > Zugriffe > Spezifische Berechtigungen]** zugegriffen werden.
* **promptLabel**: zeigt vor Ausführung des Befehls ein Bestätigungsfeld an
* **monoSelection**: erzwingt die Mono-Auswahl (standardmäßig mehrere Auswahlmöglichkeiten).
* **refreshView**: erzwingt das erneute Laden der Liste nach Ausführung des Befehls.
* **enabledIf**: Aktiviert den Befehl je nach eingegebenem Ausdruck.
* **img**: gibt ein Bild ein, das den Zugriff auf den Befehl über die Listen-Symbolleiste ermöglicht.

Ein Element **`<command>`** kann **`<command>`** Unterelemente enthalten. In diesem Fall können Sie über das übergeordnete Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument deklariert.

Mithilfe eines Befehlstrennzeichens können Sie eine Trennleiste zwischen Befehlen anzeigen. Sie wird durch den in der Befehlsbeschriftung enthaltenen Wert **&#39;-&#39;** identifiziert.

Das optionale Vorhandensein des **`<soapcall>`** -Tags mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zu SOAP-APIs finden Sie in der [JSAPI-Dokumentation für Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Der Formularkontext kann bei der Initialisierung über das Tag **`<enter>`** aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zum Formular.

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

1. Der Ordner ist eine Ansicht: Die Liste zeigt alle mit dem Schema verknüpften Datensätze an, mit der Möglichkeit, in die Ordnereigenschaften Systemfilter einzugeben.
1. Der Ordner ist verknüpft: Die Datensätze in der Liste werden implizit nach dem Ordner-Link gefiltert.

Für einen verknüpften Ordner muss das Attribut **folderLink** des Elements **`<nodemodel>`** ausgefüllt werden. Dieses Attribut enthält den Namen des Links im Ordner, der im Datenschema konfiguriert ist.

Beispiel einer Deklaration eines verknüpften Ordners im Datenschema:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Die Konfiguration von **`<nodemodel>`** im Link des Ordners &quot;Ordner&quot;sieht wie folgt aus:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
