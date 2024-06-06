---
product: campaign
title: Veröffentlichen eines Web-Formulars
description: Veröffentlichen eines Web-Formulars
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '1373'
ht-degree: 100%

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

  Diese Verschlüsselungsmethode verwendet eine extern bereitgestellte Kennung (ID), die mit einem Schlüssel verknüpft ist, der von Adobe Campaign und dem externen Anbieter gemeinsam verwendet wird. Dieser Schlüssel wird im Feld **[!UICONTROL DES-Schlüssel]** eingegeben.

* **[!UICONTROL Feldliste]**

  Mit dieser Option können Sie aus den im aktuellen Kontext des Formulars bereitgestellten Feldern auswählen. Anhand dieser Felder wird das entsprechende Profil in der Datenbank gesucht.

  ![](assets/s_ncs_admin_survey_preload_methods_002.png)

  Felder können den Formulareigenschaften über den Tab **[!UICONTROL Parameter]** hinzugefügt werden (siehe [Parameter hinzufügen](defining-web-forms-properties.md#adding-parameters)). Sie werden in der Formular-URL oder den Eingabefeldern platziert.

  >[!CAUTION]
  >
  >Die Daten in den ausgewählten Feldern sind nicht verschlüsselt. Sie dürfen nicht verschlüsselt bereitgestellt werden, da sie Adobe Campaign nicht entschlüsseln kann, wenn die Option **[!UICONTROL Feldliste]** ausgewählt ist.

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

Mit der Option **[!UICONTROL Referenzierte Daten werden automatisch in das Formular geladen]** können Sie automatisch Daten, die den Eingabe- und Verbindungsfeldern des Formulars entsprechen, vorausfüllen. Dies betrifft aber keine Daten, die in den Aktivitäten **[!UICONTROL Script]** und **[!UICONTROL Test]** referenziert werden. Ist diese Option nicht ausgewählt, müssen Sie die Felder mit der Option **[!UICONTROL Ladung zusätzlicher Daten]** definieren.

Mit der Option **[!UICONTROL Ladung zusätzlicher Daten]** können Sie Felder mit Daten vorausfüllen, auch wenn diese Informationen nicht auf den Seiten des Formulars verwendet werden.

So können Sie beispielsweise das Geschlecht des Empfängers vorausfüllen und ihn über eine Testkomponente automatisch zur entsprechenden Seite weiterleiten.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Versand und Tracking von Web-Formularen verwalten {#managing-web-forms-delivery-and-tracking}

Nachdem ein Formular erstellt, konfiguriert und veröffentlicht wurde, können Sie es bereitstellen und die Benutzerantworten tracken.

### Lebenszyklus eines Formulars {#life-cycle-of-a-form}

Der Lebenszyklus eines Formulars besteht aus drei Phasen:

1. **In Bearbeitung**

   Dies ist die anfängliche Design-Phase. Wenn ein neues Formular erstellt wird, befindet es sich in der Bearbeitungsphase. Zugriff auf das Formular, nur zu Testzwecken, erfordert dann den Parameter **[!UICONTROL __uuid]** in der URL verwendet werden. Auf diese URL können Sie über die Unterregisterkarte **[!UICONTROL Vorschau]** zugreifen. Siehe [Parameter der Formular-URL](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Der Zugriff auf das Formular erfolgt in der gesamten Bearbeitungsphase über diese spezielle URL.

1. **Veröffentlichung ausstehend**

   In einigen Fällen (z. B. beim [Importieren eines Formulars über ein Package](#import-web-packages)) kann ein Web-Formular den Status **[!UICONTROL Veröffentlichung ausstehend]** haben, bis es live geschaltet wird.

   >[!NOTE]
   >
   >Für technische Web-Anwendungen (verfügbar über das Menü **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Web-Anwendungen]**) wird automatisch ein Formular mit dem Status **[!UICONTROL Veröffentlichung ausstehend]** [veröffentlicht](#publishing-a-form) und erhält den Status **[!UICONTROL Online]**.

1. **Online**

   Nach Abschluss der Konzeptionsphase kann das Formular versendet werden.

   Wenn ein Formular den Status **[!UICONTROL In Bearbeitung]** oder **[!UICONTROL Veröffentlichung ausstehend]** aufweist, muss es [veröffentlicht](#publishing-a-form) werden, damit es online ist und über die URL des Web-Formulars in einem Browser aufgerufen werden kann.

   Nach der Veröffentlichung ist das Formular so lange live, bis seine Gültigkeit erlischt.

   Das Formular ist so lange **[!UICONTROL Live]**, bis seine Gültigkeit erlischt.

   >[!CAUTION]
   >
   >Damit ein Formular gesendet werden kann, darf seine URL nicht den Parameter **[!UICONTROL __uuid]** enthalten.

1. **Geschlossen**

   Wenn die Bereitstellungsphase vorüber ist, ist das Formular geschlossen und nicht mehr verfügbar. Benutzer können dann nicht mehr darauf zugreifen.

   Das Ablaufdatum kann im Fenster mit den Formulareigenschaften definiert werden. Weitere Informationen hierzu finden Sie unter [Formular online verfügbar machen](#making-a-form-available-online).

Der Veröffentlichungsstatus eines Formulars wird in der Formularliste angezeigt.

![](assets/s_ncs_admin_survey_status.png)

### Formular veröffentlichen {#publishing-a-form}

Um den Status eines Formulars zu ändern, müssen Sie es veröffentlichen. Klicken Sie dazu oberhalb der Liste der Web-Formulare auf die Schaltfläche **[!UICONTROL Veröffentlichung]** und wählen Sie in der Dropdown-Liste den Status aus.

![](assets/webapp_publish_webform.png)

### Formular online verfügbar machen {#making-a-form-available-online}

Damit Benutzer auf das Formular zugreifen können, muss es sich in Produktion befinden und gestartet worden sein, d. h. innerhalb seiner Gültigkeitsdauer. Die Gültigkeitsdaten werden über den Link **[!UICONTROL Eigenschaften]** des Formulars eingegeben.

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

Das Tracking der Antworten kann auf einer speziellen Registerkarte aktiviert werden, um die Wirkung Ihres Web-Formulars zu überwachen. Wählen Sie dazu im Fenster mit den Formulareigenschaften den Link **[!UICONTROL Erweiterte Parameter...]** und dann die Option **[!UICONTROL Antworten protokollieren]** aus.

![](assets/s_ncs_admin_survey_trace.png)

Im Tab **[!UICONTROL Antworten]** sehen Sie die Identität der reagierenden Kontakte.

![](assets/s_ncs_admin_survey_trace_tab.png)

Selektieren Sie einen Empfänger und wählen Sie dann die Schaltfläche **[!UICONTROL Details...]** aus, um die Antworten aufzurufen.

![](assets/s_ncs_admin_survey_trace_edit.png)

Sie können die Antwortprotokolle zu den Fragen verwenden, um beispielsweise Erinnerungen nur an Kontakte zu senden, die nicht geantwortet haben, oder um reagierenden Kontakten spezielle Nachrichten zukommen zu lassen.

### Importieren von Web-Formularpaketen {#import-web-packages}

Beim Exportieren und Importieren eines Packages mit einem Web-Formular von einer Instanz zu einer anderen Instanz (z. B. von einer Phase zur Produktion) kann der Status des Web-Formulars auf der neuen Instanz abhängig von verschiedenen Bedingungen variieren. Die unterschiedlichen Fälle sind unten aufgeführt.

Weitere Informationen zu den verschiedenen Status eines Web-Formulars finden Sie in [diesem Abschnitt](#life-cycle-of-a-form).

>[!NOTE]
>
>Wenn Sie ein Web-Formular über ein Package exportieren, ist der Formularstatus im Inhalt des resultierenden Pakets sichtbar.

* Wenn der Status des Web-Formulars **[!UICONTROL Veröffentlichung ausstehend]** oder **[!UICONTROL Online]** beim Export aus der ersten Instanz ist:

   * Das Web-Formular ruft den Status **[!UICONTROL Veröffentlichung ausstehend]** beim Import in die neue Instanz ab.

   * Wenn das Web-Formular bereits in der neuen Instanz vorhanden ist, wird es durch die neue Version des Formulars ersetzt und nimmt den Status **[!UICONTROL Veröffentlichung ausstehend]** an, auch wenn die alte Version des Formulars den Status **[!UICONTROL Online]** hatte.

   * Unabhängig davon, ob das Formular vorhanden ist oder nicht, muss das Formular [veröffentlicht](#publishing-a-form) werden, damit es mit dem Status **[!UICONTROL Online]** auf der neuen Instanz angezeigt wird und über die URL des Web-Formulars in einem Browser zugänglich ist.

* Wenn der Status des Web-Formulars beim Export **[!UICONTROL In Bearbeitung]** war:

   * Wenn das Web-Formular auf der Instanz neu ist, auf der das Paket importiert wird, erhält das Web-Formular den Status **[!UICONTROL In Bearbeitung]**.

   * Wenn das Web-Formular bereits auf der neuen Instanz vorhanden ist, handelt es sich um eine Änderung in einem vorhandenen Formular. Wenn die alte Version des Formulars den Status **[!UICONTROL Online]** hatte, bleibt die alte Version online, bis die neue Version des Formulars erneut auf der neuen Instanz [veröffentlicht](#publishing-a-form) wird.

  >[!NOTE]
  >
  >Sie können die neueste Version Ihres Web-Formulars auf der Registerkarte **[!UICONTROL Vorschau]** prüfen.

<!--For RN:
* Now, when a web form has the **Pending publication** status, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)
-->
