---
solution: Campaign Classic
product: campaign
title: SMS senden, überwachen und verfolgen
description: Erfahren Sie, wie Sie SMS in Kampagne senden, überwachen und verfolgen
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 93%

---


# SMS-Versand senden, überwachen und verfolgen{#sms-properties}

## SMS-Nachrichten senden {#sending-sms-messages}

Klicken Sie auf **[!UICONTROL Senden]**, um die Nachrichtenerstellung abzuschließen und den Versand zu starten.

Die detaillierten Schritte zur Validierung und zum Versand von Nachrichten finden Sie in den folgenden Abschnitten:

* [Versand überprüfen](../../delivery/using/steps-validating-the-delivery.md)
* [Versand durchführen](../../delivery/using/steps-sending-the-delivery.md)

## Erweiterte Parameter {#advanced-parameters}

Die Schaltfläche **[!UICONTROL Eigenschaften]** gibt Zugriff auf erweiterte Versandparameter. Der Abschnitt **[!UICONTROL SMS-Parameter]** im **[!UICONTROL Senden]**-Tab ermöglicht spezifische Konfigurationen.

Folgende Optionen stehen zur Verfügung:

* **Absenderadresse**: ermöglicht die Personalisierung des Versandabsenders mit einer Zeichenfolge aus alphanumerischen Zeichen, die auf elf Zeichen begrenzt ist. Das Feld darf nicht ausschließlich aus Zahlen bestehen. Sie können eine Bedingung definieren, um beispielsweise je nach Bereichs-Code des Empfängers unterschiedliche Namen anzuzeigen:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Überprüfen Sie die gültige Rechtslage Ihres Landes bezüglich der Änderung des Absendernamens. Stellen Sie außerdem sicher, dass Ihr Provider diese Funktionalität anbietet.

* **Übermittlungsmodus**: Art der SMS-Übermittlung.
* **Priorität**: Einer Nachricht zugeordnete Wichtigkeit. Standardmäßig wird die Priorität **[!UICONTROL Normal]** vorgeschlagen. Je nach Provider können Zuschläge für mit der Priorität **[!UICONTROL Hoch]** versendete SMS anfallen.
* **Anwendungstyp**: Verschiedene Optionen stehen zur Auswahl. Standardmäßig wird **[!UICONTROL Direktmarketing]** vorgeschlagen, da es sich um den am häufigsten verwendeten Typ handelt.

**Den NetSize-Connector betreffende Parameter**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Nachricht in mehreren SMS versenden**: ermöglicht den Versand von Nachrichten mit mehr als 160 Zeichen in mehreren SMS.

**SMPP-Connectoren betreffende Parameter**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Maximale Anzahl an SMS pro Nachricht**: ermöglicht die Angabe der maximalen SMS-Anzahl pro Nachricht, wobei 0 für eine SMS steht. Wenn die Nachricht mehr als die angegebene Anzahl an SMS benötigt, wird sie nicht gesendet.

## Überwachung und Verfolgung von SMS {#monitoring-and-tracking-sms-deliveries}

Nach Absenden der Nachrichten können Sie den Versand beobachten und verfolgen, siehe diese Abschnitte:

* [Überwachen von Sendungen](../../delivery/using/about-delivery-monitoring.md)
* [Ursachen für das Fehlschlagen von Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Über das Nachrichten-Tracking](../../delivery/using/about-message-tracking.md)

## eingehende Nachrichten verarbeiten {#processing-inbound-messages}

Das Modul **nlserver sms** ruft in regelmäßigen Abständen den Verarbeitungsfortschritt der Sendungen, Empfangsbestätigungen und Empfängerabmeldungen ab.

* **Empfangsbestätigungen**: Der Status Ihrer Sendungen kann in den Versandlogs eingesehen werden.

   >[!NOTE]
   >
   >Jede gesendete SMS ist mit einem externen Konto über den Primärschlüssel des letzteren verbunden. Dies bedeutet, dass
   >
   > * Empfangsbestätigungen eines externen Kontos für gelöschte SMS nicht korrekt verarbeitet werden können.
   > * ein SMS-Konto nur mit einem externen Konto verknüpft sein darf, damit die Empfangsbestätigungen korrekt zugeordnet werden können


* **Abmeldungen**: Empfänger, die keine SMS-Sendungen mehr erhalten möchten, können sich durch das Senden einer Nachricht mit Inhalt STOP abmelden. Wenn es Ihr Providervertrag vorsieht, können Sie diese Nachrichten mithilfe der Workflow-Aktivität **SMS-Empfang** abrufen. Dies ermöglicht die Erstellung einer Abfrage, die die Option **Diese Person nicht mehr kontaktieren** für die entsprechenden Empfänger aktiviert.

   Nähere Informationen hierzu finden Sie im [Workflows](../../workflow/using/architecture.md)-Handbuch.

## InSMS-Schema {#insms-schema}

Das InSMS-Schema enthält Informationen zu eingehenden SMS. Die Beschreibung dieser Felder findet sich in ihren jeweiligen desc-Attributen.

* **message**: Inhalt der erhaltenen SMS.
* **origin**: Mobiltelefonnummer des Nachrichtenabsenders.
* **providerId**: Kennung der vom SMS-SC (Short Message Service Centre) zurückgegebenen Nachricht.
* **created**: Eingangsdatum der Nachricht in Adobe Campaign.
* **extAccount**: externes Adobe-Campaign-Konto.

   >[!IMPORTANT]
   >
   >Die folgenden Felder sind NetSize-spezifisch.
   >
   >Wenn der Betreiber nicht NetSize verwendet, bleiben diese Felder leer.

* **alias**: Alias der eingehenden Nachricht.
* **separator**: Trennzeichen zwischen Alias und Nachrichten-Textkörper.
* **messageDate**: Nachrichtendatum gemäß Betreiber.
* **receivalDate**: Datum des Empfangs der vom Betreiber gesendeten Nachricht im SMS-SC (Short Message Service Centre).
* **deliveryDate**: Datum des Versands der Nachricht durch das SMS-SC (Short Message Service Centre).
* **largeAccount**: Code des der eingehenden SMS zugeordneten Kundenkontos.
* **countryCode**: Ländercode des Betreibers.
* **operatorCode**: Netzwerkcode des Betreiber.
* **linkedSmsId**: Adobe-Campaign-Kennung (broadlogId) der ausgehenden SMS, auf die diese SMS antwortet.

## Automatische Antworten verwalten (amerikanische Regelung) {#managing-automatic-replies--american-regulation-}

Wenn ein Abonnent auf eine durch Adobe Campaign versendete SMS mit einer die Schlüsselwörter STOP, HELP oder YES enthaltenden Nachricht antwortet, ist für den US-amerikanischen Markt eine Konfiguration der automatischen Benachrichtigungen an den Absender gesetzlich vorgeschrieben.

Wenn beispielsweise das Wort STOP gesendet wird, erhält der Abonnent automatisch eine Abmelde-Bestätigung.

Der Absendername für diese Art von Nachrichten besteht aus einer kurzen Nummer (short code), welche auch für die üblichen Sendungen genutzt wird.

>[!IMPORTANT]
>
>Das folgende detaillierte Verfahren gilt nur für SMPP-Connectoren, mit Ausnahme des Connectors „Erweitertes allgemeines SMPP“. Weitere Informationen finden Sie im Abschnitt [SMPP-Externe Konto erstellen](sms-set-up.md#creating-an-smpp-external-account).
>
>Sie betrifft die Zertifizierung durch amerikanische Provider bezüglich in den USA zu versendender Marketingkampagnen. Insbesondere müssen diese SMS dem Abonnenten, der ein entsprechendes Schlüsselwort gesendet hat, unverzüglich zugestellt werden.

1. Erstellen Sie eine XML-Datei nach folgendem Muster:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Geben Sie für das Attribut **name** des **`<shortcode>`**-Tags die Kurzwahlnummer an, die anstelle des Absendernamens angezeigt werden soll.

   Geben Sie in jedem **`<reply>`**-Tag im Attribut **keyword** ein Schlüsselwort und im Attribut **text** die dem Schlüsselwort entsprechende Nachricht an.

   >[!NOTE]
   >
   >Schlüsselwörter sind in Großbuchstaben zu schreiben.

   Wenn Sie für verschiedene Schlüsselwörter dieselbe Nachricht versenden möchten, können Sie die entsprechende Zeile duplizieren.

   Beispiel:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Speichern Sie dann die Datei unter dem Namen **smsAutoReply.xml**.

   Bitte berücksichtigen Sie, dass beim Dateinamen unter Linux die Groß- und Kleinschreibung zu beachten ist.

1. Kopieren Sie die Datei in das **conf**-Verzeichnis in Adobe Campaign (am gleichen Ort wie der Web-Server).

>[!IMPORTANT]
>
>Für diese Arten von Benachrichtigungen wird kein Verlauf erstellt. Sie sind also nicht im Versand-Dashboard enthalten. [Weitere Infos](../../delivery/using/delivery-dashboard.md).
>
>Diese Meldungen werden in den kommerziellen Druckvorschriften nicht berücksichtigt. [Weitere Infos](../../campaign/using/pressure-rules.md).
