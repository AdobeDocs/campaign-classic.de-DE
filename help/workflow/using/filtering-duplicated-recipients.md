---
product: campaign
title: Filtern doppelter Empfänger
description: Erfahren Sie, wie Sie doppelte Empfänger filtern können
feature: Workflows
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 65%

---

# Filtern doppelter Empfänger {#filtering-duplicated-recipients}



In diesem Beispiel werden wir Empfänger filtern, die doppelt oder öfter in einem Versand vorkommen, um duplizierte Profile festzustellen.

Gehen Sie wie folgt vor:

1. Ziehen Sie eine **[!UICONTROL Abfrage]** in den Workflow-Arbeitsbereich und öffnen Sie sie.
1. Wählen Sie **[!UICONTROL Abfrage bearbeiten]** aus und wählen Sie für die Zielgruppen- und Filterdimension die Option **[!UICONTROL Empfänger]** aus.

   ![](assets/query_recipients_1.png)

1. Definieren Sie die folgende Filterbedingung für die im Versandlog vorhandenen Empfänger. Auswählen **Versandlog eines Empfängers (broadlog)** im **Ausdruck** Spalte, wählen **vorhanden sind, z. B.** im **Operator** Spalte.

   ![](assets/query_recipients_2.png)

1. Definieren Sie die folgende Filterbedingung für Ihren Versand. Auswählen **[!UICONTROL Interner Name]** in der Spalte Ausdruck und **[!UICONTROL gleich]** in der Spalte Operator .
1. Fügen Sie in der Wertspalte den internen Namen des Versands ein.

   ![](assets/query_recipients_3.png)

1. Wiederholen Sie diesen Vorgang mit einem **[!UICONTROL UND]**-Operator für andere Sendungen.

   ![](assets/query_recipients_4.png)

Ihre ausgehende Transition enthält die duplizierten Empfänger der Sendungen.
