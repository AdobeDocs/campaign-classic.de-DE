---
product: campaign
title: Laden (DBMS)
description: Erfahren Sie mehr über die Workflow-Aktivität "Laden (DBMS)".
feature: Workflows, Data Management Activity
hide: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
TQID: https://experienceleague.adobe.com/w7MFQZpUw-a0SIp634sptKz2VKm2MTZisjmN3VLDt2g
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 203
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
