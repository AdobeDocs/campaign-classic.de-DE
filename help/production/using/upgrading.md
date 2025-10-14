---
product: campaign
title: Aktualisieren auf einen neuen Build
description: Erfahren Sie mehr über die technischen Schritte beim Upgrade auf einen neuen Build
feature: Monitoring, Upgrade
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 0da7fb912a909af222d796652efba4b30e39dc1c
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 8%

---

# Aktualisieren auf einen neuen Build (On-Premise){#upgrading}

Bevor Sie mit dem Upgrade-Prozess beginnen, stellen Sie fest, welche Version von Adobe Campaign auf aktualisiert werden soll, und lesen Sie die [Versionshinweise](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe empfiehlt dringend, vor der Aktualisierung eine Datenbanksicherung für jede Instanz durchzuführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../production/using/backup.md).
>* Um ein Upgrade durchzuführen, stellen Sie sicher, dass Sie über die Fähigkeit und die Berechtigungen zum Zugriff auf Instanzen und Protokolle verfügen.
>* Lesen Sie [&#x200B; Abschnitt und &#x200B;](../../installation/using/general-architecture.md) Kapitel [Build-Upgrade](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html), bevor Sie beginnen.
>

## Windows {#in-windows}

Gehen Sie in einer Windows-Umgebung wie folgt vor, um Adobe Campaign auf einen neuen Build zu aktualisieren:

* [Dienste beenden](#shut-down-services),
* [Aktualisieren des Anwendungsservers](#upgrade-the-adobe-campaign-server-application),
* [Ressourcen synchronisieren](#synchronize-resources),
* [Dienste neu &#x200B;](#restart-services).

Informationen zum Aktualisieren der Client-Konsole finden Sie in [diesem Abschnitt](../../installation/using/client-console-availability-for-windows.md).

### Dienste beenden {#shut-down-services}

Um alle Dateien durch die neue Version zu ersetzen, müssen Sie alle Instanzen des nlserver-Dienstes herunterfahren.

1. Beenden Sie die folgenden Dienste:

   * Webdienste (IIS):

     **iisreset/stop**

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

   Sie können den Windows Task-Manager verwenden, um sicherzustellen, dass alle Prozesse angehalten werden.

### Aktualisieren Sie die Adobe-Campaign-Server-Anwendung. {#upgrade-the-adobe-campaign-server-application}

Gehen Sie wie folgt vor, um die Aktualisierungsdatei auszuführen:

1. Führen Sie **setup.exe** aus.

   Um diese Datei herunterzuladen, verbinden Sie sich mit dem [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) mit Ihren Benutzeranmeldeinformationen. Weitere Informationen zur Software-Verteilung finden [&#x200B; auf dieser Seite &#x200B;](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).

1. Installationsmodus auswählen: Wählen Sie **[!UICONTROL Aktualisieren oder reparieren]**
1. Klicken Sie **[!UICONTROL Weiter]** .
1. Klicken Sie **[!UICONTROL Beenden]** .

   Das Installationsprogramm kopiert dann die neuen Dateien.

1. Nachdem der Vorgang abgeschlossen ist, klicken Sie auf **[!UICONTROL Beenden]** .

### Ressourcen synchronisieren {#synchronize-resources}

Verwenden Sie die folgende Befehlszeile:

**nlserver config -postupgrade -allInstances**

Auf diese Weise können Sie die folgenden Vorgänge ausführen:

* Ressourcen synchronisieren
* Schemata aktualisieren
* Datenbank aktualisieren

>[!NOTE]
>
>Dieser Vorgang sollte nur einmal und nur auf einem Anwendungs-Server (**nlserver web**) ausgeführt werden.

Überprüfen Sie dann, ob die Synchronisierung Fehler oder Warnungen erzeugt hat. Weitere Informationen hierzu finden Sie unter [&#x200B; von Upgrade-Konflikten](#resolving-upgrade-conflicts).

### Dienste wieder starten {#restart-services}

Die neu zu startenden Dienste sind:

* Webdienste (IIS):

  **iisreset/start**

* Adobe-Campaign-Dienst: **net start nlserver6**

## Linux {#in-linux}

Gehen Sie in einer Linux-Umgebung wie folgt vor, um Adobe Campaign auf einen neuen Build zu aktualisieren:

* [Herunterladen der aktualisierten Pakete](#obtain-updated-packages),
* [Aktualisierung durchführen](#perform-an-update),
* [Starten Sie den Webserver neu](#reboot-the-web-server).

[Weitere Informationen zur Verfügbarkeit der Client-Konsole](../../installation/using/client-console-availability-for-windows.md).

### Installieren aktualisierter Pakete {#obtain-updated-packages}

Stellen Sie zunächst die beiden aktualisierten Adobe Campaign-Pakete wieder her: Stellen Sie mithilfe Ihrer Benutzeranmeldeinformationen eine Verbindung [Software Distribution-](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) her. Weitere Informationen zur Software-Verteilung finden [&#x200B; auf dieser Seite &#x200B;](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de).

Die Datei lautet **nlserver6-v7-XXX.rpm**

>[!AVAILABILITY]
>
>Ab Version 7.4.1 sind XML-Bibliotheken für RPM Linux-Pakete nicht mehr in Campaign enthalten. Sie müssen diese Bibliotheken installieren.
> 

Anschließend können Sie die erforderlichen Pakete wie unten beschrieben installieren:

* RPM-basierte Verteilung (RedHat, SuSE)

  Wenn das `epel-release` nicht installiert ist, installieren Sie es. Geben Sie dazu den folgenden Befehl als root ein:

  ```
  yum install epel-release
  ```

  Um das Campaign-Paket zu installieren, führen Sie als Stammordner aus:

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
  >Wenn Sie `Removing:` anstelle von `Upgrading:` lesen, brechen Sie den Befehl ab. Wahrscheinlich gibt es einige Fehler (siehe oben), die die Entfernung erklären. Korrigieren Sie in diesem Fall diese Fehler, indem Sie die aufgelisteten fehlenden Abhängigkeiten aktualisieren/installieren und dann erneut versuchen, den Befehl auszuführen.

  Die rpm-Datei weist Abhängigkeiten von Paketen auf, die Sie in CentOS/Red Hat-Distributionen finden können. Wenn Sie einige dieser Abhängigkeiten nicht verwenden möchten, müssen Sie möglicherweise die Option „nodeps“ von rpm verwenden:

  ```
  rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
  ```

  Beachten Sie, dass die meisten Abhängigkeiten obligatorisch sind und `nlserver` nicht gestartet werden können, wenn sie nicht installiert sind. Die einzige Ausnahme ist OpenJDK. Sie können bei Bedarf ein anderes JDK installieren.

* DEB-basierte Distribution (Debian)

  Um sie zu installieren, führen Sie als root aus:

  ```
  apt install ./nlserver6-v7-XXXX-amd64_debX.deb
  ```

>[!NOTE]
>
>Die vollständigen Installationsverfahren werden in [diesem Abschnitt) &#x200B;](../../installation/using/installing-packages-with-linux.md). Ressourcen werden automatisch synchronisiert. Sie müssen jedoch sicherstellen, dass keine Fehler aufgetreten sind. Weitere Informationen hierzu finden Sie unter [Beheben von Upgrade-Konflikten](#resolving-upgrade-conflicts).
>

### Neustarten des Webservers {#reboot-the-web-server}

Sie müssen Apache beenden, damit die neue Bibliothek angewendet wird.

Führen Sie dazu den folgenden Befehl aus:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Ihr Skript heißt möglicherweise **httpd** anstelle von **apache**.
>* Sie MÜSSEN diesen Befehl ausführen, bis Sie die folgende Antwort erhalten:
>
>   `This operation is required in order for Apache to apply the new library.`

Starten Sie dann Apache neu:

```
/etc/init.d/apache start
```

## Upgrade-Konflikte lösen {#resolving-upgrade-conflicts}

Während der Ressourcensynchronisierung können Sie mit dem **postupgrade**-Befehl erkennen, ob die Synchronisierung Fehler oder Warnungen erzeugt hat.

### Anzeigen des Synchronisierungsergebnisses {#view-the-synchronization-result}

Es gibt zwei Möglichkeiten, das Synchronisierungsergebnis anzuzeigen:

* In der Befehlszeilenschnittstelle werden Fehler durch einen dreifachen Pfeil **>>** materialisiert und die Synchronisierung wird automatisch angehalten. Warnungen werden durch einen doppelten Pfeil **>>** materialisiert und müssen nach Abschluss der Synchronisierung aufgelöst werden. Am Ende des Postupgrades wird in der Eingabeaufforderung eine Zusammenfassung angezeigt. Er kann wie folgt aussehen:

  ```
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Wenn die Warnung einen Ressourcenkonflikt betrifft, ist ein Eingreifen des Benutzers erforderlich, um ihn zu lösen.

* Die Protokolldatei **postupgrade_`<server version number>_<time of postupgrade>`.**&quot; enthält das Synchronisierungsergebnis. Sie ist standardmäßig im folgenden Verzeichnis verfügbar: **`<installation directory>/var/<instance/postupgrade`**. Fehler und Warnungen werden durch die Attribute error und warning gekennzeichnet.

### Konflikte lösen {#resolving-conflicts}

Gehen Sie wie folgt vor, um einen Konflikt zu lösen:

1. Gehen Sie in der Adobe Campaign-Struktur zu **[!UICONTROL Administration > Konfiguration > Paketverwaltung > Konflikte bearbeiten]** .
1. Wählen Sie in der Liste den Konflikt aus, den Sie lösen möchten.

Es gibt drei Möglichkeiten, einen Konflikt zu lösen:

* **[!UICONTROL Als aufgelöst deklarieren]** : Erfordert vorab das Eingreifen des Benutzers.
* **[!UICONTROL Neue Version akzeptieren]** : Wird empfohlen, wenn die mit Adobe Campaign bereitgestellten Ressourcen von den Benutzenden nicht geändert wurden.
* **[!UICONTROL Aktuelle Version beibehalten]** : bedeutet, dass die Aktualisierung abgelehnt wird.

  >[!IMPORTANT]
  >
  >Wenn Sie diesen Auflösungsmodus auswählen, profitieren Sie möglicherweise nicht von Korrekturen in der neuen Version.

Wenn Sie den Konflikt manuell lösen möchten, gehen Sie wie folgt vor:

1. Suchen Sie im unteren Bereich des Fensters nach der Zeichenfolge **_Konflikt_**, um die Entitäten mit Konflikten zu finden. Die mit der neuen Version installierte Entität enthält das **new**-Argument. Die Entität, die mit der vorherigen Version übereinstimmt, enthält das **cus**-Argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Löschen Sie die Version, die Sie nicht behalten möchten. Löschen Sie die **_CONFLICT_ARGUMENT_**-Zeichenfolge der Entität, die Sie beibehalten.

   ![](assets/s_ncs_production_conflict003.png)

1. Navigieren Sie zu dem Konflikt, den Sie gelöst haben. Klicken Sie auf **[!UICONTROL Aktionen]** und wählen Sie **[!UICONTROL Als aufgelöst deklarieren]** aus.
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

### Best Practices {#best-practices}

Möglicherweise liegt ein Aktualisierungsfehler in der Datenbankkonfiguration vor. Stellen Sie sicher, dass die vom technischen Administrator und vom Datenbankadministrator durchgeführten Konfigurationen kompatibel sind.

Beispielsweise darf eine Unicode-Datenbank nicht nur die Speicherung von LATIN1-Daten usw. zulassen.

## Client-Konsolen über das verfügbare Update warnen {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Laden Sie auf dem Computer, auf dem der Adobe Campaign-Anwendungsserver installiert ist (**nlserver web**), die Datei **setup-client-6.XXXX.exe** in **[Pfad der Anwendung]/datakit/nl/eng/jsp** herunter und kopieren Sie sie.

Wenn die Client-Konsolen das nächste Mal verbunden werden, informiert ein Fenster den Benutzer über die Verfügbarkeit eines Updates und bietet ihm die Möglichkeit, es herunterzuladen und zu installieren.

>[!NOTE]
>
>Stellen Sie sicher, dass der IIS_XPG-Benutzer über die entsprechenden Leseberechtigungen für diese Installationsdatei verfügt, und lesen Sie das [Installationshandbuch](../../installation/using/general-architecture.md), um weitere Informationen zu erhalten.

### Linux {#in-linux-1}

Rufen Sie auf dem Computer, auf dem der Adobe Campaign-Anwendungsserver (**nlserver web**) installiert ist, das Paket **setup-client-6.XXXX.exe** ab und kopieren Sie es unter dem Namen **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Wenn die Client-Konsolen das nächste Mal verbunden werden, informiert ein Fenster den Benutzer über die Verfügbarkeit eines Updates und bietet ihm die Möglichkeit, es herunterzuladen und zu installieren.

>[!NOTE]
>
>Stellen Sie sicher, dass der Apache-Benutzer über die entsprechenden Leserechte für diese Installationsdatei verfügt, und lesen Sie das [Installationshandbuch](../../installation/using/general-architecture.md), um weitere Informationen zu erhalten.
