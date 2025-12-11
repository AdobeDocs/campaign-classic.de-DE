---
product: campaign
title: Erste Schritte mit dem Tracking
description: Weitere Informationen finden Sie in den allgemeinen Richtlinien zum Tracking in Adobe Campaign
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: ht
source-wordcount: '1267'
ht-degree: 100%

---

# Erste Schritte mit dem Tracking von Nachrichten {#get-started-tracking}

>[!IMPORTANT]
>
>**Allgemeine Anleitungen zum Tracking**, die sowohl für Campaign Classic v7 als auch für Campaign v8 gelten, finden Sie in der [Dokumentation zum Nachrichten-Tracking in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}:
>
>* [Konfigurieren nachverfolgter Links](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [Konfigurieren von URL-Tracking-Optionen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [Nachverfolgen personalisierter Links](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [Zugreifen auf Trackinglogs](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [Testen von Tracking](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [Tracking-Berichte](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**Auf dieser Seite werden nur Campaign Classic v7-spezifische Tracking-Funktionen dokumentiert**, in erster Linie für Hybrid- und On-Premise-Bereitstellungen.

## Tracking-Funktionen

### Tracking-Konfiguration {#configure-tracking}

Bei **Hybrid-/On-Premise-Bereitstellungen** von Campaign Classic v7 müssen Sie das Tracking auf Instanzebene konfigurieren, bevor Sie es verwenden können.

>[!NOTE]
>
>Für Campaign v8 Managed Cloud Services wird die Tracking-Konfiguration von Adobe durchgeführt.

**Grundprinzip**

Bevor Sie das Tracking verwenden, müssen Sie es zunächst für Ihre Instanz konfigurieren. Die Konfiguration muss auf den Anwendungs- und Webservern von Adobe Campaign durchgeführt werden.

In Campaign gibt es zwei Arten von Tracking:

* **Webtracking**: Dieser Modus ermöglicht das Tracking von Besuchen auf Web-Seiten
* **Nachrichten-Tracking**: In diesem Modus können Sie den Nachrichtenversand und das Empfängerverhalten verfolgen

Der Tracking-Modus wird während der Installation ausgewählt. Bei On-Premise-Installationen muss die Tracking-Konfiguration auf Instanzebene definiert werden. [Weitere Informationen](../../installation/using/deploying-an-instance.md#operating-principle)

**Tracking-Server**

Für die Konfiguration von Tracking muss Ihre Instanz deklariert und bei dem/den Tracking-Server(n) registriert werden. Der Tracking-Server wird verwendet, um Informationen über URLs aufzuzeichnen und abzurufen, auf die Empfängerinnen und Empfänger geklickt haben.

Bei On-Premise-Installationen ist der Tracking-Server normalerweise ein Webserver, auf dem die Adobe Campaign-Web-Anwendung ausgeführt wird. Die Tracking-Server-URL muss in Ihrer Instanzkonfiguration definiert werden. [Weitere Informationen](../../installation/using/deploying-an-instance.md#tracking-server)

**Tracking speichern**

Sobald das Tracking konfiguriert und Ihre URLs ausgefüllt sind, muss der Tracking-Server registriert werden. Die Registrierung ermöglicht es Adobe Campaign, Tracking-Informationen zu speichern und Berichte und Statistiken zu nachverfolgten Aktivitäten bereitzustellen.

Bei On-Premise-Installationen werden Tracking-Informationen in der Datenbank gespeichert und über technische Workflows abgerufen. Der technische Workflow **Tracking** verarbeitet und speichert die vom Weiterleitungs-Server erfassten Tracking-Daten. [Weitere Informationen](../../installation/using/deploying-an-instance.md#saving-tracking)

### Web-Anwendungs-Tracking {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**Das Web-Anwendungs-Tracking gilt speziell für Campaign Classic v7** und ist in Campaign v8 nicht verfügbar.

**Web-Anwendung tracken**

Sie können auch Besuche auf Web-Anwendungsseiten mit Trackingtags verfolgen und messen. Diese Funktionalität kann für alle Web-Anwendungstypen wie Formulare und Landingpages verwendet werden. [Weitere Informationen](../../web/using/tracking-a-web-application.md)

**Opt-out vom Web-Anwendungs-Tracking**

Mit der Opt-Out-Funktion für das Web-Anwendungs-Tracking können Sie das Tracking des Web-Verhaltens von Endbenutzern stoppen, die sich gegen das Tracking ihres Verhaltens entschieden haben. Sie können ermöglichen, ein Banner in Web-Anwendungen oder Zielseiten anzuzeigen, damit Benutzer sich abmelden können. [Weitere Informationen](../../web/using/web-application-tracking-opt-out.md)

## Fehlerbehebung beim Tracking {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Die folgenden Tipps zur Fehlerbehebung gelten für **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7**. Einige Informationen gelten möglicherweise auch für On-Premise-Bereitstellungen von Campaign v8. Wenden Sie sich für Campaign v8 Managed Cloud Services an Ihre Adobe-Support-Fachkraft.

Grundlegende Schritte zur Fehlerbehebung beim Tracking in Campaign v8 finden Sie in der [Dokumentation zur Fehlerbehebung beim Tracking in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}.

### Allgemeine Prüfungen {#basic-checks}

**Überprüfen Sie, ob der trackinglogd-Prozess ausgeführt wird**

Dieser Prozess liest aus dem gemeinsam genutzten IIS/Webserver-Speicher und schreibt die Weiterleitungsprotokolle.

Sie können von der Startseite aus darauf zugreifen, indem Sie in Ihrer Instanz die Registerkarte „Monitoring“ auswählen. Sie können auch den folgenden Befehl für die Instanz ausführen: `<user>@<instance>:~$ nlserver pdump`

Wenn der trackinglogd-Prozess nicht in der Liste angezeigt wird, starten Sie ihn mit dem folgenden Befehl für die Instanz: `<user>@<instance>:~$ nlserver start trackinglogd`

**Überprüfen Sie, ob der technische Tracking-Workflow kürzlich ausgeführt wurde**

Sie finden den technischen Tracking-Workflow in den Ordnern „Administration“ > „Produktion“ > „Technische Workflows“. 

### Erweiterte Problembehebung {#advanced-troubleshooting}

+++Der Tracking-Workflow schlägt fehl. 

>[!NOTE]
>
>Nur für Windows verfügbar

Die beschädigte Trackinglog-Datei .../nl6/var/&lt;Instanzname>/redir/log/0x0000 log kann den Tracking-Workflow stoppen. Mit den folgenden Befehlen können Sie beschädigte Zeilen leicht erkennen und entfernen, um den Tracking-Workflow fortzusetzen. 

**Ich weiß, in welcher Datei die beschädigte Zeile enthalten ist**

In diesem Fall können Sie die beschädigten Zeilen in der Datei 0x00000000000A0000.log finden. Der gleiche Vorgang kann jedoch nacheinander auf eine Reihe von Dateien angewendet werden.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Anschließend können Sie den Tracking-Workflow stoppen, die beschädigten Zeilen löschen und den Workflow neu starten.

**Ich weiß nicht, in welcher Datei die beschädigte Zeile enthalten ist**

1. Verwenden Sie die folgende Befehlszeile, um alle Tracking-Dateien zu prüfen.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. Der Befehl listet alle beschädigten Zeilen auf. Beispiel:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Der Zeilenumbruch wurde vor dem Benutzeragenten hinzugefügt, um bessere Lesbarkeit zu ermöglichen, und spiegelt nicht das effektive Rendering wider.

1. Führen Sie einen grep-Befehl aus, um die entsprechende Datei zu finden.

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. Suchen Sie nach dem fehlerhaften Log mit dem Dateinamen und der Zeilennummer. Beispiel:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Ein Zeilenumbruch wurde vor dem Benutzeragenten hinzugefügt, um bessere Lesbarkeit zu ermöglichen, und spiegelt nicht das effektive Rendering wider.

Anschließend können Sie den Tracking-Workflow stoppen, die beschädigten Zeilen löschen und den Workflow neu starten.

+++

+++Trackinglinks schlagen gelegentlich fehl

Beim Versuch, auf die Trackinglinks zuzugreifen, wird folgende Meldung angezeigt:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. Greifen Sie auf die URL &lt;redirect_server>/r/test zu und überprüfen Sie, ob die Build-Nummer und localhost von der Anfrage zurückgegeben wurden.

1. Überprüfen Sie die spareServer-Konfiguration in der Datei serverConf.xml auf den Tracking-Server. Diese Konfiguration sollte sich im Weiterleitungsmodus befinden.

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

1. Prüfen Sie manuell, ob die XML-Datei &lt;deliveryID>.xml auf dem Computer im Verzeichnis &quot;... / nl6 / var / &lt;Instanzname> / redir / url / &lt;JJJJ>&quot; vorhanden ist (JJJJ steht für das Versandjahr).

1. Prüfen Sie manuell, ob &lt;trackingUrlId> in der Datei &lt;deliveryID>.xml gefunden werden kann.

1. Prüfen Sie manuell, ob broadlogID im zugehörigen deliveryID-Versand vorhanden ist.

1. Prüfen Sie die Berechtigungen der &lt;deliveryID>.xml-Dateien im Verzeichnis &quot;.../nl6/var/&lt;Instanzname>/redir/url/year&quot;.

   Sie sollten mindestens die Berechtigung &quot;644&quot; haben, damit Apache die Tracking-URLs lesen kann, um den angeforderten Link umzuleiten.

+++

+++Aktualisieren der Option „NmsTracking_Pointer“

Gehen Sie beim Aktualisieren der Option &quot;NmsTracking_Pointer&quot; wie folgt vor:

1. Stoppen Sie den Tracking-Workflow an.

1. Stoppen Sie den trackinglogd-Service an.

1. Aktualisieren Sie die Option &quot;NmsTracking_Pointer&quot; auf den gewünschten Wert.

1. Starten Sie den trackinglogd-Service neu.

1. Starten Sie den Tracking-Workflow neu.

+++

+++Tracking funktioniert bei einigen Webmail-Services nicht

Sie können die Klick-Tracking-Formel anpassen und eine benutzerdefinierte Adobe Analytics-Tracking-Formel angeben.

Diese Art der Anpassung muss mit Vorsicht erfolgen, um zu vermeiden, dass zusätzliche Zeilenvorschubzeichen hinzugefügt werden. Alle Zeilenvorschubzeichen, die außerhalb des JavaScript-Ausdrucks vorhanden sind, sind in der endgültigen Formel enthalten.

Diese Art von zusätzlichem Zeilenvorschubzeichen in der Tracking-URL führt bei einigen WebMail-Services (AOL, GMail usw.) zu Problemen.

**Erstes Beispiel:**

* Falsche Syntax

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* Richtige Syntax

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

Um zu verstehen, wo sich der zusätzliche Zeilenvorschub befindet, können Sie den JavaScript-Ausdruck durch eine unveränderliche STRING-Zeichenkette ersetzen.

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
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* Richtige Syntax

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

Um zu verstehen, wo sich der zusätzliche Zeilenvorschub befindet, können Sie den JavaScript-Ausdruck durch eine unveränderliche STRING-Zeichenkette ersetzen.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++Trackinglogs werden zu langsam abgerufen

Wenn die Instanz die Trackinglogs nicht direkt abruft, sondern von einem entfernten Adobe Campaign Classic-Server, werden die Logs über den SOAP-Aufruf &quot;GetTrackingLogs&quot; abgerufen, der im remoteTracking-Schema definiert ist.

Mit einer Option in der Datei serverConf.xml können Sie die Anzahl der Logs festlegen, die mit dieser Methode gleichzeitig abgerufen werden: logCountPerRequest.

Der Standardwert von &quot;logCountPerRequest&quot; ist 1000, was sich in einigen Fällen als zu klein erweisen kann. Die zulässigen Werte müssen zwischen 0 und 10.000 liegen.

+++

+++Trackinglogs konnten nicht mit Empfängern verknüpft werden

In Adobe Campaign Classic soll ein Zielgruppen-Mapping hinsichtlich des Empfängerschemas im Vergleich zu Broadlog-/Trackinglog-Schemata eindeutig sein.

![](assets/tracking-troubleshooting.png)

Es ist nicht möglich, mehrere Zielgruppenschemata mit demselben Trackinglog-Schema zu verwenden, da der Tracking-Workflow keine Daten mit der Zielgruppenbestimmungs-ID abstimmen kann.

Wenn Sie das vorkonfigurierte Zielgruppen-Mapping nicht mit „nms:recipient“ verwenden möchten, empfehlen wir die folgenden Vorgehensweisen:

* Wenn Sie die benutzerdefinierte Zielgruppendimension verwenden möchten, müssen Sie ein benutzerdefiniertes Schema „broadLog/trackingLog“ mit nms:broadlog als Vorlage erstellen (z. B. „nms:broadLogRcp“, „nms:broadLogSvc“etc.).

* Wenn Sie die vorkonfigurierten trackingLogRcp-/broadLogRcp-Schemata verwenden möchten, muss die Zielgruppendimension „nms:recipient“ lauten und die Filterdimension könnte ein benutzerdefiniertes Schema sein.

+++
