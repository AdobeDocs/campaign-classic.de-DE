---
solution: Campaign Classic
product: campaign
title: Erstellen einer Instanz und Anmelden
description: Erstellen einer Instanz und Anmelden
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 5%

---

# Erstellen einer Instanz und Anmelden{#creating-an-instance-and-logging-on}

Um eine neue Instanz und eine neue Adobe Campaign-Datenbank zu erstellen, führen Sie den folgenden Vorgang aus:

1. Erstellen Sie die Verbindung.
1. Melden Sie sich an, um die zugehörige Instanz zu erstellen.
1. Datenbank erstellen und konfigurieren.

>[!NOTE]
>
>Diese Vorgänge können nur vom Bezeichner **internal** ausgeführt werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

Beim Starten der Adobe Campaign-Konsole greifen Sie auf eine Anmeldeseite zu.

Gehen Sie wie folgt vor, um eine neue Instanz zu erstellen:

1. Klicken Sie auf den Link in der oberen rechten Ecke der Felder mit den Anmeldeinformationen, um das Fenster für die Verbindungskonfiguration aufzurufen. Dieser Link kann entweder **[!UICONTROL Neu...]** oder einen vorhandenen Instanznamen.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicken Sie auf **[!UICONTROL Hinzufügen > Verbindung]** und geben Sie die Bezeichnung und URL des Adobe Campaign-Anwendungsservers ein.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Geben Sie über eine URL eine Verbindung zum Adobe Campaign-Anwendungsserver an. Verwenden Sie entweder ein DNS oder einen Alias des Computers oder Ihre IP-Adresse.

   Sie können beispielsweise die URL [`https://<machine>.<domain>.com`](https://myserver.adobe.com) eingeben.

   >[!CAUTION]
   >
   >Verwenden Sie für die Verbindungs-URL nur die folgenden Zeichen: `[a-z]`, `[A-Z]`, `[0-9]` und Bindestriche (-) oder vollständige Haltestellen.

1. Klicken Sie auf **[!UICONTROL OK]**, um die Einstellungen zu bestätigen: Sie können jetzt mit dem Instanzerstellungsprozess beginnen.
1. Geben Sie im Fenster **[!UICONTROL Verbindungseinstellungen]** die **interne**-Anmeldung und das zugehörige Kennwort ein, um eine Verbindung zum Adobe Campaign-Anwendungsserver herzustellen. Nach der Verbindung können Sie auf den Instanzerstellungsassistenten zugreifen, um eine neue Instanz zu deklarieren
1. Geben Sie im Feld **[!UICONTROL Name]** den Instanznamen **a3/> ein.** Da dieser Name zum Generieren einer Konfigurationsdatei **config-`<instance>`.xml** verwendet wird und in den Befehlszeilenparametern zum Identifizieren der Instanz verwendet wird, müssen Sie einen Kurznamen ohne Sonderzeichen auswählen. Beispiel: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Der Name der Instanz, die dem Domänennamen hinzugefügt wird, darf 40 Zeichen nicht überschreiten. Dadurch können Sie die Größe von &quot;Message-ID&quot;-Headern einschränken und verhindern, dass Nachrichten als Spam betrachtet werden, insbesondere von Tools wie SpamAssassin.

1. Geben Sie in die Felder **[!UICONTROL DNS-Masken]** die **Liste der DNS-Masken** ein, an die die Instanz angehängt werden soll. Der Adobe Campaign-Server verwendet den Hostnamen, der in den HTTP-Anforderungen angezeigt wird, um zu bestimmen, welche Instanz erreicht werden soll.

   Der Hostname befindet sich zwischen der Zeichenfolge **https://** und dem ersten Schrägstrich **/** der Serveradresse.

   Sie können eine Liste von Werten definieren, die durch Kommas getrennt sind.

   Nach der Validierung werden am Ende der eingegebenen URL automatisch die Zeichen ? und *-Zeichen können als Platzhalter verwendet werden, um ein oder mehrere Zeichen (DNS, Anschluss usw.) zu ersetzen. Der Wert **demo*** funktioniert z. B. mit &quot;https://demo&quot; wie mit &quot;https://demo:8080&quot; und sogar mit &quot;https://demo2&quot;.

   Die verwendeten Namen müssen im DNS definiert werden. Sie können auch die Korrespondenz zwischen einem DNS-Namen und einer IP-Adresse in der Datei **c:/windows/system32/drivers/etc/hosts** unter Windows und in der Datei **/etc/hosts** unter Linux angeben. Sie müssen daher die Verbindungseinstellungen ändern, um diesen DNS-Namen zu verwenden, um eine Verbindung zu Ihrer ausgewählten Instanz herzustellen.

   Der Server muss mit diesem Namen identifiziert werden, insbesondere zum Hochladen von Bildern in E-Mails.

   Darüber hinaus muss der Server mit diesem Namen und, wenn möglich, mit einer Loopback-Adresse - 127.0.0.1 - in der Lage sein, eine Verbindung zu sich selbst herzustellen, um insbesondere zu ermöglichen, dass Berichte im PDF-Format exportiert werden können.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Language]** die **Instanzsprache** aus: Englisch (USA), Englisch (Großbritannien), Französisch oder Japanisch.

   Die Unterschiede zwischen Englisch (USA) und Englisch (Großbritannien) werden in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#date-and-time) beschrieben.

   >[!CAUTION]
   >
   >Die Instanzsprache kann nach diesem Schritt nicht mehr geändert werden. Adobe Campaign-Instanzen sind nicht mehrsprachig: Sie können die Benutzeroberfläche nicht von einer Sprache in eine andere wechseln.

1. Klicken Sie auf **[!UICONTROL OK]**, um die Instanz-Deklaration zu bestätigen. Melden Sie sich ab und wieder an, um die Datenbank zu deklarieren.

   >[!NOTE]
   >
   >Die Instanz kann über die Befehlszeile erstellt werden. Weitere Informationen finden Sie unter [Befehlszeilen](../../installation/using/command-lines.md).
