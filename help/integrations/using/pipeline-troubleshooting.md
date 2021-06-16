---
product: campaign
title: Konfigurieren der Integration
description: Konfigurieren der Integration
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 9a126d16b394333163b974ad9690f7c93fb3034a
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 80%

---

# Fehlerbehebung bei Pipelines {#pipeline-troubleshooting}

**Pipelined schlägt fehl mit der Fehlermeldung &quot;No task corresponds to the mask pipelined@&lt; Instanz >&quot;**

Ihre Version von Adobe Campaign Classic unterstützt die Pipeline nicht.

1. Vergewissern Sie sich, dass das [!DNL pipelined]-Element in der Konfigurationsdatei vorhanden ist. Wenn nicht, bedeutet das, dass es nicht unterstützt wird.
1. Aktualisieren Sie auf Campaign 20.3 oder [!DNL Gold Standard]-Version 11.

**Pipeline schlägt fehl mit der Fehlermeldung &quot;aurait dû kommencer par `[` ou `{` (iRc=16384)&quot;**

Die Option **NmsPipeline_Config** ist nicht festgelegt. Es handelt sich dabei in Wahrheit um einen JSON-Parsing-Fehler.
Legen Sie in der Option **NmsPipeline_Config** die JSON-Konfiguration fest. Siehe &quot;Routing-Option&quot; auf dieser Seite.

**Pipelined schlägt fehl mit der Fehlermeldung &quot;the subject must be a valid organization or client&quot;**

Die Konfiguration der Organisationskennung ist ungültig.

1. Überprüfen Sie, ob die IMSOrgId in der Datei &quot;serverConf.xml&quot; festgelegt ist.
1. Suchen Sie in der Konfigurationsdatei der Instanz nach einer leeren IMSOrgId, die den Standard überschreiben kann. Wenn vorhanden, entfernen Sie den Standard.
1. Überprüfen Sie, ob die IMSOrgId mit der des Kunden in Experience Cloud übereinstimmt.

**Pipelined schlägt fehl mit der Fehlermeldung &quot;invalid key&quot;**

Der Parameter &quot;@authPrivateKey&quot; der Konfigurationsdatei der Instanz ist fehlerhaft.

1. Überprüfen Sie, ob &quot;authPrivateKey&quot; festgelegt ist.
1. Vergewissern Sie sich, dass &quot;authPrivateKey:&quot; mit &quot;@&quot; beginnt, mit &quot;=&quot; endet und etwa 4.000 Zeichen lang ist.
1. Suchen Sie nach dem ursprünglichen Schlüssel und vergewissern Sie sich, dass er: im RSA-Format, 4096 Bit lang und beginnt mit `-----BEGIN RSA PRIVATE KEY-----`.
   <br> Erstellen Sie den Schlüssel ggf. neu und registrieren Sie ihn bei Adobe Analytics.
1. Vergewissern Sie sich, dass der Schlüssel in derselben Instanz kodiert wurde wie [!DNL pipelined]. <br>Wiederholen Sie bei Bedarf die Kodierung mit dem Beispiel-JavaScript oder -Workflow.

**Pipelined schlägt fehl mit der Fehlermeldung &quot;unable to read the token during authentication&quot;**

Das Format des privaten Schlüssels ist ungültig.

1. Führen Sie die Schritte zur Verschlüsselung des Schlüssels auf dieser Seite aus.
1. Stellen Sie sicher, dass der Schlüssel auf derselben Instanz verschlüsselt wird.
1. Überprüfen Sie, ob &quot;authPrivateKey&quot; in der Konfigurationsdatei mit dem generierten Schlüssel übereinstimmt. <br>Sorgen Sie dafür, dass Sie zur Generierung des Schlüsselpaars OpenSSL verwenden. PuttyGen beispielsweise generiert nicht das richtige Format.

**Pipelined schlägt fehl mit der Fehlermeldung &quot;is not longer allowed get access token&quot;**

Die Protokolle sollten wie folgt lauten:

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

Diese Fehlermeldung bedeutet, dass die Authentifizierung mit der alten Omniture-Basis OAuth konfiguriert ist. Informationen zum Aktualisieren Ihrer Authentifizierung finden Sie in der Dokumentation [Konfigurieren der Adobe I/O für Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) .

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
1. Da die Verzögerung mit zunehmender Anzahl wächst, konfigurieren Sie die Trigger in Analytics mit weniger Nachrichten.

**Aktualisieren von Staging-Instanzen von der alten Authentifizierung zur Adobe IO-Authentifizierung**

Das Ändern der Integrationsauthentifizierung auf Ihrer Staging-Instanz wirkt sich nicht auf die Konfiguration Ihrer Produktionsinstanz aus. Sie können Ihre Staging-Instanz aktualisieren und dann die Authentifizierung auf Adobe IO aktualisieren und Ihre Trigger auf Ihrer Staging-Instanz testen.

Ihre Produktionsinstanz verwendet weiterhin die Legacy-Authentifizierung und ist von dieser Änderung nicht betroffen.
