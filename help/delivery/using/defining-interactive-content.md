---
title: Definieren von interaktiven Inhalten in Adobe Campaign Classic
description: Erfahren Sie, wie Sie mit AMP interaktive und dynamische E-Mail-Inhalte in Adobe Campaign Classic definieren.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1815f9fc6063ec86d6c12ef492396e5afb82b3e1

---


# Definieren interaktiver Inhalte{#defining-interactive-content}

Mit Adobe Campaign können Sie das neue interaktive [AMP für E-Mail](https://amp.dev/about/email/) -Format ausprobieren, das das Senden dynamischer E-Mails unter bestimmten Bedingungen ermöglicht.

>[!IMPORTANT]
>
>* Diese Funktion ist eine Betafunktion in Adobe Campaign.
>* AMP for Email ist ein neues Open-Source-Format, mit dem Entwickler dynamische und interaktive E-Mails erstellen können. Derzeit wird es von einigen E-Mail-Anbietern unterstützt: Gmail, Outlook und Mail.ru.


Derzeit können Sie nur:
* Testen Sie die Bereitstellung von AMP-E-Mails an bestimmte, entsprechend konfigurierte Adressen.
* Senden Sie AMP-E-Mails an die Adressen von Gmail, Outlook oder Mail.ru, nachdem Sie sich bei den entsprechenden Anbietern registriert haben.

Weitere Informationen zum Testen und Senden von AMP-E-Mails finden Sie unter [Targeting einer AMP-E-Mail](#targeting-amp-email).

Diese Funktion ist über ein dediziertes Paket in Adobe Campaign verfügbar. Um es zu verwenden, muss dieses Paket installiert sein. Starten Sie nach Abschluss des Vorgangs den Server neu, damit das Paket berücksichtigt wird.

Bei Hybrid- und gehosteten Architekturen muss das Paket auf allen Servern installiert sein, einschließlich des [Mid-Sourcing-Servers](../../installation/using/mid-sourcing-server.md) und der [Ausführungsinstanz](../../message-center/using/creating-a-shared-connection.md#execution-instance). Wenden Sie sich an Ihren Kundenbetreuer.

In diesem [Video](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html) erfahren Sie, wie Sie AMP in Adobe Campaign aktivieren und wie Sie die Verwendung von AMP nutzen.

## Informationen zu AMP für E-Mail {#about-amp-for-email}

Das neue **AMP für E-Mail** -Format ermöglicht es, AMP-Komponenten in Nachrichten einzuschließen, um die E-Mail-Erfahrung mit komplexen und umsetzbaren Inhalten zu verbessern. Mit modernen App-Funktionen, die direkt in E-Mails verfügbar sind, können Empfänger dynamisch mit Inhalten in der Nachricht selbst interagieren.

Beispiel:
* Mit AMP geschriebene E-Mails können interaktive Elemente wie Bildkarussells enthalten.
* Der Inhalt bleibt in der Nachricht auf dem neuesten Stand.
* Die Empfänger können beispielsweise auf ein Formular reagieren, ohne den Posteingang zu verlassen.

AMP für E-Mail ist mit vorhandenen E-Mails kompatibel. Die AMP-Version der Nachricht wird als neuer MIME-Teil in die E-Mail eingebettet, zusätzlich zum HTML- und/oder Nur-Text, sodass die Kompatibilität für alle E-Mail-Clients gewährleistet ist.

Weitere Informationen zum AMP für E-Mail-Format, Spezifikationen und Anforderungen finden Sie in der [AMP-Entwicklerdokumentation](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

## Wichtige Schritte zur Verwendung von AMP für E-Mail mit Adobe Campaign {#key-steps-to-use-amp}

Gehen Sie wie folgt vor, um eine AMP-E-Mail mit Adobe Campaign erfolgreich zu testen und zu senden:
1. Install the **[!UICONTROL AMP support (Beta)]** package. Siehe [Installieren von Campaign-Standardpaketen](../../installation/using/installing-campaign-standard-packages.md).
1. Erstellen Sie eine E-Mail und erstellen Sie Ihren AMP-Inhalt in Adobe Campaign. Siehe [Erstellen von AMP-E-Mail-Inhalten mit Adobe Campaign](#build-amp-email-content).
1. Vergewissern Sie sich, dass Sie alle Bereitstellungsanforderungen der E-Mail-Anbieter, die das AMP-Format unterstützen, befolgen. Anforderungen für die E-Mail-Zustellung finden Sie unter [AMP](#amp-for-email-delivery-requirements).

   >[!NOTE]
   >
   >AMP für E-Mail ist als Beta-Funktion für Testzwecke verfügbar. Derzeit unterstützen nur wenige E-Mail-Anbieter Tests in diesem Format.

1. Stellen Sie beim Definieren Ihres Ziels sicher, dass Sie Empfänger auswählen, die das AMP-Format anzeigen können. Siehe [Targeting einer AMP-E-Mail](#targeting-amp-email).

   >[!NOTE]
   >
   >Derzeit können Sie die Bereitstellung von AMP-E-Mails an bestimmte E-Mail-Adressen, die entsprechend konfiguriert wurden, oder nach der Registrierung bei den am AMP-Betaprogramm teilnehmenden E-Mail-Anbietern nur testen.

1. Senden Sie Ihre E-Mail wie gewohnt. Siehe [Senden einer AMP-E-Mail](#sending-amp-email).

## Erstellen von AMP-E-Mail-Inhalten in Adobe Campaign {#build-amp-email-content}

Gehen Sie wie unten beschrieben vor, um eine E-Mail im AMP-Format zu erstellen.

>[!IMPORTANT]
>
>Achten Sie darauf, dass Sie die in der [AMP-Entwicklerdokumentation](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)beschriebenen AMP-Anforderungen und -Spezifikationen befolgen. Die Best Practices[für E-Mails finden Sie auch im ](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)AMP.

1. Wählen Sie beim Erstellen Ihrer E-Mail-Auslieferung eine beliebige Vorlage aus.

   >[!NOTE]
   >
   >Eine bestimmte AMP-Vorlage enthält ein Beispiel für die Hauptkapazitäten, die Sie verwenden können: Produktliste, Karussell, doppelte Teilnahme, Umfrage und erweiterte Serveranforderung.

1.  Klicken Sie auf die **[!UICONTROL AMP content]** Registerkarte.

   ![](assets/amp_tab.png)

1. Bearbeiten Sie den AMP-Inhalt entsprechend Ihren Anforderungen.

   >[!NOTE]
   >
   >Weitere Informationen zum Erstellen der ersten AMP-E-Mail finden Sie in der [AMP-Entwicklerdokumentation](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   Beispielsweise können Sie die Produktlistenkomponente aus der AMP-Vorlage verwenden und eine Liste der Produkte eines Drittanbietersystems oder sogar innerhalb von Adobe Campaign verwalten. Wenn Sie einen Preis oder ein anderes Element anpassen, wird er automatisch angezeigt, wenn der Empfänger die E-Mail erneut aus seinem Postfach öffnet.

1. Personalisieren Sie Ihren AMP-Inhalt nach Bedarf, wie Sie es normalerweise mit dem HTML-Format in Adobe Campaign tun würden, mit Personalisierungsfeldern und Personalisierungsblöcken.

   ![](assets/amp_tab_perso.png)

1. Nachdem Sie die Bearbeitung abgeschlossen haben, wählen Sie den gesamten AMP-Inhalt aus und kopieren Sie ihn in den webbasierten [AMP-Validator](https://validator.ampproject.org) oder eine ähnliche Website.

   >[!NOTE]
   >
   >Wählen Sie **AMP4 EMAIL** aus der Dropdownliste oben auf dem Bildschirm.

   ![](assets/amp_validator.png)

   Alle Fehler werden inline gekennzeichnet.

   >[!NOTE]
   >
   >Der Adobe Campaign AMP-Editor ist nicht für die Inhaltsprüfung vorgesehen. Verwenden Sie eine externe Website, z. B. den webbasierten Validator[ für ](https://validator.ampproject.org)AMP, um zu prüfen, ob Ihre Inhalte korrekt sind.

1. Nehmen Sie die erforderlichen Änderungen vor, bis der AMP-Inhalt die Überprüfung besteht.

   ![](assets/amp_validator_pass.png)

1. Kopieren Sie Ihre validierten Inhalte in den [AMP-Playground](https://playground.amp.dev) oder eine ähnliche Website, um eine Vorschau Ihrer Inhalte anzuzeigen.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie in der Dropdownliste oben auf dem Bildschirm **AMP für E-Mail** auswählen.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Sie können Ihre AMP-Inhalte nicht direkt in Adobe Campaign anzeigen. Verwenden Sie eine externe Website wie [AMP Playground](https://playground.amp.dev).

1. Gehen Sie zurück zu Adobe Campaign und kopieren Sie den validierten Inhalt in die **[!UICONTROL AMP content]** Registerkarte.

1. Wechseln Sie zur **[!UICONTROL HTML content]** Registerkarte oder **[!UICONTROL Text content]** und definieren Sie Inhalte für mindestens eines dieser beiden Formate.

   >[!IMPORTANT]
   >
   >Wenn Ihre E-Mail neben dem AMP-Inhalt keine HTML- oder Nur-Text-Version enthält, kann sie nicht gesendet werden.

## AMP für Anforderungen für die E-Mail-Zustellung {#amp-for-email-delivery-requirements}

Beim Erstellen Ihres AMP-Inhalts in Adobe Campaign müssen Sie die Bedingungen für die Auslieferung einer dynamischen E-Mail erfüllen, die speziell für die E-Mail-Anbieter Ihrer Empfänger gelten.

Derzeit unterstützen drei E-Mail-Anbieter Tests in diesem Format: Gmail, Outlook und Mail.ru.

Alle Schritte und Spezifikationen, die zum Testen der Bereitstellung mit dem AMP-Format auf Gmail-Konten erforderlich sind, sind in den entsprechenden [Gmail](https://developers.google.com/gmail/ampemail?)-, [Outlook- ](https://docs.microsoft.com/en-gb/outlook/amphtml/) und [Mail.ru](https://postmaster.mail.ru/amp) Entwicklerdokumenten beschrieben.

Insbesondere müssen folgende Anforderungen erfüllt sein:
* Befolgen Sie die AMP-Sicherheitsanforderungen für [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) und [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* Das AMP MIME-Teil muss ein [gültiges AMP-Dokument](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)enthalten.
* Der AMP MIME-Teil muss kleiner als 100 KB sein.

Sie können auch die [Tipps und bekannten Einschränkungen für Gmail](https://developers.google.com/gmail/ampemail/tips) und die [AMP Best Practices für Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## Targeting einer AMP-E-Mail {#targeting-amp-email}

AMP für E-Mail als Beta-Funktion verfügbar. Sie können derzeit in zwei Schritten experimentieren, wie Sie eine AMP-E-Mail senden können:

1. Mit Adobe Campaign können Sie die Bereitstellung einer dynamischen AMP-E-Mail an ausgewählte E-Mail-Adressen testen, die entsprechend konfiguriert wurden, um deren Inhalt und Verhalten zu überprüfen. Ausgewählte Adressen finden Sie unter [Testen der AMP-E-Mail-Zustellung](#testing-amp-delivery-for-selected-addresses).
1. Nach dem Test können Sie eine Lieferung oder Kampagne als Teil des Programms AMP für E-Mail-Beta senden, indem Sie sich bei den entsprechenden E-Mail-Anbietern registrieren, damit Ihre Absenderdomäne in die Positivliste eingetragen wird. Siehe [Senden von AMP-E-Mails durch Registrierung bei einem E-Mail-Anbieter](#delivering-amp-emails-by-registering).

### Testen der AMP-E-Mail-Zustellung für ausgewählte Adressen {#testing-amp-delivery-for-selected-addresses}

Sie können das Senden dynamischer Nachrichten von Adobe Campaign an ausgewählte E-Mail-Adressen testen.

>[!NOTE]
>
>Derzeit unterstützen nur Gmail, Outlook und Mail.ru das Testen des AMP-Formats.

Bei Google Mail und Outlook müssen Sie zuerst die Absenderadresse(n), die Sie von Adobe Campaign für die Gmail- und Outlook-Konten, die Sie als Ziel verwenden, übermitteln, auf eine Whitelist setzen.

Gehen Sie dazu wie folgt vor:
1. Stellen Sie sicher, dass die Option zum Aktivieren der dynamischen E-Mail auf die entsprechenden E-Mail-Anbieter überprüft wurde.
1. Kopieren Sie die im **[!UICONTROL From]** Feld &quot;Zustellung&quot;angezeigte Absenderadresse und fügen Sie sie in den entsprechenden Abschnitt der Kontoeinstellungen Ihres E-Mail-Anbieters ein.

Weitere Informationen finden Sie in den Entwicklerdokumenten zu [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) und [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) .

![](assets/amp_from_field.png)

Gehen Sie zum Testen des Versands einer AMP-E-Mail an eine Mail.ru-Adresse wie in der Entwicklerdokumentation[ von ](https://postmaster.mail.ru/amp/?lang=en#howto)Mail.ru beschrieben vor (**wenn Sie ein Benutzer** sind).

### Auslieferung von AMP-E-Mails durch Registrierung bei einem E-Mail-Anbieter {#delivering-amp-emails-by-registering}

Sie können die Bereitstellung dynamischer E-Mails experimentieren, indem Sie sich bei den E-Mail-Anbietern registrieren, die am AMP-Beta-Programm teilnehmen, um Ihre Absenderdomäne auf die Positivliste setzen zu lassen.

>[!NOTE]
>
>Derzeit unterstützen nur Gmail, Outlook und Mail.ru das AMP-Format.

Nach dem Test mit wenigen Adressen können Sie AMP-E-Mails an eine beliebige Gmail- oder Outlook-Adresse senden. Dazu müssen Sie sich bei Google oder Microsoft respektvoll registrieren und auf ihre Antwort warten. Führen Sie die Schritte aus, die in den Entwicklerdokumenten von [Gmail](https://developers.google.com/gmail/ampemail/register) und [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) beschrieben sind. Nach erfolgreicher Registrierung werden Sie autorisierter Absender.

Um AMP-E-Mails an Mail.ru-Adressen zu senden, befolgen Sie die in der Entwicklerdokumentation[ für ](https://postmaster.mail.ru/amp/?lang=en#howto)Mail.ru aufgelisteten Anforderungen und Schritte (**wenn Sie ein E-Mail-Absender** sind).

## Senden einer AMP-E-Mail {#sending-amp-email}

Sobald Ihr AMP-Inhalt und Ihr Fallback fertig sind und Sie ein kompatibles Ziel definiert haben, können Sie die E-Mail wie gewohnt senden.

Zurzeit unterstützen nur Gmail, Outlook und Mail.ru das AMP Format unter bestimmten Bedingungen. Sie können Adressen von anderen E-Mail-Anbietern als Ziel auswählen, die jedoch die HTML- oder Textversion Ihrer E-Mail erhalten.

>[!IMPORTANT]
>
>Wenn Ihre E-Mail neben dem AMP-Inhalt keine HTML- oder Nur-Text-Version enthält, kann sie nicht gesendet werden.

Bei den passenden Empfängern wird die AMP-Version der E-Mail in ihrem Postfach angezeigt.

Wenn Sie beispielsweise eine Produktliste in Ihrer E-Mail eingefügt haben und die Preise in einem Drittanbietersystem bearbeiten, werden die Preise automatisch angepasst, sobald die Empfänger die E-Mail erneut in ihrem Postfach öffnen.

>[!NOTE]
>
>Sie können eine E-Mail-Verarbeitungsregel erstellen, um zu verhindern, dass bestimmte Domänen AMP-E-Mails empfangen. Siehe [Verwalten von E-Mail-Formaten](../../installation/using/email-deliverability.md#managing-email-formats).
>
>Standardmäßig ist die **[!UICONTROL AMP inclusion]** Option auf **[!UICONTROL No]**.
