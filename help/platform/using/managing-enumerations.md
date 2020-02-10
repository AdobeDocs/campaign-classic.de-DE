---
title: Auflistungen verwalten
seo-title: Auflistungen verwalten
description: Auflistungen verwalten
seo-description: null
page-status-flag: never-activated
uuid: 23ad4cae-237f-48e5-b111-cfe88cf0b864
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 7674c856-2b64-4a85-9ffa-3e14a142028e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Auflistungen verwalten{#managing-enumerations}

## Über Auflistungen {#about-enumerations}

Eine Auflistung ist eine Liste mit vom System vorgeschlagenen Werten für das Ausfüllen bestimmter Felder. Mithilfe von Auflistungen können Sie die Werte dieser Felder vereinheitlichen und die Dateneingabe und Nutzung in Abfragen vereinfachen.

Die Werteliste erscheint in Form einer Dropdown-Liste, wo der dem Feld zuzuordnende Wert ausgewählt werden kann. Die Dropdown-Liste ermöglicht zudem die prädiktive Eingabe: Der Benutzer gibt die ersten Buchstaben ein und die Anwendung vervollständigt automatisch den Wert.

Diverse Felder der Anwendung enthalten derartige Auflistungen. Sie werden &quot;offen&quot; genannt, wenn Werte über eine direkte Eingabe im entsprechenden Feld hinzufügt werden können.

## Wertekonfiguration {#access-to-values}

The values for this type of field are defined and overall administration of these fields (adding/deleting a value) is performed via the **[!UICONTROL Administration > Platform > Enumerations]** node of the tree.

![](assets/s_ncs_user_itemized_list_node.png)

* Im oberen Abschnitt befindet sich die Liste der Felder, für die eine Auflistung bestimmt wurde.
* Im unteren Abschnitt werden die vorgeschlagenen Werte aufgelistet. Diese Werte werden in den Eingabemasken wiederaufgenommen, die das entsprechende Feld verwenden.

   ![](assets/s_ncs_user_itemized_list_values.png)

   To create a new enumeration value, click **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_itemized_list.png)

   Wenn die **[!UICONTROL Open]** Option ausgewählt ist, kann der Benutzer direkt im entsprechenden Feld einen neuen Einzellistenwert hinzufügen. Mit einer Bestätigungsmeldung können Sie diesen Wert erstellen.

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* If the **[!UICONTROL Closed]** option is selected, users will not be able to create new values, but merely choose from the values available.

## Daten vereinheitlichen {#standardizing-data}

### Über die Alias-Verwaltung {#about-alias-cleansing}

In Auflistungsfelder können auch andere als die in der Auflistung vorgesehenen Werte eingegeben werden. Diese Werte können entweder, wie sie sind, gespeichert oder aber bereinigt werden.

>[!CAUTION]
>
>Die Bereinigung von Daten ist ein kritischer Prozess, der auf die Daten in der Datenbank einwirkt. Adobe Campaign aktualisiert Daten gebündelt, was zur Löschung von gewissen Werten führen kann. Dieser Vorgang ist daher erfahrenen Benutzern vorbehalten.

Der eingegebene Wert kann:

* Added to the itemized list values: in this case the **[!UICONTROL Open]** option must be selected,
* automatisch von seinem ersetzt werden. Hierzu muss Letzterer zuvor im Tab **[!UICONTROL Alias]** Alias bestimmt worden sein;
* in der Liste der Alias gespeichert werden. Die Zuordnung des Alias kann zu einem späteren Zeitpunkt erfolgen.

   >[!NOTE]
   >
   >If you need to use data cleansing capabilities, select the **[!UICONTROL Alias cleansing]** option in the itemized list.

### Alias verwenden {#using-aliases}

Die Option **[!UICONTROL Alias cleansing]** ermöglicht die Verwendung von Aliasen für die ausgewählte Einzelliste. Wenn diese Option aktiviert ist, wird die **[!UICONTROL Alias]** Registerkarte unten im Fenster angezeigt.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Alias-Erstellung {#creating-an-alias}

To create an alias, click **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Geben Sie den zu konvertierenden Alias und den anzuwendenden Wert an und klicken Sie auf **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Überprüfen Sie die Parameter vor dem Bestätigen des Vorgangs.

>[!CAUTION]
>
>Nach Bestätigung dieser Etappe können die zuvor eingegebenen Werte nicht mehr abgerufen werden: Sie wurden ersetzt.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

Thus, when a user enters the value **NEILSEN** in a &quot;company&quot; field (in the Adobe Campaign console or in a form), it will automatically be replaced by the value **NIELSEN Ltd**. Value replacement is performed by the **Alias cleansing** workflow. Siehe [Ausführen der Datenbereinigung](#running-data-cleansing).

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Werte in Alias konvertieren {#converting-values-into-aliases}

To convert an enumeration value into an alias, right-click in the list of values and choose **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Choose the values you want to convert and click **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Click **[!UICONTROL Start]** to run the conversion.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

Nach erfolgreicher Konvertierung wird der Alias der Alias-Liste hinzugefügt.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Alias abrufen {#retrieving-alias-hits}

Die von den Benutzern eingegebenen Werte können in Aliase umgewandelt werden. Wenn der Benutzer einen Wert eingibt, der nicht in der Liste der Einzelangaben enthalten ist, wird der Wert in der **[!UICONTROL Alias]** Registerkarte gespeichert.

The **Alias cleansing** technical workflow recovers these values every night to update itemized list. Siehe [Ausführen der Datenbereinigung](#running-data-cleansing)

Bei Bedarf kann die **[!UICONTROL Hits]** Spalte anzeigen, wie oft dieser Wert eingegeben wurde. Die Berechnung dieses Wertes kann sowohl Zeit- als auch Arbeitsspeicheraufwendungen verursachen. Weitere Informationen finden Sie unter [Berechnen von Einstiegsereignissen](#calculating-entry-occurrences).

### Datenbereinigung durchführen {#running-data-cleansing}

Die Datenbereinigung erfolgt durch den **[!UICONTROL Alias cleansing]** technischen Arbeitsablauf. Die für Aufzählungen definierten Konfigurationen werden während der Ausführung angewendet. Siehe [Alias-Bereinigungsarbeitsablauf](#alias-cleansing-workflow).

Cleansing can be triggered via the **[!UICONTROL Cleanse values...]** link.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

The **[!UICONTROL Advanced parameters...]** link lets you set the date starting from which collected values are taken into account.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Click the **[!UICONTROL Start]** button to run data cleansing.

#### Berechnung der Eingabeanzahl {#calculating-entry-occurrences}

Auf der **[!UICONTROL Alias]** Unterregisterkarte einer Liste kann die Anzahl der Vorkommen eines Alias unter allen eingegebenen Werten angezeigt werden. Diese Informationen sind eine Schätzung und werden in der **[!UICONTROL Hits]** Spalte angezeigt.

>[!CAUTION]
>
>Die Berechnung der Anzahl der Alias-Erscheinungen kann zeitaufwändig sein. Diese Funktion sollte daher mit Vorsicht angewandt werden.

Sie können die Trefferberechnung manuell über den **[!UICONTROL Cleanse values...]** Link ausführen. Klicken Sie dazu auf den **[!UICONTROL Advanced parameters...]** Link und wählen Sie die gewünschten Optionen aus.

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: Dadurch können Sie Treffer aktualisieren, die basierend auf dem eingegebenen Datum bereits berechnet wurden.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: ermöglicht die Ausführung von Berechnungen auf der gesamten Adobe Campaign-Plattform.

Sie können auch einen dedizierten Workflow erstellen, um die Berechnung automatisch in bestimmten Abständen durchzuführen, beispielsweise jede Woche.

To do this, create a copy of the **[!UICONTROL Alias cleansing]** workflow, change the scheduler and use the following settings in the **[!UICONTROL Enumeration value cleansing]** activity:

* **-updateHits** , um die Anzahl der Aliastreffer zu aktualisieren,
* **-updateHits:full** , um alle Aliastreffer neu zu berechnen.

#### Alias-Verwaltungs-Workflow {#alias-cleansing-workflow}

Der Workflow **Alias-Verwaltung** führt die Bereinigung der Auflistungswerte durch. Er wird standardmäßig täglich ausgeführt.

Der Zugriff erfolgt über den **[!UICONTROL Administration > Production > Technical workflows]** Knoten.

![](assets/s_ncs_user_itemized_list_alias_wf.png)

