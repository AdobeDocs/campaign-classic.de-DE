---
solution: Campaign Classic
product: campaign
title: Client-Konsolenverfügbarkeit unter Windows
description: Client-Konsolenverfügbarkeit unter Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 4%

---


# Client-Konsolenverfügbarkeit unter Windows{#client-console-availability-for-windows}

Damit Adobe Campaign-Benutzer sich bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Client-Konsole verwenden.

## Bereitstellen der Client-Konsole

Wenn der zum Beginn eines Adobe Campaign-Anwendungsservers verwendete Computer (**nlserver web**) Benutzerverbindungen von der Client-Konsole empfängt, können Sie konfigurieren, dass das Setup-Programm für den Rich-Client des Adobe Campaigns über eine HTML-Schnittstelle verfügbar gemacht wird. Sobald eine neue Version der Client-Konsole verfügbar ist, werden Benutzer eingeladen, sie beim Starten ihrer Client-Konsole herunterzuladen.

Dazu müssen Sie:

1. Wählen Sie das Paket aus, das das Programm für die Konsoleninstallation enthält.

   Diese Datei heißt für v7 `setup-client-7.X.XXXX.exe` oder für v6.1 `setup-client-6.X.XXXX.exe`, wobei `X` die Unterversion von Adobe Campaign und `XXXX` die Buildnummer ist.

1. Kopieren Sie dieses Adobe Campaign in den Installationsordner (auf dem Marketing-Server für Hybridinstallationen) unter **/datakit/nl/eng/jsp**.
1. Beginn Adobe Campaign-Server.

Kampagnen-Benutzer können das Konsoleninstallationsprogramm dann über einen Webbrowser herunterladen, indem sie die folgende URL verwenden:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Diese Seite erfordert einen Benutzernamen und ein Kennwort, die in der Anwendung definiert sind.

Erfahren Sie, wie Sie die Konsole [in diesem Abschnitt](../../installation/using/installing-the-client-console.md) installieren.

## Endbenutzer vorschlagen, ihre Client-Konsole zu aktualisieren

Sobald die Konsole im Serverordner der Kampagne verfügbar ist, werden die Benutzer aufgefordert, die neueste Clientkonsolenversion in einem dedizierten Eingabeaufforderungsfenster herunterzuladen. Adobe empfiehlt, die Option **[!UICONTROL Diese Frage]** nicht mehr auszuwählen, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.

Wenn Sie diese Option auswählen und die neueste Version nicht herunterladen möchten, wird kein anderer Benutzer über neue verfügbare Versionen informiert.

Wenn die Option ausgewählt wurde, können Sie diese Aufforderung zurücksetzen. Die folgenden Änderungen sollten nur Systemadministratoren vornehmen, die mit der Bearbeitung der Windows-Registrierung vertraut sind:

1. Öffnen Sie den Registrierungs-Editor mit dem Befehl **regedit** aus dem Menü **[!UICONTROL Beginn > Ausführen]**.
1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den Eintrag **confAdvisedUpgrade** und schließen Sie den Registrierungs-Editor.

