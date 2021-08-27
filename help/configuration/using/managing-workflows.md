---
product: campaign
title: Workflows verwalten
description: Workflows verwalten
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# Workflows verwalten{#managing-workflows}

![](../../assets/v7-only.svg)

Standardmäßig basieren Ihre neuen Workflows auf einer vorkonfigurierten Workflow-Vorlage, die auf einer Empfängertabelle (nms:recipient) basiert. Damit sie automatisch auf der benutzerdefinierten Empfängertabelle basieren, auf die in der Option **Nms_DefaultRcpSchema** verwiesen wird (siehe Abschnitt [Konfigurieren der Schnittstelle](../../configuration/using/configuring-the-interface.md) ), müssen Sie eine neue Workflow-Vorlage erstellen.

Erstellen Sie eine neue Vorlage über den Knoten **[!UICONTROL Ressourcen > Vorlagen > Workflow-Vorlagen]** . Die in den Eigenschaften der Vorlage angegebenen Dimensionen entsprechen der Tabelle der externen Empfänger.

Wenn Sie Ihre neuen Workflows auf einer kürzlich erstellten Vorlage basieren, wird Ihre personalisierte Tabelle standardmäßig für die globalen Zielgruppen- und Filterdimensionen des Workflows ausgewählt.

Alle in Ihrem Workflow verwendeten Aktivitäten verwenden daher Ihre benutzerdefinierte Tabelle, ohne dass eine zusätzliche manuelle Konfiguration erforderlich ist.

Weiterführende Informationen zu Workflows finden Sie in [diesem Abschnitt](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
