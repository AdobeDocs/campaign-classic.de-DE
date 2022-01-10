---
product: campaign
title: Workflows verwalten
description: Workflows verwalten
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# Workflows verwalten{#managing-workflows}

![](../../assets/common.svg)

Standardmäßig basieren Ihre neuen Workflows auf einer vorkonfigurierten Workflow-Vorlage, die auf einer Empfängertabelle (nms:recipient) basiert. Damit sie automatisch auf der benutzerdefinierten Empfängertabelle basieren, auf die im Abschnitt **Nms_DefaultRcpSchema** -Option (siehe [Benutzeroberfläche konfigurieren](../../configuration/using/configuring-the-interface.md) ), müssen Sie eine neue Workflow-Vorlage erstellen.

Erstellen Sie eine neue Vorlage über die **[!UICONTROL Ressourcen > Vorlagen > Workflow-Vorlagen]** Knoten. Die in den Eigenschaften der Vorlage angegebenen Dimensionen entsprechen der Tabelle der externen Empfänger.

Wenn Sie Ihre neuen Workflows auf einer kürzlich erstellten Vorlage basieren, wird Ihre personalisierte Tabelle standardmäßig für die globalen Zielgruppen- und Filterdimensionen des Workflows ausgewählt.

Alle in Ihrem Workflow verwendeten Aktivitäten verwenden daher Ihre benutzerdefinierte Tabelle, ohne dass eine zusätzliche manuelle Konfiguration erforderlich ist.

Weiterführende Informationen zu Workflows finden Sie im Abschnitt [diesem Abschnitt](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
