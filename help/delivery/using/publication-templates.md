---
title: Publikationsvorlagen
seo-title: Publikationsvorlagen
description: Publikationsvorlagen
seo-description: null
page-status-flag: never-activated
uuid: 1976f70c-b2d8-44ca-8fc3-6451fb67d18b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 279b0ae6-2578-4f1f-af59-13a1a9c80b32
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Publikationsvorlagen{#publication-templates}

## Über Publikationsvorlagen {#about-publication-templates}

Die Publikationsvorlage stellt den Steckbrief des zu publizierenden Inhalts dar. Sie verweist auf alle für die Publikation erforderlichen Ressourcen:

* das Datenschema,
* das Formular,
* die Umwandlungsvorlagen für jedes Ausgabedokument.

## Identifizierung von Publikationsvorlagen {#identification-of-a-publication-template}

Eine Publikationsvorlage wird über ihren Namen und Namensraum identifiziert.

Der Identifikationsschlüssel eines Stylesheets ist eine Zeichenkette, die den Namensraum und den Namen enthält, getrennt durch das Zeichen &#39;:&#39; (z. B. **cus:newsletter**).

>[!NOTE]
>
>Es wird empfohlen, für Schema, Formular und Publikationsvorlage den gleichen Schlüssel zu verwenden.

## Erstellung und Konfiguration der Vorlagen {#creating-and-configuring-the-template}

Veröffentlichungsvorlagen werden standardmäßig im **[!UICONTROL Administration > Configuration > Publication templates]** Knoten gespeichert. Um eine neue Vorlage zu erstellen, klicken Sie auf die **[!UICONTROL New]** Schaltfläche über der Liste der Vorlagen.

Geben Sie den Namen der Vorlage (d. h. den aus Namensraum und Namen bestehenden Identifikationsschlüssel), den Titel, das zugeordnete Datenschema sowie das entsprechende Formular an.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>Bei Erstellung eines auf dieser Publikationsvorlage beruhenden Inhalts wird der hier vergebene Titel angezeigt.

The **Check status to validate content generation** option forces a check on the &quot;Validated&quot; status of the content instances to authorize file generation. For more on this, refer to [Publication](#publication).

Für jedes Ausgabeformat muss eine Umwandlungsvorlage hinzugefügt werden. Es können so viele Umwandlungsvorlagen wie nötig erstellt werden.

Das **[!UICONTROL Name of template]** Feld ist eine kostenlose Beschriftung, die den Rendertyp bei der Ausgabe beschreibt. Die Veröffentlichungseinstellungen stehen für jede Transformationsvorlage auf den Registerkarten zur Verfügung.

### Rendering {#rendering}

The **[!UICONTROL Rendering]** tab, choose:

* den Typ der Umwandlungsvorlage: XSL-Stylesheet oder JavaScript-Template;
* das Format des Ausgabedokuments: HTML, Text, XML oder RTF;
* den Namen der Vorlage, die die Umwandlungsinformationen enthält, d. h. des Stylesheets oder des JavaScript-Templates.

### Publikation {#publication}

Publication involves generating the output document in the form of a file, if the type selected is **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

Des Weiteren können folgende Publikationsparameter konfiguriert werden:

* Der Zeichensatz für die Ausgabedateikodierung kann über das **[!UICONTROL Encoding]** Feld erzwungen werden. Der Zeichensatz Latein 1 (1252) wird standardmäßig verwendet.
* Die **[!UICONTROL Multi-file generation]** Option aktiviert einen speziellen Veröffentlichungsmodus für Dokumente. Diese Option besteht darin, ein Partitionierungs-Tag am Anfang jeder Seite des Ausgabedokuments zu füllen. Beim Generieren des Inhalts wird für jedes ausgefüllte Partitionierungs-Tag eine Datei erzeugt. Dieser Modus wird verwendet, um Mini-Sites aus einem Inhaltsblock zu generieren. for more on this, refer to [Multi-file generation](#multi-file-generation).
* Das **[!UICONTROL Location]** Feld enthält den Namen der Ausgabedatei. Der Name kann aus Variablen bestehen, um einen automatischen Dateinamen zu generieren.

   A variable is populated with the following format: **`$(<xpath>)`, where `<xpath>` is the path of a field of the publication template data schema.

   Beispielsweise kann der Dateiname auf ein Datumsfeld verweisen. In diesem Fall ist die Funktion **$date-format** zu verwenden und Feldpfad sowie Ausgabeformat sind anzugeben.

   Standardmäßig wird der Dateiname unter Verwendung der Variablen &quot;@name&quot; und &quot;@date&quot; konstruiert:

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   Der Dateiname nimmt somit folgende Form an: ct_news12_20110901.htm.

   >[!NOTE]
   >
   >Weitere Informationen zur Inhaltserstellung finden Sie unter [Erstellen einer Inhaltsinstanz](../../delivery/using/using-a-content-template.md#creating-a-content-instance).

### Versand {#delivery}

In diesem Tab kann eine Versandvorlage ausgewählt werden, um direkt einen Versand mit dem erstellten Inhalt durchzuführen. Der E-Mail-Inhalt wird automatisch in den konfigurierten Formaten - HTML oder Text - eingefügt.

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>For an example of delivery creation based on a content, refer to [Delivering a content instance](../../delivery/using/using-a-content-template.md#delivering-a-content-instance).

### Aggregator {#aggregator}

Sie können das XML-Ausgabedokument durch die Aggregation von Daten mithilfe eines Scripts oder einer Abfragenliste anreichern. Ziel ist es, gewisse referenzierte Informationen durch Links oder Elemente aus der Datenbank zu ergänzen.

### Multidatei-Erzeugung {#multi-file-generation}

Um mehrere Dateigenerationen zu aktivieren, wählen Sie die **[!UICONTROL Multi-file generation]** Option im Veröffentlichungsmodell aus. Mit dieser Option können Sie Partitionierungs-Tags am Anfang jeder Seite des Ausgabedokuments im Stylesheet angeben. Die Generierung des Inhalts erzeugt eine Datei für jedes aufgetretene Partitionierungstag.

Das zu verwendende Trennzeichen stellt sich wie folgt dar:

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** wobei **`<name_of_file>`** der Dateiname der zu generierenden Seite ist.

**Beispiel:**Generieren mehrerer Dateien mit dem Schema &quot;cus:book&quot;

Ziel ist es, eine Hauptseite zu erzeugen, die die Kapitel auflistet und die Möglichkeit bietet, die Details der Kapitel in einer externen Seite anzuzeigen.

![](assets/d_ncs_content_chunk.png)

Das entsprechende Stylesheet (&quot;cus:Buch.xsl&quot;) stellt sich wie folgt dar:

```
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

Ein zweites Stylesheet (&quot;cus:Kapitel.xsl&quot;) ist erforderlich, um die Kapiteldetails zu erzeugen:

```
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

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

The filename is constructed with the **$(path)** variable containing the publication path and **`<xsl:value-of select="@id" />`**, which matches the identifier of the chapter in the input document.

In der Publikationsvorlage müssen beide Stylesheets &quot;cus:Buch.xsl&quot; und &quot;cus:Kapitel.xsl&quot; angegeben werden.

The **[!UICONTROL Multi-file generation]** option must be active on the chapter transformation model:

![](assets/d_ncs_content_chunk2.png)

The **[!UICONTROL Location]** field is not used in the generation of multiple files, but you must still populate this field to avoid an error when publishing.
