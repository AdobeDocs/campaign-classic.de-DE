---
title: Duplizierte Empfänger filtern
description: Erfahren Sie, wie duplizierte Empfänger gefiltert werden
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Duplizierte Empfänger filtern {#filtering-duplicated-recipients}

In diesem Beispiel werden wir Empfänger filtern, die doppelt oder öfter in einem Versand vorkommen, um duplizierte Profile festzustellen.

Gehen Sie wie folgt vor:

1. Drag and drop a **[!UICONTROL Query]** activity in a workflow and open the activity.
1. Klicken Sie auf **[!UICONTROL Edit query]** und legen Sie die Ziel- und Filterdimensionen auf **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definieren Sie die folgende Filterbedingung für die Empfänger im Versandlog. Wählen Sie in der Spalte **Ausdruck** die Option **Versandlog eines Empfängers (Broadlog)** und in der Spalte **Operator** die Option **wie** aus.

   ![](assets/query_recipients_2.png)

1. Definieren Sie die folgende Filterbedingung, um Ihre Bereitstellung zielgerichtet durchzuführen. Wählen Sie **[!UICONTROL Internal name]** in der Spalte &quot;Ausdruck&quot;und in der Spalte &quot;Operator&quot; **[!UICONTROL equal to]** .
1. Fügen Sie in der Wertspalte den internen Namen des Versands ein.

   ![](assets/query_recipients_3.png)

1. With an **[!UICONTROL AND]** operator, repeat the same operations to target other deliveries.

   ![](assets/query_recipients_4.png)

Ihre ausgehende Transition enthält die duplizierten Empfänger der Sendungen.
