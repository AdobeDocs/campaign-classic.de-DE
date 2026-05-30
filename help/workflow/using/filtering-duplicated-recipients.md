---
product: campaign
title: Filtern doppelter Empfänger
description: Erfahren Sie, wie Sie doppelte Empfänger filtern können
feature: Workflows
hide: true
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
TQID: https://experienceleague.adobe.com/qsfiVfgYUq38VWmh5QEq87-WBwFGrc2iCSeAhjaKXbg
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 156
ht-degree: 100%

---

# Filtern doppelter Empfänger {#filtering-duplicated-recipients}



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
