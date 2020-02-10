---
title: Administration
seo-title: Administration
description: Administration
seo-description: null
page-status-flag: never-activated
uuid: 376efec1-1647-43b4-b72f-2603214c7cc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 860be8be-f28c-4836-b4fb-e91c6a4616c6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Administration{#administration}

Automatischer Start der Adobe Campaign-Module (**Web**, **mta**, **wfserver** usw.) wird vom **nlserver** -Server bereitgestellt.

Bei der Installation von Adobe Campaign wird der Computer automatisch so konfiguriert, dass der **nlserver** -Dienst während der Startsequenz gestartet wird.

Die folgenden Befehle werden verwendet, um den Adobe Campaign-Dienst manuell zu starten und herunterzufahren:

* Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* Unter Linux (als root):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

Im Folgenden finden Sie eine Liste der üblichen Verwaltungsbefehle, auf die unter Linux (als **Adobe Campaign**) zugegriffen werden kann:

* Alle gestarteten Adobe Campaign-Module anzeigen: **/etc/init.d/nlserver6 pdump** oder **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Durch Hinzufügen des Parameters **-who** zum **Befehl pdump** können Sie Informationen zu aktuellen Verbindungen (Benutzer und Prozesse) erfassen.\
   >Der **Befehl &quot;/etc/init.d/nlserver6 status** &quot;(ohne den Parameter &quot;-who&quot;) gibt Folgendes zurück:
   >
   >    * 0, wenn alle Prozesse ausgeführt werden.
   >    * 1, wenn ein Prozess fehlt.
   >    * 2, wenn kein Prozess ausgeführt wird.
   >    * einen anderen Wert, wenn ein Fehler auftritt.


* Ein mehrinstanzliches oder eininstanzliches Modul (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver******,inmail) starten/beenden:

   **nlserver start`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Sie können auch den **nlserver-`<module>[@<instance>]`**Befehl Neustart verwenden, um ein Modul neu zu starten.

   Beispiel:

   **nlserver start web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web -quick**

   **nlserver-Neustart Web**

   >[!NOTE]

   >* Wenn die Instanz nicht angegeben ist, wird die Standardinstanz verwendet.
   >    
   >    
   >    * Im Falle eines Notfalls verwenden Sie die **-sofortige** Option, um einen sofortigen Stopp des Prozesses zu erzwingen (entsprechend Unix Befehl **töten -9**).
   * Verwenden Sie die Option **-noconsole** , um sicherzustellen, dass das gestartete Modul nichts in der Konsole anzeigt. Seine Protokolle werden über das **syslogd** Modul auf die Festplatte geschrieben.
   * Verwenden Sie die Option **-verbose** , um weitere Informationen zu Prozessaktionen anzuzeigen.


      Beispiel:


      **nlserver Neustart web -verbose**


      **nlserver start mta@myinstance -verbose**


      Mit dieser Option werden zusätzliche Protokolle hinzugefügt. Es wird empfohlen, die Prozesse erneut ohne die **-ausführliche** Option zu starten, sobald Sie die gewünschten Informationen gefunden haben, um zu vermeiden, dass Protokolle überladen werden.


* Starten Sie alle Adobe Campaign-Prozesse (entspricht dem Starten des **nlserver6** -Dienstes):

   **nlserver watchdog -noconsole**

* Schließen Sie alle Adobe Campaign-Prozesse (entsprechend dem Herunterfahren des **nlserver6** -Dienstes):

   **nlserver shutdown**

* Laden Sie die Konfiguration des **nlserver-Webmoduls** (und gegebenenfalls des Webserver-Erweiterungsmoduls) neu, wenn die **Dateien &quot;serverConf.xml** &quot;und &quot; **config-&quot;`<instance>  .xml </instance>`**bearbeitet wurden.

   **nlserver config -reload**

   >[!NOTE]
   Einige Konfigurationsänderungen werden nicht dynamisch berücksichtigt. Adobe Campaign muss beendet und dann neu gestartet werden.

