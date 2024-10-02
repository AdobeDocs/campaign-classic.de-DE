---
product: campaign
title: Aktualisierung auf einen neuen Build
description: Technische Schritte zum Upgrade auf einen neuen Build
feature: Monitoring, Upgrade
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: cc614ed608f1e8229c0ef1ccf35dbac6cb9dddd3
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 7%

---

# Aktualisierung auf einen neuen Build (On-Premise){#upgrading}

Ermitteln und bestätigen Sie vor Beginn des Aktualisierungsprozesses, auf welche Version von Adobe Campaign aktualisiert werden soll, und lesen Sie die [Versionshinweise](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe empfiehlt dringend, vor der Aktualisierung eine Datenbanksicherung für jede Instanz durchzuführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/backup.md).
>* Um eine Aktualisierung durchzuführen, stellen Sie sicher, dass Sie über die Möglichkeit und die Berechtigung zum Zugriff auf Instanzen und Protokolle verfügen.
>* Lesen Sie [diesen Abschnitt](../../installation/using/general-architecture.md) und das Kapitel [Build-Aktualisierung](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html) , bevor Sie beginnen.
>

## Windows {#in-windows}

Gehen Sie in einer Windows-Umgebung wie folgt vor, um Adobe Campaign auf einen neuen Build zu aktualisieren:

* [Herunterfahren von Diensten](#shut-down-services),
* [ Aktualisierung des Anwendungsservers](#upgrade-the-adobe-campaign-server-application),
* [Ressourcen synchronisieren](#synchronize-resources),
* [Starten Sie die Dienste neu.](#restart-services)

Informationen zum Aktualisieren der Clientkonsole finden Sie in [diesem Abschnitt](../../installation/using/client-console-availability-for-windows.md).

### Dienste beenden {#shut-down-services}

Um alle Dateien durch die neue Version zu ersetzen, müssen Sie alle Instanzen des nlserver-Dienstes herunterfahren.

1. Beenden Sie die folgenden Dienste:

   * Webdienste (IIS):

     **iisreset /stop**

   * Adobe-Campaign-Dienst: **net stop nlserver6**

   >[!IMPORTANT]
   >
   >Außerdem müssen Sie sicherstellen, dass der Weiterleitungsserver (webmdl) angehalten wird, damit die von IIS verwendete Datei **nlsrvmod.dll** durch die neue Version ersetzt werden kann.

1. Vergewissern Sie sich, dass keine Aufgaben aktiv sind, indem Sie den Befehl **nlserver pdump** ausführen. Folgendes sollte angezeigt werden:

   ```sql
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Sie können den Windows Task Manager verwenden, um sicherzustellen, dass alle Prozesse angehalten werden.

### Aktualisieren Sie die Adobe-Campaign-Server-Anwendung. {#upgrade-the-adobe-campaign-server-application}

Gehen Sie wie folgt vor, um die Aktualisierungsdatei auszuführen:

1. Führen Sie **setup.exe** aus.

   Um diese Datei herunterzuladen, stellen Sie mithilfe Ihrer Benutzeranmeldeinformationen eine Verbindung zum [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her. Weitere Informationen zur Softwareverteilung finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).

1. Wählen Sie den Installationsmodus aus: Wählen Sie **[!UICONTROL Aktualisieren oder Reparieren]**
1. Klicken Sie auf **[!UICONTROL Weiter]** .
1. Klicken Sie auf **[!UICONTROL Beenden]** .

   Das Installationsprogramm kopiert dann die neuen Dateien.

1. Klicken Sie nach Abschluss des Vorgangs auf **[!UICONTROL Beenden]** .

### Ressourcen synchronisieren {#synchronize-resources}

Verwenden Sie die folgende Befehlszeile:

**nlserver config -postupgrade -allinstances**

Auf diese Weise können Sie die folgenden Vorgänge ausführen:

* Ressourcen synchronisieren
* Schemata aktualisieren
* Datenbank aktualisieren

>[!NOTE]
>
>Dieser Vorgang sollte nur einmal und nur auf einem Anwendungsserver (**nlserver web**) ausgeführt werden.

Überprüfen Sie dann, ob die Synchronisation Fehler oder Warnungen erzeugt hat. Weitere Informationen hierzu finden Sie unter [Beheben von Upgrade-Konflikten](#resolving-upgrade-conflicts).

### Dienste wieder starten {#restart-services}

Folgende Dienste sollen neu gestartet werden:

* Webdienste (IIS):

  **iisreset /start**

* Adobe-Campaign-Dienst: **net start nlserver6**

## Linux {#in-linux}

Gehen Sie in einer Linux-Umgebung wie folgt vor, um Adobe Campaign auf einen neuen Build zu aktualisieren:

* [Laden Sie die aktualisierten Pakete herunter](#obtain-updated-packages),
* [Führen Sie die Aktualisierung durch](#perform-an-update),
* [Starten Sie den Webserver neu.](#reboot-the-web-server)

[Erfahren Sie mehr über die Client Console-Verfügbarkeit](../../installation/using/client-console-availability-for-windows.md).

### Aktualisierte Pakete installieren {#obtain-updated-packages}

Rufen Sie zunächst beide aktualisierten Pakete von Adobe Campaign ab: Stellen Sie mithilfe Ihrer Benutzeranmeldeinformationen eine Verbindung zum [Software-Verteilungsportal](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her. Weitere Informationen zur Softwareverteilung finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).

Die Datei ist **nlserver6-v7-XXX.rpm**

>[!AVAILABILITY]
>
>Ab Version 7.4.1 sind XML-Bibliotheken für RPM Linux-Pakete nicht mehr in Campaign enthalten. Sie müssen diese Bibliotheken installieren.
> 

Anschließend können Sie die erforderlichen Pakete installieren, wie unten beschrieben:

* RPM-basierte Verteilung (RedHat, SuSe)

  Um sie zu installieren, führen Sie sie als Root aus:

  ```
  yum install ./nlserver6-v7-XXXX.rpm
  ```

  Dabei ist XXX die Version der Datei.

  Die rpm-Datei hat Abhängigkeiten von Paketen, die Sie in CentOS/Red Hat-Distributionen finden können. Wenn Sie einige dieser Abhängigkeiten nicht verwenden möchten, müssen Sie möglicherweise die Option &quot;nodeps&quot;von rpm verwenden:

  ```
  rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
  ```

  Beachten Sie, dass die meisten Abhängigkeiten obligatorisch sind und `nlserver` nicht starten kann, wenn nicht installiert ist. Die einzige Ausnahme ist openjdk. Sie können bei Bedarf ein anderes JDK installieren.

  Wenn das Paket `epel-release` nicht installiert ist, installieren Sie es. Geben Sie dazu den folgenden Befehl als Root ein:

  ```
  yum install epel-release
  ```

  Um das Campaign-Package zu installieren, führen Sie es als root aus:

  ```
  yum update ./nlserver6-v7-XXXX.rpm
  ```

  Bevor Sie die Aktualisierung bestätigen, stellen Sie sicher, dass die Ausgabe wie folgt aussieht:

  ```
  ==================================================================================================== 
  Package                         Architecture  Version                    Repository           Size 
  ==================================================================================================== 
  Upgrading: 
  nlserver6-v7                    x86_64        XXXX.0.0-1                 @commandline         63 M
  ```

  >[!IMPORTANT]
  >
  >Wenn Sie `Removing:` anstelle von `Upgrading:` lesen, brechen Sie den Befehl ab. Es gibt wahrscheinlich einige Fehler (siehe oben), die die Entfernung erklären. Korrigieren Sie in diesem Fall diese Fehler, indem Sie die aufgelisteten fehlenden Abhängigkeiten aktualisieren/installieren und versuchen Sie dann erneut, den Befehl auszuführen.

* DEB-basierte Distribution (Debian)

  Um sie zu installieren, führen Sie sie als Root aus:

  ```
  apt install ./nlserver6-v7-XXXX-amd64_debX.deb
  ```

>[!NOTE]
>
>Die vollständigen Installationsverfahren werden in [diesem Abschnitt](../../installation/using/installing-packages-with-linux.md) beschrieben. Ressourcen werden automatisch synchronisiert. Sie müssen jedoch sicherstellen, dass keine Fehler aufgetreten sind. Weitere Informationen hierzu finden Sie unter [Beheben von Aktualisierungskonflikten](#resolving-upgrade-conflicts).
>

### Webserver neu starten {#reboot-the-web-server}

Sie müssen Apache herunterfahren, damit die neue Bibliothek angewendet wird.

Führen Sie dazu den folgenden Befehl aus:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Ihr Skript könnte **httpd** anstelle von **apache** heißen.
>* Sie MÜSSEN diesen Befehl ausführen, bis Sie die folgende Antwort erhalten:
>
>   Dieser Vorgang ist erforderlich, damit Apache die neue Bibliothek anwendet.

Starten Sie dann Apache neu:

```
/etc/init.d/apache start
```

## Beheben von Aktualisierungskonflikten {#resolving-upgrade-conflicts}

Bei der Synchronisation von Ressourcen können Sie mit dem Befehl **postupgrade** erkennen, ob bei der Synchronisierung Fehler oder Warnungen aufgetreten sind.

### Synchronisierungsergebnis anzeigen {#view-the-synchronization-result}

Es gibt zwei Möglichkeiten, das Synchronisierungsergebnis anzuzeigen:

* In der Befehlszeilenschnittstelle werden Fehler durch einen dreifachen Chevron **>>** materialisiert und die Synchronisation wird automatisch angehalten. Warnungen werden durch einen doppelten Chevron **>>** materialisiert und müssen nach Abschluss der Synchronisation aufgelöst werden. Am Ende des Postupgrades wird an der Eingabeaufforderung eine Zusammenfassung angezeigt. Sie kann wie folgt aussehen:

  ```
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Wenn die Warnung einen Ressourcenkonflikt betrifft, muss der Benutzer darauf achten, ihn zu beheben.

* Die Protokolldatei **postupgrade_`<server version number>_<time of postupgrade>`.log** enthält das Synchronisierungsergebnis. Sie ist standardmäßig im folgenden Verzeichnis verfügbar: **`<installation directory>/var/<instance/postupgrade`**. Fehler und Warnungen werden durch die Fehler- und Warnattribute angezeigt.

### Konflikte lösen {#resolving-conflicts}

Gehen Sie wie folgt vor, um einen Konflikt zu lösen:

1. Wechseln Sie im Adobe Campaign-Baum zu **[!UICONTROL Administration > Konfiguration > Package-Management > Konflikte bearbeiten]** .
1. Wählen Sie in der Liste den Konflikt aus, den Sie lösen möchten.

Es gibt drei Möglichkeiten, einen Konflikt zu lösen:

* **[!UICONTROL Als aufgelöst deklarieren]** : erfordert vorab ein Eingreifen des Benutzers.
* **[!UICONTROL Neue Version akzeptieren]** : Wird empfohlen, wenn die mit Adobe Campaign bereitgestellten Ressourcen vom Benutzer nicht geändert wurden.
* **[!UICONTROL Aktuelle Version beibehalten]** : bedeutet, dass die Aktualisierung abgelehnt wird.

  >[!IMPORTANT]
  >
  >Wenn Sie diesen Auflösungsmodus auswählen, profitieren Sie möglicherweise nicht von Korrekturen in der neuen Version.

Wenn Sie den Konflikt manuell lösen möchten, gehen Sie wie folgt vor:

1. Suchen Sie im unteren Abschnitt des Fensters nach der Zeichenfolge **_conflict_** , um die Entitäten mit Konflikten zu finden. Die mit der neuen Version installierte Entität enthält das **new** -Argument. Die Entität, die mit der vorherigen Version übereinstimmt, enthält das **cus** -Argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Löschen Sie die Version, die Sie nicht beibehalten möchten. Löschen Sie die Zeichenfolge **_conflict_argument_** der Entität, die Sie beibehalten.

   ![](assets/s_ncs_production_conflict003.png)

1. Gehen Sie zu dem Konflikt, den Sie gelöst haben. Klicken Sie auf das Symbol **[!UICONTROL Aktionen]** und wählen Sie **[!UICONTROL Als aufgelöst erklären]** aus.
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

### Best Practices {#best-practices}

Ein Aktualisierungsfehler kann mit der Datenbankkonfiguration verknüpft sein. Stellen Sie sicher, dass die Konfigurationen des technischen Administrators und des Datenbankadministrators kompatibel sind.

Beispielsweise darf eine Unicode-Datenbank nicht nur die Speicherung von LATIN1-Daten usw. zulassen.

## Client-Konsolen des verfügbaren Updates warnen {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Laden Sie auf dem Computer, auf dem der Adobe Campaign-Anwendungsserver installiert ist (**nlserver web**), die Datei &quot;**setup-client-6.XXXX.exe**&quot;in den Pfad &quot;**[path of the application]/datakit/nl/eng/jsp**&quot; herunter und kopieren Sie sie.

Wenn die Clientkonsolen das nächste Mal verbunden werden, informiert ein Fenster die Benutzer über die Verfügbarkeit eines Updates und bietet ihnen die Möglichkeit, es herunterzuladen und zu installieren.

>[!NOTE]
>
>Stellen Sie sicher, dass der IIS_XPG-Benutzer über die entsprechenden Leseberechtigungen für diese Installationsdatei verfügt, und lesen Sie das [Installationshandbuch](../../installation/using/general-architecture.md) , um weitere Informationen zu erhalten.

### Linux {#in-linux-1}

Rufen Sie auf dem Computer, auf dem der Adobe Campaign-Anwendungsserver installiert ist (**nlserver web**), das Paket **setup-client-6.XXXX.exe** ab und kopieren Sie es unter dem Namen **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Wenn die Clientkonsolen das nächste Mal verbunden werden, informiert ein Fenster die Benutzer über die Verfügbarkeit eines Updates und bietet ihnen die Möglichkeit, es herunterzuladen und zu installieren.

>[!NOTE]
>
>Stellen Sie sicher, dass der Apache-Benutzer über die entsprechenden Leseberechtigungen für diese Installationsdatei verfügt, und lesen Sie das [Installationshandbuch](../../installation/using/general-architecture.md) , um weitere Informationen zu erhalten.
