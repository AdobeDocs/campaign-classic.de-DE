---
product: campaign
title: Laden (DBMS)
description: Erfahren Sie mehr über die Workflow-Aktivität "Laden (DBMS)".
feature: Workflows, Data Management Activity
hide: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 720a5f4edf534788f7fd143a476c25e58a6f1586
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 63%

---

# Laden (DBMS){#data-loading-rdbms}



Die Aktivität **[!UICONTROL Laden (DBMS)]** dient dem Abruf von für die Zielgruppenbestimmung erforderlichen Daten durch Zugriff auf externe Datenbanken.

Um eine korrekte Performance sicherzustellen, ist die Verwendung einer Abfrageaktivität vorzuziehen, die ebenfalls den Abruf externer Daten erlaubt. Weitere Informationen hierzu finden Sie unter [Zugriff auf externe Datenbanken (FDA)](accessing-an-external-database-fda.md).

Gehen Sie wie folgt vor:

1. Wählen Sie aus der Dropdown-Liste die Datenquelle aus und geben Sie den Namen der Tabelle an, die die zu extrahierenden Daten enthält.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Der Name der in das entsprechende Feld eingegebenen Tabelle wird als Vorlage für die Datenerfassung in der externen Datenbank verwendet. Der Name der vom Workflow verarbeiteten Tabelle kann durch die eingehende Transition der Aktivität Laden berechnet oder übermittelt werden. Um die zu verwendende Tabelle auszuwählen, klicken Sie auf den Link **[!UICONTROL Erweitert..]** und wählen Sie die Option **[!UICONTROL In der Transition angegeben]** oder **[!UICONTROL Explizit]** aus.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Klicken Sie auf den Link **[!UICONTROL Zu extrahierende Spalten auswählen...]**, um die abzurufenden Daten auszuwählen.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Sie können einen Filter für diese Daten definieren. Klicken Sie dazu auf den Link **[!UICONTROL Abfrage bearbeiten…]**.

   Die derart abgerufenen Daten sind im weiteren Verlauf des Workflows verwendbar.
