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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Workflows verwalten{#managing-workflows}

Standardmäßig basieren Ihre neuen Workflows auf einer Workflow-Vorlage, die vorkonfiguriert wurde und auf einer Empfängertabelle basiert (nms:empfänger). Damit sie automatisch auf der benutzerdefinierten Empfängertabelle basieren, auf die in der Option **Nms_DefaultRcpSchema** verwiesen wird (siehe Abschnitt [Konfigurieren der Schnittstelle](../../configuration/using/configuring-the-interface.md) ), müssen Sie eine neue Workflow-Vorlage erstellen.

Erstellen Sie eine neue Vorlage über den **[!UICONTROL Resources > Templates > Workflow templates]** Knoten. Die in den Eigenschaften der Vorlage angegebenen Dimensionen entsprechen der Tabelle der externen Empfänger.

Wenn Sie Ihre neuen Arbeitsabläufe auf einer kürzlich erstellten Vorlage basieren, wird Ihre personalisierte Tabelle standardmäßig für die globalen Targeting- und Filterdimensionen des Workflows ausgewählt.

Alle in Ihrem Workflow verwendeten Aktivitäten verwenden daher Ihre benutzerdefinierte Tabelle, ohne dass eine zusätzliche manuelle Konfiguration erforderlich ist.

For more information on workflows, refer to [this section](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

