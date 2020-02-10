---
title: Zielgruppenimport und -export
seo-title: Zielgruppenimport und -export
description: Zielgruppenimport und -export
seo-description: null
page-status-flag: never-activated
uuid: af03ce68-8a58-4909-83e9-23c385820284
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f26cc65a-76be-4b7a-bde3-d0cbe3eedaaf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Zielgruppenimport und -export{#importing-and-exporting-audiences}

## Audience importieren {#importing-an-audience}

Der Import von Zielgruppen/Segmenten aus Audience Manager oder People Core Service in Adobe Campaign erfolgt mithilfe von Empfängerlisten.

1. Wechseln Sie zum Knoten **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Lists]** im Adobe Campaign-Explorer.
1. Wählen Sie in der Aktionsleiste **[!UICONTROL New]** > **[!UICONTROL Create a shared audience...]**.

   ![](assets/aam_import_audience.png)

1. In the window that opens, click **[!UICONTROL Select a shared audience]** to go to the list of shared audiences/segments available from the other Adobe Experience Cloud solutions.
1. Wählen Sie die gewünschte Zielgruppe aus und validieren Sie. Die Informationen zur ausgewählten Zielgruppe werden automatisch ausgefüllt.

   Bitte beachten Sie, dass Sie zum Importieren freigegebener Zielgruppen das Produkt in der Admin-Konsole und als Administrator in Audience Manager zuordnen **[!UICONTROL Audience library]** müssen. Weiterführende Informationen dazu finden Sie im [Handbuch zur Admin Console](https://helpx.adobe.com/enterprise/managing/user-guide.html).

   ![](assets/aam_import_audience_3.png)

1. Wählen Sie im Feld **[!UICONTROL AMC Data source]** die Adobe-Marketing-Cloud-Datenquelle aus, um den erwarteten Datentyp zu definieren.

   ![](assets/aam_import_audience_2.png)

1. Speichern Sie die Zielgruppe.

Die Zielgruppe wird mithilfe eines technischen Workflows importiert. Die importierte Liste enthält die Elemente, die mithilfe der AMC-Datenquelle abgestimmt werden konnten. Von Adobe Campaign nicht erkannte Elemente werden nicht importiert.

Wenn Segmente direkt von People Core Service oder Audience Manager importiert werden, dauert die Synchronisation des Imports 24 bis 36 Stunden. Danach ist die neue Audience in Adobe Campaign auffindbar und verwendbar.

>[!NOTE]
>
>Wenn Sie Zielgruppen aus Adobe Analytics in Adobe Campaign importieren, müssen diese Zielgruppen zunächst in People Core Service oder Audience Manager freigegeben werden. Dieser Vorgang dauert 12 bis 24 Stunden. Diese Zeit muss zu den 24 bis 36 Stunden für die Synchronisation mit Campaign addiert werden.
>
>In diesem speziellen Fall kann die Zielgruppenfreigabe bis zu 60 Stunden dauern. Weitere Informationen zur Adobe Analytics-Zielgruppenfreigabe in People Core Service und Audience Manager finden Sie in dieser [Dokumentation](https://marketing.adobe.com/resources/help/en_US/mcloud/t_publish_audience_segment.html).

Bei jeder späteren Synchronisation werden alle Daten der zuvor erstellten Zielgruppe vollständig ersetzt. Nur Segmente können importiert werden. Granulare Daten wie Schlüssel/Wert-Paare, Merkmale und Regeln werden nicht unterstützt.

## Audiences exportieren {#exporting-an-audience}

Der Export von Zielgruppen aus Adobe Campaign in Audience Manager oder People Core Service erfolgt mithilfe eines Workflows. Weiterführende Informationen zur Erstellung und Verwendung von Workflows finden Sie in [diesem Dokument](../../workflow/using/building-a-workflow.md). Die exportierten Zielgruppen werden in Form von Segmenten in People Core Service gespeichert:

1. Erstellen Sie einen neuen Zielgruppen-Workflow.
1. Verwenden Sie die diversen zur Verfügung stehenden Aktivitäten, um eine Gruppe von Empfängern auszuwählen.
1. After the targeting, drag and drop an **[!UICONTROL Update shared audience]** activity, then open it.

   ![](assets/aam_export_example.png)

1. Definieren Sie die Zielgruppe, die Sie über die **[!UICONTROL Select a shared audience]** Option exportieren möchten. Im sich öffnenden Fenster können Sie eine bestehende Zielgruppe auswählen oder eine neue Zielgruppe erstellen.

   Wenn Sie eine existierende Zielgruppe verwenden, wird sie mit den neuen Datensätzen ergänzt.

   Zum Export der Empfängerliste in eine neue Zielgruppe ist zunächst das Feld **[!UICONTROL Segment name]** auszufüllen. Klicken Sie dann auf **[!UICONTROL Create]**, um die Zielgruppe zu erstellen, und wählen Sie diese für den Export aus.

   Schließen Sie den Vorgang ab, indem Sie auf die Validierungsschaltfläche oben rechts im Fenster und dann auf **[!UICONTROL OK]** klicken.

1. Wählen Sie die **[!UICONTROL AMC Data source]** aus, um den erwarteten Datentyp anzugeben. Das Schema wird automatisch bestimmt.

   ![](assets/aam_export_audience_activity.png)

1. Speichern Sie die Zielgruppe.

Die Zielgruppe wird daraufhin exportiert. Die Aktivität zum Zielgruppenexport weist zwei ausgehende Transitionen auf. Die erste Transition enthält die Empfänger, die erfolgreich exportiert wurden. Die zweite Transition enthält die Empfänger, denen keine Besucherkennung oder Declared ID zugeordnet werden konnte.

Die Synchronisation von Adobe Campaign und People Core Service dauert 24 bis 36 Stunden. Danach ist Ihre neue Audience in People Core Service auffindbar und kann in anderen Adobe Experience Cloud-Lösungen verwendet werden. Weiterführende Informationen zur Verwendung einer in Adobe Campaign freigegebenen Audience in Adobe People Core Service finden Sie in dieser [Dokumentation](https://marketing.adobe.com/resources/help/en_US/mcloud/t_audience_create.html).

>[!NOTE]
>
>Um abgestimmt werden zu können, müssen die Datensätze eine Adobe-Experience-Cloud-Kennung (&#39;visitor ID&#39; oder &#39;declared ID&#39;) aufweisen. Datensätze, die keine Adobe-Experience-Cloud-Kennung aufweisen, werden beim Import und Export der Zielgruppen ignoriert.

