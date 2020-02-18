---
title: Eigenschaften eines Webformulars definieren
seo-title: Eigenschaften eines Webformulars definieren
description: Eigenschaften eines Webformulars definieren
seo-description: null
page-status-flag: never-activated
uuid: 2fb0952a-5f73-48f5-b344-e3247cefca62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 36953eb5-3296-4796-9352-945121bbdc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7a0d82dfc6dc50026214d7d3b1094d45ffadbc03

---


# Eigenschaften eines Webformulars definieren{#defining-web-forms-properties}

Webformulare können vollständig konfiguriert und entsprechend Ihren Anforderungen angepasst werden. Geben Sie dazu im Eigenschaftenfenster die entsprechenden Parameter ein.

Auf das Eigenschaftenfenster kann über die **[!UICONTROL Properties]** Schaltfläche in der Symbolleiste des Webformulars zugegriffen werden. In diesem Fenster können Sie auf einen bestimmten Bereich von Einstellungen für das Webformular zugreifen. Einige Einstellungen stammen möglicherweise aus der Vorlagenkonfiguration.

![](assets/s_ncs_admin_survey_properties_general.png)

## Allgemeine Formulareigenschaften {#overall-form-properties}

Auf der **[!UICONTROL General]** Registerkarte des Eigenschaftenfensters können Sie die **Beschriftung** des Formulars ändern. Es wird dringend empfohlen, den **internen Namen** nicht zu ändern.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

Die Formularvorlage wird während der Formularerstellung ausgewählt. Sie kann nicht später geändert werden. Weitere Informationen zum Erstellen und Verwalten von Formularvorlagen finden Sie unter [Verwenden einer Webformularvorlage](../../web/using/using-a-web-form-template.md).

## Formulardaten speichern {#form-data-storage}

Die Felder von Webformularen werden standardmäßig in der Empfängertabelle gespeichert. Sie können die Tabelle ändern, indem Sie eine neue Tabelle im **[!UICONTROL Document type]** Feld auswählen. Mit dem **[!UICONTROL Zoom]** Symbol können Sie den Inhalt der ausgewählten Tabelle anzeigen.

Antworten werden standardmäßig in der **[!UICONTROL Answer to a recipient form]** Tabelle gespeichert.

## Fehlerseite einrichten {#setting-up-an-error-page}

Sie können eine Fehlerseite konfigurieren, die im Fall von Fehlern bei der Verwendung eines Formulars angezeigt wird.

Eine Fehlerseite wird im entsprechenden Tab des Fensters mit den Formulareigenschaften definiert.

Standardmäßig enthält sie die folgenden Informationen:

![](assets/s_ncs_admin_survey_default_error_page.png)

Der Inhalt der angezeigten Zeichenfolgen wird auf der **[!UICONTROL Error page]** Registerkarte des Eigenschaftenfensters definiert. Auf der **[!UICONTROL HTML]** Registerkarte wird das Rendering angezeigt. Auf der **[!UICONTROL Texts]** Registerkarte können Sie die Textzeichenfolgen ändern und bei Bedarf Text hinzufügen:

![](assets/s_ncs_admin_survey_error_page.png)

## Lokalisierung eines Formulars {#form-localization}

The **[!UICONTROL Localization]** tab lets you select the design and display languages for the Web form.

See [Translating a web form](../../web/using/translating-a-web-form.md).

## Navigation und Rendering im Formular {#form-browsing-and-rendering}

Im Tab **[!UICONTROL Rendering]** können Sie definieren, wie die Navigation zwischen den Seiten des Webformulars erfolgen und welche Rendering-Vorlage verwendet werden soll.

Sie können zwischen der Navigation per Link oder Schaltfläche wählen.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Standardmäßig sind Schaltflächen als Navigationselemente ausgewählt. Sie können damit folgende Aktionen ausführen:

* Approve the current page and display the next page by clicking **[!UICONTROL Next]**. This button is displayed on all pages except the last.
* Display the previous page by clicking **[!UICONTROL Previous]**. This button is displayed on all pages except the first.
* Speichern Sie die Antworten des Formulars, indem Sie auf die **[!UICONTROL Approve]** Schaltfläche klicken. Diese Schaltfläche wird nur auf der letzten Seite angezeigt.

Diese Elemente befinden sich am unteren Rand einer jeden Seite. Ihre Position kann durch die Bearbeitung des Stylesheets geändert werden.

>[!NOTE]
>
>Es ist möglich, die **[!UICONTROL Previous]** Schaltfläche auf einigen Seiten auszublenden. Gehen Sie dazu zur entsprechenden Seite und aktivieren Sie die **[!UICONTROL Disallow returning to the previous page]** Option. Diese Option ist verfügbar, wenn die Stamm-Node der Seitenstruktur ausgewählt ist.

The **[!UICONTROL Template]** field of the **[!UICONTROL Rendering]** tab lets you select a theme from those available.

Designs werden im **[!UICONTROL Administration>Configuration>Form rendering]** Knoten des Baums gespeichert. See [Selecting the form rendering template](../../web/using/form-rendering.md#selecting-the-form-rendering-template)

Im unteren Bereich des Eigenschaftenfensters wird eine Beispielwiedergabe angezeigt. Mit dem **[!UICONTROL Edit link]** Symbol können Sie die Konfiguration für das ausgewählte Design anzeigen.

![](assets/s_ncs_admin_survey_properties_render.png)

## Texte im Formular {#texts-in-the-form}

The **[!UICONTROL Page]** tab lets you define the content of the form header and footer. See [Defining headers and footers](../../web/using/form-rendering.md#defining-headers-and-footers).

Sie können damit auch Übersetzungen verwalten. See [Translating a web form](../../web/using/translating-a-web-form.md).

## Zugriff auf das Formular {#accessibility-of-the-form}

Ein Webformular ist für Benutzer verfügbar, wenn das aktuelle Datum innerhalb der Gültigkeitsdauer **[!UICONTROL Online]** liegt. Der Status des Formulars wird während der Veröffentlichung geändert (siehe [Veröffentlichen eines Formulars](../../web/using/publishing-a-web-form.md#publishing-a-form)). Der Status wird auf der Registerkarte des Eigenschaftenfensters im Abschnitt **Projekt** **[!UICONTROL General]** angezeigt.

Die Gültigkeitsdauer reicht vom **[!UICONTROL Start]** Datum bis zum **[!UICONTROL End date]**. Wenn in diesen Feldern keine Daten angegeben sind, ist das Formular dauerhaft gültig.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>If the form is closed, and therefore its validity period has not been reached or has expired, or if it was closed by the Adobe Campaign operator, a message is displayed when the user attempts to access it. You can personalize this message by clicking **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## Zugriffskontrolle auf Formulare {#form-access-control}

Standardmäßig kann der Zugriff auf Webformulare anonym erfolgen: Allen Operatoren, die auf das Formular zugreifen, werden WEBAPP-Operatorrechte erteilt.

Sie können die Zugriffssteuerung für die Anzeige des Formulars aktivieren, z. B. bei der Bereitstellung eines Formulars auf einer Intranet-Site, um Benutzer zu authentifizieren. Zeigen Sie dazu das **[!UICONTROL Properties]** Fenster des betreffenden Formulars an und klicken Sie auf die **[!UICONTROL Enable access control]** Option, wie unten dargestellt:

![](assets/s_ncs_admin_survey_access_ctrl.png)

Beim Zugriff auf die Seite erscheint das folgende Authentifizierungsformular:

![](assets/s_ncs_admin_survey_access_login.png)

Der Benutzername und das Passwort entspricht denen der Adobe Campaign-Operatoren. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt ](../../platform/using/access-management.md).

Mit der **[!UICONTROL Use a specific account]** Option können Sie die Lese- und Schreibberechtigung des Operators einschränken, der auf das Formular zugreift. Verwenden Sie das Dropdownfeld, um einen Operator oder eine Gruppe von Operatoren auszuwählen, die für die Erteilung dieser Berechtigungen zuständig sind.

![](assets/s_ncs_admin_survey_access_op_select.png)

## Parameter der Formular-URL {#form-url-parameters}

Sie können zur URL eines Formulars zusätzliche Parameter hinzufügen, um seinen Inhalt anzupassen und einen Kontext zu initialisieren (Sprache, verschlüsselte Empfänger-ID, Unternehmen, berechnete, in einer Variablen gespeicherte Formel etc.). Dadurch können Sie über mehrere URLs Zugriff auf ein Formular gewähren und den Seiteninhalt auf der Basis des in der URL angegebenen Parameterwerts anpassen.

Standardmäßig bietet Adobe Campaign Parameter für die Vorschau des Formulars und die Fehlerprüfung. Sie können neue, mit dem Formular verknüpfte Einstellungen definieren, die die Werte eines Datenbankfelds oder einer lokalen Variablen verwenden können.

## Standardparameter {#standard-parameters}

Standardmäßig sind die folgenden Parameter verfügbar:

* **id** zur Darstellung der verschlüsselten Kennung
* **lang** zur Änderung der Anzeigesprache
* **origin** zur Spezifizierung der Herkunft des reagierenden Kontakts
* **_uuid** aktiviert die Formularansicht vor der Veröffentlichung und die Fehlerverfolgung. Dieser Parameter dient internen Zwecken (Erstellung und Debugging): Wenn Sie über diese URL auf das Webformular zugreifen, werden die erstellten Datensätze bei der Verfolgung (in Berichten) nicht berücksichtigt. Der Ursprung wird zum **[!UICONTROL Adobe Campaign]** Wert gezwungen.

   Dieser Parameter wird gemeinsam mit den **_preview**-Parametern und/oder **_debug**: verwendet:

   **_preview** zur Anzeige der zuletzt gespeicherten Version. Dieser Parameter darf nur in der Testphase verwendet werden.

   **_debug** zur Anzeige der Spur der eingegebenen oder auf den Formularseiten berechneten Daten. Damit können zusätzliche Informationen zu Fehlern erfasst werden, einschließlich jenen nach der Publikation des Formulars.

   >[!CAUTION]
   >
   >When the form is displayed via a URL with the **_uuid** parameter, the value of the **[!UICONTROL origin]** parameter is forced to **Adobe Campaign**.

## Parameter hinzufügen {#adding-parameters}

Parameter können über die **[!UICONTROL Parameters...]** Registerkarte im Fenster Eigenschaften des Formulars hinzugefügt werden. Sie können wie unten gezeigt obligatorisch gemacht werden:

![](assets/s_ncs_admin_survey_properties_param.png)

Sie müssen einen Speicherort angeben, aus dem der Wert des Parameters abgerufen wird. Wählen Sie dazu eine der Speicheroptionen aus und klicken Sie dann auf die **[!UICONTROL Storage]** Registerkarte, um das Feld oder die Variable auszuwählen. Die Speicheroptionen sind in den [Antwortspeicherfeldern](../../web/using/web-forms-answers.md#response-storage-fields)ausführlich beschrieben.

Der Status des reagierenden Kontakts (0, 1 oder ein beliebiger anderer Wert) kann dann entsprechend dem Formularzugriff zur URL hinzugefügt werden. Diese Information kann auf den Formularseiten oder in einer Text-Box wiederverwendet werden. Die Anzeige von Seiten kann wie unten gezeigt von einem kontextuellen Wert abhängig gemacht werden:

1. Startseite für Kunden (**Status = 1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. Startseite für Interessenten (**Status = 0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. Startseite für andere Profile (z. B. **Status = 12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

Erstellen Sie zur Konfiguration dieses Formulars eine Test-Komponente und platzieren Sie sie wie unten gezeigt an den Anfang des Diagramms:

![](assets/s_ncs_admin_survey_test.png)

Über die Test-Komponente können Sie die Bedingungen der Seitenreihenfolge konfigurieren:

![](assets/s_ncs_admin_survey_test_box.png)

