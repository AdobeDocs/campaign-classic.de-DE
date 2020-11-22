---
solution: Campaign Classic
product: campaign
title: Administration
description: Administration
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 100%

---


# Administration{#administration}

Automatischer Start der Adobe Campaign-Module (**Web**, **mta**, **wfserver** usw.) wird vom **nlserver** -Server bereitgestellt.

Bei der Installation von Adobe Campaign wird der Rechner automatisch so konfiguriert, dass der **nlserver** -Dienst während der Startsequenz Beginn wird.

Mit den folgenden Befehlen wird der Adobe Campaign-Dienst manuell Beginn und heruntergefahren:

* Windows:

   * **net Beginn nlserver6**
   * **net stop nlserver6**

* Unter Linux (als root):

   * **/etc/init.d/nlserver6 Beginn**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>Ab 20.1 wird empfohlen, stattdessen den folgenden Befehl zu verwenden (für Linux): **systemctl Beginn nlserver** / **systemCtl stop nlserver**

Im Folgenden finden Sie eine Liste der üblichen Verwaltungsbefehle, auf die unter Linux (als **Adobe Campaign**) zugegriffen werden kann:

* Alle gestarteten Adobe Campaign-Module anzeigen: **/etc/init.d/nlserver6 pdump** oder **/etc/init.d/nlserver6-Status**

   >[!NOTE]
   >
   >Durch Hinzufügen des Parameters **-who** zum **Befehl pdump** können Sie Informationen zu aktuellen Verbindungen (Benutzer und Prozesse) erfassen.\
   >Der **Befehl &quot;/etc/init.d/nlserver6 status** &quot;(ohne den Parameter &quot;-who&quot;) gibt Folgendes zurück:
   >
   >    * 0, wenn alle Prozesse ausgeführt werden.
   >    * 1, wenn ein Prozess fehlt.
   >    * 2, wenn kein Prozess ausgeführt wird.
   >    * einen anderen Wert, wenn ein Fehler auftritt.


* Beginn/Stopp eines Multi-Instanz- oder Mono-Instanzmoduls (**web**, **trackinglogd**, **syslogd**, **mta**, **wfserver******,inmail):

   **nlserver-Beginn`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Sie können auch den **nlserver-`<module>[@<instance>]`** Befehl Neustart verwenden, um ein Modul neu zu starten.

   Beispiel:

   **nlserver Beginn Web**

   **nlserver-Beginn mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web -quick**

   **nlserver-Neustart Web**

   >[!NOTE]
   > 
   >    * Wenn die Instanz nicht angegeben ist, wird die Standardinstanz verwendet.
   >    * Im Ereignis eines Notfalls verwenden Sie die **-sofortige** Option, um einen sofortigen Stopp des Vorgangs zu erzwingen (entspricht Unix Befehl **töten -9**).
   >    * Verwenden Sie die Option **-noconsole** , um sicherzustellen, dass das gestartete Modul nichts in der Konsole anzeigt. Seine Protokolle werden über das **syslogd** Modul auf die Festplatte geschrieben.
   >    * Verwenden Sie die Option **-verbose** , um weitere Informationen zu Prozessaktionen anzuzeigen.

      >    
      >      
      Beispiel:
      >    
      >      
      **nlserver Neustart web -verbose**
      >    
      >      
      **nlserver-Beginn mta@myinstance -verbose**
      >    
      >      
      Mit dieser Option werden zusätzliche Protokolle hinzugefügt. Es wird empfohlen, die Prozesse erneut ohne die **-ausführliche** Option zu starten, sobald Sie die gewünschten Informationen gefunden haben, um zu vermeiden, dass Protokolle überladen werden.


* Beginn aller Adobe Campaign-Prozesse (entspricht dem Starten des **nlserver6** -Dienstes):

   **nlserver watchdog -noconsole**

* Beenden Sie alle Adobe Campaign-Prozesse (entsprechend dem Herunterfahren des **nlserver6** -Dienstes):

   **nlserver shutdown**

* Laden Sie die Konfiguration des **nlserver-Webmoduls** (und ggf. das Webserver-Erweiterungsmodul) neu, wenn die **Dateien &quot;serverConf.xml** &quot;und &quot; **config-&quot;`<instance>  .xml </instance>`** bearbeitet wurden.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Einige Konfigurationsänderungen werden nicht dynamisch berücksichtigt. Adobe Campaign muss heruntergefahren und dann neu gestartet werden.

