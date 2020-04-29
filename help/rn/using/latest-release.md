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
source-git-commit: eab67029d477044bc853f2a5c2de06ace70ebbee

---


# Neueste Version{#latest-release}

[Build-Aktualisierung](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html) | [Control Panel-Versionen](https://docs.adobe.com/content/help/de-DE/control-panel/using/release-notes.html) | [Aktualisierungen der Dokumentation](../../rn/using/documentation-updates.md) | [Frühere Versionshinweise](../../rn/using/release--19-2.md) | [Eingestellte Funktionen](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Allgemeine Verfügbarkeit</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Veröffentlichungskandidat</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Nicht mehr verfügbar</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Veraltet</strong></td> 
  </tr> 
   <tr> 
   <td>Neuester verfügbarer stabiler Build. Build in Produktion validiert.<br> </td>
   <td>Build validiert von Adobe. Produktionstestversand ist ausstehend.<br> </td>
   <td>Neuerer Build mit Fehlerbehebungen verfügbar. Aktualisierung erforderlich.<br> </td>
   <td>Enthält bekannte Regressionen. Aktualisierung ist obligatorisch.<br> </td>
  </tr> 
 </tbody> 
</table>

Der **letzte stabile Build** ist 9032 (3a9dc9c). Click [here](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) Version 20.1.2 – Build 9123 {#release-20-1-2-build-9123}

_13. März 2020_

* Es wurde ein Problem behoben, das die Bereitstellung von Versionen auf Red Hat 7-Servern verhinderte. (NEO-23332)

## ![](assets/do-not-localize/orange_2.png) Version 20.1 – Build 9122 {#release-20-1-build-9122}

_17. Februar 2020_

**Neue Funktionen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake ist ein vollständig verwaltetes Cloud Data Warehouse, das sowohl auf Datenspeicherung- als auch auf Computerebene skaliert werden kann. Mit diesem neuen Connector kann Adobe Campaign jetzt die Leistung von Snowflake nutzen, um eine Big Data-Segmentierung durchzuführen. Dieser Connector steht allen Kunden zur Verfügung, auch von Adobe gehostet.</p>
    <p>For more information, refer to the <a href="../../platform/using/specific-configuration-database.md#configure-access-to-snowflake">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">tutorial video</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop FDA Connector-Erweiterungen</strong><br /> </th> 
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

**Verbesserungen**

* iOS 13 wird jetzt mit dem HTTP2-Connector unterstützt.

* Verbesserte Verwaltung und Bereinigung der Quarantänen, die von der Push-Benachrichtigungsfunktion verwendet werden (nms:address und nms:appSubscriptionRcp). Bei iOS (nur HTTP2-Connector) werden deaktivierte Token jetzt genauso behandelt wie bei Android. Das Deaktivieren-Flag ist jetzt in der Tabelle NmsAppSubscriptionRcp festgelegt. [mehr dazu](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Eine neue Option wurde den Aktivitäten für den **JavaScript-Code** und den **erweiterten JavaScript-Code** -Workflow hinzugefügt, um einen Timeout-Zeitraum zu definieren. Dadurch wird verhindert, dass die Javascript-Ausführungsphase zu lange ausgeführt wird. Wenn der Timeout-Zeitraum abgelaufen ist, wird der Workflow gestoppt. Der Standardwert für das Zeitlimit ist 1 Stunde. [mehr dazu](../../workflow/using/sql-code-and-javascript-code.md)

* Die Analyse des Versands wird jetzt beendet, wenn keine übereinstimmende Affinität auf dem Mid-Sourcing-Server gefunden wird und die entsprechende Fehlermeldung angezeigt wird.

* Database Failover for Postgres wird jetzt unterstützt: Wenn der Datenbankserver abstürzt und neu startet, stellt die Kampagne jetzt automatisch eine erneute Verbindung her.

* Die Ansicht &quot; **Beginn ausstehend** &quot;wurde dem Knoten &quot;Administration&quot;> &quot;Prüfung&quot;> &quot;Workflows&quot;hinzugefügt. Dadurch können Sie alle Workflows auf Ihrer Instanz überwachen, die darauf warten, vom **operationMgt** -Prozess gestartet zu werden. Diese Ansicht ist im Lieferumfang des Marketing-Kampagnen-Pakets enthalten. [mehr dazu](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Sonstige Änderungen**

* Unter Linux verwendet der Systemstart des nlserver-Dienstes jetzt eine Systemeinheit anstelle des Skripts /etc/init.d/nlserver6. Die Migration zum neuen Startschema wird automatisch ausgeführt, wenn Sie das 20.1-Paket installieren. Der Befehl /etc/init.d/nlserver6 wird weiterhin bereitgestellt, aber für die Interaktion mit dem nlserver-Dienst (Beginn, Neustart, Stopp usw.) sollten Sie den Befehl systemCtl direkt verwenden.

* Die am häufigsten verwendeten benutzerdefinierten Tabellen wurden von der **xtkNewId** -Sequenz in dedizierte Sequenzen verschoben. [mehr dazu](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Verbesserte Leistung bei der Abfrage, die durch unnötige Datenbankverbindungen beeinträchtigt werden könnte.

* Die Leistung des Datenbankaktualisierungsassistenten wurde verbessert.

* Das Datenbankdatensatzmanagement wurde verbessert.

* Die Stabilität des Verbindungspools wurde verbessert, was dazu führen kann, dass unerwartete Verbindungsfehler zu oft auftreten.

* Die Validierungsregeln für E-Mail-Adressen, mit denen im Falle eines &quot;soft error&quot;eine Adresse an die Quarantäne gesendet werden soll, wurden verbessert. [mehr dazu](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* Für Debian verwendet Kampagne jetzt System-PCRE-Bibliotheken, wenn sie verfügbar sind.

* Kampagne ermöglicht nun die Verwendung einer aktuelleren ODBC-Systembibliothek.

* Dem LINE-Servlet wurde beim Öffnen einer Verbindung ein Timeout hinzugefügt, um ein Rich-Bild zu laden. Wenn das Laden des Bildes zu lange dauert, stoppt das Servlet die Verbindung, um einen Engpass zu vermeiden.

**Korrekturen**

* Es wurde ein Fehler bei der Verschlüsselung des Kontoschlüssels bei der Verwendung des Hadoop-Connectors behoben.

* Korrektur des Regressionsfehlers aufgrund der Implementierung der SSL-Zertifizierung, der dazu führte, dass die Benutzerverbindung auf dem Windows-Server fehlschlug. (NEO-20629)

* Es wurde ein Problem mit der Aktivität für die inkrementelle Abfrage bei negativen Workflow-IDs behoben. (NEO-19779)

* Es wurde ein Kodierungsproblem behoben, das beim Ausführen von Abfragen über den Netezza FDA Connector auftrat. (NEO-19594)

* Es wurde ein Fehler behoben, der bei der Verwendung der POST-Methode in der Aktivität des **Web Download** -Workflow-Ereignisses zu einem Fehler führte.

* Es wurde ein Problem bei der Generierung von Angebotsvorschlägen behoben. (NEO-18176)

* Ein Problem mit der Fußzeilenanzeige bei der Verwendung der Akquise-Webformularvorlage wurde behoben.

* Es wurde ein Fehler behoben, der beim Analysieren der URLs im Inhalt von kontinuierlichen Versänden zum Absturz führen konnte. (NEO-16910)

* Es wurde ein Problem behoben, bei dem die **Beginn** - und **End** -Felder beim Erstellen einer neuen Kampagne nicht berechnet wurden.

* Es wurde ein Problem mit der Workflow-Aktivität zum **Dateidownload** behoben, das bei Verwendung einer URL auftrat.

* Es wurde ein Problem behoben, das beim Anzeigen einer Vorschau einer importierten Liste in einer Abfrage-Aktivität eines Berichts auftrat. (NEO-13119)

* Es wurde ein Problem behoben, bei dem ein veraltetes Bild angezeigt wurde, wenn der Personalisierungsblock **Powered by Kampagne** im E-Mail-Editor ausgewählt wurde.

* Die Netzwerkkommunikation zwischen Client und Server wurde verbessert.

* Es wurde ein Problem behoben, durch das zu viele Workflows in derselben Kampagne erstellt wurden. Jetzt können Sie nicht mehr als 28 Workflows erstellen. Es wird eine Warnung angezeigt.

* Es wurde ein Fehler behoben, der bei Verwendung der Option **Spaltenabgleich** A in einer Workflow-Aktivität der **Vereinigung** auftrat.

* Es wurde ein Problem mit einem Konsolenabsturz behoben, das auftrat, wenn eine beschädigte Anreicherung-Liste in einem Workflow verwendet wurde. (NEO-18096)

* Es wurden verschiedene Probleme mit einem Konsolenabsturz behoben, die in Workflows auftreten konnten (NEO-18010, NEO-18032)

* Es wurde ein Fehler behoben, der die Ausführung einer Workflow-Aktivität für **externe Signale** auch dann ermöglichte, wenn diese deaktiviert war. (NEO-17524)

* Es wurde ein Problem beim Erstellen eines neuen Schemas behoben.

* Ein Verfolgungsproblem beim Senden von SMS-Nachrichten wurde behoben. (NEO-19595)

* Es wurde ein Problem behoben, durch das in Versand-Indikatoren eine falsche zielgerichtete Audience angezeigt wurde.

* Es wurde ein Problem behoben, bei dem beim Generieren eines beschreibenden Berichts über eine Workflow-Aktivität falsche Prozentwerte angezeigt wurden. (NEO-14314)

* Es wurde ein Fehler behoben, der dazu führte, dass im Bericht zum Durchsatz des Versands beim Ansicht des Zeitparameters unterschiedliche Zahlen angezeigt wurden. (NEO-11783)

* Es wurde ein Fehler behoben, der verhinderte, dass die Verfolgungsindikatoren für Transaktionsnachrichten vom Verfolgungsarbeitsablauf aktualisiert wurden. (NEO-17770)

* Es wurde ein Regressionsfehler behoben, der dazu führte, dass der Webprozess abstürzte und neu gestartet wurde, wenn ein Angebot über SOAP angefordert wurde. (NEO-19482)

* Es wurde ein Fehler behoben, der verhinderte, dass Daten in öffentliche Ressourcen hochgeladen werden konnten, wenn der Upload-Ordner ein freigegebener Remote-Speicherort war. (NEO-19361)

* Es wurde ein Fehler behoben, der dazu führte, dass die **Import-Audiencen aus dem technischen Arbeitsablauf der Adobe Experience Cloud** ständig fehlschlugen. (NEO-18463)

* Es wurde ein Fehler behoben, der verhinderte, dass Versand gesendet wurden, wenn Vorlagen aus Experience Manager importiert wurden. (NEO-17540)

* Es wurde ein Problem behoben, das nach der Aktualisierung auf Version 9032 auftrat und verhinderte, dass die Instanz über das SSL-Protokoll eine Verbindung zum FTP-Server herstellen konnte. (NEO-20498)

* Es wurde ein Problem behoben, das beim Löschen, Einfügen oder Aktualisieren einer großen Datenmenge mit der Aktivität &quot;Daten **** aktualisieren&quot;in einem Workflow auftrat, wobei ein FDA-Schema als Zielgruppendimension verwendet wurde. (NEO-13280)

* Es wurde ein Fehler behoben, der verhinderte, dass E-Mails gesendet wurden, wenn die if-Anweisung außerhalb des `body` Tags verwendet wurde.

* Es wurde ein Problem behoben, das beim Versuch auftrat, die Mirrorseite aus den Versandlogs einer gesendeten Nachricht anzuzeigen. (NEO-17976)

* Es wurde ein Problem behoben, bei dem der Personalisierungsblock **Link zur Mirrorseite** nicht auf der Registerkarte **Textinhalt** angezeigt wurde, nachdem in einem Versand auf HTML **** importieren geklickt wurde. (NEO-17568)

* Die Fehlermeldung, die beim Klicken auf einen Link zu einer abgelaufenen Mirrorseite angezeigt wird, wurde geklärt. (NEO-17340)

* Es wurde ein Fehler behoben, der dazu führte, dass einige Schaltflächen nicht im Erstellungsbildschirm für die **Datenverteilung** verwendet werden konnten.

* Es wurde ein Problem behoben, das beim Planen einer Versand-Aktivität in einer Instanz mit Asien/Kalkutta als Zeitzone auftrat. (NEO-20001)

* Es wird nun ein Fehler angezeigt, wenn ein Versand ein Problem mit der Affinität-Konfiguration hat.

* Es wurde ein Problem behoben, bei dem im Menü **Info** eine falsche Version-Tag-Nummer angezeigt wurde.

* Es wurde ein Problem behoben, das beim Versuch auftrat, das Routing-Konto von den Eigenschaften eines wiederkehrenden Versands in einem Workflow zu aktualisieren. (NEO-18684)

* Es wurde ein Problem behoben, das beim Herstellen einer Verbindung mit der Instanz über das Umleitungsmodul auftrat und verhindert hat, dass die Verbindung nach dem Schließen ordnungsgemäß gereinigt wurde.
