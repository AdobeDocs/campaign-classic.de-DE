---
product: campaign
title: SMS-Kanal von Campaign in einer Mid-Sourcing-Infrastruktur konfigurieren
description: Erfahren Sie, wie Sie den SMS-Kanal in Campaign in einer Mid-Sourcing-Infrastruktur konfigurieren
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: SMS
role: User, Developer, Admin
source-git-commit: 4165f5988dfeee2f3b4d872c445ace11c9aa4fe1
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 45%

---

# SMS-Kanal in einer Mid-Sourcing-Infrastruktur konfigurieren {#setting-up-sms-channel}

Folgende Voraussetzungen müssen gegeben sein, um mit Mid-Server an ein Mobiltelefon zu senden:

1. Ein SMS-Operator , der auf dem Mid-Server erstellt wurde, der für das externe SMS-Konto verwendet wird, das auf dem Marketing-Server erstellt wurde.

1. Ein externes Konto auf dem Marketing-Server, das den Kanal und den Versandmodus angibt.

1. Ein externes Konto auf dem Mid-Server, in dem der Connector und der Nachrichtentyp detailliert aufgeführt sind.

1. Eine Versandvorlage, die auf das externe Konto verweist, um den Versandprozess zu optimieren.

>[!NOTE]
>
> Für SMS-Sendungen sollte die Typologie eine bestimmte SMS-Affinität verwenden, die in **einem** dedizierten Anwendungs-Server-Container erstellt wurde. [Weitere Informationen](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## Erstellen des SMS-Operators auf dem Mid-Server {#create-sms-operator}

Um den Konfigurationsprozess zu starten, müssen Sie auf dem Mid-Server einen SMS-Operator speziell für das externe Konto erstellen.

>[!IMPORTANT]
>
>Jeder SMS-Connector benötigt einen eindeutigen SMS-Operator.

1. Im **[!UICONTROL Administration]** > **[!UICONTROL Zugriffsverwaltung]** > **[!UICONTROL Benutzerknoten]** Knoten des Baums, klicken Sie auf die **[!UICONTROL Neu]** Symbol.

   ![](assets/sms_operator_mid_3.png)

1. Geben Sie die **[!UICONTROL Identifizierungsparameter]**, einschließlich Login, Passwort und Name. Login und Passwort sind erforderlich, damit sich der Benutzer sicher bei Adobe Campaign anmelden kann.

   Beachten Sie Folgendes: **[!UICONTROL Name (login)]** wird später verwendet, um Ihr externes SMPP-Konto im Mid-Server zu benennen.

   ![](assets/sms_operator_mid_1.png)

1. Wählen Sie die dem Benutzer erteilten Berechtigungen im Abschnitt Zugriffsberechtigungen des Benutzers aus.

   Um dem Benutzer Berechtigungen zuzuweisen, klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** oberhalb der Liste der Berechtigungen. Wählen Sie als Nächstes eine **[!UICONTROL Benutzergruppe]** oder **[!UICONTROL Spezifische Berechtigungen]** aus der verfügbaren Gruppenliste.

   ![](assets/sms_operator_mid_2.png)

1. Klicks **[!UICONTROL Speichern]** , um die Erstellung des Benutzers abzuschließen. Das Profil ist jetzt in der Liste der existierenden Benutzer enthalten.

## Externes SMS-Konto auf dem Marketing-Server erstellen {#create-accound-mkt}

Um eine SMS mit Mid-Servern an ein Mobiltelefon zu senden, müssen Sie zunächst Ihr externes SMS-Konto auf dem Marketing-Server erstellen.

1. Wählen Sie dazu im Navigationsbaum im Knoten **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]** das Symbol **[!UICONTROL Neu]** aus.

   ![](assets/mid_external_account_2.png)

1. Geben Sie Ihre **[!UICONTROL Titel]** und **[!UICONTROL Interner Name]**. Beachten Sie, dass der interne Name später verwendet werden soll, um Ihr externes SMPP-Konto im Mid-Server zu benennen.

1. Definieren Sie den Kontotyp als **[!UICONTROL Routing]**, den Kanal als **[!UICONTROL Mobiltelefon (SMS)]** und im Versandmodus **[!UICONTROL Mid-Sourcing]**.

   ![](assets/mid_external_account_1.png)

1. Im **[!UICONTROL Mid-Sourcing]** auf, geben Sie die Mid-Sourcing-Server-Verbindungsparameter an.

   Geben Sie die Details der [zuvor erstellter SMS-Connector](#create-sms-operator) im **[!UICONTROL Konto]** und **[!UICONTROL Passwort]** -Felder.

   ![](assets/mid_external_account_7.png)

1. Bestätigen Sie Ihre Konfiguration durch Klicken auf **[!UICONTROL Verbindung testen]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Erstellen eines externen SMPP-Kontos auf dem Mid-Server {#creating-smpp-mid}

>[!IMPORTANT]
>
>Die Verwendung desselben Kontos und Kennworts für mehrere externe SMS-Konten kann zu Konflikten und Überschneidungen zwischen den Konten führen. Siehe die [Seite zur SMS-Fehlerbehebung](troubleshooting-sms.md#external-account-conflict).

Nachdem Sie Ihr externes SMS-Konto erfolgreich auf dem Marketing-Server eingerichtet haben, besteht der nächste Schritt darin, Ihr externes SMPP-Konto auf dem Mid-Server einzurichten.

Weiterführende Informationen zum SMS-Protokoll und dessen Einstellungen finden Sie auf dieser [Seite](sms-protocol.md).

Gehen Sie dazu wie folgt vor:

1. Wählen Sie dazu im Navigationsbaum im Knoten **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]** das Symbol **[!UICONTROL Neu]** aus.

1. Geben Sie Ihre **[!UICONTROL Titel]** und **[!UICONTROL Interner Name]**.

   >[!WARNING]
   >
   >Beim Zuweisen eines **[!UICONTROL Interner Name]**müssen Sie die angegebene Namenskonvention befolgen:
   > </br>`SMS Operator Name_Internal Name of the Marketing SMS external account`

   ![](assets/mid_external_account_6.png)

1. Definieren Sie den Kontotyp mit **Routing**, den Kanal mit **Mobiltelefon (SMS)** und den Versandmodus mit **Gebündelter Versand**.

   ![](assets/mid_external_account_3.png)

1. Kreuzen Sie die Option **[!UICONTROL Aktiviert]** an.

1. Wählen Sie im Tab **[!UICONTROL Mobiltelefon]** aus der **[!UICONTROL Connector]**-Dropdown-Liste die Option **[!UICONTROL Erweitertes allgemeines SMPP]**.

   ![](assets/mid_external_account_4.png)

1. Die **[!UICONTROL Ausführliche SMPP-Verfolgung in Logdatei aktivieren]** -Option können Sie den gesamten SMPP-Traffic in Logdateien speichern. Diese Option sollte nur aktiviert sein, um Fehler im Connector zu beheben und einen Vergleich mit dem vom Provider aufgezeichneten Traffic anzustellen.

1. Wenden Sie sich an Ihren SMS-Dienstleister. Dieser kann Ihnen die für das externe Konto erforderlichen Angaben auf dem Tab **[!UICONTROL Verbindungsparameter]** bereitstellen.

   Der von Ihnen ausgewählte Provider nennt Ihnen danach den Wert für das Feld **[!UICONTROL Name der SMSC-Implementierung]**.

   Sie können die Anzahl der Verbindungen mit dem Dienstleister per untergeordnetem MTA definieren. Standardmäßig ist 1 eingestellt.

1. Standardmäßig kommt in Bezug auf die maximal zulässige Zeichenanzahl einer SMS der Mobilfunkstandard GSM zur Anwendung.

   SMS, die das GSM-Alphabet verwenden, sind auf 160 Zeichen begrenzt oder auf 153 Zeichen pro SMS bei Nachrichten, die in mehreren Teilen gesendet werden.

   >[!NOTE]
   >
   >Gewisse Zeichen zählen doppelt (Akkoladen, eckige Klammern, Eurozeichen etc.).
   >
   >Die Liste der verfügbaren GSM-Zeichen finden Sie unter [diesem Abschnitt](sms-set-up.md#about-character-transliteration).

   Sie können auch die Transliteration von Zeichen zulassen, indem Sie die entsprechende Option ankreuzen.

   ![](assets/mid_external_account_5.png)

1. Im Tab **[!UICONTROL Durchsatz und Dauer]** können Sie den maximalen Durchsatz für ausgehende Nachrichten (&quot;MT&quot;, Mobile Terminated) festlegen. Bei Angabe von &quot;0&quot; im entsprechenden Feld ist der Durchsatz unbegrenzt.

   Werte, die eine Dauer angeben, sind in Sekunden auszudrücken.

1. Im Tab **[!UICONTROL Kodierungs-Mapping]** können Sie Kodierungen definieren.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](sms-set-up.md#about-text-encodings).

1. Im Tab **[!UICONTROL SMSC-Besonderheiten]** ist die Option **[!UICONTROL Vollständige Telefonnummer senden]** standardmäßig deaktiviert. Aktivieren Sie sie nicht, wenn Sie die Konformität mit dem SMPP-Protokoll wahren und nur Zahlen an den Server des SMS-Anbieters (SMSC) übertragen möchten.

   Bei gewissen Anbietern ist die Verwendung des Vorzeichens &#39;+&#39; jedoch erforderlich, sodass es ratsam ist, mit Ihrem Anbieter Kontakt aufzunehmen, der Sie bei Bedarf dazu auffordern wird, diese Option zu aktivieren.

   Die Checkbox **[!UICONTROL TLS über SMPP aktivieren]** ermöglicht die Verschlüsselung des SMPP-Traffics. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](sms-protocol.md).

1. Wenn Sie einen Connector vom Typ **[!UICONTROL Erweitertes allgemeines SMPP]** konfigurieren, können Sie automatische Antworten einrichten.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](sms-set-up.md#automatic-reply).

## Versandvorlage ändern {#changing-the-delivery-template}

Adobe Campaign bietet eine mobile Versandvorlage im **[!UICONTROL Ressourcen > Vorlagen > Versandvorlagen]** Knoten. Weiterführende Informationen finden Sie im Abschnitt [Über Vorlagen](about-templates.md).

Um Nachrichten über den SMS-Kanal zu senden, müssen Sie eine Vorlage erstellen, die einen Verweis auf den Kanal-Connector enthält.

Um die native Versandvorlage beizubehalten, wird empfohlen, sie zu duplizieren und dann zu konfigurieren.

Im folgenden Beispiel wird eine Vorlage generiert, die den Versand von Nachrichten über das zuvor erstellte SMPP-Konto erleichtert. Gehen Sie dazu wie folgt vor:

1. Im **[!UICONTROL Ressourcen]** > **[!UICONTROL Vorlagen]** > **[!UICONTROL Versandvorlagen]** Knoten des Baums, klicken Sie mit der rechten Maustaste auf die **[!UICONTROL Mobiltelefon-Versand]** und wählen Sie **[!UICONTROL Duplizieren]**.

   ![](assets/delivery_template_mid_1.png)

1. Ändern Sie die Beschriftung der Vorlage, z. B. **Mobiltelefon-Versand (SMPP)**.

   ![](assets/delivery_template_mid_2.png)

1. Klicken Sie auf **[!UICONTROL Eigenschaften]**.

1. Im **[!UICONTROL Allgemein]** wählen Sie einen Routing-Modus aus, der dem externen Konto entspricht, das Sie im Abschnitt erstellt haben. [Externes SMS-Konto auf dem Marketing-Server erstellen](#create-accound-mkt).

   ![](assets/delivery_template_mid_3.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Erstellung abzuschließen.

   ![](assets/delivery_template_mid_4.png)

Sie verfügen nun über ein externes Konto und eine Versandvorlage, die es Ihnen erlauben, per SMS zu versenden.

## Verwandte Themen {#related-topics}

* [Transliteration von SMS-Zeichen](sms-set-up.md#about-character-transliteration)
* [Textcodierungen](sms-set-up.md#about-text-encodings)
* [Automatische Antwort](sms-set-up.md#automatic-reply)

