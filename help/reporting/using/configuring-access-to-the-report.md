---
product: campaign
title: Konfigurieren des Zugriffs auf den Bericht
description: Konfigurieren des Zugriffs auf den Bericht
feature: Reporting, Monitoring
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 1e5ab922-481c-4dce-a05e-a58408002e24
TQID: https://experienceleague.adobe.com/I1mGm11kQMgw-Iy-tbKBPGupVtiiCIT-SUzZVjoPwuM
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2: id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2: id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47id: cfda811a-e413-43a4-adf0-7370888f5cfcid: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 810
ht-degree: 100%

---

# Konfigurieren des Zugriffs auf den Bericht{#configuring-access-to-the-report}



## Anzeigekontext von Berichten {#report-display-context}

Definieren Sie den Anzeigekontext des Berichts mithilfe der Registerkarte **[!UICONTROL Anzeige]** in der Adobe Campaign-Plattform.Der Zugriff auf einen Bericht hängt von Auswahltyp, Anzeigebedingungen und Zugriffsberechtigungen ab.

### Auswahltyp {#selection-type}

Der Zugriff auf den Bericht kann auf einen bestimmten Kontext oder eine bestimmte Platzierung beschränkt werden, beispielsweise einen Versand, eine Empfängerin bzw. einen Empfänger, eine Auswahl an Empfangenden usw. Dieser Zugriff wird im Abschnitt **[!UICONTROL Auswahltyp]** auf der Registerkarte **[!UICONTROL Anzeige]** konfiguriert.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Einfach-Auswahl]**: Der Bericht ist nur bei Auswahl einer bestimmten Entität zugänglich.
* **[!UICONTROL Mehrfach-Auswahl]**: Der Bericht ist bei Auswahl mehrerer Entitäten zugänglich.
* **[!UICONTROL Allgemein]**: Der Bericht ist über die Liste der verfügbaren Berichte im Tab **[!UICONTROL Berichte]** zugänglich.

### Anzeigereihenfolge {#display-sequence}

Das Feld **[!UICONTROL Reihenfolge]** ermöglicht die Auswahl eines numerischen Wertes, der die Anzeigereihenfolge des Berichts in der Liste festlegt.

Die Berichte werden standardmäßig anhand dieses Feldes nach Relevanz geordnet. Der Bericht mit dem höchsten Wert gilt als am relevantesten.

Sie können eine beliebige Skala verwenden, zum Beispiel von 1 bis 10, von 0 bis 100 oder von -10 bis 10.

### Anzeigebedingungen {#display-conditions}

Die Anzeige des Berichts kann auch mittels einer Abfrage an Bedingungen geknüpft werden.

![](assets/s_ncs_advuser_report_visibility_5.png)

Im unten stehenden Beispiel ist die Anzeigebedingung, dass der Hauptkanal der Kampagne E-Mail ist.

![](assets/s_ncs_advuser_report_visibility_6.png)

Wenn es sich beim Hauptkanal der Kampagne um Briefpost handelt, wird der Bericht nicht in den Berichten der Kampagne verfügbar sein.

### Zugriffsberechtigung {#access-authorization}

Es besteht die Möglichkeit, den Bericht mit anderen Benutzern zu teilen.

Um den Zugriff auf einen Bericht zu ermöglichen, wählen Sie die Option **[!UICONTROL Mit anderen Benutzern geteilter Bericht]** aus. Wenn diese Option nicht ausgewählt ist, kann nur die Erstellerin bzw. der Ersteller des Berichts auf diesen zugreifen.

Der Bericht kann auch mit bestimmten Benutzern oder Benutzergruppen geteilt werden, indem sie im Bereich der Berechtigungen hinzugefügt werden.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Definieren der Filteroptionen {#defining-the-filtering-options}

Im Tab **[!UICONTROL Berichte]** werden alle in der Plattform verfügbaren Berichte anzeigt, auf die der angemeldete Benutzer Zugriff hat.

Sie werden standardmäßig nach Relevanz sortiert, es stehen jedoch andere Filtertypen zur Verfügung: nach Alphabet, Alter etc.

Sie können die Anzeige auch nach den Berichtkategorien filtern:

![](assets/report_ovv_select_type.png)

Um einen Bericht einer Kategorie zuzuordnen, wählen Sie diese im Tab **[!UICONTROL Anzeige]** wie im nachstehenden Beispiel aus:

![](assets/report_select_category.png)

Sie können hier eine neue Kategorie eingeben und sie zur Liste der verfügbaren Kategorien hinzufügen. Die entsprechende Auflistung wird automatisch aktualisiert.

## Erstellen eines Links zu einem Bericht {#creating-a-link-to-a-report-}

Sie können einen Bericht über einen spezifischen Knoten im Navigationsbaum wie eine Liste, einen Empfänger, einen Versand o. Ä. zugänglich machen. Erstellen Sie hierzu einfach eine Verknüpfung zum betreffenden Bericht und geben Sie die Entität an, in der dieser verfügbar gemacht werden soll.

Als Beispiel wird im Folgenden eine Verknüpfung eines Berichts zu einer Empfängerliste erstellt.

1. Klicken Sie auf **[!UICONTROL Neu]** und wählen Sie **[!UICONTROL Existierenden Bericht verknüpfen]** im Berichterstellungs-Assistenten aus.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Wählen Sie mithilfe der Dropdown-Liste den Bericht aus, für den Sie eine Verknüpfung erstellen möchten. Im vorliegenden Beispiel wird der Bericht **Kunden/Interessenten pro Land** gewählt.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Geben Sie einen Titel ein und wählen Sie das Schema aus. In diesem Beispiel wählen wir die Tabelle mit der Liste der Empfängerinnen und Empfänger aus.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Dies bedeutet, dass der Bericht von jeder Empfängerliste aus zugänglich sein wird und die Statistiken basierend auf den in der markierten Liste enthaltenen Empfängern berechnet werden.

1. Speichern Sie den Bericht und öffnen Sie ihn.
1. Geben Sie den Verbindungsschlüssel ein. In diesem Fall handelt es sich um den Fremdschlüssel der Verbindung „Ordner“.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Veröffentlichen Sie Ihren Bericht.
1. Öffnen Sie eine Ihrer Listen und klicken Sie auf den Tab **[!UICONTROL Berichte]**: Der zuvor erstellte Bericht ist nun verfügbar.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Berichtvorschau {#preview-of-the-report}

Bevor Sie Ihren Bericht veröffentlichen, stellen Sie im Tab **[!UICONTROL Vorschau]** sicher, dass er korrekt angezeigt wird.

![](assets/s_ncs_advuser_report_preview_01.png)

Wählen Sie entsprechend den Anzeigeparametern des Berichts zwischen den Optionen **[!UICONTROL Global]** und **[!UICONTROL Auswahl]**.

Diese beiden Optionen werden entsprechend den Anzeigeeinstellungen des Berichts ausgewählt. Wenn der gewählte Anzeigeparameter **[!UICONTROL Global]** ist, wählen Sie die gleichnamige Vorschauoption.**** Wenn die Anzeigeeinstellungen **[!UICONTROL Einzelauswahl]** oder **[!UICONTROL Mehrfachauswahl]**, die **[!UICONTROL Auswahl]** Die Vorschauoption muss ausgewählt sein.

Weitere Informationen hierzu finden Sie unter [Anzeigekontext von Berichten](#report-display-context).

Es stehen zudem Parameter zur Verfügung, die eine Kontrolle der Fehler ermöglicht. Der Parameter **_uuid** ist Teil der URL des Berichts. Sie können ihm die Parameter **&amp;_preview** oder **&amp;_debug** hinzufügen.

Die Funktionsweise dieser Parameter wird im Abschnitt zur Definition von **Webformular-Eigenschaften** des Kapitels [Webformulare](../../web/using/about-web-forms.md) beschrieben.

## Veröffentlichen des Berichts {#publishing-the-report}

Das Veröffentlichen des Berichts ist obligatorisch, wenn Sie ihn mit anderen Benutzern teilen und in der Liste der verfügbaren Berichte anzeigen möchten (siehe auch [Anzeigekontext von Berichten](#report-display-context)). Dieser Vorgang muss bei jeder Änderung des Berichts erneut durchgeführt werden.

1. Öffnen Sie den Publikationsassistenten durch Klicken auf **[!UICONTROL Publizieren]** in der Symbolleiste.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Klicken Sie auf **[!UICONTROL Starten]**, um die Veröffentlichung zu beginnen.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Der Bericht wird daraufhin in der Rubrik **[!UICONTROL Berichte]** verfügbar.
