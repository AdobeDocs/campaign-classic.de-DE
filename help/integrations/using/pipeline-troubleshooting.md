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
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '644'
ht-degree: 100%

---


# Fehlerbehebung bei Pipelines {#pipeline-troubleshooting}

**Pipelined schlägt fehl mit der Fehlermeldung &quot;No task corresponds to the mask pipelined@&quot;**

Ihre Version von Adobe Campaign Classic unterstützt die Pipeline nicht.

1. Vergewissern Sie sich, dass das [!DNL pipelined]-Element in der Konfigurationsdatei vorhanden ist. Wenn nicht, bedeutet das, dass es nicht unterstützt wird.
1. Aktualisieren Sie auf Version 6.11 Build 8705 oder höher.

**Pipeline schlägt fehl mit der Fehlermeldung &quot;aurait dû kommencer par `[` ou `{` (iRc=16384)&quot;**

Die Option **NmsPipeline_Config** ist nicht festgelegt. Es handelt sich dabei in Wahrheit um einen JSON-Parsing-Fehler.
Legen Sie in der Option **NmsPipeline_Config** die JSON-Konfiguration fest. Siehe &quot;Routing-Option&quot; auf dieser Seite.

**Pipelined schlägt fehl mit der Fehlermeldung &quot;the subject must be a valid organization or client&quot;**

Die IMSOrgId-Konfiguration ist ungültig.

1. Überprüfen Sie, ob die IMSOrgId in der Datei &quot;serverConf.xml&quot; festgelegt ist.
1. Suchen Sie in der Konfigurationsdatei der Instanz nach einer leeren IMSOrgId, die den Standard überschreiben kann. Wenn vorhanden, entfernen Sie den Standard.
1. Überprüfen Sie, ob die IMSOrgId mit der des Kunden in Experience Cloud übereinstimmt.

**Pipelined schlägt fehl mit der Fehlermeldung &quot;invalid key&quot;**

Der Parameter &quot;@authPrivateKey&quot; der Konfigurationsdatei der Instanz ist fehlerhaft.

1. Überprüfen Sie, ob &quot;authPrivateKey&quot; festgelegt ist.
1. Vergewissern Sie sich, dass &quot;authPrivateKey:&quot; mit &quot;@&quot; beginnt, mit &quot;=&quot; endet und etwa 4.000 Zeichen lang ist.
1. Suchen Sie nach dem Originalschlüssel und stellen Sie sicher, dass er im RSA-Format vorliegt, 4.096 Bit lang ist und mit -----BEGIN RSA PRIVATE KEY----- beginnt.
   <br> Erstellen Sie den Schlüssel bei Bedarf neu und registrieren Sie ihn bei Adobe Analytics. Siehe diesen [Abschnitt](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Vergewissern Sie sich, dass der Schlüssel in derselben Instanz kodiert wurde wie [!DNL pipelined]. <br>Wiederholen Sie bei Bedarf die Kodierung mit dem Beispiel-JavaScript oder -Workflow.

**Pipelined schlägt fehl mit der Fehlermeldung &quot;unable to read the token during authentication&quot;**

Das Format des privaten Schlüssels ist ungültig.

1. Führen Sie die Schritte zur Verschlüsselung des Schlüssels auf dieser Seite aus.
1. Stellen Sie sicher, dass der Schlüssel auf derselben Instanz verschlüsselt wird.
1. Überprüfen Sie, ob &quot;authPrivateKey&quot; in der Konfigurationsdatei mit dem generierten Schlüssel übereinstimmt. <br>Sorgen Sie dafür, dass Sie zur Generierung des Schlüsselpaars OpenSSL verwenden. PuttyGen beispielsweise generiert nicht das richtige Format.

**Es werden keine Auslöser abgerufen**

Wenn der [!DNL pipelined]-Prozess ausgeführt wird und keine Auslöser abgerufen werden:

1. Vergewissern Sie sich, dass der Auslöser in Analytics aktiv ist und Ereignisse generiert.
1. Vergewissern Sie sich, dass der [!DNL pipelined]-Prozess ausgeführt wird.
1. Suchen Sie im [!DNL pipelined]-Log nach Fehlern.
1. Suchen Sie auf der [!DNL pipelined]-Statusseite nach Fehlern. &quot;trigger-discarted&quot;, &quot;trigger-failures&quot; sollten null sein.
1. Überprüfen Sie, ob der Auslösername in der Option **[!UICONTROL NmsPipeline_Config]** konfiguriert ist. Verwenden Sie im Zweifel die Platzhalteroption.
1. Vergewissern Sie sich, dass Analytics über einen aktiven Auslöser verfügt und Ereignisse generiert. Nach der Konfiguration in Analytics kann eine Verzögerung von einigen Stunden auftreten, bevor der Auslöser aktiv wird.

**Ereignisse sind nicht mit einem Kunden verknüpft**

Wenn bestimmte Ereignisse nicht mit einem Kunden verknüpft sind:

1. Überprüfen Sie, ob der Abstimmungs-Workflow ausgeführt wird (falls zutreffend).
1. Überprüfen Sie, ob das Ereignis eine Kunden-ID enthält.
1. Stellen Sie mit der Kunden-ID eine Abfrage an die Kundentabelle.
1. Überprüfen Sie die Häufigkeit des Kundenimports. Neue Kunden werden mit einem Workflow in Adobe Campaign importiert.

**Latenz bei der Verarbeitung von Ereignissen**

Wenn der Analytics-Zeitstempel viel älter ist als das Erstellungsdatum des Ereignisses in Campaign.

Im Allgemeinen kann es 15–90 Minuten dauern, bis eine Marketing-Kampagne gestartet wird. Dies hängt von der Implementierung der Datenerfassung, der Auslastung der Pipeline, der benutzerdefinierten Konfiguration des festgelegten Auslösers und dem Workflow in Adobe Campaign ab.

1. Überprüfen Sie, ob der [!DNL pipelined]-Prozess ausgeführt wird.
1. Suchen Sie in &quot;pipelined.log&quot; nach Fehlern, die weitere Zustellversuche verursachen können. Beheben Sie die Fehler, falls zutreffend.
1. Prüfen Sie die [!DNL pipelined]-Statusseite auf die Warteschlangengröße. Wenn der Warteschlangenumfang groß ist, optimieren Sie die Leistung des JS.
1. Da die Verzögerung mit zunehmendem Volumen zu wachsen scheint, konfigurieren Sie die Auslöser in Analytics mit weniger Nachrichten.
Anhänge

**Verwenden des JavaScripts für die Verschlüsselung des Schlüssels**

Führen Sie ein JavaScript aus, um den privaten Schlüssel zu verschlüsseln. Das ist für die Pipeline-Konfiguration erforderlich.

Im Folgenden finden Sie ein Code-Beispiel, mit dem Sie die Funktion &quot;cryptString&quot; ausführen können:

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

Führen Sie das JavaScript auf dem Server aus:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

Kopieren Sie den verschlüsselten Schlüssel aus der Ausgabe und fügen Sie ihn in die Konsole ein.