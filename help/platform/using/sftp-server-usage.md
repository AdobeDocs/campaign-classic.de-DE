---
title: Nutzung von SFTP-Servern
description: Erfahren Sie mehr über Best Practices und Fehlerbehebung für SFTP-Server.
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8198c4aa6eccc0cbb5de4712ebdd8000783b615c
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 65%

---


# Best Practices zum SFTP-Server und Fehlerbehebung {#sftp-server-usage}

## Best Practices für die Nutzung von SFTP-Servern {#sftp-server-best-practices}

Wenn Dateien und Daten für ETL-Zwecke verwaltet werden, werden diese Dateien auf einem von Adobe bereitgestellten gehosteten SFTP-Server gespeichert. Dieser SFTP-Server ist ein vorübergehender Speicherplatz, auf dem Sie die Aufbewahrung und Löschung von Dateien selbst kontrollieren können.

Wenn der Speicherplatz nicht korrekt verwendet oder gewartet wird, kann der verfügbare physische Platz schnell aufgebraucht sein und dazu führen, dass Dateien beim Hochladen abgeschnitten werden. Wenn der Speicherplatz aufgebraucht ist, kann eine automatische Bereinigung ausgelöst werden, bei der die ältesten Dateien aus dem SFTP-Speicher gelöscht werden.

Um solche Probleme zu vermeiden, empfiehlt Adobe, die unten stehenden Best Practices zu befolgen.

>[!NOTE]
>
>Wenn Ihre Instanz auf AWS gehostet wird, können Sie den Speicherplatz des SFTP-Servers mit dem [Control Panel](https://docs.adobe.com/content/help/de-DE/control-panel/using/sftp-management/sftp-storage-management.html) von Campaign Classic überwachen.
>
>Um zu überprüfen, ob Ihre Instanz auf AWS gehostet wird, folgen Sie den Schritten in [diesem Abschnitt](https://docs.adobe.com/content/help/de-DE/control-panel/using/faq.html#ims-org-id) .

* Die Größe des Servers variiert je nach Ihrer Lizenz. Achten Sie in jedem Fall darauf, dass die Datengröße möglichst gering ist und bewahren Sie Daten nur so lange auf, wie dies erforderlich ist (15 Tage ist das obere Zeitlimit).
* Verwenden Sie eine schlüsselbasierte Authentifizierung anstelle einer passwortbasierten Authentifizierung, um das Ablaufen von Passwörtern zu vermeiden (Passwörter haben eine Gültigkeitsdauer von 90 Tagen). Außerdem ermöglicht die schlüsselbasierte Authentifizierung die Erstellung mehrerer Schlüssel, wenn beispielsweise mehrere Entitäten verwaltet werden. Im Gegensatz dazu erfordert die passwortbasierte Authentifizierung, dass das Passwort mit allen verwalteten Entitäten geteilt wird.

   Das unterstützte Schlüsselformat ist SSH-2 RSA 2048. Schlüssel können mit Tools wie PyTTY (Windows) oder ssh-keygen (Unix) erstellt werden. Stellen Sie dem Adobe-Supportteam den öffentlichen Schlüssel über ein [Supportticket](https://support.neolane.net) bereit, damit er zum Campaign-Server hochgeladen werden kann.

* Verwenden Sie Workflows, um Daten ordnungsgemäß zu löschen (verwalten Sie die Beibehaltung von Daten innerhalb der Workflows, die die Daten nutzen).
* Verwenden Sie Batch-Prozesse bei SFTP-Uploads und in Workflows.
* Beseitigen Sie Fehler/Ausnahmen.
* Melden Sie sich gelegentlich beim SFTP-Server direkt an, um dessen Inhalt zu prüfen.
* Beachten Sie bitte, dass die Verwaltung des SFTP-Speichers hauptsächlich Ihre Verantwortung ist.
* Standardmäßig sind alle von Ihnen erstellten Ordner im Lese-/Schreibmodus ausschließlich für Ihre Kennung verfügbar. Wenn Sie Ordner erstellen, auf die Campaign Zugriff haben soll, konfigurieren Sie sie mit Lese-/Schreibrechten für die gesamte Gruppe. Andernfalls ist es für Workflows unmöglich, Dateien zu erstellen oder zu löschen, da sie aus Sicherheitsgründen innerhalb derselben Gruppe unter einer anderen Kennung ausgeführt werden.
* Die öffentlichen IPs, von denen Sie versuchen, die SFTP-Verbindung zu starten, müssen der Zulassungsliste in der Kampagne-Instanz hinzugefügt werden. Das Hinzufügen von IP-Adressen zur Zulassungsliste kann über ein [Support-Ticket](https://support.neolane.net)angefordert werden.

>[!CAUTION]
>
>Wenn Sie Ihren eigenen SFTP-Server verwenden, versuchen Sie, die Empfehlungen möglichst umfassend einzuhalten.

## Verbindungsprobleme mit Adobe-gehostetem SFTP-Server {#sftp-server-troubleshooting}

Im folgenden Abschnitt finden Sie die Informationen, die Sie dem Adobe-Supportteam bereitstellen müssen, wenn Sie im Fall eines Verbindungsproblems mit den von Adobe gehosteten SFTP-Servern ein [Supportticket](https://support.neolane.net) lösen.

1. Überprüfen Sie, ob Ihre Instanz ausgeführt wird. Öffnen Sie dazu Ihren Browser und machen Sie einen **[!UICONTROL GET]**-Aufruf am **[!UICONTROL /r/test]**-Endpunkt der Instanz:

   ```
   https://instanceUrl/r/test
   ```

   Wenn die Instanz ausgeführt wird, erhalten Sie in etwa diese Antwort:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   Geben Sie in jedem Fall im Supportticket die Antwort an, die Sie auf den Befehl erhalten haben.

1. Überprüfen Sie, ob der ausgehende Port 22 dort geöffnet ist, wo Sie versuchen, die SFTP-Verbindung aufzubauen. Verwenden Sie dazu den folgenden Befehl:

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >Mithilfe des Netcat Tools können Sie mühelos Netzwerkverbindungen auf verschiedenen Betriebssystemen verwalten (siehe [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Wenn der Port nicht geöffnet ist, stellen Sie sicher, dass Sie ausgehende Verbindungen auf Ihrer Seite öffnen und versuchen Sie es dann erneut. Wenn Sie immer noch Verbindungsprobleme haben, melden Sie das Ergebnis des Befehls dem Adobe-Supportteam.

1. Vergewissern Sie sich, dass die öffentliche IP, über die Sie die SFTP-Verbindung starten möchten, die IP ist, die Sie der Adobe Support für die Zulassungsliste angegeben haben.
1. Wenn Sie Passwort-basierte Authentifizierung verwenden, ist Ihr Passwort möglicherweise abgelaufen (die Gültigkeitsdauer von Passwörtern beträgt 90 Tage). Daher empfehlen wir dringend die Verwendung einer schlüsselbasierten Authentifizierung (siehe [Best Practices für die Nutzung von SFTP-Servern](#sftp-server-best-practices)).
1. Wenn Sie eine schlüsselbasierte Authentifizierung verwenden, überprüfen Sie, ob der von Ihnen verwendete Schlüssel mit dem übereinstimmt, den Sie dem Adobe-Supportteam zur Konfiguration der Instanz bereitgestellt haben.
1. Wenn Sie FileZilla oder ein ähnliches FTP-Tool verwenden, geben Sie im Supportticket die Verbindungsprotokoll-Details an.

## Fehler &quot;Hostname konnte nicht aufgelöst werden&quot;

Dieser Abschnitt enthält Informationen zu den Prüfungen und Aktionen, die beim Abrufen des Fehlers &quot;Host name konnte nicht aufgelöst werden&quot;nach dem Herstellen einer Verbindung mit dem FTP-Server von Campaign Classic ausgeführt werden.

Das Workflow-Protokoll enthält die folgenden Protokolle:

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Dieser Fehler tritt auf, wenn versucht wird, den FTP-Server über einen Workflow zu verbinden und die Dateien vom Server herunterzuladen, während Sie weiterhin über FTP eine Verbindung mit FileZilla oder WinSCP herstellen können.

Dieser Fehler gibt an, dass der Domänenname des FTP-Servers nicht ordnungsgemäß aufgelöst werden konnte. Gehen Sie zur Fehlerbehebung wie folgt vor:

1. Fehlerbehebung bei der **DNS-Serverkonfiguration**:

   1. Überprüfen Sie, ob der Servername dem lokalen DNS-Server hinzugefügt wurde.
   1. Falls ja, führen Sie den folgenden Befehl auf dem Adobe Campaign-Server aus, um die IP-Adresse abzurufen:

      `nslookup <server domain name>`

      Dies bestätigt, dass der FTP-Server funktioniert und vom Adobe Campaign-Anwendungsserver aus erreichbar ist.

1. Fehlerbehebung bei **Sitzungsprotokollen**:

   1. Klicken Sie im Workflow mit der Dublette auf die Aktivität [Dateiübertragung](../../workflow/using/file-transfer.md) .
   1. Wechseln Sie zur Registerkarte **[!UICONTROL Dateiübertragung]** und klicken Sie dann auf **[!UICONTROL Erweiterte Parameter]**.
   1. Aktivieren Sie die Option Sitzungsprotokolle **[!UICONTROL anzeigen]** .

      ![](assets/sftp-error-display-logs.png)

   1. Gehen Sie zur Workflow-Prüfung und prüfen Sie, ob in den Protokollen der Fehler &quot;Host-Name konnte nicht aufgelöst werden&quot;angezeigt wird.

1. Wenn der SFTP-Server von der Adobe gehostet wird, prüfen Sie, ob der Zulassungsliste IP hinzugefügt wird, indem Sie sich an den Kundendienst wenden.

   Andernfalls validieren:

   * Das Kennwort enthält kein &quot;@&quot;. Die Verbindung ist fehlgeschlagen, wenn das Kennwort &quot;@&quot;enthält.
   * Es gibt keine Firewall-Probleme, die die Kommunikation zwischen dem Adobe Campaign-Anwendungsserver und dem SFTP-Server behindern können.
   * Führen Sie die Befehle &quot;track&quot;und &quot;telnet&quot;vom Kampagne-Server zum SFTP aus, um zu sehen, ob Verbindungsprobleme vorliegen.
   * Es gibt keine Probleme mit dem Kommunikationsprotokoll.
   * Port ist offen.
