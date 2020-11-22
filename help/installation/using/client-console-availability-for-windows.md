---
solution: Campaign Classic
product: campaign
title: Client-Konsolenverfügbarkeit unter Windows
description: Client-Konsolenverfügbarkeit unter Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 5%

---


# Client-Konsolenverfügbarkeit unter Windows{#client-console-availability-for-windows}

Damit Adobe Campaign-Benutzer sich bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Client-Konsole verwenden.

Wenn der zum Beginn eines Adobe Campaign-Anwendungsservers verwendete Computer (**nlserver-Web**) Benutzerverbindungen von der Client-Konsole erhält, können Sie ihn so konfigurieren, dass das Setup-Programm für den Rich-Client des Adobe Campaigns über eine HTML-Schnittstelle verfügbar gemacht wird.

Dazu müssen Sie:

1. Stellen Sie das Programm mit dem Konsoleninstallationspaket wieder her.

   Diese Datei wird `setup-client-7.X.XXXX.exe` für v7 oder `setup-client-6.X.XXXX.exe` für v6.1 aufgerufen, wobei `X` es sich um die Subversion von Adobe Campaign handelt und die Buildnummer `XXXX` angegeben ist.

1. Kopieren Sie dieses Adobe Campaign und fügen Sie es in den Installationsordner unter **/datakit/nl/eng/jsp** ein.
1. Beginn des Adobe Campaign-Servers.

Die Endbenutzer können dann das Konsoleninstallationsprogramm über einen Webbrowser herunterladen, indem sie die folgende URL verwenden:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Diese Seite erfordert einen Benutzernamen und ein Kennwort, die in der Anwendung definiert sind.

Informationen zum Herunterladen und Installieren der Konsole finden Sie unter [Installieren der Client-Konsole](../../installation/using/installing-the-client-console.md).

Sobald eine neue Version der Client-Konsole verfügbar ist, können Sie sie herunterladen.

>[!NOTE]
>
>In der angezeigten Eingabeaufforderung empfiehlt Adobe, die Option Diese Frage **[!UICONTROL nicht]** mehr stellen deaktiviert zu lassen, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.\
>Wenn Sie diese Option auswählen und die neueste Version nicht herunterladen möchten, wird kein anderer Benutzer über neue verfügbare Versionen informiert.

Gehen Sie wie folgt vor, um diese Eingabeaufforderung zurückzusetzen (nur Systemadministratoren, die mit der Bearbeitung der Registrierung vertraut sind, sollten diese Änderungen vornehmen):

1. Öffnen Sie den Registrierungs-Editor mit dem **Befehl regedit** aus dem Menü **[!UICONTROL Beginn > Ausführen]** .
1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den Eintrag **confAdvisedUpgrade** und schließen Sie den Registrierungseditor.

