---
product: campaign
title: E-Mail-Anreicherung mit benutzerdefinierten Datumsfeldern
description: Erfahren Sie, wie Sie E-Mails mit benutzerdefinierten Datumsfeldern anreichern.
feature: Workflows
hide: true
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
TQID: https://experienceleague.adobe.com/HBRLw5dHFXoihTa4JCgMxKp9TxIUwsPp-LJYyEBnN7k
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 633
ht-degree: 100%

---

# E-Mail-Anreicherung mit benutzerdefinierten Datumsfeldern{#email-enrichment-with-custom-date-fields}



In diesem Beispiel möchten wir Empfangenden, die im aktuellen Monat Geburtstag haben, eine E-Mail mit benutzerdefinierten Datenfeldern senden. Die E-Mail enthält einen Coupon, der eine Woche vor und nach dem Geburtstag gültig ist.

Wir müssen mit einer Aktivität **[!UICONTROL Aufspaltung]** Empfangende aus einer Liste ansprechen, die diesen Monat Geburtstag haben. Danach wird mit der Aktivität **[!UICONTROL Anreicherung]** das benutzerdefinierte Datenfeld zur Angabe des Gültigkeitsdatums in der Angebots-E-Mail verwendet.

![](assets/uc_enrichment.png)

Gehen Sie wie folgt vor:

1. Fügen Sie im Tab **[!UICONTROL Zielgruppenbestimmungen und Workflows]** Ihrer Kampagne per Drag &amp; Drop die Aktivität **[!UICONTROL Liste lesen]** hinzu, um Ihre Empfängerliste auszuwählen.
1. Die zu verarbeitende Liste kann explizit angegeben, von einem Script berechnet oder dynamisch abgerufen werden. Dies hängt von den hier aktivierten Optionen oder angegebenen Parametern ab.

   ![](assets/uc_enrichment_1.png)

1. Fügen Sie die Aktivität **[!UICONTROL Aufspaltung]** hinzu, um die Empfänger, die im aktuellen Monat Geburtstag haben, von den restlichen Empfängern zu trennen.
1. Um Ihre Liste aufzuspalten, wählen Sie in der Kategorie **[!UICONTROL Filterung der Datensätze]** die Option **[!UICONTROL Filterbedingung für die Eingangspopulation hinzufügen]** aus. Klicken Sie danach auf **[!UICONTROL Bearbeiten]**.

   ![](assets/uc_enrichment_2.png)

1. Wählen Sie **[!UICONTROL Filterbedingungen]** aus und danach die Schaltfläche **[!UICONTROL Ausdruck bearbeiten]**, um nach dem Geburtstagsmonat zu filtern.

   ![](assets/uc_enrichment_3.png)

1. Wählen Sie **[!UICONTROL Erweiterte Auswahl]** und danach **[!UICONTROL Formel von einem Ausdruck ausgehend erstellen]** aus und fügen Sie den folgenden Ausdruck hinzu: Month(@birthDate).
1. Wählen Sie in der Spalte **[!UICONTROL Operator]** die Option **[!UICONTROL gleich]** aus.
1. Filtern Sie Ihre Bedingung weiter, indem Sie für den Monat den **[!UICONTROL Wert]** des aktuellen Datums hinzufügen: Month(GetDate()).

   Dadurch werden Empfänger abgefragt, deren Geburtsmonat mit dem aktuellen Monat übereinstimmt.

   ![](assets/uc_enrichment_4.png)

1. Klicken Sie auf **[!UICONTROL Beenden]**. Wählen Sie dann im Tab **[!UICONTROL Allgemein]** der Aktivität **[!UICONTROL Aufspaltung]** in der Kategorie **[!UICONTROL Ergebnisse]** die Option **[!UICONTROL Komplement erzeugen]** aus.

   Mit dem Ergebnis von **[!UICONTROL Komplement]** können Sie eine Versandaktivität hinzufügen oder eine Liste aktualisieren. In unserem Beispiel haben wir einfach die Aktivität **[!UICONTROL Ende]** hinzugefügt.

   ![](assets/uc_enrichment_6.png)

Konfigurieren Sie anschließend die Aktivität **[!UICONTROL Anreicherung]**:

1. Fügen Sie die Aktivität **[!UICONTROL Anreicherung]** nach Ihrer Teilmenge ein, um Ihre benutzerdefinierten Datumsfelder hinzuzufügen.

   ![](assets/uc_enrichment_7.png)

1. Öffnen Sie die Aktivität **[!UICONTROL Anreicherung]**. Wählen Sie in der Kategorie **[!UICONTROL Zusatzinformationen]** die Option **[!UICONTROL Daten hinzufügen]** aus.

   ![](assets/uc_enrichment_8.png)

1. Wählen Sie zuerst **[!UICONTROL Daten in Relation mit der Filterdimension]** und danach **[!UICONTROL Daten der Filterdimension]** aus.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**.

   ![](assets/uc_enrichment_9.png)

1. Fügen Sie einen **[!UICONTROL Titel]** hinzu. Wählen Sie dann in der Spalte **[!UICONTROL Ausdruck]** die Option **[!UICONTROL Ausdruck bearbeiten]** aus.

   ![](assets/uc_enrichment_10.png)

1. Zuerst muss die Woche vor dem Geburtstag als das **Gültigkeitsstartdatum** mit dem folgenden **[!UICONTROL Ausdruck]** ausgewählt werden: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Um danach das benutzerdefinierte Datumsfeld **Gültigkeitsenddatum** zu erstellen, mit dem die Woche nach dem Geburtstag ausgewählt wird, muss dieser **[!UICONTROL Ausdruck]** hinzugefügt werden: `AddDays([target/@birthDate], 7)`.

   Sie können Ihren Ausdruck mit einem Titel kennzeichnen.

   ![](assets/uc_enrichment_12.png)

1. Klicken Sie auf **[!UICONTROL OK]**. Ihre Anreicherung ist nun fertig.

Nach der Aktivität **[!UICONTROL Anreicherung]** können Sie einen Versand hinzufügen. In unserem Fall haben wir einen E-Mail-Versand hinzugefügt, mit dem Empfangende, die im aktuellen Monat Geburtstag haben, ein spezielles Angebot mit Gültigkeitsdaten erhalten.

1. Fügen Sie die Aktivität **[!UICONTROL E-Mail-Versand]** per Drag &amp; Drop nach der Aktivität **[!UICONTROL Anreicherung]** ein.

   ![](assets/uc_enrichment_15.png)

1. Doppelklicken Sie auf die Aktivität **[!UICONTROL E-Mail-Versand]**, um Ihren Versand zu personalisieren.
1. Fügen Sie zu Ihrem Versand einen **[!UICONTROL Titel]** hinzu und wählen Sie dann **[!UICONTROL Fortfahren]** aus.
1. Bestätigen Sie die Erstellung des E-Mail-Versands mithilfe der **[!UICONTROL Speichern]**-Schaltfläche.
1. Vergewissern Sie sich im Tab **[!UICONTROL Validierung]** in den **[!UICONTROL Versandeigenschaften]** der E-Mail, dass die Option **[!UICONTROL Vor dem Start Versand bestätigen]** aktiviert ist.

   Starten Sie dann den Workflow, um Ihre ausgehende Transition mit den ausgewählten Daten anzureichern.

   ![](assets/uc_enrichment_18.png)

Sie können jetzt Ihre E-Mail-Nachricht mit den benutzerdefinierten Feldern gestalten, die Sie in der Aktivität **[!UICONTROL Anreicherung]** erstellt haben.

1. Doppelklicken Sie auf die Aktivität **[!UICONTROL E-Mail-Versand]**.
1. Fügen Sie Ihrer E-Mail die Zielgruppenerweiterungen zu hinzu. Diese sollten sich innerhalb des folgenden Ausdrucks befinden, damit Sie das Format der Gültigkeitsdaten konfigurieren können.

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Klicken Sie auf ![](assets/uc_enrichment_16.png). Wählen Sie **[!UICONTROL Erweiterung des Zieldatensatzes]** aus und wählen Sie danach mit der Aktivität **[!UICONTROL Anreicherung]** die zuvor erstellten benutzerdefinierten Gültigkeitsdaten aus, um Ihre Erweiterung zum formatDate-Ausdruck hinzuzufügen.

   ![](assets/uc_enrichment_19.png)

1. Konfigurieren Sie Ihren E-Mail-Inhalt nach Bedarf.

   ![](assets/uc_enrichment_17.png)

1. Sehen Sie sich Ihre E-Mail in der Vorschau an, um zu überprüfen, ob die benutzerdefinierten Datumsfelder korrekt konfiguriert wurden.

   ![](assets/uc_enrichment_20.png)

Ihre E-Mail ist jetzt bereit. Sie können mit dem Ausführen Ihrer Testsendungen beginnen und den Versand Ihrer Geburtstags-E-Mails bestätigen.
