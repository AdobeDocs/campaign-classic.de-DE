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
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 75%

---


# Import und Export von Zielgruppen{#importing-and-exporting-audiences}



## Audience importieren {#importing-an-audience}

Sie können Zielgruppen/Segmente aus Audience Manager über die Empfängerlisten in Adobe Campaign importieren.

1. Gehen Sie in den Knoten **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Listen]** des Adobe Campaign Explorer.
1. Klicken Sie in der Aktionsleiste auf die Schaltfläche **[!UICONTROL Neu]** > **[!UICONTROL Freigegebene Zielgruppe erstellen...]**

   ![](assets/aam_import_audience.png)

1. Klicken Sie dann im sich öffnenden Fenster auf **[!UICONTROL Freigegebene Zielgruppe auswählen]**, um auf die Liste der von anderen Adobe Experience Cloud-Lösungen freigegebenen Audiences/Segmente zugreifen zu können.
1. Wählen Sie die gewünschte Audience aus und validieren Sie. Die Informationen zur ausgewählten Audience werden automatisch ausgefüllt.

   Um freigegebene Zielgruppen importieren zu können, sollte Ihnen das Produkt **[!UICONTROL Audience Library]** in der Admin Console zugewiesen worden sein. Außerdem sollten Sie in Audience Manager Administratorrechte besitzen. Weiterführende Informationen dazu finden Sie im [Handbuch zur Admin Console](https://helpx.adobe.com/de/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Wählen Sie im Feld **[!UICONTROL AMC Data source]** die Adobe-Marketing-Cloud-Datenquelle aus, um den erwarteten Datentyp zu definieren.

   ![](assets/aam_import_audience_2.png)

1. Speichern Sie die Audience.

Die Audience wird mithilfe eines technischen Workflows importiert. Die importierte Liste enthält die Elemente, die mithilfe der AMC-Datenquelle abgestimmt werden konnten. Von Adobe Campaign nicht erkannte Elemente werden nicht importiert.

Die Synchronisation des Importvorgangs dauert 24 bis 36 Stunden, wenn Segmente direkt aus Audience Manager importiert werden. Danach ist die neue Audience in Adobe Campaign auffindbar und verwendbar.

>[!NOTE]
>
>Wenn Sie Zielgruppen aus Adobe Analytics in Adobe Campaign importieren, müssen diese Zielgruppen zunächst in Audience Manager freigegeben werden. Dieser Vorgang dauert 12-24 Stunden, die zu der 24-36-Stunden-Synchronisation mit Campaign hinzugefügt werden müssen.
>
>Die Freigabe einer Audience kann demnach bis zu 60 Stunden dauern. Weitere Informationen zur Freigabe von Adobe Analytics-Zielgruppen in Audience Manager finden Sie unter [Adobe Analytics-Dokumentation](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de){target="_blank"}.

Bei jeder späteren Synchronisation werden alle Daten der zuvor erstellten Audience vollständig ersetzt. Nur Segmente können importiert werden. Granulare Daten wie Schlüssel/Wert-Paare, Merkmale und Regeln werden nicht unterstützt.

## Audiences exportieren {#exporting-an-audience}

Sie können eine Zielgruppe mithilfe eines Workflows aus Adobe Campaign in Audience Manager exportieren. Weiterführende Informationen zur Erstellung und Verwendung von Workflows finden Sie in [diesem Dokument](../../workflow/using/building-a-workflow.md). Die exportierten Zielgruppen werden als Segmente gespeichert:

1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Verwenden Sie die diversen zur Verfügung stehenden Aktivitäten, um eine Gruppe von Empfängern auszuwählen.
1. Platzieren Sie im Anschluss an die Zielgruppenbestimmung die Aktivität **[!UICONTROL Aktualisierung freigegebener Zielgruppe]** im Workflow-Diagramm und öffnen Sie sie.

   ![](assets/aam_export_example.png)

1. Definieren Sie die zu exportierende Audience anhand der Option **[!UICONTROL Freigegebene Zielgruppe auswählen]**. Im sich öffnenden Fenster können Sie zwischen der Auswahl einer existierenden und der Erstellung einer neuen Audience wählen.

   Wenn Sie eine existierende Audience verwenden, wird sie mit den neuen Datensätzen ergänzt.

   Zum Export der Empfängerliste in eine neue Audience ist zunächst das Feld **[!UICONTROL Segment name]** auszufüllen. Klicken Sie dann auf **[!UICONTROL Create]**, um die Audience zu erstellen, und wählen Sie diese für den Export aus.

   Schließen Sie den Vorgang ab, indem Sie auf die Validierungsschaltfläche oben rechts im Fenster und dann auf **[!UICONTROL OK]** klicken.

1. Wählen Sie im Feld **[!UICONTROL AMC Data source]** die Adobe-Marketing-Cloud-Datenquelle aus, um den erwarteten Datentyp zu definieren. Das Schema wird automatisch abgeleitet.

   ![](assets/aam_export_audience_activity.png)

1. Speichern Sie die Audience.

Die Audience wird daraufhin exportiert. Die Aktivität zum Audience-Export weist zwei ausgehende Transitionen auf. Die erste Transition enthält die Empfänger, die erfolgreich exportiert wurden. Die zweite Transition enthält die Empfänger, denen keine Besucherkennung oder Declared ID zugeordnet werden konnte.

Die Synchronisation zwischen Lösungen dauert 24 bis 36 Stunden. Danach können Sie Ihre neue Zielgruppe finden und sie in anderen Adobe Experience Cloud-Lösungen wiederverwenden. Weiterführende Informationen zur Verwendung einer freigegebenen Adobe Campaign-Zielgruppe finden Sie in diesem Abschnitt [Dokumentation](https://experienceleague.adobe.com/en/docs/core-services/interface/services/audiences/create){target="_blank"}.

>[!NOTE]
>
>Um abgestimmt werden zu können, müssen die Datensätze eine Adobe Experience Cloud-Kennung (&#39;visitor ID&#39; oder &#39;declared ID&#39;) aufweisen. Datensätze, die keine Adobe Experience Cloud-Kennung aufweisen, werden beim Import und Export der Audiences ignoriert.
