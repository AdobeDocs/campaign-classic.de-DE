---
title: Prüfen vor dem Senden
seo-title: Prüfen vor dem Senden
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 5e6ecd636ee0b2199808c03b2fd898a194f0c1ea
workflow-type: ht
source-wordcount: '874'
ht-degree: 100%

---


# Durchführen aller Prüfungen vor dem Senden {#perform-all-checks}

Wenn Ihre Nachricht fertig ist, prüfen Sie, ob ihr Inhalt auf allen Geräten richtig dargestellt wird, und stellen Sie sicher, dass sie keine Fehler wie falsche Personalisierung oder defekte Links enthält.

Prüfen Sie vor dem Nachrichtenversand außerdem, ob die Parameter und die Konfiguration dem Versand entsprechen.

## Warum die Validierung wichtig ist {#validation-is-key}

Bevor Sie einen Versand durchführen, müssen Sie sicherstellen, dass Ihre Empfänger tatsächlich die Nachricht erhalten, die Sie ihnen senden möchten. Zu diesem Zweck müssen Sie den Nachrichteninhalt und die Versandparameter validieren.

Durch diese Maßnahme können Sie mögliche Fehler erkennen und beheben, bevor Sie den Versand an Ihre Hauptzielgruppe durchführen.

In [diesem Abschnitt](../../delivery/using/steps-validating-the-delivery.md) werden die Schritte zur Validierung eines Versands vorgestellt.

## Inbox Rendering {#inbox-and-email-rendering}

Mit Inbox Rendering können Sie sich eine Vorschau Ihrer Nachrichten in den gängigsten E-Mail-Clients ansehen, Inhalt und Reputation überprüfen und feststellen, wie Empfänger Ihre Nachrichten lesen.

**Tipps**:

* Sie können sich ansehen, wie Nachrichten je nach verwendetem Empfangsmedium (Smartphones und Tablets, Web-Clients etc.) beim Empfänger dargestellt werden.

* Fähigkeiten zum Inbox Rendering sind entscheidend, um festzustellen, ob Ihre E-Mail-Kampagnen erfolgreich durch die Filter der großen ISPs (Internet Service Providers) und Webmail-Dienste befördert werden. Diese Tools senden vorab eine Kopie einer E-Mail an ein Netzwerk von Test-Posteingängen, damit Sie sehen, wie eine Nachricht in diesen Diensten dargestellt wird. Manche dieser Tools bieten auch Berichte und Code-Korrektur-Möglichkeiten, mit denen Sie Fehler rasch erkennen und beheben und so die Zustellbarkeit verbessern können.

Weiterführende Informationen finden Sie [in diesem Abschnitt](../../delivery/using/inbox-rendering.md).

## Nachrichten in Testsendungen {#proof-messages}

Mit Testsendungen können Sie den Abmelde-Link, die Mirrorseite und andere Links testen, die Nachricht validieren, die Anzeige von Bildern überprüfen, mögliche Fehler erkennen etc. Außerdem können Sie Ihr Design und die Darstellung auf verschiedenen Geräten testen.

Weiterführende Informationen finden Sie [in diesem Abschnitt](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Einrichten von A/B-Test-Sendungen {#a-b-testing-deliveries}

Wenn mehrere Versionen von Inhalten für den E-Mail-Versand vorhanden sind, können Sie mithilfe von A/B-Tests feststellen, welche Version die größte Auswirkung auf die Zielkontakte hat.

**Tipps**:

* Senden Sie die unterschiedlichen Versionen an einige Ihrer Empfänger.

* Wählen Sie die Version mit der höchsten Erfolgsquote aus und senden Sie sie an die restliche Zielgruppe.

Weiterführende Informationen finden Sie [in diesem Abschnitt](../../workflow/using/a-b-testing.md).

## Nachrichtenzustellung überprüfen {#make-sure-your-message-is-delivered}

Optimieren Sie Ihre Möglichkeiten und nutzen Sie die Funktionen von Adobe Campaign Classic, um sicherzustellen, dass Ihre Nachricht tatsächlich bei den entsprechenden Empfängern ankommt.

### Validierungsprozess

Sie können einen vollständigen Validierungsprozess einschließlich der Adobe-Campaign-Benutzer und -Gruppen definieren, um die Zielgruppe und den Nachrichteninhalt zu validieren. Dadurch wird eine umfassende Steuerung und Kontrolle der unterschiedlichen Kampagnenprozesse ermöglicht. Hierzu gehören Zielgruppenbestimmung, Inhalt, Budget, Extraktion und Testversand. Je nach Berechtigung werden Benutzer benachrichtigt, erhalten Testsendungen und können die Nachricht validieren oder ablehnen. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../campaign/using/marketing-campaign-approval.md#approval-process).

### Schübe verwenden

Mit Schüben können Sie das gesendete Nachrichtenvolumen nach und nach steigern. Dadurch wird verhindert, dass Ihre Nachrichten als Spam gekennzeichnet werden, oder Sie können die Anzahl der pro Tag versendeten Nachrichten beschränken. Mit Schüben können Sie Sendungen in mehrere Teilsendungen unterteilen, anstatt große Mengen von Nachrichten gleichzeitig zu senden. Weiterführende Informationen finden Sie [in diesem Abschnitt](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### Nachrichten priorisieren

Sie können die Reihenfolge der Sendungen durch Angabe der Versandpriorität festlegen. Gehen Sie dabei folgendermaßen vor:

1. Bearbeiten Sie die Versandeigenschaften und wählen Sie den Tab **[!UICONTROL Versand]** aus.

1. Bestimmen Sie dann die Dringlichkeit von **[!UICONTROL Sehr niedrig]** bis **[!UICONTROL Sehr hoch]**.

>[!NOTE]
>
>Die Reihenfolge der versendeten Nachrichten innerhalb eines Versands kann nicht festgelegt werden.

### Einrichten von IP-Affinitäten

Um den ausgehenden SMTP-Traffic besser zu steuern, können Sie für jede Affinität die Verwendung bestimmter IP-Adressen festlegen. Damit können Sie die Zustellung von E-Mails auf bestimmte Geräte oder IP-Adressen begrenzen. So können Sie beispielsweise eine Affinität pro Land oder Sub-Domain verwenden. Dann können Sie für jedes Land eine Typologie erstellen und jede Affinität mit der entsprechenden Typologie verbinden.

Sie haben folgende Möglichkeiten:

* Definieren Sie die IP-Affinitäten in der Konfigurationsdatei „serverConf.xml“. [Mehr dazu](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Geben Sie für jedes IPAffinity-Element an, welche IP-Adressen verwendet werden können. [Mehr dazu](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Verbinden Sie in der von Ihnen ausgewählten [Typologie](../../campaign/using/about-campaign-typologies.md) im Feld **[!UICONTROL Verwaltung der IP-Adressen-Affinitäten]** die Sendungen mit dem Versand-Server (MTA), in dem die betreffende Affinität verwaltet wird. [Mehr dazu](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Prüfen Sie nach dem Versand der E-Mail den Header, um festzustellen, von welcher IP-Adresse aus der Versand erfolgte. Ihr E-Mail-Administrator ist Ihnen beim Feststellen der Header-Informationen behilflich.

>[!NOTE]
>
>Die meisten dieser Schritte können nur von einem erfahrenen Benutzer durchgeführt werden.

### Typologien verwenden

Typologieregeln ermöglichen den kriterienbasierten Ausschluss eines Teils der Zielgruppe. Auf diese Weise werden ein ideal auf Kundenbedürfnisse abgestimmter Nachrichtenversand sowie eine kohärente Unternehmenskommunikation sichergestellt. Beispielsweise können Sie minderjährige Empfänger aus der Zielgruppe Ihres Newsletters herausfiltern. Weiterführende Informationen finden Sie [in diesem Beispiel](../../campaign/using/filtering-rules.md).

### Anhänge vermeiden

Anhänge zählen zu den häufigsten Trägern von Malware, besonders wenn sie in einer Massensendung verschickt werden. Fügen Sie in die Nachricht einen sicheren Link ein, anstatt ein Dokument anzuhängen. Dies sorgt für zusätzlichen Schutz vor unbeabsichtigter Weiterverbreitung und verringert auch die Gefahr, dass die Nachricht an eingehenden E-Mail-Gateways wegen der Nachrichtengröße oder aus Sicherheitsgründen abgelehnt wird.
