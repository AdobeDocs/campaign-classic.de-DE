---
title: 'Konfiguration '
seo-title: 'Konfiguration '
description: 'Konfiguration '
seo-description: null
page-status-flag: never-activated
uuid: 0f2aadc3-5199-476c-9956-6e39b899a7d0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: b781fd52-828c-4582-a546-a1fee7e5a26d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# Konfiguration{#configuration}

Die von der Navigationsliste verwendeten Ordnertypen werden in einem XML-Dokument beschrieben, das der Grammatik des **xtk:navtree** -Schemas folgt.

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

Das XML-Dokument enthält das **`<navtree>`** Stammelement mit den Attributen **name** und **namespace** , um den Dokumentnamen und den Namespace anzugeben. Der Name und der Namespace bilden den Dokumentkennungsschlüssel.

Die globalen Befehle der Anwendung werden im Dokument aus dem **`<commands>`** Element deklariert.

Die Deklaration der Dateitypen ist im Dokument mit den folgenden Elementen strukturiert: **`<model>`** und **`<nodemodel>`**.

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

Die Beschreibung eines globalen Befehls wird in das **`<command>`** Element mit den folgenden Eigenschaften eingegeben:

* **name**: Interner Name des Befehls: der Name muss eingegeben und eindeutig
* **label**: Beschriftung des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **form**: Formular, das gestartet werden soll: der einzugebende Wert ist der Identifizierungsschlüssel des Eingabedrucks (z. &quot;cus:empfänger&quot;)
* **Rechte**: Liste der benannten Rechte (durch Kommas getrennt), die Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Rechte kann aus dem **[!UICONTROL Administration > Access management > Named rights]** Ordner abgerufen werden.
* **promptLabel**: zeigt ein Bestätigungsfeld vor Ausführung des Befehls an.

Ein **`<command>`** Element kann **`<command>`** Unterelemente enthalten. In diesem Fall können Sie mit dem übergeordneten Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument.

Mithilfe einer Befehlstrennlinie können Sie eine Trennleiste zwischen Befehlen anzeigen. Er wird durch den **&#39;-&#39;** Wert in der Befehlsbeschriftung identifiziert.

Das optionale Vorhandensein des **`<soapcall>`** -Tags mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zur SOAP-API finden Sie in der JSAPI-Dokumentation von [Campaign](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html).

Der Formularkontext kann bei der Initialisierung vom **`<enter>`** Tag aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zu den Eingabeformularen.

**Beispiel**:

* Erklärung eines globalen Befehls zum Starten des Formulars &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Ein Tastaturbefehl wird auf dem &quot;I&quot;-Zeichen durch das Vorhandensein von **&amp;** in der Befehlszeile deklariert.

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

Mit einem Ordnertyp können Sie Zugriff auf die Daten eines Schemas gewähren. Die mit dem Ordner verknüpfte Ansicht besteht aus einer Liste und einem Eingabefeld.

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

Die Deklaration des Ordnertyps muss unter einem **`<model>`** Element eingegeben werden. Mit diesem Element können Sie eine hierarchische Organisation definieren, die im **[!UICONTROL Add new folder]** Menü sichtbar ist. Ein **`<model>`** Element muss **`<nodemodel>`** Elemente und andere **`<model>`** Elemente enthalten.

Die **Attribute für Name** und **Bezeichnung** füllen den internen Namen des Elements und die im **[!UICONTROL Add new folder]** Menü angezeigte Bezeichnung aus.

Das **`<nodemodel>`** -Element enthält die Beschreibung des Ordnertyps mit den folgenden Eigenschaften:

* **name**: interner Name
* **label**: -Beschriftung im **[!UICONTROL Add new folder]** Menü und als Standardbeschriftung beim Einfügen eines Ordners verwendet.
* **img**: Standardbild beim Einfügen des Ordners.
* **hiddenCommands**: Liste der zu maskierenden Befehle (durch Kommas getrennt). Mögliche Werte: &quot;insert&quot;, &quot;delete&quot;, &quot;update&quot; und &quot;duplicate&quot;.
* **newFolderShortCuts**: Liste der Tastaturbefehle auf Modellen (durch Kommas **`<nodemodel>`** getrennt) bei der Ordnererstellung.
* **insertRight**, **editRight**, **deleteRight**: Rechte zum Einfügen, Bearbeiten und Löschen von Ordnern.

Das **`<view>`** Element unter dem **`<nodemodel>`** Element enthält die Konfiguration der Liste, die der Ansicht zugeordnet ist. Das Schema der Liste wird im **Schemaattribut** des **`<view>`** Elements eingegeben.

Zur Bearbeitung der Datensätze der Liste wird implizit das Eingabedatum mit demselben Namen wie das Listenschema verwendet. Das **type** -Attribut des **`<view>`** Elements wirkt sich auf die Anzeige des Formulars aus. Mögliche Werte:

* **listdet**: zeigt das Formular unten in der Liste an.
* **list**: zeigt nur die Liste an. Das Formular wird durch Doppelklick oder über die Option &quot;Öffnen&quot;im Menü zur Auswahl der Liste gestartet.
* **form**: zeigt ein schreibgeschütztes Formular an.
* **editForm**: zeigt ein Formular im Bearbeitungsmodus an.

>[!NOTE]
>
>Der Name des Eingabefelds kann durch Eingabe des **form** -Attributs in das **`<view>`** Element überladen werden.

Die Standardkonfiguration der Listenspalten wird über das **`<columns>`** Element eingegeben. Eine Spalte wird für ein **`<node>`** Element deklariert, das das Attribut **xpath** enthält, wobei das Feld als Wert im Schema referenziert werden muss.

**Beispiel**: Deklaration eines Ordnertyps im Schema &quot;nms:empfänger&quot;.

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

Beim Laden der Liste können Filter und Sortierung angewendet werden:

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

Mit einem Tastaturbefehl können Sie eine Aktion beim Auswählen der Liste starten. Die Aktion kann ein Eingabedatum oder ein SOAP-Aufruf sein.

Befehle können über das **[!UICONTROL Action]** Menü der Liste oder die zugehörige Menüschaltfläche aufgerufen werden.

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

Die Beschreibung eines Befehls wird im **`<command>`** Element mit den folgenden Eigenschaften eingegeben:

* **name**: Interner Name des Befehls: der Name muss eingegeben und eindeutig sein.
* **label**: Beschriftung des Befehls.
* **desc**: Beschreibung, die in der Statusleiste des Hauptbildschirms angezeigt wird.
* **form**: Formular, das gestartet werden soll: der einzugebende Wert ist der Identifizierungsschlüssel des Eingabedrucks (z. &quot;cus:empfänger&quot;).
* **Rechte**: Liste der benannten Rechte (durch Kommas getrennt), die Zugriff auf diesen Befehl ermöglichen. Die Liste der verfügbaren Rechte kann aus dem **[!UICONTROL Administration > Access management > Named rights]** Ordner abgerufen werden.
* **promptLabel**: zeigt ein Bestätigungsfeld vor Ausführung des Befehls an
* **monoSelection**: erzwingt die Mono-Auswahl (standardmäßig mehrere Auswahlen).
* **refreshView**: erzwingt das erneute Laden der Liste nach Ausführung des Befehls.
* **enabledIf**: Aktiviert den Befehl abhängig vom eingegebenen Ausdruck.
* **img**: gibt ein Bild ein, das den Zugriff auf den Befehl in der Symbolleiste der Liste ermöglicht.

Ein **`<command>`** Element kann **`<command>`** Unterelemente enthalten. In diesem Fall können Sie mit dem übergeordneten Element ein Untermenü anzeigen, das aus diesen untergeordneten Elementen besteht.

Die Befehle werden in derselben Reihenfolge angezeigt wie im XML-Dokument.

Mithilfe einer Befehlstrennlinie können Sie eine Trennleiste zwischen Befehlen anzeigen. Er wird durch den **&#39;-&#39;** Wert in der Befehlsbeschriftung identifiziert.

Das optionale Vorhandensein des **`<soapcall>`** -Tags mit seinen Eingabeparametern definiert den Aufruf einer auszuführenden SOAP-Methode. Weitere Informationen zu SOAP-APIs finden Sie in der JSAPI-Dokumentation von [Campaign](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html).

Der Formularkontext kann bei der Initialisierung über das **`<enter>`** Tag aktualisiert werden. Weitere Informationen zu diesem Tag finden Sie in der Dokumentation zum Eingabefeld.

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

1. Der Ordner ist eine Ansicht: In der Liste werden alle mit dem Schema verknüpften Datensätze angezeigt, wobei die Möglichkeit besteht, dass das System in die Ordnereigenschaften gefiltert wird.
1. Der Ordner ist verknüpft: die Datensätze in der Liste werden implizit auf dem Ordnerlink gefiltert.

Bei einem verknüpften Ordner muss das Attribut **folderLink** des **`<nodemodel>`** Elements ausgefüllt werden. Dieses Attribut enthält den Namen des Links im Ordner, der im Datenschema konfiguriert ist.

Beispiel für die Deklaration eines verknüpften Ordners im Datenschema:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Die Konfiguration der **`<nodemodel>`** auf dem Link des Ordners &quot;folder&quot;lautet wie folgt:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

