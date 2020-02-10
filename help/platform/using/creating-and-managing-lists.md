---
title: Listen erstellen und verwalten
seo-title: Listen erstellen und verwalten
description: Listen erstellen und verwalten
seo-description: null
page-status-flag: never-activated
uuid: 17d1a7d0-a728-490e-a820-19f469fddbcd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 9fc243b2-7b7b-4083-83f6-04c12336492d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Listen erstellen und verwalten{#creating-and-managing-lists}

## Über Listen in Adobe Campaign {#about-lists-in-adobe-campaign}

Eine Liste ist eine statische Gruppe von Profilen, die als Zielgruppe für Sendungen verwendet oder durch Importe sowie Workflows aktualisiert werden kann. So kann beispielsweise eine mithilfe einer Abfrage aus der Datenbank gefilterte Population in einer Liste gespeichert werden.

Basierend auf derart erstellten Listen ist es nun möglich, Sendungen (per E-Mail, SMS usw.) zu konfigurieren. Bitte stellen Sie zuvor eine der Deontologie entsprechende Verwaltung der Empfängerzustimmungen und -ablehnungen (Permission Marketing) sicher.

Listen werden über den **[!UICONTROL Lists]** Link auf der **[!UICONTROL Profiles and targets]** Registerkarte erstellt und verwaltet.

![](assets/s_ncs_user_interface_group_link.png)

In Adobe Campaign sind zwei Arten von Listen verfügbar:

* **[!UICONTROL Group]** type: Die **[!UICONTROL Group]** Typlisten gehören zu einer **statischen** Liste von Personen, die nach bestimmten Kriterien ausgewählt wurden. Die Liste ist wie eine Momentaufnahme eines Profilsatzes. Bitte beachten Sie, dass das Profil nicht automatisch aktualisiert wird, wenn der Datenbank Profile hinzugefügt werden.

   For more information on how to create a **[!UICONTROL Group]** type list, refer to this [page](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** type: Mithilfe der **[!UICONTROL List]** Typlisten können Sie mithilfe von Workflows Listen erstellen und verwalten. Dabei handelt es sich um spezifische Listen, die sich aus Datenimporten ergeben und über die dedizierte **[!UICONTROL List update]** Workflow-Aktivität aktualisiert werden können.

   Im Gegensatz zur **[!UICONTROL Group]** Typliste kann diese Typliste automatisch mit einer **[!UICONTROL Scheduler]** Aktivität aktualisiert werden. Beachten Sie, dass ein Beispiel zum Erstellen von **[!UICONTROL List]** Typlisten auf [dieser Seite](../../workflow/using/list-update.md)aufgeführt ist.

## Profilliste von einer Gruppe erstellen {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** Typlisten, die über den **[!UICONTROL Profiles and targets]** Link erstellt wurden, müssen auf der standardmäßigen Adobe Campaign-Profiltabelle (nms:empfänger) basieren.

>[!NOTE]
>
>Die Erstellung von Listen mit anderen Daten ist unter Verwendung eines Workflows möglich. Sie können beispielsweise eine Besucherliste anlegen, indem Sie einen Workflow mit einer Abfrage bezüglich der Besuchertabelle und der Aktivität Listenaktualisierung erstellen. Weiterführende Informationen zu Workflows finden Sie in [diesem Abschnitt](../../workflow/using/about-workflows.md).

To create a new **[!UICONTROL Group]** type list, apply the following steps:

1. Klicken Sie auf die **[!UICONTROL Create]** Schaltfläche und wählen Sie **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Enter the information in the **[!UICONTROL Edit]** tab of the list creation window.

   * Enter the list name in the **[!UICONTROL Label]** field and, if necessary, change the internal name.
   * Sie haben die Möglichkeit, eine Beschreibung in Bezug auf die Liste zu erfassen.
   * Des Weiteren können Sie ein Ablaufdatum angeben. Bei Erreichen des Datums wird die Liste automatisch gelöscht.

      ![](assets/list_expiration_date.png)

1. In the **[!UICONTROL Content]** tab, click **[!UICONTROL Add]** to select the profiles belonging to the list.

   ![](assets/s_ncs_user_add_group.png)

1. Klicken Sie auf **[!UICONTROL Save]** , um die Liste zu speichern. Er wird dann der Übersicht über die Listen hinzugefügt.

You can create new profiles directly from the &#39;add profiles&#39; window by clicking **[!UICONTROL Create]**. The profile will be added to the database.

![](assets/s_ncs_user_new_recipient_from_group.png)

Die Profilliste kann wie andere Listen konfiguriert werden. Siehe [Konfigurieren von Listen](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Daten einer Liste zuordnen {#linking-data-to-a-list}

>[!NOTE]
>
>Linking data to a list can only been done with a **[!UICONTROL Group]** type list.

Es besteht die Möglichkeit, Profile zu filtern und das Ergebnis einer Liste zuzuordnen. Diese Liste kann dann als Zielgruppe für Sendungen verwendet werden. Gehen Sie folgendermaßen vor, um Profile zusammenzufassen:

1. Markieren Sie die gewünschten Profile und wählen Sie sie mit der rechten Maustaste aus.
1. Auswählen **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Select the desired list or create a new list using the **[!UICONTROL Create]** button, then click **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Click the **[!UICONTROL Start]** button.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

Die **[!UICONTROL Recreate the list]** Option löscht den vorherigen Inhalt aus der Liste. Dieser Modus ist optimiert, da keine Abfrage erforderlich ist, um zu überprüfen, ob die Profile bereits mit der Liste verknüpft sind.

Wenn Sie die **[!UICONTROL No trace of this job is saved in the database]** Option deaktivieren, können Sie den Ausführungsordner auswählen (oder erstellen), in dem die mit diesem Prozess verknüpften Informationen gespeichert werden.

Im oberen Bereich des Fensters können Sie die Ausführung überwachen. Mit der **[!UICONTROL Stop]** Schaltfläche können Sie den Prozess beenden. Bereits verarbeitete Kontakte werden mit der Liste verknüpft.

You can monitor the process via the **[!UICONTROL Lists]** tab on the profiles concerned by this operation:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Sie können die Liste auch über die Adobe Campaign-Homepage bearbeiten: Klicken Sie auf das **[!UICONTROL Profiles and Targets > Lists]** Menü und wählen Sie die entsprechende Liste aus. Auf der **[!UICONTROL Content]** Registerkarte werden die Profile angezeigt, die mit dieser Liste verknüpft sind.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Profil aus einer Liste entfernen {#removing-a-profile-from-a-list}

Sie haben verschiedene Möglichkeiten, Profile aus einer Liste zu entfernen. Sie können:

* Edit the list, select the profile in the **[!UICONTROL Content]** tab, then click the **[!UICONTROL Delete]** icon.

   ![](assets/list_remove_a_recipient.png)

* Edit the profile, click the **[!UICONTROL List]** tab, then click the **[!UICONTROL Delete]** icon.

   ![](assets/recipient_remove_a_list.png)

## Profilliste löschen {#deleting-a-list-of-profiles}

Sie können eine oder mehrere Listen aus der Gruppenliste in der Adobe Campaign-Struktur löschen. Bearbeiten Sie dazu die Struktur über den **[!UICONTROL Advanced > Explorer]** Link auf der Adobe Campaign-Homepage. Wählen Sie die betreffende(n) Gruppe(n) aus und klicken Sie mit der rechten Maustaste. Auswählen **[!UICONTROL Delete]**. In einer Warnmeldung werden Sie aufgefordert, den Löschvorgang zu bestätigen.

>[!NOTE]
>
>Die Löschung einer Liste hat außer der Aktualisierung der Profildaten keinen Einfluss auf die der Liste zugeordneten Profile.

