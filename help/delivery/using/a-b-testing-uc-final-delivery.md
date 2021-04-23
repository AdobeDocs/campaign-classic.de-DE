---
solution: Campaign Classic
product: campaign
title: Endgültigen Versand festlegen
description: Erfahren Sie anhand eines speziellen Anwendungsbeispiels, wie Sie A/B-Tests durchführen.
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '121'
ht-degree: 100%

---

# Endgültigen Versand festlegen {#step-6--defining-the-final-delivery}

Nachdem das Script zur Ermittlung des Gewinners des A/B-Tests erstellt wurde, können Sie die Parameter des endgültigen Versands definieren.

1. Verbinden Sie die Aktivität **[!UICONTROL JavaScript-Code]** mit der restlichen **[!UICONTROL Versand]**-Aktivität.
1. Öffnen Sie die **[!UICONTROL Versand]**-Aktivität.
1. Deaktivieren Sie die Option **[!UICONTROL Ausgehende Transition erzeugen]**, um den Workflow mit dieser Aktivität abzuschließen.
1. Lassen Sie die Standardwerte der anderen Optionen unverändert.

   ![](assets/ab_test_final_delivery.png)

Durch die Vorbereitung des in der Transition spezifizierten Versands (definiert durch die **[!UICONTROL Javascript-Code]**-Aktivität), können Sie sie im Anschluss validieren und den Versand starten, wie im nächsten Schritt beschrieben wird.

Sie können jetzt den Workflow starten (siehe [Schritt 7: Workflow starten](../../delivery/using/a-b-testing-uc-start-workflow.md)).
