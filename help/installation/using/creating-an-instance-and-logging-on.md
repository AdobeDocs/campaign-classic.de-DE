---
product: campaign
title: Instanz erstellen und anmelden
description: Instanz erstellen und anmelden
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 9%

---

# Instanz erstellen und anmelden{#creating-an-instance-and-logging-on}



Gehen Sie wie folgt vor, um eine neue Instanz und eine neue Adobe Campaign-Datenbank zu erstellen:

1. Erstellen Sie die Verbindung.
1. Melden Sie sich an, um die zugehörige Instanz zu erstellen.
1. Erstellen und konfigurieren Sie die Datenbank.

>[!NOTE]
>
>Nur der **interne** Bezeichner kann diese Vorgänge ausführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

Wenn die Adobe Campaign Konsole gestartet wird, greifen Sie auf eine Log-in Seite zu.

Gehen Sie folgen wie folgt vor, um eine neue Instanz zu erstellen:

1. Klicken Sie auf das verknüpfen in der oberen rechten Ecke der Anmeldedatenfelder, um auf das Fenster für die Verbindungskonfiguration zuzugreifen. Dieser Link kann entweder **[!UICONTROL Neu…]** oder ein vorhandener Instanzname sein.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungs-Servers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie per URL eine Verbindung zum Adobe Campaign-Anwendungs-Server an. Verwenden Sie entweder einen DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise eine URL vom Typ `https://<machine>.<domain>.com` eingeben.

   >[!CAUTION]
   >
   >Verwenden Sie für die Verbindung URL nur folgende Zeichen: `[a-z]`, `[A-Z]`, `[0-9]` und Bindestriche (-) oder Punkte.

1. Klicken Sie auf **[!UICONTROL &quot;OK]** &quot;, um die Einstellungen zu bestätigen: Sie können jetzt mit der Instanz Erstellung beginnen.
1. Geben Sie im Fenster Verbindung **[!UICONTROL Einstellungen]** den **internen** Log-in und dessen Kennwort ein, um eine Verbindung zum Adobe Campaign Applikation-Server herzustellen. Sobald die Verbindung hergestellt ist, greifen Sie auf den Erstellungsassistenten für Instanz zu, um eine neue Instanz zu deklarieren
1. Geben Sie in das **[!UICONTROL Feld &quot;Name]** &quot; den **Instanz** Namen ein. Da dieser Name zum Generieren einer Konfigurationsdatei **config-`<instance>`.xml** verwendet wird und in den Befehlszeilenparametern verwendet wird, um die Instanz zu identifizieren, stellen Sie sicher, dass Sie einen Kurznamen ohne Sonderzeichen wählen. Beispiel: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Der Name der Instanz, die dem Domänennamen hinzugefügt wird, darf nicht länger als 40 Zeichen sein. Auf diese Weise können Sie die Größe von &quot;Message-ID&quot;-Headern begrenzen und verhindern, dass Nachrichten als Spam betrachtet werden, insbesondere von Tools wie SpamAssassin.

1. Geben Sie in den **[!UICONTROL Feldern DNS-Masken die** Liste der DNS-Masken **]** ein, an die die Instanz angehängt werden soll. Der Adobe Campaign-Server verwendet den Host-Namen, der in den HTTP-Anfragen angezeigt wird, um zu bestimmen, welche Instanz erreicht werden soll.

   Der Hostname befindet sich zwischen der Zeichenfolge **https://** und dem ersten Schrägstrich **/** der Serveradresse.

   Sie können eine Liste von Werten definieren, die durch Kommas getrennt sind.

   Die ? und &#42; Zeichen können als Platzhalter verwendet werden, um ein oder mehrere Zeichen zu ersetzen (DNS, portieren usw.). Bei Instanz funktioniert der **Demowert&#42;** mit &quot;https://demo&quot; ebenso wie mit &quot;https://demo:8080&quot; und Linear &quot;https://demo2&quot;.

   Die verwendeten Namen müssen in Ihrem DNS definiert werden. Sie können die Entsprechung zwischen einem DNS-Namen und einer IP-Adresse auch in der **Datei c:/windows/system32/drivers/etc/hosts** unter Windows und in der **Datei /etc/hosts** unter Linux angeben. Sie müssen daher die Verbindungseinstellungen ändern, um diesen DNS-Namen zu verwenden, bestellen eine Verbindung zu Ihrem ausgewählten Instanz herzustellen.

   Der Server muss insbesondere beim Hochladen von Bildern in E-Mails mit diesem Namen identifiziert werden.

   Darüber hinaus muss der Server in der Lage sein, sich mit diesem Namen und, wenn möglich, mit einer Loopback-Adresse - 127.0.0.1 - zu verbinden, insbesondere um den Export von Berichten im PDF-Format zu ermöglichen.

1. Wählen Sie in der **[!UICONTROL Dropdown-Liste Sprache]** die **Instanz Sprache** aus: Englisch (USA), Englisch (Großbritannien), Französisch oder Japanisch.

   Die Unterschiede zwischen Englisch (USA) und Englisch (Großbritannien) werden in [ Abschnitt beschrieben](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Die Sprache der Instanz kann nach diesem Schritt nicht mehr geändert werden. Adobe Campaign-Instanzen sind nicht mehrsprachig: Sie können die Benutzeroberfläche von einer Sprache nicht in eine andere wechseln.

1. Klicken Sie **[!UICONTROL OK]**, um die Instanzdeklaration zu bestätigen. Melden Sie sich ab und wieder an, um die Datenbank zu deklarieren.

   >[!NOTE]
   >
   >Die Instanz kann über die Befehlszeile erstellt werden. Weitere Informationen hierzu finden Sie in den [Befehl Zeilen](../../installation/using/command-lines.md).
