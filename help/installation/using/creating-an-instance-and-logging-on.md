---
product: campaign
title: Instanz erstellen und anmelden
description: Instanz erstellen und anmelden
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 9%

---

# Instanz erstellen und anmelden{#creating-an-instance-and-logging-on}



Gehen Sie wie folgt vor, um eine neue Instanz und eine neue Adobe Campaign-Datenbank zu erstellen:

1. Erstellen Sie die Verbindung.
1. Melden Sie sich an, um die zugehörige Instanz zu erstellen.
1. Erstellen und Konfigurieren der Datenbank.

>[!NOTE]
>
>Nur die **interne** Kennung kann diese Vorgänge ausführen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

Beim Starten der Adobe Campaign-Konsole greifen Sie auf eine Anmeldeseite zu.

Gehen Sie wie folgt vor, um eine neue Instanz zu erstellen:

1. Klicken Sie auf den Link in der oberen rechten Ecke der Felder mit den Anmeldedaten, um auf das Fenster für die Verbindungskonfiguration zuzugreifen. Dieser Link kann entweder **[!UICONTROL Neu…]** oder ein vorhandener Instanzname sein.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungs-Servers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie per URL eine Verbindung zum Adobe Campaign-Anwendungs-Server an. Verwenden Sie entweder einen DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise eine URL vom Typ `https://<machine>.<domain>.com` eingeben.

   >[!CAUTION]
   >
   >Verwenden Sie für die Verbindungs-URL nur die folgenden Zeichen: `[a-z]`, `[A-Z]`, `[0-9]` und Bindestriche (-) oder Punkt.

1. Klicken Sie **[!UICONTROL OK]**, um die Einstellungen zu bestätigen: Sie können jetzt mit dem Prozess zur Instanzerstellung beginnen.
1. Geben Sie im Fenster **[!UICONTROL Verbindungseinstellungen]** den **internen** Anmeldenamen und dessen Kennwort ein, um eine Verbindung zum Adobe Campaign-Anwendungsserver herzustellen. Sobald die Verbindung hergestellt ist, greifen Sie auf den Assistenten zur Instanzerstellung zu, um eine neue Instanz zu deklarieren
1. Geben Sie **[!UICONTROL Feld]** den **Instanznamen** ein. Da dieser Name zum Generieren einer Konfigurationsdatei (**-`<instance>`.xml) verwendet** und in den Befehlszeilenparametern zur Identifizierung der Instanz verwendet wird, stellen Sie sicher, dass Sie einen kurzen Namen ohne Sonderzeichen auswählen. Beispiel: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Der Name der zum Domain-Namen hinzugefügten Instanz darf 40 Zeichen nicht überschreiten. Dadurch können Sie die Größe der „Message-ID“-Header einschränken und verhindern, dass Nachrichten als Spam eingestuft werden, insbesondere durch Tools wie SpamAssassin.

1. Geben Sie in **[!UICONTROL DNS]** Masken) die **Liste der DNS-Masken** ein, an die die Instanz angehängt werden soll. Der Adobe Campaign-Server verwendet den Host-Namen, der in den HTTP-Anfragen angezeigt wird, um zu bestimmen, welche Instanz erreicht werden soll.

   Der Hostname befindet sich zwischen der Zeichenfolge **https://** und dem ersten Schrägstrich **/** der Serveradresse.

   Sie können eine Liste von Werten definieren, die durch Kommas getrennt sind.

   Die ? und &#42; Zeichen können als Platzhalter verwendet werden, um ein oder mehrere Zeichen (DNS, Port usw.) zu ersetzen. Beispielsweise funktioniert der Wert **demo&#42;** mit &quot;https://demo&quot; genauso wie mit &quot;https://demo:8080&quot; und sogar &quot;https://demo2&quot;.

   Die verwendeten Namen müssen in Ihrem DNS definiert sein. Sie können auch die Korrespondenz zwischen einem DNS-Namen und einer IP-Adresse in der Datei **c:/windows/system32/drivers/etc/hosts** in Windows und in der Datei **/etc/hosts** in Linux mitteilen. Sie müssen daher die Verbindungseinstellungen so ändern, dass dieser DNS-Name verwendet wird, um eine Verbindung zu der ausgewählten Instanz herzustellen.

   Der Server muss mit diesem Namen identifiziert werden, insbesondere für das Hochladen von Bildern in E-Mails.

   Darüber hinaus muss der Server in der Lage sein, über diesen Namen und nach Möglichkeit über eine Loopback-Adresse - 127.0.0.1 - eine Verbindung zu sich selbst herzustellen, insbesondere um den Export von Berichten im PDF-Format zu ermöglichen.

1. Wählen Sie in **[!UICONTROL Dropdown]** Liste Sprache die **Sprache der Instanz**: Englisch (US), Englisch (UK), Französisch oder Japanisch.

   Die Unterschiede zwischen Englisch (USA) und Englisch (Großbritannien) werden in der Dokumentation [Campaign v8 (Konsole)) ] (.https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/new/campaign-ui).

   >[!CAUTION]
   >
   >Die Sprache der Instanz kann nach diesem Schritt nicht mehr geändert werden. Adobe Campaign-Instanzen sind nicht mehrsprachig: Sie können die Benutzeroberfläche von einer Sprache nicht in eine andere wechseln.

1. Klicken Sie **[!UICONTROL OK]**, um die Instanzdeklaration zu bestätigen. Melden Sie sich ab und wieder an, um die Datenbank zu deklarieren.

   >[!NOTE]
   >
   >Die Instanz kann über die Befehlszeile erstellt werden. Weitere Informationen hierzu finden Sie unter [Befehlszeilen](../../installation/using/command-lines.md).
