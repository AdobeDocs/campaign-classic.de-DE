---
product: campaign
title: Ereignisverarbeitung
description: Erfahren Sie, wie Transaktionsnachrichtenereignisse in Adobe Campaign Classic verarbeitet werden
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
TQID: https://experienceleague.adobe.com/pex7wiGCNMdY86-Ug7dyLxE3RRT-ejlgz8eH7zVmZc4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: ht
source-wordcount: 728
ht-degree: 100%

---

# Ereignisverarbeitung {#about-event-processing}



Im Zusammenhang mit dem Transaktionsnachrichtenversand wird von einem externen Informationssystem ein Ereignis generiert und über die Methoden **[!UICONTROL PushEvent]** und **[!UICONTROL PushEvents]** an Adobe Campaign gesendet (siehe [Ereignisbeschreibung](../../message-center/using/event-description.md)).

Dieses Ereignis enthält Daten, die mit dem Ereignis verknüpft sind, darunter etwa dessen [Typ](../../message-center/using/creating-event-types.md) (Bestellbestätigung, Kontoerstellung auf einer Website usw.), dessen E-Mail-Adresse oder Mobiltelefonnummer sowie weitere Informationen, mit denen Sie die Transaktionsnachricht vor dem Versand anreichern und personalisieren können (Kundenkontaktdaten, Sprache der Nachricht, E-Mail-Format usw.).

Beispiel für Ereignisdaten:

![](assets/messagecenter_events_request_001.png)

## Schritte zur Ereignisverarbeitung {#event-processing}

Um Transaktionsnachrichten-Ereignisse zu verarbeiten, werden die folgenden Schritte auf der/den Ausführungsinstanz(en) ausgeführt:

1. [Ereignissammlung](#event-collection)
1. [Weiterleitung des Ereignisses zu einer Nachrichtenvorlage](#routing-towards-a-template)
1. Anreicherung des Ereignisses mit Personalisierungsdaten
1. [Versandausführung](../../message-center/using/delivery-execution.md)
1. [Recycling von Ereignissen](#event-recycling), bei denen der mit ihnen verknüpfte Versand fehlgeschlagen ist (über einen Adobe Campaign-Workflow)

Sobald alle oben genannten Schritte auf der Ausführungsinstanz ausgeführt wurden, erhält jeder Zielkontakt eine personalisierte Nachricht.

>[!NOTE]
>
>Näheres zu Instanzen für Transaktionsnachrichten finden Sie unter [Transaktionsnachrichten-Architektur](../../message-center/using/transactional-messaging-architecture.md).


## Ereignisabruf {#event-collection}

Die vom Informationssystem erzeugten Ereignisse können auf zwei Weisen abgerufen werden:

* Nutzung von SOAP-Methoden, die die Ereignisse Adobe Campaign zuführen: Die PushEvent-Methode ermöglicht den Versand eines Ereignisses, die PushEvents-Methode den Versand mehrerer Ereignisse auf einmal. Weiterführende Informationen hierzu finden Sie unter [Ereignisbeschreibung](../../message-center/using/event-description.md).

* Ausführung eines Workflows, der den Abruf der Ereignisse über einen Dateiimport oder ein SQL-Gateway ermöglicht (mit der Option [Federated Data Access](../../installation/using/about-fda.md)).

Nach dem Abruf werden die Ereignisse von den technischen Workflows auf die Echtzeit- und Batch-Warteschlangen der Ausführungsinstanzen verteilt, bis sie mit einer Nachrichtenvorlage verknüpft werden.

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>Auf den Ausführungsinstanzen dürfen die Ordner **[!UICONTROL Echtzeit-Ereignisse]** oder **[!UICONTROL Batch-Ereignisse]** nicht als Ansichten festgelegt werden, da dies zu Problemen mit Zugriffsrechten führen könnte. Weitere Informationen zum Festlegen eines Ordners als Ansicht finden Sie in der [Dokumentation zu Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.

## Weiterleitung zu Vorlagen {#routing-towards-a-template}

Nach der Veröffentlichung der Nachrichtenvorlage auf den Ausführungsinstanzen werden automatisch zwei Vorlagen erstellt: eine, die mit einem Echtzeit-Ereignis verknüpft wird, und eine, die mit einem Batch-Ereignis verknüpft wird.

Beim Routing-Schritt wird ein Ereignis mit der entsprechenden Nachrichtenvorlage verknüpft. Dies erfolgt basierend auf:

* dem in den Eigenschaften des Ereignisses angegebenen Ereignistyp:

  ![](assets/messagecenter_event_type_001.png)

* dem in den Eigenschaften der Nachrichtenvorlage angegebenen Ereignistyp:

  ![](assets/messagecenter_event_type_002.png)

Standardmäßig erfolgt das Routing auf Basis folgender Informationen:

* dem Ereignistyp
* dem verwendeten Kanal (standardmäßig: E-Mail)
* der auf dem Veröffentlichungsdatum basierenden letzten Versandvorlage

## Ereignisstatus {#event-statuses}

Im **Ereignisverlauf** unter **[!UICONTROL Message Center]** > **[!UICONTROL Ereignisverlauf]** werden alle verarbeiteten Ereignisse in einer gemeinsamen Übersicht zusammengefasst. Sie können entweder nach Ereignistyp oder nach **Status** kategorisiert werden. Folgende Status existieren:

* **Ausstehend**: Bei dem Ereignis kann es sich um Folgendes handeln:

   * Ereignis, das kurz zuvor eingetreten ist, jedoch noch nicht verarbeitet wurde. Die Spalte **[!UICONTROL Fehleranzahl]** gibt den Wert 0 an. Die E-Mail-Vorlage wurde noch nicht verknüpft.
   * Ereignis, das verarbeitet wurde, bei dessen Bestätigung jedoch Fehler aufgetreten sind. Die Spalte **[!UICONTROL Fehleranzahl]** zeigt einen Wert an, der nicht 0 ist. Um zu erfahren, wann dieses Ereignis erneut verarbeitet wird, konsultieren Sie die Spalte **[!UICONTROL Prozess angefordert am]**.

* **Versand ausstehend**: Das Ereignis wurde verarbeitet und die Versandvorlage ist verknüpft. Die E-Mail ist versandbereit und der klassische Versandprozess wird angewendet. Für weitere Informationen können Sie den Versand öffnen.
* **Gesendet**, **Ignoriert** und **Versandfehler**: Diese Versandstatus werden über den Workflow **updateEventsStatus** abgerufen. Für weitere Informationen können Sie den entsprechenden Versand öffnen.
* **Ereignis wurde nicht berücksichtigt**: Die Routing-Phase der Transaktionsnachricht ist fehlgeschlagen. Ein Beispiel hierfür wäre, dass Adobe Campaign die E-Mail, die als Vorlage für das Ereignis dient, nicht finden konnte.
* **Ereignis ist abgelaufen**: Die maximale Anzahl an Versandversuchen wurde erreicht. Das Ereignis wird als nichtig betrachtet.

## Ereignis-Recycling {#event-recycling}

Wenn der Versand einer Nachricht über einen bestimmten Kanal fehlschlägt, kann Adobe Campaign die Nachricht über einen anderen Kanal erneut senden. Wenn beispielsweise der Versand einer Nachricht über den SMS-Kanal fehlschlägt, wird die Nachricht über den E-Mail-Kanal erneut versandt.

Konfigurieren Sie hierzu einen Workflow, der alle Ereignisse mit **Versandfehler** neu erstellt und ihnen einen sich vom ersten Kanal unterscheidenden Kanal zuordnet.

>[!CAUTION]
>
>Dieser Schritt kann nur mithilfe eines Workflows durchgeführt werden und sollte daher erfahrenen Benutzern vorbehalten bleiben. Wenden Sie sich für weitere Informationen hierzu an Ihren Adobe-Kundenbetreuer.