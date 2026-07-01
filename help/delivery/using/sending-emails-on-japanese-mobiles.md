---
product: campaign
title: Versenden von E-Mails auf japanischen Mobiltelefonen mit Adobe Campaign Classic
description: Erfahren Sie, wie Sie E-Mails konfigurieren, entwerfen und versenden, die auf einem japanischen Mobilgerät gelesen werden sollen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email, Email Design
role: User
hide: true
exl-id: 44634227-2340-49c4-b330-740c739ea551
TQID: https://experienceleague.adobe.com/-IaAfjCvy9znHFt89tg-gGkcbAHpJExugPFr9T6RwWA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 782
ht-degree: 100%

---

# Senden von E-Mails auf japanischen Mobiltelefonen {#sending-emails-on-japanese-mobiles}

## E-Mail-Formate für japanische Mobiltelefone {#email-formats-for-japanese-mobiles}

Adobe Campaign unterstützt drei spezifisch japanische Formate für E-Mail auf Mobilgeräten: **Deco-mail** (DoCoMo-Mobilgeräte), **Decore Mail** (Softbank-Mobilgeräte) und **Decoration Mail** (KDDI AU-Mobilgeräte). Diese Formate erzwingen besondere Einschränkungen hinsichtlich Codierung, Struktur und Größe. Weitere Informationen zu Einschränkungen und Empfehlungen finden Sie in [diesem Abschnitt](#limitations-and-recommendations).

Damit ein Empfänger, der eines dieser Formate verwendet, Nachrichten korrekt angezeigt bekommt, wird empfohlen, das entsprechende Format **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** oder **[!UICONTROL Decoration Mail (KDDI AU)]** im Empfängerprofil auszuwählen:

![](assets/deco-mail_03.png)

Wenn Sie hingegen im Feld **[!UICONTROL E-Mail-Format]** eine der Optionen **[!UICONTROL Unbekannt]**, **[!UICONTROL HTML]** oder **[!UICONTROL Text]** auswählen, erkennt Adobe Campaign bei Versand der E-Mail das japanische Format, das zu verwenden ist, um eine korrekte Anzeige zu gewährleisten.

Dieses automatische Erkennungssystem beruht auf der in den E-Mail-Regeln **[!UICONTROL E-Mail-Formatverwaltung]** gespeicherten Domainliste. Weiterführende Informationen zur Verwaltung von E-Mail-Formaten finden Sie auf [dieser Seite](../../installation/using/email-deliverability.md#managing-email-formats).

## Einschränkungen und Empfehlungen {#limitations-and-recommendations}

Der E-Mail-Versand an Mobiltelefone unter Vertrag mit japanischen Anbietern (Softbank, DoCoMo, KDDI AU) unterliegt gewissen Einschränkungen.

Aus diesem Grund müssen Sie:

* ausschließlich Bilder im JPEG- oder GIF-Format verwenden;
* einen Versand erstellen, bei dem die Summe aus Text und HTML in keinem Fall 10.000 Bytes übersteigt (für KDDI AU und DoCoMo);
* Bilder verwenden, deren Gesamtgröße vor der Kodierung weniger als 100 KB beträgt;
* in einer Nachricht nicht mehr als 20 Bilder verwenden;
* ein reduziertes HTML-Format verwenden (für jeden Anbieter steht eine begrenzte Anzahl an Tags zur Verfügung).

>[!NOTE]
>
>Die für jeden Anbieter spezifischen Einschränkungen müssen bei der Erstellung der Nachricht berücksichtigt werden. Informationen dazu finden sich in der jeweiligen Produktdokumentation.


## Testen des E-Mail-Inhalts {#testing-the-email-content}

### Vorschau der Nachricht {#previewing-the-message}

In Adobe Campaign haben Sie die Möglichkeit zu prüfen, ob das Format Ihrer Nachricht dem Versand an japanische Mobiltelefone angepasst ist.

Sobald Sie Ihren Inhalt erstellt und den Betreff der E-Mail angegeben haben, können Sie Anzeige und Formatierung der Nachricht kontrollieren.

Verwenden Sie hierzu im **[!UICONTROL Vorschau]**-Tab des Fensters zur Inhaltsbearbeitung den Link **[!UICONTROL Details...> Deco-Mail-Prüfung]**. Hier können Sie:

* prüfen, ob die Tags des HTML-Inhalts den mit dem japanischen Format einhergehenden Einschränkungen entsprechen;
* prüfen, ob die Anzahl an Bildern in der Nachricht nicht die durch das Format vorgegebene Höchstgrenze von maximal 20 Bildern überschreitet;
* prüfen, ob die Gesamtgröße nicht den Grenzwert von 100 KB übersteigt.

  ![](assets/deco-mail_06.png)

### Ausführen der Typologieregel {#running-typology-rule}

Zusätzlich zur Vorschauprüfung wird eine zweite Prüfung durchgeführt, die an einen Testversand oder einen normalen Versand gekoppelt ist: Eine spezifische Typologieregel, die **[!UICONTROL Deco-mail-Analyse]**, kommt im Zuge der Analyse zur Anwendung.

>[!IMPORTANT]
>
>Diese Typologieregel wird nur dann ausgeführt, wenn mindestens ein Empfängerprofil für den Empfang von E-Mails im Format **[!UICONTROL Deco-mail (DoCoMo)]**, **[!UICONTROL Decore Mail (Softbank)]** oder **[!UICONTROL Decoration Mail (KDDI AU)]** konfiguriert wurde.

Mithilfe dieser Regel können Sie sich vergewissern, ob bei der Sendung die von den japanischen Anbietern vorgegebenen [Formateinschränkungen](#limitations-and-recommendations) respektiert werden, insbesondere im Hinblick auf die Gesamtgröße der E-Mail, die jeweilige Größe ihrer HTML- und Textanteile, die Anzahl an Bildern in der Nachricht sowie die Tags des HTML-Inhalts.

### Durchführen eines Testversands {#sending-proofs}

Sie können Testsendungen durchführen, um Ihren Versand zu testen. Wenn Sie beim Durchführen von Testsendungen Ersatzadressen verwenden, geben Sie bitte Adressen ein, die dem E-Mail-Format des verwendeten Profils entsprechen.

Beispielsweise können Sie die Adresse eines Profils durch test@softbank.ne.jp ersetzen, wenn das E-Mail-Format für dieses Profil zuvor in **[!UICONTROL Decore Mail (Softbank)]** definiert wurde.

![](assets/deco-mail_05.png)

## Senden von Nachrichten {#sending-messages}

Für den Versand einer E-Mail an Empfänger mit japanischen E-Mail-Formaten mit Campaign haben Sie zwei Möglichkeiten:

* Erstellen Sie zwei Sendungen, eine nur für japanische Empfänger und die andere für alle anderen Empfänger. Weitere Informationen dazu finden Sie in [diesem Abschnitt](#designing-a-specific-delivery-for-japanese-formats).
* Erstellen Sie einen einzigen Versand und Adobe Campaign erkennt das Format automatisch. Weitere Informationen dazu finden Sie in [diesem Abschnitt](#designing-a-delivery-for-all-formats).

### Entwerfen eines spezifischen Versands für japanische Formate {#designing-a-specific-delivery-for-japanese-formats}

Erstellen Sie einen Workflow mit zwei Sendungen: einen Versand, der für japanische Mobiltelefone bestimmt ist, und einen zweiten für Empfänger mit einem Standard-E-Mail-Format.

Verwenden Sie hierfür eine **[!UICONTROL Aufspaltung]**-Aktivität in Ihrem Workflow und definieren Sie die japanischen E-Mail-Formate (Deco-mail, Decoration Mail und Decore Mail) als Filterbedingungen.

![](assets/deco-mail_08.png)

![](assets/deco-mail_07.png)

### Entwerfen eines Versands für alle Formate {#designing-a-delivery-for-all-formats}

Wenn Adobe Campaign die Formate dynamisch in Abhängigkeit von der Domain verwaltet (Profile mit E-Mail-Format **[!UICONTROL Unbekannt]**, **[!UICONTROL HTML]** oder **[!UICONTROL Text]**), können Sie für alle Empfänger denselben Versand verwenden.

Der Nachrichteninhalt wird sowohl für Empfänger mit japanischen Mobiltelefonen als auch für Standardempfänger korrekt angezeigt.

>[!IMPORTANT]
>
>Beachten Sie die Einschränkungen, denen die verschiedenen japanischen Formate (Deco-mail, Decoration Mail und Decore Mail) unterliegen. Weiterführende Informationen zu Einschränkungen finden Sie in [diesem Abschnitt](#limitations-and-recommendations).
