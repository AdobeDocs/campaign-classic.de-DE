---
product: campaign
title: Import und Export von Zielgruppen
description: Import und Export von Zielgruppen
feature: Audiences
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
TQID: https://experienceleague.adobe.com/bOM6WFh4gyejeYtHdOSBO3jbY4LFvLB--P5pxN5t5O0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 657
ht-degree: 100%

---

# Import und Export von Zielgruppen{#importing-and-exporting-audiences}



## Zielgruppe importieren {#importing-an-audience}

Der Import von Zielgruppen/Segmenten aus Audience Manager in Adobe Campaign erfolgt mithilfe von Empfängerlisten.

1. Gehen Sie in den Knoten **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Listen]** des Adobe Campaign Explorer.
1. Klicken Sie in der Aktionsleiste auf die Schaltfläche **[!UICONTROL Neu]** > **[!UICONTROL Freigegebene Zielgruppe erstellen...]**

   ![](assets/aam_import_audience.png)

1. Klicken Sie dann im sich öffnenden Fenster auf **[!UICONTROL Freigegebene Zielgruppe auswählen]**, um auf die Liste der von anderen Adobe Experience Cloud-Lösungen freigegebenen Audiences/Segmente zugreifen zu können.
1. Wählen Sie eine Zielgruppe aus und bestätigen Sie. Die Informationen zur Zielgruppe werden automatisch ausgefüllt.

   Um freigegebene Zielgruppen importieren zu können, sollte Ihnen das Produkt **[!UICONTROL Audience Library]** in der Admin Console zugewiesen worden sein. Außerdem sollten Sie in Audience Manager Administratorrechte besitzen. Weiterführende Informationen dazu finden Sie im [Handbuch zur Admin Console](https://helpx.adobe.com/de/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Wählen Sie im Feld **[!UICONTROL AMC Data source]** die Adobe-Marketing-Cloud-Datenquelle aus, um den erwarteten Datentyp zu definieren.

   ![](assets/aam_import_audience_2.png)

1. Speichern Sie die Zielgruppe.

Die Zielgruppe wird dann mithilfe eines technischen Workflows importiert. Die importierte Liste enthält Elemente, die mithilfe der AMC-Datenquelle abgestimmt werden können. Von Adobe Campaign nicht erkannte Elemente werden nicht importiert.

Wenn Segmente direkt aus Audience Manager importiert werden, dauert die Synchronisation des Imports 24 bis 36 Stunden. Danach ist die neue Zielgruppe in Adobe Campaign auffindbar und kann verwendet werden.

>[!NOTE]
>
>Beim Import von Zielgruppen von Adobe Analytics nach Adobe Campaign müssen diese Zielgruppen zuerst in Audience Manager freigegeben werden. Dieser Prozess dauert 12 bis 24 Stunden, die zu den 24 bis 36 Stunden für die Synchronisation mit Campaign hinzugezählt werden müssen.
>
>Die Freigabe einer Zielgruppe kann demnach in diesem Fall bis zu 60 Stunden dauern. Weitere Informationen zur Freigabe einer Adobe Analytics-Zielgruppe in Audience Manager finden Sie in der [Dokumentation zu Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de){target="_blank"}.

Bei jeder späteren Synchronisation werden alle Daten der zuvor erstellten Zielgruppe vollständig ersetzt. Nur Segmente können importiert werden. Granulare Daten wie Schlüssel/Wert-Paare, Merkmale und Regeln werden nicht unterstützt.

## Zielgruppe exportieren {#exporting-an-audience}

Der Export von Zielgruppen aus Adobe Campaign in Audience Manager erfolgt mithilfe eines Workflows. Weiterführende Informationen zur Erstellung und Verwendung von Workflows finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=de){target="_blank"}. Die exportierten Zielgruppen werden als Segmente gespeichert:

1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Verwenden Sie die diversen zur Verfügung stehenden Aktivitäten, um eine Gruppe von Empfängern auszuwählen.
1. Platzieren Sie im Anschluss an die Zielgruppenbestimmung die Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppe]** im Workflow-Diagramm und öffnen Sie sie.

   ![](assets/aam_export_example.png)

1. Definieren Sie über die Option **[!UICONTROL Freigegebene Zielgruppe auswählen]** eine Zielgruppe, die Sie exportieren möchten. Im sich öffnenden Fenster können Sie eine vorhandene Zielgruppe auswählen oder eine neue Zielgruppe erstellen.

   Wenn Sie eine existierende Zielgruppe verwenden, wird sie mit den neuen Datensätzen ergänzt.

   Zum Export der Empfängerliste in eine neue Zielgruppe ist zunächst das Feld **[!UICONTROL Segment name]** auszufüllen. Klicken Sie dann auf **[!UICONTROL Create]**, um die Zielgruppe zu erstellen, und wählen Sie diese für den Export aus.

   Schließen Sie den Vorgang ab, indem Sie auf die Validierungsschaltfläche oben rechts im Fenster und dann auf **[!UICONTROL OK]** klicken.

1. Wählen Sie die **[!UICONTROL AMC-Datenquelle]** aus, um den erwarteten Datentyp anzugeben. Das Schema wird automatisch bestimmt.

   ![](assets/aam_export_audience_activity.png)

1. Speichern Sie die Zielgruppe.

Die Zielgruppe wird dann exportiert. Die Aktivität „Zielgruppe speichern“ hat zwei ausgehende Transitionen. Die Haupttransition enthält die Empfängerinnen und Empfänger, die erfolgreich exportiert wurden. Die zusätzliche Transition enthält die Empfangenden, die keiner Besucher-ID oder deklarierten ID zugeordnet werden konnten.

Die Synchronisation zwischen Lösungen dauert 24 bis 36 Stunden. Danach ist Ihre neue Zielgruppe auffindbar und kann in anderen Adobe Experience Cloud-Lösungen verwendet werden. Weiterführende Informationen zur Verwendung einer in Adobe Campaign freigegebenen Zielgruppe finden Sie in dieser [Dokumentation](https://experienceleague.adobe.com/de/docs/core-services/interface/services/audiences/create){target="_blank"}.

>[!NOTE]
>
>Damit die Einträge abgestimmt werden können, müssen sie eine Adobe Experience Cloud-Kennung („Visitor ID“ oder „Declared ID“) aufweisen. Einträge, die keine Adobe Experience Cloud-ID aufweisen, werden beim Import und Export der Zielgruppen ignoriert.
