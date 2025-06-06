---
product: campaign
title: Anwendungsbeispiel
description: Anwendungsbeispiel
feature: Subscriptions, Email, Data Management
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 100%

---

# Anwendungsbeispiel{#use-case}



## Filter für das E-Mail-Format von Abonnenten erstellen {#creating-a-filter-on-the-email-format-of-subscribers}

In diesem Anwendungsbeispiel wird die Erstellung eines Filters beschrieben, der Newsletter-Abonnements entsprechend des von den Empfängern angegebenen E-Mail-Formats filtert.

Hierfür wird ein vordefinierter Filter verwendet. Diese einem Dokumenttyp zugeordnete Art von Filter ist über den Verzeichnisknoten **[!UICONTROL Administration > Konfiguration > Vordefinierte Filter]** zugänglich. Er kann in jedem Editor- oder Dokumenttyp zum Einsatz kommen.

Datenfilter werden wie vordefinierte Filter erstellt. Ein zusätzliches Feld ermöglicht es jedoch, den Dokumenttyp auszuwählen, für den der Filter angewendet werden soll.

Gehen Sie wie folgt vor:

1. Erstellen Sie einen neuen Filter ausgehend vom Verzeichnisknoten **[!UICONTROL Administration > Konfiguration > Vordefinierte Filter]**.
1. Klicken Sie auf das Symbol **[!UICONTROL Verknüpfung auswählen]**, um das gewünschte Dokument auszuwählen:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Wählen Sie das Schema Abonnements (nms:subscription) aus und klicken Sie auf **[!UICONTROL OK.]**

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Klicken Sie zur Ansicht der Felder des ausgewählten Dokuments auf das Symbol **[!UICONTROL Verknüpfung ansehen]**.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Sie können nun den Inhalt des gewählten Dokuments einsehen:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Diese Felder werden für die Bestimmung der Filterbedingungen im Filtereditor zugänglich sein. Die Bestimmung eines Anwendungsfilters erfolgt auf die gleiche Weise wie die eines erweiterten Filters. Weitere Informationen finden Sie unter [Erweiterte Filter erstellen](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Erstellen Sie einen neuen Abonnementfilter, um nur solche Abonnements anzuzeigen, für die kein E-Mail-Format bestimmt wurde:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um den Filter den vordefinierten Filtern für diesen Listentyp hinzuzufügen.
1. Der Filter &quot;Unbekanntes E-Mail-Format&quot; kann nun in der Registerkarte **[!UICONTROL Abonnements]** des Empfängerprofils angewendet werden und ist über die Schaltfläche **[!UICONTROL Filter]** zugänglich.

   ![](assets/s_ncs_user_filter_on_events.png)

   Der Name des aktuellen Filters wird oberhalb der Liste angezeigt. Um den Filter aufzuheben, klicken Sie auf das Symbol **[!UICONTROL Diesen Filter entfernen]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
