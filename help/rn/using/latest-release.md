---
solution: Campaign Classic
product: campaign
title: Aktuelle Version
description: Aktuelle Version von Campaign Classic  Anmerkungen
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 14513d5ecbfdd5637b764c8f19bc01358e63c130
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# Neueste Version{#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Campaign Classic Release Candidate-Version** aufgelistet.

Die Informationen für die Campaign Classic Gold Standard-Version (aktueller allgemein verfügbarer Build) [finden Sie auf dieser Seite](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Version 21.1.1 – Build 9277 {#release-21-1-1-build-9277}

_22. Februar 2021_

**Verbesserungen bei der Sicherheit**

* Der Konsolenauthentifizierungsmechanismus wurde verbessert, um die Sicherheit zu optimieren. (NEO-26944)
* Fehlerkorrektur – Es wurde ein Sicherheitsproblem behoben, um den Schutz vor SSRF-Problemen (Server Side Request Forgery) zu verbessern. (NEO-28532)

**Aktualisierungen zur Kompatibilität**

Die folgenden Systeme werden jetzt von Campaign unterstützt:

* Salesforce API Version 49 wird jetzt bei der Verwendung des Salesforce CRM-Externen Kontos unterstützt.

**Eingestellte Funktionen**

Der Bericht **Überwachung der technischen Lieferbarkeit** wird jetzt nicht mehr unterstützt.

Weitere Informationen finden Sie auf der Seite [Eingestellte und entfernte Funktionen ](../../rn/using/deprecated-features.md).

**Verbesserungen**

**Email Feedback Service (EFS)** ist ein skalierbarer Service, der das Feedback direkt von der erweiterten MTA erfasst und damit die Genauigkeit der Berichte verbessert. Diese Funktion wird als private Beta veröffentlicht und wird in zukünftigen Versionen nach und nach allen Kunden zur Verfügung stehen.

* Alle Kategorien von Feedback werden jetzt für vollständiges und genaues Reporting erfasst.
* Die Berechnung des Zugestellt-Indikators basiert nun auf Echtzeit-Feedback des erweiterten MTA, um Genauigkeit und Reaktivität zu verbessern.
* EFS löst das Problem der Verzögerungen beim Reporting zu synchronen Bounces.

Weitere Informationen finden Sie im [entsprechenden Handbuch](../../delivery/using/sending-with-enhanced-mta.md#efs).
Wenn Sie an dieser privaten Beta-Version teilnehmen möchten, füllen Sie dieses [Formular](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) aus und wir melden uns bei Ihnen.

**Sonstige Änderungen**

* Die Übertragungsgeschwindigkeit für große Trackinglogs wurde durch Komprimierung verbessert.
* Workflow Heatmap wurde verbessert, um Zeitüberschreitungen zu vermeiden, wenn Workflows mit mehreren Aktivitäten ausgeführt werden. (NEO-27423).
* Es wurde ein Problem behoben, durch das ein Angebot angezeigt werden konnte, selbst wenn das Enddatum überschritten wurde. Campaign Classic berücksichtigt nun den gesamten Zeitstempel des Enddatums und nicht nur das Datum. (NEO-27590)
* Der Google+-Link wurde aus dem Personalisierungsblock **Social-Netzwerkfreigabe-Links** entfernt.
* Es wurde ein Problem behoben, das nach der Implementierung einer Fehlerbehebung in der letzten Version auftrat. Beim Verbinden mit SSL/TLS wurde eine Prüfung des Hostnamens hinzugefügt, die dazu führte, dass SMS-Versand fehlschlugen. Die Hostnamenüberprüfung wurde für die meisten Protokolle wie POP3, SMS und HTTP mit Proxy deaktiviert und die Zertifikatsprüfung für das SMS-Externe Konto wurde mit drei Werten verbessert (NEO-29581). [Mehr dazu](../../delivery/using/sms-protocol.md#skip-tls)

**Korrekturen**

* Es wurde ein Fehler behoben, der dazu führte, dass die Tastenkombinationen Tab, Eingabetaste und Escape nicht auf dem neuen Anmeldebildschirm funktionierten.
* Korrektur des Aktualisierungsfehlers, der dazu führte, dass der Name eines neu erstellten Workflows nach dem Speichern durch den Standardwert ersetzt wurde (NEO-26106).
* Es wurde ein Problem behoben, das beim Ausführen Workflows, bei dem ein neues Feld als Teil einer **Anreicherung**-Aktivität vor einer **Versand**-Aktivität mit einem **Zielgruppen-Mapping** hinzugefügt wurde, wenn eine externe Datei ausgeführt wurde, auftrat: Dem Zielgruppen-Mapping **Externe Dateien** wurden unerwünschte Felder hinzugefügt. (NEO-27687)
* Es wurde ein Fehler behoben, der dazu führte, dass einige Zeichen im Quellcode beim erneuten Öffnen einer zuvor erstellten und gespeicherten Webanwendung geändert wurden. (NEO-27597)
* Es wurde ein Problem behoben, das beim Aktualisieren auf einen Build auftrat, einschließlich des neuen Signaturmechanismus für die Verfolgung von Links (von Build 19.1.4 und Kampagne 20.2): Wenn mehrere Vorlagen mit einem Ereignis verknüpft waren, könnte die Aktualisierung dazu führen, dass beim Senden der Transaktionsnachricht die falsche Vorlage ausgewählt wird. (NEO-28326)
* Es wurde ein Fehler behoben, der dazu führte, dass die MTA nicht reagierte und Versand nur verarbeitet werden konnten, wenn sie neu gestartet wurden. (NEO-27455)
* Es wurde ein Problem in der MSSQL-Datenbank behoben, das sich auf die Zeitstempelverwaltung während Massenladevorgängen für eine Datumszeitspalte bezog.
* Es wurde ein Problem mit der Workflow-Abfrage behoben, das bei Verwendung der Redshift xtk-Funktionen auftrat. Die SubDays, SubSeconds, SubMinutes und SubHours akzeptieren jetzt beide Redshift-Zeitstempeltypen (NEO-24962).
* Es wurde ein Problem behoben, bei dem beim Versuch, einen Bericht mit anonymer Vorschau zu erstellen, eine Skriptfehlermeldung angezeigt wurde. (NEO-27081)
* Es wurde ein Problem behoben, durch das die Speicherbelegung auf dem Server beim Ausführen der Versand-Analyse reduziert werden konnte.
* Es wurde ein Fehler behoben, der dazu führte, dass die Instanz beim Versuch, bestimmte komplexe Abfragen auszuführen, nicht funktionierte.
* Es wurde ein Problem behoben, das die Ausführung des technischen Arbeitsablaufs **Synchronisieren von Twitter-Seiten** verhindern konnte. (NEO-28634)
* Es wurde ein Problem behoben, durch das beim Versuch, mithilfe der Versandvorlage **Tweet (twitter)** auf Twitter zu veröffentlichen, eine Fehlermeldung zur Funktion decryptPassword angezeigt werden konnte. (NEO-28216)
* Es wurde ein Problem behoben, das bei der Verwendung einer **JavaScript**-Aktivität zur Erstellung einer HTTP-Anforderung in einem Workflow auftrat. Nach dem Definieren der Anschlussnummer im Hostnamen schlägt der Aufruf mit dem folgenden Fehler fehl (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Es wurde ein Fehler behoben, der verhinderte, dass neue Versand mit Zielgruppe-Datenpersonalisierung gesendet wurden.
* Es wurde ein Problem behoben, bei dem mehrere Abstürze in der Marketing-Instanz auftraten, die zu Kerndateien führten.
* Es wurde ein Fehler behoben, der dazu führte, dass der **Tracking**-Workflow mit dem folgenden Fehler fehlschlug (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Es wurde ein Fehler behoben, der beim Erstellen und Speichern eines Versands auf der Registerkarte **Targeting und Workflow** einer Kampagne auftrat: die Vorschau mit folgendem Fehler fehlschlagen würde (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Es wurde ein Fehler behoben, der beim Einrichten eines Externen Kontos zwischen einer Marketing-Instanz und einer Adobe Campaign Standard-Instanz oder einer Campaign Classic-Mid-Sourcing-Instanz und bei Verwendung der Option &quot;DisableFOH2=1&quot;auftrat. Bei Verwendung der Option &quot;DisableFOH2=1&quot;im Externe Konto wurden die Verbindungen nicht ordnungsgemäß geschlossen, sodass der folgende Fehler auftrat (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Es wurde ein Fehler mit SMS behoben, der auftrat, wenn Verbindungsprobleme zwischen Server und Anbieter auftraten. Die Verbindung wird dann automatisch vom untergeordneten MTA-Objekt deaktiviert. Adobe Campaign Classic würde nicht versuchen, eine Verbindung zu dieser fehlerhaften Verbindung herzustellen, solange kein neues Kind gestartet wurde.
