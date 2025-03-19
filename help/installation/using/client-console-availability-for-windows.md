---
product: campaign
title: Client-Konsolenverfügbarkeit unter Windows
description: Client-Konsolenverfügbarkeit unter Windows
feature: Installation, Upgrade
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 8%

---

# Client-Konsolenverfügbarkeit unter Windows{#client-console-availability-for-windows}



Damit sich Adobe Campaign-Benutzende bei der von Ihnen erstellten und konfigurierten Instanz anmelden können, müssen sie die Client-Konsole verwenden.

## Client-Konsole verfügbar machen

Wenn der Computer, der zum Starten eines Adobe Campaign-Anwendungsservers (**nlserver web**) verwendet wird, Benutzerverbindungen von der Client-Konsole erhält, können Sie ihn so konfigurieren, dass das Installationsprogramm für den Adobe Campaign Rich-Client über eine HTML-Oberfläche verfügbar gemacht wird. Wenn eine neue Version der Client-Konsole verfügbar ist, werden Benutzer beim Starten ihrer Client-Konsole aufgefordert, diese herunterzuladen.

Gehen Sie dazu folgendermaßen vor:

1. Wählen Sie das Paket aus, das das Konsolen-Installationsprogramm enthält.

   Diese Datei wird als `setup-client-7.X.XXXX.exe` bezeichnet, wobei `X` die Unterversion von Adobe Campaign und `XXXX` die Build-Nummer ist.

1. Kopieren Sie dieses Paket und fügen Sie es in den Adobe Campaign-Installationsordner (auf dem Marketing-Server für Hybridinstallationen) unter **/datakit/nl/eng/jsp** ein.
1. Starten Sie den Adobe Campaign-Server.

Campaign-Benutzer können dann das Installationsprogramm für die Konsole über einen Webbrowser unter folgender URL herunterladen:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Für diese Seite sind ein Login und ein Passwort erforderlich, die im Programm definiert sind.

Wie Sie die Konsole installieren, erfahren [ (in diesem Abschnitt](../../installation/using/installing-the-client-console.md).

## Endbenutzenden vorschlagen, ihre Client-Konsole zu aktualisieren

Sobald die Konsole im Campaign-Server-Ordner verfügbar ist, werden die Benutzer in einem speziellen Eingabeaufforderungsfenster eingeladen, die neueste Version der Client-Konsole herunterzuladen. Adobe empfiehlt, die Option **[!UICONTROL Diese Frage nicht mehr stellen]** deaktiviert zu lassen, um sicherzustellen, dass alle Benutzenden benachrichtigt werden, wenn eine neue Konsolenversion verfügbar ist.

Wenn Sie diese Option wählen und nicht die neueste Version herunterladen möchten, wird kein anderer Benutzer über neue verfügbare Versionen informiert.

Falls die Option ausgewählt wurde, können Sie diese Eingabeaufforderung zurücksetzen. Diese Änderungen sollten nur von Systemadministratoren vorgenommen werden, die mit der Bearbeitung der Windows-Registrierung vertraut sind:

1. Öffnen Sie den Registrierungs-Editor mit dem Befehl **regedit** im Menü **[!UICONTROL Start > Ausführen]**.
1. Suchen Sie nach dem Knoten und erweitern Sie ihn.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Löschen Sie den **confAdvisedUpgrade**-Eintrag und schließen Sie den Registrierungs-Editor.
