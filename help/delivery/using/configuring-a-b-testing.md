---
product: campaign
title: Konfigurieren von A/B-Tests
description: Erfahren Sie, wie Sie in Campaign A/B-Tests konfigurieren.
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 98%

---

# Konfigurieren von A/B-Tests {#configuring-a-b-testing}

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

Sie können den Workflow jetzt starten. Sobald die Sendungen ausgeführt wurden, können Sie das Verhalten der drei Untermengen in den Versand-Logs nachverfolgen, um zu sehen, welcher Betreff am erfolgreichsten war.

Mithilfe von Workflows können Sie Ihre Prozesse auch automatisieren, indem Sie automatisch die Versandvariante identifizieren, die besser abgeschnitten hat, und diese dann an die verbleibende Population senden. Weitere Informationen dazu finden Sie im [entsprechenden Anwendungsbeispiel](a-b-testing-use-case.md).
