---
product: campaign
title: Profile verwalten
description: Profile verwalten
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: ht
source-wordcount: '239'
ht-degree: 100%

---

# Verwalten von Profilen{#managing-profiles}

![](../../assets/v7-only.svg)

## Empfängerknoten im Navigationsbaum {#recipient-tree}

Erweiterte Funktionalitäten zur Empfängerverwaltung stehen über den Navigationsbaum zur Verfügung. Klicken Sie hierfür auf der Adobe-Campaign-Startseite auf die **[!UICONTROL Explorer]**-Schaltfläche in der Symbolleiste.

Der Empfängerordner befindet sich standardmäßig im Knoten **[!UICONTROL Profile und Zielgruppen]** des Adobe-Campaign-Navigationsbaums. Sie können von diesem Knoten ausgehend weitere Ordner oder Unterordner erstellen, um Empfängerprofile zu speichern.

Jeder Knoten entspricht einem Ordner. Die Daten eines Ordners sind als in sich abgeschlossen zu betrachten. Somit würde sich z. B. die Deduplizierung im Falle von mehreren Empfängerordnern als schwierig erweisen.

>[!NOTE]
>
>Um eine Liste aller in der Datenbank enthaltenen Empfänger anzuzeigen, ist die Erstellung einer Ansicht erforderlich. Weitere Informationen finden Sie unter [Ordner und Ansichten](../../platform/using/access-management-folders.md).

## Empfänger verschieben   {#moving-recipients}

Sie können einen Empfänger oder eine Gruppe von Empfängern markieren und per Drag-and-drop aus der Liste in einen anderen Ordner verschieben. Vor der endgültigen Verschiebung ist eine Bestätigung Ihrerseits erforderlich.

## Empfänger kopieren {#copying-a-recipient}

Es besteht die Möglichkeit, einen Empfänger im selben Ordner zu duplizieren. Klicken Sie hierzu mit der rechten Maustaste auf den entsprechenden Empfänger und wählen Sie **[!UICONTROL Kopieren]**.

## Empfänger löschen {#deleting-recipients}

Zu löschende Empfänger sind zunächst in einen spezifischen Ordner zu verschieben, welcher im Anschluss daran bereinigt wird. Es wird **dringend davon abgeraten**, in diesem Zusammenhang die Option **[!UICONTROL Löschen]** zu verwenden.

Löschen Sie den Ordnerinhalt, indem Sie mit der rechten Maustaste auf den entsprechenden Ordner klicken und **[!UICONTROL Aktionen > Ordner bereinigen]** auswählen.

![](assets/s_ncs_user_purge_folder.png)

Klicken Sie auf **[!UICONTROL Starten]**, um den Vorgang zu beginnen. Eine Statusleiste zeigt den Bearbeitungsfortschritt an:

![](assets/s_ncs_user_purge_folder_start.png)
