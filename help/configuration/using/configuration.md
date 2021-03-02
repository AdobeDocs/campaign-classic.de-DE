---
solution: Campaign Classic
product: campaign
title: 'Konfiguration '
description: 'Konfiguration '
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 04b8287dba00adbc391d611cbaf63b36a4bc3d10
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 2%

---


# Konfiguration{#configuration}

Die von der Navigations-Liste verwendeten Ordnertypen werden in einem XML-Dokument beschrieben, das der Grammatik des **xtk:navtree**-Schemas folgt.

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

Das XML-Dokument enthält das Stammelement **`<navtree>`** mit den Attributen **name** und **Namensraum**, um den Dokument und den Namensraum anzugeben. Der Name und der Namensraum bilden den Dokument-Identifizierungsschlüssel.

Die globalen Befehle der Anwendung werden im Dokument aus dem Element **`<commands>`** deklariert.

Die Deklaration von Dateitypen ist im Dokument mit den folgenden Elementen strukturiert: **`<model>`** und **`<nodemodel>`**.

## Globale Befehle {#global-commands}

Mit einem globalen Befehl können Sie eine Aktion starten. Bei dieser Aktion kann es sich um ein Eingabefeld oder einen SOAP-Aufruf handeln.

Globale Befehle können über das Hauptmenü **[!UICONTROL Tools]** aufgerufen werden.

Die Befehlskonfigurationsstruktur lautet wie folgt:

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

* **name**: Interner Name des Befehls: der Name muss eingegeben und eindeutig
* **label**: Beschriftung des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **form**: Formular, das gestartet werden soll: der einzugebende Wert ist der Identifizierungsschlüssel des Eingabedrucks (z. &quot;cus:Empfänger&quot;)
* **Rechte**: Liste von Spezifische Berechtigungen (durch Kommas getrennt), die Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Rechte ist über den Ordner **[!UICONTROL Administration > Zugriffsverwaltung > Spezifische Berechtigungen]** verfügbar.
* **promptLabel**: zeigt ein Bestätigungsfeld vor Ausführung des Befehls an.

Ein **`<command>`**-Element kann **`<command>`**-Unterelemente enthalten. In diesem Fall können Sie mit dem übergeordneten Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument.

Mithilfe einer Befehlstrennlinie können Sie eine Trennleiste zwischen Befehlen anzeigen. Er wird durch den in der Befehlsbeschriftung enthaltenen Wert **&#39;-&#39;** identifiziert.

Das optionale Vorhandensein des Tags **`<soapcall>`** mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zur SOAP-API finden Sie in der JSAPI-Dokumentation [Kampagne](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Der Formularkontext kann bei der Initialisierung vom **`<enter>`**-Tag aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zu den Eingabeformularen.

**Beispiel**:

* Erklärung eines globalen Befehls zum Starten des Formulars &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Ein Tastaturbefehl wird auf dem &quot;I&quot;-Zeichen durch **&amp;** in der Befehlsbezeichnung deklariert.

* Beispiel eines Untermenüs mit einer Trennlinie:

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

Mit einem Ordnertyp können Sie Zugriff auf die Daten eines Schemas gewähren. Die mit dem Ordner verknüpfte Ansicht besteht aus einer Liste und einem Eingabedatum.

Die Konfigurationsstruktur des Ordnertyps lautet wie folgt:

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

Die Deklaration des Ordnertyps muss unter einem **`<model>`**-Element eingegeben werden. Mit diesem Element können Sie eine hierarchische Organisation definieren, die im Menü **[!UICONTROL Hinzufügen neuer Ordner]** angezeigt wird. Ein **`<model>`**-Element muss **`<nodemodel>`**-Elemente und andere **`<model>`**-Elemente enthalten.

Die Attribute **name** und **label** füllen den internen Namen des Elements und die im Menü **[!UICONTROL Hinzufügen neuer Ordner]** angezeigte Bezeichnung aus.

Das **`<nodemodel>`**-Element enthält die Beschreibung des Ordnertyps mit den folgenden Eigenschaften:

* **name**: interner Name
* **label**: -Beschriftung im  **[!UICONTROL Hinzufügen neuen]** Ordnermenü und als Standardbeschriftung beim Einfügen eines Ordners verwendet.
* **img**: Standardbild beim Einfügen des Ordners.
* **hiddenCommands**: Liste der zu maskierenden Befehle (durch Kommas getrennt). Mögliche Werte: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; und &quot;adbdup&quot;.
* **newFolderShortCuts**: Liste von Tastaturbefehlen auf Modellen (durch Kommas **`<nodemodel>`** getrennt) bei der Ordnererstellung.
* **insertRight**,  **editRight**,  **deleteRight**: Rechte zum Einfügen, Bearbeiten und Löschen von Ordnern.

Das Element **`<view>`** unter dem Element **`<nodemodel>`** enthält die Konfiguration der mit der Ansicht verknüpften Liste. Das Schema der Liste wird im Attribut **Schema** des Elements **`<view>`** eingetragen.

Zur Bearbeitung der Datensätze der Liste wird implizit das Eingabedatum mit demselben Namen wie das Liste-Schema verwendet. Das **type**-Attribut des **`<view>`**-Elements wirkt sich auf die Anzeige des Formulars aus. Mögliche Werte:

* **listdet**: zeigt das Formular unten in der Liste an.
* **Liste**: zeigt nur die Liste an. Das Formular wird durch Dublette-Klick oder über die &quot;Öffnen&quot; im Menü zur Auswahl der Liste gestartet.
* **form**: zeigt ein schreibgeschütztes Formular an.
* **editForm**: zeigt ein Formular im Bearbeitungsmodus an.

>[!NOTE]
>
>Der Name des Eingabefelds kann überladen werden, indem Sie das Attribut **form** in das Element **`<view>`** eingeben.

Die Standardkonfiguration der Spalten &quot;Liste&quot;wird über das Element **`<columns>`** eingegeben. Eine Spalte wird für ein **`<node>`**-Element deklariert, das das **xpath**-Attribut enthält, wobei das Feld in seinem Schema als Wert referenziert werden muss.

**Beispiel**: Deklaration eines Ordnertyps im Schema &quot;nms:Empfänger&quot;.

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

### Tastenkombinationsbefehle {#shortcut-commands}

Mit einem Tastaturbefehl können Sie eine Aktion beim Auswählen der Liste starten. Die Aktion kann ein Eingabedatum oder ein SOAP-Aufruf sein.

Befehle können über das Menü **[!UICONTROL Aktion]** der Liste oder der zugehörigen Menüschaltfläche aufgerufen werden.

Die Befehlskonfigurationsstruktur lautet wie folgt:

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

* **name**: Interner Name des Befehls: der Name muss eingegeben und eindeutig sein.
* **label**: Beschriftung des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **form**: Formular, das gestartet werden soll: der einzugebende Wert ist der Identifizierungsschlüssel des Eingabedrucks (z. &quot;cus:Empfänger&quot;).
* **Rechte**: Liste von Spezifische Berechtigungen (durch Kommas getrennt), die Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Rechte ist über den Ordner **[!UICONTROL Administration > Zugriffsverwaltung > Spezifische Berechtigungen]** verfügbar.
* **promptLabel**: zeigt ein Bestätigungsfeld vor Ausführung des Befehls an
* **monoSelection**: erzwingt die Mono-Auswahl (standardmäßig mehrere Auswahlen).
* **refreshView**: erzwingt das erneute Laden der Liste nach Ausführung des Befehls.
* **enabledIf**: aktiviert den Befehl je nach eingegebenem Ausdruck.
* **img**: gibt ein Bild ein, das den Zugriff auf den Befehl über die Werkzeugleiste &quot;Liste&quot;ermöglicht.

Ein **`<command>`**-Element kann **`<command>`**-Unterelemente enthalten. In diesem Fall können Sie mit dem übergeordneten Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument.

Mithilfe einer Befehlstrennlinie können Sie eine Trennleiste zwischen Befehlen anzeigen. Er wird durch den in der Befehlsbeschriftung enthaltenen Wert **&#39;-&#39;** identifiziert.

Das optionale Vorhandensein des Tags **`<soapcall>`** mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zu SOAP-APIs finden Sie in der JSAPI-Dokumentation [Kampagne](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Der Formularkontext kann bei der Initialisierung über das **`<enter>`**-Tag aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zum Eingabefeld.

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

1. Der Ordner ist eine Ansicht: Die Liste zeigt alle mit dem Schema verknüpften Datensätze an, mit der Möglichkeit, dass das System in die Ordnereigenschaften gefiltert werden kann.
1. Der Ordner ist verknüpft: die Datensätze in der Liste implizit auf dem Ordnerlink gefiltert werden.

Bei einem verknüpften Ordner muss das **folderLink**-Attribut des **`<nodemodel>`**-Elements ausgefüllt werden. Dieses Attribut enthält den Namen des Links im Schema, der im Datenverzeichnis konfiguriert ist.

Beispiel für die Deklaration eines verknüpften Ordners im Schema data:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Die Konfiguration von **`<nodemodel>`** auf dem Link des Ordners &quot;folder&quot; lautet wie folgt:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

