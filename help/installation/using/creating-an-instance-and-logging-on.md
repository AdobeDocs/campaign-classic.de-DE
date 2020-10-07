---
title: Erstellen einer Instanz und Anmelden
seo-title: Erstellen einer Instanz und Anmelden
description: Erstellen einer Instanz und Anmelden
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 4%

---


# Erstellen einer Instanz und Anmelden{#creating-an-instance-and-logging-on}

Um eine neue Instanz und eine neue Adobe Campaign-Datenbank zu erstellen, führen Sie den folgenden Vorgang aus:

1. Erstellen Sie die Verbindung.
1. Melden Sie sich an, um die zugehörige Instanz zu erstellen.
1. Erstellen und konfigurieren Sie die Datenbank.

>[!NOTE]
>
>Diese Vorgänge können nur vom **internen** Bezeichner ausgeführt werden. For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

Beim Starten der Adobe Campaign-Konsole greifen Sie auf eine Anmeldeseite zu.

Gehen Sie wie folgt vor, um eine neue Instanz zu erstellen:

1. Klicken Sie auf den Link in der oberen rechten Ecke der Felder mit den Anmeldeinformationen, um das Fenster für die Verbindungskonfiguration aufzurufen. Dieser Link kann entweder **[!UICONTROL Neu...]** oder einen vorhandenen Instanznamen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und die URL des Adobe Campaign-Anwendungsservers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie über eine URL eine Verbindung zum Adobe Campaign-Anwendungsserver an. Verwenden Sie entweder ein DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise die URL des [`https://<machine>.<domain>.com`](https://machine) Typs verwenden.

   >[!CAUTION]
   >
   >Verwenden Sie für die Verbindungs-URL nur die folgenden Zeichen: `[a-z]`, `[A-Z]`und `[0-9]` Bindestriche (-) oder Vollstopps.

1. Klicken Sie auf **[!UICONTROL OK]** , um die Einstellungen zu bestätigen: Sie können jetzt mit dem Instanzerstellungsprozess beginnen.
1. Geben Sie im Fenster &quot; **[!UICONTROL Verbindungseinstellungen]** &quot;die **interne** Anmeldung und das zugehörige Kennwort ein, um eine Verbindung zum Adobe Campaign-Anwendungsserver herzustellen. Nach der Verbindung können Sie auf den Instanzerstellungsassistenten zugreifen, um eine neue Instanz zu deklarieren
1. Geben Sie im Feld **[!UICONTROL Name]** den **Instanznamen** ein. Da dieser Name zum Generieren einer Konfigurationsdatei &quot; **config-`<instance>`.xml** &quot;verwendet wird und in den Befehlszeilenparametern zur Identifizierung der Instanz verwendet wird, müssen Sie einen kurzen Namen ohne Sonderzeichen wählen. Beispiel: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Der Name der Instanz, die dem Domänennamen hinzugefügt wird, darf 40 Zeichen nicht überschreiten. Dadurch können Sie die Größe von &quot;Message-ID&quot;-Headern einschränken und verhindern, dass Nachrichten als Spam betrachtet werden, insbesondere von Tools wie SpamAssassin.

1. Geben Sie in die Felder **[!UICONTROL DNS-Masken]** die **Liste der DNS-Masken** ein, an die die Instanz angehängt werden soll. Der Adobe Campaign-Server verwendet den Hostnamen, der in den HTTP-Anforderungen angezeigt wird, um zu bestimmen, welche Instanz erreicht werden soll.

   Der Hostname befindet sich zwischen der Zeichenfolge **https://** und dem ersten Schrägstrich **/** der Serveradresse.

   Sie können eine Liste von Werten definieren, die durch Kommas getrennt sind.

   Nach der Validierung werden am Ende der eingegebenen URL automatisch die Zeichen ? und *-Zeichen können als Platzhalter verwendet werden, um ein oder mehrere Zeichen (DNS, Anschluss usw.) zu ersetzen. Der **demo*** -Wert funktioniert z. B. mit &quot;https://demo&quot;, wie auch mit &quot;https://demo:8080&quot; und sogar &quot;https://demo2&quot;.

   Die verwendeten Namen müssen im DNS definiert werden. Sie können auch die Korrespondenz zwischen einem DNS-Namen und einer IP-Adresse in der Datei **c:/windows/system32/drivers/etc/hosts** unter Windows und in der Datei **/etc/hosts** unter Linux angeben. Sie müssen daher die Verbindungseinstellungen ändern, um diesen DNS-Namen zu verwenden, um eine Verbindung zu Ihrer ausgewählten Instanz herzustellen.

   Der Server muss mit diesem Namen identifiziert werden, insbesondere zum Hochladen von Bildern in E-Mails.

   Darüber hinaus muss der Server mit diesem Namen und, wenn möglich, mit einer Loopback-Adresse - 127.0.0.1 - in der Lage sein, eine Verbindung zu sich selbst herzustellen, um insbesondere zu ermöglichen, dass Berichte im PDF-Format exportiert werden können.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Sprache]** die **Instanzsprache** aus: Englisch (USA), Englisch (Großbritannien), Französisch oder Japanisch.

   Die Unterschiede zwischen Englisch und Englisch in den USA werden in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#date-and-time)beschrieben.

   >[!CAUTION]
   >
   >Die Instanzsprache kann nach diesem Schritt nicht mehr geändert werden. Adobe Campaign-Instanzen sind nicht mehrsprachig: Sie können die Benutzeroberfläche nicht von einer Sprache in eine andere wechseln.

1. Klicken Sie auf **[!UICONTROL OK]** , um die Instanz-Deklaration zu bestätigen. Melden Sie sich ab und wieder an, um die Datenbank zu deklarieren.

   >[!NOTE]
   >
   >Die Instanz kann über die Befehlszeile erstellt werden. For more on this, refer to [Command lines](../../installation/using/command-lines.md).

