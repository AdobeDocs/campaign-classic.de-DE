---
product: campaign
title: Prüfen vor dem Senden
description: Sobald Ihre Nachricht fertig ist, führen Sie alle Prüfungen vor dem Senden durch
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
role: User
hide: true
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
TQID: https://experienceleague.adobe.com/ngnYPos--1A5p7WN-fJnxaLt-yHG50lWHid4wbbyVZw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 914
ht-degree: 91%

---

# Durchführen aller Prüfungen vor dem Senden {#perform-all-checks}

Wenn Ihre Nachricht fertig ist, prüfen Sie, ob ihr Inhalt auf allen Geräten richtig dargestellt wird, und stellen Sie sicher, dass sie keine Fehler wie falsche Personalisierung oder defekte Links enthält.

Prüfen Sie vor dem Nachrichtenversand außerdem, ob die Parameter und die Konfiguration dem Versand entsprechen.

## Warum die Validierung wichtig ist {#validation-is-key}

Bevor Sie einen Versand durchführen, müssen Sie sicherstellen, dass Ihre Empfänger bzw. Empfängerinnen tatsächlich die Nachricht erhalten, die Sie ihnen senden möchten. Dazu müssen Sie den Nachrichteninhalt und die Versandparameter validieren.

Durch diese Maßnahme können Sie mögliche Fehler erkennen und beheben, bevor Sie den Versand an Ihre Hauptzielgruppe durchführen.

In [diesem Abschnitt](steps-validating-the-delivery.md) werden die Schritte zur Validierung eines Versands vorgestellt.

## Inbox Rendering {#inbox-and-email-rendering}

Mit Inbox Rendering können Sie sich eine Vorschau Ihrer Nachrichten in den gängigsten E-Mail-Clients ansehen, Inhalt und Reputation überprüfen und feststellen, wie Empfänger Ihre Nachrichten lesen.

**Tipps**:

* Sie können sich ansehen, wie Nachrichten je nach verwendetem Empfangsmedium (Mobilgeräte, Web-Clients etc.) beim Empfänger dargestellt werden.

* Inbox Rendering-Funktionen sind entscheidend, um zu ermitteln, ob Ihre E-Mail-Kampagnen erfolgreich über die Filter der wichtigsten ISPs (Internet Service Provider) und Webmail-Services hinauskommen. Solche Tools senden eine Pre-Flight-Kopie einer E-Mail an ein Netzwerk von Test-Posteingängen, sodass Sie sehen können, wie die Nachricht über diese Dienste hinweg angezeigt oder gerendert wird. Sie können auch Berichte und Optionen zur Code-Korrektur enthalten, mit denen Sie schnell Korrekturen zur Verbesserung der Zustellbarkeit ermitteln und vornehmen können.

Weitere Informationen finden Sie in [diesem Abschnitt](inbox-rendering.md).

## Nachrichten in Testsendungen {#proof-messages}

Mit Testsendungen können Sie den Ausschluss-Link, die Mirrorseite und andere Links testen, die Nachricht validieren, die Anzeige von Bildern überprüfen und mögliche Fehler erkennen. Außerdem können Sie das Design und die Darstellung auf verschiedenen Geräten testen.

Weiterführende Informationen finden Sie [in diesem Abschnitt](steps-validating-the-delivery.md#sending-a-proof).

## Einrichten von A/B-Test-Sendungen {#a-b-testing-deliveries}

Wenn mehrere Versionen von Inhalten für den E-Mail-Versand vorhanden sind, können Sie mithilfe von A/B-Tests feststellen, welche Version die größte Auswirkung auf die Zielpopulation hat.

**Tipps**:

* Senden Sie die unterschiedlichen Versionen an einige Ihrer Empfänger.

* Wählen Sie die Version mit der höchsten Erfolgsquote aus und senden Sie sie an die restliche Zielgruppe.

Weiterführende Informationen finden Sie [in diesem Abschnitt](get-started-a-b-testing.md).

## Nachrichtenzustellung überprüfen {#make-sure-your-message-is-delivered}

Optimieren Sie Ihre Möglichkeiten und nutzen Sie die Funktionen von Adobe Campaign Classic, um sicherzustellen, dass Ihre Nachricht tatsächlich bei den entsprechenden Empfängern ankommt.

### Validierungsprozess

Sie können einen vollständigen Validierungsprozess einschließlich der Adobe Campaign-Benutzer und -Gruppen definieren, um die Zielgruppe und den Nachrichteninhalt zu validieren. Dadurch wird eine umfassende Steuerung und Kontrolle der unterschiedlichen Kampagnenprozesse ermöglicht. Hierzu gehören Zielgruppenbestimmung, Inhalt, Budget, Extraktion und Testversand. Je nach Berechtigung werden Benutzer benachrichtigt, erhalten Testsendungen und können die Nachricht validieren oder ablehnen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../campaign/using/marketing-campaign-approval.md).

### Schübe verwenden

Mit Schüben können Sie das gesendete Nachrichtenvolumen nach und nach steigern. Dadurch wird verhindert, dass Ihre Nachrichten als Spam gekennzeichnet werden, oder Sie können die Anzahl der pro Tag versendeten Nachrichten beschränken. Mit Schüben können Sie Sendungen in mehrere Teilsendungen unterteilen, anstatt große Mengen von Nachrichten gleichzeitig zu senden. Weiterführende Informationen finden Sie [in diesem Abschnitt](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Nachrichten priorisieren

Sie können die Reihenfolge der Sendungen durch Angabe der Versandpriorität festlegen. Gehen Sie dabei folgendermaßen vor:

1. Bearbeiten Sie die Versandeigenschaften und wählen Sie den Tab **[!UICONTROL Versand]** aus.

1. Bestimmen Sie dann die Dringlichkeit von **[!UICONTROL Sehr niedrig]** bis **[!UICONTROL Sehr hoch]**.

>[!NOTE]
>
>Die Reihenfolge der versendeten Nachrichten innerhalb eines Versands kann nicht festgelegt werden.

### Einrichten von IP-Affinitäten

Um den ausgehenden SMTP-Traffic besser zu steuern, können Sie für jede Affinität die Verwendung bestimmter IP-Adressen festlegen. Damit können Sie die Zustellung von E-Mails auf bestimmte Geräte oder IP-Adressen begrenzen. Sie können beispielsweise eine Affinität pro Land oder Subdomain verwenden. Anschließend können Sie für jedes Land eine Typologie erstellen und jede Affinität mit der entsprechenden Typologie verknüpfen.

Sie haben folgende Möglichkeiten:

* Definieren Sie die IP-Affinitäten in der Konfigurationsdatei „serverConf.xml“. [Weitere Informationen](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Geben Sie für jedes IPAffinity-Element an, welche IP-Adressen verwendet werden können. [Weitere Informationen](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Verbinden Sie in der von Ihnen ausgewählten [Typologie](../../campaign-opt/using/about-campaign-typologies.md) im Feld **[!UICONTROL Verwaltung der IP-Adressen-Affinitäten]** die Sendungen mit dem Versand-Server (MTA), in dem die betreffende Affinität verwaltet wird. [Weitere Informationen](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* Überprüfen Sie nach dem Versand der E-Mail in der Kopfzeile, von welcher IP-Adresse der Versand gesendet wurde. Ihr E-Mail-Administrator sollte Ihnen beim Abrufen der Kopfzeileninformationen behilflich sein.

* Stellen Sie bei SMS-Sendungen sicher, dass der SMS-Kanal über eine dedizierte Affinität verfügt, die auf **einen** Anwendungs-Server-Container beschränkt ist. [Weitere Informationen](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>Die meisten dieser Schritte können nur von einem erfahrenen Benutzer durchgeführt werden.

### Typologien verwenden

Typologieregeln ermöglichen den kriterienbasierten Ausschluss eines Teils der Zielgruppe. Auf diese Weise werden ein ideal auf Kundenbedürfnisse abgestimmter Nachrichtenversand sowie eine kohärente Unternehmenskommunikation sichergestellt. Beispielsweise können Sie minderjährige Empfänger aus der Zielgruppe Ihres Newsletters herausfiltern. Weiterführende Informationen finden Sie [in diesem Beispiel](../../campaign-opt/using/filtering-rules.md).

### Anhänge vermeiden

Anhänge zählen zu den häufigsten Trägern von Malware, besonders wenn sie in einer Massensendung verschickt werden. Fügen Sie in die Nachricht einen sicheren Link ein, anstatt ein Dokument anzuhängen. Dies sorgt für zusätzlichen Schutz vor unbeabsichtigter Weiterverbreitung und verringert auch die Gefahr, dass die Nachricht an eingehenden E-Mail-Gateways wegen der Nachrichtengröße oder aus Sicherheitsgründen abgelehnt wird.
