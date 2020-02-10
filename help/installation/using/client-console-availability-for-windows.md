---
title: Client-Konsolenverfügbarkeit für Windows
seo-title: Client-Konsolenverfügbarkeit für Windows
description: Client-Konsolenverfügbarkeit für Windows
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Client-Konsolenverfügbarkeit für Windows{#client-console-availability-for-windows}

Damit Adobe Campaign-Benutzer sich bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Client-Konsole verwenden.

Wenn der zum Starten eines Adobe Campaign-Anwendungsservers (**nlserver web**) verwendete Computer Benutzerverbindungen von der Client-Konsole erhält, können Sie dieses so konfigurieren, dass das Installationsprogramm für den Rich-Client von Adobe Campaign über eine HTML-Schnittstelle verfügbar gemacht wird.

Dazu müssen Sie:

1. Stellen Sie das Paket mit dem Konsoleninstallationsprogramm wieder her.

   Diese Datei wird `setup-client-7.X.XXXX.exe` für Version 7 oder `setup-client-6.X.XXXX.exe` für Version 6.1 aufgerufen, wobei `X` es sich um die Unterversion von Adobe Campaign handelt und `XXXX` die Buildnummer lautet.

1. Kopieren Sie dieses Paket und fügen Sie es in den Adobe Campaign-Installationsordner unter **/datakit/nl/eng/jsp** ein.
1. Starten Sie den Adobe Campaign-Server.

Die Endbenutzer können dann das Konsoleninstallationsprogramm über einen Webbrowser herunterladen, indem sie die folgende URL verwenden:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Diese Seite erfordert einen Benutzernamen und ein Kennwort, die in der Anwendung definiert sind.

Informationen zum Herunterladen und Installieren der Konsole finden Sie unter [Installieren der Clientkonsole](../../installation/using/installing-the-client-console.md).

Sobald eine neue Version der Client-Konsole verfügbar ist, können Sie sie herunterladen.

>[!NOTE]
>
>In der angezeigten Eingabeaufforderung empfiehlt Adobe, die Option nicht auszuwählen, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Version der Konsole verfügbar ist. **[!UICONTROL No longer ask this question]**\
>Wenn Sie diese Option auswählen und die neueste Version nicht herunterladen möchten, wird kein anderer Benutzer über neue verfügbare Versionen informiert.

Gehen Sie wie folgt vor, um diese Eingabeaufforderung zurückzusetzen (nur Systemadministratoren, die mit der Bearbeitung der Registrierung vertraut sind, sollten diese Änderungen vornehmen):

1. Öffnen Sie den Registrierungs-Editor mit dem **Befehl regedit** aus dem **[!UICONTROL Start > Run]** Menü.
1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den Eintrag **confAdvisedUpgrade** und schließen Sie den Registrierungseditor.

