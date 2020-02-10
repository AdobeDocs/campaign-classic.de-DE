---
title: Filter erstellen
seo-title: Filter erstellen
description: Filter erstellen
seo-description: null
page-status-flag: never-activated
uuid: 9fa4a80d-8f03-4f24-92a1-44f6ae2a2337
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: filtering-data
discoiquuid: 066e730b-2527-4257-b11f-2e73f746a8a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Filter erstellen{#creating-filters}

## Einleitung {#introduction}

Wenn Sie in der Struktur von Adobe Campaign navigieren (über das **[!UICONTROL Explorer]** Menü auf der Homepage), werden die in der Datenbank enthaltenen Daten in Listen angezeigt. Diese Listen können so konfiguriert werden, dass nur die vom Operator benötigten Daten angezeigt werden. Aktionen können dann für die gefilterten Daten gestartet werden. Mit der Filterkonfiguration können Sie Daten aus einer Liste auswählen **[!UICONTROL dynamically]**. Wenn die Daten geändert werden, werden die gefilterten Daten aktualisiert.

>[!NOTE]
>
>Die Anzeigekonfiguration wird lokal auf Workstation-Ebene definiert. Es wird in versteckten Dateien gespeichert, und es kann manchmal notwendig sein, diese Daten zu bereinigen, insbesondere wenn beim Aktualisieren von Daten Probleme auftreten. Verwenden Sie dazu das **[!UICONTROL File > Clear the local cache]** Menü.

## Typologie verfügbarer Filter {#typology-of-available-filters}

Adobe Campaign ermöglicht die Filterung von Datenlisten.

Diese Filter können einmalig angewandt oder zur wiederholten Nutzung gespeichert werden. Es können mehrere Filter gleichzeitig genutzt werden.

Folgende Filtertypen sind in Adobe Campaign verfügbar:

* Standardfilter

   **Standardfilter** stehen oberhalb der Listen zur Verfügung. Sie ermöglichen die Filterung nach standardmäßig festgelegten Feldern (für Empfängerprofile z. B. sind dies Name und E-Mail). Über diese Felder kann nach Zeichen oder nach aus der Dropdown-Liste ausgewählten Bedingungen gefiltert werden.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an e-mail address in the domain "yahoo.com".
-->
Sie können den Standardfilter einer Liste ändern. Weitere Informationen finden Sie unter [Ändern des Standardfilters](#altering-the-default-filter).

* Einfache Filter

   **Einfache Filter** ermöglichen die punktuelle Filterung der Spalten einer Liste. Sie können mittels einfacher Suchkriterien konfiguriert werden.

   Es können mehrere einfache Filter für eine Datenliste kombiniert werden, um eine Suche zu verfeinern. Die Felder der Filterkriterien werden untereinander angezeigt. Sie können unabhängig voneinander gelöscht werden.

   ![](assets/filters_recipient_simple_filter.png)

   Einfache Filter werden unter [Erstellen eines einfachen Filters](#creating-a-simple-filter)ausführlich beschrieben.

* Erweiterte Filter

   **Erweiterte Filter** werden basierend auf einer Abfrage oder einer Kombination von Abfragen über die Daten erstellt.

   Weitere Informationen zum Erstellen eines erweiterten Filters finden Sie unter [Erstellen eines erweiterten Filters](#creating-an-advanced-filter).

   Sie können Funktionen verwenden, um den Inhalt des Filters zu definieren. Weitere Informationen finden Sie unter [Erstellen eines erweiterten Filters mit Funktionen](#creating-an-advanced-filter-with-functions).

   >[!NOTE]
   >
   >Mehr Informationen über die Erstellung von Abfragen in Adobe Campaign erhalten Sie in [diesem Abschnitt](../../platform/using/about-queries-in-campaign.md).

* Benutzerfilter

   Ein **Anwendungsfilter** ist ein erweiterter Filter, dessen Konfiguration zur wiederholten und gemeinsamen Nutzung mit anderen Benutzern gespeichert wird.

   Die **[!UICONTROL Filters]** Schaltfläche oberhalb der Listen bietet eine Reihe von Anwendungsfiltern, die kombiniert werden können, um die Filterung zu verfeinern. Die Methode zum Erstellen dieser Filter wird unter [Speichern eines Filters](#saving-a-filter)beschrieben.

## Standardfilter ändern {#altering-the-default-filter}

Um den Standardfilter für eine Empfängerliste zu ändern, klicken Sie auf die **[!UICONTROL Profiles and Targets > Pre-defined filters]** Node der Struktur.

For all other types of data, configure the default filter via the **[!UICONTROL Administration > Configuration > Predefined filters]** node.

Gehen Sie wie folgt vor:

1. Wählen Sie den Filter aus, der als Standardfilter dienen soll.
1. Klicken Sie auf die **[!UICONTROL Parameters]** Registerkarte und wählen Sie **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Wenn bereits ein Standardfilter für diese Liste definiert wurde, muss dieser vor der Anwendung des neuen Filters deaktiviert werden. Klicken Sie hierzu auf das rote Kreuz oberhalb der Filterfelder.

1. Click **[!UICONTROL Save]** to apply the filter.

   >[!NOTE]
   >
   >Das Fenster &quot;Filterdefinition&quot;wird unter [Erstellen eines erweiterten Filters](#creating-an-advanced-filter) und [Speichern eines Filters](#saving-a-filter)ausführlich beschrieben.

## Einfache Filter erstellen {#creating-a-simple-filter}

Gehen Sie wie folgt vor, um einen **einfachen Filter** zu erstellen:

1. Klicken Sie mit der rechten Maustaste auf das Feld, das Sie filtern möchten, und wählen Sie **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   Die Standard-Filterfelder werden oberhalb der Liste angezeigt.

1. Wählen Sie in der Dropdown-Liste die Filteroption aus oder geben Sie die anzuwendenden Filterbedingungen an (der Auswahl- oder Eingabemodus der Filterbedingungen hängt vom Feldtyp ab: Text, Auflistung etc.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Drücken Sie auf die Enter-Taste oder klicken Sie auf den rechts von den Filterfeldern gelegenen grünen Pfeil, um den Filter zu aktivieren.

Wenn das Feld, nach dem die Daten gefiltert werden sollen, nicht im Profilformular angezeigt wird, können Sie es zu den angezeigten Spalten hinzufügen und anschließend nach dieser Spalte filtern. Befolgen Sie hierzu die nachstehenden Schritte:

1. Click the **[!UICONTROL Configure the list]** icon.

   ![](assets/s_ncs_user_configure_list.png)

1. Wählen Sie die anzuzeigende Spalte aus, zum Beispiel das Alter des Empfängers. Durch Doppelklick wird das Feld zur Liste der Ausgabespalten hinzugefügt.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Klicken Sie mit der rechten Maustaste auf die Spalte **Alter** in der Empfängerliste und wählen Sie **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Nun können Sie die Filteroptionen bezüglich des Alters auswählen.

   ![](assets/s_ncs_user_delete_filter.png)

## Erweiterte Filter erstellen {#creating-an-advanced-filter}

Gehen Sie wie folgt vor, um einen **erweiterten Filter** zu erstellen.

1. Klicken Sie auf die **[!UICONTROL Filters]** Schaltfläche und wählen Sie **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   You can also right-click the list of data to filter and select **[!UICONTROL Advanced filter...]**.

   Daraufhin wird das Fenster zur Bestimmung der Filterbedingungen angezeigt.

1. Click the **[!UICONTROL Expression]** column to define the input value.
1. Click **[!UICONTROL Edit expression]** to select the field to which the filter will be applied.

   ![](assets/s_user_filter_choose_field.png)

1. Wählen Sie in der Liste das Feld aus, in dem die Daten gefiltert werden sollen. Klicken Sie **[!UICONTROL Finish]** zur Bestätigung.
1. Klicken Sie in die Spalte **[!UICONTROL Operator]** und wählen Sie in der Dropdown-Liste den anzuwendenden Operator aus.
1. Wählen Sie einen erwarteten Wert aus der **[!UICONTROL Value]** Spalte. Sie können mehrere Filter kombinieren, um Ihre Abfrage zu verfeinern. Um eine Filterbedingung hinzuzufügen, klicken Sie auf **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. Mithilfe der Pfeile in der Symbolleiste können Sie die Ausdrücke hierarchisch gliedern oder die Reihenfolge der Ausdrücke der Abfrage ändern.
1. Der Standard-Operator zwischen den Ausdrücken ist **Und**, er kann jedoch durch einen Klick in das entsprechende Feld in das entsprechende Feld durch **Oder** bzw. Außer ersetzt werden.

   ![](assets/s_ncs_user_filter_operator.png)

1. Klicken Sie auf **[!UICONTROL OK]**, um die Erstellung des Filters zu bestätigen und ihn auf die Liste anzuwenden.

Der angewendete Filter wird oberhalb der Liste angezeigt.

![](assets/s_ncs_user_filter_adv_edit.png)

Durch Klick auf seinen Titel kann der Filter bearbeitet werden.

To cancel this filter, click the **[!UICONTROL Remove this filter]** icon to the right of the filter.

![](assets/s_ncs_user_filter_adv_remove.png)

Sie können einen erweiterten Filter speichern, um ihn für die zukünftige Verwendung zu verwenden. Weitere Informationen zu diesem Filtertyp finden Sie unter [Speichern eines Filters](#saving-a-filter).

### Erweiterte Filter mit Funktionen erstellen {#creating-an-advanced-filter-with-functions}

Erweiterte Filter können Funktionen verwenden: **Filter mit Funktionen** werden über einen Ausdruckseditor erstellt, der es ermöglicht, anhand von Daten aus der Datenbank und erweiterten Funktionen Formeln zu definieren. Befolgen Sie die Schritte 1, 2 und 3 der Erstellung von erweiterten Filtern und gehen Sie anschließend wie folgt vor:

1. In the field selection window, click **[!UICONTROL Advanced selection]**.
1. Wählen Sie den zu verwendenden Formeltyp aus.

   ![](assets/s_ncs_user_filter_formula_select.png)

   Folgende Optionen stehen zur Verfügung:

   * **[!UICONTROL Field only]** , um ein Feld auszuwählen. Dies ist der Standardmodus.
   * **[!UICONTROL Aggregate]** zur Auswahl der zu verwendenden Summenformel (Zähler, Summe, Durchschnitt, Maximum, Minimum).
   * **[!UICONTROL User filter]** , um einen der vorhandenen Benutzerfilter auszuwählen. Benutzerfilter werden unter [Speichern eines Filters](#saving-a-filter)ausführlich beschrieben.
   * **[!UICONTROL Expression]** , um auf den Ausdruckseditor zuzugreifen.

      Der Ausdruckseditor dient der Erstellung erweiterter Filter. Er gestaltet sich wie folgt:

      ![](assets/s_ncs_user_create_exp_exple01.png)

      Damit können Sie Felder in Datenbanktabellen auswählen und ihnen erweiterte Funktionen hinzufügen: Wählen Sie die zu verwendende Funktion im **[!UICONTROL List of functions]** Menü. Die verfügbaren Funktionen sind in [Liste der Funktionen](../../platform/using/defining-filter-conditions.md#list-of-functions)beschrieben. Wählen Sie dann das Feld bzw. die Felder aus, die von den Funktionen betroffen sind, und klicken Sie auf , um den Ausdruck **[!UICONTROL OK]** zu genehmigen.

      >[!NOTE]
      >
      >Im Abschnitt [Identifizieren von Empfängern, die Geburtstag haben](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is) wird ein Beispiel eines auf einem Ausdruck basierenden Filters dargestellt.

## Filter speichern {#saving-a-filter}

Filter sind jedem Benutzer spezifisch und werden bei jeder Cache-Leerung der Clientkonsole zurückgesetzt.

Sie haben jedoch die Möglichkeit, einen **Anwendungsfilter** durch die Speicherung eines erweiterten zu erstellen. Einmal gespeichert kann dieser über die rechte Maustaste in jeder Liste oder über die Schaltfläche **[!UICONTROL Filters]** Filter oberhalb der Listen wiederverwendet werden.

Direkter Zugriff auf diese Filter besteht zudem über den Versand-Assistenten bei der Zielgruppenbestimmung (nähere Informationen zur Erstellung von Sendungen erhalten Sie in [diesem Abschnitt](../../delivery/using/creating-an-email-delivery.md)). Es gibt folgende Möglichkeiten, einen Anwendungsfilter zu erstellen:

* Konvertieren Sie einen erweiterten Filter in einen Anwendungsfilter. Klicken Sie dazu auf , **[!UICONTROL Save]** bevor Sie den erweiterten Filter-Editor schließen.

   ![](assets/s_ncs_user_filter_save.png)

* Erstellen Sie diesen Anwendungsfilter über den Knoten **[!UICONTROL Administration > Configuration > Predefined filters]** (oder **[!UICONTROL Profiles and targets > Predefined filters]** für Empfänger) der Struktur. Klicken Sie dazu mit der rechten Maustaste auf die Filterliste und wählen Sie **[!UICONTROL New...]**. Das Verfahren entspricht dem zum Erstellen erweiterter Filter.

   Mit dem **[!UICONTROL Label]** Feld können Sie diesem Filter einen Namen geben. Dieser Name wird im Kombinationsfeld der **[!UICONTROL Filters...]** Schaltfläche angezeigt.

   ![](assets/user_filter_apply.png)

You can delete all filters on the current list by right-clicking and selecting **[!UICONTROL No filter]** or via the **[!UICONTROL Filters]** icon located above the list.

You can combine filters by clicking the **[!UICONTROL Filters]** button and using the **[!UICONTROL And...]** menu.

![](assets/s_ncs_user_filter_combination.png)

## Empfängerfilter {#filtering-recipients}

Vordefinierte Filter (siehe [Speichern eines Filters](#saving-a-filter)) ermöglichen es Ihnen, die Profile der in der Datenbank enthaltenen Empfänger zu filtern. Sie können Filter vom **[!UICONTROL Profiles and Targets > Predefined filters]** Knoten der Struktur bearbeiten. Die Filter werden über die **[!UICONTROL Filters]** Schaltfläche im oberen Bereich des Arbeitsbereichs angezeigt.

Wählen Sie einen Filter aus, um seine Parameter anzuzeigen und eine Vorschau der gefilterten Daten zu erhalten.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>For a detailed example of predefined filter creation, refer to [Use case](../../platform/using/use-case.md).

Folgende vordefinierte Filter stehen standardmäßig zur Verfügung:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Titel</strong><br /> </td> 
   <td> <strong>Abfrage</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Haben geöffnet<br /> </td> 
   <td> Auswahl der Empfänger, die einen Versand geöffnet haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Haben geöffnet aber nicht geklickt<br /> </td> 
   <td> Auswahl der Empfänger, die den angegebenen Versand geöffnet, aber keinen Link angeklickt haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inaktive Empfänger<br /> </td> 
   <td> Auswahl der Empfänger, die seit der angegebenen Anzahl an Monaten keinen Versand geöffnet haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Letzte Aktivität nach Gerätetyp<br /> </td> 
   <td> Auswahl der Empfänger, die unter Verwendung eines Geräts vom Typ X den Versand Y in den letzten Z Tagen angeklickt oder geöffnet haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Letzte Aktivität nach Gerätetyp (Tracking)<br /> </td> 
   <td> Auswahl der Empfänger, die unter Verwendung eines Geräts vom Typ X den Versand Y in den letzten Z Tagen angeklickt oder geöffnet haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nicht kontaktierte Empfänger<br /> </td> 
   <td> Auswahl der Empfänger, die seit X Monaten nicht über den Kanal Y kontaktiert wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sehr aktive Empfänger<br /> </td> 
   <td> Auswahl der Empfänger, die in den letzten X Monaten mindestens Y Mal geklickt haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> E-Mail-Adresse auf Blacklist<br /> </td> 
   <td> Auswahl der Empfänger, deren E-Mail-Adresse auf der Blacklist steht.<br /> </td> 
  </tr> 
  <tr> 
   <td> E-Mail-Adresse in Quarantäne<br /> </td> 
   <td> Auswahl der Empfänger, deren E-Mail-Adresse in Quarantäne ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> Im Ordner mehrfach enthaltene E-Mail-Adressen<br /> </td> 
   <td> Auswahl der Empfänger, deren E-Mail-Adresse mehrfach im zugrunde liegenden Ordner enthalten ist.<br /> </td> 
  </tr> 
  <tr> 
   <td> Haben weder geöffnet noch geklickt<br /> </td> 
   <td> Auswahl der Empfänger, die den angegebenen Versand weder geöffnet noch darin auf einen Link geklickt haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Neue Empfänger (Tage)<br /> </td> 
   <td> Auswahl der Empfänger, die in den letzten X Tagen erstellt wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Neue Empfänger (Minuten)<br /> </td> 
   <td> Auswahl der Empfänger, die in den letzten X Minuten erstellt wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Neue Empfänger (Monate)<br /> </td> 
   <td> Auswahl der Empfänger, die in den letzten X Monaten erstellt wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Abonnement<br /> </td> 
   <td> Auswahl der Empfänger, die den angegebenen Dienst abonniert haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Klicks auf eine spezifische URL<br /> </td> 
   <td> Auswahl der Empfänger, die im Versand X auf die URL Y geklickt haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Verhalten im Anschluss an einen Versand<br /> </td> 
   <td> Auswahl der Empfänger, die nach Erhalt des Versands X mit dem Verhalten Y reagiert haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Erstellungsdatum<br /> </td> 
   <td> Auswahl der Empfänger, die im Zeitraum von vor X bis Y Monaten (jeweils aktuelles Datum abzüglich n Monate) erstellt wurden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Liste<br /> </td> 
   <td> Auswahl der Empfänger, die der angegebenen Liste angehören.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Anzahl an Klicks<br /> </td> 
   <td> Auswahl der Empfänger, die in den letzten X Monaten zwischen Y und Z Mal in Sendungen geklickt haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Anzahl an empfangenen Nachrichten<br /> </td> 
   <td> Auswahl der Empfänger, die über den angegebenen Kanal in den letzten X Monaten zwischen Y und Z Nachrichten erhalten haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Anzahl an Öffnungen<br /> </td> 
   <td> Auswahl der Empfänger, die in den letzten X Monaten zwischen Y und Z Sendungen geöffnet haben.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Name oder E-Mail<br /> </td> 
   <td> Auswahl der Empfänger nach Nachname oder E-Mail-Adresse.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nach Altersgruppen<br /> </td> 
   <td> Auswahl der Empfänger im Alter von X bis Y Jahren.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alle Zählungen und Zeiträume betreffenden Vergleiche verstehen sich einschließlich der angegebenen Werte.

Zum Beispiel:

* Auswahl der Empfänger im Alter von 30 Jahren und jünger:

   ![](assets/predefined_filters_01.png)

* Auswahl der Empfänger im Alter von 18 Jahren und älter:

   ![](assets/predefined_filters_03.png)

* Auswahl der Empfänger zwischen 18 und 30 Jahren:

   ![](assets/predefined_filters_02.png)

## Erweiterte Parameter von Datenfiltern {#advanced-settings-for-data-filters}

Click the **[!UICONTROL Settings]** tab to access the following options:

* **[!UICONTROL Default filter for the associated document type]**: Mit dieser Option können Sie diesen Filter standardmäßig im Editor der von der Sortierung betroffenen Listen vorschlagen.

   Der **[!UICONTROL By name or login]** Filter wird beispielsweise auf Operatoren angewendet. Diese Option ist aktiviert, sodass der Filter immer in allen Operatorlisten angezeigt wird.

* **[!UICONTROL Filter shared with other operators]**: Mit dieser Option können Sie den Filter allen anderen Operatoren in der aktuellen Datenbank zur Verfügung stellen.
* **[!UICONTROL Use parameter entry form]**: Mit dieser Option können Sie die Filterfelder definieren, die über der Liste angezeigt werden sollen, wenn dieser Filter ausgewählt ist. Mit diesen Feldern können Sie die Filtereinstellungen definieren. Dieses Formular muss über die **[!UICONTROL Form]** Schaltfläche im XML-Format eingegeben werden. Beispielsweise zeigt der vorkonfigurierte Filter, der in der Liste der Empfänger verfügbar **[!UICONTROL Recipients who have opened]** ist, ein Filterfeld an, in dem Sie die Bereitstellung auswählen können, für die der Filter bestimmt ist.

   The **[!UICONTROL Preview]** button displays the result of the selected filter.

* Über den **[!UICONTROL Advanced parameters]** Link können Sie weitere Einstellungen festlegen. Insbesondere können Sie eine SQL-Tabelle mit dem Filter verknüpfen, um sie allen Editoren, die die Tabelle gemeinsam verwenden, zuzuordnen.

   Wählen Sie die **[!UICONTROL Do not restrict the filter]** Option aus, wenn Sie verhindern möchten, dass der Benutzer diesen Filter außer Kraft setzt.

   Diese Option ist zum Beispiel für die im Versand-Assistenten angebotenen Filter &quot;Versandempfänger&quot; und &quot;Zu einem Ordner gehörende Versandempfänger&quot; aktiv, die nicht überschrieben werden können.

   ![](assets/s_ncs_user_filter_advanced_param.png)

