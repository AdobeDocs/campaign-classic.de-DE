---
product: campaign
title: Überwachungsverfahren
description: Erfahren Sie, wie Sie Campaign-Prozesse überwachen.
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '3779'
ht-degree: 2%

---

# Überwachungsverfahren{#monitoring-processes}

![](../../assets/v7-only.svg)

Der Anwendungsserver und der Weiterleitungsserver (**tracking**) manuell oder automatisch überwacht werden.

## Manuelle Überwachung {#manual-monitoring}

Navigieren Sie zu **[!UICONTROL Überwachung]** und klicken Sie auf **[!UICONTROL Übersicht]** -Link, um die Adobe Campaign-Prozessüberwachungsseite anzuzeigen.

![](assets/d_ncs_monitoring.png)

Auf der angezeigten Seite können Sie den Status der verbundenen Instanz anzeigen, d. h.:

* Informationen zur Instanz: Version, Name, Datenbank-Engine, installierte Pakete, Server-Systemindikatoren,
* die Liste der fehlenden Prozesse und Ausführungsinformationen (Startdatum, PID usw.),
* Übersicht über Workflows und Sendungen.

Weitere Möglichkeiten zur Überwachung der verschiedenen Campaign-Prozesse werden auf [dieser Seite](../../production/using/monitoring-guidelines.md) vorgestellt.

### Protokoll-Protokoll {#log-journal}

Es ist möglich, das Protokollprotokoll anzuzeigen, das sich auf einen Prozess bezieht. Klicken Sie dazu auf den Prozess, **mta** Klicken Sie beispielsweise auf **[!UICONTROL Protokoll-Protokoll öffnen]** .

![](assets/d_ncs_monitoring2.png)

### Systemindikator {#system-indicators}

Die Liste der Systemindikatoren ermöglicht die Anzeige von Informationen über den Computer, wie z. B. physischer und virtueller Speicher, aktive Prozesse und verfügbarer Speicherplatz. Die Indikatoren unterscheiden sich bei Linux- und Windows-Betriebssystemen. Navigieren Sie zu **[!UICONTROL Instanzüberwachung]** und klicken Sie auf **[!UICONTROL Anzeige]** Link, um die Liste der Indikatoren zu öffnen

#### Windows {#in-windows}

* **[!UICONTROL Ausstehende Ereignisse in der Warteschlange]** : Indikator, der spezifisch für **Message Center**. Weitere Informationen finden Sie in [diesem Abschnitt](../../message-center/using/additional-configurations.md#monitoring-thresholds).

* **[!UICONTROL Speicher]** : Informationen zum physischen Speicher (RAM).

   **[!UICONTROL Aktueller Wert]** : tatsächlicher Speicherverbrauch.

   **[!UICONTROL Max. Wert]** : Gesamtanzahl der installierten Arbeitsspeicher.

   **[!UICONTROL Verfügbar]** : Menge an verfügbarem Speicher.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 80 % des Gesamtvolumens erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 90 % des Gesamtvolumens erreicht.

   Wenn die **[!UICONTROL Warnung]** und **[!UICONTROL Warnhinweis]** angezeigt werden, können Sie das Problem lösen, indem Sie dem Computer, auf dem der Adobe Campaign-Server installiert ist, RAM hinzufügen. Sie können sich auch dafür entscheiden, den Adobe Campaign-Server auf einem dedizierten Computer zu installieren.

* **[!UICONTROL Speicher tauschen]** : Informationen zum virtuellen Speicher, der mit einer Paging-Datei übereinstimmt: Ein Bereich auf der Festplatte, der von Windows als RAM verwendet wird.

   **[!UICONTROL Aktueller Wert]** : tatsächlicher Speicherverbrauch.

   **[!UICONTROL Max. Wert]** : Gesamtspeichermenge.

   **[!UICONTROL Verfügbar]** : Menge an verfügbarem Speicher.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 80 % des Gesamtvolumens erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 90 % des Gesamtvolumens erreicht.

   Wenn die **[!UICONTROL Warnung]** und **[!UICONTROL Warnhinweis]** angezeigt werden, können Sie das Problem lösen, indem Sie die Größe der Exchange-Datei in den erweiterten Windows-Einstellungen erhöhen.

* **[!UICONTROL Datenträger XXX]** : Informationen über Maschinenleser.

   **[!UICONTROL Aktueller Wert]** : tatsächlich verwendeter Speicherplatz.

   **[!UICONTROL Max. Wert]** : Gesamtkapazität der Festplatte.

   **[!UICONTROL Verfügbar]** : verfügbarer Speicherplatz

   **[!UICONTROL Verwendet]** : Prozentsatz der verwendeten Festplatte.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn der verfügbare Speicherplatz 80 % der Gesamtkapazität erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn der verfügbare Speicherplatz 90 % der Gesamtkapazität erreicht.

* **[!UICONTROL Anzahl der Prozesse zu alt]** : Informationen zu Adobe Campaign-Prozessen, die seit mehr als einem Tag aktiv sind.

   **[!UICONTROL Aktueller Wert]** : Anzahl der derzeit aktiven Prozesse.

   **[!UICONTROL Max. Wert]** : Höchstzahl zulässiger Prozesse (1).

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn die Anzahl der Prozesse gleich 1 ist.

   Wenn die **[!UICONTROL Warnhinweis]** angezeigt wird, kann es sein, dass der betreffende Prozess durch die SQL-Datenbank-Engine gesperrt oder in einer Endlosschleife feststeckt. Die **watchdog** Der von Adobe Campaign bereitgestellte Prozess startet automatisch alle Prozesse jeden Tag neu und ermöglicht es Ihnen, dieses Problem zu lösen. Sie können den entsprechenden Prozess jedoch auch selbst stoppen, um einen Neustart zu erzwingen.

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Ausstehende Ereignisse in der Warteschlange]** : Indikator, der spezifisch für **Message Center**. Weitere Informationen finden Sie in [diesem Abschnitt](../../message-center/using/additional-configurations.md#monitoring-thresholds).

* **[!UICONTROL Lastdurchschnitt (1/5/15 Minuten)]** : Informationen über die Last, d. h. die Nutzrate des Prozessors durch die Prozesse, die in letzter Minute, fünf Minuten oder fünfzehn Minuten auf dem Gerät ausgeführt werden.

   **[!UICONTROL Aktueller Wert]** : tatsächliche Belastung der Maschine.

   **[!UICONTROL Max. Wert]** : maximale Nutzlast der Prozesse auf dem Computer

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn die Last 80 % des maximal zulässigen Wertes in der letzten Minute, fünf Minuten oder fünfzehn Minuten erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn die Last 90 % des maximal zulässigen Wertes der letzten Minute, fünf Minuten oder fünfzehn Minuten erreicht.

* **[!UICONTROL Speicher]** : Informationen zum physischen Speicher (RAM).

   **[!UICONTROL Aktueller Wert]** : tatsächlicher Speicherverbrauch.

   **[!UICONTROL Max. Wert]** : Gesamtanzahl der installierten Arbeitsspeicher.

   **[!UICONTROL Verfügbar]** : Menge an verfügbarem Speicher.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 80 % des Gesamtvolumens erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 90 % des Gesamtvolumens erreicht.

   Wenn die **[!UICONTROL Warnung]** und **[!UICONTROL Warnhinweis]** angezeigt werden, können Sie das Problem lösen, indem Sie dem Computer, auf dem der Adobe Campaign-Server installiert ist, RAM hinzufügen. Sie können sich auch dafür entscheiden, den Adobe Campaign-Server auf einem dedizierten Computer zu installieren.

* **[!UICONTROL Speicher tauschen]** : Informationen zum virtuellen Speicher, der mit einer Paging-Datei übereinstimmt: Ein Bereich auf der Festplatte, der von Windows als RAM verwendet wird.

   **[!UICONTROL Aktueller Wert]** : tatsächlicher Speicherverbrauch.

   **[!UICONTROL Max. Wert]** : Gesamtspeichermenge.

   **[!UICONTROL Verfügbar]** : Menge an verfügbarem Speicher.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 80 % des Gesamtvolumens erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn der Speicherverbrauch 90 % des Gesamtvolumens erreicht.

   Wenn die **[!UICONTROL Warnung]** und **[!UICONTROL Warnhinweis]** angezeigt werden, können Sie das Problem lösen, indem Sie die Größe der Exchange-Datei erhöhen.

* **[!UICONTROL Kerndateien]** : Informationen zu den Dateien, die nach dem Absturz eines Adobe Campaign-Prozesses generiert wurden. Mit diesen Dateien können Sie die Ursachen des Absturzes diagnostizieren.

   **[!UICONTROL Aktueller Wert]** : Anzahl der vorhandenen Dateien.

   **[!UICONTROL Max. Wert]** : maximale Anzahl zulässiger Dateien (1).

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn sich die Anzahl der Dateien in der Nähe von 1 befindet.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn die Anzahl der Dateien gleich 1 ist.

   Wenn ein Prozess aufgrund eines Absturzes fehlt, wird er in der Prozessliste rot angezeigt und automatisch von der **watchdog** -Prozess, der von Adobe Campaign bereitgestellt wird.

* **[!UICONTROL Anzahl der gemeinsamen Speichersegmente]** : Informationen zu den Speichersegmenten, die von allen Adobe Campaign-Prozessen gemeinsam genutzt werden.

   **[!UICONTROL Aktueller Wert]** : Anzahl der derzeit verwendeten Speichersegmente.

   **[!UICONTROL Max. Wert]** : Maximale Anzahl zulässiger Speichersegmente (2).

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn die Anzahl der Speichersegmente 1 erreicht.

   **[!UICONTROL Warnhinweis]** : Diese Anzeige wird angezeigt, wenn die Anzahl der Speichersegmente 2 erreicht.

* **[!UICONTROL Anzahl der Prozesse zu alt]** : Informationen zu Prozessen, die seit mehr als einem Tag aktiv sind.

   **[!UICONTROL Aktueller Wert]** : Anzahl der derzeit aktiven Prozesse.

   **[!UICONTROL Max. Wert]** : maximale Anzahl zulässiger Prozesse.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn die Anzahl der Prozesse 80 % der zulässigen Schwelle erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn die Anzahl der Prozesse 90 % der zulässigen Schwelle erreicht.

* **[!UICONTROL Datei-Handles]** : Informationen über die Dateideskriptoren, d. h. die Anzahl der pro Prozess geöffneten Dateien.

   **[!UICONTROL Aktueller Wert]** : aktuelle Anzahl von Dateideskriptoren.

   **[!UICONTROL Max. Wert]** : maximale Anzahl von Dateideskriptoren, die vom Betriebssystem genehmigt wurden.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn die Anzahl der zugelassenen Dateideskriptoren den Schwellenwert von 80 % erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn die Anzahl der zugelassenen Dateideskriptoren den Schwellenwert von 90 % erreicht.

* **[!UICONTROL Prozesse]** : Informationen über die Maschinenprozesse.

   **[!UICONTROL Aktueller Wert]** : Anzahl der derzeit aktiven Prozesse.

   **[!UICONTROL Max. Wert]** : maximale Anzahl zulässiger Prozesse.

   **[!UICONTROL Aktive Prozesse]** : Anzahl der aktiven Prozesse.

   **[!UICONTROL Inaktive Prozesse]** : Anzahl der inaktiven Prozesse.

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn die Anzahl genehmigter Prozesse den Schwellenwert von 80 % erreicht.

   **[!UICONTROL Warnhinweis]** : Dieser Indikator wird angezeigt, wenn die Anzahl der zugelassenen Prozesse den Schwellenwert von 90 % erreicht.

* **[!UICONTROL Zombie-Prozesse]** : Informationen zu den Prozessen, die angehalten wurden, aber noch eine Prozess-ID (PID) aufweisen und in der Prozesstabelle sichtbar bleiben.

   **[!UICONTROL Aktueller Wert]** : Anzahl der derzeit aktiven Zombie-Prozesse.

   **[!UICONTROL Max. Wert]** : maximale Anzahl der autorisierten Zombie-Prozesse (2).

   **[!UICONTROL Warnung]** : Dieser Indikator wird angezeigt, wenn die Anzahl der Zombie-Prozesse nahe 2 liegt.

   **[!UICONTROL Warnhinweis]** Dieser Indikator wird angezeigt, wenn die Anzahl der Zombie-Prozesse 2 erreicht.

#### Benutzerdefinierte Indikatoren {#customized-indicators}

Adobe Campaign ermöglicht die Anpassung von Indikatoren. Gehen Sie dazu wie folgt vor:

1. Erstellen Sie eine **.sh** Datei und Namen **[!UICONTROL cust_indicators.sh]** .
1. Fügen Sie Ihre benutzerdefinierten Indikatoren dieser Datei hinzu. Beispiel:

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   oder

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. Fügen Sie die Datei in die **[!UICONTROL usr/local/neolane/nl6]** Ordner.

Diese Datei wird von Adobe Campaign aufgerufen.

## SMTP-Berichte {#smtp-reports}

SMTP-Versandüberwachungsberichte sind in die Adobe Campaign-Plattform integriert. Der Zugriff erfolgt über die Konsole oder über den Webzugriff.

Diese Berichte zeigen die SMTP-Versandstatistiken und SMTP-Fehler nach Domain an.

Um darauf zugreifen zu können, muss der Benutzer über Administratorrechte verfügen.

Sie sind unter **Überwachung** > &quot;SMTP Monitoring&quot;.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* Informationen zur SMTP-Überwachung sind nur verfügbar, wenn der E-Mail-Kanal aktiviert wurde.
>* Die **[!UICONTROL SMTP-Sendestatistiken]** werden nur angeboten, wenn der Statistikserver auf der Instanz gestartet wird.

>


### SMTP-Versandstatistiken {#smtp-sending-statistics}

Die **[!UICONTROL SMTP-Sendestatistiken]** können Sie die Serveraktivität steuern. Es zeigt eine Synthese der einzelnen MTA-Kindprozesse an.

![](assets/smtp_stats_report.png)

Die Liste der Indikatoren für diesen Bericht ist unten in der Grafik dargestellt.

1. Anzahl gesendeter Nachrichten insgesamt
1. 
   * Blaue Linie: Versandbereite Nachrichten, die in den Shaper gelangt sind, d. h. die letzte Phase vor dem Senden von SMTP (entspricht den eingehenden Daten).

   * Grüne Zeile: erfolgreich gesendete Nachrichten (entspricht den ausgehenden Daten).

   * Rote Linie: Nachrichten, die vom Shaper abgebrochen und an die **mta** (entspricht den Daten, die bei dieser Wiederherstellung zurückgewiesen wurden).

   Diese Werte werden in Anzahl an Nachrichten pro Stunde ausgedrückt.

1. Stellt zwei Warteschlangen des Shapers dar:

   * Blaue Kurve: Warteschlange aktiver Nachrichten. Diese Nachrichten werden so bald wie möglich gesendet.

   * Kaki-Kurve: die Warteschlange &quot;verzögert&quot;. Diese Nachrichten können im Moment nicht zurückgegeben werden, weil sie gedrosselt wurden oder keine Verbindung zum Ziel verfügbar ist. Alle 5, 10, 20, 40, 2 Min. usw. werden wiederholt. für die definierte **MaxAgeSec** Zeit, bevor sie verlassen werden.

1. In diesen Diagrammen wird eine Detailansicht der abgebrochenen Nachrichten angezeigt (rote Kurve auf der zweiten Grafik): Er zeigt den Anteil an Nachrichten, die ohne weitere Zustellversuche abgebrochen wurden (manuell), in Bezug auf Nachrichten, deren Versand fehlgeschlagen ist (rot). Auf diese Weise können Sie den Anteil der Nachrichten anzeigen, die innerhalb des festgelegten Zeitraums aufgrund von Einschränkungen durch den Statistikserver (Einschränken) oder aufgrund der Nichtverfügbarkeit des Remote-Servers nicht verarbeitet wurden.
1. SMTP-Verbindungen, die offen sind oder geöffnet werden
1. Schätzung der Anzahl **mtachild**.

>[!NOTE]
>
>Dieser Bericht bezieht sich auf den Status der Komponente &quot;Email Traffic Shaper&quot;.

### SMTP-Fehler nach Domain {#smtp-errors-per-domain}

Dieser Bericht zeigt die Versandfehler in einem bestimmten Zeitraum nach Domain aufgeschlüsselt an.

>[!NOTE]
>
>Die **minConnectionsToLog**, **minErrorsToLog** und **minMessagesToLog** Optionen der **serverConf.xml** -Datei definieren die Schwellenwerte, ab denen Verbindungsstatistiken berücksichtigt werden.

![](assets/smtp_error_report.png)

Die Liste der Indikatoren für diesen Bericht ist der Tabelle zu entnehmen.

* Die **Domäne** -Spalte enthält den Namen der Domäne, an die die Nachrichten gesendet werden (oder den tatsächlichen Domänennamen, z. B. yahoo.com für yahoo.fr),
* Die **CNX** -Spalte zeigt die Anzahl der für diese Domäne geöffneten SMTP-Verbindungen an,
* Die **Gesendet** Spalte entspricht der Anzahl an Nachrichten, die an diese Domain gesendet werden,
* Die **Lautstärke** zeigt die Anzahl an Nachrichten an, die an diese Domain gesendet werden sollen (ungefährer Wert);
* Die **Fehler** -Spalte zeigt einen Volumenindikator für Fehler in dieser Domain über den Zeitraum an,
* Die **Letzte Antwort** -Spalte zeigt die letzte SMTP-Antwortnachricht an, die für diese Domain empfangen wurde,
* Die **Datum** zeigt das Datum der letzten SMTP-Antwort an, die für diese Domäne empfangen wurde.

>[!NOTE]
>
>Die in der Variablen **CNX**, **Gesendet** und **Lautstärke** die Spalten werden in Bezug auf den in der Variablen **[!UICONTROL Zeitraum]** -Feld.

Klicken Sie auf einen Domänennamen, um dessen Fehler anzuzeigen.

Sie werden nach PublicId kategorisiert: Diese Kennung entspricht einer IP-Adresse, die von mehreren Adobe Campaign-MTAs hinter einem Router gemeinsam genutzt wird. Der Statistikserver verwendet diese Kennung, um die Verbindungs- und Versandstatistiken zwischen diesem Startpunkt und dem Zielserver zu speichern.

![](assets/smtp_error_report_details.png)

Die **[!UICONTROL Inhaber der Domäne]** -Feld können Sie verschiedene Domänennamen unter derselben Bezeichnung gruppieren. In der ersten Berichtsansicht werden alle MX-Domänennamen diesem Eigentümer zugeordnet.

Klicken Sie auf eine PublicId-Kennung, um weitere Details anzuzeigen.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>Der Fehlerprozentsatz wird in zwei Diagrammen dargestellt. Das erste ist ein horizontaler Fortschrittsbalken auf einem schwarzen Hintergrund. Die zweite Grafik ist chronologisch. Der ausgewählte Zeitraum wird in zwölf Zeitintervalle unterteilt, die jeweils durch einen vertikalen Fortschrittsbalken dargestellt werden. Wenn in beiden Darstellungen kein Fehler erkannt wurde, ist der Balken schwarz. Die Farbe des Balkens hängt vom Prozentsatz der aufgetretenen Fehler ab (gelb, dann orange und schließlich rot). Die Farbgrau bedeutet, dass kein signifikantes Datenvolumen gefunden wurde. Es ist möglich, den genauen Fehlerprozentsatz anzuzeigen, indem Sie den Cursor auf das Diagramm setzen.

>[!NOTE]
>
>Weitere Informationen zu SMTP-Fehlern und deren Verwaltung in Adobe Campaign finden Sie unter [diesem Abschnitt](../../installation/using/email-deliverability.md).

## Rechnungsstellungsbericht {#billing-report}

Die **[!UICONTROL Rechnungsstellung]** technischer Workflow sendet den Aktivitätsbericht des Systems per E-Mail an den fakturierungsverantwortlichen Benutzer (&#39;billing&#39;). Er wird standardmäßig am 25. jedes Monats in der Marketing-Instanz ausgelöst.

Der technische Workflow befindet sich in einem Unterordner des folgenden Knotens: **Administration** > **Produktion** > **Technische Workflows**.

![](assets/billing.png)

Sobald der Workflow alle 25 Monate gestartet wird, erhält Ihr Abrechnungs-Benutzer den folgenden Bericht in seinem Posteingang.

![](assets/billing_2.png)

Folgende Metriken stehen zur Verfolgung Ihrer Sendungen zur Verfügung:

* **[!UICONTROL Startdatum]** : Startdatum des Versands. Beachten Sie, dass der Bericht früher als das Datum &quot;Von&quot;des Berichts sein kann.
* **[!UICONTROL Titel]** : Titel des Versands Sendungen mit weniger als 100 zu sendenden Nachrichten werden als zu klein angesehen und somit nach dem Startdatum aggregiert. In diesem Fall zeigt der Titel die Anzahl der Aggregate an, z. B. [Aggregation von 3 kleinen Sendungen].
* **[!UICONTROL Gesamtvolumen]** : Gesamtvolumen der für die Bereitstellung übertragenen Bytes.
* **[!UICONTROL Durchschnittliches Volumen]** : Durchschnittliche Menge der übertragenen Bytes. Dies ist das Ergebnis der folgenden Formel **(Gesamtvolumen/Nachrichten)**, die die Berechnungsgrundlage der **[!UICONTROL Multiplikator]** Metrik.
* **[!UICONTROL Nachrichten]** : Anzahl gesendeter Nachrichten. Dazu gehören sowohl erfolgreich gesendete Nachrichten als auch erneute Zustellversuche (nach Erhalt einer Bounce Message vom kontaktierten Server).
* **[!UICONTROL Multiplikator (x)]** : Der Wert des Multiplikators wird vom durchschnittlichen Volumen der Nachrichten abgezogen.
* **[!UICONTROL Count]** : Ergebnis der Multiplikation der Nachrichten und des Multiplikators.

## Automatische Überwachung {#automatic-monitoring}

Adobe Campaign bietet mehrere automatische Überwachungsmethoden, die nachfolgend beschrieben werden.

### Befehlszeile {#command-line}

Befehl

**nlserver-Monitor**

Ermöglicht die Auflistung einer Reihe von Indikatoren in den Adobe Campaign-Modulen und im System.

Es erzeugt die Ausgabe in einem einfach verarbeiteten XML-Format.

Dieser Befehl kann auch mit der **-missing** -Parameter, der die in dieser Instanz fehlenden Prozesse auflistet, wenn die Konfigurationsdateien sagen, dass sie ausgeführt werden sollen.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### Vom Server veröffentlichte Informationen {#information-published-by-the-server}

#### /r/test {#r-test}

Die **http(s)://`<application>`/r/test** -Seite wird zum Testen des Weiterleitungsservers verwendet. Es wird empfohlen, dieselbe Methode zum Testen der für das Tracking verwendeten Frontserver zu verwenden. Diese Seite kann auch zum Testen eines Load Dispatchers verwendet werden.

Es wird eine Zeile wie die folgende im XML-Format angezeigt:

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**Häufigkeit**: dieser Test nutzt keine Last und kann daher sehr oft ausgeführt werden (z. B. einmal pro Sekunde).

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

Diese **http(s)://`<Application server url>`/nl/jsp/ping.jsp**  -Seite funktioniert auf dieselbe Weise wie das zugehörige Netzwerk-Gegenstück: Es testet eine vollständige Abfrage, die durch Apache/Tomcat/Webmodul/Datenbank läuft und auf den Client hochgeladen wird. Wenn alles ordnungsgemäß funktioniert, wird &quot;OK&quot;zurückgegeben. Es wird empfohlen, diesen Test auf Computern auszuführen, die Zugriff auf die Datenbanken haben (z. B. MTA und Umfragen).

**Nutzung**: Ein Sitzungstoken, das mit einer Benutzeranmeldung verknüpft ist, muss als Argument übergeben werden, um sich remote anmelden zu können (siehe Tipp in [Automatische Überwachung über Adobe Campaign-Skripte](#automatic-monitoring-via-adobe-campaign-scripts)).

Beispiel:

![](assets/ncs_monitoring_ping.png)

Der Benutzername und die Anmeldung des Benutzers müssen zuvor in der Adobe Campaign-Clientkonsole mit Datenbankrechten konfiguriert werden.

![](assets/ncs_operators_rights_01.png)

**Häufigkeit**: Dies ist ein Test, der sehr wenig Bandbreite verwendet. Es kann also ziemlich oft, aber nicht mehr als einmal pro Minute ausgeführt werden.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

Dies ist ein Test, um zu überprüfen, ob ein Benutzer über eine Webseite auf den Adobe Campaign-Server zugreifen kann. die Webseite, auf die über die Menüs der Clientkonsole zugegriffen wird. Sie können diese Seite über Ihre Überwachungstools (Tivoli, Nagios usw.) aufrufen.

![](assets/ncs_monitoring_web.png)

**Nutzung**: Ein Sitzungstoken, das mit einer Operatoranmeldung verknüpft ist, mit der Sie eine Verbindung zur Instanz herstellen können, muss als Argument verwendet werden (siehe Tipp in [Automatische Überwachung über Adobe Campaign-Skripte](#automatic-monitoring-via-adobe-campaign-scripts)).

Der Benutzer und seine Anmeldung müssen zuvor in der Adobe Campaign-Clientkonsole mit den entsprechenden Datenbankrechten und -beschränkungen konfiguriert werden.

**Häufigkeit**: Dies ist ein vollständiger Server-Test und muss nicht oft ausgeführt werden (er kann beispielsweise alle zehn Minuten ausgeführt werden).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

Diese **jsp** stellt den Einstiegspunkt der Adobe Campaign-Anwendungs-APIs dar. Sie kann daher eine detaillierte Überwachung des Antrags vornehmen. Sie kann auch zur Überwachung von Adobe Campaign-Webdiensten verwendet werden. Sie wird in unseren Überwachungsskripts verwendet, aber beachten Sie, dass sie nur für Power-User bestimmt ist.

### Überwachung anhand von Bereitstellungstypen {#monitoring-based-on-deployment-types}

Adobe Campaign ermöglicht verschiedene Bereitstellungskonfigurationen (weitere Informationen hierzu finden Sie unter [diesem Abschnitt](../../installation/using/hosting-models.md)). In diesem Abschnitt werden die verschiedenen automatischen Überwachungsverfahren beschrieben, die je nach Installationstyp anzuwenden sind.

<table> 
 <thead> 
  <tr> 
   <th> Bereitstellungstyp </th> 
   <th> Monitoring      </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Eigenständig </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> und <span class="uicontrol">/nl/jsp/monitor.jsp</span> auf dem Adobe Campaign-Server</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Standard </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> und <span class="uicontrol">/nl/jsp/ping.jsp</span> auf den Frontservern</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> auf dem Anwendungsserver</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Unternehmen </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> und <span class="uicontrol">/nl/jsp/ping.jsp</span> auf den Frontservern</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> und <span class="uicontrol">/nl/jsp/monitor.jsp</span> auf dem Anwendungsserver</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Mid-Sourcing </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> auf dem Anwendungsserver</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Automatische Überwachung über Adobe Campaign-Skripte {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign kann ein Tool zur Instanzüberwachung (netreport) bereitstellen, mit dem Sie einen Bericht über die erkannten Anomalien per E-Mail versenden können.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>Dieses Tool kann zur Überwachung Ihrer Instanzen verwendet werden, wird jedoch nicht von Adobe Campaign unterstützt. Weitere Informationen erhalten Sie von Ihrem Campaign-Administrator.

### Erforderliche Elemente {#required-elements}

Für die automatische Überwachung sind folgende Vorsichtsmaßnahmen vor der Installation erforderlich:

* Sie müssen über die **netreport.tgz** (Linux-Installation) oder **netreport.zip** (Windows-Installation) Dateien,
* Wir empfehlen Ihnen dringend, keine Überwachung auf dem zu überwachenden Computer zu installieren.
* sie muss auf einem Computer mit JRE oder JDK installiert sein,
* in Linux muss der zu überwachende Computer über die **bc** Paket. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages).

### Installationsverfahren {#installation-procedure}

Die Installation erfolgt wie folgt:

1. Erstellen Sie in der Konsole bei Bedarf einen neuen Benutzer (der Benutzer &quot;Monitoring&quot;ist bereits vorhanden), weisen Sie jedoch keine Rechte zu.
1. Archivextraktion ausführen.
1. Lesen Sie die **Readme** -Datei.
1. Aktualisieren Sie die **netconf.xml** Konfigurationsdatei.
1. Aktualisieren Sie die **netreport.bat** (Windows) oder **netreport.sh** (Linux).

### Konfigurieren der Datei &quot;netconf.xml&quot; {#configuring-the-netconf-xml-file}

Die XML-Konfigurationsdatei enthält die folgenden Elemente:

* [Element &quot;Eigenschaften&quot;](#properties--element)
* [&#39;Instance&#39;-Element](#instance--element)
* [Element &quot;Host&quot;](#host--element)
* [Unterelemente](#sub-elements)

Im Folgenden finden Sie ein Konfigurationsbeispiel:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>Sie können verschiedene Konfigurationen angeben, indem Sie dem **netconf.xml** -Datei, z. B. **netconf-dev.xml**, **netconf-prod.xml**, usw. Geben Sie dann die Konfiguration für die Ausführung des Netzwerkberichts im **netreport.bat** oder **netreport.sh** Dateien durch Hinzufügen von **$JAVA_HOME/bin/java netreport dev** oder **@%JAVA_HOME%binjava netreport prod** zum Beispiel.

>[!IMPORTANT]
>
>Für **Monitoring** -Operator verwenden, muss sich die Maschine, auf der der Netzwerkbericht ausgeführt wird, in einer Sicherheitszone befinden, die sich in **sessionTokenOnly** -Modus. Wenn für diesen Operator keine vertrauenswürdige IP-Maske angegeben wurde, muss auch die Sicherheitszone in **allowEmptyPassword** und **allowUserPassword** -Modus.

#### Element &quot;Eigenschaften&quot; {#properties--element}

Dieses Element wird verwendet, um die Konfiguration von E-Mails, d. h.

* **mailServer**: SMTP-Server, der zum Senden von E-Mails verwendet wird (z. B.: smtp.domain.net).
* **mailFrom**: E-Mail-Adresse des Berichtabsenders (z. B.: monitoring@domain.net).
* **recipientList**: die Liste der E-Mail-Adressen der Empfänger, die die Überwachung durchführen. Die Adressen müssen durch Kommas (ohne Leerzeichen) getrennt werden.
* &#39;**Nacht** Der optionale Modus verhindert den Versand von E-Mails zwischen dem angegebenen Zeitraum. Stattdessen werden die Daten konsolidiert und nach der Endzeit (standardmäßig 7:00 Uhr) wird eine E-Mail zur Aktivität der Nacht gesendet.
* Die **buildRange** -Unterelement (optional) ermöglicht die Angabe einer Mindest- und einer Höchstzahl an Builds. Es wird ein Fehler für alle Computer erzeugt, deren Build-Nummer nicht in diesen Bereich fällt

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* Sie können eine **`<sla>`** (optional) Unterelement im **properties** -Element. Jedes Mal, wenn der netreport ausgeführt wird, wird eine Protokolldatei erzeugt. Der Dateiname enthält den Konfigurationsnamen sowie Datum und Uhrzeit, z. B. **dev_06_12_13_16_47_05.tmp**. Die Datei enthält die folgenden Informationen: Instanzname, Maschinenname, Schweregrad, (0 bis 3, vom geringsten bis zum kritischsten), Datum (Zeitstempelformat), Zeit (in Millisekunden) zwischen der Abfrage und der Antwort, verwendeter Dienst (http, ncs, ncsex, redir). Diese Informationen werden am Ende jedes Dienstes durch Tabulationszeichen und Zeilenumbrüche getrennt.

>[!NOTE]
>
>Die **persistHtmlFile** -Attribut mit dem Wert &quot;true&quot;auf der **`<property>`** -Element zum Aufzeichnen des neuesten Überwachungsstatus in der Datei verwendet wird **netreport.md**. Diese Datei wird im Installationsverzeichnis gespeichert.

#### &#39;Instance&#39;-Element {#instance--element}

Mit diesem Element können Sie mehrere Rechner (Hosts) in derselben Instanz gruppieren. Die Instanznamen werden im ersten Teil der Monitoring-E-Mail angezeigt. Sie können auf den Namen einer Instanz klicken, um auf Details zu den einzelnen Computern zuzugreifen.

```
instance name="instanceName" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**: Instanzname, der im ersten Teil der E-Mail angezeigt wird.
* **recipientList** (optional): ermöglicht den Versand eines Überwachungsberichts über eine bestimmte Instanz per E-Mail.

#### Element &quot;Host&quot; {#host--element}

Dieses Element konfiguriert die Überwachung eines bestimmten Servers auf dem Host, d. h.

* **name**: Name des zu überwachenden Geräts.
* **alias** (optional): Name des überwachten Computers, wie er im Bericht angezeigt wird.
* **sessionToken**: bietet Anmeldeauthentifizierung über ein autorisiertes Sitzungstoken.

   Um das Sitzungstoken zu konfigurieren, wählen Sie die **Monitoring** in der Adobe Campaign-Konsole. Im **Zugriffsberechtigungen** Geben Sie die IP-Adressen der Computer an, die zur Überwachung dieser Instanz berechtigt sind. Anschließend können Sie über die **Monitoring** und ohne ein Kennwort angeben zu müssen.

   ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** (optional): ermöglicht die Sortierung von Fehlern nach Schweregrad. Mögliche Werte sind &quot;0&quot;(alle angezeigten Ebenen), &quot;1&quot;(nur hochgradige und kritische Fehler) und &quot;2&quot;(nur kritische Fehler werden angezeigt). Wenn dieses Attribut nicht angegeben wird, werden alle Fehlerstufen angezeigt.
* **filter** (optional): ermöglicht den Ausschluss bestimmter Workflow-Fehler, beispielsweise **filter=&quot;wkf;wkf1&quot;**. Workflow-Beschriftungen müssen durch Semikolons getrennt werden.

#### Unterelemente {#sub-elements}

* **tcp**: überprüft, ob der Server ausgefallen ist oder nicht. Sie müssen eine Portnummer eingeben.
* **http**: überprüft, ob der Webserver vorhanden ist (Anwendungsserver betriebsbereit).
* **ncs**: überprüft die Prozesse auf der Instanz, die im Attribut &quot;Instanz&quot; eingegeben wurden (Workflow-Fehler, Speicherbelegung usw.). Die **enthalten** (obligatorisch) gibt Ihnen die Möglichkeit, veraltete Prozesse anzuzeigen (&quot;true&quot;- oder &quot;false&quot;-Werte).
* **redir**: überprüft das Tracking.

In den meisten Fällen ist nur die **ncs** und **redir** -Unterelemente beibehalten werden.

In jedem Fall können bestimmte Knoten in den Unterelementen (z. B. dem Knoten ) überschrieben werden **port=75** , um den für die Verbindung http, ncs oder redir verwendeten Port zu überladen):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

Im **ncs**, **redir** und **http** -Unterelementen, können Sie die **isSecure** -Attribut (optional), um festzulegen, ob das HTTPS-Protokoll (&quot;true&quot;- oder &quot;false&quot;-Werte) verwendet werden soll oder nicht. Wenn dieses Attribut nicht angegeben wird, wird das HTTP-Protokoll verwendet.

### Konfigurieren der Datei netreport.bat oder netreport.sh {#configuring-the-netreport-bat-or-netreport-sh--file}

Um sie zu konfigurieren, bearbeiten Sie diese Datei und geben Sie an, in welchem Ordner das JRE- oder JDK installiert ist.

### Startüberwachung {#launching-monitoring}

Um die Überwachung zu starten, führen Sie die **netreport.bat** oder **netreport.sh** in regelmäßigen Abständen über ein Skript. Ein Bericht wird nach der ersten Ausführung und dann nur im Falle einer Statusänderung gesendet.

### Testüberwachung {#testing-monitoring}

Führen Sie zum Testen der Überwachung den **netreport.bat** oder **netreport.sh** -Datei.

An die in der Variablen **recipientList** des **netconf.xml** -Datei.
