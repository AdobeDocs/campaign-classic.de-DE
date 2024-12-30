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
ht-degree: 16%

---

# Workflows verwalten{#managing-workflows}



Standardmäßig basieren Ihre neuen Workflows auf einer Workflow-Vorlage, die vorkonfiguriert wurde, und auf einer Empfängertabelle (nms:recipient). Damit sie automatisch auf der benutzerdefinierten Empfängertabelle basieren, auf die in der Option **Nms_DefaultRcpSchema** verwiesen wird (siehe Abschnitt [Konfigurieren der ](../../configuration/using/configuring-the-interface.md)), müssen Sie eine neue Workflow-Vorlage erstellen.

Erstellen Sie eine neue Vorlage über den Knoten **[!UICONTROL Ressourcen > Vorlagen > Workflow-]**&quot;. In den Eigenschaften der Vorlage entsprechen die bereitgestellten Dimensionen Ihrer externen Empfängertabelle.

Wenn Ihre neuen Workflows auf einer kürzlich erstellten Vorlage basieren, wird Ihre personalisierte Tabelle standardmäßig für die globalen Zielgruppen- und Filterdimensionen des Workflows ausgewählt.

Alle in Ihrem Workflow verwendeten Aktivitäten verwenden somit Ihre benutzerdefinierte Tabelle, ohne dass eine zusätzliche manuelle Konfiguration erforderlich ist.

Weiterführende Informationen zu Workflows finden Sie in [diesem Abschnitt](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
