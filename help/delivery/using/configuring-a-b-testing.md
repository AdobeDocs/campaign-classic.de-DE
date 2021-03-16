---
solution: Campaign Classic
product: campaign
title: A/B-Tests konfigurieren
description: Erfahren Sie, wie Sie A/B-Tests in Campaign Classic konfigurieren.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: ht
source-git-commit: a341980e9d940857388bb2755e5eaa74824cf6ea
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---


# A/B-Tests konfigurieren {#configuring-a-b-testing}

In diesem Abschnitt wird beschrieben, wie Sie einen Workflow zum Durchführen von A/B-Tests erstellen.

1. Erstellen Sie einen neuen Workflow und konfigurieren Sie dann eine [Abfrageaktivität](../../workflow/using/query.md), um die gewünschte Population zu erfassen.

1. Fügen Sie eine [Aufspaltungsaktivität](../../workflow/using/split.md) hinzu, um die Zielpopulation in mehrere Untermengen zu unterteilen.

1. Öffnen Sie die Aktivität und konfigurieren Sie dann die einzelnen Untermengen entsprechend Ihren Anforderungen. Weitere Informationen zur Konfiguration einer **[!UICONTROL Aufspaltungsaktivität]** finden Sie in [diesem Abschnitt](../../workflow/using/split.md).

   In diesem Beispiel möchten wir zwei neue Themen für einen Newsletter testen, indem wir sie jeweils 10 % der Zielgruppe präsentieren.

   ![](assets/ab-testing-split.png)

1. Fügen Sie eine Transition hinzu, um an die verbleibende Population den Newsletter mit dem aktuellen Thema zu senden. Aktivieren Sie dazu die Option **[!UICONTROL Komplement erzeugen]** auf der Registerkarte **[!UICONTROL Allgemein]**.

   ![](assets/ab-testing-complement.png)

1. Fügen Sie für jede Untermenge die zu testende Version des Versands hinzu.

   ![](assets/ab-testing-delivery.png)

Sie können den Workflow jetzt starten. Sobald die Sendungen ausgeführt wurden, können Sie das Verhalten der drei Untermengen in den Versandlogs nachverfolgen, um zu sehen, welches Thema am erfolgreichsten war.

Mithilfe von Workflows können Sie Ihre Prozesse auch automatisieren, indem Sie automatisch die Versandvariante identifizieren, die besser abgeschnitten hat, und diese dann an die verbleibende Population senden. Weitere Informationen dazu finden Sie im [entsprechenden Anwendungsbeispiel](../../delivery/using/a-b-testing-use-case.md).
