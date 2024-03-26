---
product: campaign
title: Import und Export von Zielgruppen
description: Import und Export von Zielgruppen
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: c2293fc5-c9ba-4a73-8f39-fa7cdd06e8dd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 87%

---


# Import und Export von Zielgruppen{#importing-and-exporting-audiences}



## Audience importieren {#importing-an-audience}

Der Import von Audiences/Segmenten aus Audience Manager oder People Core Service in Adobe Campaign erfolgt mithilfe von Empfängerlisten.

1. Gehen Sie in den Knoten **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Listen]** des Adobe Campaign Explorer.
1. Klicken Sie in der Aktionsleiste auf die Schaltfläche **[!UICONTROL Neu]** > **[!UICONTROL Freigegebene Zielgruppe erstellen...]**

   ![](assets/aam_import_audience.png)

1. Klicken Sie dann im sich öffnenden Fenster auf **[!UICONTROL Freigegebene Zielgruppe auswählen]**, um auf die Liste der von anderen Adobe Experience Cloud-Lösungen freigegebenen Audiences/Segmente zugreifen zu können.
1. Wählen Sie die gewünschte Audience aus und validieren Sie. Die Informationen zur ausgewählten Audience werden automatisch ausgefüllt.

   Um freigegebene Zielgruppen importieren zu können, sollte Ihnen die **[!UICONTROL Zielgruppenbibliothek]** -Produkt in der Admin Console verwenden und Administrator in Audience Manager sein. Weitere Informationen hierzu finden Sie im Abschnitt [Dokumentation zur Admin Console](https://helpx.adobe.com/de/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Wählen Sie im Feld **[!UICONTROL AMC Data source]** die Adobe-Marketing-Cloud-Datenquelle aus, um den erwarteten Datentyp zu definieren.

   ![](assets/aam_import_audience_2.png)

1. Speichern Sie die Audience.

Die Audience wird mithilfe eines technischen Workflows importiert. Die importierte Liste enthält die Elemente, die mithilfe der AMC-Datenquelle abgestimmt werden konnten. Von Adobe Campaign nicht erkannte Elemente werden nicht importiert.

Wenn Segmente direkt von People Core Service oder Audience Manager importiert werden, dauert die Synchronisation des Imports 24 bis 36 Stunden. Danach ist die neue Audience in Adobe Campaign auffindbar und verwendbar.

>[!NOTE]
>
>Wenn Sie Audiences aus Adobe Analytics in Adobe Campaign importieren, müssen diese Audiences zunächst in People Core Service oder Audience Manager freigegeben werden. Dieser Vorgang dauert 12 bis 24 Stunden. Diese Zeit muss zu den 24 bis 36 Stunden für die Synchronisation mit Campaign addiert werden.
>
>Die Freigabe einer Audience kann demnach bis zu 60 Stunden dauern. Weitere Informationen zur Freigabe einer Adobe Analytics-Audience in People Core Service und Audience Manager finden Sie in der [Dokumentation zu Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=de).

Bei jeder späteren Synchronisation werden alle Daten der zuvor erstellten Audience vollständig ersetzt. Nur Segmente können importiert werden. Granulare Daten wie Schlüssel/Wert-Paare, Merkmale und Regeln werden nicht unterstützt.

## Audiences exportieren {#exporting-an-audience}

Sie können eine Zielgruppe mithilfe eines Workflows aus Adobe Campaign in Audience Manager oder People Core Service exportieren. Die Prozesse zum Erstellen und Verwenden eines Workflows werden im Abschnitt [dieses Dokuments](../../workflow/using/building-a-workflow.md). Die exportierten Zielgruppen werden als Segmente in People Core Service gespeichert:

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

Die Synchronisation von Adobe Campaign und People Core Service dauert 24 bis 36 Stunden. Danach ist Ihre neue Audience in People Core Service auffindbar und kann in anderen Adobe Experience Cloud-Lösungen verwendet werden. Weiterführende Informationen zur Verwendung einer in Adobe Campaign freigegebenen Audience in Adobe People Core Service finden Sie in dieser [Dokumentation](https://experienceleague.adobe.com/docs/core-services/interface/audiences/t-audience-create.html?lang=de).

>[!NOTE]
>
>Um abgestimmt werden zu können, müssen die Datensätze eine Adobe Experience Cloud-Kennung (&#39;visitor ID&#39; oder &#39;declared ID&#39;) aufweisen. Datensätze, die keine Adobe Experience Cloud-Kennung aufweisen, werden beim Import und Export der Audiences ignoriert.
