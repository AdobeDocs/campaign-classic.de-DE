---
title: Integration konfigurieren
seo-title: Integration konfigurieren
description: Integration konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 2%

---


# Fehlerbehebung bei Pipeline {#pipeline-troubleshooting}

**Pipelined schlägt fehl mit der Fehlermeldung &quot;Keine Aufgabe entspricht der pipelinierten@&quot;**

Ihre Version von Adobe Campaign Classic unterstützt die Pipeline nicht.

1. Überprüfen Sie, ob das Pipeline-Element in der Konfigurationsdatei vorhanden ist. Wenn nicht, bedeutet das, dass es nicht unterstützt wird.
1. Aktualisieren Sie auf Version 6.11 Build 8705 oder höher.

**Peilinierte fehlschlagen mit &#39;&#39; aurait dû kommencer par &#39;[&#39; ou &#39;{&#39; (iRc=16384)&#39;**

Die Option **NmsPipeline_Config** ist nicht festgelegt. Es ist eigentlich ein JSON-Parsing-Fehler.
Legen Sie die JSON-Konfiguration in der Option **NmsPipeline_Config** fest. Siehe &quot;Routing-Option&quot;auf dieser Seite.

**&quot;Das Thema muss eine gültige Organisation oder ein Kunde sein&quot; schlägt fehl.**

Die IMSOrgid-Konfiguration ist ungültig.

1. Überprüfen Sie, ob die IMSOrgId in der Datei serverConf.xml festgelegt ist.
1. Suchen Sie in der Konfigurationsdatei der Instanz nach einer leeren IMSOrgId, die den Standard überschreiben kann. Wenn ja, entfernen Sie es.
1. Überprüfen Sie, ob die IMSOrgId mit der des Kunden im Experience Cloud übereinstimmt.

**Ausgewählte Elemente schlagen mit &quot;ungültiger Schlüssel&quot;fehl**

Der Parameter &quot;@authPrivateKey&quot;der Konfigurationsdatei der Instanz ist nicht korrekt.

1. Überprüfen Sie, ob der authPrivateKey eingestellt ist.
1. Überprüfen Sie, ob der authPrivateKey: Beginn mit @, endet mit = und ist etwa 4000 Zeichen lang.
1. Suchen Sie nach dem Originalschlüssel und stellen Sie sicher, dass er: im RSA-Format, 4096 Bit lang und Beginn mit —BEGIN RSA PRIVATE KEY—.
   <br> Erstellen Sie den Schlüssel bei Bedarf neu und registrieren Sie ihn bei Adobe Analytics. Siehe diesen [Abschnitt](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Überprüfen Sie, ob der Schlüssel in derselben Instanz wie die Pipeline kodiert wurde. <br>Wiederholen Sie bei Bedarf die Kodierung mit dem Beispiel-JavaScript oder -Arbeitsablauf.

**Ausgewählte Elemente funktionieren nicht mit &quot;Token kann bei der Authentifizierung nicht gelesen werden&quot;.**

Das Format des privaten Schlüssels ist ungültig.

1. Führen Sie die Schritte für die Schlüsselverschlüsselung auf dieser Seite aus.
1. Vergewissern Sie sich, dass der Schlüssel auf derselben Instanz verschlüsselt ist.
1. Überprüfen Sie, ob der authPrivateKey in der Konfigurationsdatei mit dem generierten Schlüssel übereinstimmt. <br>Stellen Sie sicher, dass Sie OpenSSL verwenden, um das Schlüsselpaar zu generieren. PuttyGen generiert beispielsweise nicht das richtige Format.

**Es werden keine Auslöser abgerufen**

Wenn der Pipeline-Prozess ausgeführt wird und keine Auslöser abgerufen werden:

1. Stellen Sie sicher, dass der Auslöser in Analytics aktiv ist und Ereignis generiert.
1. Vergewissern Sie sich, dass der Pipeline-Prozess ausgeführt wird.
1. Suchen Sie nach Fehlern im Pipeline-Protokoll.
1. Suchen Sie auf der Seite mit dem Pipeline-Status nach Fehlern. auslöser-verworfen, Auslöserfehler sollten null sein.
1. Überprüfen Sie, ob der Auslösername in der Option **[!UICONTROL NmsPipeline_Config]** konfiguriert ist. Bei Zweifeln verwenden Sie die Platzhalteroption.
1. Vergewissern Sie sich, dass Analytics über einen aktiven Auslöser verfügt und Ereignis generiert. Es kann eine Verzögerung von ein paar Stunden nach der Konfiguration in Analytics geben, bevor sie aktiv ist.

**Ereignis sind nicht mit Kunden verknüpft**

Wenn einige Ereignis nicht mit einem Kunden verknüpft sind:

1. Überprüfen Sie, ob der Abgleichungsarbeitsablauf ausgeführt wird (falls zutreffend).
1. Überprüfen Sie, ob das Ereignis eine Kunden-ID enthält.
1. Machen Sie mit der Kunden-ID eine Abfrage auf der Kundentabelle.
1. Überprüfen Sie die Häufigkeit des Kundenimports. Neue Kunden werden mit einem Workflow in Adobe Campaign importiert.

**Latenz bei der Verarbeitung von Ereignissen**

Wenn der Analytics-Zeitstempel viel älter ist als das Erstellungsdatum des Ereignisses in der Kampagne.

Im Allgemeinen kann es 15-90 Minuten dauern, bis eine Marketing-Kampagne gestartet wird. Dies hängt von der Implementierung der Datenerfassung, dem Laden in der Pipeline, der benutzerdefinierten Konfiguration des definierten Auslösers und dem Workflow in Adobe Campaign ab.

1. Überprüfen Sie, ob der Pipeline-Prozess ausgeführt wurde.
1. Suchen Sie nach Fehlern in pipelined.log, die weitere Zustellversuche verursachen können. Korrigieren Sie die Fehler, falls zutreffend.
1. Überprüfen Sie die Seite mit dem Pipeline-Status auf die Warteschlangengröße. Wenn die Warteschlangengröße groß ist, verbessern Sie die Leistung des JS.
1. Da eine Verzögerung mit zunehmendem Volumen zu steigen scheint, konfigurieren Sie die Auslöser auf Analytics mit weniger Nachrichten.
Anhänge

**Verwendung des Schlüsselverschlüsselungs-JavaScript**

Führen Sie ein JavaScript aus, um den privaten Schlüssel zu verschlüsseln. Es ist für die Pipeline-Konfiguration erforderlich.

Im Folgenden finden Sie ein Codebeispiel, mit dem Sie die Funktion cryptString ausführen können:

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

Führen Sie auf dem Server das Javascript aus:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

Kopieren Sie den kodierten Schlüssel aus der Ausgabe in die Konsole und fügen Sie ihn ein.