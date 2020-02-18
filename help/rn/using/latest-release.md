---
title: Neueste Version
description: Neueste Version
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 78c94268723e172b4a4e3c3a965877978b075b82

---


# Neueste Version{#latest-release}

[Build-Aktualisierung](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | [Systemsteuerung](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) | [Aktualisierungen](../../rn/using/documentation-updates.md) der Dokumentation| [Frühere Versionen](../../rn/using/release--19-2.md) | [Veraltete Funktionen](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/green3.png"/><strong>Allgemeine Verfügbarkeit</strong></td>
   <td><img src="assets/blue3.png"/><strong>Release Candidate</strong></td> 
   <td><img src="assets/orange3.png"/><strong>Nicht mehr verfügbar</strong></td> 
   <td><img src="assets/red3.png"/><strong>Veraltet</strong></td> 
  </tr> 
   <tr> 
   <td>Neueste stabile Version verfügbar. <br>Erstellen validiert in Produktion. </td>
   <td>Erstellen von Adobe validiert <br>Warte auf Proof. </td>
   <td>Neuere Version mit Fehlerbehebungen verfügbar. <br>Aktualisierung erforderlich. </td>
   <td>Enthält bekannte Regressionen. <br>Aktualisierung ist obligatorisch. </td>
  </tr> 
 </tbody> 
</table>

Klicken Sie [hier](../../rn/using/release--19-1.md#release-19-1-4-build-9032) , um den **letzten stabilen Build** (GA) anzuzeigen.

## ![](assets/blue-2.png) Version 20.1 - Build 9122 {#release-20-1-build-XXXX}

_17. Februar 2020_

**Neue Funktionen?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake ist ein vollständig verwaltetes Cloud Data Warehouse, das sowohl auf Speicher- als auch auf Computerebene skaliert werden kann. Mit diesem neuen Connector kann Adobe Campaign jetzt die Leistung von Snowflake nutzen, um eine Big Data-Segmentierung durchzuführen. Dieser Connector steht allen Kunden zur Verfügung, auch von Adobe gehostet.</p>
    <p>Weitere Informationen finden Sie im <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">entsprechenden Handbuch</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop FDA Connector-Verbesserungen</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Der Hadoop FDA Connector wurde verbessert, um sowohl Hadoop 3.0 als auch Cloudera zu unterstützen.</p>
    <p>Weitere Informationen finden Sie im <a href="../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3">entsprechenden Handbuch</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Verbesserte Sicherheit in der Berichtskonfiguration zum Schutz vor dem Clickjacking. Dies gilt für neue Berichte. Für alte Berichte müssen Sie sie erneut veröffentlichen, um Änderungen anzuwenden. (NEO-13282)

* Korrektur eines kleinen Speicherproblems in cryptString. (NEO-20071)

* Verbessertes JSP für Monitore zur Korrektur einer internen IP-Offenlegung. (NEO-16821)

* Es wurde ein Problem behoben, bei dem Stapelablaufdaten Nicht-Admin-Benutzern angezeigt werden konnten. (NEO-12388)

* Die Verwaltung zwischengespeicherter Daten aus vorherigen Sitzungen wurde verbessert. (NEO-17039)

* Es wurde ein Fehler behoben, der verhinderte, dass die Datei &quot;login.log&quot;erfolgreiche Anmeldeversuche über IMS aufzeichnete. (NEO-11004)

**Neuheiten**

* iOS 13 wird jetzt mit dem HTTP2-Connector unterstützt.

* Verbesserte Quarantäne-Verwaltung und Bereinigung der von der Push-Benachrichtigungsfunktion verwendeten Tabellen (nms:address und nms:appSubscriptionRcp). Bei iOS (nur HTTP2-Connector) werden deaktivierte Token jetzt genauso behandelt wie bei Android. Das Deaktivieren-Flag ist jetzt in der Tabelle NmsAppSubscriptionRcp festgelegt. [Mehr dazu](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Im Arbeitsablauf für **JavaScript-Code** - und **erweiterte JavaScript-Code** -Aktivitäten wurde eine neue Option hinzugefügt, um einen Zeitlimitzeitraum zu definieren. Dadurch wird verhindert, dass die Javascript-Ausführungsphase zu lange ausgeführt wird. Wenn der Timeout-Zeitraum abgelaufen ist, wird der Workflow beendet. Der Standardwert für das Zeitlimit ist 1 Stunde. [Mehr dazu](../../workflow/using/sql-code-and-javascript-code.md)

* Die Auslieferungsanalyse wird nun beendet, wenn keine übereinstimmende Affinität auf dem mid-sourcing-Server gefunden wird und die entsprechende Fehlermeldung angezeigt wird.

* Database Failover for Postgres wird jetzt unterstützt: Wenn der Datenbankserver abstürzt und neu startet, stellt Campaign jetzt automatisch eine erneute Verbindung her.

* Die Ansicht &quot; **Start ausstehend** &quot;wurde dem Knoten Administration > Prüfung > Arbeitsablaufstatus hinzugefügt. Dadurch können Sie alle Workflows auf Ihrer Instanz überwachen, die darauf warten, vom **operationMgt** -Prozess gestartet zu werden. Diese Ansicht wird mit dem Marketing-Kampagnenpaket geliefert. [Mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Sonstige Änderungen**

* Unter Linux verwendet der Systemstart des nlserver-Dienstes jetzt eine Systemeinheit anstelle des Skripts /etc/init.d/nlserver6. Die Migration zum neuen Startschema wird automatisch ausgeführt, wenn Sie das 20.1-Paket installieren. Der Befehl /etc/init.d/nlserver6 wird weiterhin bereitgestellt, aber für die Interaktion mit dem nlserver-Dienst (Start, Neustart, Stopp usw.) sollten Sie den Befehl systemCtl direkt verwenden.

* Die am häufigsten verwendeten benutzerdefinierten Tabellen wurden von der **xtkNewId** -Sequenz in dedizierte Sequenzen verschoben. [Mehr dazu](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Verbesserte Abfrageleistung, die durch unnötige Datenbankverbindungen beeinträchtigt werden könnte.

* Die Leistung des Datenbankaktualisierungsassistenten wurde verbessert.

* Das Datenbankdatensatzmanagement wurde verbessert.

* Die Stabilität des Verbindungspools wurde verbessert, was dazu führen kann, dass unerwartete Verbindungsfehler zu oft auftreten.

* Die Validierungsregeln für E-Mail-Adressen, mit denen im Falle eines weichen Fehlers eine Adresse an Quarantäne gesendet werden soll, wurden verbessert. [Mehr dazu](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Für Debian verwendet Campaign jetzt System-PCRE-Bibliotheken, wenn diese verfügbar sind.

* Kampagne ermöglicht nun die Verwendung einer aktuelleren ODBC-Systembibliothek.

* Dem LINE-Servlet wurde beim Öffnen einer Verbindung ein Timeout hinzugefügt, um ein Rich-Bild zu laden. Wenn das Laden des Bildes zu lange dauert, beendet das Servlet die Verbindung, um einen Engpass zu vermeiden.

**Korrekturen**

* Es wurde ein Fehler bei der Verschlüsselung des Kontoschlüssels bei der Verwendung des Hadoop-Connectors behoben.

* Korrektur des Regressionsfehlers aufgrund der Implementierung der SSL-Zertifizierung, der dazu führte, dass die Benutzerverbindung auf dem Windows-Server fehlschlug. (NEO-20629)

* Es wurde ein Problem mit der inkrementellen Abfrageaktivität bei negativen Workflow-IDs behoben. (NEO-19779)

* Es wurde ein Kodierungsfehler behoben, der beim Ausführen von Abfragen über den Netezza FDA-Connector auftrat. (NEO-19594)

* Es wurde ein Fehler behoben, der bei der Verwendung der POST-Methode in der **Web Download** -Workflow-Ereignisaktivität zu einem Fehler führte.

* Es wurde ein Problem bei der Erstellung von Angebotsprogrammen behoben. (NEO-18176)

* Ein Problem mit der Fußzeilenanzeige bei der Verwendung der Akquise-Webformularvorlage wurde behoben.

* Es wurde ein Fehler behoben, der beim Analysieren der URLs im Inhalt von kontinuierlichen Auslieferungen zum Absturz führte. (NEO-16910)

* Es wurde ein Problem behoben, bei dem die Felder **Start** und **Ende** beim Erstellen einer neuen Kampagne nicht berechnet wurden.

* Es wurde ein Problem mit der Aktivität zum **Dateidownload** behoben, das bei Verwendung einer URL auftrat.

* Es wurde ein Problem behoben, das beim Anzeigen einer Vorschau einer importierten Liste in einer Abfrageaktivität eines Berichts auftrat. (NEO-13119)

* Es wurde ein Problem behoben, bei dem ein veraltetes Bild angezeigt wurde, wenn der Personalisierungsblock **Powered by Campaign** im E-Mail-Editor ausgewählt wurde.

* Die Netzwerkkommunikation zwischen Client und Server wurde verbessert.

* Es wurde ein Problem behoben, durch das zu viele Workflows in derselben Kampagne erstellt wurden. Jetzt können Sie nicht mehr als 28 Workflows erstellen. Es wird eine Warnung angezeigt.

* Es wurde ein Problem behoben, das bei der Verwendung der Option **A-Auswahl der Spalten** -Abgleich in einer **Union** -Workflow-Aktivität auftrat.

* Es wurde ein Problem mit einem Absturz der Konsole behoben, das beim Einsatz einer beschädigten Anreicherungsliste in einem Workflow auftreten konnte. (NEO-18096)

* Korrektur verschiedener Probleme mit Konsolenabstürzen, die in Workflows auftraten (NEO-18010, NEO-18032)

* Es wurde ein Fehler behoben, der die Ausführung einer Workflow-Aktivität für **externe Signale** auch dann ermöglichte, wenn sie deaktiviert war. (NEO-17524)

* Es wurde ein Problem beim Erstellen eines neuen Schemas behoben.

* Ein Verfolgungsproblem beim Senden von SMS-Nachrichten wurde behoben. (NEO-19595)

* Es wurde ein Problem behoben, bei dem in den Auslieferungsindikatoren eine falsche Zielgruppenanzahl angezeigt wurde.

* Es wurde ein Problem behoben, bei dem beim Generieren eines beschreibenden Berichts über eine Workflow-Aktivität falsche Prozentwerte angezeigt wurden. (NEO-14314)

* Es wurde ein Fehler behoben, der dazu führte, dass der Bericht zum Bereitstellungsdurchsatz bei Zeitansichtsparametern unterschiedliche Zahlen anzeigte. (NEO-11783)

* Es wurde ein Fehler behoben, der verhinderte, dass die Verfolgungsindikatoren für Transaktionsmeldungen vom Tracking-Workflow aktualisiert wurden. (NEO-17770)

* Es wurde ein Regressionsfehler behoben, der dazu führte, dass der Webprozess abstürzte und neu gestartet wurde, wenn ein Angebot über SOAP angefordert wurde. (NEO-19482)

* Es wurde ein Fehler behoben, der verhinderte, dass Daten in öffentliche Ressourcen hochgeladen werden konnten, wenn der Upload-Ordner ein freigegebener Remote-Speicherort war. (NEO-19361)

* Es wurde ein Fehler behoben, der dazu führte, dass die **Import-Zielgruppen aus dem technischen Arbeitsablauf der Adobe Experience Cloud** ständig fehlschlugen. (NEO-18463)

* Es wurde ein Fehler behoben, der verhinderte, dass Auslieferungen gesendet wurden, wenn Vorlagen aus Experience Manager importiert wurden. (NEO-17540)

* Es wurde ein Problem behoben, das nach der Aktualisierung auf Version 9032 auftrat und verhinderte, dass die Instanz über das SSL-Protokoll eine Verbindung zum FTP-Server herstellen konnte. (NEO-20498)

* Es wurde ein Problem behoben, das beim Löschen, Einfügen oder Aktualisieren einer großen Menge von Daten mit der **Aktualisierungsdatenaktivität** in einem Workflow mit einem FDA-Schema als Targeting-Dimension auftrat. (NEO-13280)

* Es wurde ein Fehler behoben, der verhinderte, dass E-Mails gesendet wurden, wenn die if-Anweisung außerhalb des `body` Tags verwendet wurde.

* Es wurde ein Problem behoben, das beim Versuch auftrat, die Spiegelseite aus den Lieferprotokollen einer gesendeten Nachricht anzuzeigen. (NEO-17976)

* Es wurde ein Fehler behoben, der verhinderte, dass der **Link zum Spiegeln des Seiten** -Personalisierungsblocks auf der Registerkarte **Textinhalt** angezeigt wurde, nachdem in einer Bereitstellung auf HTML **** importieren geklickt wurde. (NEO-17568)

* Die Fehlermeldung, die beim Klicken auf einen Link zu einer abgelaufenen Spiegelseite angezeigt wird, wurde geklärt. (NEO-17340)

* Es wurde ein Fehler behoben, der dazu führte, dass einige Schaltflächen nicht im Erstellungsbildschirm zur **Datenverteilung** verwendet werden konnten.

* Es wurde ein Problem behoben, das beim Planen einer Bereitstellungsaktivität in einer Instanz mit Asien/Kalkutta als Zeitzone auftrat. (NEO-20001)

* Ein Fehler wird nun angezeigt, wenn bei einer Bereitstellung ein Affinitätskonfigurationsproblem auftritt.

* Es wurde ein Problem behoben, bei dem im Menü **Info** eine falsche Version-Tag-Nummer angezeigt wurde.

* Es wurde ein Problem behoben, das beim Versuch auftrat, das Routingkonto von den Eigenschaften einer wiederkehrenden Bereitstellung in einem Workflow zu aktualisieren. (NEO-18684)

* Es wurde ein Problem behoben, das beim Herstellen einer Verbindung mit der Instanz über das Umleitungsmodul auftrat und verhindert hat, dass die Verbindung nach dem Schließen ordnungsgemäß gereinigt wurde.
