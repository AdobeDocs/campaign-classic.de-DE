---
solution: Campaign Classic
product: campaign
title: Adobe Campaign-Arbeitsbereich
description: Erfahren Sie, wie Sie den Campaign-Arbeitsbereich verwenden und anpassen.
feature: Übersicht
role: Data Engineer
level: Anfänger
translation-type: ht
source-git-commit: c91d9c39d92779ed0366905a944f065c427b1e5a
workflow-type: ht
source-wordcount: '1293'
ht-degree: 100%

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

### Zugriff über Clientkonsole versus Webzugriff {#console-and-web-access}

Auf die Adobe-Campaign-Plattform kann entweder über eine Clientkonsole oder über einen Webbrowser zugegriffen werden.

Der Webzugriff bietet eine der Clientkonsole ähnliche Bedieneroberfläche mit eingeschränkten Funktionalitäten.

So wird z. B. für einen Benutzer eine Kampagne in der Clientkonsole mit folgenden Optionen angezeigt:

![](assets/operation_from_console.png)

Im Webzugriff hingegen stehen vorwiegend konsultative Optionen zur Verfügung:

![](assets/operation_from_web.png)

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

Jede Rubrik enthält eine Reihe von Funktionen, die dem Benutzerkontext und den spezifischen Bedürfnissen entsprechend angeordnet wurden. So haben Sie z. B. in der Rubrik **[!UICONTROL Profile und Zielgruppen]** Zugriff auf Empfängerlisten, Abonnements, existierende Zielgruppen-Workflows sowie auf Verknüpfungen zur Elementerstellung.

Listen z. B. sind somit über den Link **[!UICONTROL Listen]** verfügbar, der sich auf der linken Seite des Fensters **[!UICONTROL Profile und Zielgruppen]** befindet.

![](assets/recipient_list_overview.png)

### Tabs verwenden {#using-tabs}

* Wenn Sie eine Rubrik oder einen Link auswählen, ersetzt die aufgerufene Seite die aktuelle. Mithilfe der Schaltflächen **[!UICONTROL Zurück]** und **[!UICONTROL Startseite]** können Sie zum Ausgangspunkt zurückkehren.

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* Bei der Auswahl eines Menüs oder einer Verknüpfung mit einer Webanwendung, einem Programm, einem Versand, einem Bericht o. Ä. öffnet sich die Seite in einem neuen Tab. Dies ermöglicht das Wechseln zwischen verschiedenen Ansichten durch die Auswahl des entsprechenden Tabs.

   ![](assets/d_ncs_user_interface_tabs.png)

### Element erstellen {#creating-an-element}

In jeder Rubrik können Sie sich innerhalb der verschiedenen Elemente bewegen. Nutzen Sie hierzu die im Abschnitt **[!UICONTROL Navigation]** zur Verfügung stehenden Verknüpfungen. Der Link **[!UICONTROL Andere Optionen]** erlaubt den Zugriff auf alle anderen Seiten, unabhängig von der aktuellen Rubrik.

Neue Elemente (Versand, Webanwendung, Workflow etc.) können über die im Abschnitt **[!UICONTROL Erstellen]** angebotenen Verknüpfungen angelegt werden. Die Schaltfläche **[!UICONTROL Erstellen]** rechts oberhalb der Liste erlaubt das Hinzufügen eines neuen Listenelements.

Nutzen Sie beispielsweise auf der Seite der Sendungen die Schaltfläche **[!UICONTROL Erstellen]**, um einen neuen Versand anzulegen.

![](assets/d_ncs_user_interface_tab_add_del.png)

## Adobe Campaign-Explorer verwenden {#using-adobe-campaign-explorer}

Auf den Adobe-Campaign-Explorer kann über das entsprechende Symbol in der Symbolleiste zugegriffen werden. Mit seiner Hilfe gelangen Sie zu allen Adobe-Campaign-Funktionen und in die verschiedenen Konfigurationsbildschirme der Adobe-Campaign-Plattform. Darüber hinaus bietet er eine detaillierte Ansicht gewisser Elemente.

Die **[!UICONTROL Explorer]**-Ansicht ist in drei Bereiche unterteilt:

![](assets/s_ncs_user_navigation.png)

**1 – Baum**: Sie können den Inhalt des Baums anpassen (Knoten hinzufügen, verschieben oder löschen). Dies sollte nur von Experten durchgeführt werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#about-navigation-hierarchy).

**2 – Liste**: Sie können diese Liste filtern, Suchvorgänge durchführen, Informationen hinzufügen und Daten darin sortieren. [Weitere Informationen](adobe-campaign-ui-lists.md).

**3 – Details**: Sie können Details des ausgewählten Elements anzeigen. Mit dem Symbol rechts oben können Sie die Anzeige zum Vollbildschirm vergrößern.

### Ordner und Navigationsbaum{#about-navigation-hierarchy}

Der Navigationsbaum funktioniert wie ein Datei-Browser (z. B. Windows Explorer). Ordner können Unterordner enthalten. Wenn Sie einen Knoten auswählen, wird die dem Knoten entsprechende Ansicht angezeigt.

Die angezeigte Ansicht ist eine Liste, die mit einem Schema und einem Eingabeformular zur Bearbeitung der ausgewählten Zeile verknüpft ist.

![](assets/d_ncs_integration_navigation.png)

Um dem Baum einen neuen Ordner hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Ordner in der Verzweigung, wo Sie einen Ordner einfügen möchten, und wählen Sie **[!UICONTROL Neuen Ordner hinzufügen]** aus. Wählen Sie im Shortcut-Menü den zu erstellenden Dateityp aus.

![](assets/d_ncs_integration_navigation_create.png)

[In diesem Abschnitt](../../configuration/using/configuration.md) erfahren Sie, wie Sie den Campaign-Navigationsbaum konfigurieren.

[In diesem Abschnitt](access-management-folders.md) erfahren Sie, wie Sie Berechtigungen für Ordner festlegen.

### Best Practices für die Ordnerkonfiguration

* **Integrierte Ordner verwenden**

   Die Verwendung der integrierten Ordner macht es für nicht am Projekt beteiligte Personen einfacher, das Programm zu verwenden, zu warten und Fehler zu beheben. Sie sollten keine benutzerdefinierten Ordnerstrukturen für Empfänger, Listen, Versand usw. erstellen, sondern die Standardordner wie &quot;Administration&quot;, &quot;Profile und Zielgruppen&quot; und &quot;Kampagnenverwaltung&quot; verwenden.

* **Unterordner erstellen**

   Legen Sie technische Workflows im Standardordner &quot;Administration/Produktion/Technische Workflows&quot; ab und legen Sie für jeden Workflow-Typ Unterverzeichnisse an.

* **Namenskonventionen festlegen**

   Sie können die Workflows beispielsweise in alphabetischer Reihenfolge benennen, sodass sie nach der Reihenfolge der Ausführung geordnet angezeigt werden.

   Beispiel:

   * A1 – Empfänger importieren, Beginn um 10:00 Uhr;
   * A2 – Tickets importieren, Beginn um 11:00 Uhr.

* **Vorlagen als Ausgangsbasis für Benutzer erstellen**

   Erstellen Sie benutzerspezifische Versandvorlagen, Workflow-Vorlagen und Kampagnenvorlagen. Dies kann Zeit sparen und sicherstellen, dass für jeden Benutzer das richtige Versand-Mapping und die korrekten Typologien verwendet werden.

### Bildschirmauflösung {#screen-resolution}

Adobe empfiehlt für optimale Navigation und Nutzung eine Bildschirmauflösung von mindestens 1600 x 900 Pixel.

>[!CAUTION]
>
>Auflösungen von weniger als 1.600 x 900 Pixel werden von Adobe Campaign unterstützt.

Wenn im **[!UICONTROL Explorer]** einige Teile des Bereichs **[!UICONTROL Details]** abgeschnitten sind, erweitern Sie den Bereich mit dem Pfeil am oberen Rand oder klicken Sie auf die Schaltfläche **[!UICONTROL Vergrößern]**.

![](assets/s_ncs_user_resolution.png)

### Durchsuchen und Anpassen von Listen {#browsing-lists}

[In diesem Abschnitt ](adobe-campaign-ui-lists.md) erfahren Sie, wie Sie Listen durchsuchen, verwalten und anpassen.

## Formate und Einheiten {#formats-and-units}

### Datum und Uhrzeit {#date-and-time}

Die Sprache Ihrer Adobe-Campaign-Classic-Instanz hat Auswirkungen auf das Format von Datum und Uhrzeit.

Die Sprache wird während der Installation von Campaign ausgewählt und kann danach nicht mehr geändert werden. Zur Auswahl stehen: Englisch (US), Englisch (EN), Französisch, Deutsch oder Japanisch. Weiterführende Informationen dazu finden Sie auf [dieser Seite](../../installation/using/creating-an-instance-and-logging-on.md).

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

Die Eingabefelder in Dropdown-Listen ermöglichen die Angabe eines Auflistungswerts, der zur weiteren Verwendung gespeichert werden kann. Wenn Sie z. B. im Feld **[!UICONTROL Ort]** im Tab **[!UICONTROL Allgemein]** eines Empfängerprofils &quot;Berlin&quot; eingeben und auf Enter drücken, werden Sie gefragt, ob Sie diesen Wert zu der dem Feld entsprechenden Auflistung hinzufügen möchten.

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

In diesem Video wird der Campaign Classic-Workspace vorgestellt.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
