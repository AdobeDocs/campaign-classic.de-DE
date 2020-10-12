---
title: Version 18.4
seo-title: Version 18.4
description: Version 18.4
seo-description: null
page-status-flag: never-activated
uuid: d132570e-20e6-4550-95bd-176701f43b19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 4dc87ff3-eb6a-40ac-97ee-00b64cd7718d
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '2285'
ht-degree: 100%

---


# Version 18.4{#release-18-4}

## Version 18.4.5 – Build 8937{#release-18-4-5-build-8937}

_21. November 2018_

**Neuheiten**

* Mehrere Probleme bei der Ausführung von Workflows unter Verwendung von MySQL bei FDA wurden beseitigt. (NEO-11652)
* Fehlerkorrektur – Jetzt verharrt kein Teil der Versandpopulation mehr im Status &quot;Ausstehend&quot;. (NEO-11336)
* Fehlerkorrektur – Jetzt tritt bei der automatischen SMS-Antwort kein Problem mehr auf. (NEO-11811)
* Fehlerkorrektur – Bei der Verwendung von Testadressen in einem Versand sind IDs jetzt unbegrenzt verfügbar. (NEO-11842)
* Fehlerkorrektur – Beim Sortieren in einer Anreicherungsaktivität in einem Workflow tritt kein Syntaxfehler mehr auf. (NEO-11394)
* Fehlerkorrektur – Beim Neustart von IIS besteht nicht mehr die Gefahr eines Webserver-Absturzes. (NEO-10862)
* Fehlerkorrektur – Im Tracking-Workflow tritt nach einer Build-Aktualisierung kein Fehler mehr auf (FDA - SQL). (NEO-11635)
* Fehlerkorrektur – Workflow-Listendaten gehen jetzt nicht mehr verloren. (NEO-11696)
* Fehlerkorrektur – Beim Versand von Push-Benachrichtigungen treten keine Leistungsprobleme mehr auf. (NEO-11787)
* Fehlerkorrektur – Webtracking funktioniert jetzt für &quot;com.au&quot;-Domains. (NEO-4385)
* Fehlerkorrektur – Bei der Verwendung von komplexen Workflows friert der Client nicht mehr ein. (NEO-11847)
* Fehlerkorrektur – Jetzt tritt beim Speichern eines neuen Versands nach der Auswahl eines Elements eines bestimmten Schemas kein Oracle-Fehler mehr auf. (NEO-11682)
* Fehlerkorrektur – Jetzt tritt beim Aufrufen eines Feldes, das Zeichen mit Akzenten enthält, kein Fehler mehr auf (FDA/Teradata). Sie können die Kodierung zur Kommunikation mit dem Teradata-Treiber jetzt über das externe Konto ändern. (NEO-11818).
* Fehlerkorrektur – Die Mobile App erhält jetzt keine falsch formatierten oder falschen Daten mehr, wenn URLs in zusätzlichen Variablen in einer Push-Benachrichtigung weitergegeben werden. (NEO-11468, NEO-11960)
* Fehlerkorrektur – Die Werteverteilung mit einer 1:N-Relation wird jetzt korrekt angezeigt. (NEO-11820)
* Fehlerkorrektur – Bulk-Load funktioniert in Teradata 16 jetzt einwandfrei.
* Die Puffergröße für den Zeitstempel bei Teradata wurde erhöht, um Bind-Probleme beim 15.10-Treiber zu vermeiden.
* Die Verwaltung langer Indexnamen wurde verbessert, was andernfalls Probleme mit dem Postupgrade verursachen könnte.
* Die Verfügbarkeitsdauer des gemeinsamen Speichers bei der Verarbeitung von untergeordneten Zombieprozessen wurde verlängert (MTA).
* In Apache wurde ein potenzieller Deadlock behoben (Tracking).

## Version 18.4.4 – Build 8936{#release-18-4-4-build-8936}

1. August 2018

**Neuheiten**

* E-Mail-Archivierungs-Logs wurden verbessert. Dank der BCC-Archivierung kann jetzt einfacher festgestellt werden, welche E-Mails erfolgreich gesendet wurden oder fehlgeschlagen sind. (NEO-10675)
* Fehlerkorrektur – In den Tracking-Broadlogs werden jetzt Kunden-IPs anstatt Lastverteilungs-IPs angezeigt. (NEO-11295)
* Fehlerkorrektur – Bei der LATIN1-Codierung tritt jetzt kein Fehler mehr auf, wenn eine FDA-Verbindung zu einer PostgreSQL-Datenbank verwendet wird. (NEO-11299)
* Fehlerkorrektur – Bei der Verwendung der Versandoption **[!UICONTROL Personalisierungsdaten mit einem Workflow vorbereiten]** tritt kein Fehler mehr auf. (NEO-11047, NEO-11301)
* Fehlerkorrektur – Die Eigenschaften eines Versands werden nicht mehr fälschlicherweise überschrieben. (NEO-11015)
* Fehlerkorrektur – Bei der Verwendung von berechneten Feldern in der Workflow-Aktivität **[!UICONTROL Umfrageantworten]** tritt kein Fehler mehr auf. (NEO-11382)
* Es wurde ein Problem behoben, das bei der Verwendung von in XML gespeicherten Daten in einer Workflow-Aktivität **[!UICONTROL Umfrageantworten]** auftrat. (NEO-10816)
* Es wurde ein Problem bei der Server-Aktualisierung mit Build 8935 behoben.
* Fehlerkorrektur – Im Postupgrade-Log werden keine unnützen Fehler mehr angezeigt, wenn die Workflow-Aktivität **[!UICONTROL Umfrageantworten]** nicht vollständig konfiguriert ist.
* FDA-Teradata: Es wurde ein Problem mit automatisch inkrementierten Feldern und Indizes in SQL-Tabellen behoben.

## Version 18.4.3 – Build 8935{#release-18-4-3-build-8935}

_22. Juni 2018_

**Neuheiten**

* Fehlerkorrektur – die Tracking-Kodierung bei Microsoft Edge und Internet Explorer funktioniert nun fehlerfrei. (NEO-11257)
* Fehlerkorrektur – Bildlinks beim LINE-Versand können nun personalisiert werden. (NEO-11077)
* Fehlerkorrektur – der Mechanismus für die Generierung von ID-Sequenzen wird nun ordnungsgemäß ausgeführt. (NEO-11115)
* Fehlerkorrektur – Datenschutzanfragen (DSGVO) funktionieren nun, wenn ein benutzerdefinierter Namespace mit einem Integer-Abstimmschlüssel verwendet wird. (NEO-11123)
* Fehlerkorrektur – die Verwendung der Option **[!UICONTROL Werteverteilung]** in **[!UICONTROL Abfrage]**-Workflow-Aktivitäten funktioniert nun fehlerfrei. (NEO-10958)
* Fehlerkorrektur – die Synchronisierung von Platzierungen zwischen der Marketinginstanz und der Interaktionsinstanz funktioniert nun fehlerfrei. (NEO-11162)
* Die Verwaltung langer Indexnamen während des Postupgrades wurde verbessert.

## Version 18.4.2 – Build 8932{#release-18-4-2-build-8932}

_22. Mai 2018_

**Neuheiten**

* Fehlerkorrektur – das Update für Windows Server wird nun ordnungsgemäß ausgeführt.
* Fehlerkorrektur – für die Aktivität **[!UICONTROL Umfrageergebnis]** wird der Bericht bei Verwendung von in XML gespeicherten Daten nun ordnungsgemäß angezeigt. (NEO-10816)
* Fehlerkorrektur – für den inMail-Prozess tritt bei Verwendung eines Bounce Message-Servers kein Leistungsproblem mehr auf. (NEO-10641)
* Fehlerkorrektur – bei der Aktualisierung von mehr als 1.000 Schemata gibt es kein Problem mehr beim Datenbank-Update.

## Version 18.4 – Build 8931{#release-18-4-build-8931}

_24. April 2018_

**Neue Funktionen?**

<table> 
 <thead> 
  <tr> 
   <th> Funktion<br /> </th> 
   <th> Beschreibung<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> EU-Datenschutz-Grundverordnung (DSGVO)<br /> </td> 
   <td> <p>Die DSGVO ist die neue Datenschutz-Grundverordnung der Europäischen Union (EU), die am 25. Mai 2018 in Kraft tritt und in der die Anforderungen an den Datenschutz harmonisiert und neu geregelt werden. Die DSGVO gilt für Adobe Campaign-Kunden, die Daten von Personen erfassen, die in der EU wohnhaft sind.</p> <p>Aus diesem Grund möchten wir als Datenverarbeiter Ihnen als Datenverantwortlichen zusätzlich zu den bereits in Adobe Campaign verfügbaren Datenschutzoptionen (Einverständnisverwaltung, Einstellungen für die Datenbeibehaltung und Benutzerrollen etc.) weitere Funktionen bereitstellen, mit deren Hilfe Sie DSGVO-konformes Verhalten sicherstellen können:</p> 
    <ul> 
     <li> <p>Recht auf Zugriff: Das Datensubjekt hat das Recht, eine Kopie seiner personenbezogenen Daten, die vom Datenverantwortlichen erfasst werden, zu erhalten. Hierzu zählen unter Umständen auch die in Adobe Campaign gespeicherten Daten.</p> </li> 
     <li> <p>Recht auf Löschung: Das Datensubjekt hat das Recht, seine personenbezogenen Daten, die vom Datenverantwortlichen erfasst werden, löschen zu lassen. Hierzu zählen unter Umständen auch die in Adobe Campaign gespeicherten Daten.</p> </li> 
    </ul> Lesen Sie für weiterführende Informationen das <a href="https://helpx.adobe.com/de/campaign/kb/acc-privacy.html">entsprechende Handbuch</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aktive Profile<br /> </td> 
   <td> <p>Adobe Campaign stellt nun eine Liste aktiver Profile zur Verfügung, die jeden Monat mithilfe eines speziellen Workflows aktualisiert wird.</p> <p>Weitere Informationen finden Sie im <a href="../../platform/using/about-profiles.md#active-profiles">entsprechenden Handbuch</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Verbesserung des Android-Connectors für Push-Benachrichtigungen<br /> </td> 
   <td> <p>Der Android-Connector wurde verbessert und bietet jetzt höheren Durchsatz. </p> <p>Weitere Informationen finden Sie im <a href="../../delivery/using/configuring-the-mobile-application.md">entsprechenden Handbuch</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

* Die Erweiterung externer Entitäten ist jetzt deaktiviert, um potenzielle Angriffe von nicht authentifizierten Benutzern zu verhindern. (NEO-10173)
* Die Berechtigungen werden jetzt strenger gehandhabt, um Standardbenutzer daran zu hindern, die Konfigurationsparameter der Instanz zu verändern, wie etwa URLs zum Zugriff auf Anwendungen, LDAP-Einstellungen etc. (NEO-10171)
* Fehlerkorrektur – Jetzt werden keine sensiblen Daten mehr über Stack Traces offengelegt. Fehlerdetails werden jetzt im Backend an einem Ort protokolliert, der nicht vom externen Netzwerk aus zugänglich ist. (NEO-10176)
* Die Berechtigungen werden jetzt strenger gehandhabt, um Standardbenutzer daran zu hindern, die von einem Administrator hochgeladenen Dokumente und/oder exportierten Packages zu sehen. (NEO-10170)

**Neuheiten**

* **LINE-Kanal - verbesserte Architektur**: Der LINE-Kanal wird jetzt wie alle anderen Kanäle in Adobe Campaign in allen Installationstypen unterstützt: gehostet, Hybrid und On-Premise.
* **Automatische Erzeugung von Sequenzen**: Der Mechanismus zur ID-Erzeugung wurde verbessert, sodass nun die Lebensdauer von Campaign-Instanzen bei großen Objektmengen verlängert ist. Weiterführende Informationen finden Sie in dieser [Technote](https://helpx.adobe.com/de/campaign/kb/sequence_auto_generation.html).

**Sonstige Änderungen**

* Für den Package-Import ist ein neuer Modus verfügbar, bei dem die Befehlszeile verwendet wird. Dadurch sind zirkuläre Abhängigkeiten möglich (nicht empfohlen für große Packages). Weiterführende Informationen dazu finden Sie im Abschnitt &quot;Technische Entwicklungen&quot;. (NEO-8979)
* Die Leistung für große, in Teradata geladene Datenmengen wurde verbessert. Außerdem wurde ein Fehler behoben, sodass nun der richtige Wert verarbeiteter Daten im Log angezeigt wird. (NEO-10429)
* Der Import von Audiences aus Audience Manager funktioniert jetzt mit aufgesplitteten Dateien. Zuvor wurde vom technischen Workflow importSharedAudience nur die letzte Datei des Segments importiert. (NEO-10156)
* Unter Windows hat sich der Standard-Installationspfad für den Campaign-Server geändert. Beim Setup der 64-Bit-Version lautet der standardmäßige Installationspfad jetzt: **C:\Program Files\Adobe\Adobe Campaign Classic v7** anstatt **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**.
* Die Standard-MX-Regeln wurden verbessert und enthalten jetzt mehr Domains und ermöglichen höheren Durchsatz.
* Zugriffsbeschränkungen für den SOAP-Aufruf des Softwareverteilungs-Assistenten wurden verstärkt (xtk:serverOptions#SaveOptions).
* Die veraltete Bibliothek weka.jar wurde entfernt und die OpenSSL-Bibliothek wurde zur Optimierung der Sicherheit aktualisiert.
* Der technische Fakturierungs-Workflow wurde verbessert, um eine ausreichende Leistung der Instanzen sicherzustellen.
* Administratoren haben jetzt wieder die Möglichkeit, das Passwort von Benutzern festzulegen oder zurückzusetzen. Klicken Sie dazu mit der rechten Maustaste auf einen Benutzer, wählen Sie **[!UICONTROL Aktionen]** > **[!UICONTROL Passwort zurücksetzen]** und geben Sie das neue Passwort des Benutzers ein. Wir empfehlen Benutzern, ihr Passwort bei der ersten Anmeldung zu ändern. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../production/using/lost-password.md).
* Um die neue Mandantenfähigkeit in Adobe Target zu unterstützen, kann jetzt ein neuer &quot;at_property&quot;-Parameter zu URLs hinzugefügt werden, wenn Optionen und externe Konten für die Integration mit Target konfiguriert werden. Der für diesen Parameter zu verwendende Wert kann Adobe Target entnommen werden und wird von Campaign bei Abrufen in Target verwendet. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../integrations/using/inserting-a-dynamic-image.md).
* Jetzt kann eine Standard-Landingpage spezifiziert werden, die sich öffnet, wenn auf ein von Adobe Target ausgegebenes Bild geklickt wird. Zuvor wurde bei Klick nur zum bei der E-Mail-Erstellung eingefügten Standard-Bild weitergeleitet. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../integrations/using/inserting-a-dynamic-image.md).
* Im externen Konto wurde das Kästchen **Enable SMPP traces** hinzugefügt, um die Spurenausgabe zu erzwingen. Weiterführende Informationen dazu finden Sie im [entsprechenden Handbuch](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Technische Entwicklungen**

queryDef

queryDef wurde in Bezug auf die Bedingung &quot;orderBy&quot; geändert. Vor der Änderung wurde der Primärschlüssel der abgefragten Tabelle implizit zur Bedingung &quot;orderBy&quot; hinzugefügt. Bei manchen Datenbank-Engines (zumindest postgresql) verhindert dies die Verwendung von Indizes (alle Felder der Bedingung orderBy müssen im selben Index eingeschlossen sein). Wenn Ihre Konfiguration vom früheren Verhalten abhängt, müssen Sie nun den Primärschlüssel in Ihrer Bedingung &quot;orderBy&quot; explizit hinzufügen.

Angenommen, Sie haben die folgende Abfrage:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Diese würde implizit so gehandhabt werden (vor den Änderungen von 18.4):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode function

Die JavaScript-Funktion &quot;urlEncode&quot; hat für Nicht-ASCII-Zeichen nicht ordnungsgemäß funktioniert. Das wurde jetzt korrigiert und die Funktion kann jetzt mit allen Unicode-Zeichen verwendet werden (einschließlich japanischer Zeichen). Wenn Sie für Nicht-ASCII-Zeichen das &quot;urlEncode&quot;-Verhalten benötigen, müssen Sie Ihren Code anpassen.

Neuer Modus für Package-Import

Für den Package-Import ist ein neuer Modus verfügbar, bei dem die Befehlszeile verwendet wird, was zirkuläre Abhängigkeiten ermöglicht (nicht empfohlen für große Packages). Die vorhandene Funktion wird beibehalten. Für diese Packages mit zirkulären Abhängigkeiten wurde das neue Flag **-usejs** zum Befehlszeilen-Package-Import hinzugefügt. Bei der Ausführung wird die JSEngine so verwendet, als würde der Package-Import in der Benutzeroberfläche durchgeführt.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Korrekturen**

* Fehlerkorrektur - jetzt tritt kein Synchronisationsfehler mehr auf, wenn Versand- und Trackinglogs von Adobe Campaign Standard nach Adobe Campaign Classic repliziert werden. (NEO-10023)
* Fehlerkorrektur - jetzt können Fehler- und Log-Tabellen problemlos in Teradata verwendet werden, wenn ein ETL-Workflow nach einem Fehler bei einem Schnellladevorgang fortgesetzt wird. Die Fehler- und Log-Tabellen werden jetzt beim Fortsetzen des Workflows ordnungsgemäß gelöscht. (NEO-10672)
* Fehlerkorrektur - jetzt wird beim Postupgrade das Hive-Package automatisch installiert (für Hadoop erforderlich), wenn das FDA-Package installiert ist. (NEO-10592)
* Fehlerkorrektur - ungültige Domains werden jetzt nicht mehr als **nicht definierter** Fehler gehandhabt. (NEO-10248)
* Fehlerkorrektur - Logs werden jetzt nicht mehr in der deliveryLogStats-Tabelle dupliziert, wenn Android-Push-Benachrichtigungen gesendet werden. (NEO-10234)
* Fehlerkorrektur – jetzt können alle Barcodeformate von Barcodescannern gelesen werden. (NEO-10125)
* Fehlerkorrektur - die JavaScript-Funktion &quot;urlEncode&quot; kann jetzt mit Nicht-ASCII-Zeichen verwendet werden. Weiterführende Informationen dazu finden Sie im Abschnitt &quot;Technische Entwicklungen&quot;. (NEO-10123)
* Fehlerkorrektur - Abfragen mit sha256-Funktionen in Teradata-Datenbanken können jetzt fehlerfrei durchgeführt wird. (NEO-10119)
* Fehlerkorrektur - jetzt treten bei der SalesForce-Aktivität keine Workflow-Speicherfehler mehr auf, wenn sehr große SalesForce-Tabellen verwendet werden. (NEO-9900)
* Fehlerkorrektur - Bei Verwendung von FDA tritt in Zielgruppen-Workflow-Aktivitäten bei der Verwendung der Option **Komplement erzeugen** jetzt kein Fehler mehr auf. (NEO-9878)
* Fehlerkorrektur - die Metriken **Verarbeitet** und **Erfolg** werden jetzt in der Marketinginstanz aktualisiert, wenn Mid-Sourcing verwendet wird. (NEO-9454)
* Korrektur der Interaktionsregeln zur Verhinderung von Neuvorschlägen bei mehr als 10.000 Angeboten auf der Plattform. (NEO-9352)
* Fehlerkorrektur - die Zielgruppe eines Versands kann jetzt bei der Verwendung einer externen XML-Datei spezifiziert werden. (NEO-9312)
* Fehlerkorrektur - jetzt treten keine Workflow-Fehler mehr auf, wenn eine Hypothese für ein Angebot ausgeführt und der Status des Vorschlags aktualisiert wird. (NEO-9304)
* Fehlerkorrektur - die Versandanalyse wird jetzt fehlerfrei ausgeführt, wenn Werbedruck-Regeln auf der Basis eines Attributs des Android-Versand-Mappings verwendet werden. (NEO-9202)
* Fehlerkorrektur - Spalten in Empfängerlisten können jetzt sortiert werden, ohne Leistungsprobleme hervorzurufen. Weiterführende Informationen zu den queryDef-Änderungen finden Sie unten im Abschnitt &quot;Technische Entwicklungen&quot;. (NEO-9042)
* Fehlerkorrektur - die Links in einer Validierungs-E-Mail verweisen nicht mehr auf eine falsche Anmelde-URL. Dieser Fehler trat insbesondere auf, wenn ein Login vom Typ &quot;Federated ID&quot; verwendet wurde. (NEO-9011)
* Fehlerkorrektur - jetzt werden in der Datumsauswahl von Berichten keine falschen Daten mehr für gewisse Zeitzonen angezeigt. (NEO-9007)
* Fehlerkorrektur - die Zielgruppe eines ausgehenden Versands kann jetzt bei der Verwendung einer FDA-SQL-Datenbank angezeigt werden. (NEO-8924)
* Fehlerkorrektur - der CRM-Connector MS Dynamics ruft jetzt auch Daten für die ersten sieben Tage eines Monats ab. (NEO-8803)
* Fehlerkorrektur - bei der Analytics-Integration können jetzt auch internationale Zeichen einbezogen werden. (NEO-8719)
* Fehlerkorrektur - die Bearbeitung eines Workflows ist jetzt nur mehr mit den entsprechenden Rechten möglich. (NEO-8708)
* Fehlerkorrektur - bei FDA über HTTP treten jetzt keine Verbindungsunterbrechungen oder Verbindungsverluste (durch Zeitüberschreitung) mehr auf, wenn das Message Center in einer Hybridarchitektur verwendet wird. (NEO-8438)
* Fehlerkorrektur - jetzt treten bei der Aktivität &quot;Inkrementelle Abfrage&quot; keine Workflow-Fehler mehr für negative IDs auf. (NEO-8229)
* Fehlerkorrektur - jetzt werden Bildlaufleisten auf manchen Bildschirmen nicht mehr doppelt angezeigt. (NEO-8208)
* Fehlerkorrektur - jetzt wird keine Fehlermeldung mehr angezeigt, wenn der Assistent zur Aktualisierung der Datenbankstruktur ausgeführt wird. Im Postupgrade werden Indizes mit Namen mit mehr als 30 Zeichen umbenannt. Beachten Sie bitte, dass bei großen Tabellen das Ersetzen der Indizes einige Zeit in Anspruch nimmt. (NEO-7983)
* Fehlerkorrektur - Trackinglogs werden jetzt korrekt von der Message-Center-Ausführungsinstanz zur Kontrollinstanz synchronisiert. (NEO-7286)
* Fehlerkorrektur - bei der Angebotsanreicherungsaktivität tritt kein Leistungsproblem mehr auf. (NEO-7263)
* Fehlerkorrektur - die DaysAgo-Funktion kann jetzt verwendet werden, wenn eine Redshift-Datenbank über FDA abgefragt wird. (NEO-7099)
* Fehlerkorrektur - bei der Datenverwaltung tritt keine Regression mehr auf, sodass bei Workflow-Aktivitäten zur Anreicherung jetzt Indizes erstellt werden können.
* Fehlerkorrektur - jetzt tritt kein Fehler mehr auf, wenn externe Ressourcen mit dem Titel @id erstellt werden.
* Fehlerkorrektur - beim Hochladen von komprimierten Dateien über einen FTP-Server oder mit Wildcards im Dateinamen tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur - bei in Campaign Standard erstellten externen benutzerdefinierten Ressourcen, die Auflistungen mit Datentyp &quot;long&quot; enthalten, tritt kein Fehler mehr auf.
* Fehlerkorrektur - SMS werden jetzt nur mehr gesendet, wenn eine Verbindung mit dem Provider hergestellt werden kann. Zuvor hatte dies den Verlust von SMS zur Folge.
* Fehlerkorrektur - Der SMTP-Verbindungsaufbau kann jetzt nicht mehr unbegrenzte Zeit in Anspruch nehmen.
* Fehlerkorrektur - jetzt tritt bei Druck-Typologieregeln während der Nachrichtenvorbereitung kein Fehler mehr auf, wenn LINE-Mapping verwendet wird oder wenn die Filter- und Zielgruppenschemata unterschiedlich sind.
