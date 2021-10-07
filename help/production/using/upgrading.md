---
product: campaign
title: Aktualisierung auf einen neuen Build
description: Technische Schritte zum Upgrade auf einen neuen Build
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 13%

---

# Aktualisierung auf einen neuen Build (On-Premise){#upgrading}

![](../../assets/v7-only.svg)

Ermitteln und bestätigen Sie vor dem Starten des Aktualisierungsprozesses, auf welche Version von Adobe Campaign aktualisiert werden soll, und lesen Sie die [Versionshinweise](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe empfiehlt dringend, vor der Aktualisierung eine Datenbanksicherung für jede Instanz durchzuführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/backup.md).
>* Um eine Aktualisierung durchzuführen, stellen Sie sicher, dass Sie über die Möglichkeit und die Berechtigung zum Zugriff auf Instanzen und Protokolle verfügen.
>* Lesen Sie [diesen Abschnitt](../../installation/using/general-architecture.md) und das Kapitel [Build-Upgrade](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html) , bevor Sie beginnen.

>


## Windows {#in-windows}

Gehen Sie in einer Windows-Umgebung wie folgt vor, um Adobe Campaign auf einen neuen Build zu aktualisieren:

* [Dienste beenden](#shut-down-services),
* [Aktualisieren Sie den Anwendungsserver](#upgrade-the-adobe-campaign-server-application),
* [Ressourcen synchronisieren](#synchronize-resources),
* [Dienste wieder starten](#restart-services).

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

   ```
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

1. Wählen Sie nach Abschluss des Vorgangs die Option **[!UICONTROL Beenden]** aus .

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

* [Laden Sie die aktualisierten Pakete](#obtain-updated-packages) herunter.
* [Führen Sie die Aktualisierung durch](#perform-an-update),
* [Starten Sie den Webserver neu](#reboot-the-web-server).

[Erfahren Sie mehr über die Client Console-Verfügbarkeit](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>Ab Build 8757 wird die Bibliothek von Drittanbietern nicht mehr benötigt.

### Aktualisierte Pakete abrufen {#obtain-updated-packages}

Beginnen Sie mit der Wiederherstellung der beiden aktualisierten Pakete von Adobe Campaign: Stellen Sie mithilfe Ihrer Benutzeranmeldeinformationen eine Verbindung zum [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) her. Weitere Informationen zur Softwareverteilung finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

Die Datei ist **nlserver6-v7-XXX.rpm**

### Aktualisieren {#perform-an-update}

* RPM-basierte Verteilung (RedHat, SuSe)

   Um sie zu installieren, führen Sie sie als Root aus:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   Dabei ist XXX die Version der Datei.

   Die rpm-Datei hat Abhängigkeiten von Paketen, die Sie in CentOS/Red Hat-Distributionen finden können. Wenn Sie einige dieser Abhängigkeiten nicht verwenden möchten, müssen Sie möglicherweise die Option &quot;nodeps&quot;von rpm verwenden:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* DEB-basierte Distribution (Debian)

   Um sie zu installieren, führen Sie sie als Root aus:

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>Die vollständigen Installationsverfahren werden in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md) beschrieben. Ressourcen werden automatisch synchronisiert. Sie müssen jedoch sicherstellen, dass keine Fehler aufgetreten sind. Weitere Informationen hierzu finden Sie unter [Beheben von Upgrade-Konflikten](#resolving-upgrade-conflicts).

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

### Anzeigen des Synchronisierungsergebnisses {#view-the-synchronization-result}

Es gibt zwei Möglichkeiten, das Synchronisierungsergebnis anzuzeigen:

* In der Befehlszeilenschnittstelle werden Fehler durch einen dreifachen Chevron **>>** materialisiert und die Synchronisation wird automatisch gestoppt. Warnungen werden durch einen doppelten Pfeil **>>** materialisiert und müssen nach Abschluss der Synchronisation behoben werden. Am Ende des Postupgrades wird an der Eingabeaufforderung eine Zusammenfassung angezeigt. Sie kann wie folgt aussehen:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Wenn ein Warnhinweis aufgrund eines Konflikts von Ressourcen ausgegeben wird, muss ihn der Benutzer lösen.

* Die Protokolldatei **postupgrade_`<server version number>_<time of postupgrade>`.log** enthält das Synchronisierungsergebnis. Sie ist standardmäßig im folgenden Verzeichnis verfügbar: **`<installation directory>/var/<instance/postupgrade`**. Fehler und Warnungen werden durch die Fehler- und Warnattribute angezeigt.

### Konflikte lösen {#resolving-conflicts}

Gehen Sie wie folgt vor, um einen Konflikt zu lösen:

1. Gehen Sie im Adobe Campaign-Navigationsbaum zu **[!UICONTROL Administration > Konfiguration > Package Management > Konflikte bearbeiten]** .
1. Wählen Sie in der Liste den Konflikt aus, den Sie lösen möchten.

Es gibt drei Möglichkeiten, einen Konflikt zu lösen:

* **[!UICONTROL Deklarieren Sie als aufgelöst]** : erfordert vorab eine Benutzerinteraktion.
* **[!UICONTROL Akzeptieren Sie die neue Version]** : empfohlen, wenn die mit Adobe Campaign bereitgestellten Ressourcen vom Benutzer nicht geändert wurden.
* **[!UICONTROL Aktuelle Version beibehalten]** : bedeutet, dass die Aktualisierung abgelehnt wird.

   >[!IMPORTANT]
   >
   >Wenn Sie diesen Auflösungsmodus auswählen, profitieren Sie möglicherweise nicht von Korrekturen in der neuen Version.

Wenn Sie den Konflikt manuell lösen möchten, gehen Sie wie folgt vor:

1. Suchen Sie im unteren Abschnitt des Fensters nach der Zeichenfolge **_conflict_** , um die Entitäten mit Konflikten zu finden. Die mit der neuen Version installierte Entität enthält das **neue**-Argument. Die Entität, die mit der vorherigen Version übereinstimmt, enthält das **cus**-Argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Löschen Sie die Version, die Sie nicht beibehalten möchten. Löschen Sie die Zeichenfolge **_conflict_argument_** der Entität, die Sie beibehalten.

   ![](assets/s_ncs_production_conflict003.png)

1. Gehen Sie zum gelösten Konflikt. Klicken Sie auf das Symbol **[!UICONTROL Aktionen]** und wählen Sie **[!UICONTROL Als gelöst deklarieren]** aus .
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

### Best Practices {#best-practices}

Ein Aktualisierungsfehler kann mit der Datenbankkonfiguration verknüpft sein. Stellen Sie sicher, dass die Konfigurationen des technischen Administrators und des Datenbankadministrators kompatibel sind.

Beispielsweise darf eine Unicode-Datenbank nicht nur die Speicherung von LATIN1-Daten usw. zulassen.

## Client-Konsolen des verfügbaren Updates warnen {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Laden Sie auf dem Computer, auf dem der Adobe Campaign-Anwendungsserver installiert ist (**nlserver web**), die Datei **setup-client-6.XXXX.exe** in den Pfad der Anwendung]/datakit/nl/eng/jsp **herunter und kopieren Sie sie.**[

Wenn die Clientkonsolen das nächste Mal verbunden werden, informiert ein Fenster die Benutzer über die Verfügbarkeit eines Updates und bietet ihnen die Möglichkeit, es herunterzuladen und zu installieren.

>[!NOTE]
>
>Stellen Sie sicher, dass der IIS_XPG-Benutzer über die entsprechenden Leseberechtigungen für diese Installationsdatei verfügt, und lesen Sie das [Installationshandbuch](../../installation/using/general-architecture.md), um weitere Informationen zu erhalten.

### Linux {#in-linux-1}

Rufen Sie auf dem Computer, auf dem der Adobe Campaign-Anwendungsserver installiert ist (**nlserver web**), das Paket **setup-client-6.XXXX.exe** ab und kopieren Sie es unter dem Namen **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Wenn die Clientkonsolen das nächste Mal verbunden werden, informiert ein Fenster die Benutzer über die Verfügbarkeit eines Updates und bietet ihnen die Möglichkeit, es herunterzuladen und zu installieren.

>[!NOTE]
>
>Stellen Sie sicher, dass der Apache-Benutzer über die entsprechenden Leseberechtigungen für diese Installationsdatei verfügt, und lesen Sie für weitere Informationen das [Installationshandbuch](../../installation/using/general-architecture.md) .
