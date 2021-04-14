---
solution: Campaign Classic
product: campaign
title: Aktuelle Version
description: Aktuelle Version von Campaign Classic    Anmerkungen
feature: Übersicht
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
translation-type: tm+mt
source-git-commit: 2c2dff554c716468c0984f3d893bd29aa9fd4453
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 97%

---

# Aktuelle Version{#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Campaign Classic Release Candidate-Version** aufgelistet.

>[!NOTE]
>
>Builds für die Kampagne **Allgemeine Verfügbarkeit (GA)** sind: [[!DNL Gold Standard] 11 release](../../rn/using/gold-standard.md#gs-11) und [Kampagne 20.2.5 release](../../rn/using/release--20-2.md).


## ![](assets/do-not-localize/blue_2.png) Version 21.1.2 – Build 9282 {#release-21-1-2-build-9282}

_14. April 2021_

* Die Kennwortverwaltung wurde verbessert, um die Sicherheit zu optimieren.
* Es wurde ein Problem behoben, das MTA-Abstürze verursachen konnte.

## ![](assets/do-not-localize/red_2.png) Version 21.1.1 – Build 9277 {#release-21-1-1-build-9277}

_22. Februar 2021_

**Verbesserungen bei der Sicherheit**

* Der Authentifizierungsmechanismus der Konsole wurde verbessert, um die Sicherheit zu optimieren. (NEO-26944)
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-28532)

**Aktualisierungen zur Kompatibilität**

Die folgenden Systeme werden jetzt von Campaign unterstützt:

* Die Salesforce-API-Version 49 wird jetzt bei Verwendung eines externen Salesforce CRM-Kontos unterstützt.

**Eingestellte Funktionen**

Der Bericht zum **technischen Zustellbarkeits-Monitoring** wird jetzt nicht mehr unterstützt.

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen ](../../rn/using/deprecated-features.md).

**Verbesserungen**

**Email Feedback Service (EFS)** ist ein skalierbarer Dienst, der das Feedback direkt vom Enhanced MTA erfasst und damit die Reporting-Genauigkeit verbessert. Diese Funktion wird als private Beta veröffentlicht und wird in zukünftigen Versionen nach und nach allen Kunden zur Verfügung stehen.

* Alle Kategorien von Feedback werden jetzt für vollständiges und genaues Reporting erfasst.
* Die Berechnung des Indikators &quot;Zugestellt&quot; basiert nun auf Echtzeit-Feedback des Enhanced MTA, um Genauigkeit und Reaktivität zu verbessern.
* EFS löst das Problem der Verzögerungen beim Reporting zu synchronen Softbounces.

Weitere Informationen finden Sie im [entsprechenden Handbuch](../../delivery/using/sending-with-enhanced-mta.md#efs).
Wenn Sie an dieser privaten Beta teilnehmen möchten, füllen Sie dieses [Formular](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) aus. Wir werden uns bei Ihnen melden.

**Sonstige Änderungen**

* Die Übertragungsgeschwindigkeit für große Trackinglogs wurde durch Komprimierung verbessert.
* Workflow-Heatmap wurde verbessert, um Zeitüberschreitungen zu vermeiden, wenn Workflows mit mehreren Aktivitäten ausgeführt werden. (NEO-27423).
* Es wurde ein Problem behoben, durch das ein Angebot auch dann präsentiert werden konnte, wenn das Enddatum überschritten wurde. Campaign Classic berücksichtigt nun den gesamten Zeitstempel des Enddatums und nicht nur das Datum. (NEO-27590)
* Der Google+-Link wurde aus dem Gestaltungsbaustein **Teilen-Links der sozialen Netzwerke** entfernt.
* Es wurde ein Problem behoben, das nach der Implementierung einer Fehlerbehebung in der letzten Version auftrat. Beim Verbinden mit SSL/TLS wurde eine Prüfung des Host-Namens hinzugefügt, die dazu führte, dass SMS-Sendungen fehlschlugen. Die Überprüfung des Host-Namens wurde für die meisten Protokolle wie POP3, SMS und HTTP mit Proxy deaktiviert, und die Zertifikatsprüfung für das externe SMS-Konto wurde mithilfe von drei Werten verbessert (NEO-29581). [Weitere Infos](../../delivery/using/sms-protocol.md#skip-tls)

**Korrekturen**

* Fehlerkorrektur – Die Tastenkürzel &quot;Tab&quot;, &quot;Eingabe&quot; und &quot;Escape&quot; können jetzt auf dem neuen Anmeldebildschirm angezeigt werden.
* Fehlerkorrektur – Der Name eines neu erstellten Workflows wird jetzt nach dem Speichern nicht mehr durch den Standardwert ersetzt (NEO-26106).
* Fehlerkorrektur – Beim Ausführen von Workflows, bei denen vor einer **Versandaktivität** ein neues Feld als Teil einer **Anreicherungsaktivität** mithilfe eines Zielgruppen-Mappings auf der Basis von **externen Dateien** hinzugefügt wird, besteht jetzt kein Problem mehr. Zuvor wurden dem Zielgruppen-Mapping auf der Basis von **externen Dateien** unerwünschte Felder hinzugefügt. (NEO-27687)
* Fehlerkorrektur – Jetzt werden beim erneuten Öffnen einer zuvor erstellten und gespeicherten Web-Anwendung keine Zeichen im Quellcode mehr geändert. (NEO-27597)
* Fehlerkorrektur – Beim Aktualisieren auf einen Build, der den neuen Signaturmechanismus zum Tracking von Links bereitstellt (ab Build 19.1.4 und Campaign 20.2), tritt jetzt kein Problem mehr auf. Wenn mehrere Vorlagen mit einem Ereignis verknüpft waren, konnte die Aktualisierung zuvor dazu führen, dass beim Senden der Transaktionsnachricht die falsche Vorlage ausgewählt wurde. (NEO-28326)
* Fehlerkorrektur – Mit dem MTA tritt jetzt kein Problem mehr auf. Zuvor konnte es passieren, dass er nicht mehr reagierte und keine Sendungen mehr verarbeiten konnte, sodass er neu gestartet werden musste. (NEO-27455)
* Fehlerkorrektur – In der MSSQL-Datenbank tritt jetzt während Massenladevorgängen kein Problem mehr mit der Zeitstempelverwaltung in einer Spalte vom Typ &quot;Datum/Uhrzeit&quot; auf.
* Fehlerkorrektur – Die Workflow-Abfrage funktioniert bei Verwendung von Redshift-xtk-Funktionen jetzt fehlerfrei. Die SubDays-, SubSeconds-, SubMinutes- und SubHours-Funktionen akzeptieren nun beide Redshift-Zeitstempeltypen (NEO-24962).
* Fehlerkorrektur – Jetzt wird keine Skript-Fehlermeldung mehr angezeigt, wenn versucht wird, eine Vorschau eines Berichts mit anonymem Zugriff zu erstellen. (NEO-27081)
* Fehlerkorrektur – Bei der Durchführung der Versandanalyse wird die Speichernutzung auf dem Server nicht mehr verringert.
* Fehlerkorrektur – Bei der Ausführung bestimmter komplexer Abfragen funktioniert die Instanz jetzt einwandfrei.
* Fehlerkorrektur – Der technische Workflow zum **Synchronisieren von Twitter-Seiten** kann jetzt problemlos ausgeführt werden. (NEO-28634)
* Fehlerkorrektur – Jetzt wird im Zusammenhang mit der Funktion &quot;decryptPassword&quot; keine Fehlermeldung mehr angezeigt, wenn versucht wird, mithilfe der Versandvorlage **Tweet (Twitter)** Inhalte auf Twitter zu veröffentlichen. (NEO-28216)
* Fehlerkorrektur – Jetzt tritt kein Problem mehr auf, wenn zum Erstellen einer HTTP-Anfrage in einem Workflow eine **JavaScript**-Aktivität verwendet wird. Nach der Definition der Port-Nummer im Host-Namen schlug der Aufruf fehl, und folgender Fehler wurde angezeigt (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Fehlerkorrektur – Jetzt können neue Sendungen mit personalisierten Zielgruppendaten durchgeführt wurden (NEO-30323).
* Fehlerkorrektur – In der Marketing-Instanz treten keine Abstürze mehr auf, die Core-Dateien erzeugen.
* Fehlerkorrektur – Der **Tracking**-Workflow schlägt nicht mehr fehl. Zuvor wurde folgender Fehler angezeigt (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Fehlerkorrektur – Beim Erstellen und Speichern eines Versands in der Registerkarte **Zielgruppenbestimmungen und Workflows** einer Kampagne tritt jetzt kein Fehler mehr auf. Zuvor schlug die Vorschau fehl und folgender Fehler wurde angezeigt (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Fehlerkorrektur – Beim Einrichten eines externen Kontos zwischen einer Marketing-Instanz und einer Adobe Campaign Standard-Instanz oder einer Campaign Classic-Mid-Sourcing-Instanz tritt bei Verwendung der Option &quot;DisableFOH2 = 1&quot; jetzt kein Fehler mehr auf. Bei Verwendung der Option &quot;DisableFOH2 = 1&quot; im externen Konto wurden die Verbindungen nicht ordnungsgemäß geschlossen und stauten sich, was zu folgendem Fehler führte (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Fehlerkorrektur – Beim SMS-Versand tritt jetzt kein Fehler mehr auf, wenn Verbindungsprobleme zwischen Server und Provider bestehen. Zuvor wurde die Verbindung vom untergeordneten MTA-Element automatisch deaktiviert. Adobe Campaign Classic versuchte erst wieder, eine neue Verbindung herzustellen, wenn ein neues untergeordnetes Element gestartet wurde. 
