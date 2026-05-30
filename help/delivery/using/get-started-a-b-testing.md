---
product: campaign
title: Erste Schritte mit A/B-Tests
description: Erfahren Sie mehr über A/B-Tests in Campaign
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: A/B Testing
role: User
exl-id: ae046ef6-d850-4222-b82c-8ef5b3da7037
TQID: https://experienceleague.adobe.com/uqiRMLevklMVBiKDSdSy0309jsIBRr05w3mBgOF-RE8
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
source-wordcount: 363
ht-degree: 100%

---

# Erste Schritte mit A/B-Tests {#get-started-a-b-testing}


Mit A/B-Tests können Sie mehrere Versionen eines Versands miteinander vergleichen, um herauszufinden, welche Version die größte Wirkung auf die Zielpopulation hat.

Dazu müssen Sie zunächst mehrere Versandvarianten definieren. Jede Variante wird dann an Testpopulationen gesendet, um zu ermitteln, welche in Abhängigkeit von den von Ihnen gewählten Kriterien (Öffnungen, Spam-Beschwerden, Klicks auf einen bestimmten Link usw.) besser abschneidet.

Im folgenden Beispiel wurde die Zielgruppe des Versands in zwei Gruppen aufgeteilt, die jeweils 50 % der Zielpopulation ausmachen. Jede Gruppe erhält zwei Versionen des Versands mit zwei verschiedenen Werbeangeboten. Nach der Ausführung des Versands wird festgestellt, dass Variante A besser abschneidet – basierend auf der Anzahl der Klicks auf die Werbeangebote.

![](assets/a-b-testing-schema.png)

Mit Campaign Classic werden A/B-Tests über Workflows implementiert, in denen Sie die Zielpopulation sowie die Gruppen, die jede Variante erhalten sollen, festlegen (siehe [A/B-Tests konfigurieren](configuring-a-b-testing.md)).

Die wichtigsten Schritte sind:

1. **Festlegen** der gewünschten Population.
1. **Aufteilen der Population** in Untermengen, mit denen Sie die Varianten Ihres Versands testen möchten.

   Sie können beispielsweise eine Version eines Versands an einen kleinen Teil der Zielgruppe und eine andere an die restliche Population senden. Auf diese Weise können Sie eine neue Version eines Versands testen, im Gegensatz zum Versand, der normalerweise an Ihre Kunden gesendet wird. Sie können die Zielpopulation auch in drei Gruppen unterteilen, um ihnen drei verschiedene Versionen eines Versands zu senden.

1. **Erstellen mehrerer Versionen** des Versands, die den einzelnen Untermengen entsprechen. Die zu testende Variante kann der Betreff, der Inhalt der Nachricht, der Name des Absenders usw. sein.
1. Starten Sie den Workflow und analysieren Sie anhand der **Versand-Logs** das Verhalten der Untereinheiten für jede Variante.

>[!NOTE]
>
>Mithilfe von Workflows können Sie Ihre Prozesse auch automatisieren, indem Sie automatisch die Versandvariante identifizieren, die besser abgeschnitten hat, und diese dann an die verbleibende Population senden. Weitere Informationen dazu finden Sie im [entsprechenden Anwendungsbeispiel](a-b-testing-use-case.md).
