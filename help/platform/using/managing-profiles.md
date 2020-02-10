---
title: Profile verwalten
seo-title: Profile verwalten
description: Profile verwalten
seo-description: null
page-status-flag: never-activated
uuid: f045dd5e-e069-4293-8c44-49d71071b041
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: ef7aa3a0-249f-46eb-9300-5b97bce31c8c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Profile verwalten{#managing-profiles}

## Empfängerknoten im Navigationsbaum {#recipient-tree}

Um auf die erweiterten Funktionen zur Verwaltung der Empfänger zuzugreifen, müssen Sie die Adobe Campaign-Struktur bearbeiten. Klicken Sie dazu auf die **[!UICONTROL Explorer]** Schaltfläche in der Symbolleiste.

Standardmäßig werden Empfänger im **[!UICONTROL Profiles and targets]** Knoten der Adobe Campaign-Struktur gespeichert. Auf demselben Knoten können Sie einen oder mehrere Ordner und Unterordner erstellen, um Empfängerprofile zu speichern.

Jeder Knoten entspricht einem Ordner. Die Daten eines Ordners sind als in sich abgeschlossen zu betrachten. Somit würde sich z. B. die Deduplizierung im Falle von mehreren Empfängerordnern als schwierig erweisen.

>[!NOTE]
>
>Um die Liste aller Empfänger in der Datenbank anzuzeigen, müssen Sie eine Ansicht erstellen. Siehe [Ordner und Ansichten](../../platform/using/access-management.md#folders-and-views).

## Empfänger verschieben {#moving-recipients}

Sie können einen oder eine Gruppe von Empfängern markieren und sie durch Drag&amp;Drop aus der Liste in einen anderen Ordner verschieben. Vor der endgültigen Verschiebung ist eine Bestätigung Ihrerseits erforderlich.

## Empfänger duplizieren {#copying-a-recipient}

You can copy a recipient in the same folder by right-clicking the desired recipient and selecting **[!UICONTROL Copy]**.

## Empfänger löschen {#deleting-recipients}

Um Empfänger zu löschen, verschieben Sie sie in einen bestimmten Ordner und löschen Sie dann den Inhalt dieses Ordners. Es wird **dringend empfohlen, in diesem Fall die Option nicht zu verwenden****[!UICONTROL Delete]** .

To purge a folder, use the **[!UICONTROL Actions > Purge folder]** menu, accessed by right-clicking the desired folder.

![](assets/s_ncs_user_purge_folder.png)

Klicken Sie auf **[!UICONTROL Start]** , um den Vorgang zu starten. Im mittleren Bereich des Fensters wird der Status des Fortschritts angezeigt, wie unten dargestellt:

![](assets/s_ncs_user_purge_folder_start.png)

