---
product: campaign
title: Client-Konsolenverfügbarkeit unter Windows
description: Client-Konsolenverfügbarkeit unter Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 5%

---

# Client-Konsolenverfügbarkeit unter Windows{#client-console-availability-for-windows}



Damit sich Adobe Campaign-Benutzer bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Clientkonsole verwenden.

## Bereitstellen der Client-Konsole

Wenn der Computer zum Starten eines Adobe Campaign-Anwendungsservers verwendet wurde (**nlserver web**) Benutzerverbindungen von der Clientkonsole erhält, können Sie sie so konfigurieren, dass das Installationsprogramm für den Rich-Client von Adobe Campaign über eine HTML-Oberfläche verfügbar ist. Sobald eine neue Version der Client-Konsole verfügbar ist, werden Benutzer aufgefordert, sie beim Start ihrer Client-Konsole herunterzuladen.

Gehen Sie dazu folgendermaßen vor:

1. Wählen Sie das Paket aus, das das Konsoleninstallationsprogramm enthält.

   Diese Datei heißt `setup-client-7.X.XXXX.exe`, wobei `X` ist die Unterversion von Adobe Campaign und `XXXX` ist die Build-Nummer.

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
