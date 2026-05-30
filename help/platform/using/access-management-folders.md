---
product: campaign
title: Zugriff auf Campaign-Ordner verwalten
description: Erfahren Sie, wie Sie Zugriff auf Campaign-Ordner gewähren und Ansichten erstellen.
badge: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
hide: true
TQID: https://experienceleague.adobe.com/c4mev5HLxN6XRYRkqNokbrt45a1nImtMaJJ0uEZLGH4
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 545
ht-degree: 65%

---

# Zugriff auf Ordner verwalten{#folder-access-management}



Jeder Ordner des Explorer-Navigationsbaums verfügt über Lese-, Schreib- und Löschzugriffsrechte. Um auf eine Datei zugreifen zu können, muss ein Benutzer oder eine Benutzergruppe zumindest über Lesezugriff verfügen.

>[!NOTE]
>
>Weitere Informationen zu Berechtigungen für Ordner finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}.


## Ordner und Ansichten {#folders-and-views}

### Definition eines Ordners {#about-folders}

Ordner sind Knoten im Adobe Campaign-Navigationsbaum. Diese werden mit einem Klick der rechten Maustaste auf den Baum über das Menü **[!UICONTROL Ordner hinzufügen]** erstellt. Das erste Menü ermöglicht standardmäßig die Erstellung eines dem aktuellen Kontext entsprechenden Ordners.

![](assets/s_ncs_user_add_folder_in_tree.png)

Sie können den Navigationsbaum des Explorers anpassen. Erfahren Sie [in diesem Abschnitt](adobe-campaign-workspace.md) mehr über Konfigurationsschritte und Best Practices.

### Definition einer Ansicht {#about-views}

Darüber hinaus können Sie Ansichten erstellen, um den Zugriff auf Daten zu beschränken und den Inhalt der Baumstruktur entsprechend Ihren Anforderungen zu organisieren. Anschließend können Sie den Ansichten Rechte zuweisen.

Eine Ansicht ist ein Ordner, der Datensätze anzeigt, die physisch in einem oder mehreren anderen Ordnern desselben Typs gespeichert sind. Wenn Sie beispielsweise einen Kampagnenordner als Ansicht erstellen, werden alle in der Datenbank vorhandenen Kampagnen unabhängig von ihrer Herkunft standardmäßig angezeigt. Diese Daten können dann gefiltert werden.

Wenn Sie einen Ordner in eine Ansicht konvertieren, werden alle Daten, die dem in der Datenbank vorhandenen Ordnertyp entsprechen, in der Ansicht angezeigt, unabhängig vom Ordner, in dem er gespeichert ist. Sie können sie dann filtern, um die Liste der angezeigten Daten einzuschränken.

>[!IMPORTANT]
>
>Die Ansichten enthalten Daten und bieten Zugriff darauf, aber die Daten werden nicht physisch im Ansichtsordner gespeichert. Der Benutzer muss über die entsprechenden Berechtigungen für die gewünschte Aktion in den Datenquellenordnern verfügen (mindestens Lesezugriff).
>
>Um Zugriff auf eine Ansicht ohne Zugriff auf den Herkunftsordner zu verleihen, darf kein Lesezugriff auf den übergeordneten Knoten des Herkunftsordners gegeben werden.

Zur Unterscheidung zwischen Ansichten und Ordnern wird der Name der Ansichten in einer anderen Farbe angezeigt (dunkeltürkis).

![](assets/s_ncs_user_view_name_color.png)

### Ordner hinzufügen und Ansichten erstellen {#adding-folders-and-creating-views}

>[!IMPORTANT]
>
>Vorkonfigurierte Ordner sollten nicht für die Ansicht markiert werden.


Im folgenden Beispiel werden wir neue Ordner erstellen, um bestimmte Daten darzustellen:

1. Erstellen Sie einen neuen Ordner vom Typ **[!UICONTROL Sendungen]** und nennen Sie ihn **Sendungen Deutschland**.
1. Klicken Sie mit der rechten Maustaste auf diesen Ordner und wählen Sie **[!UICONTROL Eigenschaften...]** aus.

   ![Screenshot, in dem mit rechts auf die Eigenschaften geklickt wird](assets/s_ncs_user_add_folder_exple.png)

1. Wählen Sie auf **[!UICONTROL Registerkarte]** Einschränkung **[!UICONTROL die Option „Dieser Ordner ist eine Ansicht]** aus. Alle Sendungen in der Datenbank werden dann angezeigt.

   ![Screenshot, in dem das Ansichtsfeld ausgewählt wird](assets/s_ncs_user_add_folder_exple01.png)

1. Bestimmen Sie mithilfe des Abfrage-Editors im mittleren Abschnitt des Fensters die Bedingungen, nach denen die Sendungen gefiltert werden sollen: Es werden nur die dem Filter entsprechenden Sendungen angezeigt.

   >[!NOTE]
   >
   >Der Abfrage-Editor wird in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#about-queries-in-campaign) beschrieben.

   Mit den folgenden Filterbedingungen:

![Screenshot mit den verschiedenen Filterbedingungen](assets/s_ncs_user_add_folder_exple00.png)

werden folgende Sendungen in der Ansicht angezeigt:

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>Bei der Verwaltung von Ereignissen des Typs [Transaktionsnachrichten](../../message-center/using/about-transactional-messaging.md) dürfen die Ordner **[!UICONTROL Echtzeitereignis]** oder **[!UICONTROL Batch-Ereignis]** auf den Ausführungsinstanzen nicht als Ansichten festgelegt werden, da dies zu Problemen mit den Zugriffsrechten führen kann. Weiterführende Informationen zum Sammeln von Ereignissen finden Sie in [diesem Abschnitt](../../message-center/using/about-event-processing.md#event-collection).

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->