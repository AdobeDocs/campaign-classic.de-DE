---
solution: Campaign Classic
product: campaign
title: Konfigurieren der Integration
description: Konfigurieren der Integration
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 100%

---


# Fehlerbehebung bei Pipelines {#pipeline-troubleshooting}

**Pipelined schlägt fehl mit der Fehlermeldung &quot;No task corresponds to the mask pipelined@&lt; Instanz >&quot;**

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
   <br> Erstellen Sie den Schlüssel ggf. neu und registrieren Sie ihn bei Adobe Analytics.
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
