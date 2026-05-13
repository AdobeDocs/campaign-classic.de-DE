---
product: campaign
title: Anwendungsbeispiel
description: Anwendungsbeispiel
feature: Subscriptions, Email, Data Management
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
TQID: https://experienceleague.adobe.com/WuZ0tN8noOI48gW8vl4-923lo2aC8-Jcaz6Ph76nlmE
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 293
ht-degree: 74%

---

# Anwendungsbeispiel{#use-case}



## Filter für das E-Mail-Format von Abonnenten erstellen {#creating-a-filter-on-the-email-format-of-subscribers}

In diesem Anwendungsbeispiel wird die Erstellung eines Filters beschrieben, der Newsletter-Abonnements entsprechend des von den Empfängern angegebenen E-Mail-Formats filtert.

Dazu müssen wir einen vordefinierten Filter verwenden: Diese Filter sind mit einem Dokumenttyp verknüpft und sind über den Knoten **[!UICONTROL Administration > Konfiguration > Vordefinierte Filter]** zugänglich. Diese Datenfilter können für jeden Editor- (oder Dokument-)Typ in der Anwendung verwendet werden.

Datenfilter werden wie vordefinierte Filter erstellt. Ein zusätzliches Feld ermöglicht es jedoch, den Dokumenttyp auszuwählen, für den der Filter angewendet werden soll.

Gehen Sie wie folgt vor:

1. Erstellen Sie einen neuen Filter ausgehend vom Verzeichnisknoten **[!UICONTROL Administration > Konfiguration > Vordefinierte Filter]**.
1. Klicken Sie auf das Symbol **[!UICONTROL Verknüpfung auswählen]**, um das gewünschte Dokument auszuwählen:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Wählen Sie das Abonnementschema (nms:subscription) aus und klicken Sie auf **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Klicken Sie zur Ansicht der Felder des ausgewählten Dokuments auf das Symbol **[!UICONTROL Verknüpfung ansehen]**.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Sie können nun den Inhalt des gewählten Dokuments einsehen:

   ![](assets/s_ncs_user_filter_view_schema.png)

   Sie können auf diese Felder zugreifen, um Filterbedingungen im Hauptteil des Filter-Editors zu definieren. Ein Anwendungsfilter wird genau wie ein erweiterter Filter definiert. Weitere Informationen zu Filtern finden Sie in der [Dokumentation zu Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.


1. Erstellen Sie einen neuen Abonnementfilter, um nur solche Abonnements anzuzeigen, für die kein E-Mail-Format bestimmt wurde:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um den Filter den vordefinierten Filtern für diesen Listentyp hinzuzufügen.
1. Der Filter &quot;Unbekanntes E-Mail-Format&quot; kann nun in der Registerkarte **[!UICONTROL Abonnements]** des Empfängerprofils angewendet werden und ist über die Schaltfläche **[!UICONTROL Filter]** zugänglich.

   ![](assets/s_ncs_user_filter_on_events.png)

   Der Name des aktuellen Filters wird oberhalb der Liste angezeigt. Um den Filter aufzuheben, klicken Sie auf das Symbol **[!UICONTROL Diesen Filter entfernen]**.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
