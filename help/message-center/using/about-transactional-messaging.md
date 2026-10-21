---
product: campaign
title: Erste Schritte mit Transaktionsnachrichten
description: Erfahren Sie mehr über die Funktionsweise von Transaktionsnachrichten in Adobe Campaign Classic und die wichtigsten Schritte für ihre Verwendung
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: ht
source-wordcount: '610'
ht-degree: 100%
---
# Erste Schritte mit Transaktionsnachrichten {#about-transactional-messaging}



## Übersicht {#overview}

Der **Transaktionsnachrichtenversand** (Message Center) ist ein Campaign-Modul zur Verwaltung von Benachrichtigungen bei benutzerspezifischen Triggern. Diese werden von Ereignissen generiert, die von einem externen Informationssystem gesendet werden.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zu transaktionalem Messaging finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

Dieser Abschnitt behandelt die Architektur für transaktionales Messaging und die Konfiguration der Steuerungs- und Ausführungsinstanzen speziell für On-Premise- und Hybrid-Bereitstellungen.

>[!IMPORTANT]
>
>Für Transaktionsnachrichten ist eine spezifische Lizenz erforderlich. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Funktionsweise von Transaktionsnachrichten {#transactional-messaging-operating-principle}

Das Transaktionsnachrichtenmodul von Adobe Campaign ist in ein Informationssystem integriert, das Ereignisse zurückgibt, die in personalisierte Transaktionsnachrichten umgewandelt werden. Diese Nachrichten können einzeln oder in Batches per E-Mail, SMS oder Push-Benachrichtigungen gesendet werden.

Grundlage dieser Funktion ist eine spezielle Architektur, bei der die **Ausführungsinstanz** von der **Kontrollinstanz** getrennt ist. Durch diese Unterteilung wird eine höhere Verfügbarkeit sowie eine bessere Lastverwaltung gewährleistet. Weiterführende Informationen hierzu finden Sie unter [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Um neue Benutzer für in Adobe Cloud gehostete Message Center-Ausführungsinstanzen zu erstellen, kontaktieren Sie die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Benutzer von Message Center benötigen spezifische Berechtigungen für den Zugriff auf die Ordner für **[!UICONTROL Echtzeit-Ereignisse (nmsRtEvent)]**.

>[!NOTE]
>
>In Adobe Campaign hat die Verarbeitung von Transaktionsnachrichten Priorität vor allen anderen Sendungen.

## Die wichtigsten Schritte {#key-steps}

Die wichtigsten Schritte beim Erstellen und Verwalten personalisierter Transaktionsnachrichten in Adobe Campaign sind im Folgenden zusammengefasst.

### Auf der Kontrollinstanz durchzuführende Schritte

Führen Sie auf der **Kontrollinstanz** die folgenden Aktionen aus:

1. [Erstellen Sie einen Ereignistyp](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"} (Dokumentation zu Campaign v8).
1. [Erstellen und gestalten Sie die Nachrichtenvorlage](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (Dokumentation zu Campaign v8). Bei diesem Schritt müssen Sie ein Ereignis mit Ihrer Nachricht verknüpfen.
1. [Testen Sie die Nachricht](../../message-center/using/testing-message-templates.md).
1. [Veröffentlichen Sie die Nachrichtenvorlage](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} (Dokumentation zu Campaign v8).

>[!NOTE]
>
>Die oben genannten Schritte werden allesamt auf der **Kontrollinstanz** ausgeführt. Das Veröffentlichen der Vorlage auf der Kontrollinstanz hat zur Folge, dass sie auch auf allen **Ausführungsinstanzen** veröffentlicht wird. Näheres zu Instanzen für Transaktionsnachrichten finden Sie unter [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md).

### Ereignisverarbeitung auf der Ausführungsinstanz

Nachdem Sie die Transaktionsnachrichtenvorlage erstellt und veröffentlicht haben und ein entsprechendes Ereignis ausgelöst wurde, werden die folgenden Hauptschritte auf der **Ausführungsinstanz** ausgeführt:

1. Wenn das Ereignis vom externen Informationssystem generiert wird, werden die relevanten Daten über die Methoden **PushEvent** und **PushEvents** an Campaign gesendet. Siehe [Ereignissammlung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"} (Dokumentation zu Campaign v8).
1. Das Ereignis wird der entsprechenden Nachrichtenvorlage zugeordnet. Siehe [Routing zu einer Vorlage](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"} (Dokumentation zu Campaign v8).
1. Nach Abschluss der Anreicherung wird der Versand durchgeführt. Siehe [Versandausführung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (Dokumentation zu Campaign v8). Jeder Zielkontakt erhält eine personalisierte Nachricht.

## Verwandte Themen {#related-topics}

* [Erste Schritte mit Kommunikationskanälen](../../delivery/using/communication-channels.md)
* [Wichtigste Schritte bei der Versanderstellung](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=de){target="_blank"}
* [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md)
* [Zugreifen auf Berichte zu Transaktionsnachrichten](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} (Dokumentation zu Campaign v8)
