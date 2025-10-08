---
product: campaign
title: Adobe Campaign-Arbeitsbereich
description: Erfahren Sie, wie Sie den Campaign-Arbeitsbereich verwenden und anpassen.
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 9df46ed923831ffdfb28acddfbc371cecafb251c
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 83%

---

# Adobe Campaign-Arbeitsbereich {#adobe-campaign-workspace}

## Über die Benutzeroberfläche von Adobe Campaign {#about-adobe-campaign-interface}

Nach Herstellung der Datenbankverbindung gelangen Sie auf die Startseite von Adobe Campaign. Diese ist wie ein Dashboard gestaltet und besteht aus Links und Verknüpfungen, die Ihnen je nach Installation den Zugriff auf Funktionen und die allgemeinen Konfigurationselemente der Plattform erlauben.

In der Mitte des Fensters haben Sie die Möglichkeit, auf die Online-Dokumentation, das Forum und die Webseite des Supports zuzugreifen.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) [&#x200B; Campaign-Arbeitsbereich im Video kennenlernen](#video)

>[!NOTE]
>
>Die in Ihrer Instanz verfügbaren Adobe Campaign-Funktionen hängen von den installierten Modulen und Add-ons ab. Je nach Ihren Berechtigungen und Konfigurationen sind manche möglicherweise nicht verfügbar.
>
>Prüfen Sie Ihren Lizenzvertrag oder kontaktieren Sie Ihren Adobe-Kundenbetreuer, bevor Sie Module oder Add-ons installieren.

### Zugriff über Client-Konsole versus Web-Zugriff {#console-and-web-access}

Auf die Adobe Campaign-Plattform kann entweder über eine Konsole oder über einen Webbrowser zugegriffen werden. Die kompatiblen Browser entnehmen Sie der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#Browsers).

Die Benutzeroberfläche für den Web-Zugriff ähnelt der Benutzeroberfläche der Konsole. Von einem Browser aus können Sie dieselben Funktionen zum Navigieren und Anzeigen wie in der Konsole verwenden, aber Sie können nur einen reduzierten Satz von Aktionen für Kampagnen durchführen. Sie können beispielsweise Kampagnen anzeigen und abbrechen, aber keine Kampagnen ändern. So wird beispielsweise für einen Benutzer in der Konsole eine Kampagne mit folgenden Optionen angezeigt:

![Über das Dashboard einer Kampagne kann der Benutzer eine Kampagne anzeigen und abbrechen, sie aber auch ändern und Sendungen, Dokumente und Aufgaben zu diese Kampagne hinzufügen.](assets/operation_from_console.png)

Beim Web-Zugriff ermöglichen die Optionen jedoch vor allem das Anzeigen:

![Derselbe Benutzer kann von einem Browser aus nur die Kampagne anzeigen und abbrechen.](assets/operation_from_web.png)

Weitere Informationen zum [Web-Zugriff](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### Sprachen {#languages}

Die Sprache wird bei der Installation der Adobe Campaign Classic-Instanz ausgewählt.

![](assets/language.png)

Sie können zwischen fünf verschiedenen Sprachen wählen:

* Englisch (UK)
* Englisch (US)
* Französisch
* Deutsch
* Japanisch

Die für Ihre Adobe Campaign Classic-Instanz ausgewählte Sprache kann sich auf Datums- und Uhrzeitformate auswirken. Weitere Informationen hierzu finden Sie in der Dokumentation zu [&#x200B; v8 (Konsole](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Weiterführende Informationen zum Erstellen einer Instanz finden Sie auf dieser [Seite](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>Die Sprache kann nach der Instanzerstellung nicht mehr geändert werden.

## Navigationsprinzipien {#navigation-basics}

### Seiten durchsuchen {#browsing-pages}

Die Funktionen der Plattform sind in verschiedene Rubriken unterteilt. Verwenden Sie die Links im oberen Bereich der Bedieneroberfläche, um darauf zuzugreifen.

![](assets/overview_home.png)

Die Liste der Rubriken hängt von den installierten Packages und Add-ons sowie den Zugriffsberechtigungen des aktuellen Benutzers ab.

Jede Funktion umfasst eine Reihe von Funktionen, die auf aufgabenbezogenen Anforderungen und dem Anwendungskontext basieren. So haben Sie z. B. in der Rubrik **[!UICONTROL Profile und Zielgruppen]** Zugriff auf Empfängerlisten, Abonnements, existierende Zielgruppen-Workflows sowie auf Verknüpfungen zur Elementerstellung.

Listen z. B. sind somit über den Link **[!UICONTROL Listen]** verfügbar, der sich auf der linken Seite des Fensters **[!UICONTROL Profile und Zielgruppen]** befindet.

![](assets/recipient_list_overview.png)

### Tabs verwenden {#using-tabs}

* Wenn Sie eine Rubrik oder einen Link auswählen, ersetzt die aufgerufene Seite die aktuelle. Um zur vorherigen Seite zurückzukehren, klicken Sie auf die Schaltfläche **[!UICONTROL Zurück]** in der Symbolleiste. Um zur Startseite zurückzukehren, klicken Sie auf die Schaltfläche **[!UICONTROL Startseite]**.

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* Bei der Auswahl eines Menüs oder einer Verknüpfung mit einer Webanwendung, einem Programm, einem Versand, einem Bericht o. Ä. öffnet sich die Seite in einem neuen Tab. Dies ermöglicht das Wechseln zwischen verschiedenen Ansichten durch die Auswahl des entsprechenden Tabs.

  ![](assets/d_ncs_user_interface_tabs.png)

### Element erstellen {#creating-an-element}

In jeder Rubrik können Sie sich innerhalb der verschiedenen Elemente bewegen. Nutzen Sie hierzu die im Abschnitt **[!UICONTROL Navigation]** zur Verfügung stehenden Verknüpfungen. Der Link **[!UICONTROL Andere Optionen]** erlaubt den Zugriff auf alle anderen Seiten, unabhängig von der aktuellen Rubrik.

Sie können ein neues Element (Versand, Web-Anwendung, Workflow usw.) mithilfe der Tastaturbefehle im Abschnitt **[!UICONTROL Erstellen]** auf der linken Bildschirmseite erstellen. Die Schaltfläche **[!UICONTROL Erstellen]** rechts oberhalb der Liste erlaubt das Hinzufügen eines neuen Listenelements.

Nutzen Sie beispielsweise auf der Seite der Sendungen die Schaltfläche **[!UICONTROL Erstellen]**, um einen neuen Versand anzulegen.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Adobe Campaign-Explorer verwenden {#using-adobe-campaign-explorer}

Auf den Adobe Campaign-Explorer kann über das entsprechende Symbol in der Symbolleiste zugegriffen werden. Mit seiner Hilfe gelangen Sie zu allen Adobe Campaign-Funktionen und in die verschiedenen Konfigurationsbildschirme der Adobe Campaign-Plattform und können einige Plattformelemente im Detail anzeigen.

Weitere Informationen zu Adobe Campaign Explorer finden Sie auf diesen Seiten in der Dokumentation zu Campaign v8 (Konsole):

* [Übersicht über die Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}

* [Einstellungen der Campaign-Benutzeroberfläche](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [Ordner und Ansichten im Explorer verwalten](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


## Filtern von Daten {#filters}

Beim Filtern von Daten wird ein Datensatz so eingegrenzt, dass er nur die Datensätze enthält, die bestimmten Kriterien entsprechen. Diese Teilmenge kann dann für zielgerichtete Aktionen (wie Aktualisierungen oder Zielgruppenerstellung) oder für Analysen verwendet werden.

Beim Durchsuchen von Campaign werden die Daten in Listen angezeigt. Sie können integrierte Filter anwenden, um schnell auf eine definierte Teilmenge zuzugreifen, z. B. Adressen in Quarantäne, nicht kontaktierte Empfänger oder Datensätze innerhalb eines bestimmten Altersbereichs oder Erstellungsdatums. Darüber hinaus können Sie benutzerdefinierte Filter erstellen, sie für die zukünftige Verwendung speichern und für andere Campaign-Benutzer freigeben.

>[!NOTE]
>
>Informationen zum Zugreifen auf, Entwerfen und Freigeben von Filtern finden Sie in der Dokumentation [Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.


## Arbeiten mit Listen {#manage-and-customize-lists}

In der Campaign-Client-Console werden die Daten in Listen angezeigt. Sie können diese Listen Ihren Bedürfnissen entsprechend anpassen. Sie können beispielsweise Spalten hinzufügen, Daten filtern, Einträge zählen und Ihre Einstellungen speichern und freigeben.

>[!NOTE]
>
>Informationen zum Verwalten und Anpassen von Listen finden Sie in der Dokumentation [Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.

## Verwalten von Aufzählungen{#managing-enumerations}

Eine Aufzählung (auch als Aufzählungsliste bezeichnet) ist eine vordefinierte Liste von Werten, die Sie zum Ausfüllen bestimmter Felder verwenden können. Aufzählungen helfen dabei, Feldwerte zu standardisieren, sodass die Dateneingabe konsistenter wird und Abfragen vereinfacht werden.

Wenn Werte definiert sind, werden sie in einer Dropdown-Liste angezeigt. Ein Wert kann direkt ausgewählt oder über eine prädiktive Eingabe eingegeben werden, bei der übereinstimmende Einträge vorgeschlagen und ausgefüllt werden. Einige Felder enthalten vordefinierte Aufzählungen. Bei Bedarf können zusätzliche Aufzählungen erstellt werden.

Weitere Informationen zum **Arbeiten mit Aufzählungen** finden Sie in der [Dokumentation zu Adobe Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.

## Anleitungsvideo {#video}

In diesem Video wird der Campaign Classic-Arbeitsbereich vorgestellt.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)
