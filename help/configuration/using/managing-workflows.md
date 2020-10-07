---
title: Workflows verwalten
seo-title: Workflows verwalten
description: Workflows verwalten
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 5%

---


# Workflows verwalten{#managing-workflows}

Standardmäßig basieren Ihre neuen Workflows auf einer Workflow-Vorlage, die vorkonfiguriert wurde und auf einer Empfänger-Tabelle basiert (nms:Empfänger). Damit sie automatisch auf der benutzerdefinierten Tabelle der Empfänger basieren, auf die in der Option **Nms_DefaultRcpSchema** verwiesen wird (siehe Abschnitt [Konfigurieren der Schnittstelle](../../configuration/using/configuring-the-interface.md) ), müssen Sie eine neue Workflow-Vorlage erstellen.

Erstellen Sie eine neue Vorlage über den Knoten **[!UICONTROL Ressourcen > Vorlagen > Workflow-Vorlagen]** . Die in den Eigenschaften der Vorlage angegebenen Dimensionen entsprechen der Tabelle mit den externen Empfängern.

Wenn Sie Ihre neue Workflows auf einer kürzlich erstellten Vorlage basieren, wird Ihre personalisierte Tabelle standardmäßig für das globale Targeting und die Filterdimensionen des Workflows ausgewählt.

Alle in Ihrem Workflow verwendeten Aktivitäten verwenden daher Ihre benutzerdefinierte Tabelle, ohne dass eine zusätzliche manuelle Konfiguration erforderlich ist.

For more information on workflows, refer to [this section](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

