---
solution: Campaign Classic
product: campaign
title: Duplizierte Empfänger filtern
description: Erfahren Sie, wie duplizierte Empfänger gefiltert werden
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '156'
ht-degree: 100%

---

# Duplizierte Empfänger filtern {#filtering-duplicated-recipients}

In diesem Beispiel werden wir Empfänger filtern, die doppelt oder öfter in einem Versand vorkommen, um duplizierte Profile festzustellen.

Gehen Sie wie folgt vor:

1. Ziehen Sie eine **[!UICONTROL Abfrage]** in den Workflow-Arbeitsbereich und öffnen Sie sie.
1. Wählen Sie **[!UICONTROL Abfrage bearbeiten]** aus und wählen Sie für die Zielgruppen- und Filterdimension die Option **[!UICONTROL Empfänger]** aus.

   ![](assets/query_recipients_1.png)

1. Definieren Sie die folgende Filterbedingung für die Empfänger im Versandlog. Wählen Sie in der Spalte **Ausdruck** die Option **Versandlog eines Empfängers (Broadlog)** und in der Spalte **Operator** die Option **wie** aus.

   ![](assets/query_recipients_2.png)

1. Definieren Sie die folgende Filterbedingung für Ihren Versand. Wählen Sie in der Ausdrucksspalte die Option **[!UICONTROL Interner Name]** und in der Operator-Spalte die Option **[!UICONTROL gleich]**.
1. Fügen Sie in der Wertspalte den internen Namen des Versands ein.

   ![](assets/query_recipients_3.png)

1. Wiederholen Sie diesen Vorgang mit einem **[!UICONTROL UND]**-Operator für andere Sendungen.

   ![](assets/query_recipients_4.png)

Ihre ausgehende Transition enthält die duplizierten Empfänger der Sendungen.
