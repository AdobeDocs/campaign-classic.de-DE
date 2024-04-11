---
product: campaign
title: Veröffentlichen eines Web-Formulars
description: Veröffentlichen eines Web-Formulars
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 51%

---

# Veröffentlichen eines Web-Formulars{#publishing-a-web-form}



## Formulardaten vorausfüllen {#pre-loading-the-form-data}

Wenn Sie die in der Datenbank gespeicherten Profile mithilfe eines Webformulars aktualisieren möchten, können Sie eine Vorausfüllen-Komponente verwenden. Über diese Komponente können Sie angeben, wie der in der Datenbank zu aktualisierende Datensatz gefunden werden soll.

Folgende Identifizierungsmöglichkeiten gibt es:

* **[!UICONTROL Adobe Campaign-Verschlüsselung]**

  Diese Verschlüsselungsmethode verwendet die verschlüsselte Adobe Campaign-Kennung (ID). Diese Methode ist nur für Adobe Campaign-Objekte möglich. Die verschlüsselte Kennung darf außerdem nur von der Adobe Campaign-Plattform generiert werden.

  Wenn Sie diese Methode verwenden, müssen Sie die URL des Formulars anpassen, das an die E-Mail-Adresse gesendet wird. Fügen Sie zu diesem Zweck den Parameter **`<%=escapeUrl(recipient.cryptedId) %>`** hinzu. Weitere Informationen hierzu finden Sie unter [Formular per E-Mail versenden](#delivering-a-form-via-email).

* **[!UICONTROL DES-Verschlüsselung]**

  ![](assets/s_ncs_admin_survey_preload_methods_001.png)

  Diese Verschlüsselungsmethode verwendet eine extern bereitgestellte Kennung (ID), die mit einem Schlüssel verknüpft ist, der von Adobe Campaign und dem externen Anbieter gemeinsam verwendet wird. Die **[!UICONTROL DES-Schlüssel]** ermöglicht die Eingabe des Verschlüsselungsschlüssels.

* **[!UICONTROL Feldliste]**

  Mit dieser Option können Sie aus den im aktuellen Kontext des Formulars bereitgestellten Feldern auswählen. Anhand dieser Felder wird das entsprechende Profil in der Datenbank gesucht.

  ![](assets/s_ncs_admin_survey_preload_methods_002.png)

  Felder können den Formulareigenschaften über den Tab **[!UICONTROL Parameter]** hinzugefügt werden (siehe [Parameter hinzufügen](defining-web-forms-properties.md#adding-parameters)). Sie werden in der Formular-URL oder den Eingabefeldern platziert.

  >[!CAUTION]
  >
  >Die Daten in den ausgewählten Feldern werden nicht verschlüsselt. Sie darf nicht in verschlüsselter Form bereitgestellt werden, da Adobe Campaign sie nicht entschlüsseln kann, wenn die **[!UICONTROL Feldliste]** ausgewählt ist.

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

Wenn Sie keine Profile aktualisieren möchten, muss die Option **[!UICONTROL Bei nicht angegebener Identifizierung vorausgefüllte Informationen ignorieren]** ausgewählt werden. In diesem Fall wird jedes eingegebene Profil nach Genehmigung des Formulars der Datenbank hinzugefügt. Diese Option wird beispielsweise verwendet, wenn das Formular auf einer Website veröffentlicht wird.

Die **[!UICONTROL Im Formular referenzierte Daten werden automatisch geladen]** -Option können Sie automatisch die Daten vorab laden, die den Eingabe- und Zusammenführungsfeldern im Formular entsprechen. Die Daten, auf die in **[!UICONTROL Skript]** und **[!UICONTROL Test]** sind nicht betroffen. Wenn diese Option nicht aktiviert ist, müssen Sie die Felder mithilfe der **[!UICONTROL Zusätzliche Daten laden]** -Option.

Mit der Option **[!UICONTROL Ladung zusätzlicher Daten]** können Sie Felder mit Daten vorausfüllen, auch wenn diese Informationen nicht auf den Seiten des Formulars verwendet werden.

So können Sie beispielsweise das Geschlecht des Empfängers vorausfüllen und ihn über eine Testkomponente automatisch zur entsprechenden Seite weiterleiten.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Versand und Tracking von Web-Formularen verwalten {#managing-web-forms-delivery-and-tracking}

Nachdem ein Formular erstellt, konfiguriert und veröffentlicht wurde, können Sie es bereitstellen und die Benutzerantworten tracken.

### Lebenszyklus eines Formulars {#life-cycle-of-a-form}

Der Lebenszyklus eines Formulars besteht aus drei Phasen:

1. **In Bearbeitung**

   Dies ist die anfängliche Designphase. Wenn ein neues Formular erstellt wird, befindet es sich in der Bearbeitungsphase. Zugriff auf das Formular, nur zu Testzwecken, erfordert dann den Parameter **[!UICONTROL __uuid]** in der URL verwendet werden. Auf diese URL kann im **[!UICONTROL Vorschau]** Unterregisterkarte. Siehe [Parameter der Formular-URL](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Der Zugriff auf das Formular erfolgt in der gesamten Bearbeitungsphase über diese spezielle URL.

1. **Veröffentlichung ausstehend**

   In einigen Fällen (z. B. wenn [Importieren eines Formulars über ein Package](#import-web-packages)), kann ein Webformular **[!UICONTROL Veröffentlichung ausstehend]** -Status, bis sie live ist.

   >[!NOTE]
   >
   >Für technische Webanwendungen (verfügbar über **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Webanwendungen]** ), ein Formular mit dem **[!UICONTROL Veröffentlichung ausstehend]** Status wird automatisch [veröffentlicht](#publishing-a-form) und erhält die **[!UICONTROL Online]** -Status.

1. **Online**

   Sobald die Entwurfsphase abgeschlossen ist, kann das Formular bereitgestellt werden.

   Wenn ein Formular **[!UICONTROL In Bearbeitung]** oder **[!UICONTROL Veröffentlichung ausstehend]** status, muss es [veröffentlicht](#publishing-a-form) , um online zu sein und über die URL des Webformulars in einem Browser zugänglich zu sein.

   Nach der Veröffentlichung ist das Formular aktiv, bis es abläuft.

   Das Formular ist so lange **[!UICONTROL Live]**, bis seine Gültigkeit erlischt.

   >[!CAUTION]
   >
   >Die URL des Formulars darf nicht die Variable **[!UICONTROL __uuid]** -Parameter.

1. **Geschlossen**

   Wenn die Bereitstellungsphase vorüber ist, ist das Formular geschlossen und nicht mehr verfügbar. Benutzer können dann nicht mehr darauf zugreifen.

   Das Ablaufdatum kann im Fenster mit den Formulareigenschaften definiert werden. Weitere Informationen hierzu finden Sie unter [Formular online verfügbar machen](#making-a-form-available-online).

Der Veröffentlichungsstatus eines Formulars wird in der Formularliste angezeigt.

![](assets/s_ncs_admin_survey_status.png)

### Formular veröffentlichen {#publishing-a-form}

Um den Status eines Formulars zu ändern, müssen Sie es veröffentlichen. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Veröffentlichung]** oberhalb der Liste der Webformulare und wählen Sie den Status in der Dropdown-Liste aus.

![](assets/webapp_publish_webform.png)

### Formular online verfügbar machen {#making-a-form-available-online}

Damit Benutzer auf das Formular zugreifen können, muss es sich in Produktion befinden und gestartet worden sein, d. h. innerhalb seiner Gültigkeitsdauer. Die Gültigkeitsdaten werden über die **[!UICONTROL Eigenschaften]** Link des Formulars.

* Geben Sie im Bereich **[!UICONTROL Projekt]** über die entsprechenden Felder das Start- und Enddatum für das Formular ein.

  ![](assets/webapp_availability_date.png)

* Wählen Sie den Link **[!UICONTROL Nachricht personalisieren, die bei geschlossenem Formular angezeigt wird...]** aus, um eine Fehlernachricht zu definieren. Diese wird angezeigt, wenn ein Benutzer versucht, auf das Formular zuzugreifen, das nicht gültig ist;

  Siehe [Zugriff auf das Formular](defining-web-forms-properties.md#accessibility-of-the-form).

### Formular per E-Mail versenden {#delivering-a-form-via-email}

Wenn Sie eine Einladung per E-Mail versenden, können Sie die Option **[!UICONTROL Adobe-Campaign-Verschlüsselung]** zur Abstimmung der Daten verwenden. Gehen Sie dazu zum Versand-Assistenten und passen Sie den Link an das Formular an, indem Sie die folgenden Parameter hinzufügen:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

In diesem Fall muss der Abstimmschlüssel für die Datenspeicherung die verschlüsselte Kennung des Empfängers sein. Weitere Informationen finden Sie unter [Formulardaten vorausfüllen](#pre-loading-the-form-data).

In diesem Fall müssen Sie im Datensatzfeld die Option **[!UICONTROL Vorausgefüllten Datensatz aktualisieren]** aktivieren. Weiterführende Informationen finden Sie unter [Antworten in Webformularen speichern](web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Antworten protokollieren {#log-responses}

Das Tracking von Antworten kann in einem speziellen Tab aktiviert werden, um die Auswirkungen Ihres Webformulars zu überwachen. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Erweiterte Parameter...]** im Fenster der Formulareigenschaften verknüpfen und die **[!UICONTROL Protokollantworten]** -Option.

![](assets/s_ncs_admin_survey_trace.png)

Im Tab **[!UICONTROL Antworten]** sehen Sie die Identität der reagierenden Kontakte.

![](assets/s_ncs_admin_survey_trace_tab.png)

Selektieren Sie einen Empfänger und wählen Sie dann die Schaltfläche **[!UICONTROL Details...]** aus, um die Antworten aufzurufen.

![](assets/s_ncs_admin_survey_trace_edit.png)

Sie können die Antwortprotokolle zu den Fragen verwenden, um beispielsweise Erinnerungen nur an Kontakte zu senden, die nicht geantwortet haben, oder um reagierenden Kontakten spezielle Nachrichten zukommen zu lassen.

### Webformularpakete importieren {#import-web-packages}

Beim Exportieren und Importieren eines Packages mit einem Webformular von einer Instanz zu einer anderen Instanz (z. B. von einer Phase zur Produktion) kann der Status des Webformulars auf der neuen Instanz abhängig von verschiedenen Bedingungen variieren. Die verschiedenen Fälle sind unten aufgeführt.

Weitere Informationen zu den verschiedenen Status eines Webformulars finden Sie in [diesem Abschnitt](#life-cycle-of-a-form).

>[!NOTE]
>
>Wenn Sie ein Webformular über ein Package exportieren, ist der Formularstatus im Inhalt des resultierenden Pakets sichtbar.

* Wenn der Status des Webformulars **[!UICONTROL Veröffentlichung ausstehend]** oder **[!UICONTROL Online]** beim Export aus der ersten Instanz:

   * Das Webformular ruft die **[!UICONTROL Veröffentlichung ausstehend]** Status beim Import in die neue Instanz.

   * Wenn das Webformular bereits in der neuen Instanz vorhanden ist, wird es durch die neue Version des Formulars ersetzt und nimmt die **[!UICONTROL Veröffentlichung ausstehend]** Status, auch wenn die alte Version des Formulars **[!UICONTROL Online]**.

   * Unabhängig davon, ob das Formular vorhanden ist oder nicht, muss das Formular [veröffentlicht](#publishing-a-form) werden **[!UICONTROL Online]** auf der neuen Instanz angezeigt werden und über die URL des Webformulars in einem Browser zugänglich sind.

* Wenn der Status des Webformulars **[!UICONTROL In Bearbeitung]** beim Export:

   * Wenn das Webformular auf der Instanz neu ist, auf der das Paket importiert wird, ruft das Webformular die **[!UICONTROL In Bearbeitung]** -Status.

   * Wenn das Webformular bereits in der neuen Instanz vorhanden ist, handelt es sich um eine Änderung in einem vorhandenen Formular. Wenn die alte Formularversion **[!UICONTROL Online]**, bleibt die alte Version online, bis die neue Version des Formulars [veröffentlicht](#publishing-a-form) erneut auf der neuen Instanz.

  >[!NOTE]
  >
  >Sie können die neueste Version Ihres Webformulars mit dem **[!UICONTROL Vorschau]** Registerkarte.

<!--For RN:
* Now, when a web form has the **Pending publication** status, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)
-->
