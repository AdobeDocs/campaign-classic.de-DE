---
product: campaign
title: Laden (DBMS)
description: Erfahren Sie mehr über die Workflow-Aktivität "Laden (DBMS)".
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: ht
source-wordcount: '203'
ht-degree: 100%

---

# Laden (DBMS){#data-loading-rdbms}

![](../../assets/common.svg)

Die Aktivität **[!UICONTROL Laden (DBMS)]** dient dem Abruf von für die Zielgruppenbestimmung erforderlichen Daten durch Zugriff auf externe Datenbanken.

Um eine korrekte Leistung sicherzustellen, ist die Verwendung einer Abfrageaktivität vorzuziehen, die ebenfalls den Abruf externer Daten erlaubt. Weitere Informationen hierzu finden Sie unter [Zugriff auf externe Datenbanken (FDA)](accessing-an-external-database--fda-.md).

Gehen Sie wie folgt vor:

1. Wählen Sie aus der Dropdown-Liste die Datenquelle aus und geben Sie den Namen der Tabelle an, die die zu extrahierenden Daten enthält.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Der Name der Tabelle dient als Vorlage zum Abruf der externen Daten. Der Name der Tabelle, die tatsächlich vom Workflow verarbeitet wird, kann berechnet oder von einer eingehenden Transition übermittelt werden. Um die zu verwendende Tabelle auszuwählen, klicken Sie auf **[!UICONTROL Erweitert...]** und wählen Sie die Option **[!UICONTROL Wird durch die Transition angegeben]** oder **[!UICONTROL Explizit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Klicken Sie auf den Link **[!UICONTROL Zu extrahierende Spalten auswählen...]**, um die abzurufenden Daten auszuwählen.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Durch Klick auf **[!UICONTROL Abfrage bearbeiten...]** können die Daten gefiltert werden.

   Derart abgerufene Daten sind im weiteren Verlauf des Workflows verwendbar.
