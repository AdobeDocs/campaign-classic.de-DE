---
solution: Campaign Classic
product: campaign
title: Protokoll und Einstellungen des SMS-Connectors
description: Erfahren Sie mehr über den SMS-Connector und dessen Konfiguration.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: ht
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: ht
source-wordcount: '2751'
ht-degree: 100%

---


# SMS-Fehlerbehebung {#troubleshooting-sms}

## Konflikt zwischen verschiedenen externen Konten {#external-account-conflict}

Wenn die Instanz über mehrere externe SMS-Konten verfügt, müssen Sie sicherstellen, dass Probleme nicht durch einen Konflikt zwischen externen Konten verursacht werden.

Adobe Campaign behandelt externe Konten als nicht verwandte Entitäten.

Wenn Sie mehrere Konten haben, gehen Sie wie folgt vor, um das externe Konto zu isolieren, das Probleme verursacht:

1. Deaktivieren Sie alle externen Konten.
1. Aktivieren Sie ein externes Konto.
1. Versuchen Sie, das Problem zu reproduzieren.
1. Wenn das anfängliche Problem nicht immer auftritt, führen Sie eine angemessene Anzahl von Versuchen durch, bevor Sie Ihre Schlussfolgerung ziehen.
1. Wenn das Problem bei diesem einen Konto nicht auftritt, deaktivieren Sie es und beginnen Sie erneut mit Schritt 2 beim nächsten Konto.

Nachdem Sie jedes Konto einzeln geprüft haben, gibt es zwei mögliche Szenarien:

* **Das Problem trat bei einem oder mehreren Konten auf**

   In diesem Fall können Sie für jedes Konto andere Verfahren zur Fehlerbehebung anwenden. Es ist am besten, andere Konten zu deaktivieren, während Sie ein Konto diagnostizieren, um den Netzwerk-Traffic und die Anzahl der Logs zu reduzieren.

* **Das Problem trat nicht auf, wenn jeweils nur ein Konto aktiv war**

   Es gibt einen Konflikt zwischen den Konten. Wie bereits erwähnt, behandelt Adobe Campaign die Konten einzeln, aber der Provider behandelt sie möglicherweise als ein einziges Konto.

   * Sie verwenden unterschiedliche Anmelde-/Kennwortkombinationen für alle Ihre Konten.
Sie müssen den Provider kontaktieren, um potenzielle Konflikte auf dessen Seite zu diagnostizieren.

   * Einige der externen Konten verwenden dieselbe Anmelde-/Kennwortkombination.
Der Anbieter kann nicht feststellen, von welchem externen Konto die `BIND PDU` stammt, also behandelt er alle Verbindungen von mehreren Konten als eine einzige. Möglicherweise wurden MO und SR wahllos über die beiden Konten geleitet, was zu Problemen führt.
Wenn der Provider mehrere Kurzwahlnummern für dieselbe Anmelde-/Kennwortkombination unterstützt, müssen Sie ihn fragen, wo diese Kurzwahlnummer in die `BIND PDU` eingefügt werden soll. Beachten Sie, dass diese Information in die `BIND PDU` und nicht in `SUBMIT_SM` eingefügt werden muss, da nur in der `BIND PDU` eine korrekte Weiterleitung von MOs möglich ist.
Siehe den Abschnitt [Informationen in den verschiedenen PDU-Arten](../../delivery/using/sms-protocol.md#information-pdu) weiter oben, um zu erfahren, welches Feld in `BIND PDU` verfügbar ist. Normalerweise fügen Sie die Kurzwahlnummer in `address_range` hinzu. Dies erfordert jedoch besondere Unterstützung durch den Provider. Wenden Sie sich an diesen, um zu erfahren, wie er mehrere Kurzwahlnummern unabhängig voneinander weiterleiten wird.
Adobe Campaign unterstützt die Verarbeitung mehrerer Kurzwahlnummern in demselben externen Konto.

## Problem mit dem externen Konto im Allgemeinen {#external-account-issues}

* Untersuchen Sie, ob und von wem der Connector kürzlich geändert wurde (überprüfen Sie die externen Konten als Gruppe).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Untersuchen Sie (im Verzeichnis &quot;/postupgrade&quot;), ob und wann das System aktualisiert wurde.
* Untersuchen Sie, ob Pakete, die sich auf SMS auswirken, kürzlich aktualisiert wurden (/var/log/dpkg.log).

## Problem mit Mid-Sourcing (gehostet){#issue-mid-sourcing}

* Wenn das Problem in einer Mid-Sourcing-Umgebung auftritt, stellen Sie sicher, dass die Versand-Logs und die broadLogs ordnungsgemäß auf dem Mid-Sourcing-Server erstellt und aktualisiert werden. Wenn das nicht der Fall ist, liegt kein SMS-Problem vor.

* Wenn auf dem Mid-Sourcing-Server alles funktioniert und SMS ordnungsgemäß gesendet werden, die Marketing-Instanz jedoch nicht ordnungsgemäß aktualisiert wird, liegt möglicherweise ein Problem mit der Mid-Synchronisation vor.

## Problem beim Herstellen einer Verbindung zum Provider {#issue-provider}

* Wenn die `BIND PDU` einen `command_status`-Code ungleich Null zurückgibt, fragen Sie den Provider nach weiteren Informationen.

* Überprüfen Sie, ob das Netzwerk ordnungsgemäß konfiguriert ist, damit die TCP-Verbindung zum Provider hergestellt werden kann.

* Bitten Sie den Provider, zu überprüfen, ob die IP-Adressen ordnungsgemäß zur Zulassungsliste der Adobe Campaign-Instanz hinzugefügt wurden.

* Überprüfen Sie die Einstellungen für **externe Konten**. Fragen Sie den Provider nach dem Wert der Felder.

* Wenn die Verbindung erfolgreich, aber instabil ist, lesen Sie den Abschnitt [Probleme mit instabilen Verbindungen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Wenn Verbindungsprobleme schwer zu diagnostizieren sind, kann eine Netzwerkaufzeichnung Informationen liefern. Achten Sie darauf, dass die Netzwerkaufzeichnung läuft, während das Problem auftritt, damit es effizient analysiert werden kann. Sie sollten auch den genauen Zeitpunkt notieren, zu dem das Problem auftritt.

## Probleme mit instabilen Verbindungen {#issues-unstable-connection}

Eine Verbindung wird als instabil angesehen, wenn eine der folgenden Situationen eintritt:

* Die Verbindung besteht für weniger als eine Stunde. Dies gilt jedoch nicht für Transmitter-Verbindungen, was mit der Funktionsweise des MTA von Adobe Campaign Classic zusammenhängt.

* Der Provider sendet `UNBIND PDU`s.

* Das `enquire_link`-Zeitlimit wird entweder auf der Adobe Campaign-Seite oder auf der Provider-Seite überschritten. In diesem Fall wird möglicherweise `ENQUIRE_LINK_RESP` mit einem Fehler-Code ungleich Null angezeigt.

* Es gibt viele `BIND PDU`s. Abhängig von der Anzahl der Verbindungen sollten an einem Tag nicht mehr als ein paar vorhanden sein. Mehr als 1 BIND PDU pro Stunde ist alarmierend.

Beheben von Problemen mit der Verbindungsstabilität:

* Instabile Verbindungen sind selten die eigentliche Ursache. Sie sind häufig das Ergebnis eines anderen Problems, das einen Verbindungsabbruch auslöst. Die Suche nach der eigentlichen Ursache hat Priorität.

* Aktivieren Sie die ausführliche SMPP-Verfolgung. Sie benötigen diese, um zu sehen, was passiert, wenn die Verbindung neu gestartet wird.

* Wenn der Provider `BIND PDU`s sendet, stimmt möglicherweise etwas nicht. Fragen Sie Ihren Provider, warum `UNBING` gesendet wird.

* Eine Netzwerkaufzeichnung ist manchmal die einzige Möglichkeit, um zu sehen, wie die Verbindung geschlossen wird.

* Wird die Verbindung vonseiten des Providers durch Versenden von `TCP FIN` oder `TCP RST packet` geschlossen, wenden Sie sich an diesen, um weitere Informationen zu erhalten.

* Wenn der Provider die Verbindung schließt, nachdem er einen ordnungsgemäßen Fehler wie `DELIVER_SM_RESP` mit einem Fehler-Code gesendet hat, muss er seinen Connector reparieren. Andernfalls wird verhindert, dass andere Arten von Nachrichten übertragen werden, und die MTA-Drosselung wird ausgelöst. Dies ist besonders im Transceiver-Modus wichtig, wo sich das Schließen der Verbindung sowohl auf MT als auch auf SR auswirkt.

## Problem beim Senden von MT (reguläre SMS an einen Endbenutzer){#issue-MT}

* Überprüfen Sie, ob die Verbindung stabil ist. Eine SMPP-Verbindung sollte mindestens eine Stunde durchgängig bestehen (außer bei Transmittern in Adobe Campaign Classic). Weitere Informationen finden Sie im Abschnitt [Probleme mit instabilen Verbindungen](../../delivery/using/sms-protocol.md#issues-unstable-connection).

* Wenn durch einen Neustart des MTA das Senden von MT für einen kurzen Zeitraum wieder funktioniert, besteht wahrscheinlich eine Drosselung aufgrund einer instabilen Verbindung. Weitere Informationen finden Sie im Abschnitt [Probleme mit instabilen Verbindungen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Überprüfen Sie, ob das Broadlog vorhanden ist und den richtigen Status mit den richtigen Daten aufweist. Ist dies nicht der Fall, könnte es sich um ein Problem beim Versand oder bei der Versandvorbereitung handeln.

* Prüfen Sie, ob der MTA die Nachricht tatsächlich verarbeitet. Ist dies nicht der Fall, handelt es sich möglicherweise nicht um ein SMS-Problem.

* Prüfen Sie, ob der SMS-Connector tatsächlich mit den Geräten des Providers verbunden ist. Bitten Sie den Provider um Rückmeldung, um sicherzustellen, dass alle Systeme richtig kommunizieren. Informationen zum Bindungsprozess finden Sie unter `BIND_TRANSMITTER` und `BIND_TRANSCEIVER PDU`s. Möglicherweise müssen Sie SMPP-Traces aktivieren, um eine ordnungsgemäße Fehlerbehebung zu ermöglichen.

* Überprüfen Sie bei aktivierten SMPP-Traces, ob `SUBMIT_SM PDU` die richtigen Informationen enthält.

* Stellen Sie sicher, dass der Provider mit einem `SUBMIT_SM_RESP PDU` mit dem Wert &quot;OK&quot; (Code 0) antwortet. Stellen Sie sicher, dass die PDU mit einer angemessenen Verzögerung eintrifft: Alles, was länger als 1 Sekunde ist, muss mit dem Provider besprochen werden. Sie kommt normalerweise in weniger als 100 ms an.

* Wenn alle diese Schritte funktionieren, können Sie sicher sein, dass das Problem auf der Seite des Providers liegt. Er muss dann die Fehlersuche auf seiner Plattform durchführen.

* Wenn es funktioniert, der Durchsatz jedoch inkonsistent ist, versuchen Sie, das Übertragungsfenster anzupassen und den MT-Durchsatz zu verringern. Für diese Anpassung müssen Sie mit dem Provider zusammenarbeiten. Adobe Campaign kann Nachrichten sehr schnell senden, so dass Leistungsprobleme auf den Geräten des Providers auftreten können.

## MT wird dupliziert (dieselbe SMS wird mehrmals hintereinander gesendet){#duplicated-MT}

Duplikate werden häufig durch Wiederholungsversuche verursacht. Es ist normal, dass Duplikate auftreten, wenn Nachrichten wiederholt gesendet werden. Sie sollten stattdessen versuchen, die Ursache für die Wiederholungen zu beseitigen.

* Wenn Sie sehen, dass Duplikate im Abstand von genau 60 Sekunden gesendet werden, ist dies wahrscheinlich ein Problem auf der Seite des Providers, der die `SUBMIT_SM_RESP` nicht schnell genug sendet.

* Wenn Sie viele `BIND/UNBIND` sehen, haben Sie eine instabile Verbindung. Suchen Sie zuerst Lösungen im Abschnitt [Probleme mit instabilen Verbindungen](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection), bevor Sie versuchen, Probleme mit doppelten Nachrichten zu lösen.

Verringerung der Anzahl von Duplikaten bei einer Wiederholung:

* Reduzieren Sie das Übertragungsfenster. Das Übertragungsfenster sollte groß genug sein, um die Latenz der `SUBMIT_SM_RESP` abzudecken. Sein Wert stellt die maximale Anzahl von Nachrichten dar, die dupliziert werden können, wenn ein Fehler auftritt, während das Fenster voll ist.

## Problem bei der Verarbeitung von SR (Empfangsbestätigungen) {#issue-process-SR}

* Sie müssen SMPP-Traces aktivieren, um jegliche Art von SR-Fehlerbehebung durchzuführen.

* Überprüfen Sie, ob die `DELIVER_SM PDU` vom Provider kommt und korrekt formuliert ist.

* Überprüfen Sie, ob Adobe Campaign rechtzeitig mit einer erfolgreichen `DELIVER_SM_RESP PDU` antwortet. Diese gewährleistet in Adobe Campaign Classic, dass der SR in die Tabelle `providerMsgId` eingefügt wurde, um die verzögerte Verarbeitung durch den SMS-Prozess zu ermöglichen.

Wenn die `DELIVER_SM PDU` nicht erfolgreich quittiert wurde, sollten Sie Folgendes überprüfen:

* Überprüfen Sie den Regex für die ID-Extraktion und die Fehlerverarbeitung im **externen Konto**. Möglicherweise müssen Sie diese anhand des Inhalts von `DELIVER_SM PDU` validieren.

* Überprüfen Sie, ob die Fehler in der Tabelle `broadLogMsg` richtig bereitgestellt wurden.

Wenn die `DELIVER_SM PDU` vom erweiterten SMPP-Connector in Adobe Campaign Classic quittiert wurde, das broadLog jedoch nicht ordnungsgemäß aktualisiert wird, überprüfen Sie den im Abschnitt [Abgleichen von MT-, SR- und broadLog-Einträgen](../../delivery/using/sms-protocol.md#matching-mt) beschriebenen Prozess zur ID-Abstimmung.

Wenn Sie alle Probleme behoben haben, die Puffer des Providers jedoch noch einige ungültige SR enthalten, können Sie diese mit der Option &quot;Zählung der &#39;ungültige ID&#39; Antworten&quot; überspringen. Dies sollte mit Vorsicht verwendet und so schnell wie möglich auf 0 zurückgesetzt werden, nachdem die Puffer bereinigt wurden.

## Problem bei der Verarbeitung von MO (und Blockierungsauflistung/automatische Antwort){#issue-process-MO}

* Aktivieren Sie SMPP-Traces während der Tests. Wenn Sie TLS nicht aktivieren, sollten Sie bei der Fehlerbehebung bei MO eine Netzwerkaufzeichnung durchführen, um zu überprüfen, ob die PDUs die richtigen Informationen enthalten und ordnungsgemäß formatiert sind.

* Wenn Sie Netzwerk-Traffic aufzeichnen oder SMPP-Traces analysieren, stellen Sie sicher, dass Sie die gesamte Konversation mit dem MO und seiner Antwort-MT erfassen, wenn eine Antwort konfiguriert ist.

* Wenn MO (`DELIVER_SM PDU`) nicht in Traces angezeigt wird, liegt das Problem auf der Seite des Providers. Er muss dann die Fehlersuche auf seiner Plattform durchführen.

* Wenn `DELIVER_SM PDU` angezeigt wird, überprüfen Sie, ob sie von Adobe Campaign mit einer erfolgreichen `DELIVER_SM_RESP PDU` (Code 0) quittiert wird. Diese RESP garantiert, dass die gesamte Verarbeitungslogik von Adobe Campaign angewendet wurde (automatische Antwort und Zulassungs-/Blockierungsliste). Wenn dies nicht der Fall ist, überprüfen Sie die Logs des SMS-Prozesses auf eine Fehlermeldung.

* Wenn automatische Antworten aktiviert sind, überprüfen Sie, ob `SUBMIT_SM` an den Provider gesendet wurde. Ist das nicht der Fall, können Sie davon ausgehen, dass die Logs des SMS-Prozesses eine Fehlermeldung enthalten.

* Wenn die `SUBMIT_SM MT PDU`, die die Antwort enthält, in Traces gefunden wird, die SMS aber nicht auf dem Mobiltelefon ankommt, müssen Sie sich an den Provider wenden, um Unterstützung bei der Fehlerbehebung zu erhalten.

## Problem bei der Versandvorbereitung, die Empfänger unter Quarantäne nicht ausschließt (durch die automatische Antwortfunktion in Quarantäne gestellt) {#issue-delivery-preparation}

* Überprüfen Sie, ob die Telefonnummern in der Quarantänetabelle und im Versand-Log im exakt gleichen Format vorliegen. Ist dies nicht der Fall, gehen Sie zu diesem [Abschnitt](../../delivery/using/sms-protocol.md#automatic-reply), wenn Sie Probleme mit dem &quot;+&quot;-Präfix des internationalen Telefonnummernformats haben.

* Prüfen Sie die Kurzwahlnummern. Es kann zu Ausschlüssen kommen, wenn die Kurzwahlnummer des Empfängers entweder dieselbe ist, wie im externen Konto definiert, oder wenn sie leer ist (leer = beliebige Kurzwahlnummer). Wenn nur eine Kurzwahlnummer für die gesamte Adobe Campaign-Instanz verwendet wird, ist es einfacher, alle Felder mit **Kurzwahlnummern** leer zu lassen.

## Kodierungsprobleme {#encoding-issues}

**Schritt 1: Kontaktaufnahme mit dem Provider**

Nehmen Sie Kontakt mit ihm auf und fragen Sie nach, ob es ein Problem gibt. Er sollte Ihnen mitteilen können, ob das Problem auf seiner Seite oder auf der Seite von Adobe Campaign liegt. Wenn das Problem in Adobe Campaign auftritt, sollte er Ihnen genau mitteilen können, welches Feld falsch ist.

**Schritt 2: Inhalt Ihrer Nachricht überprüfen**

Unicode erlaubt viele Varianten für ähnliche Zeichen, und Adobe Campaign kann nicht alle verarbeiten.

Die häufigste Ursache für Probleme ist das Kopieren und Einfügen aus einem Textverarbeitungsprogramm, das gängige Zeichen in typografisch korrekte Versionen umwandelt, z. B. Leerzeichen in feste Leerzeichen, doppelte Anführungszeichen in öffnende und schließende Anführungszeichen, Minuszeichen in verschiedene Arten von Bindestrichen usw.

Kopieren Sie Ihre Nachricht beim Testen nicht, sondern geben Sie sie immer direkt in die Benutzeroberfläche ein.

Bei hexadezimalen Zeichen können Sie den Unterschied zwischen ähnlichen Zeichen erkennen. Ein kleines L, ein großes I, O, 0, alle verschiedenen Arten von Anführungszeichen, nicht-lateinische Kodierungen oder sogar verschiedene Arten von Leerzeichen können alle gleich aussehen oder gar nicht angezeigt werden.

Um Unicode in hexadezimale Werte zu konvertieren, können Sie Online-Tools wie die Website [Unicode-Codekonverter](https://r12a.github.io/app-conversion/) verwenden. Geben Sie Ihren Text ein, vergewissern Sie sich, dass keine persönlichen Informationen wie Telefonnummern vorhanden sind, und klicken Sie auf **Konvertieren**. Die hexadezimalen Werte werden unten angezeigt (UTF-32-Zone).

Geben Sie beim Öffnen von Tickets für Kodierungsprobleme, sei es beim Provider oder bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), immer eine hexadezimale Version Ihrer Eingabe und Ihrer Anzeige an.

**Schritt 3: Überprüfen, was Sie senden sollten**

Legen Sie die Kodierung fest, die Sie voraussichtlich verwenden werden, und suchen Sie online nach der Zeichentabelle. Vergewissern Sie sich, dass die Zeichen, die Sie senden möchten, tatsächlich in dieser Zeichenumsetztabelle verfügbar sind. Überprüfen Sie, ob das Feld `data_coding` korrekt ist und mit dem übereinstimmt, was Sie und der Provider erwarten.

**Schritt 4: Überprüfen, was Sie tatsächlich gesendet haben**

Sie benötigen die Debug-Ausgabe des Connectors, um genau zu sehen, welche Bytes Sie an den Provider senden. Kodierungsprobleme werden in `SUBMIT_SM PDU`s angezeigt. Zeichnen Sie sie daher unbedingt auf. Senden Sie gut erkennbare Nachrichten, die im Log leicht zu finden sind.

Senden Sie beim Testen verschiedene Sonderzeichen. Zum Beispiel enthält die GSM7-Kodierung erweiterte Zeichen, deren hexadezimale Form sich von anderen sehr unterscheidet. Sie sind leicht zu erkennen, da sie in keiner anderen Kodierung vorkommen.

## Elemente, die bei der Kommunikation über ein SMS-Problem berücksichtigt werden müssen {#element-include}

Wann immer Sie um Unterstützung bei einem SMS-Problem bitten, sei es beim Öffnen eines Support-Tickets bei Adobe Campaign, beim SMS-Provider oder bei jeder Art von Kommunikation über das Problem, müssen Sie die folgenden Informationen angeben, um sicherzustellen, dass das Problem richtig qualifiziert wird. Richtig qualifizierte Probleme sind der Schlüssel zur schnelleren Lösung von Problemen.

* **Aktivieren Sie ausführliche SMPP-Meldungen**, wenn das Problem auftritt. Die meisten SMS-Probleme lassen sich nur damit lösen.

* Wenn das Problem mit dem SMS-Traffic zusammenhängt, wenden Sie sich zuerst an den Provider. Deren Plattform ist für eine effiziente Diagnose von SMS-Traffic-Problemen in Echtzeit am besten geeignet.

* Fügen Sie eine kurze, sachliche Beschreibung des Problems bei.

* Fügen Sie eine Beschreibung des erwarteten Ergebnisses bei.

* Fügen Sie die Rückmeldung des Providers bei.

* Fügen Sie relevante Logs und/oder Netzwerkaufzeichnungen bei. Achten Sie bei der Aufzeichnung darauf, das Problem während der Aufzeichnung zu reproduzieren.

* Wenn Sie Logs, Traces oder Aufzeichnungen beifügen, geben Sie die genaue Stelle in der Datei an, an der das Problem auftritt.

* Wenn Sie auf Nachrichten, PDUs oder Logs verweisen, geben Sie deren Zeitstempel an, damit sie leichter zu finden sind.

* Versuchen Sie, das Problem in einer Testumgebung zu reproduzieren. Wenn Sie sich bei einer Einstellung nicht sicher sind, versuchen Sie sie in der Testumgebung und überprüfen Sie das Ergebnis mit SMPP-Traces. In der Regel ist es besser, in Testumgebungen replizierte Probleme zu melden, als Probleme in Produktionsumgebungen direkt zu melden.

* Fügen Sie alle Änderungen oder Optimierungen hinzu, die auf der Plattform vorgenommen wurden. Schließen Sie auch alle Änderungen ein, die der Provider möglicherweise auf seiner Seite vorgenommen hat.

### Netzwerkaufzeichnung {#network-capture}

Eine Netzwerkaufzeichnung ist nicht immer erforderlich. In der Regel reichen ausführliche SMPP-Meldungen aus. Im Folgenden finden Sie einige Richtlinien, anhand derer Sie feststellen können, ob eine Netzwerkaufzeichnung erforderlich ist:

* Verbindungsprobleme, aber in den ausführlichen Meldungen werden keine `BIND_RESP PDU` angezeigt.

* Ungeklärte Verbindungsabbrüche ohne Fehlermeldung, das übliche Verhalten des Connectors, wenn er einen Protokollfehler auf niedriger Ebene erkennt.

* Der Provider beschwert sich über Verbindungsabbrüche.

* Kodierungsprobleme in optionalen TLV-Feldern.

* Es wird vermutet, dass der Traffic zwischen verschiedenen Verbindungen vermischt ist.

Überprüfen Sie in allen anderen Situationen zunächst die ausführlichen SMPP-Meldungen. Eine Netzwerkaufzeichnung sollten Sie nur anfordern, wenn die ausführlichen Logs keinen Aufschluss geben.

In einigen Fällen ist die Aufzeichnung des Netzwerk-Traffic nicht erforderlich. Die häufigsten Situationen sind:

* TLS aktiviert: Der TLS-Traffic ist von vornherein verschlüsselt, sodass er nicht aufgezeichnet werden kann.

* Leistungsprobleme: Die Logs enthalten alle erforderlichen Informationen zum Verfolgen von Leistungsproblemen.

* Timing-Probleme (`retry timing`, `enquire_link`-Zeitraum, Durchsatzbegrenzung usw.)

* SR-Analyse und -Verarbeitung: Ausführliche Logs bieten viel mehr Kontext und eine bessere Darstellung.

* MO-Verarbeitung (automatische Antworten, Quarantäne).

* Fehler, die nicht den eigentlichen SMPP-Traffic betreffen: Versandvorbereitung, Probleme mit der Message Center-API, Workflow-Probleme usw.

## Aktivieren von SMPP-Traces{#enabling-smpp-traces}

Der neue Connector unterstützt die erweiterte Protokollierung durch Traces: SMPP. Trace-Ergebnisse werden im MTA-Log und nicht in der Standardausgabe ausgegeben.

**Aktivieren pro externem Konto (bevorzugte Methode)**

1. Aktivieren Sie im **externen Konto** die Option **Ausführliche SMPP-Protokolle in der Log-Datei aktivieren**.
1. Warten Sie zehn Minuten, bis der Server die externen Konten neu geladen hat.

Jetzt sollten sie aktiv sein.

**Aktivieren in der Konfiguration**

Legen Sie in der `config-instance.xml`-Datei die folgenden Parameter fest:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Überprüfen der Anzahl offener Verbindungen eines Containers {#open-connections}

Mit dem folgenden Befehl können Sie die Anzahl der offenen Verbindungen eines Containers überprüfen:

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Damit wird die Anzahl der offenen Verbindungen für einen bestimmten Port aufgelistet. Hier verwenden wir den Port 3600.

Das Ergebnis sollte wie folgt lauten:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

Vier geöffnete Verbindungen für den SMS-Prozess und zwei pro untergeordnetem MTA-Element mit fünf untergeordneten Elementen.
