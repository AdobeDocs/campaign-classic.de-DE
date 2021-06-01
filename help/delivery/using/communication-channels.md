---
product: campaign
title: Kommunikationskanäle
description: Erstellen Sie Sendungen, um personalisierte Nachrichten über verschiedene Kanäle zu senden.
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 100%

---

# Kommunikationskanäle{#communication-channels}

Mit Adobe Campaign können Sie kanalübergreifende Kampagnen wie E-Mails, SMS, LINE-Nachrichten, Push-Benachrichtigungen und Briefpost senden und deren Effektivität mithilfe verschiedener dedizierter [Berichte](../../reporting/using/delivery-reports.md) messen. Diese Nachrichten werden mittels Sendungen entworfen und gesendet und können für jeden Empfänger personalisiert werden.

Zu den Kernfunktionen zählen die Zielgruppenbestimmung, die Definition und Personalisierung von Nachrichten, die Ausführung von Kommunikationen und die damit verbundenen operativen Berichte. Als Hauptzugriffspunkt dient der Versand-Assistent. Dieser Zugriffspunkt führt zu mehreren Funktionen, die von Adobe Campaign abgedeckt werden.

>[!NOTE]
>
>Adobe Campaign bietet eine Reihe von Tools zur Überwachung Ihrer Zustellbarkeit und zur Optimierung des E-Mail-Versands. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../delivery/using/about-deliverability.md).

Sendungen können automatisiert werden, indem ein Versand vorbereitet und/oder über einen Workflow gesendet wird. Weiterführende Informationen zu Versandaktivitäten in Workflows finden Sie in [diesem Abschnitt](../../workflow/using/about-action-activities.md).

Folgende Versandkanäle stehen in Adobe Campaign zur Verfügung:

1. **E-Mail-Kanal**: Ein E-Mail-Versand richtet personalisierte elektronische Nachrichten an eine zuvor bestimmte Zielpopulation. Siehe [Über den E-Mail-Kanal](../../delivery/using/about-email-channel.md).
1. **Briefpost-Kanal**: Ein Briefpost-Versand erzeugt eine Ausgabedatei, die die Daten der Zielpopulation enthält. Weitere Informationen finden Sie unter [Über den Briefpost-Kanal](../../delivery/using/about-direct-mail-channel.md).
1. **Mobile-Kanal**: Ein Versand über den Mobile-Kanal richtet personalisierte SMS- oder LINE-Nachrichten an eine zuvor bestimmte Zielpopulation. Siehe [SMS-Kanal](../../delivery/using/sms-channel.md).
1. **Mobile-App-Kanal**: Ein Mobile-App-Versand ermöglicht den Versand von Benachrichtigungen an iOS- und Android-Systeme. Siehe hierzu das Kapitel [Mobile App Channel](../../delivery/using/about-mobile-app-channel.md).

   Andere Kanäle werden auf [dieser Seite](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels) beschrieben.

   >[!NOTE]
   >
   >Die Anzahl der verfügbaren Kanäle hängt von Ihrem Vertrag ab. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

Sendungen können **online** (per E-Mail, Mobile-Kanal und Push-Benachrichtigungen) und **offline** (Brief-Kanal) durchgeführt werden.

Je nach Kanal sind folgende Versandmodi verfügbar:

* Gebündelter Versand via Adobe Campaign (Standardmodus beim E-Mail-Kanal).
* Externer Versand über spezialisierte Dienstleister. In diesem Fall erzeugt der Versand-Assistent eine Ausgabedatei. (Standardmodus beim Briefpost-Kanal.)

Die hierfür benötigten externen Konten werden im Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** verwaltet. Die Konfiguration sollte von erfahrenen Benutzern vorgenommen werden.

## E-Mail-Versand {#email-deliveries}

Der [E-Mail-Kanal](../../delivery/using/about-email-channel.md) ist einer der wichtigsten Kanäle in Adobe Campaign. Damit können Sie den Versand von personalisierten E-Mails an bestimmte Zielgruppen planen und durchführen.

Verschiedene Typen von E-Mails können gesendet werden:

* Einmalige E-Mails: E-Mails, die ein einziges Mal an eine definierte Zielgruppe gesendet werden. Sie werden zur Verbreitung spezifischer Inhalte verwendet, die nur ein einziges Mal vorbereitet und gesendet werden (Newsletter, Werbe-E-Mails etc.).
* Wiederkehrende E-Mails: Ein und dieselbe E-Mail wird regelmäßig gesendet und die Sendungen und Berichte werden regelmäßig aggregiert. Die E-Mail selbst bleibt unverändert, doch die Zielgruppe ändert sich je nach Versandtag. Ein Beispiel dafür sind Geburtstags-E-Mails. Weiterführende Informationen dazu finden Sie unter [Wiederkehrender Versand](../../workflow/using/recurring-delivery.md).
* Transaktions-E-Mails: einzelne E-Mails, die auf der Basis des Kundenverhaltens ausgelöst werden. Siehe auch [Transaktionsnachrichten](../../message-center/using/about-transactional-messaging.md).

Weiterführende Informationen zum Versand und Empfehlungen dazu finden Sie im Abschnitt [Best Practices beim Versand](../../delivery/using/delivery-best-practices.md).

Weiterführende Informationen zu den unterschiedlichen Versandarten finden Sie in [diesem Abschnitt](#types-of-deliveries).

## Versand über den Mobiltelefon-Kanal {#mobile-deliveries}

Adobe Campaign ermöglicht den Versand von Nachrichten per [SMS](../../delivery/using/sms-channel.md) und [LINE](../../delivery/using/line-channel.md) auf Mobiltelefone.

Die Inhalt-Kachel von SMS bietet ebenfalls die Möglichkeit der Erstellung, Anpassung und Personalisierung von Nachrichteninhalten, jedoch ausschließlich im Textformat. Es ist außerdem möglich, vor dem Versand eine Vorschau der SMS zu erzeugen.

LINE-Nachrichten können Text, Bilder und Links enthalten.

Folgende Voraussetzungen müssen gegeben sein, um SMS- oder LINE-Nachrichten an Mobiltelefone zu senden:

* Ein externes Konto, das für den Kanal **[!UICONTROL Mobiltelefon (SMS)]** oder **[!UICONTROL LINE]** konfiguriert wurde.
* Eine SMS- oder LINE-Versandvorlage, die auf das externe Konto Bezug nimmt.

## Push-Benachrichtigungen {#push-notifications}

Sie können mit Adobe Campaign über spezielle Apps personalisierte und zielgruppenspezifische [Push-Benachrichtigungen](../../delivery/using/about-mobile-app-channel.md) an iOS- und Android-Mobilgeräte versenden. Um derartige Sendungen vorzubereiten und durchzuführen, sind zunächst Konfigurations- und Integrationsschritte erforderlich. Zusätzlich können Rich-Benachrichtigungen mit Bildern oder Videos erstellt werden.

## Briefpost {#direct-mail}

[Briefpost ist ein Offline-Kanal, über den Sie eine für Briefpost-Dienstleister nötige Datei erstellen und personalisieren können. ](../../delivery/using/about-direct-mail-channel.md) Sie erhalten damit die Möglichkeit, Online- und Offline-Kanäle in Ihren Customer Journeys zu mischen.

Über Online-Kanäle können Sie Nachrichten erstellen (E-Mail, SMS, Mobile-App-Versand etc.) und direkt über Adobe Campaign an Ihre Audience senden. Offline-Kanäle sind anders. Wenn Sie einen Briefpost-Versand vorbereiten, erzeugt Adobe Campaign eine Datei, die alle Zielgruppenprofile und die ausgewählte Kontaktinformationen enthält (z. B. Postanschrift). Dann senden Sie diese Datei an Ihren Briefpost-Dienstleister, der den tatsächlichen Versand vornimmt.

## Sonstige Kanäle {#other-channels}

Adobe Campaign bietet eine Vorlage für den Festnetztelefon-Versand, die zur Erstellung von externen Sendungen dient. Eine Verwendung dieses Kanals setzt voraus, dass Sie spezielle Methoden zur Verarbeitung von Ausgabedateien eingerichtet haben. Die Konfigurationsschritte sind mit denen des [Brief-Kanals](../../delivery/using/about-direct-mail-channel.md) identisch.

>[!NOTE]
>
>Der Festnetztelefon-Kanal ist nicht nativ verfügbar. Seine Implementierung erfordert die Einbindung von Adobe Consulting oder einem Adobe-Partner. Wenden Sie sich für weitere Informationen an Ihren Adobe-Support-Mitarbeiter.

Zusätzlich verwenden Sendungen vom Typ &quot;Sonstige&quot; eine spezifische technische Vorlage, die keinen Vorgang auslöst. Dies erlaubt beispielsweise die Verwaltung von außerhalb der Plattform durchgeführten Marketingaktionen.

Dieser Kanal besitzt keinen bestimmten Mechanismus. Er ist ein allgemeiner Kanal, der wie jeder andere Kommunikationskanal in Adobe Campaign über eine eigene externe Konto-Routing-Möglichkeit, Versandvorlagenart und Kampagnen-Workflow-Aktivität verfügt.

Dieser Kanal ist nur für informative Zwecke konzipiert, wie etwa um Zielgruppeninformationen zu mit externen Tools durchgeführten Kampagnen zu speichern.

## Versandtypen{#types-of-deliveries}

In Campaign gibt es drei Typen von Versandobjekten:

### Einzelversand {#single-delivery}

Ein **Versand** ist ein unabhängiges Versandobjekt, das ein einziges Mal ausgeführt wird. Es kann dupliziert und nochmals vorbereitet werden, doch sobald es in seinem finalen Zustand ist (abgebrochen, gestoppt, fertiggestellt), kann es nicht wiederverwendet werden.

Sendungen können entweder in der Versandliste oder innerhalb eines Workflows über die Aktivität [Versand](../../workflow/using/delivery.md) erstellt werden.

Workflows bieten abhängig vom zu verwendeten Kanal auch spezifische Versandaktivitäten. Weiterführende Informationen zu diesen Aktivitäten erhalten Sie in [diesem Abschnitt](../../workflow/using/cross-channel-deliveries.md).

### Wiederkehrender Versand {#recurring-delivery}

Mit einem **wiederkehrenden Versand** können Sie jedes Mal, wenn eine bestimmte Aktivität ausgeführt wird, einen neuen Versand erstellen. Dadurch müssen Sie für sich wiederholende Aufgaben nicht jedes Mal erneut einen Versand erstellen.

Wenn Sie diese Aktivität beispielsweise einmal im Monat ausführen, ergibt das im Jahr 12 Sendungen.

Wiederkehrende Sendungen werden über Workflows mit der Aktivität [](../../workflow/using/recurring-delivery.md)Wiederkehrender Versand erstellt. Ein Beispiel für diese Aktivität finden Sie in diesem Abschnitt: [Erstellen eines wiederkehrenden Versands in einem Zielgruppen-Workflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Versand (fortlaufend){#continuous-delivery}

Bei einem **fortlaufenden Versand** können Sie einem bestehenden Versand neue Empfänger hinzufügen, sodass Sie nicht jedes Mal einen neuen Versand erstellen müssen.

Wenn sich Daten im Versand ändern (Inhalt, Name etc.), wird bei der Ausführung des Versands ein neues Versandobjekt erstellt. Wenn keine Daten geändert wurden, wird dasselbe Versandobjekt erneut verwendet und die Versand- und Trackinglogs werden im selben Objekt hinzugefügt.

Wenn Sie diese Aktivität beispielsweise einmal im Monat ausführen, ergibt das eine einzige Sendung im Jahr (vorausgesetzt Sie haben am Versand keine Änderung vorgenommen).

Fortlaufende Sendungen werden in Workflows über die Aktivität [Versand (fortlaufend)](../../workflow/using/continuous-delivery.md) erstellt.
