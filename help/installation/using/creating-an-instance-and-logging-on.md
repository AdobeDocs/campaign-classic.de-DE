---
product: campaign
title: Erstellen einer Instanz und Anmelden
description: Erstellen einer Instanz und Anmelden
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 18%

---

# Erstellen einer Instanz und Anmelden{#creating-an-instance-and-logging-on}



Um eine neue Instanz und Adobe Campaign zu erstellen, wenden Sie den folgenden Prozess an:

1. Erstellen der Verbindung.
1. Melden Sie sich an, um die entsprechenden Instanz zu erstellen.
1. Datenbank erstellen und konfigurieren.

>[!NOTE]
>
>Nur die **interne** Kennung kann diese Vorgänge ausführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

Wenn die Adobe Campaign Konsole gestartet wird, greifen Sie auf eine Log-in Seite zu.

Um eine neue Instanz zu erstellen, folgen Sie die folgenden Schritte:

1. Klicken Sie in der oberen rechten Ecke der Felder mit den Anmeldedaten auf den Link, um das Fenster für die Verbindungskonfiguration aufzurufen. Dieser Link kann entweder **[!UICONTROL Neu...]** oder einem vorhandenen Instanznamen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungs-Servers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie per URL eine Verbindung zum Adobe Campaign-Anwendungs-Server an. Verwenden Sie entweder einen DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise eine URL vom Typ `https://<machine>.<domain>.com` eingeben.

   >[!CAUTION]
   >
   >Verwenden Sie für die Verbindung URL nur die folgenden Zeichen: `[a-z]` , `[A-Z]` `[0-9]` und Gedankenstriche (-) oder vollständige Haltestellen.

1. Klicken **[!UICONTROL Sie auf OK]** , um Einstellungen zu bestätigen: Sie können nun mit dem Instanz Erstellungsvorgang beginnen.
1. **[!UICONTROL Geben Sie im Fenster &quot;Verbindung Einstellungen]** &quot; die **interne** Log-in und ihre Kennwort ein, um eine Verbindung zum Adobe Campaign Applikation Server herzustellen. Nach der Verbindung greifen Sie auf die Instanz Erstellung Assistent, um eine neue Instanz
1. **[!UICONTROL Geben Sie im Feld &quot;Name]** &quot; den **Instanz-namens** ein. Da dieser Name verwendet wird, um eine Konfigurationsdatei **config.php `<instance>`** zu generieren, und in den Befehlszeilenparametern zum Identifizieren der Instanz verwendet wird, sollten Sie einen kurzen Name ohne Sonderzeichen auswählen. Beispiel: **eMarketing** .

   ![](assets/s_ncs_install_create_instance.png)

   Der Name der Instanz, die dem Domänennamen hinzugefügt wird, darf 40 Zeichen nicht überschreiten. Auf diese Weise können Sie die Größe der Kopfzeilen &quot;Nachrichten-ID&quot; einschränken und verhindern, dass Nachrichten als Spam betrachtet werden, insbesondere von Tools wie SpamAssassin.

1. Im **[!UICONTROL DNS-Masken]** die **Liste der DNS-Masken** an die die Instanz angehängt werden soll. Der Adobe Campaign-Server verwendet den Hostnamen, der in den HTTP-Anfragen angezeigt wird, um zu bestimmen, welche Instanz erreicht werden soll.

   Der Hostname ist zwischen der Zeichenfolge enthalten. **https://** und dem ersten Schrägstrich **/** der Serveradresse.

   Sie können eine durch Kommas getrennte Liste von Werten definieren.

   Die ? Und &#42; Zeichen können als Platzhalter verwendet werden, um ein oder mehrere Zeichen (DNS, portieren usw.) zu ersetzen. Für Instanz wird der **Demoverwert&#42;** mit &quot;https://Demo&quot; wie mit &quot;https://Demo:8080&quot; und Linear &quot;https://demo2&quot; funktionieren.

   Die verwendeten Namen müssen in Ihrem DNS definiert werden. Sie können auch die Korrespondenz zwischen einem DNS-Server und einer IP-Adresse in der **Datei &quot;C:/Windows/System32/Drivers/etc/Hosts** &quot; in Windows und in der **Datei &quot;/etc/Hosts** unter Linux&quot; informieren. Sie müssen daher die Verbindungseinstellungen ändern, um diesen DNS-Server in bestellen zu verwenden, um eine Verbindung zu ihren gewählten Instanz herzustellen.

   Der Server muss anhand dieses Namens identifiziert werden, insbesondere zum Hochladieren von Bildern in E-Mails.

   Darüber hinaus muss der Server eine Verbindung zu sich selbst herstellen können, und wenn möglich über eine Loabback-Adresse-127.0.0.1-, insbesondere, damit Berichte im PDF-Format exportiert werden können.

1. Im **[!UICONTROL Sprache]** Dropdown-Liste, wählen Sie die **Instanzensprache**: Englisch (US), Englisch (UK), Französisch oder Japanisch.

   Unterschiede zwischen US-amerikanischem Englisch und britischem Englisch werden im Abschnitt [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Die Instanzsprache kann nach diesem Schritt nicht mehr geändert werden. Adobe Campaign-Instanzen sind nicht mehrsprachig: Sie können die Benutzeroberfläche nicht von einer Sprache in eine andere wechseln.

1. Klicken Sie **[!UICONTROL auf OK]** , um Instanz Erklärung zu bestätigen. Melden Sie sich ab und zurück, um die-Datenbank zu deklarieren

   >[!NOTE]
   >
   >Die Instanz kann über die Befehlszeile erstellt werden. Weiterführende Informationen hierzu finden Sie in [ Befehl Zeilen ](../../installation/using/command-lines.md) .
