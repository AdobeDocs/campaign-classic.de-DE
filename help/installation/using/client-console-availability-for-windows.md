---
solution: Campaign Classic
product: campaign
title: Client-Konsolenverfügbarkeit unter Windows
description: Client-Konsolenverfügbarkeit unter Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 5%

---


# Client-Konsolenverfügbarkeit unter Windows{#client-console-availability-for-windows}

Damit Adobe Campaign-Benutzer sich bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Client-Konsole verwenden.

Wenn der zum Beginn eines Adobe Campaign-Anwendungsservers verwendete Computer (**nlserver web**) Benutzerverbindungen von der Client-Konsole empfängt, können Sie konfigurieren, dass das Setup-Programm für den Rich-Client des Adobe Campaigns über eine HTML-Schnittstelle verfügbar gemacht wird.

Dazu müssen Sie:

1. Stellen Sie das Programm mit dem Konsoleninstallationspaket wieder her.

   Diese Datei heißt für v7 `setup-client-7.X.XXXX.exe` oder für v6.1 `setup-client-6.X.XXXX.exe`, wobei `X` die Unterversion von Adobe Campaign und `XXXX` die Buildnummer ist.

1. Kopieren Sie dieses Adobe Campaign und fügen Sie es in den Installationsordner unter **/datakit/nl/eng/jsp** ein.
1. Beginn des Adobe Campaign-Servers.

Die Endbenutzer können das Konsoleninstallationsprogramm dann über einen Webbrowser herunterladen, indem sie die folgende URL verwenden:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Diese Seite erfordert einen Benutzernamen und ein Kennwort, die in der Anwendung definiert sind.

Informationen zum Herunterladen und Installieren der Konsole finden Sie unter [Installieren der Client-Konsole](../../installation/using/installing-the-client-console.md).

Sobald eine neue Version der Client-Konsole verfügbar ist, können Sie sie herunterladen.

>[!NOTE]
>
>In der angezeigten Eingabeaufforderung empfiehlt Adobe, die Option **[!UICONTROL Frage]** nicht mehr auszuwählen, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.\
>Wenn Sie diese Option auswählen und die neueste Version nicht herunterladen möchten, wird kein anderer Benutzer über neue verfügbare Versionen informiert.

Gehen Sie wie folgt vor, um diese Eingabeaufforderung zurückzusetzen (nur Systemadministratoren, die mit der Bearbeitung der Registrierung vertraut sind, sollten diese Änderungen vornehmen):

1. Öffnen Sie den Registrierungs-Editor mit dem Befehl **regedit** aus dem Menü **[!UICONTROL Beginn > Ausführen]**.
1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den Eintrag **confAdvisedUpgrade** und schließen Sie den Registrierungs-Editor.

