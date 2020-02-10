---
title: Personalisierte PDF-Dokumente erstellen
seo-title: Personalisierte PDF-Dokumente erstellen
description: Personalisierte PDF-Dokumente erstellen
seo-description: null
page-status-flag: never-activated
uuid: d4c27523-bff3-457a-ba60-e2747a2b3166
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 8dfc5e7c-c762-46ba-bbda-a7251354cb47
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Personalisierte PDF-Dokumente erstellen{#generating-personalized-pdf-documents}

## Über PDF-Dateien mit Variablen {#about-variable-pdf-documents}

Adobe Campaign ermöglicht ausgehend von LibreOffice- oder Microsoft-Word-Dateien das Erstellen von PDF-Dateien mit Variablen, die für personalisierte E-Mail-Anhänge oder Briefpost-Sendungen genutzt werden können.

Unterstützt werden die Formate &quot;.docx&quot;, &quot;.doc&quot; und &quot;.odt&quot;.

Um die entsprechenden Dokumente zu personalisieren, stehen Ihnen die gleichen JavaScript-Funktionen zur Verfügung, die auch bei E-Mails Verwendung finden.

Sie müssen die **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** Option aktivieren. Diese Option ist verfügbar, wenn Sie die Datei an die E-Mail-Zustellung anhängen. Weitere Informationen zum Anhängen einer berechneten Datei finden Sie im Abschnitt [Anhängen von Dateien](../../delivery/using/attaching-files.md) .

Beispiel der Personalisierung eines Rechnungskopfes:

![](assets/s_ncs_pdf_simple.png)

Die Erzeugung dynamischer Tabellen und der Einschluss von Bildern über URLs wird nachfolgend dargestellt.

## Dynamische Tabellen erstellen {#generating-dynamic-tables}

Gehen Sie wie folgt vor, um eine dynamische Tabelle zu erzeugen:

* Erstellen Sie eine Tabelle mit drei Zeilen und einer beliebigen Anzahl an Spalten. Konfigurieren Sie das Layout (Rahmen usw.).
* Platzieren Sie den Cursor auf die Tabelle und klicken Sie auf das **[!UICONTROL Table > Table properties]** Menü. Gehen Sie zur **[!UICONTROL Table]** Registerkarte und geben Sie einen Namen ein, der mit **NlJsTable** beginnt.
* Definieren Sie in der ersten Zelle der ersten Zeile eine Schleife (z. B. &quot;for&quot;), die die Iteration der Werte, die Sie anzeigen möchten, ermöglicht.
* Fügen Sie in jeder Zelle der zweiten Zeile die Scripts ein, die die anzuzeigenden Werte ausgeben.
* Schließen Sie die Schleife in der dritten und letzten Zeile der Tabelle.

   Beispiel der Erstellung einer dynamischen Tabelle:

   ![](assets/s_ncs_pdf_table.png)

## Externe Bilder einfügen {#inserting-external-images}

Sie haben die Möglichkeit, ein Dokument mit Bildern zu personalisieren, deren URL in einem Feld des Empfängerprofils gespeichert ist.

Konfigurieren Sie hierzu einen Gestaltungsbaustein und verweisen Sie auf diesen im angehängten Dokument.

**Anwendungsbeispiel: Einfügen eines personalisierten Logos in Abhängigkeit vom Herkunftsland des Empfängers**

**1. Schritt: Erstellung des Anhangs**

* Fügen Sie den Verweis auf den Gestaltungsbaustein ein: **&lt;%@ include view=&quot;Baustein-Name&quot; %>**.
* Fügen Sie den (eventuell personalisierten) Inhalt in den Nachrichten-Textkörper ein.

![](assets/s_ncs_open_office_blocdeperso.png)

**2. Schritt: Erstellung des Gestaltungsbausteins**

* Gehen Sie zum **[!UICONTROL Resources > Campaign management > Personalization blocks]** Menü der Adobe Campaign-Konsole.
* Erstellen Sie einen neuen Baustein mit dem Titel &quot;Mein Logo&quot; und dem internen Namen &quot;Mein_Logo&quot;.
* Klicken Sie auf den **[!UICONTROL Advanced parameters...]** Link und aktivieren Sie die **[!UICONTROL "The content of the block is included in an attachment"]** Option. Dadurch können Sie die Definition des Personalisierungsblocks direkt in den Inhalt der OpenOffice-Datei kopieren.

   ![](assets/s_ncs_pdf_bloc_option.png)

   Innerhalb des Gestaltungsbausteins sind zwei Deklarierungstypen zu unterscheiden:

   * The Adobe Campaign code of the personalization fields for which the &quot;open&quot; and &quot;closed&quot; chevrons must be replaced with escape characters (respectively `&lt;` and `&gt;`).
   * Der OpenOffice-XML-Code wird vollständig in das OpenOffice-Dokument kopiert.

Im Beispiel weist der Gestaltungsbaustein folgendes Format auf:

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

Die Personalisierung bezüglich des Herkunftslands des Empfängers wurde korrekt konfiguriert:

![](assets/s_ncs_pdf_result.png)
