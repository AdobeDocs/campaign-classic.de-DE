---
product: campaign
title: Adobe Campaign-Arbeitsbereich
description: Erfahren Sie, wie Sie den Campaign-Arbeitsbereich verwenden und anpassen.
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '942'
ht-degree: 97%

---

# Adobe Campaign-Arbeitsbereich{#adobe-campaign-workspace}



## Über die Benutzeroberfläche von Adobe Campaign {#about-adobe-campaign-interface}

Nach Herstellung der Datenbankverbindung gelangen Sie auf die Startseite von Adobe Campaign. Diese ist wie ein Dashboard gestaltet und besteht aus Links und Verknüpfungen, die Ihnen je nach Installation den Zugriff auf Funktionen und die allgemeinen Konfigurationselemente der Plattform erlauben.

In der Mitte des Fensters haben Sie die Möglichkeit, auf die Online-Dokumentation, das Forum und die Webseite des Supports zuzugreifen.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ Campaign-Arbeitsbereich im Video kennenlernen](#video)

>[!NOTE]
>
>Die in Ihrer Instanz verfügbaren Adobe-Campaign-Funktionen hängen von den installierten Modulen und Add-ons ab. Je nach Ihren Berechtigungen und Konfigurationen sind manche möglicherweise nicht verfügbar.
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

Die für Ihre Adobe Campaign Classic-Instanz ausgewählte Sprache kann sich auf Datums- und Uhrzeitformate auswirken. Weiterführende Informationen hierzu finden Sie in diesem [Abschnitt](../../platform/using/adobe-campaign-workspace.md#date-and-time).

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


## Formate und Einheiten {#formats-and-units}

### Datum und Uhrzeit {#date-and-time}

Die Sprache Ihrer Adobe-Campaign-Classic-Instanz hat Auswirkungen auf das Format von Datum und Uhrzeit.

Die Sprache wird während der Installation von Campaign ausgewählt und kann danach nicht mehr geändert werden. Zur Auswahl stehen: Englisch (US), Englisch (EN), Französisch, Deutsch oder Japanisch. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../installation/using/creating-an-instance-and-logging-on.md).

Die Hauptunterschiede zwischen US-amerikanischem Englisch und britischem Englisch sind:

<table> 
 <thead> 
  <tr> 
   <th> Formate<br /> </th> 
   <th> Englisch (US)<br /> </th> 
   <th> Englisch (EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> Woche beginnt am Sonntag<br /> </td> 
   <td> Woche beginnt am Montag<br /> </td> 
  </tr> 
  <tr> 
   <td> Kurzform des Datums<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>z. B.: 09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>z. B.: 25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> Kurzform des Datums mit Uhrzeit<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>z. B.: 09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>z. B.: 25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### Werte in einer Auflistung hinzufügen {#add-values-in-an-enumeration}

Mithilfe der Eingabefelder mit Dropdown-Liste können Sie einen Auflistungswert eingeben, der gespeichert und dann als Option in der Dropdown-Liste vorgeschlagen werden kann. Beispiel: Im Feld **[!UICONTROL Ort]** auf der Registerkarte **[!UICONTROL Allgemein]** eines Empfängerprofils können Sie „London“ eingeben. Wenn Sie die Eingabetaste drücken, um diesen Wert zu bestätigen, werden Sie gefragt, ob Sie diesen Wert für die mit dem Feld verknüpfte Auflistung speichern möchten.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

Wenn Sie auf **[!UICONTROL Ja]** klicken, erscheint der Wert zukünftig in der Dropdown-Liste des entsprechenden Feldes. (Hier: **[!UICONTROL Ort]**).

>[!NOTE]
>
>Auflistungen werden vom Administrator im Bereich **[!UICONTROL Administration > Plattform > Auflistungen]** verwaltet. Weitere Informationen hierzu finden Sie im Abschnitt [Auflistungen verwalten](../../platform/using/managing-enumerations.md).

### Standardeinheiten {#default-units}

In Feldern, die eine Dauer bezeichnen (z. B. Gültigkeit von Versandressourcen, Validierungszeitraum einer Aufgabe etc.), sind verschiedene **Einheiten** möglich:

* **[!UICONTROL s]** für Sekunden,
* **[!UICONTROL min]** für Minuten,
* **[!UICONTROL h]** für Stunden,
* **[!UICONTROL T]** für Tage.

![](assets/enter_unit_sample.png)

## Anleitungsvideo {#video}

In diesem Video wird der Campaign Classic-Arbeitsbereich vorgestellt.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
