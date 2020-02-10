---
title: Webformular publizieren
seo-title: Webformular publizieren
description: Webformular publizieren
seo-description: null
page-status-flag: never-activated
uuid: 37222829-1d56-438c-a4ca-878925debcb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: f4322902-c72d-4443-9c30-09add4c615a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Webformular publizieren{#publishing-a-web-form}

## Formulardaten vorausfüllen {#pre-loading-the-form-data}

Wenn Sie die in der Datenbank gespeicherten Profile mithilfe eines Webformulars aktualisieren möchten, können Sie eine Vorausfüllen-Komponente verwenden. Über diese Komponente können Sie angeben, wie der in der Datenbank zu aktualisierende Datensatz gefunden werden soll.

Folgende Identifizierungsmöglichkeiten gibt es:

* **[!UICONTROL Adobe Campaign Encryption]**

   Diese Verschlüsselungsmethode verwendet die verschlüsselte Adobe Campaign-Kennung (ID). Diese Methode ist nur für Adobe Campaign-Objekte möglich. Die verschlüsselte Kennung darf außerdem nur von der Adobe Campaign-Plattform generiert werden.

   When using this method, you need to adapt the URL of the form to deliver to the email address by adding the **`<%=escapeUrl(recipient.cryptedId) %>`** parameter. Weitere Informationen hierzu finden Sie unter [Senden eines Formulars per E-Mail](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   Diese Verschlüsselungsmethode verwendet eine ID (ID), die extern bereitgestellt wird und mit einem Schlüssel verknüpft ist, der von Adobe Campaign und dem externen Anbieter gemeinsam verwendet wird. Im **[!UICONTROL Des key]** Feld können Sie diesen Verschlüsselungsschlüssel eingeben.

* **[!UICONTROL List of fields]**

   Mit dieser Option können Sie aus den im aktuellen Kontext des Formulars bereitgestellten Feldern auswählen. Anhand dieser Felder wird das entsprechende Profil in der Datenbank gesucht.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   Felder können den Formulareigenschaften über die **[!UICONTROL Parameters]** Registerkarte hinzugefügt werden (siehe [Parameter](../../web/using/defining-web-forms-properties.md#adding-parameters)hinzufügen). Sie werden in der Formular-URL oder in den Eingabebereichen platziert.

   >[!CAUTION]
   >
   >Die Daten in den ausgewählten Feldern werden nicht verschlüsselt. Es darf nicht in einem verschlüsselten Formular bereitgestellt werden, da Adobe Campaign es nicht entschlüsseln kann, wenn die **[!UICONTROL Field list]** Option aktiviert ist.

   Im folgenden Beispiel wird das Vorausfüllen des Profils auf Basis der E-Mail-Adresse durchgeführt.

   In der URL kann die unverschlüsselte E-Mail-Adresse enthalten sein. In diesem Fall haben Benutzer direkten Zugriff auf Seiten.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   Ansonsten werden sie nach ihrem Passwort gefragt.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >Wenn mehrere Felder in der Liste spezifiziert sind, müssen die Daten **ALLER FELDER** mit den in der Datenbank gespeicherten Daten übereinstimmen, damit das Profil aktualisiert wird. Ansonsten wird ein neues Profil erstellt.
   > 
   >Diese Funktion ist besonders nützlich für Webanwendungen, aber nicht empfohlen für öffentliche Formulare. Als Zugriffskontrolloption muss &quot;Zugriffskontrolle aktivieren&quot; ausgewählt werden.

Die **[!UICONTROL Skip preloading if identification is empty]** Option muss aktiviert sein, wenn Sie keine Profile aktualisieren möchten. In diesem Fall wird jedes eingegebene Profil nach Genehmigung des Formulars der Datenbank hinzugefügt. Diese Option wird beispielsweise verwendet, wenn das Formular auf einer Website veröffentlicht wird.

Mit dieser **[!UICONTROL Auto-load data referenced in the form]** Option können Sie die Daten, die mit Eingabe- und Zusammenführungsfeldern im Formular übereinstimmen, automatisch im Voraus laden. Daten, auf die in **[!UICONTROL Script]** und **[!UICONTROL Test]** Aktivitäten verwiesen wird, sind jedoch nicht betroffen. Wenn diese Option nicht ausgewählt ist, müssen Sie die Felder mit der **[!UICONTROL Load additional data]** Option definieren.

The **[!UICONTROL Load additional data]** option lets you add information which is not used in the pages of the form, but will nonetheless be preloaded.

So können Sie beispielsweise das Geschlecht des Empfängers vorausfüllen und ihn über eine Test-Komponente automatisch zur entsprechenden Seite weiterleiten.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Versand und Tracking von Webformularen verwalten {#managing-web-forms-delivery-and-tracking}

Nachdem ein Formular erstellt, konfiguriert und veröffentlicht wurde, können Sie es bereitstellen und die Benutzerantworten tracken.

### Lebenszyklus eines Formulars {#life-cycle-of-a-form}

Der Lebenszyklus eines Formulars besteht aus drei Phasen:

1. **Das Formular wird bearbeitet**

   Dies ist die erste Entwurfsphase. Wenn ein neues Formular erstellt wird, befindet es sich in der Bearbeitungsphase. Für den Zugriff auf das Formular, nur zu Testzwecken, muss der Parameter dann in der URL verwendet **[!UICONTROL __uuid]** werden. Auf diese URL kann auf der **[!UICONTROL Preview]** Unterregisterkarte zugegriffen werden. Siehe Parameter für die [Formular-URL](../../web/using/defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Der Zugriff auf das Formular erfolgt in der gesamten Bearbeitungsphase über diese spezielle URL.

1. **Das Formular ist online**

   Nach Abschluss der Entwurfsphase kann das Formular ausgeliefert werden. Erstens muss sie veröffentlicht werden. Weitere Informationen finden Sie unter [Veröffentlichen eines Formulars](#publishing-a-form).

   Das Formular ist so lange **[!UICONTROL Live]**, bis seine Gültigkeit erlischt.

   >[!CAUTION]
   >
   >To be delivered, the URL of the survey must not contain the **[!UICONTROL __uuid]** parameter.

1. **Das Formular ist nicht verfügbar**

   Wenn die Bereitstellungsphase vorüber ist, ist das Formular geschlossen und nicht mehr verfügbar. Benutzer können dann nicht mehr darauf zugreifen.

   Das Ablaufdatum kann im Fenster &quot;Formulareigenschaften&quot;definiert werden. Weitere Informationen finden Sie unter [Bereitstellen eines Formulars online](#making-a-form-available-online)

Der Publikationsstatus eines Formulars wird in der Formularliste angezeigt.

![](assets/s_ncs_admin_survey_status.png)

### Formular publizieren {#publishing-a-form}

Um den Status eines Formulars zu ändern, müssen Sie es veröffentlichen. Klicken Sie dazu auf die **[!UICONTROL Publication]** Schaltfläche über der Liste der Webformulare und wählen Sie den Status in der Dropdown-Liste aus.

![](assets/webapp_publish_webform.png)

### Formular online verfügbar machen {#making-a-form-available-online}

Damit der Benutzer darauf zugreifen kann, muss das Formular in Produktion sein und innerhalb der Gültigkeitsdauer gestartet werden. Die Gültigkeitsdaten werden über den **[!UICONTROL Properties]** Link des Formulars eingegeben.

* Use the fields in the **[!UICONTROL Project]** section to enter start and end dates for the form.

   ![](assets/webapp_availability_date.png)

* Klicken Sie auf den **[!UICONTROL Personalize the message displayed if the form is closed...]** Link, um die Fehlermeldung zu definieren, die angezeigt werden soll, wenn der Benutzer versucht, auf das Formular zuzugreifen, während es nicht gültig ist.

   See [Accessibility of the form](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form).

### Formular per E-Mail versenden {#delivering-a-form-via-email}

Wenn Sie eine Einladung per E-Mail senden, können Sie die **[!UICONTROL Adobe Campaign Encryption]** Option für die Datenabstimmung verwenden. Gehen Sie dazu zum Auslieferungsassistenten und passen Sie den Link zum Formular an, indem Sie den folgenden Parameter hinzufügen:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

In diesem Fall muss der Abgleichschlüssel für die Datenspeicherung der verschlüsselte Identifikator des Empfängers sein. Weitere Informationen finden Sie unter [Vorladen der Formulardaten](#pre-loading-the-form-data).

In diesem Fall müssen Sie die **[!UICONTROL Update the preloaded record]** Option im Feld &quot;Datensatz&quot;aktivieren. Weitere Informationen finden Sie unter [Speichern von Webformularantworten](../../web/using/web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Log responses {#log-responses}

Die Rückverfolgung von Antworten kann auf einer speziellen Registerkarte aktiviert werden, um die Auswirkungen Ihres Webformulars zu überwachen. Klicken Sie dazu auf den **[!UICONTROL Advanced parameters...]** Link im Fenster &quot;Formulareigenschaften&quot;und wählen Sie die **[!UICONTROL Log responses]** Option aus.

![](assets/s_ncs_admin_survey_trace.png)

The **[!UICONTROL Responses]** tab appears to let you view the identity of respondents.

![](assets/s_ncs_admin_survey_trace_tab.png)

Select a recipient and click the **[!UICONTROL Detail...]** button to view the responses provided.

![](assets/s_ncs_admin_survey_trace_edit.png)

Sie können die Antwortprotokolle zu den Fragen verwenden, um beispielsweise Erinnerungen nur an Kontakte zu senden, die nicht geantwortet haben, oder um reagierenden Kontakten spezielle Nachrichten zukommen zu lassen.

>[!NOTE]
>
>Für ein vollständiges Tracking der bereitgestellten Antworten exportieren Sie die Antworten und erstellen Sie spezielle Berichte. Verwenden Sie dazu das optionale **Umfragemodul**. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../web/using/about-surveys.md).

