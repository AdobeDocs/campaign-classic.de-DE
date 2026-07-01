---
product: campaign
title: Veröffentlichungsvorlagen
description: Veröffentlichungsvorlagen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Templates
role: User
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
TQID: https://experienceleague.adobe.com/mU7usRNlg73dYQS1PuorYpp9g4d7bNXAWBtIEE1VULk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 844
ht-degree: 100%

---

# Veröffentlichungsvorlagen{#publication-templates}

## Über Veröffentlichungsvorlagen {#about-publication-templates}

Die Publikationsvorlage verweist auf die im Veröffentlichungsprozess verwendeten Ressourcen, d. h.:

* das Datenschema,
* das Formular,
* die Umwandlungsvorlagen für jedes Ausgabedokument.

## Identifizierung von Veröffentlichungsvorlagen {#identification-of-a-publication-template}

Eine Veröffentlichungsvorlage wird über ihren Namen und Namespace identifiziert.

Der Identifikationsschlüssel eines Stylesheets ist ein String, der den Namespace und den Namen enthält, getrennt durch einen Doppelpunkt (z. B. **cus:newsletter**).

>[!NOTE]
>
>Es wird empfohlen, für Schema, Formular und Veröffentlichungsvorlage den gleichen Schlüssel zu verwenden.

## Erstellen und Konfigurieren der Vorlage {#creating-and-configuring-the-template}

Standardmäßig werden Veröffentlichungsvorlagen im Knoten **[!UICONTROL Administration > Konfiguration > Veröffentlichungsvorlagen]** gespeichert. Klicken Sie dort zur Erstellung einer neuen Vorlage auf die Schaltfläche **[!UICONTROL Neu]**.

Geben Sie den Namen der Vorlage (d. h. den aus Namespace und Namen bestehenden Identifikationsschlüssel), den Titel, das zugeordnete Datenschema sowie das entsprechende Formular an.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>Bei Erstellung eines auf dieser Veröffentlichungsvorlage beruhenden Inhalts wird der hier vergebene Titel angezeigt.

Die Option **Zur Erstellung des Inhalts Status prüfen** stellt sicher, dass die Inhaltsinstanzen den Status „Validiert“ aufweisen, bevor die Datei erzeugt wird. Weitere Informationen hierzu finden Sie im Abschnitt [Veröffentlichung](#publication).

Für jedes Ausgabedokument muss eine Umwandlungsvorlage hinzugefügt werden. Sie können so viele Umwandlungsvorlagen wie nötig erstellen.

Im Feld **[!UICONTROL Vorlagenname]** wird ein frei wählbarer Titel angegeben, der das Rendering des Ausgabedokuments beschreibt. Für jede Umwandlungsvorlage sind die Veröffentlichungseinstellungen in den Registerkarten verfügbar.

### Rendering {#rendering}

Konfigurieren Sie im **[!UICONTROL Rendering]**-Tab folgende Parameter:

* den Typ der Umwandlungsvorlage: XSL-Stylesheet oder JavaScript-Template;
* das Format des Ausgabedokuments: HTML, Text, XML oder RTF;
* den Namen der Vorlage, die die Umwandlungsinformationen enthält, d. h. des Stylesheets oder des JavaScript-Templates.

### Veröffentlichung {#publication}

Veröffentlichung bezeichnet den Vorgang der Erzeugung des Ausgabedokuments in Form einer Datei. Wählen Sie hierzu im gleichnamigen Tab im Feld Typ die Option **[!UICONTROL Datei]**.

![](assets/d_ncs_content_model2.png)

Des Weiteren können folgende Veröffentlichungsparameter konfiguriert werden:

* Den Zeichensatz für die Codierung der Ausgabedatei können Sie mithilfe des Felds **[!UICONTROL Codierung]** erzwingen. Standardmäßig wird der Zeichensatz „Latin 1 (1252)“ verwendet.
* Mit der Option **[!UICONTROL Multidatei-Erzeugung]** wird ein spezieller Modus für die Veröffentlichung von Dokumenten aktiviert. Bei dieser Option wird am Anfang jeder Seite des Ausgabedokuments ein Partitionierungs-Tag eingefügt. Durch Generieren des Inhalts wird eine Datei für jedes ausgefüllte Partitionierungs-Tag erstellt. Dieser Modus wird verwendet, um aus einem Inhaltsbaustein Mini-Sites zu generieren. Weitere Informationen hierzu finden Sie im Abschnitt [Multidatei-Erzeugung](#multi-file-generation).
* Das Feld **[!UICONTROL Speicherort]** enthält den Namen der Ausgabedatei. Sie können den Namen aus Variablen zusammensetzen, um den Dateinamen automatisch zu generieren.

  Die Variablen sind wie folgt anzugeben: **`$(<xpath>)`**, wobei **`<xpath>`** den Pfad eines Felds des der Veröffentlichungsvorlage zugrunde liegenden Datenschemas bezeichnet.

  Beispielsweise kann der Dateiname auf ein Datumsfeld verweisen. In diesem Fall ist die Funktion **$date-format** zu verwenden und Feldpfad sowie Ausgabeformat sind anzugeben.

  Standardmäßig wird der Dateiname unter Verwendung der Variablen &quot;@name&quot; und &quot;@date&quot; konstruiert:

  ```xml
  ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
  ```

  Der Dateiname nimmt somit folgende Form an: ct_news12_20110901.htm.

  >[!NOTE]
  >
  >Weitere Informationen zur Inhaltserstellung finden Sie unter [Erstellen einer Inhaltsinstanz](using-a-content-template.md#creating-a-content-instance).

### Versand {#delivery}

In dieser Registerkarte können Sie ein Szenario auswählen, um einen Versand direkt mit dem Inhalt zu starten. Der Inhalt der E-Mail wird automatisch basierend auf dem Ausgabeformat (HTML oder Text) ausgefüllt.

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>Ein Beispiel für eine Versanderstellung basierend auf Inhalten finden Sie im Abschnitt [Versenden einer Inhaltsinstanz](using-a-content-template.md#delivering-a-content-instance).

### Aggregator {#aggregator}

Sie können das XML-Ausgabedokument durch die Aggregation von Daten mithilfe eines Skripts oder einer Abfrageliste anreichern. Ziel ist es, bestimmte durch Links referenzierte Informationen zu ergänzen oder Elemente aus der Datenbank hinzuzufügen.

### Multidatei-Erzeugung {#multi-file-generation}

Um die Generierung mehrerer Dateien zu aktivieren, wählen Sie im Veröffentlichungsmodell die Option **[!UICONTROL Multidatei-Erzeugung]** aus. Mit dieser Option können Sie im Stylesheet Partitionierungs-Tags für den Beginn jeder Seite des Ausgabedokuments angeben. Bei der Inhaltserstellung wird für jedes vorhandene Partitionierungs-Tag eine Datei erstellt.

Das zu verwendende Trennzeichen stellt sich wie folgt dar:

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`**, wobei **`<name_of_file>`** der Dateiname der zu erzeugenden Seite ist.

**Beispiel:** Multidatei-Erzeugung mit dem Schema „cus:book“.

Ziel ist es, eine Hauptseite zu erzeugen, die die Kapitel auflistet und die Möglichkeit bietet, die Details der Kapitel in einer externen Seite anzuzeigen.

![](assets/d_ncs_content_chunk.png)

Das entsprechende Stylesheet („cus:book.xsl“) lautet wie folgt:

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Ein zweites Stylesheet („cus:chapter.xsl“) ist erforderlich, um die Details der Kapitel zu generieren:

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

Das Trennzeichen wird zu Beginn jeder Seite angegeben, die in die zu erzeugende Datei einzuschließen ist.

```xml
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

Der Dateiname wird mit der Variable **$(path)** konstruiert, welche den Veröffentlichungspfad bezeichnet, ergänzt durch **`<xsl:value-of select="@id" />`**, was der Kennung des Kapitels im Quelldokument entspricht.

Das Veröffentlichungsmodell muss mit den beiden Stylesheets „cus:book.xsl“ und „cus:chapter.xsl“ gefüllt werden.

In der Umwandlungsvorlage der Kapitel ist die Option **[!UICONTROL Multidatei-Erzeugung]** zu aktivieren:

![](assets/d_ncs_content_chunk2.png)

Auch wenn das Feld **[!UICONTROL Speicherort]** bei der Multidatei-Erzeugung nicht verwendet wird, muss ein Dateiname angegeben werden, um eine Fehlermeldung bei der Veröffentlichung zu vermeiden.
