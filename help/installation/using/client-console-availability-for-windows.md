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

Wenn der Computer zum Starten eines Adobe Campaign-Anwendungsservers verwendet wurde (**nlserver web**) Benutzerverbindungen von der Clientkonsole erhält, können Sie sie so konfigurieren, dass das Installationsprogramm für den Rich-Client von Adobe Campaign über eine HTML-Oberfläche verfügbar ist. Sobald eine neue Version der Client-Konsole verfügbar ist, werden Benutzer aufgefordert, sie beim Start ihrer Client-Konsole herunterzuladen.

Dazu müssen Sie:

1. Wählen Sie das Paket aus, das das Konsoleninstallationsprogramm enthält.

   Diese Datei heißt `setup-client-7.X.XXXX.exe` für v7 oder `setup-client-6.X.XXXX.exe` für v6.1, wobei `X` ist die Unterversion von Adobe Campaign und `XXXX` ist die Build-Nummer.

1. Kopieren Sie dieses Paket und fügen Sie es in den Adobe Campaign-Installationsordner ein (auf dem Marketing-Server für hybride Installationen), unter **/datakit/nl/eng/jsp**.
1. Starten Sie den Adobe Campaign-Server.

Campaign-Benutzer können dann das Installationsprogramm der Konsole über einen Webbrowser herunterladen. Die URL lautet dazu:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Für diese Seite sind ein Login und ein Kennwort erforderlich, die in der Anwendung definiert sind.

Erfahren Sie, wie Sie die Konsole installieren [in diesem Abschnitt](../../installation/using/installing-the-client-console.md).

## Endbenutzer vorschlagen, ihre Clientkonsole zu aktualisieren

Sobald die Konsole im Ordner des Campaign-Servers verfügbar ist, werden die Benutzer aufgefordert, die neueste Clientkonsolenversion in einem dedizierten Eingabeaufforderungsfenster herunterzuladen. Adobe empfiehlt, die Option zu verlassen **[!UICONTROL Diese Frage stellen Sie nicht mehr]** nicht ausgewählt ist, um sicherzustellen, dass alle Benutzer benachrichtigt werden, wenn eine neue Version der Konsole verfügbar ist.

Wenn Sie diese Option auswählen und sich gegen den Download der neuesten Version entscheiden, wird kein anderer Benutzer über die neuen verfügbaren Versionen informiert.

Wenn die Option ausgewählt wurde, können Sie diese Aufforderung zurücksetzen. Nur Systemadministratoren, die mit der Bearbeitung von Windows Registry vertraut sind, sollten diese Änderungen vornehmen:

1. Öffnen Sie den Registrierungs-Editor mithilfe der **regedit** -Befehl aus dem **[!UICONTROL Start > Ausführen]** Menü.
1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie die **confAdvisedUpgrade** Registrieren Sie sich und schließen Sie den Registrierungs-Editor.
