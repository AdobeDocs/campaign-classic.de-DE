---
product: campaign
title: Campaign Explorer-Navigationsbaum konfigurieren
feature: Application Settings
description: Erfahren Sie, wie Sie den Navigationsbaum von Campaign Explorer konfigurieren
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 1%

---

# Campaign Explorer-Navigationsbaum konfigurieren{#configuration}

Als erfahrener Benutzer können Sie Ordner in der Explorer-Struktur hinzufügen und sie anpassen.

Weitere Informationen zum Campaign-Explorer und zur Navigationshierarchie finden [ in diesem Abschnitt ](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

Die von der Navigationsliste verwendeten Ordnertypen werden in einem XML-Dokument beschrieben, das der Grammatik des Schemas **xtk:navtree** entspricht.

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

Das XML-Dokument enthält das **`<navtree>`** Stammelement mit den Attributen **name** und **namespace**, um den Dokumentnamen und den Namespace anzugeben. Name und Namespace bilden den Identifizierungsschlüssel des Dokuments.

Die globalen Befehle der Anwendung werden im Dokument über das **`<commands>`**-Element deklariert.

Die Deklaration von Dateitypen ist im Dokument mit den folgenden Elementen strukturiert: **`<model>`** und **`<nodemodel>`**.

## Globale Befehle {#global-commands}

Mit einem globalen Befehl können Sie eine Aktion starten. Bei dieser Aktion kann es sich um ein Eingabeformular oder einen SOAP-Aufruf handeln.

Globale Befehle sind über das Hauptmenü **[!UICONTROL Tools]** verfügbar.

Die Struktur der Befehlskonfiguration sieht wie folgt aus:

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

Die Beschreibung eines globalen Befehls wird in das **`<command>`**-Element mit den folgenden Eigenschaften eingegeben:

* **name**: Interner Name des Befehls: Der Name muss eingegeben und eindeutig sein
* **label**: Bezeichnung des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms sichtbar ist.
* **form**: Zu startendes Formular: Der einzugebende Wert ist der Identifizierungsschlüssel des Formulars (z. B. „cus:recipient„)
* **rights**: Liste der spezifischen Berechtigungen (durch Kommas getrennt), die den Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Berechtigungen ist über den Ordner **[!UICONTROL Administration > Zugriffsverwaltung > Spezifische Berechtigungen]** zugänglich.
* **promptLabel**: Zeigt vor Ausführung des Befehls ein Bestätigungsfeld an.

Ein **`<command>`** kann **`<command>`** Unterelemente enthalten. In diesem Fall können Sie mit dem übergeordneten Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt, in der sie im XML-Dokument deklariert sind.

Mit einem Befehlstrennzeichen können Sie eine Trennleiste zwischen Befehlen anzeigen. Er wird durch den Wert **&#39;-&#39;** identifiziert, der in der Befehlsbeschriftung enthalten ist.

Das optionale Vorhandensein des **`<soapcall>`**-Tags mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zur SOAP-API finden Sie in der [Campaign JSAPI-](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Der Formularkontext kann bei Initialisierung über das Tag **`<enter>`** aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zu Formularen.

**Beispiel**:

* Deklaration eines globalen Befehls zum Starten des Formulars „xtk:import“:

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  Ein Tastaturbefehl wird auf dem Zeichen „I“ durch das Vorhandensein von **&amp;** in der Befehlsbeschriftung deklariert.

* Beispiel für ein Untermenü mit einem Trennzeichen:

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

Mit einem Ordnertyp können Sie Zugriff auf die Daten eines Schemas gewähren. Die mit dem Ordner verknüpfte Ansicht besteht aus einer Liste und einem Eingabeformular.

Die Konfigurationsstruktur für den Ordnertyp sieht wie folgt aus:

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

Die Ordnertypdeklaration muss unter einem **`<model>`** Element eingegeben werden. Mit diesem Element können Sie eine hierarchische Organisation definieren, die im Menü **[!UICONTROL Neuen Ordner hinzufügen]** sichtbar ist. Ein **`<model>`** muss **`<nodemodel>`** und andere **`<model>`** Elemente enthalten.

Mit den **name** und **label** werden der interne Name des Elements und die im Menü **[!UICONTROL Neuen Ordner hinzufügen]** angezeigte Beschriftung ausgefüllt.

Das **`<nodemodel>`**-Element enthält die Beschreibung des Ordnertyps mit den folgenden Eigenschaften:

* **name**: Interner Name
* **label**: Bezeichnung, die im Menü **[!UICONTROL Neuen Ordner hinzufügen]** und beim Einfügen eines Ordners als Standardbezeichnung verwendet wird.
* **img**: Standardbild beim Einfügen des Ordners.
* **hiddenCommands**: Liste der Befehle (durch ein Komma getrennt), die maskiert werden sollen. Mögliche Werte: „adbnew“, „adbsave“, „adbcancel“ und „adbdup“.
* **newFolderShortCuts**: Liste der Tastaturbefehle für Modelle (**`<nodemodel>`** durch Kommas getrennt) bei der Ordnererstellung.
* **insertRight**, **editRight**, **deleteRight**: Rechte zum Einfügen, Bearbeiten und Löschen von Ordnern.

Das **`<view>`** Element unter dem **`<nodemodel>`** Element enthält die Konfiguration der Liste, die mit der Ansicht verknüpft ist. Das Schema der Liste wird im Attribut **schema** des **`<view>`** Elements eingegeben.

Um die Datensätze der Liste zu bearbeiten, wird implizit das Eingabeformular mit demselben Namen wie das Listenschema verwendet. Das **type**-Attribut im **`<view>`** wirkt sich auf die Anzeige des Formulars aus. Mögliche Werte:

* **listdet**: Zeigt das Formular am unteren Rand der Liste an.
* **list**: Zeigt die Liste allein an. Das Formular wird durch Doppelklicken oder über das Menü „Öffnen“ bei der Auswahl der Liste gestartet.
* **form**: Zeigt ein schreibgeschütztes Formular an.
* **editForm**: Zeigt ein Formular im Bearbeitungsmodus an.

>[!NOTE]
>
>Der Name des Eingabeformulars kann überladen werden, indem Sie das Attribut **form** in das **`<view>`**-Element eingeben.

Die Standardkonfiguration der Listenspalten wird über das Element **`<columns>`** eingegeben. Eine Spalte wird in einem **`<node>`** deklariert, das das Attribut **xpath** mit dem Feld enthält, auf das in seinem Schema als Wert verwiesen werden soll.

**Beispiel**: Deklaration eines Ordnertyps im Schema „nms:recipient“.

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

Das entsprechende Ordnereinfügemenü:

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

Auf Befehle kann über das Menü **[!UICONTROL Aktion]** der Liste oder die zugehörige Menüschaltfläche zugegriffen werden.

Die Struktur der Befehlskonfiguration sieht wie folgt aus:

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

Die Beschreibung eines Befehls wird mit den folgenden Eigenschaften in das **`<command>`**-Element eingegeben:

* **name**: Interner Name des Befehls: Der Name muss eingegeben und eindeutig sein.
* **label**: Bezeichnung des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms sichtbar ist.
* **form**: Zu startendes Formular: Der einzugebende Wert ist der Identifizierungsschlüssel des Formulars (z. B. „cus:recipient„).
* **rights**: Liste der spezifischen Berechtigungen (durch Kommas getrennt), die den Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Berechtigungen ist über den Ordner **[!UICONTROL Administration > Zugriffsverwaltung > Spezifische Berechtigungen]** zugänglich.
* **promptLabel**: Zeigt vor Ausführung des Befehls ein Bestätigungsfeld an
* **monoSelection**: Erzwingt die Monoauswahl (standardmäßig Mehrfachauswahl).
* **refreshView**: Erzwingt das erneute Laden der Liste nach Ausführung des Befehls.
* **enabledIf**: aktiviert den Befehl in Abhängigkeit vom eingegebenen Ausdruck.
* **img**: Gibt ein Bild ein, das den Zugriff auf den Befehl in der Listen-Symbolleiste ermöglicht.

Ein **`<command>`** kann **`<command>`** Unterelemente enthalten. In diesem Fall können Sie mit dem übergeordneten Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt, in der sie im XML-Dokument deklariert sind.

Mit einem Befehlstrennzeichen können Sie eine Trennleiste zwischen Befehlen anzeigen. Er wird durch den Wert **&#39;-&#39;** identifiziert, der in der Befehlsbeschriftung enthalten ist.

Das optionale Vorhandensein des **`<soapcall>`**-Tags mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zu SOAP-APIs finden Sie in der [Campaign JSAPI-Dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=de).

Der Formularkontext kann bei der Initialisierung über das Tag **`<enter>`** aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zum Eingabeformular.

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

Es gibt zwei Arten von Ordnerverwaltungsvorgängen:

1. Der Ordner ist eine Ansicht: Die Liste zeigt alle mit dem Schema verbundenen Datensätze an, mit der Möglichkeit, die in den Ordnereigenschaften eingegebenen Systemfilter zu filtern.
1. Der Ordner ist verknüpft: Die Datensätze in der Liste werden implizit nach der Ordnerrelation gefiltert.

Für einen verknüpften Ordner muss das **folderLink**-Attribut im **`<nodemodel>`** ausgefüllt werden. Dieses Attribut enthält den Namen der Relation zum Ordner, der im Datenschema konfiguriert wurde.

Beispiel für die Deklaration eines verknüpften Ordners im Datenschema:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Die Konfiguration der **`<nodemodel>`** auf dem Link des Ordners mit dem Namen „Ordner“ ist wie folgt:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
