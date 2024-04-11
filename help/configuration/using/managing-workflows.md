---
product: campaign
title: Workflows verwalten
description: Workflows verwalten
feature: Workflows, Configuration
role: Data Engineer, Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 7%

---

# Workflows verwalten{#managing-workflows}



Standardmäßig basieren Ihre neuen Workflows auf einer vorkonfigurierten Workflow-Vorlage, die auf einer Empfängertabelle (nms:recipient) basiert. Damit sie automatisch auf der benutzerdefinierten Empfängertabelle basieren, auf die im Abschnitt **Nms_DefaultRcpSchema** -Option (siehe [Benutzeroberfläche konfigurieren](../../configuration/using/configuring-the-interface.md) ), müssen Sie eine neue Workflow-Vorlage erstellen.

Erstellen Sie eine neue Vorlage über die **[!UICONTROL Ressourcen > Vorlagen > Workflow-Vorlagen]** Knoten. Die in den Eigenschaften der Vorlage angegebenen Dimensionen entsprechen der Tabelle der externen Empfänger.

Wenn Sie Ihre neuen Workflows auf einer kürzlich erstellten Vorlage basieren, wird Ihre personalisierte Tabelle standardmäßig für die globalen Zielgruppen- und Filterdimensionen des Workflows ausgewählt.

Alle in Ihrem Workflow verwendeten Aktivitäten verwenden daher Ihre benutzerdefinierte Tabelle, ohne dass eine zusätzliche manuelle Konfiguration erforderlich ist.

Weitere Informationen zu Workflows finden Sie unter [diesem Abschnitt](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
