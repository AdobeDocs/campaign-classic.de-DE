---
solution: Campaign Classic
product: campaign
title: Protokoll und Einstellungen für den SMS-Anschluss
description: Erfahren Sie mehr über den SMS-Connector und dessen Konfiguration.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 96ad3208c792efb47097768bc779bec59d9ca313
workflow-type: tm+mt
source-wordcount: '2745'
ht-degree: 0%

---


# SMS-Fehlerbehebung {#troubleshooting-sms}

## Konflikt zwischen verschiedenen Externen Konti {#external-account-conflict}

Wenn die Instanz über mehrere SMS-Externe Konti verfügt, müssen Sie überprüfen, ob Probleme nicht durch einen Konflikt zwischen Externen Konti verursacht werden.

Adobe Campaign behandelt Externe Konti als nicht verbundene Entitäten.

Wenn Sie mehrere Konten haben, führen Sie dieses Verfahren aus, um das Externe Konto zu isolieren, das Probleme verursacht:

1. Deaktivieren Sie alle Externe Konti.
1. Aktivieren Sie ein Externe Konto.
1. Versuch, das Problem zu reproduzieren.
1. Wenn das ursprüngliche Problem nicht immer auftritt, versuchen Sie es mit einer angemessenen Anzahl von Versuchen, bevor Sie abschließen.
1. Wenn das Problem bei diesem einzelnen Konto nicht auftritt, deaktivieren Sie es und starten Sie beim nächsten Konto mit Schritt 2 neu.

Nachdem Sie jedes Konto einzeln geprüft haben, gibt es zwei mögliche Szenarien:

* **Das Problem trat auf einem oder mehreren Konten auf**

   In diesem Fall können Sie für jedes Konto andere Verfahren zur Fehlerbehebung anwenden. Es ist am besten, andere Konten während der Diagnose eines Kontos zu deaktivieren, um den Netzwerkverkehr und die Anzahl der Protokolle zu reduzieren.

* **Das Problem wurde nicht angezeigt, wenn immer nur ein Konto aktiv war**

   Sie haben einen Konflikt zwischen Konten. Wie bereits erwähnt, behandelt Adobe Campaign Konten einzeln, aber der Anbieter kann sie als ein einziges Konto behandeln.

   * Sie verwenden verschiedene Kombinationen aus Login/Passwort zwischen all Ihren Konten.
Sie müssen den Anbieter kontaktieren, um potenzielle Konflikte auf ihrer Seite zu diagnostizieren.

   * Einige der Externe Konti verwenden dieselbe Kombination aus Benutzername und Kennwort.
Der Anbieter kann nicht sagen, von welchem Externe Konto das `BIND PDU` kommt, daher behandeln sie alle Verbindungen aus mehreren Konten als ein einziges. Möglicherweise haben sie MO und SR zufällig über die beiden Konten geleitet, was Probleme verursacht hat.
Wenn der Anbieter mehrere Kurzcodes für dieselbe Login-/Passwortkombination unterstützt, müssen Sie ihn fragen, wo er diesen Kurzcode in `BIND PDU` einfügen soll. Beachten Sie, dass diese Information in das `BIND PDU` und nicht in `SUBMIT_SM` eingefügt werden muss, da `BIND PDU` der einzige Ort ist, an dem Routing-MOs korrekt zulässig sind.
Siehe den Abschnitt [Informationen in jeder Art von PDU](../../delivery/using/sms-protocol.md#information-pdu) weiter oben, um zu erfahren, welches Feld in `BIND PDU` verfügbar ist. Normalerweise fügen Sie den Kurzcode in `address_range` hinzu, was jedoch besondere Unterstützung vom Anbieter erfordert. Kontaktieren Sie sie, um zu erfahren, wie sie erwarten, mehrere Kurzcodes unabhängig zu routen.
Adobe Campaign unterstützt die Verarbeitung mehrerer Kurzcodes auf demselben Externe Konto.

## Problem mit Externe Konto im Allgemeinen {#external-account-issues}

* Untersuchen Sie, ob der Connector kürzlich geändert wurde und von wem (prüfen Sie die Externe Konti als Gruppe).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Untersuchen Sie (im Verzeichnis /nach der Aktualisierung), ob und wann das System aktualisiert wurde
* Untersuchen Sie, ob möglicherweise kürzlich aktualisierte Pakete mit SMS-Unterstützung (/var/log/dpkg.log) installiert wurden.

## Problem mit Mid-Sourcing (gehostet){#issue-mid-sourcing}

* Wenn das Problem auf einer Mid-Sourcing-Umgebung auftritt, stellen Sie sicher, dass der Versand und die allgemeinen Protokolle ordnungsgemäß erstellt und auf dem Mid-Sourcing-Server aktualisiert werden. Wenn das nicht der Fall ist, ist dies keine SMS-Ausgabe.

* Wenn alles auf dem Mid-Server funktioniert und SMS ordnungsgemäß gesendet werden, die Marketing-Instanz jedoch nicht ordnungsgemäß aktualisiert wurde, kann es zu einem Mid-Synchronisierungsproblem kommen.

## Problem beim Herstellen einer Verbindung mit dem Anbieter {#issue-provider}

* Wenn `BIND PDU` einen Nicht-Null-`command_status`-Code zurückgibt, fragen Sie den Anbieter nach weiteren Informationen.

* Vergewissern Sie sich, dass das Netzwerk ordnungsgemäß konfiguriert ist, damit die TCP-Verbindung mit dem Anbieter hergestellt werden kann.

* Bitten Sie den Anbieter, zu überprüfen, ob die IPs der Zulassungsliste der Adobe Campaign-Instanz ordnungsgemäß hinzugefügt wurden.

* Überprüfen Sie die Einstellungen für **Externe Konto**. Fragen Sie den Anbieter nach dem Wert der Felder.

* Wenn die Verbindung erfolgreich, aber instabil ist, überprüfen Sie den Abschnitt [Problem mit instabilen Verbindungen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Wenn Verbindungsprobleme schwer zu diagnostizieren sind, kann eine Netzwerkerfassung Informationen liefern. Stellen Sie sicher, dass die Netzwerkerfassung gleichzeitig ausgeführt wird, während das Problem angezeigt wird, damit es effizient analysiert werden kann. Beachten Sie auch den genauen Zeitpunkt, zu dem das Problem auftritt.

## Probleme mit der instabilen Verbindung {#issues-unstable-connection}

Eine Verbindung gilt als instabil, wenn einer der folgenden Ereignisse eintritt:

* Die Verbindung dauert weniger als eine Stunde. Adobe Campaign Classic Transmitterverbindungen sind eine Ausnahme aufgrund der Funktionsweise der Adobe Campaign Classic MTA.

* Der Anbieter sendet `UNBIND PDU`s.

* `enquire_link` Zeitüberschreitung, entweder auf der Adobe Campaign- oder auf der Anbieterseite. In diesem Fall wird `ENQUIRE_LINK_RESP` mit einem Fehlercode ungleich null angezeigt.

* Es gibt viele `BIND PDU`s. Je nach Anzahl der Verbindungen sollte es pro Tag nicht mehr als einige geben. Mehr als 1 BIND PDU pro Stunde sollte alarmiert werden.

Beheben von Problemen mit der Verbindungsstabilität:

* Unstable-Verbindungen sind selten die Ursache, es ist oft das Ergebnis eines anderen Problems, das eine Trennung auslöst. Die Suche nach der Ursache ist die Priorität.

* Aktivieren Sie ausführliche SMPP-Spuren. Sie werden sie benötigen, um zu sehen, was passiert, wenn die Verbindung neu gestartet wird.

* Wenn der Anbieter `BIND PDU`s sendet, kann etwas nicht stimmen. Fragen Sie Ihren Anbieter, warum `UNBING` gesendet wird.

* Eine Netzwerkerfassung ist manchmal die einzige Möglichkeit, zu sehen, wie die Verbindung geschlossen wird.

* Wenn der Anbieter die Verbindungen schließt, indem er entweder ein `TCP FIN` oder ein `TCP RST packet` sendet, fragen Sie Ihren Anbieter nach weiteren Informationen.

* Wenn der Anbieter die Verbindung schließt, nachdem er einen sauberen Fehler wie `DELIVER_SM_RESP` mit einem Fehlercode gesendet hat, muss er den Connector reparieren. Andernfalls wird verhindert, dass andere Arten von Nachrichten übertragen werden, und MTA-Einschränkungen ausgelöst. Dies ist besonders im Transceiver-Modus wichtig, wo das Schließen der Verbindung sowohl MT als auch SR beeinflusst.

## Problem beim Senden eines MT (normales SMS an einen Endbenutzer){#issue-MT}

* Überprüfen Sie, ob die Verbindung stabil ist. Eine SMPP-Verbindung sollte mindestens eine Stunde ununterbrochen in Betrieb bleiben, außer bei Sendern auf Adobe Campaign Classic. Siehe Abschnitt [Problem mit instabilen Verbindungen](../../delivery/using/sms-protocol.md#issues-unstable-connection).

* Wenn der Neustart des MTA dazu führt, dass das Senden von MT für eine kurze Zeit wieder funktioniert, haben Sie wahrscheinlich Einschränkungen wegen einer instabilen Verbindung. Siehe Abschnitt [Problem mit instabilen Verbindungen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Überprüfen Sie, ob das breite Protokoll vorhanden ist und im richtigen Status mit den richtigen Daten. Ist dies nicht der Fall, könnte es sich um ein Problem mit der Vorbereitung des Versands oder Versands handeln.

* Vergewissern Sie sich, dass die Nachricht tatsächlich vom MTA verarbeitet wird. Ist dies nicht der Fall, ist dies möglicherweise keine SMS-Ausgabe.

* Vergewissern Sie sich, dass der SMS-Anschluss tatsächlich an das Gerät des Anbieters angeschlossen ist. Bitten Sie den Anbieter um Feedback, um sicherzustellen, dass alle Systeme ordnungsgemäß kommunizieren. Informationen zum Bindungsprozess finden Sie unter `BIND_TRANSMITTER` und `BIND_TRANSCEIVER PDU`s. Möglicherweise müssen Sie SMPP-Traces aktivieren, um eine ordnungsgemäße Fehlerbehebung zu ermöglichen.

* Überprüfen Sie bei aktivierten SMPP-Traces, ob `SUBMIT_SM PDU` die richtigen Informationen enthält.

* Stellen Sie sicher, dass der Anbieter mit einem `SUBMIT_SM_RESP PDU`-Wert mit dem Wert &quot;OK&quot;(Code 0) antwortet. Stellen Sie sicher, dass die PDU mit einer angemessenen Verzögerung eintrifft: Alles, was länger als 1 Sekunde dauert, muss mit dem Anbieter besprochen werden, es kommt in der Regel in weniger als 100 ms.

* Wenn alle diese Schritte funktionieren, können Sie darauf vertrauen, dass das Problem auf der Anbieterseite auftritt. Sie müssen die Fehlerbehebung auf ihrer Plattform durchführen.

* Wenn es funktioniert, aber der Durchsatz inkonsistent ist, versuchen Sie, das sendende Fenster anzupassen und den MT-Durchsatz zu senken. Sie müssen mit dem Anbieter zusammenarbeiten, um dies anzupassen. Adobe Campaign kann sehr schnell Nachrichten senden, sodass Leistungsprobleme auf dem Gerät des Anbieters auftreten können.

## MT werden dupliziert (dieselbe SMS wird mehrere Male in einer Zeile gesendet){#duplicated-MT}

Duplikat werden oft von weiteren Zustellversuchen verursacht. Es ist normal, Duplikate beim erneuten Testen von Nachrichten zu haben, sollten Sie versuchen, stattdessen die Wurzel-Ursache von weiteren Zustellversuchen zu entfernen.

* Wenn Sie Duplikat sehen, die genau 60 Sekunden auseinander geschickt wurden, ist es wahrscheinlich ein Problem auf der Anbieterseite, sie senden nicht schnell genug ein `SUBMIT_SM_RESP`.

* Wenn Sie viele `BIND/UNBIND` sehen, haben Sie eine instabile Verbindung. Im Abschnitt [Problem mit instabilen Verbindungen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) finden Sie Lösungen, bevor Sie versuchen, Probleme mit Duplikat-Meldungen zu lösen.

Verringerung der Anzahl von Duplikaten bei Wiederholung:

* Reduzieren Sie das sendende Fenster. Das sendende Fenster sollte groß genug sein, um für `SUBMIT_SM_RESP` Latenz abzudecken. Der Wert stellt die maximale Anzahl von Meldungen dar, die dupliziert werden können, wenn ein Fehler auftritt, während das Fenster voll ist.

## Problem bei der Verarbeitung von SR (Versand-Empfangsbestätigungen) {#issue-process-SR}

* Sie benötigen SMPP-Traces, die für jede SR-Fehlerbehebung aktiviert sind.

* Überprüfen Sie, ob das `DELIVER_SM PDU` vom Anbieter kommt und ob es gut geformt ist.

* Überprüfen Sie, ob das Adobe Campaign rechtzeitig mit einem erfolgreichen `DELIVER_SM_RESP PDU` antwortet. Unter Adobe Campaign Classic garantiert dies, dass der SR in die Tabelle `providerMsgId` für die verzögerte Verarbeitung durch den SMS-Prozess eingefügt wurde.

Wenn `DELIVER_SM PDU` nicht erfolgreich bestätigt wurde, sollten Sie Folgendes überprüfen:

* Überprüfen Sie den Regex in Bezug auf die ID-Extraktion und die Fehlerverarbeitung im **Externe Konto**. Möglicherweise müssen Sie sie gegen den Inhalt von `DELIVER_SM PDU` validieren.

* Überprüfen Sie, ob die Fehler in der Tabelle `broadLogMsg` richtig bereitgestellt wurden.

Wenn das `DELIVER_SM PDU` vom Adobe Campaign Classic Extended SMPP Connector bestätigt wurde, das &quot;wideLog&quot;jedoch nicht ordnungsgemäß aktualisiert wurde, überprüfen Sie den im Abschnitt [Matching MT, SR und Broadlog Einträge](../../delivery/using/sms-protocol.md#matching-mt) beschriebenen ID-Abgleichungsprozess.

Wenn Sie alle Fehler behoben haben, aber einige ungültige SR-Regeln noch in den Puffern des Anbieters vorhanden sind, können Sie sie mit der Option &quot;Anzahl der ungültigen ID-Bestätigung&quot;überspringen. Dies sollte mit Vorsicht verwendet werden und so schnell wie möglich auf 0 zurückgesetzt werden, nachdem die Puffer sauber sind.

## Problem bei der Verarbeitung von MO (und Blacklisting/automatische Antwort){#issue-process-MO}

* Aktivieren Sie SMPP-Spuren während Tests. Wenn Sie TLS nicht aktivieren, sollten Sie bei der Fehlerbehebung von MO eine Netzwerkerfassung durchführen, um zu überprüfen, ob PDUs die richtigen Informationen enthalten und korrekt formatiert sind.

* Wenn Sie Netzwerkverkehr erfassen oder SMPP-Spuren analysieren, stellen Sie sicher, dass Sie die gesamte Konversation mit dem MO und seiner Antwort MT erfassen, wenn eine Antwort konfiguriert ist.

* Wenn das MO (`DELIVER_SM PDU`) nicht in den Spuren angezeigt wird, liegt das Problem auf der Anbieterseite. Sie müssen die Fehlerbehebung auf ihrer Plattform durchführen.

* Wenn `DELIVER_SM PDU` angezeigt wird, überprüfen Sie, ob es durch Adobe Campaign mit einem erfolgreichen `DELIVER_SM_RESP PDU` (Code 0) bestätigt wird. Diese RESP garantiert, dass die gesamte Verarbeitungslogik von Adobe Campaign angewendet wurde (automatische Antwort und Zulassen/Blockierungsliste). Wenn dies nicht der Fall ist, suchen Sie in den SMS-Prozessprotokollen nach einer Fehlermeldung.

* Wenn automatische Antworten aktiviert sind, überprüfen Sie, ob `SUBMIT_SM` an den Anbieter gesendet wurde. Ist dies nicht der Fall, wird garantiert, dass eine Fehlermeldung in den SMS-Prozessprotokollen gefunden wird.

* Wenn die `SUBMIT_SM MT PDU`, die die Antwort enthalten, in den Spuren gefunden wird, die SMS aber nicht zum Handy kommt, müssen Sie sich an den Anbieter wenden, um Hilfe bei der Fehlerbehebung zu erhalten.

## Problem bei der Vorbereitung des Versands ohne Ausschluss von isolierten Empfängern (durch die Funktion für die automatische Antwort isoliert) {#issue-delivery-preparation}

* Überprüfen Sie, ob das Telefonnummernformat in der Tabelle &quot;Quarantäne&quot;und im Versand-Protokoll identisch ist. Ist dies nicht der Fall, lesen Sie den Abschnitt [Abschnitt](../../delivery/using/sms-protocol.md#automatic-reply), wenn Sie Probleme mit dem Präfix plus des internationalen Telefonnummernformats haben.

* Prüfen Sie die Kurzcodes. Ausnahmen können auftreten, wenn der Kurzcode des Empfängers entweder mit dem im Externe Konto definierten oder mit leerem Code identisch ist (leer = beliebiger Kurzcode). Wenn nur ein Kurzcode für die gesamte Adobe Campaign-Instanz verwendet wird, ist es einfacher, alle **Kurzcode**-Felder leer zu lassen.

## Kodierungsprobleme {#encoding-issues}

**Schritt 1: Kontakt zum Anbieter**

Kontaktieren Sie sie und sehen Sie, was sie haben. Sie sollten Ihnen sagen können, ob das Problem auf ihrer Seite oder auf der Adobe Campaign-Seite liegt. Wenn das Problem im Adobe Campaign liegt, sollten sie Ihnen genau sagen können, welches Feld falsch ist.

**Schritt 2: Was in Ihrer Nachricht enthalten ist**

Unicode erlaubt viele Varianten für aussehende Zeichen und Adobe Campaign kann nicht alle umgehen.

Die häufigste Ursache für Probleme ist eine Kopieren-Einfügen aus einem Textverarbeitungsprogramm, das die üblichen Zeichen in typografisch korrekte Versionen ändert: Leerzeichen wurden zu geschützten Leerzeichen, Dubletten-Anführungszeichen zu öffnenden und schließenden Anführungszeichen, Minuszeichen zu verschiedenen Trennstrichen usw. geändert.

Kopieren Sie Ihre Nachricht beim Testen nicht, sondern geben Sie sie immer direkt in die Benutzeroberfläche ein.

Mit hexadezimalen Zeichen können Sie den Unterschied zwischen ähnlichen Zeichen erkennen. Ein Kleinbuchstabe L, ein Großbuchstabe I, O, 0, alle verschiedenen Arten von Anführungszeichen, Nicht-Lateinkodierungen oder sogar verschiedene Arten von Leerzeichen können alle gleich aussehen oder gar nicht angezeigt werden.

Um Unicode in Hexadezimal zu konvertieren, können Sie Online-Tools wie die Website [Unicode-Codekonverter](https://r12a.github.io/app-conversion/) verwenden. Geben Sie Ihren Text ein, vergewissern Sie sich, dass keine PII wie Telefonnummern vorhanden sind, und klicken Sie auf **Konvertieren**. Die Hexadezimalwerte werden unten angezeigt (UTF-32-Zone).

Wenn Sie Tickets zu Kodierungsproblemen öffnen, egal ob mit dem Anbieter oder dem Adobe Campaign, fügen Sie immer eine Hexadezimalversion des von Ihnen eingegebenen und angezeigten Artikels bei.

**Schritt 3: Was Sie senden sollten**

Legen Sie die Kodierung fest, die Sie erwarten, und suchen Sie online nach der entsprechenden Zeichentabelle. Vergewissern Sie sich, dass die Zeichen, die Sie senden möchten, tatsächlich auf der Codepage der Zielgruppe verfügbar sind. Überprüfen Sie, ob das Feld `data_coding` korrekt ist und mit dem übereinstimmt, was Sie und der Anbieter erwarten.

**Schritt 4: Wissen, was Sie tatsächlich gesendet haben**

Sie benötigen die Debug-Ausgabe des Connectors, um genau zu sehen, welche Bytes Sie an den Provider senden. Kodierungsprobleme werden in `SUBMIT_SM PDU`s angezeigt. Achten Sie daher darauf, sie zu erfassen. Senden Sie sehr unterschiedliche Nachrichten, die im Protokoll leicht zu finden sind.

Senden Sie beim Testen verschiedene Sonderzeichen. Beispielsweise enthält die GSM7-Kodierung erweiterte Zeichen, die sich in ihrer hexadezimalen Form sehr unterscheiden. Sie sind leicht zu erkennen, da sie in keiner anderen Kodierung angezeigt werden.

## Zu berücksichtigende Elemente bei der Kommunikation über ein SMS-Problem {#element-include}

Wenn Sie Hilfe bei einer SMS-Frage suchen, ob es ein Support-Ticket für Adobe Campaign, den SMS-Provider oder eine andere Art der Kommunikation zu diesem Problem öffnet, müssen Sie die folgenden Informationen eintragen, um sicherzustellen, dass es ordnungsgemäß qualifiziert ist. Richtig qualifizierte Probleme sind der Schlüssel zur schnelleren Lösung von Problemen.

* **Aktivieren Sie ausführliche SMPP-** Meldungen, wenn das Problem angezeigt wird. Die meisten SMS-Probleme lassen sich ohne diese nicht lösen.

* Wenn das Problem mit dem SMS-Traffic zusammenhängt, wenden Sie sich zuerst an den Anbieter. Ihre Plattform eignet sich am besten zur effizienten Diagnose von SMS-Verkehrsproblemen in Echtzeit.

* Schließen Sie eine kurze, aber sachliche Beschreibung des Problems ein.

* Geben Sie eine Beschreibung des erwarteten Ergebnisses ein.

* Schließen Sie das Feedback des Anbieters ein.

* Schließen Sie relevante Protokolle und/oder Netzwerkaufnahmen ein. Achten Sie bei der Erfassung darauf, das Problem während der Erfassung zu reproduzieren.

* Wenn Sie Protokolle, Spuren oder Aufnahmen einschließen, bestimmen Sie den genauen Speicherort in der Datei, wenn das Problem auftritt.

* Wenn Sie auf Nachrichten, PDUs oder Protokolle verweisen, geben Sie deren Zeitstempel deutlich an, um sie leichter zu finden.

* Versuchen Sie, das Problem auf einer Umgebung zu reproduzieren. Wenn Sie sich bezüglich einer Einstellung nicht sicher sind, probieren Sie sie in der Test-Umgebung aus und überprüfen Sie das Ergebnis mit den SMPP-Spuren. Normalerweise ist es besser, Probleme zu melden, die auf Umgebung des Tests repliziert wurden, als Probleme mit dem Berichte auf Umgebung der Produktion.

* Schließen Sie alle Änderungen oder Änderungen ein, die auf der Plattform vorgenommen wurden. Schließen Sie außerdem alle Änderungen ein, die der Anbieter möglicherweise auf seiner Seite vorgenommen hat.

### Netzwerkerfassung {#network-capture}

Eine Netzwerkerfassung ist nicht immer erforderlich, meist sind ausführliche SMPP-Nachrichten ausreichend. Im Folgenden finden Sie einige Richtlinien, die Ihnen dabei helfen, festzustellen, ob eine Netzwerkerfassung erforderlich ist:

* Verbindungsprobleme, aber die ausführlichen Meldungen zeigen kein `BIND_RESP PDU` an.

* Unerklärtes Trennen von Verbindungen ohne Fehlermeldung, das übliche Verhalten des Connectors bei der Erkennung eines Protokollfehlers auf niedriger Ebene.

* Der Anbieter beklagt sich über den Prozess der Aufhebung/Trennung der Verbindung.

* Kodierungsprobleme in optionalen TLV-Feldern.

* Es wird vermutet, dass der Traffic zwischen verschiedenen Verbindungen gemischt wird.

In allen anderen Situationen sollten Sie zunächst ausführliche SMPP-Meldungen analysieren und nur dann eine Netzwerkerfassung anfordern, wenn Informationen in den ausführlichen Protokollen fehlen.

In einigen Fällen ist die Erfassung des Netzwerkverkehrs nicht erforderlich. Die häufigsten Situationen sind:

* TLS aktiviert: Der TLS-Traffic ist per Definition verschlüsselt, sodass er nicht erfasst werden kann.

* Leistungsprobleme: Protokolle enthalten alle erforderlichen Informationen zur Verfolgung von Leistungsproblemen.

* Timing-Probleme (`retry timing`, `enquire_link` Punkt, Durchsatzbegrenzung usw.)

* SR-Analyse und -Verarbeitung: Ausführliche Protokolle geben viel mehr Kontext und eine bessere Präsentation.

* MO-Verarbeitung (automatische Antworten, Quarantäne).

* Fehler ohne SMPP-Traffic: Vorbereitung des Versands, Probleme mit der Message Center-API, Workflow-Probleme usw.

## Aktivieren von SMPP-Spuren {#enabling-smpp-traces}

Neuer Connector unterstützt erweiterte Protokollierung durch Spuren: SMPP. Traces werden im MTA-Protokoll und nicht in der Standardausgabe ausgegeben.

**Aktivieren pro Externe Konto (bevorzugte Methode)**

1. Aktivieren Sie im Externe Konto **die Option** Ausführliche SMPP-Spuren in der Protokolldatei **aktivieren.**
1. Warten Sie 10 Minuten, damit der Server die Externe Konti neu laden kann.

Sie sollte jetzt aktiv sein.

**Aktivieren in der Konfiguration**

Legen Sie in der Datei `config-instance.xml` die folgenden Parameter fest:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Überprüfen der Anzahl offener Verbindungen auf einem Container {#open-connections}

Um die Anzahl der geöffneten Verbindungen auf einem Container zu überprüfen, können Sie den folgenden Befehl verwenden:

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Dadurch wird die Anzahl der Verbindungen, die für einen bestimmten Port geöffnet werden, Liste. Hier benutzen wir den Port 3600.

Das Ergebnis sollte wie folgt lauten:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 offene Verbindungen für den sms Prozess und 2 pro mta Kind mit 5 Kindern.
