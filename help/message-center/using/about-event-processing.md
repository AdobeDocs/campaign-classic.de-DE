---
product: campaign
title: Ereignisverarbeitung
description: Erfahren Sie, wie die Transaktionsnachrichten-Ereignisse in Adobe Campaign Classic verarbeitet werden.
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: b46a483594f210c4530a934194c6d2b73deaeaf9
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 30%

---

# Ereignisverarbeitung {#about-event-processing}

Im Zusammenhang mit Transaktionsnachrichten wird von einem externen Informationssystem ein Ereignis generiert und über die Methoden **[!UICONTROL PushEvent]** und **[!UICONTROL PushEvents]** an Adobe Campaign gesendet (siehe [Ereignisbeschreibung](../../message-center/using/event-description.md)).

Dieses Ereignis enthält Daten, die mit dem Ereignis verknüpft sind, wie z. B. sein [Typ](../../message-center/using/creating-event-types.md) (Bestellbestätigung, Kontoerstellung auf einer Website usw.), E-Mail-Adresse oder Mobiltelefonnummer sowie weitere Informationen, mit denen Sie die Transaktionsnachricht vor dem Versand anreichern und personalisieren können (Kundenkontaktdaten, Sprache der Nachricht, E-Mail-Format usw.).

Beispiel für Ereignisdaten:

![](assets/messagecenter_events_request_001.png)

## Schritte zur Ereignisverarbeitung {#event-processing}

Um Transaktionsnachrichten-Ereignisse zu verarbeiten, werden die folgenden Schritte auf die Ausführungsinstanz(en) angewendet:

1. [Ereigniskollektion](#event-collection)
1. [Weiterleitung des Ereignisses zu einer Nachrichtenvorlage](#routing-towards-a-template)
1. Anreicherung des Ereignisses mit Personalisierungsdaten
1. [Versandausführung](../../message-center/using/delivery-execution.md)
1. [Recycling von ](#event-recycling) Ereignissen, deren verknüpfte Bereitstellung fehlgeschlagen ist (über einen Adobe Campaign-Workflow)

Sobald alle oben genannten Schritte in der Ausführungsinstanz ausgeführt werden, erhält jeder Zielgruppenempfänger eine personalisierte Nachricht.

>[!NOTE]
>
>Weitere Informationen zu den Instanzen von Transaktionsnachrichten finden Sie unter [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md).


## Ereignisabruf {#event-collection}

Die vom Informationssystem erzeugten Ereignisse können auf zwei Weisen abgerufen werden:

* Aufrufe von SOAP-Methoden ermöglichen das Pushen von Ereignissen in Adobe Campaign: Wenn Sie mit der Methode PushEvent jeweils ein Ereignis senden, können Sie mit der Methode PushEvents mehrere Ereignisse gleichzeitig senden. Weitere Informationen hierzu finden Sie unter [Ereignisbeschreibung](../../message-center/using/event-description.md).

* Ausführung eines Workflows, der den Abruf der Ereignisse über einen Dateiimport oder ein SQL-Gateway ermöglicht (mit der Option [Federated Data Access](../../installation/using/about-fda.md)).

Nach der Erfassung werden die Ereignisse durch technische Workflows zwischen Echtzeit- und Batch-Warteschlangen der Ausführungsinstanz(en) aufgeschlüsselt, wobei darauf gewartet wird, mit einer Nachrichtenvorlage verknüpft zu werden.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Auf den Ausführungsinstanzen dürfen die Ordner **[!UICONTROL Echtzeit-Ereignisse]** oder **[!UICONTROL Batch-Ereignisse]** nicht als Ansichten festgelegt werden, da dies zu Problemen mit Zugriffsrechten führen könnte. Weitere Informationen zum Festlegen eines Ordners als Ansicht finden Sie in [diesem Abschnitt](../../platform/using/access-management-folders.md).

## Weiterleitung zu Vorlagen {#routing-towards-a-template}

Nach der Publikation der Nachrichtenvorlage in der/den Ausführungsinstanz(en) werden zwei Vorlagen automatisch erzeugt: eines, das mit einem Echtzeit-Ereignis verknüpft werden soll, und eines, das mit einem Batch-Ereignis verknüpft werden soll.

Der Routing-Schritt besteht in der Verknüpfung eines Ereignisses mit der entsprechenden Nachrichtenvorlage basierend auf:

* Der in den Eigenschaften des Ereignisses selbst angegebene Ereignistyp:

   ![](assets/messagecenter_event_type_001.png)

* Der in den Eigenschaften der Nachrichtenvorlage angegebene Ereignistyp:

   ![](assets/messagecenter_event_type_002.png)

Standardmäßig beruht das Routing auf den folgenden Informationen:

* dem Ereignistyp
* dem verwendeten Kanal (standardmäßig: E-Mail)
* der auf dem Veröffentlichungsdatum basierenden letzten Versandvorlage

## Ereignisstatus {#event-statuses}

Im **Ereignisverlauf** unter **[!UICONTROL Message Center]** > **[!UICONTROL Ereignisverlauf]** werden alle verarbeiteten Ereignisse in einer gemeinsamen Übersicht zusammengefasst. Sie können entweder nach Ereignistyp oder nach **Status** kategorisiert werden. Folgende Status existieren:

* **Ausstehend**: Das Ereignis kann:

   * Ein Ereignis, das gerade erfasst wurde und noch nicht verarbeitet wurde. Die Spalte **[!UICONTROL Fehleranzahl]** enthält den Wert 0. Die E-Mail-Vorlage wurde noch nicht zugeordnet.
   * Ein verarbeitetes Ereignis, dessen Bestätigung jedoch fehlerhaft ist. Die Spalte **[!UICONTROL Fehleranzahl]** enthält einen Wert, der nicht 0 ist. In der Spalte **[!UICONTROL Verarbeitung angefordert für]** können Sie sehen, wann dieses Ereignis erneut verarbeitet wird.

* **Versand ausstehend**: Das Ereignis wurde verarbeitet und die Versandvorlage wurde verknüpft. Die E-Mail steht vor dem Versand und der klassische Versandprozess wird angewendet. Weitere Informationen erhalten Sie, wenn Sie den  [Versand](../../delivery/using/about-message-tracking.md) öffnen.
* **Gesendet**,  **** Ignoriert und  **Versandfehler**: Diese Versandstatus werden über den  **** updateEventsStatus -Workflow abgerufen. Für weitere Informationen können Sie den entsprechenden Versand öffnen.
* **Ereignis wurde nicht berücksichtigt**: Die Routing-Phase der Transaktionsnachrichten schlug fehl. Beispielsweise konnte Adobe Campaign die E-Mail, die als Vorlage für das Ereignis dient, nicht finden.
* **Ereignis ist abgelaufen**: Die maximale Anzahl von Versandversuchen wurde erreicht. Das Ereignis wird als null betrachtet.

## Ereignis-Recycling {#event-recycling}

Wenn der Versand einer Nachricht über einen bestimmten Kanal fehlschlägt, kann Adobe Campaign über einen anderen Kanal einen erneuten Versandversuch starten. Wenn beispielsweise der Versand einer Nachricht über den SMS-Kanal fehlschlägt, wird die Nachricht über den E-Mail-Kanal erneut versandt.

Konfigurieren Sie hierzu einen Workflow, der alle Ereignisse mit **Versandfehler** neu erstellt und ihnen einen sich vom ersten Kanal unterscheidenden Kanal zuordnet.

>[!CAUTION]
>
>Dieser Schritt kann nur mithilfe eines Workflows durchgeführt werden und ist daher erfahrenen Benutzern vorbehalten. Weitere Informationen erhalten Sie von Ihrem Kundenbetreuer bei der Adobe.