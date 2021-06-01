---
product: campaign
title: Erste Schritte mit Transaktionsnachrichten
description: 'Erfahren Sie mehr über die Funktionsweise von Transaktionsnachrichten in Adobe Campaign Classic und die wichtigsten Schritte. '
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 42%

---


# Erste Schritte mit Transaktionsnachrichten {#about-transactional-messaging}

## Übersicht {#overview}

**Transaktionsnachrichten**  (Message Center) ist ein Campaign-Modul zur Verwaltung von Benachrichtigungen bezüglich benutzerspezifischer Trigger, die von durch ein externes Informationssystem gesendeten Ereignissen erzeugt werden.

Bei einer Transaktionsnachricht handelt es sich um eine individuell zugeschnittene, eindeutige Mitteilung, die beispielsweise über eine Website in Echtzeit übermittelt wird. Sie wird erwartet, weil sie wichtige Informationen enthält, die der Empfänger überprüfen oder bestätigen möchte.

Die Funktionen für Transaktionsnachrichten unterstützen die Skalierbarkeit und bieten rund um die Uhr einen Service.

* **Wann wird diese Nachricht gesendet?** Da diese Nachricht wichtige Informationen enthält, erwartet der Benutzer, dass sie in Echtzeit gesendet wird. Folglich muss die Verzögerung zwischen der Auslösung des Ereignisses und dem Eintreffen der Nachricht sehr kurz sein.

* **Warum ist das wichtig?** Im Allgemeinen hat eine Transaktionsnachricht hohe Öffnungsraten. Sie sollte daher sorgfältig gestaltet werden, da sie einen starken Einfluss auf das Kundenverhalten und die Kundenbeziehung im Allgemeinen haben kann.

* **Beispiel?** Es kann sich um eine Willkommensnachricht nach der Erstellung eines Kontos, eine Bestätigung, dass eine Bestellung versandt wurde, eine Rechnung, eine Nachricht zur Bestätigung einer Passwortänderung, eine Benachrichtigung nach dem Besuch einer Website durch einen Kunden, eine Mitteilung über die Nichtverfügbarkeit eines Produkts, einen Kontoauszug usw. handeln.

>[!IMPORTANT]
>
>Für Transaktionsnachrichten ist eine spezifische Lizenz erforderlich. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Funktionsweise von Transaktionsnachrichten {#transactional-messaging-operating-principle}

Das Transaktionsnachrichtenmodul von Adobe Campaign ist in ein Informationssystem integriert, das Ereignisse zurückgibt, die in personalisierte Transaktionsnachrichten geändert werden. Diese Nachrichten können einzeln oder in Batches per E-Mail, SMS oder Push-Benachrichtigungen gesendet werden.

Diese Funktion beruht auf einer bestimmten Architektur, bei der die **Ausführungsinstanz** von der **Kontrollinstanz** getrennt ist. Diese Verteilung sorgt für höhere Verfügbarkeit und bessere Lastverwaltung. Weiterführende Informationen dazu finden Sie unter [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Um neue Benutzer für in der Adobe Cloud gehostete Message-Center-Ausführungsinstanzen zu erstellen, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Message Center-Benutzer sind bestimmte Benutzer, die spezielle Berechtigungen für den Zugriff auf die Ordner **[!UICONTROL Echtzeit-Ereignisse (nmsRtEvent)]** benötigen.

Der gesamte Prozess der Transaktionsnachrichten kann wie folgt beschrieben werden:

![](assets/transactional-msg-overview.png)

Angenommen, Sie sind eine Firma mit einer Website, auf der Ihre Kunden Produkte kaufen können.

Mit Adobe Campaign können Sie eine Benachrichtigungs-E-Mail an Kunden senden, die ihrem Warenkorb Produkte hinzugefügt haben. Wenn ein Kunde Ihre Website verlässt, ohne seine Einkäufe zu tätigen (externes Ereignis, das ein Campaign-Ereignis auslöst), wird automatisch eine Warenkorbabbruchs-E-Mail an ihn gesendet (Versand einer Transaktionsnachricht).

Die wichtigsten Schritte für die Einrichtung sind nachfolgend in [diesem Abschnitt](#key-steps) beschrieben.

>[!NOTE]
>
>In Adobe Campaign hat die Verarbeitung von Transaktionsnachrichten Priorität vor allen anderen Sendungen.

## Die wichtigsten Schritte {#key-steps}

Die wichtigsten Schritte beim Erstellen und Verwalten personalisierter Transaktionsnachrichten in Adobe Campaign sind unten zusammengefasst.

### Schritte für die Kontrollinstanz

Auf der **Kontrollinstanz** müssen Sie die folgenden Aktionen durchführen:

1. [Erstellen Sie einen Ereignistyp](../../message-center/using/creating-event-types.md).
1. [Erstellen und entwerfen Sie die Nachrichtenvorlage](../../message-center/using/creating-the-message-template.md). Während dieses Schritts müssen Sie ein Ereignis mit Ihrer Nachricht verknüpfen.
1. [Testen Sie die Nachricht](../../message-center/using/testing-message-templates.md).
1. [Veröffentlichen Sie die Nachrichtenvorlage](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>Alle oben genannten Schritte werden auf der **Kontrollinstanz** ausgeführt. Wenn Sie die Vorlage in der Kontrollinstanz veröffentlichen, wird sie auch in allen **Ausführungsinstanzen** veröffentlicht. Weitere Informationen zu den Instanzen von Transaktionsnachrichten finden Sie unter [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md).

### Ereignisverarbeitung in der Ausführungsinstanz

Nachdem Sie die Transaktionsnachrichtenvorlage entworfen und veröffentlicht haben und ein entsprechendes Ereignis ausgelöst wurde, werden die folgenden Hauptschritte auf der **Ausführungsinstanz** ausgeführt:

1. Wenn das Ereignis vom externen Informationssystem generiert wird, werden die relevanten Daten über die Methoden **PushEvent** und **PushEvents** an Campaign gesendet. Siehe [Ereignisabruf](../../message-center/using/about-event-processing.md#event-collection).
1. Das Ereignis ist mit der entsprechenden Nachrichtenvorlage verknüpft. Siehe [Routing zu einer Vorlage](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. Nach Abschluss der Anreicherung wird der Versand durchgeführt. Siehe [Versandausführung](../../message-center/using/delivery-execution.md). Jeder Empfänger erhält eine personalisierte Nachricht.

## Verwandte Themen {#related-topics}

* [Erste Schritte mit Kommunikationskanälen](../../delivery/using/communication-channels.md)
* [Wichtige Schritte bei der Versanderstellung](../../delivery/using/steps-about-delivery-creation-steps.md)
* [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md)
* [Transaktionsnachrichten-Berichte aufrufen](../../message-center/using/about-transactional-messaging-reports.md)
