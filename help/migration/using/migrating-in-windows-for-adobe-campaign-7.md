---
solution: Campaign Classic
product: campaign
title: Migration in Windows zu Adobe Campaign 7
description: Migration in Windows zu Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1561'
ht-degree: 1%

---


# Migration in Windows zu Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## Allgemeines Verfahren {#general-procedure}

Für Windows gelten die folgenden Migrationsschritte:

1. Dienste beenden: Siehe [Dienstunterbrechung](#service-stop).
1. Datenbank sichern: finden Sie unter Datenbank und aktuelle Installation [sichern](#back-up-the-database-and-the-current-installation).
1. Plattform migrieren: Siehe [Bereitstellen von Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Migrieren des Umleitungsservers (IIS): Siehe [Migrieren des Umleitungsservers (IIS)](#migrating-the-redirection-server--iis-).
1. Beginn-Dienst: finden Sie unter Dienste [neu starten](#re-starting-the-services).
1. Löschen und Bereinigen der vorherigen Adobe Campaign-Version: siehe [Löschen und Datenbereingung Adobe Campaign der vorherigen Version](#deleting-and-cleansing-adobe-campaign-previous-version).

## Dienstunterbrechung {#service-stop}

Beenden Sie zunächst alle Prozesse mit Zugriff auf die Datenbank auf allen betroffenen Computern.

1. Alle Server, die das Umleitungsmodul (**webmdl** -Dienst) verwenden, müssen beendet werden. Führen Sie für IIS den folgenden Befehl aus:

   ```
   iisreset /stop
   ```

1. Das **mta** -Modul und seine untergeordneten Module (**mtachild**) müssen mithilfe der folgenden Befehle beendet werden:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Beenden Sie die Adobe Campaign-Dienste auf allen Servern. Melden Sie sich mit Administratorrechten an und führen Sie den folgenden Befehl aus:

   ```
   net stop nlserver6
   ```

   Wenn Sie von Version 5.11 migrieren, führen Sie den folgenden Befehl aus:

   ```
   net stop nlserver5
   ```

1. Stellen Sie für jeden Server sicher, dass die Adobe Campaign-Dienste ordnungsgemäß beendet wurden. Melden Sie sich mit Administratorrechten an und führen Sie den folgenden Befehl aus:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   Die Liste der aktiven Prozesse zusammen mit ihrer ID (PID) wird angezeigt.

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Wenn ein oder mehrere Adobe Campaign-Prozesse nach einigen Minuten noch aktiv oder blockiert sind, beenden Sie sie. Melden Sie sich mit Administratorrechten an und führen Sie den folgenden Befehl aus:

   ```
   taskkill /IM nlserver* /T
   ```

1. Wenn einige Prozesse nach einigen Minuten noch aktiv sind, können Sie sie mithilfe des Befehls zum Schließen zwingen:

   ```
   taskkill /F /IM nlserver* /T
   ```

## Datenbank und aktuelle Installation sichern {#back-up-the-database-and-the-current-installation}

Die Vorgehensweise hängt von der vorherigen Version Ihres Adobe Campaigns ab.

### Migration von Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Erstellen Sie eine Sicherung der Adobe Campaign-Datenbank.
1. Erstellen Sie mithilfe des folgenden Befehls eine Sicherung des Ordners **Neolane v5** :

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir, den Ordner **Neolane v5.back** zu zippen und an einem anderen sicheren Speicherort als dem Server zu speichern.

1. Deaktivieren Sie in der Verwaltungskonsole des Windows-Dienstes den automatischen Start des 5.11-Anwendungsserverdiensts. Sie können auch den folgenden Befehl verwenden:

   ```
   sc config nlserver5 start= disabled
   ```

1. Bearbeiten Sie die Datei **config-`<instance name>`.xml** (in **Neolane v5). zurück** ), um zu verhindern, dass **mta**, **wfserver**, **stat** usw. Dienste automatisch starten. Ersetzen Sie beispielsweise **autoStart** durch **_autoStart**.

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

### Migration von Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Erstellen Sie eine Sicherung der Adobe Campaign-Datenbank.
1. Erstellen Sie mithilfe des folgenden Befehls eine Sicherung des Ordners **Neolane v6** :

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme empfehlen wir, den Ordner **Neolane v6.back** zu zippen und an einem anderen sicheren Speicherort als dem Server zu speichern.

1. Deaktivieren Sie im Windows-Dienstmanager den automatischen Start des Anwendungsservers 6.02. Sie können auch den folgenden Befehl verwenden:

   ```
   sc config nlserver6 start= disabled
   ```

1. Bearbeiten Sie **config-`<instance name>`.xml** (in der **Neolane v6. zurück** ), um zu verhindern, dass **mta**, **wfserver**, **stat** usw. Dienste automatisch starten. Ersetzen Sie beispielsweise **autoStart** durch **_autoStart**.

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

### Migration von Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Erstellen Sie eine Sicherung der Adobe Campaign-Datenbank.
1. Erstellen Sie mithilfe des folgenden Befehls eine Sicherung des Ordners **Adobe Campaign v6** :

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Als Vorsichtsmaßnahme sollten Sie den Ordner &quot; **Adobe Campaign v6.back** &quot;komprimieren und an einem anderen sicheren Speicherort als dem Server speichern.

1. Deaktivieren Sie in der Verwaltungskonsole des Windows-Dienstes den automatischen Start des 6.11-Anwendungsserverdiensts. Sie können auch den folgenden Befehl verwenden:

   ```
   sc config nlserver6 start= disabled
   ```

## Bereitstellen von Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Die Bereitstellung von Adobe Campaign erfolgt in zwei Schritten:

* Build v7 installieren: dieser Vorgang muss auf jedem Server ausgeführt werden.
* Nach der Aktualisierung: Dieser Befehl muss auf jeder Instanz gestartet werden.

Gehen Sie wie folgt vor, um Adobe Campaign bereitzustellen:

1. Installieren Sie den neuesten Adobe Campaign v7-Build, indem Sie die Installationsdatei **setup.exe** ausführen. Weitere Informationen zum Installieren des Adobe Campaign-Servers unter Windows finden Sie in [diesem Abschnitt](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7 wird standardmäßig im Ordner **C:\Program Files\Adobe\Adobe Campaign v7** installiert.

1. Um das Programm für die Installation der Clientkonsole verfügbar zu machen, kopieren Sie die Datei **setup-client-7.0.XXXX.exe** in den Installationsordner des Adobe Campaigns: **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Weitere Informationen zum Installieren von Adobe Campaign unter Windows finden Sie in [diesem Abschnitt](../../installation/using/installing-the-server.md).

1. Beginn der Instanz für die erste Verwendung mit den folgenden Befehlen:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Mit diesen Befehlen können Sie das interne Dateisystem des Adobe Campaigns v7 erstellen: **conf** -Ordner (mit den Dateien **config-default.xml** und **serverConf.xml** ), **var** usw.

1. Kopieren Sie die Konfigurationsdateien und Unterordner jeder Instanz und fügen Sie sie über die Sicherungsdatei **Neolane v5.back**, **Neolane v6.back** oder **Adobe Campaign v6.back** ein (je nach der Version, von der Sie migrieren - siehe [diesen Abschnitt](#back-up-the-database-and-the-current-installation)).
1. Führen Sie entsprechend der Version, von der Sie migrieren, die folgenden Befehle aus:

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
   >Kopieren Sie für den ersten oben stehenden Befehl nicht die Datei &quot; **config-default.xml** &quot;.

1. Wenden Sie in den **Dateien &quot;serverConf.xml** &quot;und &quot; **config-default.xml** &quot;von Adobe Campaign v7 die spezifischen Konfigurationen an, die Sie in der vorherigen Adobe Campaign-Version hatten. Verwenden Sie für die Datei &quot; **serverConf.xml** &quot;die **Datei &quot;v5/conf/serverConf.xml.diff**&quot;, &quot; **Neolane v6/conf/serverConf.xml.diff** &quot;oder das **Adobe Campaign &quot;v6/conf/serverConf.xml.diff** &quot;.

   >[!NOTE]
   >
   >Stellen Sie beim Erstellen von Berichte-Konfigurationen von Adobe Campaign-Version zu Adobe Campaign v7 sicher, dass die Pfade zu den physischen Ordnern zu Adobe Campaign v7 führen (und nicht zu Neolane v5, Neolane v6 oder Adobe Campaign v6).

1. Laden Sie die Adobe Campaign v7-Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

1. Beginn des Nachbearbeitungsprozesses mit dem folgenden Befehl:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>Beginn-Adobe Campaign-Dienste noch nicht: einige Änderungen an IIS vorgenommen werden müssen.

## Migrieren des Umleitungsservers (IIS) {#migrating-the-redirection-server--iis-}

In diesem Stadium muss der IIS-Server beendet werden. Siehe [Dienstunterbrechung](#service-stop).

1. Öffnen Sie die **Internet Informationsdiensts (IIS) Manager** -Konsole.
1. Ändern Sie die Bindungen (Listen-Ports) der Site, die für die Adobe Campaign-ältere Version verwendet wird:

   * Klicken Sie mit der rechten Maustaste auf die Site, die für die vorherige Adobe Campaign-Version verwendet wurde, und wählen Sie &quot;Bindungen **[!UICONTROL bearbeiten&quot;]**.
   * Wählen Sie für jeden Listener-Port-Typ (**[!UICONTROL http]** und/oder **[!UICONTROL https]**) die entsprechende Zeile aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
   * Geben Sie einen anderen Anschluss ein. Standardmäßig ist der Überwachungsanschluss für HTTP 80 und für HTTPS 443. Überprüfen Sie, ob der neue Anschluss verfügbar ist.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >Wenn Ihr IIS-Server mehrere Websites zum Adobe Campaign mit einer erweiterten Konfiguration (freigegebener Port und verschiedene IP-Adressen) enthält, wenden Sie sich bitte an Ihren Administrator.

1. Neue Website für Adobe Campaign v7 erstellen:

   * Klicken Sie mit der rechten Maustaste auf den Ordner **[!UICONTROL Sites]** und wählen Sie **[!UICONTROL Hinzufügen Website...]**.

      ![](assets/_migration_iis_4.png)

   * Geben Sie den Namen der Site ein, z. B. **Adobe Campaign v7** .
   * Der Zugriffspfad zum Basisverzeichnis der Website wird nicht verwendet, aber das Feld **[!UICONTROL Physikalischer Zugriffspfad]** muss eingegeben werden. Geben Sie den standardmäßigen IIS-Zugriffspfad ein: **C:\inetpub\wwwroot**.
   * Klicken Sie auf **[!UICONTROL Verbinden als...]** als angezeigt wird, und stellen Sie sicher, dass die Option **[!UICONTROL Anwendungsbenutzer]** ausgewählt ist.
   * Sie können die Standardwerte in den Feldern **[!UICONTROL IP-Adresse]** und **[!UICONTROL Anschluss]** belassen. Wenn Sie andere Werte verwenden möchten, stellen Sie sicher, dass die IP-Adresse und/oder der Anschluss verfügbar sind.
   * Markieren Sie das **[!UICONTROL Kästchen Beginn Website sofort]** .

      ![](assets/_migration_iis_5_7.png)

1. Führen Sie das Skript **is_neolane_setup.vbs** aus, um die vom Adobe Campaign-Server für den zuvor erstellten virtuellen Ordner verwendeten Ressourcen automatisch zu konfigurieren.

   * Diese Datei befindet sich im Ordner **`[Adobe Campaign v7]`\conf** , wo **`[Adobe Campaign v7]`** sich der Zugriffspfad zum Installationsordner des Adobe Campaigns befindet. Der Befehl zum Ausführen des Skripts lautet wie folgt (für Administratoren):

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
      cscript iis_neolane_setup.vbs
      ```

   * Klicken Sie auf **[!UICONTROL OK]** , um die Skriptausführung zu bestätigen.

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Geben Sie die Nummer der Website ein, die zuvor für Adobe Campaign v7 erstellt wurde, und klicken Sie auf **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Es sollte eine Bestätigungsmeldung angezeigt werden:

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * Vergewissern Sie sich auf der Registerkarte **[!UICONTROL Content Ansicht]** , dass die Websitekonfiguration korrekt mit Adobe Campaign-Ressourcen konfiguriert ist:

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >Wenn die Baumstruktur nicht angezeigt wird, führen Sie einen erneuten Beginn des IIS durch.
      >
      >Die folgenden IIS-Konfigurationsschritte werden in [diesem Abschnitt](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server)beschrieben.

## Sicherheitszonen {#security-zones}

Wenn Sie eine Migration von Version 6.02 oder früher durchführen, müssen Sie Ihre Sicherheitszonen konfigurieren, bevor Sie Dienste starten. Weitere Informationen finden Sie unter [Sicherheit](../../migration/using/general-configurations.md#security).

## Neustarten der Dienste {#re-starting-the-services}

Beginn IIS- und Adobe Campaign-Dienste auf jedem der folgenden Server:

1. Tracking- und Weiterleitungsserver.
1. Mid-Sourcing-Server.
1. Marketing-Server.

Bevor Sie mit dem nächsten Schritt fortfahren, führen Sie einen vollständigen Test der neuen Installation durch, stellen Sie sicher, dass es keine Regressionen gibt und dass alles funktioniert, indem Sie alle Empfehlungen im Abschnitt [Allgemeine Konfigurationen](../../migration/using/general-configurations.md) befolgen.

## Löschen und Datenbereingung Adobe Campaign der vorherigen Version {#deleting-and-cleansing-adobe-campaign-previous-version}

Die Vorgehensweise hängt von der vorherigen Version Ihres Adobe Campaigns ab.

### Adobe Campaign v5 {#adobe-campaign-v5}

Bevor Sie die Adobe Campaign v5-Installation löschen und bereinigen, müssen Sie die folgenden Empfehlungen anwenden:

* Besorgen Sie sich die Funktionsteams, um eine vollständige Prüfung der neuen Installation durchzuführen.
* Deinstallieren Sie Adobe Campaign v5 nur, wenn Sie sicher sind, dass kein Rollback erforderlich ist.

1. Löschen Sie in IIS die **Neolane v5** -Website und dann den **Neolane v5** -Anwendungspool.
1. Benennen Sie den Ordner **Neolane v5.back** in **Neolane v5** um.
1. Deinstallieren Sie Adobe Campaign v5 mithilfe des Assistenten zum Hinzufügen/Entfernen von Komponenten.

   ![](assets/migration_wizard_2.png)

1. Löschen Sie den **nlserver5** Windows-Dienst mit dem folgenden Befehl:

   ```
   sc delete nlserver5
   ```

1. Beginn Sie den Server erneut an.

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Bevor Sie die Adobe Campaign v6.02-Installation löschen und bereinigen, müssen Sie die folgenden Empfehlungen anwenden:

* Besorgen Sie sich die Funktionsteams, um eine vollständige Prüfung der neuen Installation durchzuführen.
* Deinstallieren Sie Adobe Campaign v6.02 nur, wenn Sie sicher sind, dass kein Rollback erforderlich ist.

1. Löschen Sie in IIS die **Neolane v6** -Website und dann den **Neolane v6** -Anwendungspool.
1. Benennen Sie den Ordner **Neolane v6.back** in **Neolane v6** um.
1. Deinstallieren Sie Adobe Campaign v6.02 mithilfe des Assistenten zum Hinzufügen/Entfernen von Komponenten.

   ![](assets/migration_wizard_2.png)

1. Beginn Sie den Server erneut an.

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

Bevor Sie die Adobe Campaign v6-Installation löschen und bereinigen, müssen Sie die folgenden Empfehlungen anwenden:

* Besorgen Sie sich die Funktionsteams, um eine vollständige Prüfung der neuen Installation durchzuführen.
* Deinstallieren Sie Adobe Campaign v6 nur, wenn Sie sicher sind, dass kein Rollback erforderlich ist.

1. Löschen Sie in IIS die **Adobe Campaign v6** -Website und dann den **Adobe Campaign v6** -Anwendungspool.
1. Benennen Sie den Ordner &quot; **Adobe Campaign v6.back** &quot;in **Adobe Campaign v6** um.
1. Deinstallieren Sie Adobe Campaign v6 mithilfe des Assistenten zum Hinzufügen/Entfernen von Komponenten.

   ![](assets/migration_wizard_2.png)

1. Beginn Sie den Server erneut an.

