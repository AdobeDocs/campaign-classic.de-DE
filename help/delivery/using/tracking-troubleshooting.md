---
solution: Campaign Classic
product: campaign
title: Fehlerbehebung bei der Verfolgung
description: Dieser Abschnitt enthält allgemeine Fragen zur Tracking-Konfiguration und -Implementierung in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: efa36dc08ce4dd59805bb9eba63a4249e14609d7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Tracking-Fehlerbehebung {#tracking-troubleshooting}

In diesem Abschnitt finden Sie allgemeine Fragen zur Tracking-Konfiguration und -Implementierung in Adobe Campaign Classic.

## Der Tracking-Workflow schlägt fehl.{#tracking-workflow-failing}

Mein Tracking-Workflow schlägt fehl. Wie kann ich die beschädigten Zeilen in der Verfolgungsdatei erkennen?

>[!NOTE]
>
>Nur für Windows verfügbar

Die beschädigte Verfolgungsprotokolldatei .../nl6/var//redir/log/0x000 log kann den Tracking-Workflow stoppen. Um beschädigte Zeilen einfach zu erkennen und sie zu entfernen, um den Verfolgungsarbeitsablauf wiederaufzunehmen, können Sie die folgenden Befehle verwenden.

### Ich weiß, in welcher Datei die beschädigte Zeile enthalten ist

In diesem Fall sind beschädigte Zeilen in der Datei &quot;0x000000000000A0000.log&quot;zu finden, aber derselbe Prozess kann auf mehrere Dateien angewendet werden - eine nach der anderen.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Anschließend können Sie den Tracking-Workflow beenden, die beschädigten Zeilen löschen und den Workflow neu starten.

### Ich weiß nicht, in welcher Datei die beschädigte Zeile enthalten ist

1. Verwenden Sie die folgende Befehlszeile, um alle Verfolgungsdateien einzuchecken.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. Der Befehl Liste alle beschädigten Zeilen. Beispiel:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Der Wagenrücklauf wurde vor dem Benutzeragent hinzugefügt, um eine bessere Lesbarkeit zu ermöglichen, und spiegelt nicht die effektive Wiedergabe wider.

1. Führen Sie einen grep-Befehl aus, um die entsprechende Datei zu suchen.

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. Suchen Sie das fehlerhafte Protokoll mit dem Dateinamen und der Zeilennummer. Beispiel:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Vor dem Benutzeragent wurde ein Wagenrücklauf hinzugefügt, um eine bessere Lesbarkeit zu ermöglichen, und spiegelt kein effektives Rendering wider.

Anschließend können Sie den Tracking-Workflow beenden, die beschädigten Zeilen löschen und den Workflow neu starten.

## Nachverfolgungslinks schlagen gelegentlich fehl{#tracking-links-fail-intermittently}

Beim Versuch, auf die Tracking-Links zuzugreifen, wird folgende Meldung angezeigt:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. Greifen Sie auf die URL &lt;redirect_server>/r/test zu und überprüfen Sie, ob die Buildnummer und der localhost von der Anforderung zurückgegeben wurden.

1. Überprüfen Sie die &quot;reserveServer&quot;-Konfiguration in der Datei &quot;serverConf.xml&quot;auf den Tracking-Server. Diese Konfiguration sollte sich im Umleitungsmodus befinden.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Überprüfen Sie manuell, ob die Datei &lt;deliveryID>.xml auf dem Computer in .../nl6/var//redir/url/&lt;YYYY> Verzeichnis (YYYY steht für Versand).

1. Überprüfen Sie manuell, ob &lt;trackingUrlId> in der Datei &lt;deliveryID>.xml enthalten ist.

1. Überprüfen Sie manuell, ob eine BroadlogID im entsprechenden DeliveryID-Versand vorhanden ist.

1. Überprüfen Sie die Zugriffsrechte für .xml-Dateien in .../nl6/var//redir/url/year.

   Sie sollten über mindestens 644 Berechtigungen verfügen, damit Apache Tracking-URLs lesen kann, um den angeforderten Link umzuleiten.

## Aktualisieren der Option NmsTracking_Zeiger? {#updating-option}

Führen Sie beim Aktualisieren der Option NmsTracking_Zeiger die folgenden Schritte aus:

1. Beenden Sie den Verfolgungsarbeitsablauf.

1. Beenden Sie den TrackingLogd-Dienst.

1. Aktualisieren Sie die Option NmsTracking_Pointer auf den gewünschten Wert.

1. Starten Sie den TrackingLogd-Dienst neu.

1. Starten Sie den Tracking-Workflow neu.

## Die Verfolgung funktioniert offenbar nicht mit einigen WebMail {#webmail}

Sie können die Klick-Tracking-Formel anpassen und eine benutzerdefinierte Adobe Analytics-Verfolgungsformel angeben.

Diese Art der Anpassung muss mit Vorsicht erfolgen, um zu vermeiden, dass zusätzliche Zeilenvorschubzeichen hinzugefügt werden. Alle Linefeed-Zeichen, die außerhalb des JavaScript-Ausdrucks vorhanden sind, werden in der endgültigen Formel angezeigt.

Diese Art zusätzlicher Zeilenvorschubzeichen in der Tracking-URL führt in einigen webMail (AOL, GMail usw.) zu Problemen.

**Erstes Beispiel:**

* Falsche Syntax

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* Richtige Syntax

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

Um zu verstehen, wo der zusätzliche Zeilenvorschub ist, können Sie JavaScript-Ausdruck durch eine feste Zeichenfolge STRING ersetzen.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Zweites Beispiel**

* Falsche Syntax

   ```
   <%@ include option='NmsTracking_ClickFormula' %>
   <% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* Richtige Syntax

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

Um zu verstehen, wo der zusätzliche Zeilenvorschub ist, können Sie JavaScript-Ausdruck durch eine feste Zeichenfolge STRING ersetzen.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## Trackinglogs werden zu langsam {#slow-retrieval} abgerufen

Wenn die Instanz nicht direkt Trackinglogs abruft, sondern von einem entfernten Adobe Campaign Classic-Server, werden die Protokolle über den SOAP-Aufruf GetTrackingLogs abgerufen, der im remoteTracking-Schema definiert ist.

Mit einer Option in der Datei &quot;serverConf.xml&quot;können Sie die Anzahl der Protokolle festlegen, die mit dieser Methode gleichzeitig abgerufen werden: logCountPerRequest.

Der Standardwert von logCountPerRequest ist 1000, er kann sich in einigen Fällen als zu klein erweisen. Die zulässigen Werte müssen zwischen 0 und 10.000 liegen.

## Trackinglogs konnten nicht mit Empfängern {#link-recipients} verknüpft werden

In Adobe Campaign Classic soll ein Zielgruppen-Mapping im Hinblick auf Empfänger Schema im Vergleich zu Broadlog-/Trackinglog-Schemas einzigartig sein.

![](assets/tracking-troubleshooting.png)

Es ist nicht möglich, mehrere Targeting-Schema mit demselben Verfolgungsprotokoll-Schema zu verwenden, da der Verfolgungsarbeitsablauf keine Daten mit der Targeting-ID abgleichen kann.

Wenn Sie das vordefinierte Zielgruppen-Mapping nicht mit nms:Empfänger verwenden möchten, empfehlen wir die folgenden Vorgehensweisen:

* Wenn Sie die benutzerdefinierte Zielgruppendimension verwenden möchten, müssen Sie ein benutzerdefiniertes Schema &quot;wideLog/trackingLog&quot;mit nms:extenlog als Vorlage erstellen (z. B. nms:wideLogRcp, nms:wideLogSvc usw.).

* Wenn Sie OOB trackingLogRcp/wideLogRcp verwenden möchten, muss die Zielgruppendimension nms:Empfänger lauten, und die Filterdimension könnte ein benutzerdefiniertes Schema sein.
