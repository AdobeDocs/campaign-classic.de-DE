---
product: campaign
title: Konfigurieren von A/B-Tests
description: Erfahren Sie, wie Sie in Campaign A/B-Tests konfigurieren.
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: 6adf2e75-63b1-44ad-8925-03beb3bc0bdd
TQID: https://experienceleague.adobe.com/PHIsuJZ-o5mBRAPggyVYdzS7PBXL9GYCBc6Fr56ur5Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 264
ht-degree: 100%

---

# Konfigurieren von A/B-Tests {#configuring-a-b-testing}

In diesem Abschnitt wird beschrieben, wie Sie einen Workflow zum Durchführen von A/B-Tests erstellen.

1. Erstellen Sie einen neuen Workflow und konfigurieren Sie dann eine Abfrageaktivität, um die gewünschte Population zu erfassen. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=de){target="_blank"}.

1. Fügen Sie eine Aufspaltungsaktivität hinzu, um die Zielpopulation in mehrere Untermengen zu unterteilen. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html?lang=de){target="_blank"}.

1. Öffnen Sie die Aktivität und konfigurieren Sie dann die einzelnen Untermengen entsprechend Ihren Anforderungen. Weitere Informationen zur Konfiguration einer **[!UICONTROL Aufspaltungsaktivität]** finden Sie in [diesem Abschnitt](../../workflow/using/split.md).

   In diesem Beispiel möchten wir zwei neue Themen für einen Newsletter testen, indem wir sie jeweils 10 % der Zielpopulation präsentieren.

   ![](assets/ab-testing-split.png)

1. Fügen Sie eine Transition hinzu, um an die verbleibende Population den Newsletter mit dem aktuellen Thema zu senden. Aktivieren Sie dazu die Option **[!UICONTROL Komplement erzeugen]** auf der Registerkarte **[!UICONTROL Allgemein]**.

   ![](assets/ab-testing-complement.png)

1. Fügen Sie für jede Untermenge die zu testende Version des Versands hinzu.

   ![](assets/ab-testing-delivery.png)

Sie können den Workflow jetzt starten. Sobald die Sendungen ausgeführt wurden, können Sie das Verhalten der drei Untermengen in den Versand-Logs nachverfolgen, um zu sehen, welcher Betreff am erfolgreichsten war.

Mithilfe von Workflows können Sie Ihre Prozesse auch automatisieren, indem Sie automatisch die Versandvariante identifizieren, die besser abgeschnitten hat, und diese dann an die verbleibende Population senden. Weitere Informationen dazu finden Sie im [entsprechenden Anwendungsbeispiel](a-b-testing-use-case.md).
