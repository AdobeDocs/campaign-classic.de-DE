---
product: campaign
title: Definieren der Eigenschaften von Web-Formularen
description: Definieren der Eigenschaften von Web-Formularen
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 71%

---

# Definieren der Eigenschaften von Web-Formularen{#defining-web-forms-properties}



Sie können Web-Formulare vollständig Ihren Anforderungen entsprechend konfigurieren und personalisieren. Die Parameter müssen im Eigenschaftenfenster eingegeben werden.

Auf das Eigenschaftenfenster können Sie über die Schaltfläche **[!UICONTROL Eigenschaften]** in der Symbolleiste des Web-Formulars zugreifen. Über dieses Fenster haben Sie Zugriff auf die Eigenschaften des Web-Formulars. Einige Einstellungen stammen möglicherweise aus der Konfiguration der Vorlage.

![](assets/s_ncs_admin_survey_properties_general.png)

## Allgemeine Formulareigenschaften {#overall-form-properties}

Im **[!UICONTROL Allgemein]** im Eigenschaftenfenster können Sie die **Titel** des Formulars. Es wird dringend empfohlen, die **Interner Name**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

Die Formularvorlage wird bei der Formularerstellung ausgewählt. Sie kann später nicht mehr geändert werden. Weitere Informationen zum Erstellen und Verwalten von Formularvorlagen finden Sie unter [Webformularvorlage verwenden](using-a-web-form-template.md).

## Formulardaten speichern {#form-data-storage}

Die Felder der Webformulare werden standardmäßig in der Empfängertabelle gespeichert. Sie können die verwendete Tabelle ändern, indem Sie eine neue Tabelle im **[!UICONTROL Dokumenttyp]** -Feld. Die **[!UICONTROL Zoom]** -Symbol zeigt den Inhalt der ausgewählten Tabelle an.

Standardmäßig werden die Antworten in der Tabelle **Antworten auf ein Formular** gespeichert.

## Fehlerseite einrichten {#setting-up-an-error-page}

Sie können eine Fehlerseite konfigurieren, die im Fall von Fehlern bei der Verwendung eines Formulars angezeigt wird.

Eine Fehlerseite wird im entsprechenden Tab des Fensters mit den Formulareigenschaften definiert.

Standardmäßig enthält sie die folgenden Informationen:

![](assets/s_ncs_admin_survey_default_error_page.png)

Der Inhalt der angezeigten Strings wird im Abschnitt **[!UICONTROL Fehlerseite]** im Eigenschaftenfenster. Die **[!UICONTROL HTML]** -Tab zeigt das Rendering und die **[!UICONTROL Texte]** -Tab können Sie die Textzeichenfolgen ändern und bei Bedarf Text hinzufügen:

![](assets/s_ncs_admin_survey_error_page.png)

## Lokalisierung eines Formulars {#form-localization}

Im Tab **[!UICONTROL Lokalisierung]** können Sie das Design und die Anzeigesprachen für das Webformular auswählen.

Siehe [Webformular übersetzen](translating-a-web-form.md).

## Navigation und Rendering im Formular {#form-browsing-and-rendering}

Im Tab **[!UICONTROL Rendering]** können Sie definieren, wie die Navigation zwischen den Seiten des Webformulars erfolgen und welche Rendering-Vorlage verwendet werden soll.

Sie können zwischen der Navigation per Link oder Schaltfläche wählen.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Standardmäßig sind Schaltflächen als Navigationselemente ausgewählt. Sie können damit folgende Aktionen ausführen:

* Die aktuelle Seite validieren und durch Auswahl von **[!UICONTROL Weiter]** die nächste Seite anzeigen. Diese Schaltfläche wird auf allen Seiten außer der letzten angezeigt.
* Durch Auswahl von **[!UICONTROL Zurück]** die vorherige Seite anzeigen. Diese Schaltfläche wird auf allen Seiten außer der ersten angezeigt.
* Die Formularantworten durch Auswahl der Schaltfläche **[!UICONTROL Validieren]** speichern. Diese Schaltfläche wird nur auf der letzten Seite angezeigt.

Diese Elemente befinden sich am unteren Rand einer jeden Seite. Ihre Position kann durch die Bearbeitung des Stylesheets geändert werden.

>[!NOTE]
>
>Die **[!UICONTROL Vorherige]** auf einigen Seiten. Gehen Sie dazu zur entsprechenden Seite und überprüfen Sie die **[!UICONTROL Rückkehr zur vorherigen Seite nicht zulassen]** -Option. Diese Option ist verfügbar, wenn der Stamm des Seitenbaums ausgewählt ist.

Das Feld **[!UICONTROL Vorlage]** des Tabs **[!UICONTROL Rendering]** ermöglicht die Auswahl eines Themas.

Themen werden im Knoten **[!UICONTROL Administration > Konfiguration > Formular-Rendering]** des Baums gespeichert. Siehe [Vorlage zum Formular-Rendering auswählen](form-rendering.md#selecting-the-form-rendering-template).

Im unteren Teil des Eigenschaftenfensters wird ein Beispiel für das Rendering angezeigt. Die **[!UICONTROL Link bearbeiten]** -Symbol zeigt die Konfiguration für das ausgewählte Thema an.

![](assets/s_ncs_admin_survey_properties_render.png)

## Texte im Formular {#texts-in-the-form}

Im Tab **[!UICONTROL Seite]** können Sie den Inhalt des Formularkopfs und -fußes definieren. Siehe [Header und Footer definieren](form-rendering.md#defining-headers-and-footers).

Dort können Sie auch Übersetzungen verwalten. Siehe [Webformular übersetzen](translating-a-web-form.md).

## Zugriff auf das Formular {#accessibility-of-the-form}

Ein Webformular ist für Benutzer verfügbar, wenn es **[!UICONTROL online]** ist und das aktuelle Datum innerhalb der Gültigkeitsdauer liegt. Der Status des Formulars ändert sich in der Veröffentlichungsphase (siehe [Formular veröffentlichen](publishing-a-web-form.md#publishing-a-form)). Der Status wird im Bereich **Projekt** im Tab **[!UICONTROL Allgemein]** des Eigenschaftenfensters angezeigt.

Der Gültigkeitszeitraum erstreckt sich vom **[!UICONTROL Startdatum]** bis zum **[!UICONTROL Enddatum]**. Wenn keine Daten in diesen Feldern eingetragen sind, hat das Formular permanente Gültigkeit.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>Wenn das Formular geschlossen wird und sein Gültigkeitszeitraum daher nicht erreicht oder abgelaufen ist oder der Adobe Campaign-Benutzer es geschlossen hat, wird eine Meldung angezeigt, wenn der Benutzer versucht, auf das Formular zuzugreifen. Sie können diese Nachricht personalisieren, indem Sie auf **[!UICONTROL Nachricht personalisieren, die angezeigt wird, wenn das Formular geschlossen wird..]**.

## Zugriffskontrolle auf Formulare {#form-access-control}

Standardmäßig kann der Zugriff auf Webformulare anonym erfolgen: Allen Operatoren, die auf das Formular zugreifen, werden WEBAPP-Operatorrechte erteilt.

Sie können die Zugriffskontrolle für die Anzeige des Formulars aktivieren, um Benutzer zu authentifizieren, z. B. wenn Sie ein Formular auf einer Intranet-Site bereitstellen. Zeigen Sie dazu die **[!UICONTROL Eigenschaften]** Fenster des betroffenen Formulars und klicken Sie auf **[!UICONTROL Zugriffskontrolle aktivieren]** wie unten gezeigt:

![](assets/s_ncs_admin_survey_access_ctrl.png)

Beim Zugriff auf die Seite erscheint das folgende Authentifizierungsformular:

![](assets/s_ncs_admin_survey_access_login.png)

Die Anmeldung und das Kennwort werden von Adobe Campaign-Benutzern verwendet. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/access-management.md).

Mit der Option **[!UICONTROL Spezifisches Konto nutzen]** können Sie die Lese- oder Schreibrechte eines Operators einschränken, der auf das Formular zugreift. Wählen Sie in der Dropdown-Liste einen Operator oder eine Operatorgruppe aus, die für die Vergabe dieser Rechte zuständig sein sollen.

![](assets/s_ncs_admin_survey_access_op_select.png)

## Parameter der Formular-URL {#form-url-parameters}

Sie können zur URL eines Formulars zusätzliche Parameter hinzufügen, um seinen Inhalt anzupassen und einen Kontext zu initialisieren (Sprache, verschlüsselte Empfänger-ID, Unternehmen, berechnete, in einer Variablen gespeicherte Formel etc.). Dadurch können Sie über mehrere URLs Zugriff auf ein Formular gewähren und den Seiteninhalt auf der Basis des in der URL angegebenen Parameterwerts anpassen.

Standardmäßig bietet Adobe Campaign Parameter für die Vorschau des Formulars und die Fehlerprüfung. Sie können neue, mit dem Formular verknüpfte Einstellungen definieren, die die Werte eines Datenbankfelds oder einer lokalen Variablen verwenden können.

## Standardparameter {#standard-parameters}

Standardmäßig sind die folgenden Parameter verfügbar:

* **id** zur Darstellung der verschlüsselten Kennung
* **lang** zur Änderung der Anzeigesprache
* **origin** zur Spezifizierung der Herkunft des reagierenden Kontakts
* **_uuid** ermöglicht die Anzeige von Formularen vor der Veröffentlichung und die Fehlerverfolgung. Dieser Parameter ist für die interne Verwendung vorgesehen (Erstellung und Debugging): Wenn Sie über diese URL auf das Webformular zugreifen, werden die erstellten Datensätze beim Tracking (in Berichten) nicht berücksichtigt. Der Ursprung muss **[!UICONTROL Adobe Campaign]** -Wert.

  Dieser Parameter wird gemeinsam mit den Parametern **_preview** und/oder **_debug** verwendet:

  **_preview** zur Anzeige der zuletzt gespeicherten Version. Dieser Parameter darf nur in der Testphase verwendet werden.

  **_debug** zur Anzeige der Spur der eingegebenen oder auf den Formularseiten berechneten Daten. Damit können zusätzliche Informationen zu Fehlern erfasst werden, einschließlich jenen nach der Veröffentlichung des Formulars.

  >[!CAUTION]
  >
  >Wenn das Formular über eine URL mit dem Parameter **_uuid** aufgerufen wird, wird im Parameterwert **[!UICONTROL Herkunft]** immer **Adobe Campaign** angezeigt.

## Parameter hinzufügen {#adding-parameters}

Parameter können im Eigenschaftenfenster des Formulars über den Tab **[!UICONTROL Parameter...]** hinzugefügt werden. Sie können wie unten gezeigt als obligatorisch festgelegt werden:

![](assets/s_ncs_admin_survey_properties_param.png)

Sie müssen einen Speicherort angeben, von dem der Wert des Parameters abgerufen wird. Wählen Sie dazu eine der Speicheroptionen aus und klicken Sie auf die Schaltfläche **[!UICONTROL Speicherung]** zur Auswahl des entsprechenden Felds oder der betreffenden Variablen. Die Speicheroptionen werden in den [Speicherfeldern für Antworten](web-forms-answers.md#response-storage-fields) ausführlich beschrieben.

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
