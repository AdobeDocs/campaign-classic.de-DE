---
solution: Campaign Classic
product: campaign
title: Aktualisieren auf einen neuen Build
description: Erfahren Sie mehr über die technischen Schritte zur Aktualisierung auf einen neuen Build
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 9%

---


# Aktualisieren auf einen neuen Build (lokal){#upgrading}

Bevor Sie den Aktualisierungsprozess starten, müssen Sie feststellen, auf welche Version des Adobe Campaigns aktualisiert werden soll, und die [Versionshinweise](../../rn/using/latest-release.md) lesen.

>[!IMPORTANT]
>
>Es wird dringend empfohlen, vor der Aktualisierung eine Datenbanksicherung für jede Instanz durchzuführen. Weitere Informationen finden Sie unter [Backup](../../production/using/backup.md).\
>Um eine Aktualisierung durchzuführen, stellen Sie sicher, dass Sie über die Fähigkeit und die Berechtigungen zum Zugriff auf Instanzen und Protokolle verfügen.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Installationsanleitung](../../installation/using/general-architecture.md) und unter [Build-Aktualisierung](https://helpx.adobe.com/de/campaign/kb/acc-build-upgrade.html).

## Windows {#in-windows}

Um Adobe Campaign bei der Bereitstellung eines neuen Builds in einer neuen Version zu aktualisieren, sollte unter Windows das folgende Verfahren angewendet werden:

* [Dienste beenden](#shut-down-services),
* [Aktualisieren Sie die Adobe Campaign-Serveranwendung](#upgrade-the-adobe-campaign-server-application),
* [Ressourcen synchronisieren](#synchronize-resources),
* [Dienste wieder starten](#restart-services).

Informationen zum Aktualisieren der Client-Konsole finden Sie in [diesem Abschnitt](../../installation/using/client-console-availability-for-windows.md).

### Dienste beenden {#shut-down-services}

Um alle Dateien durch die neue Version zu ersetzen, müssen Sie alle Instanzen des nlserver-Dienstes herunterfahren.

1. Beenden Sie die folgenden Dienste:

   * Webdienste (IIS):

      **iisreset/stop**

   * Adobe-Campaign-Dienst: **net stop nlserver6**

   >[!IMPORTANT]
   >
   >Sie müssen auch sicherstellen, dass der Umleitungsserver (webmdl) gestoppt wird, damit die **nlsrvmod.dll**-Datei, die von IIS verwendet wird, durch die neue Version ersetzt werden kann.

1. Vergewissern Sie sich, dass keine Aufgaben aktiv sind, indem Sie den Befehl **nlserver pdump** ausführen. Es sollte Folgendes aufgeführt werden:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Sie können den Windows Aufgabe Manager verwenden, um sicherzustellen, dass alle Prozesse beendet werden.

### Aktualisieren Sie die Adobe-Campaign-Server-Anwendung.{#upgrade-the-adobe-campaign-server-application}

Um die Aktualisierungsdatei auszuführen, führen Sie die folgenden Schritte aus:

1. Führen Sie **setup.exe** aus.

   Um diese Datei herunterzuladen, stellen Sie eine Verbindung zum [Software-Distributionsportal](https://experience.adobe.com/downloads) mit Ihren Benutzeranmeldeinformationen her. Weitere Informationen zur Softwareverteilung finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

1. Wählen Sie den Installationsmodus aus: **[!UICONTROL Aktualisieren oder Reparieren]**
1. Klicken Sie auf **[!UICONTROL Weiter]** .
1. Klicken Sie auf **[!UICONTROL Beenden]** .

   Anschließend kopiert das Programm die neuen Dateien.

1. Wählen Sie nach Abschluss des Vorgangs die Option **[!UICONTROL Beenden]** aus .

### Ressourcen synchronisieren {#synchronize-resources}

Verwenden Sie die folgende Befehlszeile:

**nlserver config -postupgrade -allinstances**

Auf diese Weise können Sie die folgenden Vorgänge durchführen:

* Ressourcen synchronisieren,
* Schemas aktualisieren,
* die Datenbank aktualisieren.

>[!NOTE]
>
>Dieser Vorgang sollte nur einmal und nur auf einem Anwendungsserver (**nlserver web**) durchgeführt werden.

Überprüfen Sie dann, ob die Synchronisierung Fehler oder Warnungen generiert hat. Weitere Informationen hierzu finden Sie unter [Beheben von Aktualisierungskonflikten](#resolving-upgrade-conflicts).

### Dienste wieder starten {#restart-services}

Folgende Dienste sollen neu gestartet werden:

* Webdienste (IIS):

   **iisreset/Beginn**

* Adobe-Campaign-Dienst: **net start nlserver6**

## Linux {#in-linux}

Um Adobe Campaign in einer neuen Version zu aktualisieren, wenn ein neuer Build bereitgestellt wird, gilt folgendes Verfahren für Linux:

* [Abrufen aktualisierter Pakete](#obtain-updated-packages),
* [Führen Sie eine Aktualisierung](#perform-an-update) durch,
* [Starten Sie den Webserver](#reboot-the-web-server) neu.

Informationen zum Aktualisieren der Client-Konsole finden Sie in [diesem Abschnitt](../../installation/using/client-console-availability-for-linux.md).

>[!NOTE]
>
>Ab Build 8757 wird die Drittanbieter-Bibliothek nicht mehr benötigt.

### Abrufen aktualisierter Pakete {#obtain-updated-packages}

Beginn durch Wiederherstellen der beiden aktualisierten Pakete des Adobe Campaigns: Verbinden Sie sich mit dem [Software Distribution Portal](https://experience.adobe.com/downloads) mit Ihren Benutzeranmeldeinformationen. Weitere Informationen zur Softwareverteilung finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

Die Datei ist **nlserver6-v7-XXX.rpm**

### Führen Sie eine Aktualisierung durch {#perform-an-update}

* RPM-basierte Distribution (RedHat, SuSe)

   Führen Sie zum Installieren die folgenden Schritte als Root aus:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   wobei XXX die Version der Datei ist.

   Die rpm-Datei hat Abhängigkeiten von Paketen, die Sie in CentOS/Red Hat-Distributionen finden können. Wenn Sie einige dieser Abhängigkeiten nicht verwenden möchten, müssen Sie möglicherweise die Option &quot;nodeps&quot;von rpm verwenden:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* DEB-basierte Distribution (Debian)

   Führen Sie zum Installieren die folgenden Schritte als Root aus:

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>Ausführliche Installationsanweisungen finden Sie in [diesem Abschnitt](../../installation/using/installing-campaign-standard-packages.md). Ressourcen werden automatisch synchronisiert. Sie müssen jedoch sicherstellen, dass keine Fehler aufgetreten sind. Weitere Informationen hierzu finden Sie unter [Beheben von Aktualisierungskonflikten](#resolving-upgrade-conflicts).

### Webserver neu starten {#reboot-the-web-server}

Sie müssen den Apache herunterfahren, damit die neue Bibliothek angewendet werden kann.

Führen Sie dazu den folgenden Befehl aus:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Ihr Skript kann anstelle von **apache** **httpd heißen.**
>* Sie MÜSSEN diesen Befehl ausführen, bis Sie die folgende Antwort erhalten:
>
>   Dieser Vorgang ist erforderlich, damit Apache die neue Bibliothek anwenden kann.


Starten Sie dann Apache neu:

```
/etc/init.d/apache start
```

## Beheben von Aktualisierungskonflikten {#resolving-upgrade-conflicts}

Bei der Ressourcensynchronisierung können Sie mit dem Befehl **postupgrade** erkennen, ob die Synchronisierung Fehler oder Warnungen hervorgerufen hat.

### Ansicht des Synchronisierungsergebnisses {#view-the-synchronization-result}

Es gibt zwei Möglichkeiten, das Synchronisierungsergebnis anzuzeigen:

* In der Befehlszeilenschnittstelle werden Fehler durch ein dreifaches chevron **>>** angezeigt und die Synchronisierung wird automatisch beendet. Warnungen werden durch eine Dublette chevron **>** erzeugt und müssen nach Abschluss der Synchronisierung aufgelöst werden. Am Ende der Aktualisierung wird an der Eingabeaufforderung eine Zusammenfassung angezeigt. Es kann wie folgt aussehen:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Wenn ein Warnhinweis aufgrund eines Konflikts von Ressourcen ausgegeben wird, muss ihn der Benutzer lösen.

* Die Protokolldatei **postupgrade_`<server version number>_<time of postupgrade>`.log** enthält das Synchronisierungsergebnis. Er ist standardmäßig im folgenden Verzeichnis verfügbar: **`<installation directory>/var/<instance/postupgrade`**. Fehler und Warnungen werden durch die Fehler- und Warnattribute angezeigt.

### Beheben von Konflikten {#resolving-conflicts}

Gehen Sie wie folgt vor, um einen Konflikt zu lösen:

1. Wechseln Sie in der Baum &quot;Adobe Campaign&quot;zu **[!UICONTROL Administration > Konfiguration > Paketverwaltung > Konflikte bearbeiten]** .
1. Wählen Sie in der Liste den Konflikt aus, den Sie lösen möchten.

Es gibt drei Möglichkeiten, einen Konflikt zu lösen:

* **[!UICONTROL Als gelöst]**  deklarieren: erfordert eine vorherige Benutzereingabe.
* **[!UICONTROL Die neue Version]**  akzeptieren: empfohlen, wenn die mit Adobe Campaign bereitgestellten Ressourcen vom Benutzer nicht geändert wurden.
* **[!UICONTROL Aktuelle Version]**  beibehalten: bedeutet, dass die Aktualisierung abgelehnt wird.

   >[!IMPORTANT]
   >
   >Wenn Sie diesen Auflösungsmodus auswählen, werden in der neuen Version möglicherweise keine Korrekturen vorgenommen.

Wenn Sie den Konflikt manuell lösen möchten, gehen Sie wie folgt vor:

1. Suchen Sie im unteren Bereich des Fensters nach der Zeichenfolge **_konflikt_**, um die Entitäten mit Konflikten zu suchen. Die mit der neuen Version installierte Entität enthält das Argument **new**. Die Entität, die der vorherigen Version entspricht, enthält das Argument **cus**.

   ![](assets/s_ncs_production_conflict002.png)

1. Löschen Sie die Version, die Sie nicht behalten möchten. Löschen Sie die Zeichenfolge **_column_argument_** der Entität, die Sie behalten möchten.

   ![](assets/s_ncs_production_conflict003.png)

1. Gehen Sie zum gelösten Konflikt. Klicken Sie auf das Symbol **[!UICONTROL Aktionen]** und wählen Sie **[!UICONTROL Als gelöst deklarieren]** aus .
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

### Best Practices {#best-practices}

Ein Updatefehler kann mit der Datenbankkonfiguration verknüpft sein. Vergewissern Sie sich, dass die vom technischen Administrator und vom Datenbankadministrator ausgeführten Konfigurationen kompatibel sind.

Beispielsweise darf eine Unicode-Datenbank nicht nur die Datenspeicherung von LATIN1-Daten usw. autorisieren.

## Warnt die Client-Konsolen des verfügbaren Updates {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Laden Sie die Adobe Campaign-Datei auf dem Computer, auf dem der Anwendungsserver (**nlserver web**) installiert ist, herunter und kopieren Sie sie

**setup-client-6.XXXX.exe**

in **[Pfad der Anwendung]**datakitnlänjsp

Wenn die Client-Konsolen das nächste Mal angeschlossen werden, informiert ein Fenster die Benutzer über die Verfügbarkeit eines Updates und gibt ihnen die Möglichkeit, das Update herunterzuladen und zu installieren, ein Angebot.

>[!NOTE]
>
>Vergewissern Sie sich, dass der IIS_XPG-Benutzer über die entsprechenden Leserechte für diese Installationsdatei verfügt, und lesen Sie das [Installationshandbuch](../../installation/using/general-architecture.md), um weitere Informationen zu erhalten.

### Linux {#in-linux-1}

Rufen Sie auf dem Adobe Campaign, auf dem der Anwendungsserver (**nlserver web**) installiert ist, das folgende Paket ab:

**setup-client-6.XXXX.exe**

und kopieren Sie es, indem Sie als **/usr/local/neolane/nl6/datakit/nl/eng/jsp** speichern:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Wenn die Client-Konsolen das nächste Mal angeschlossen werden, informiert ein Fenster die Benutzer über die Verfügbarkeit eines Updates und gibt ihnen die Möglichkeit, das Update herunterzuladen und zu installieren, ein Angebot.

>[!NOTE]
>
>Vergewissern Sie sich, dass der Apache-Benutzer über die entsprechenden Leserechte für diese Installationsdatei verfügt, und lesen Sie das [Installationshandbuch](../../installation/using/general-architecture.md), um weitere Informationen zu erhalten.

