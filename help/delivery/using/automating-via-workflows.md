---
title: Automatisierung mit Workflows
seo-title: Automatisierung mit Workflows
description: Automatisierung mit Workflows
seo-description: null
page-status-flag: never-activated
uuid: c77e8b2b-2a2c-4c6e-8497-662e7269e226
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 4abce633-647f-4ae4-9419-859f6e2e8628
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 100%

---


# Automatisierung mit Workflows{#automating-via-workflows}

## Inhaltsverwaltungsaktivitäten {#content-management-activity}

Die Erstellung, Bearbeitung und Publikation von Inhalten kann mithilfe eines in der Adobe-Campaign-Clientkonsole konfigurierten Workflows automatisiert werden.

Die Aktivität **Content Management** ist in der **[!UICONTROL Werkzeug]**-Symbolleiste des Workflow-Diagramms enthalten.

Vier Aktivitätseigenschaften sind zu konfigurieren:

* **[!UICONTROL Inhalt]** - Auswahl eines existierenden oder Erstellung eines neuen Inhalts;
* **[!UICONTROL Inhalt aktualisieren]** - Änderung des Betreffs oder Aktualisierung des Inhalts mit einem XML-Stream;
* **[!UICONTROL Auszuführende Aktion]** - Speicherung oder Erzeugung des Inhalts;
* **[!UICONTROL Transition]** - Erzeugung und Benennung einer ausgehenden Transition.

![](assets/d_ncs_content_wf.png)

### Content {#content}

* **Wird durch die Transition angegeben**

   Der zu verwendende Inhalt wurde zuvor erstellt, die Bearbeitungsvorgänge beziehen sich auf die Inhaltsinstanz, welche vom Eingangsereignis übernommen wurde. Auf die Kennung des Inhalts kann über die Variable &quot;contentId&quot; des Ereignisses zugegriffen werden.

* **Explizit**

   Ermöglicht die Auswahl eines zuvor erstellten Inhalts.

* **Wird durch ein Script erstellt**

   Wählt eine Inhaltsinstanz ausgehend von einem JavaScript-Template aus. Der auszuwertende Code ermöglicht den Abruf der Inhaltskennung.

* **Neu, basierend auf einer Publikationsvorlage erstellt**

   Erstellt einen neuen Inhalt ausgehend von einer Publikationsvorlage. Die Inhaltsinstanz wird im angegebenen &quot;Inhaltskanal&quot;-Ordner gespeichert.

### Inhalt aktualisieren {#update-the-content}

* **Betreff**

   Ermöglicht bei der Publikation die Anpassung des Versandbetreffs.

* **Zugriff auf Daten eines XML-Streams**

   Der Inhalt wird mit einem XML-Stream aktualisiert, der aus einer externen Quelle stammt. Zum Download der Daten muss die entsprechende URL angegeben werden.

   Mithilfe eines XSL-Stylesheets können dann die eingehenden XML-Daten umgewandelt werden.

### Auszuführende Aktion {#action-to-execute}

* **Speichern**

   Speichert den erstellten oder geänderten Inhalt. Die Kennung des Inhalts wird in der Variablen &quot;contentID&quot; des ausgehenden Ereignisses übernommen.

* **Erzeugen**

   Erzeugt die Ausgabedateien für jede Publikationsvorlage mit Typ &quot;Datei&quot;. Die ausgehende Transition wird für jede erzeugte Datei aktiviert, wobei die in der Variablen &quot;contentID&quot; gespeicherte Inhaltskennung und der in der Variable &quot;filename&quot; gespeicherte Dateiname als Parameter übergeben werden.

### Transition {#transition}

Die Option **Ausgehende Transition erzeugen** fügt der Aktivität **[!UICONTROL Content Management]** eine Transition hinzu, damit der Workflow mit einer neuen Aktivität fortgesetzt werden kann. Wenn Sie diese Option ankreuzen, ist die Angabe eines Titels für die Transition erforderlich.

## Beispiele  {#examples}

### Erstellung und Versand eines Inhalts automatisieren {#automating-content-creation-and-delivery}

Folgender Workflow automatisiert die Erstellung und den Versand eines Inhalts:

![](assets/d_ncs_content_workflow2.png)

Der Inhalt wird in der Aktivität &quot;Content Management&quot; konfiguriert:

![](assets/d_ncs_content_workflow3.png)

Ausgehend von der Publikationsvorlage wird im Inhaltskanal-Ordner eine neue Inhaltsinstanz erstellt.

Im vorliegenden Beispiel wurde der Versandbetreff überschrieben. Er ersetzt den in der Versandvorlage der **[!UICONTROL Versand]**-Aktivität angegebenen Betreff.

Der Inhalt wird automatisch durch den von der angegebenen URL heruntergeladenen XML-Stream ergänzt:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

Das Datenformat stimmt nicht mit dem Datenschema überein, das in der Publikationsvorlage eingegeben wurde (**cus:book** in unserem Beispiel); das **`<section>`**-Element muss durch das **`<chapter>`** Element ersetzt werden. Sie müssen das Stylesheet „cus:book-workflow.xsl“ anwenden, um die notwendigen Änderungen vorzunehmen.

Quellcode des verwendeten XSLT-Stylesheets:

```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
 <xsl:output indent="yes" method="xml"  encoding="ISO-8859-1"/>

 <xsl:template match="text()|@*"/>

  <xsl:template match="*">
    <xsl:variable name="element.name" select="name(.)"/>
    <xsl:element name="{$element.name}">
      <xsl:copy-of select="text()|@*"/>
      <xsl:apply-templates/>
    </xsl:element>
  </xsl:template>

  <xsl:template match="book">
  <book name="test">
     <xsl:apply-templates/>
    <book>
 </xsl:template>

  <xsl:template match="section">
    <chapter>
      <xsl:for-each select="@*">
        <xsl:copy-of select="."/>
      </xsl:for-each>
       <xsl:apply-templates/>
    </chapter>
  </xsl:template>
  
</xsl:stylesheet>
```

Die Content-Management-Aktivität endet mit der Speicherung der Inhaltsinstanz und dem Übergang zur nächsten Aktivität.

Die Zielgruppe wird mithilfe der **Abfrage**-Aktivität bestimmt.

Damit der Versand erst gestartet wird, wenn die Zielgruppenabfrage und die Aktualisierung des Inhalts abgeschlossen sind, wurde eine **Und-Verknüpfung** hinzugefügt.

Die Konfiguration des Versands erfolgt in der **Versand**-Aktion:

![](assets/d_ncs_content_workflow4.png)

Bei Erstellung eines neuen Versands ist die Angabe der Vorlage erforderlich.

Hier werden die Umwandlungsvorlagen aus der Publikationsvorlage als Versandvorlage verwendet. Bei der Inhaltserzeugung werden die HTML- und Text-Vorlagen genutzt, wenn sie keine verknüpfte Versandvorlage haben oder mit derselben Vorlage wie der in der Aktivität angegebenen referenziert sind.

Empfänger und Inhalt des Versands

werden im eingehenden Ereignis angegeben.

Die Aktivität endet mit der Vorbereitung und dem Start des Versands.

### Inhalt erstellen und später versenden {#creating-content-and-publishing-it-later}

Dieser Workflow erstellt einen Inhalt, die Datei-Publikation erfolgt jedoch zu einem späteren Zeitpunkt.

![](assets/d_ncs_content_workflow5.png)

Die erste **Content-Management**-Aktivität erstellt eine Inhaltsinstanz.

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>Im **[!UICONTROL Publikation]**-Tab der Umwandlungsvorlagen ist der Speicherort der zu erzeugenden Zielgruppe anzugeben.

Eine Warte-Aktivität setzt die nachfolgende Transition für die Dauer einer Woche aus.

![](assets/d_ncs_content_workflow7.png)

Der Inhalt wird während dieser Zeitspanne manuell angegeben.

Die nachfolgende Aktivität startet die Inhaltserzeugung.

![](assets/d_ncs_content_workflow8.png)

Der zu publizierende Inhalt wird in der eingehenden Transition angegeben.

Die Aktivität endet mit der Erzeugung des Inhalts unter Verwendung des angegebenen Publikationsverzeichnisses.

Die Aktivität **JavaScript-Code** speichert den kompletten Namen jeder erzeugten Datei.

![](assets/d_ncs_content_workflow9.png)

### Versand und Inhalt erstellen {#creating-the-delivery-and-its-content}

Der folgende Workflow entspricht dem ersten Beispiel, beginnt jedoch mit der Erstellung des Versands.

![](assets/d_ncs_content_workflow10.png)

In der ersten **Versanderstellung**-Aktivität wird der Versand konfiguriert.

Die Verzweigung ermöglicht das parallele Ablaufen der Zielgruppenberechnung und der Erstellung der Inhaltsinstanz.

Nach Abschluss dieser beiden Aktivitäten aktiviert die Und-Verknüpfung die **Versand**-Aktivität mit dem Inhalt und der Zielgruppe, die zuvor definiert wurden.

![](assets/d_ncs_content_workflow11.png)

Die zu startende Versandaktion wird in der eingehenden Transition angegeben.

Empfänger und Inhalt des Versands

werden im eingehenden Ereignis angegeben.

Die Aktivität endet mit der Vorbereitung und dem Start des Versands.

### Import von Inhalt von FTP-Servern {#importing-content-from-ftp}

Wenn Ihr Versandinhalt in einer auf FTP- oder SFTP-Servern befindlichen HTML-Datei verfügbar ist, können Sie diesen Inhalt einfach in Adobe-Campaign-Sendungen laden. In [diesem Beispiel](../../workflow/using/loading-delivery-content.md) wird dies näher erläutert.

### Import von Inhalt von Amazon Simple Storage Service (S3) Connector {#importing-content-from-amazon-simple-storage-service--s3--connector}

Wenn Ihr Versandinhalt in Amazon Simple Storage Service (S3) Buckets verfügbar ist, können Sie diesen Inhalt einfach in Adobe-Campaign-Sendungen laden. In [diesem Beispiel](../../workflow/using/loading-delivery-content.md) wird dies näher erläutert.

## Halbautomatische Aktualisierung {#semi-automatic-update}

Inhaltsdaten können in einem halbautomatischen Modus aktualisiert werden. Die Daten der Aktualisierung stammen aus einem XML-Stream, auf den über eine URL zugegriffen wird.

Die Aktivierung des Datenabrufs geschieht manuell über ein Formular.

Das Ziel besteht darin, ein **editBtn**-Feld **`<input>`** im Formular zu deklarieren. Dieses Steuerelement umfasst eine Bearbeitungszone und eine Schaltfläche zum Starten der Verarbeitung.

Die variablen Daten für die Erstellung der URL des XML-Streams der abzurufenden Daten werden im Editor erfasst.

Die Betätigung der Schaltfläche löst die **GetAndTransform**-SOAP-Methode aus, die unter dem **`<input>`**-Tag notiert ist.

Das Steuerelement wird im Formular wie folgt deklariert:

```
<input type="editbtn" xpath="<path>">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="<url>" type="string"/>
      <param exprIn="'xtk:xslt|<style sheet>'" type="string"/>
      <param type="DOMElement" xpathOut="<output path>"/>
    </soapCall>
  </enter>
</input>
```

Die **GetAndTransform**-Methode muss unter dem **`<enter>`**-Element des **`<input>`**-Tags deklariert werden. Dieses Tag akzeptiert als Parameter die URL der Wiederherstellung von XML-Daten aus einem dynamisch erstellten Ausdruck. Der zweite Parameter der Funktion ist optional und verweist auf ein Stylesheet, das für eine Zwischentransformation verwendet wird, wenn die eingehenden XML-Daten nicht im gleichen Format wie der Inhalt vorliegen.

Die Aktualisierung der Inhaltsinstanz geschieht ausgehend vom im letzten Parameter angegebenen Pfad.

**Beispiel**: Anhand des Schemas &quot;cus:Buch&quot; wird diese Funktion näher erläutert.

Das Formular wird um ein Eingabefeld für die halbautomatische Aktualisierung ergänzt:

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://server/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

Der Name der abzurufenden Datei wird im Editor erfasst. Die URL wird ausgehend von diesem Namen erstellt, z. B.: https://server/incomin/data.xml.

Das Format der abzurufenden Daten ist das gleiche wie im ersten Beispiel bezüglich der Workflow-Automatisation. Es wird erneut das dort erwähnte Stylesheet &quot;cus:Buch-workflow.xsl&quot; verwendet.

Aus der Ausführung des Vorgangs resultiert die Aktualisierung der Inhaltsinstanz ausgehend vom Pfad &#39;.&#39;.
