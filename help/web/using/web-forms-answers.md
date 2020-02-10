---
title: Antworten in Webformularen
seo-title: Antworten in Webformularen
description: Antworten in Webformularen
seo-description: null
page-status-flag: never-activated
uuid: 374df070-8969-4bf6-bd24-0b827d38593f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: c89926b6-488e-4c72-8f67-b6af388bade3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Antworten in Webformularen{#web-forms-answers}

## Speicherfelder für Antworten {#response-storage-fields}

Antworten auf Formulare können in einem Feld der Datenbank oder vorübergehend in einer lokalen Variablen gespeichert werden. Der Speichermodus für Antworten wird während der Felderstellung ausgewählt. Es kann über den **[!UICONTROL Edit storage...]** Link bearbeitet werden.

Für jedes Eingabefeld in einem Formular sind die folgenden Speicheroptionen verfügbar:

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   Sie können ein Feld der Datenbank auswählen: Die Antworten der Benutzer werden in diesem Feld gespeichert. Für jeden Benutzer wird nur der zuletzt eingegebene Wert gespeichert: Es wird zu ihrem Profil hinzugefügt: Siehe [Speichern von Daten in der Datenbank](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   Wenn Sie keine Informationen in der Datenbank speichern möchten, können Sie eine Variable verwenden. Lokale Variablen können im Upstream deklariert werden. Siehe [Speichern von Daten in einer lokalen Variablen](#storing-data-in-a-local-variable).

### Speichern von Daten in der Datenbank {#storing-data-in-the-database}

To save the data in an existing field of the database, click the **[!UICONTROL Edit expression]** icon and select it from the list of available fields.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>Das Standardreferenzdokument ist das Schema **nms:empfänger** . Um das Formular anzuzeigen oder ein neues auszuwählen, wählen Sie das Formular in der Liste aus und klicken Sie auf die **[!UICONTROL Properties]** Schaltfläche.

### Daten in einer lokalen Variablen speichern {#storing-data-in-a-local-variable}

Durch die Verwendung lokaler Variablen können Daten auf derselben oder einer anderen Seite wiederverwendet werden, auch wenn sie nicht in der Datenbank gespeichert werden. Dies kann beispielsweise hilfreich sein, um die Anzeige eines Felds an eine Bedingung zu knüpfen oder um eine Nachricht anzupassen.

Das bedeutet, dass Sie den Wert eines nicht gespeicherten Felds verwenden können, um eine Gruppe von Optionen auf der Seite anzuzeigen. Auf der unten dargestellten Seite ist der Fahrzeugtyp nicht in der Datenbank gespeichert.

![](assets/s_ncs_admin_survey_no_storage_variable.png)

It is stored in a variable which must be selected when the drop-down box is created, or via the **[!UICONTROL Edit storage...]** link.

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

Sie können vorhandene Variablen anzeigen und über den **[!UICONTROL Edit variables...]** Link neue erstellen. Click the **[!UICONTROL Add]** button to create a new variable.

![](assets/s_ncs_admin_survey_add_a_variable.png)

Die hinzugefügte Variable wird in der Liste lokaler Variablen verfügbar sein, wenn die Eingabefelder der Seite erstellt werden.

>[!NOTE]
>
>Für jedes Formular können Sie Variablen im Upstream erstellen. Wählen Sie dazu das Formular aus und klicken Sie auf die **[!UICONTROL Properties]** Schaltfläche. Die **[!UICONTROL Variables]** Registerkarte enthält die lokalen Variablen für das Formular.

**Beispiel für die lokale Speicherung mit einer Bedingung**

In the above example, the container that includes data concerning private vehicles is displayed only if the **[!UICONTROL Private]** option is selected from the drop-down list, as indicated in the visibility condition:

![](assets/s_ncs_admin_survey_add_a_condition.png)

Wenn der Benutzer ein Personenfahrzeug auswählt, bietet das Webformular folgende Optionen an:

![](assets/s_ncs_admin_survey_no_storage_conda.png)

Der Container mit Daten zu Nutzfahrzeugen wird dann angezeigt, wenn die Nutzfahrzeugoption (wie in der Sichtbarkeitsbedingung dargestellt) ausgewählt wird:

![](assets/s_ncs_admin_survey_view_a_condition.png)

Wenn der Benutzer ein Nutzfahrzeug auswählt, bietet das Webformular folgende Optionen an:

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## Erfasste Informationen verwenden {#using-collected-information}

Für jedes Formular können die bereitgestellten Antworten in Feldern oder Titeln wiederverwendet werden. Dabei müssen die folgenden Syntaxen verwendet werden:

* Für Inhalte, die in einem Datenbankfeld gespeichert werden:

   ```
   <%=ctx.recipient.@field name%
   ```

* Für Inhalte, die in einer lokalen Variablen gespeichert werden:

   ```
   <%= ctx.vars.variable name %
   ```

* Für Inhalte, die in einem HTML-Textfeld gespeichert werden:

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >Unlike the other fields for which `<%=` characters are replaced with escape characters, the HTML content is saved as is by using the `<%==` syntax.

## Webformulare-Antworten speichern {#saving-web-forms-answers}

Um die in Formularseiten erfassten Informationen zu speichern, müssen Sie in das Diagramm die Komponente &quot;Speicherung&quot; einfügen.

![](assets/s_ncs_admin_survey_save_box.png)

Sie haben zwei Möglichkeiten, diese Komponente zu verwenden:

* Wenn der Zugriff auf das Webformular über einen per E-Mail gesendeten Link erfolgt und der Benutzer, der auf die Anwendung zugreift, sich bereits in der Datenbank befindet, können Sie die **[!UICONTROL Update the preloaded record]** Option aktivieren. Weitere Informationen hierzu finden Sie unter [Senden eines Formulars per E-Mail](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).

   In diesem Fall verwendet Adobe Campaign den verschlüsselten Primärschlüssel des Benutzerprofils, einen eindeutigen Bezeichner, der jedem Profil von Adobe Campaign zugewiesen wird. Sie müssen die Informationen so konfigurieren, dass sie über das Feld für das Vorausladen vorgeladen werden. Weitere Informationen finden Sie unter [Vorladen der Formulardaten](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   >[!CAUTION]
   >
   >Mit dieser Option werden die Benutzerdaten, einschließlich der E-Mail-Adresse, überschrieben, wenn ein Feld vorhanden ist, über das eine neue Eingabe getätigt werden kann. Diese Option kann nicht zur Erstellung neuer Profile verwendet werden und erfordert eine Vorausfüllen-Komponente im Formular.

* Um Empfängerdaten in der Datenbank anzureichern, bearbeiten Sie die Komponente &quot;Speicherung&quot; und wählen Sie den Abstimmschlüssel aus. Wählen Sie die Abstimmfelder für die interne Verwendung (normalerweise für das Intranet) oder für ein Formular zum Erstellen neuer Profile aus. In der Komponente sind alle Datenbankfelder vorhanden, die auf den Seiten der Webanwendung verwendet werden:

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

Standardmäßig werden die Daten durch einen **[!UICONTROL Update or insertion]** Vorgang in die Datenbank importiert: Wenn es in der Datenbank vorhanden ist, wird das Element aktualisiert (z. B. der ausgewählte Newsletter oder die eingegebene E-Mail-Adresse). Wenn sie nicht vorhanden ist, werden die Informationen hinzugefügt.

Sie können dieses Verhalten jedoch auch verändern. Wählen Sie dazu die Wurzel des Elements aus und danach aus der Dropdown-Liste den auszuführenden Vorgang.

![](assets/s_ncs_admin_survey_save_operation.png)

Sie können für die Abstimmung einen Suchordner und für neue Profile den Erstellungsordner auswählen. Wenn diese Felder leer sind, wird nach den Profilen gesucht und diese werden im Standardordner des jeweiligen Operators erstellt.

>[!NOTE]
>
>Mögliche Vorgänge sind: **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>Der Standardordner des Operators entspricht dem ersten Ordner, für den er Schreibzugriff hat.\
>Siehe [diesen Abschnitt](../../platform/using/access-management.md).

