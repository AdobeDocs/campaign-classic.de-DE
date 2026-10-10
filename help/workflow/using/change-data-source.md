---
title: Datenquelle ändern
description: Erfahren Sie mehr über die Aktivität "Datenquelle ändern".
feature: Workflows, Data Management, Federated Data Access
hide: true
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
TQID: 'https://experienceleague.adobe.com/VhOrIcFK-BbCuzPTC6Y8Px8u-VY0-4O86F8z8muZIHM'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
    internal-label: Data management
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 100%
---
# Datenquelle ändern {#change-data-source}

>[!NOTE]
>
> Die Aktivität **[!UICONTROL Datenquelle ändern]** ist nur mit dem Package **[!UICONTROL Zugriff auf externe Daten (Federated Data Access)]** verfügbar. Weitere Informationen zu integrierten Adobe Campaign Classic-Packages finden Sie auf dieser [Seite](../../installation/using/installing-campaign-standard-packages.md).

Die Aktivität **[!UICONTROL Datenquelle ändern]** ermöglicht es Ihnen, die Datenquelle des Workflows **[!UICONTROL Arbeitstabelle]** zu ändern. Dies bietet mehr Flexibilität bei der Verwaltung von Daten in verschiedenen Datenquellen wie FDA, FFDA und lokalen Datenbanken.

Die **[!UICONTROL Arbeitstabelle]** ermöglicht es dem Adobe Campaign Classic-Workflow, Daten zu verarbeiten und für die Workflow-Aktivitäten freizugeben.
Standardmäßig wird die **[!UICONTROL Arbeitstabelle]** in derselben Datenbank erstellt wie die Quelle der Daten, die abgefragt werden.

Wenn Sie beispielsweise die Tabelle **[!UICONTROL Profile]** in der Cloud-Datenbank abfragen, erstellen Sie eine **[!UICONTROL Arbeitstabelle]** in derselben Cloud-Datenbank.
Um dies zu ändern, können Sie die Aktivität **[!UICONTROL Datenquelle ändern]** hinzufügen, um eine andere Datenquelle für Ihre **[!UICONTROL Arbeitstabelle]** auszuwählen.

Beachten Sie, dass Sie bei Verwendung der Aktivität **[!UICONTROL Datenquelle ändern]** zur Cloud-Datenbank zurückkehren müssen, um die Ausführung des Workflows fortzusetzen.

So verwenden Sie die Aktivität **[!UICONTROL Datenquelle ändern]**:

1. Erstellen Sie einen Workflow.

1. Fragen Sie Ihre ausgewählten Empfänger mit einer **[!UICONTROL Abfrage]**-Aktivität ab.

   Weitere Informationen zur Aktivität **[!UICONTROL Abfrage]** erhalten Sie auf dieser [Seite](../../workflow/using/query.md#creating-a-query).

1. Fügen Sie in der Registerkarte **[!UICONTROL Targeting]** die Aktivität **[!UICONTROL Datenquelle ändern]** hinzu.

   ![](assets/change-data-source.png)

1. Doppelklicken Sie auf die Aktivität **[!UICONTROL Datenquelle ändern]**, um die **[!UICONTROL Standarddatenquelle]** auszuwählen.

   Die Arbeitstabelle, die das Ergebnis Ihrer Abfrage enthält, wird dann in die standardmäßige PostgreSQL-Datenbank verschoben.

   ![](assets/change-data-source_2.png)

1. Ziehen Sie aus der Registerkarte **[!UICONTROL Aktionen]** die Aktivität **[!UICONTROL JavaScript-Code]** per Drag-and-drop, um einzelne Vorgänge auf die Arbeitstabelle anzuwenden.

   Weitere Informationen zur Aktivität **[!UICONTROL JavaScript-Code]** finden Sie auf der Seite [JavaScript-Code und erweiterter JavaScript-Code](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

1. Fügen Sie eine weitere Aktivität vom Typ **[!UICONTROL Datenquelle ändern]** hinzu, um zur Cloud-Datenbank zurückzukehren.

1. Doppelklicken Sie auf Ihre Aktivität und wählen Sie **[!UICONTROL Aktives externes FDA-Konto]** und dann das entsprechende externe Konto für die **[!UICONTROL Externe Datenbank]** aus.

   ![](assets/change-data-source_3.png)

1. Sie können den Workflow jetzt starten.
