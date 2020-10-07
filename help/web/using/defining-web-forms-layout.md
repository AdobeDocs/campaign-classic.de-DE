---
title: Layout eines Webformulars definieren
seo-title: Layout eines Webformulars definieren
description: Layout eines Webformulars definieren
seo-description: null
page-status-flag: never-activated
uuid: ae8659d0-3608-44dd-93ec-33c418a66ad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 67d1d39b-3a5f-4ed6-8fcf-570891043b10
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 100%

---


# Layout eines Webformulars definieren{#defining-web-forms-layout}

## Container erstellen {#creating-containers}

Mit Containern können Sie die Felder einer Seite zusammenfassen und ihr Layout konfigurieren, um die Elemente der Seite anzuordnen.

Sie können für jede Seite des Formulars Container mit der Schaltfläche **[!UICONTROL Container]** in der Symbolleiste erstellen.

![](assets/s_ncs_admin_survey_containers_add.png)

Mit Containern können Sie die Elemente einer Seite gruppieren, ohne einen Titel zum endgültigen Rendering hinzuzufügen. Die Elemente sind im Container-Unterverzeichnis zusammengefasst. Mit Standard-Containern können Sie das Layout verwalten.

Beispiel:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

Die Position der Titel wird auf die Elemente angewendet, die sich in der Hierarchie unter dem Container befinden. Bei Bedarf kann die Position in jedem Element überschrieben werden. Zum Ändern des Layouts können Spalten hinzugefügt oder entfernt werden. Siehe [Die Felder auf der Seite positionieren](#positioning-the-fields-on-the-page).

Im obigen Beispiel wird das Rendering wie folgt ausgeführt:

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## Die Felder auf der Seite positionieren {#positioning-the-fields-on-the-page}

Das Layout jeder Seite des Webformulars ist in jedem Container definiert und kann für jedes Steuerelement überschrieben werden.

Seiten sind in Spalten unterteilt: Jede Seite enthält eine bestimmte Anzahl von Spalten. Jedes Feld der Seite hat **n** Zellen. Container umfassen auch eine gewisse Anzahl von Spalten und die in ihnen enthaltenen Felder haben eine bestimmte Anzahl von Zellen.

Standardmäßig werden Seiten auf einer einzigen Spalte erstellt und jedes Element hat eine einzige Zelle. Das bedeutet, dass Felder untereinander angezeigt werden, wobei jedes wie unten dargestellt eine ganze Zeile umfasst:

![](assets/s_ncs_admin_survey_container_ex.png)

Im folgenden Beispiel wurde die Standardkonfiguration beibehalten. Die Seite umfasst eine einzige Spalte mit vier Containern.

![](assets/s_ncs_admin_survey_container_ex0.png)

Jeder Container belegt eine Spalte und jedes Element belegt eine Zelle:

![](assets/s_ncs_admin_survey_container_ex0a.png)

Das Rendering sieht folgendermaßen aus:

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

Sie können die Anzeigeparameter anpassen, um das folgende Rendering zu erhalten:

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

Im obigen Rendering-Beispiel belegt jedes Eingabefeld, jeder Titel und jedes Bild eine einzige Zelle in den Spalten der Container.

Sie können die Formatierung in jedem Container ändern. In unserem Beispiel können Sie den Inhalt von Container 4 auf zwei Spalten aufteilen und die Elemente verteilen.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

Der Titel und die Liste befinden sich in je einer Zelle (und daher in einer ganzen Zeile des Containers) und die Checkbox erstreckt sich über zwei Zellen. Die Anzahl der dem Eingabefeld zugeordneten Zellen ist im Tab **[!UICONTROL Allgemein]** oder im Tab **[!UICONTROL Erweitert]** entsprechend dem Feldtyp definiert:

![](assets/s_ncs_admin_survey_container_ex2.png)

## Die Position von Titeln definieren {#defining-the-position-of-labels}

Sie können die Ausrichtung von Feldern und Titeln im Formular definieren.

Standardmäßig übernehmen die Anzeigeparameter für Felder und andere Inhalte der Seite die allgemeine Konfiguration des Formulars, die Konfiguration der Seite oder die Konfiguration des übergeordneten Containers, sofern einer vorhanden ist.

Die globalen Anzeigeparameter für das gesamte Formular werden im Eigenschaftsfeld des Formulars festgelegt. Im Tab **[!UICONTROL Rendering]** kann die Position der Titel ausgewählt werden.

![](assets/s_ncs_admin_survey_label_position.png)

Diese Position kann für jede Seite, jeden Container und jedes Feld über den Tab **[!UICONTROL Erweitert]** überschrieben werden.

Folgende Ausrichtungen werden unterstützt:

* Geerbt: Die Ausrichtung wird vom übergeordneten Element (Standardwert) übernommen, d. h. vom übergeordneten Container, sofern vorhanden, oder ansonsten von der Seite.
* Links/rechts: Der Titel wird rechts oder links neben dem Feld positioniert.
* Oberhalb/unterhalb: Der Titel wird ober- oder unterhalb des Felds positioniert.
* Ausgeblendet: Der Titel wird nicht angezeigt.

