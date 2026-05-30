---
product: campaign
title: Entwerfen eines Web-Programms
description: Entwerfen eines Web-Programms
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
TQID: https://experienceleague.adobe.com/8HdoOgOBgZgI3-Kxnn-I0kW5zyTSBfUtM0IoLGBvHag
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 309
ht-degree: 80%

---

# Web-Anwendung konzipieren{#designing-a-web-application}



Web-Anwendungen werden nach dem gleichen Prinzip wie [Web-Formulare](about-web-forms.md) erstellt und verwaltet.

>[!CAUTION]
>
>Verwenden Sie die Unterregisterkarte **[!UICONTROL Vorschau]**, um Fehler beim Design von Web-Anwendungen zu überprüfen. Beachten Sie, dass der Profiltest, der für die Vorschau Ihrer Web-Anwendung verwendet wird, in einem Ordner abgelegt sein muss, auf den Benutzer vom Typ **[!UICONTROL Web-Anwendungsagent]** **[!UICONTROL Zugriffsrechte]** haben. </br>Bis zur Veröffentlichung der Web-Anwendung werden die Änderungen den Endbenutzern nicht angezeigt.

## Grafiken in eine Web-Anwendung einfügen {#inserting-charts-in-a-web-application}

Sie können Diagramme in Web-Anwendungen einbeziehen. Verwenden Sie dazu die Dropdown-Liste der Diagramme in der Taskleiste, um den Typ des einzufügenden Diagramms auszuwählen.

![](assets/s_ncs_admin_webapps_bar_graph.png)

Sie können auch das Menü **[!UICONTROL Grafik hinzufügen]** verwenden.

![](assets/s_ncs_admin_webapps_graph.png)

## Tabellen in eine Web-Anwendung einfügen {#inserting-tables-in-a-web-application}

Wenn Sie eine Tabelle hinzufügen möchten, verwenden Sie die Tabellen-Dropdown-Liste in der Symbolleiste und wählen Sie den Typ der einzufügenden Tabelle aus.

![](assets/s_ncs_admin_webapps_bar_table.png)

Sie können den Tabellentyp auch im Dropdown-Menü auswählen.

![](assets/s_ncs_admin_webapps_table.png)

## Web-Anwendungen vom Typ &quot;Übersicht&quot; {#overview-type-web-applications}

In der Benutzeroberfläche von Adobe Campaign werden zahlreiche Webanwendungen bereitgestellt, die es Ihnen ermöglichen, auf Empfänger, Sendungen, Kampagnen, gespeicherte Assets etc. zuzugreifen, sie zu verwalten und mit ihnen zu interagieren.

In der Benutzeroberfläche erscheinen sie in Form von Dashboards, die aus einer einzigen Seite bestehen.

Die nativen Webanwendungen sind im Knoten **[!UICONTROL Administration > Konfiguration > Webanwendungen]** gespeichert.

## Web-Anwendungen mit Bearbeitungsformularen bearbeiten {#edit-forms-type-web-applications}

Webanwendungen mit Bearbeitungsformularen für ein Extranet besitzen folgende Merkmale:

* Eine Option zum Vorausfüllen

  In den meisten Fällen müssen die anzuzeigenden Daten vorgeladen werden. Da die Benutzer, die auf diese Formulare zugreifen, (über eine Zugriffssteuerung) identifiziert werden, ist das Vorabladen nicht unbedingt verschlüsselt.

* Eine Option zum Speichern
* Eine Option zum Hinzufügen von Seiten

  Während Webanwendungen vom Typ &quot;Übersicht&quot; eine einzige Seite besitzen, bieten Bearbeitungsformulare mehrere Seiten basierend auf bestimmten Kriterien (Tests, Auswahl, Profil des verbundenen Benutzers etc.).

