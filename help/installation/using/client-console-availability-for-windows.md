---
product: campaign
title: Client-Konsolenverfügbarkeit unter Windows
description: Client-Konsolenverfügbarkeit unter Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 4%

---

# Client-Konsolenverfügbarkeit unter Windows{#client-console-availability-for-windows}

![](../../assets/v7-only.svg)

Damit sich Adobe Campaign-Benutzer bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Clientkonsole verwenden.

## Bereitstellen der Client-Konsole

Wenn der zum Starten eines Adobe Campaign-Anwendungsservers verwendete Computer (**nlserver web**) Benutzerverbindungen von der Clientkonsole erhält, können Sie ihn so konfigurieren, dass das Installationsprogramm für den Rich-Client von Adobe Campaign über eine HTML-Schnittstelle verfügbar gemacht wird. Sobald eine neue Version der Client-Konsole verfügbar ist, werden Benutzer aufgefordert, sie beim Start ihrer Client-Konsole herunterzuladen.

Dazu müssen Sie:

1. Wählen Sie das Paket aus, das das Konsoleninstallationsprogramm enthält.

   Diese Datei wird `setup-client-7.X.XXXX.exe` für v7 oder `setup-client-6.X.XXXX.exe` für v6.1 aufgerufen, wobei `X` die Unterversion von Adobe Campaign und `XXXX` die Build-Nummer ist.

1. Kopieren Sie dieses Paket und fügen Sie es in den Adobe Campaign-Installationsordner (auf dem Marketing-Server für hybride Installationen) unter **/datakit/nl/eng/jsp** ein.
1. Starten Sie den Adobe Campaign-Server.

Campaign-Benutzer können dann das Installationsprogramm der Konsole über einen Webbrowser herunterladen. Die URL lautet dazu:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Für diese Seite sind ein Login und ein Kennwort erforderlich, die in der Anwendung definiert sind.

In diesem Abschnitt](../../installation/using/installing-the-client-console.md) erfahren Sie, wie Sie die Konsole [installieren.

## Endbenutzer vorschlagen, ihre Clientkonsole zu aktualisieren

Sobald die Konsole im Ordner des Campaign-Servers verfügbar ist, werden die Benutzer aufgefordert, die neueste Clientkonsolenversion in einem dedizierten Eingabeaufforderungsfenster herunterzuladen. Adobe empfiehlt, die Option **[!UICONTROL Diese Frage nicht mehr stellen]** nicht ausgewählt zu lassen, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.

Wenn Sie diese Option auswählen und sich gegen den Download der neuesten Version entscheiden, wird kein anderer Benutzer über die neuen verfügbaren Versionen informiert.

Wenn die Option ausgewählt wurde, können Sie diese Aufforderung zurücksetzen. Nur Systemadministratoren, die mit der Bearbeitung von Windows Registry vertraut sind, sollten diese Änderungen vornehmen:

1. Öffnen Sie den Registrierungs-Editor mit dem Befehl **regedit** im Menü **[!UICONTROL Start > Ausführen]** .
1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den Eintrag **confAdvisedUpgrade** und schließen Sie den Registrierungs-Editor.
