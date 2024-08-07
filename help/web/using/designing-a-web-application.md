---
product: campaign
title: Entwerfen eines Web-Programms
description: Entwerfen eines Web-Programms
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 100%

---

# Web-Anwendung konzipieren{#designing-a-web-application}



Web-Anwendungen werden nach dem gleichen Prinzip wie [Web-Formulare](about-web-forms.md) erstellt und verwaltet.

>[!CAUTION]
>
>Verwenden Sie die Unterregisterkarte **[!UICONTROL Vorschau]**, um Fehler beim Design von Web-Anwendungen zu überprüfen. Beachten Sie, dass der Profiltest, der für die Vorschau Ihrer Web-Anwendung verwendet wird, in einem Ordner abgelegt sein muss, auf den Benutzer vom Typ **[!UICONTROL Web-Anwendungsagent]** **[!UICONTROL Zugriffsrechte]** haben. </br>Bis zur Veröffentlichung der Web-Anwendung werden die Änderungen den Endbenutzern nicht angezeigt.

## Grafiken in eine Web-Anwendung einfügen {#inserting-charts-in-a-web-application}

Sie können Grafiken in Webanwendungen einfügen. Verwenden Sie dazu die Grafiken-Dropdown-Liste in der Symbolleiste und wählen Sie die Art der einzufügenden Grafik aus.

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

  In den meisten Fällen müssen die Daten, die angezeigt werden sollen, vorausgefüllt werden. Da sich die Benutzer, die auf diese Formulare zugreifen, über eine Zugriffskontrolle identifizieren müssen, muss das Vorausfüllen nicht unbedingt verschlüsselt erfolgen.

* Eine Option zum Speichern
* Eine Option zum Hinzufügen von Seiten

  Während Webanwendungen vom Typ &quot;Übersicht&quot; eine einzige Seite besitzen, bieten Bearbeitungsformulare mehrere Seiten basierend auf bestimmten Kriterien (Tests, Auswahl, Profil des verbundenen Benutzers etc.).

