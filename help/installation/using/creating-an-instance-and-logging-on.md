---
product: campaign
title: Erstellen einer Instanz und Anmelden
description: Erstellen einer Instanz und Anmelden
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 17%

---

# Erstellen einer Instanz und Anmelden{#creating-an-instance-and-logging-on}



Gehen Sie wie folgt vor, um eine neue Instanz und eine Adobe Campaign-Datenbank zu erstellen:

1. Erstellen der Verbindung.
1. Melden Sie sich an, um die zugehörige Instanz zu erstellen.
1. Datenbank erstellen und konfigurieren.

>[!NOTE]
>
>Nur die **intern** Die Kennung kann diese Vorgänge ausführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

Wenn die Adobe Campaign-Konsole gestartet wird, greifen Sie auf eine Anmeldeseite zu.

Gehen Sie wie folgt vor, um eine neue Instanz zu erstellen:

1. Klicken Sie in der oberen rechten Ecke der Felder mit den Anmeldedaten auf den Link, um das Fenster für die Verbindungskonfiguration aufzurufen. Dieser Link kann entweder **[!UICONTROL Neu...]** oder einem vorhandenen Instanznamen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungs-Servers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie per URL eine Verbindung zum Adobe Campaign-Anwendungs-Server an. Verwenden Sie entweder einen DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise eine URL vom Typ `https://<machine>.<domain>.com` eingeben.

   >[!CAUTION]
   >
   >Verwenden Sie für die Verbindungs-URL nur die folgenden Zeichen: `[a-z]`, `[A-Z]`, `[0-9]` und Bindestriche (-) oder Vollstopps.

1. Klicken **[!UICONTROL Ok]** zur Bestätigung der Einstellungen: können Sie jetzt mit dem Erstellungsprozess der Instanz beginnen.
1. Im **[!UICONTROL Verbindungsparameter]** -Fenster, geben Sie die **intern** Anmeldung und Kennwort zum Herstellen einer Verbindung zum Adobe Campaign-Anwendungsserver. Nach der Verbindung greifen Sie auf den Assistenten zur Instanzerstellung zu, um eine neue Instanz zu deklarieren
1. Im **[!UICONTROL Name]** eingeben. **Instanzname**. Da dieser Name zum Generieren einer Konfigurationsdatei verwendet wird **config-`<instance>`.xml** und in den Befehlszeilenparametern verwendet wird, um die Instanz zu identifizieren, müssen Sie einen Kurznamen ohne Sonderzeichen auswählen. Beispiel: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Der Name der Instanz, die dem Domänennamen hinzugefügt wird, darf 40 Zeichen nicht überschreiten. Auf diese Weise können Sie die Größe von &quot;Nachrichten-ID&quot;-Headern einschränken und verhindern, dass Nachrichten insbesondere von Tools wie SpamAssassin als Spam eingestuft werden.

1. Im **[!UICONTROL DNS-Masken]** die **Liste der DNS-Masken** an die die Instanz angehängt werden soll. Der Adobe Campaign-Server verwendet den Hostnamen, der in den HTTP-Anfragen angezeigt wird, um zu bestimmen, welche Instanz erreicht werden soll.

   Der Hostname ist zwischen der Zeichenfolge enthalten. **https://** und dem ersten Schrägstrich **/** der Serveradresse.

   Sie können eine Liste mit durch Kommas getrennten Werten definieren.

   Die ? und &#42; -Zeichen können als Platzhalter verwendet werden, um ein oder mehrere Zeichen (DNS, Port usw.) zu ersetzen. Beispielsweise wird die **Demo&#42;** -Wert funktioniert mit &quot;https://demo&quot;, da er mit &quot;https://demo:8080&quot;und sogar &quot;https://demo2&quot;funktioniert.

   Die verwendeten Namen müssen in Ihrem DNS definiert sein. Sie können auch die Korrespondenz zwischen einem DNS-Namen und einer IP-Adresse in der **c:/windows/system32/driver/etc/hosts** Datei unter Windows und in der Datei **/etc/hosts** Datei in Linux. Daher müssen Sie die Verbindungseinstellungen ändern, um diesen DNS-Namen zu verwenden, um eine Verbindung mit Ihrer ausgewählten Instanz herzustellen.

   Der Server muss mit diesem Namen identifiziert werden, insbesondere zum Hochladen von Bildern in E-Mails.

   Darüber hinaus muss der Server über diesen Namen und nach Möglichkeit über eine Loopback-Adresse - 127.0.0.1 - eine Verbindung zu sich selbst herstellen können, um insbesondere den Export von Berichten im PDF-Format zu ermöglichen.

1. Im **[!UICONTROL Sprache]** Dropdown-Liste, wählen Sie die **Instanzensprache**: Englisch (US), Englisch (UK), Französisch oder Japanisch.

   Unterschiede zwischen US-amerikanischem Englisch und britischem Englisch werden im Abschnitt [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Die Instanzsprache kann nach diesem Schritt nicht mehr geändert werden. Adobe Campaign-Instanzen sind nicht mehrsprachig: Sie können die Benutzeroberfläche nicht von einer Sprache in eine andere wechseln.

1. Klicken **[!UICONTROL Ok]** zur Bestätigung der Instanzdeklaration. Melden Sie sich ab und wieder an, um die Datenbank zu deklarieren.

   >[!NOTE]
   >
   >Die Instanz kann über die Befehlszeile erstellt werden. Weitere Informationen hierzu finden Sie unter [Befehlszeilen](../../installation/using/command-lines.md).
