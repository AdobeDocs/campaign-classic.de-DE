---
product: campaign
title: Erstellen und Verwalten von Listen
description: Erfahren Sie, wie Sie Listen erstellen und verwalten.
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Profiles
role: User
level: Beginner
exl-id: 711b84cd-bac8-4f1a-9999-0124fbfc3a01
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 75%

---

# Erstellen und Verwalten von Listen{#creating-and-managing-lists}



## Definition einer Liste  {#about-lists-in-adobe-campaign}

Eine Liste ist eine statische Gruppe von Profilen, die als Zielgruppe für Sendungen verwendet oder durch Importe sowie Workflows aktualisiert werden kann. So kann beispielsweise eine mithilfe einer Abfrage aus der Datenbank gefilterte Population in einer Liste gespeichert werden.

Listen werden über den Link **[!UICONTROL Listen]** im Tab **[!UICONTROL Profile und Zielgruppen]** erstellt und verwaltet.

![](assets/s_ncs_user_interface_group_link.png)

In Adobe Campaign sind zwei Arten von Listen verfügbar:

* **[!UICONTROL Gruppe]**: Diese Listen vom Typ **[!UICONTROL Gruppe]** gehören zu **statischen** Listen von nach bestimmten Kriterien ausgewählten Kontakten. Eine Liste ist eine Art Fotografie einer Profilgruppe zu einem bestimmten Zeitpunkt. Bitte beachten Sie, dass diese Listen nicht automatisch aktualisiert werden, wenn Profile zur Datenbank hinzugefügt werden.

  Weiterführende Informationen zum Erstellen einer Liste vom Typ **[!UICONTROL Gruppe]** finden Sie auf [dieser Seite](#creating-a-profile-list-from-a-group).

* **[!UICONTROL Liste]** type: Die **[!UICONTROL Liste]** Mit Typlisten können Sie mithilfe von Workflows Listen erstellen und verwalten. Hierbei handelt es sich um spezifische Listen, die aus Datenimporten resultieren und über die entsprechende **[!UICONTROL Listen-Update]** Workflow-Aktivität.

  Im Gegensatz zu **[!UICONTROL Gruppe]** Typenliste, kann diese Typliste automatisch mit einer **[!UICONTROL Planung]** -Aktivität. Beachten Sie Folgendes: Ein Beispiel für die Erstellung von **[!UICONTROL Liste]** Typlisten, siehe [diese Seite](../../workflow/using/list-update.md).

![](assets/do-not-localize/how-to-video.png) [Entdecken Sie diese Funktion im Video](#create-list-video)

## Profilliste von einer Gruppe erstellen {#creating-a-profile-list-from-a-group}

Listen vom Typ **[!UICONTROL Gruppe]**, die über den Link **[!UICONTROL Profile und Zielgruppen]** erstellt wurden, basieren ausschließlich auf der Standard-Profiltabelle (nms:recipient).

>[!NOTE]
>
>Um Listen mit anderen Datentypen zu erstellen, müssen Sie einen Workflow ausführen. Wenn Sie beispielsweise eine Abfrage in der Besuchertabelle verwenden und die Liste dann aktualisieren, können Sie eine Besucherliste erstellen. Weitere Informationen zu Workflows finden Sie unter [diesem Abschnitt](../../workflow/using/about-workflows.md).

Gehen Sie wie folgt vor, um eine neue Liste vom Typ **[!UICONTROL Gruppe]** zu erstellen:

1. Verwenden Sie die Schaltfläche **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Neue Liste]** aus.

   ![](assets/s_ncs_user_new_group.png)

1. Erfassen Sie im Tab **[!UICONTROL Bearbeiten]** des Listenfensters alle nötigen Informationen.

   * Geben Sie im Feld **[!UICONTROL Titel]** den Namen der Liste an und ändern Sie ggf. den internen Namen.
   * Sie haben die Möglichkeit, eine Beschreibung in Bezug auf die Liste zu erfassen.
   * Des Weiteren können Sie ein Ablaufdatum angeben. Bei Erreichen des Datums wird die Liste automatisch gelöscht.

     ![](assets/list_expiration_date.png)

1. Setzen Sie im Tab **[!UICONTROL Inhalt]** durch Klick auf die Schaltfläche **[!UICONTROL Hinzufügen]** Profile auf die Liste.

   ![](assets/s_ncs_user_add_group.png)

1. Verwenden Sie die Schaltfläche **[!UICONTROL Speichern]**. Die Liste ist nunmehr über die Listenübersicht zugänglich.

Es ist auch möglich, neue Profile direkt im Hinzufügefenster anzulegen, indem Sie die Schaltfläche **[!UICONTROL Erstellen]** verwenden. Das auf diese Weise hinzugefügte Profil wird in die Datenbank aufgenommen.

![](assets/s_ncs_user_new_recipient_from_group.png)

Die Darstellung der Empfängerliste kann wie andere Listen auch Ihren Bedürfnissen entsprechend angepasst werden. Weitere Informationen finden Sie in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Daten einer Liste zuordnen {#linking-data-to-a-list}

>[!NOTE]
>
>Die Zuordnung von Daten zu einer Liste ist nur mit Listen vom Typ **[!UICONTROL Gruppe]** möglich.

Es besteht die Möglichkeit, Profile zu filtern und das Ergebnis einer Liste zuzuordnen. Diese Liste kann dann als Zielgruppe für Sendungen verwendet werden. Gehen Sie folgendermaßen vor, um Profile zusammenzufassen:

1. Markieren Sie die gewünschten Profile und wählen Sie sie mit der rechten Maustaste aus.
1. Wählen Sie nun > **[!UICONTROL Aktionen > Auswahl einer Liste zuordnen...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Wählen Sie eine existierende Liste aus oder erstellen Sie eine neue durch Auswahl der Schaltfläche **[!UICONTROL Erstellen]**. Verwenden Sie anschließend **[!UICONTROL Weiter]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL starten]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

Bei Auswahl der Option **[!UICONTROL Liste neu erstellen]** wird der frühere Listeninhalt gelöscht. Es handelt sich hierbei um den optimierten Modus, da keine Abfrage erforderlich ist, um zu prüfen, ob gewisse Profile bereits dieser Liste zugeordnet wurden.

Wenn Sie die Option **[!UICONTROL Vorgang nicht in der Datenbank protokollieren]** abwählen, ist die Auswahl oder Erstellung eines Ausführungsordners erforderlich, in dem die den Vorgang betreffenden Protokollnachrichten gespeichert werden.

Im oberen Bereich des Fensters können Sie die Ausführung überwachen. Die **[!UICONTROL Anhalten]** -Schaltfläche können Sie den Vorgang stoppen. Bereits verarbeitete Kontakte werden mit der Liste verknüpft.

Im Tab **[!UICONTROL Listen]** der vom Vorgang betroffenen Profile kann das Ergebnis der Listenzuordnung geprüft werden:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Sie können die Liste auch über die Adobe Campaign-Startseite bearbeiten: Klicken Sie auf die Schaltfläche **[!UICONTROL Profile und Zielgruppen > Listen]** und wählen Sie die gewünschte Liste aus. Die **[!UICONTROL Inhalt]** zeigt die der Liste zugeordneten Profile an.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Profil aus einer Liste entfernen {#removing-a-profile-from-a-list}

Sie haben verschiedene Möglichkeiten, Profile aus einer Liste zu entfernen. Sie können:

* die Liste bearbeiten, das Profil im Tab **[!UICONTROL Inhalt]** auswählen und auf das Symbol **[!UICONTROL Löschen]** klicken;

  ![](assets/list_remove_a_recipient.png)

* das Profil bearbeiten und im Tab **[!UICONTROL Liste]** auf das Symbol **[!UICONTROL Löschen]** klicken.

  ![](assets/recipient_remove_a_list.png)

## Liste der Profile löschen {#deleting-a-list-of-profiles}

Sie können eine oder mehrere Listen aus der Gruppenliste im Adobe Campaign-Baum löschen. Bearbeiten Sie hierzu den Baum über das **[!UICONTROL Erweitert > Explorer]** auf der Adobe Campaign-Startseite. Wählen Sie die betreffende(n) Gruppe(n) aus und klicken Sie mit der rechten Maustaste darauf. Auswählen **[!UICONTROL Löschen]**. In einer Warnmeldung werden Sie aufgefordert, den Löschvorgang zu bestätigen.

>[!NOTE]
>
>Die Löschung einer Liste hat außer der Aktualisierung der Profildaten keinen Einfluss auf die der Liste zugeordneten Profile.

## Anleitungsvideo {#create-list-video}

### Eine Empfängerliste erstellen

Eine Liste ist ein statischer Satz von Empfängern, die in Versandaktionen als Zielkontakte dienen oder beim Importieren bzw. bei der Workflow-Ausführung aktualisiert werden können. Eine Liste von Empfängern wird auch als Audience bezeichnet.

Erfahren Sie mehr über das Erstellen einer Audience durch Konfigurieren einer Empfängerliste aus dem Explorer.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### So verwenden Sie einen Workflow zum Erstellen einer Liste von Empfängern {#create-list-in-a-wf-video}

Erfahren Sie, wie Sie einen Workflow erstellen, um Empfänger als Zielkontakte auszuwählen und den Workflow als wiederkehrend einzurichten, bevor die Liste als Zielgruppe für eine E-Mail-Kampagne verwendet wird.

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
