---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit A/B-Tests
description: Erfahren Sie mehr über A/B-Tests in Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Erste Schritte mit A/B-Tests {#get-started-a-b-testing}

Mit A/B-Tests können Sie mehrere Versionen eines Versands miteinander vergleichen, um herauszufinden, welche Version die größte Auswirkung auf die Zielgruppe hat.

Dazu müssen Sie zunächst mehrere Varianten des Versands definieren. Jede Variante wird dann an Populationsbeispiele gesendet, um festzustellen, welche besser funktioniert, je nach den Kriterien Ihrer Wahl (öffnet, Spam-Beschwerden, Klicks auf einen bestimmten Link, ...).

Im folgenden Beispiel wurde die Zielgruppe des Versands in zwei Gruppen aufgeteilt, die jeweils 50 % der Zielgruppe ausmachen. Jede Gruppe erhält zwei Versionen des Versands mit zwei verschiedenen Promo-Angeboten. Nach dem Senden des Versands wird der Schluss gezogen, dass Variante A besser abschneidet, basierend auf der Anzahl der Klicks auf die Angebot der Promotion.

![](assets/a-b-testing-schema.png)

Mit Campaign Classic werden A/B-Tests über Workflows implementiert, in denen Sie die zu Zielgruppe Population sowie die Gruppen angeben, die die einzelnen Varianten erhalten (siehe [Konfigurieren von a/b-Tests](../../delivery/using/configuring-a-b-testing.md)).

Die wichtigsten Schritte sind:

1. **Targeting** der gewünschten Population.
1. **Teilen Sie die** Population in Untergruppen auf, auf denen Sie die Varianten Ihres Versands testen möchten.

   Sie können beispielsweise eine Version eines Versands an einen kleinen Teil der Zielgruppe und eine andere an die restliche Zielgruppe senden. Auf diese Weise können Sie eine neue Version eines Versands testen, im Gegensatz zu dem Versand, der normalerweise an Ihre Kunden gesendet wird. Sie können die Zielgruppe auch in drei Gruppen unterteilen, um ihnen drei verschiedene Versionen eines Versands zu senden.

1. **Erstellen Sie mehrere** Versionen des Versands, die den einzelnen Untergruppen entsprechen. Die zu testende Variante kann der Betreff, der Inhalt der Nachricht, der Name des Absenders usw. sein.
1. Beginn Sie den Workflow und verwenden Sie dann die **Versandlogs**, um das Verhalten der Untergruppen mit jeder Variante zu analysieren.

>[!NOTE]
>
>Workflows ermöglichen Ihnen auch, Ihre Prozesse zu automatisieren, indem Sie automatisch die Versand-Variante identifizieren, die besser abgeschnitten hat, und diese dann an die restliche Population senden. Weitere Informationen hierzu finden Sie in diesem dedizierten [Anwendungsfall](../../delivery/using/a-b-testing-use-case.md).
