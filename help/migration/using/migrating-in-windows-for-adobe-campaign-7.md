---
product: campaign
title: Migrieren einer Microsoft Windows-Plattform zu Adobe Campaign v7
description: Erfahren Sie, wie Sie eine Microsoft Windows-Plattform auf Adobe Campaign v7 migrieren.
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
hide: true
hidefromtoc: true
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1115'
ht-degree: 0%

---

# Migrieren einer Microsoft Windows-Plattform zu Campaign v7{#migrating-in-windows-for-adobe-campaign}



Für eine Microsoft Windows-Umgebung sind die Migrationsschritte wie folgt:

1. Beenden aller Services - [Weitere Informationen](#service-stop).
1. Datenbank sichern - [Weitere Informationen](#back-up-the-database).
1. Migrieren der Plattform - [Weitere Informationen](#deploying-adobe-campaign-v7).
1. Migrieren des Weiterleitungsservers (IIS) - [Weitere Informationen](#migrating-the-redirection-server--iis-).
1. Service neu starten - [Weitere Informationen](#re-starting-the-services).
1. Löschen und Löschen der vorherigen Adobe Campaign-Version - [Weitere Informationen](#deleting-and-cleansing-adobe-campaign-previous-version).

## Service-Stopp {#service-stop}

Beenden Sie zunächst alle Prozesse mit Zugriff auf die Datenbank auf allen betroffenen Computern.

1. Alle Server, die das Umleitungsmodul (**webmdl)-** verwenden, müssen angehalten werden. Führen Sie für IIS den folgenden Befehl aus:

   ```
   iisreset /stop
   ```

1. Das **mta**-Modul und seine untergeordneten Module (**mtachild**) müssen mit den folgenden Befehlen beendet werden:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Beenden Sie Adobe Campaign-Services auf allen Servern. Melden Sie sich mit Administratorrechten an und führen Sie den folgenden Befehl aus:

   ```
   net stop nlserver6
   ```

<!--

   If you are migrating from v5.11, run the following command:

   ```
   net stop nlserver5
   ```

-->

1. Stellen Sie für jeden Server sicher, dass die Adobe Campaign-Services ordnungsgemäß angehalten werden. Melden Sie sich mit Administratorrechten an und führen Sie den folgenden Befehl aus:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   Die Liste der aktiven Prozesse wird zusammen mit ihrer ID (PID) angezeigt.

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Wenn ein oder mehrere Adobe Campaign-Prozesse nach einigen Minuten noch aktiv oder blockiert sind, beenden Sie sie. Melden Sie sich mit Administratorrechten an und führen Sie den folgenden Befehl aus:

   ```
   taskkill /IM nlserver* /T
   ```

1. Wenn einige Prozesse nach einigen Minuten noch aktiv sind, können Sie das Schließen erzwingen, indem Sie den Befehl verwenden:

   ```
   taskkill /F /IM nlserver* /T
   ```

## Campaign-Datenbank sichern {#back-up-the-database}

Im Folgenden finden Sie das Verfahren zum Sichern von Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v5** directory using the following command:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v5.back** folder and save it elsewhere in a safe location other than the server.

1. In the windows service management console, disable the automatic startup of the 5.11 application server service. You can also use the following command:

   ```
   sc config nlserver5 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v5. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

<!--
### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v6** directory using the following command:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v6.back** folder and save it elsewhere in a safe location other than the server.

1. In the Windows service manager, deactivate the 6.02 application server automatic startup. You can also use the following command:

   ```
   sc config nlserver6 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v6. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

1. Erstellen Sie eine Sicherung der Adobe Campaign-Datenbank.
1. Erstellen Sie eine Sicherungskopie des Ordners **Adobe Campaign v6** mit dem folgenden Befehl:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir, den Ordner **Adobe Campaign v6.back** zu komprimieren und an einem anderen sicheren Speicherort als dem Server zu speichern.

1. Deaktivieren Sie in der Windows-Dienstverwaltungskonsole den automatischen Start des Anwendungsserverdiensts 6.11. Sie können auch den folgenden Befehl verwenden:

   ```
   sc config nlserver6 start= disabled
   ```

## Bereitstellen von Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Phasen:

* Installieren von Build v7: Dieser Vorgang muss auf jedem Server ausgeführt werden.
* Nach dem Upgrade: Dieser Befehl muss in jeder Instanz gestartet werden.

Gehen Sie wie folgt vor, um Adobe Campaign bereitzustellen:

1. Installieren Sie den neuesten Adobe Campaign v7-Build, indem Sie die Installationsdatei **setup.exe** ausführen. Weitere Informationen zur Installation des Adobe Campaign-Servers unter Windows finden Sie [diesem Abschnitt](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7 wird standardmäßig im Verzeichnis **C:\Program Files\Adobe\Adobe Campaign v7** installiert.

1. Um das Installationsprogramm für die Client-Konsole verfügbar zu machen, kopieren Sie die Datei **setup-client-7.0.XXXX.exe** in das Adobe Campaign-Installationsverzeichnis **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Weitere Informationen zur Installation von Adobe Campaign unter Windows finden Sie [diesem Abschnitt](../../installation/using/installing-the-server.md).

1. Starten Sie die Instanz zur ersten Verwendung mit den folgenden Befehlen:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Mit diesen Befehlen können Sie das interne Dateisystem von Adobe Campaign v7 erstellen: **conf**-Verzeichnis (mit den **config-default.xml**- und **serverConf.xml**-Dateien) **var**-Verzeichnis usw.

1. Kopieren Sie die Konfigurationsdateien und Unterordner jeder Instanz und fügen Sie sie über die Backup-Datei **Neolane v5.back**, **Neolane v6.back** oder **Adobe Campaign v6.** ein (je nach der Version, von der Sie migrieren - siehe [diesen Abschnitt](#back-up-the-database-and-the-current-installation)).
1. Führen Sie je nach Version, von der Sie migrieren, die folgenden Befehle aus:

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >Kopieren Sie für den ersten obigen Befehl nicht die Datei **config-default.xml**.

1. Wenden Sie in **serverConf.**- und **config-default.xml**-Dateien von Adobe Campaign v7 die spezifischen Konfigurationen an, die Sie in der vorherigen Version von Adobe Campaign hatten. Verwenden Sie für die Datei **serverConf** xml) die Datei **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** oder **Adobe Campaign v6/conf/serverConf.xml.diff**.

   >[!NOTE]
   >
   >Wenn Sie Konfigurationen von Adobe Campaign in einer früheren Version auf Adobe Campaign v7 melden, stellen Sie sicher, dass die Pfade zu den physischen Verzeichnissen zu Adobe Campaign v7 führen (und nicht zu Neolane v5, Neolane v6 oder Adobe Campaign v6).

1. Laden Sie die Adobe Campaign v7-Konfiguration mithilfe des folgenden Befehls neu:

   ```
   nlserver config -reload
   ```

1. Starten Sie den Prozess nach dem Upgrade mit dem folgenden Befehl:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>Starten Sie Adobe Campaign-Dienste noch nicht: Einige Änderungen müssen an IIS vorgenommen werden.

## Umleitungsserver migrieren {#migrating-the-redirection-server--iis-}

In dieser Phase muss der IIS-Server angehalten werden. Siehe [Service stoppen](#service-stop).

1. Öffnen Sie die **IIS-Manager-Konsole**.
1. Ändern Sie die Bindungen (Listen-Ports) der für die Adobe Campaign-Vorgängerversion verwendeten Site:

   * Klicken Sie mit der rechten Maustaste auf die für die vorherige Adobe Campaign-Version verwendete Site und wählen Sie **[!UICONTROL Bindungen bearbeiten]**.
   * Wählen Sie für jeden Typ von Listen-Port **[!UICONTROL http]** und/oder **[!UICONTROL https]**) die entsprechende Zeile aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
   * Einen anderen Port eingeben. Standardmäßig ist der Listen-Port 80 für http und 443 für https. Prüfen, ob der neue Anschluss verfügbar ist.

     ![](assets/_migration_iis_3_611.png)

     >[!NOTE]
     >
     >Wenden Sie sich an Ihren Administrator, wenn Ihr IIS-Server mehrere Websites für Adobe Campaign mit einer erweiterten Konfiguration (freigegebener Port und verschiedene IP-Adressen) enthält.

1. Erstellen Sie eine neue Website für Adobe Campaign v7:

   * Klicken Sie mit der rechten Maustaste auf **[!UICONTROL Sites]**-Ordner und wählen Sie **[!UICONTROL Website hinzufügen…]**.

     ![](assets/_migration_iis_4.png)

   * Geben Sie den Namen der Site ein, z. B. &lbrace;0 **Adobe Campaign v7.**
   * Der Zugriffspfad zum Basisverzeichnis der Website wird nicht verwendet, aber das Feld **[!UICONTROL Physikalischer Zugriffspfad]** muss eingegeben werden. Geben Sie den standardmäßigen IIS-Zugriffspfad ein: **C:\inetpub\wwwroot**.
   * Klicken Sie auf **[!UICONTROL Verbinden als…]** und stellen Sie sicher, dass die Option **[!UICONTROL Anwendungsbenutzer]** ausgewählt ist.
   * Sie können die Standardwerte in den Feldern **[!UICONTROL IP-Adresse]** und **[!UICONTROL Port]** beibehalten. Wenn Sie andere Werte verwenden möchten, stellen Sie sicher, dass die IP-Adresse und/oder der Port verfügbar sind.
   * Aktivieren Sie das **[!UICONTROL Website sofort starten]**.

     ![](assets/_migration_iis_5_7.png)

1. Führen Sie das Skript **iis_neolane_setup.vbs** aus, um die vom Adobe Campaign-Server verwendeten Ressourcen automatisch für das zuvor erstellte virtuelle Verzeichnis zu konfigurieren.

   * Diese Datei befindet sich im Verzeichnis **`[Adobe Campaign v7]`\conf**, wobei **`[Adobe Campaign v7]`** der Zugriffspfad zum Adobe Campaign-Installationsverzeichnis ist. Der Befehl zum Ausführen des Skripts lautet wie folgt (für Administratoren):

     ```
     cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
     cscript iis_neolane_setup.vbs
     ```

   * Klicken Sie auf **[!UICONTROL OK]**, um die Skriptausführung zu bestätigen.

     ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Geben Sie die Nummer der zuvor für Adobe Campaign v7 erstellten Website ein und klicken Sie auf **[!UICONTROL OK]**.

     ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Es sollte eine Bestätigungsmeldung angezeigt werden:

     ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * Stellen Sie auf der **[!UICONTROL Inhaltsansicht]** sicher, dass die Website-Konfiguration mit den Adobe Campaign-Ressourcen korrekt konfiguriert ist:

     ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

     >[!NOTE]
     >
     >Wenn die Baumstruktur nicht angezeigt wird, starten Sie IIS neu.
     >
     >Die folgenden IIS-Konfigurationsschritte werden in [ Abschnitt ](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

<!--
## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. [Learn more](../../migration/using/general-configurations.md#security)
-->

## Dienste neu starten {#re-starting-the-services}

Starten Sie IIS- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver
1. Mid-Sourcing-Server
1. Marketing-Server.

Bevor Sie mit dem nächsten Schritt fortfahren, führen Sie einen vollständigen Test der neuen Installation durch, stellen Sie sicher, dass es keine Regressionen gibt und dass alles funktioniert.

## Löschen der vorherigen Version {#deleting-and-cleansing-adobe-campaign-previous-version}

Im Folgenden finden Sie das Verfahren zum Löschen von Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5 {#adobe-campaign-v5}

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v5** website, then the **Neolane v5** application pool. 
1. Rename the **Neolane v5.back** folder as **Neolane v5**.
1. Uninstall Adobe Campaign v5 using the Add/remove components assistant. 

   ![](assets/migration_wizard_2.png)

1. Delete the **nlserver5** Windows service using the following command:

   ```
   sc delete nlserver5
   ```

1. Re-start the server.

### For Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Before you delete and cleanse the Adobe Campaign v6.02 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v6.02 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v6** website, then the **Neolane v6** application pool. 
1. Rename the **Neolane v6.back** folder as **Neolane v6**.
1. Uninstall Adobe Campaign v6.02 using the Add/remove components assistant. 

   ![](assets/migration_wizard_2.png)

1. Re-start the server.

-->

Bevor Sie die Adobe Campaign v6-Installation löschen und bereinigen, müssen Sie die folgenden Empfehlungen anwenden:

* Bitten Sie die Funktionsteams, eine vollständige Überprüfung der neuen Installation durchzuführen.
* Deinstallieren Sie Adobe Campaign v6 erst, wenn Sie sicher sind, dass kein Rollback erforderlich ist.

1. Löschen Sie in IIS die Website **Adobe Campaign v6** und dann den Anwendungspool **Adobe Campaign v6**.
1. Benennen Sie den Ordner **Adobe Campaign v6.back** in **Adobe Campaign v6** um.
1. Deinstallieren Sie Adobe Campaign v6 mithilfe des Komponentenassistenten.

   ![](assets/migration_wizard_2.png)

1. Starten Sie den Server neu.
