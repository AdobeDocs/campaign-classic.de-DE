---
product: campaign
title: Anhänge erstellen
description: Anhänge erstellen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email
role: User
hide: true
exl-id: db65e83e-276f-4163-98c3-3658a48acffc
TQID: https://experienceleague.adobe.com/6AE1xmaWKR8AecaLkFsOsf7YKNuIPYHZ8f0TekKp-18
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: id: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1085
ht-degree: 85%

---

# Anhängen von Dateien an eine E-Mail{#attaching-files}

## Über E-Mail-Anhänge {#about-email-attachments}

Sie können an einen E-Mail-Versand eine oder mehrere Dateien anhängen.

>[!NOTE]
>
>Zur Vermeidung von Performance-Problemen wird empfohlen, nicht mehr als einen Anhang pro E-Mail hinzuzufügen. Der empfohlene Schwellenwert kann über [die Liste der Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md#delivery) konfiguriert werden.

Sie haben zwei Möglichkeiten:

* Datei unverändert anhängen.
* Den Inhalt des Anhangs für jeden Empfänger personalisieren. In diesem Fall ist die Erstellung eines **berechneten Anhangs** erforderlich. Der Titel des Anhangs wird für jede Nachricht zum Zeitpunkt des Versands berechnet und kann somit Empfänger-spezifisch sein. Die personalisierten Anhänge vor dem Senden in eine PDF-Datei umwandeln, wenn Sie über die Lizenz für **Variable Digital Printing** verfügen.

>[!NOTE]
>
>Diese Konfiguration wird in der Regel in den Versandvorlagen vorgenommen. Weitere Informationen hierzu finden Sie im Abschnitt [Über Vorlagen](about-templates.md).

## Schutzmechanismen {#attachments-guardrails}

Um Performance-Probleme zu vermeiden, dürfen die in den E-Mails enthaltenen Bilder nicht größer als 100 KB sein. Diese standardmäßig festgelegte Beschränkung kann in der Option `NmsDelivery_MaxDownloadedImageSize` geändert werden. Adobe empfiehlt jedoch dringend, große Bilder in E-Mail-Sendungen zu vermeiden.

Adobe empfiehlt außerdem, die Größe und Anzahl der angehängten Dateien zu begrenzen. Standardmäßig kann nur eine Datei als Anhang zu einer E-Mail hinzugefügt werden. Dieser Schwellenwert kann in der Option `NmsDelivery_MaxRecommendedAttachments` konfiguriert werden.

Weitere Informationen finden Sie in der [Liste der Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md#delivery).

## Lokale Datei anhängen {#attaching-a-local-file}

Gehen Sie wie folgt vor, um eine lokale Datei an einen Versand anzuhängen.

>[!NOTE]
>
>Sie können auch mehrere Dateien an einen Versand anhängen. Die Anhänge können in jedem beliebigen Format vorliegen, darunter auch im Zip-Format.

1. Wählen Sie den Link **[!UICONTROL Anhänge]**.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**.
1. Klicken Sie auf **[!UICONTROL Datei...]**, um die Datei auszuwählen, die an den Versand angehängt werden soll.

   ![](assets/s_ncs_user_wizard_email_attachement.png)

Sie können die Datei auch per Drag-and-Drop direkt in das Versandfeld **[!UICONTROL Anhänge]** ziehen oder das Symbol für **[!UICONTROL Datei anfügen]** in der Symbolleiste des Versandassistenten verwenden.

![](assets/s_ncs_user_wizard_add_file_ico.png)

Sobald Sie die Datei ausgewählt haben, wird sie auf den Server geladen, um zum Zeitpunkt des Versandstarts zur Verfügung zu stehen. Sie wird im Feld **[!UICONTROL Anhänge]** aufgeführt.

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Berechneten Anhang erstellen {#creating-a-calculated-attachment}

Wenn Sie einen berechneten Anhang erstellen, kann der Name des Anhangs bei der Analyse oder beim Versand jeder Nachricht berechnet werden und vom Empfänger abhängen. Es kann auch personalisiert und in PDF konvertiert werden.

![](assets/s_ncs_user_wizard_attachment.png)

Gehen Sie wie folgt vor, um einen personalisierten Anhang zu erstellen:

1. Wählen Sie den Link **[!UICONTROL Anhänge]**.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie **[!UICONTROL Berechneter Anhang]**.
1. Wählen Sie in der Dropdown-Liste des **[!UICONTROL Typ]**-Felds eine der folgenden Berechnungsmodi aus:

![](assets/s_ncs_user_wizard_email01_136.png)

Folgende Optionen stehen zur Verfügung:

* **Dateiname wird bei der Erstellung der Versandvorlage angegeben**
* **Dateiinhalt wird zum Zeitpunkt der Absendung für jede Nachricht personalisiert und in PDF konvertiert**
* **Dateiname wird bei der Versandanalyse berechnet (unabhängig vom Empfänger)**
* **Dateiname wird bei der Absendung für jede Nachricht berechnet (kann vom Empfänger abhängen)**

### Lokale Datei anhängen {#attach-a-local-file}

Wenn der Anhang eine lokale Datei ist, wählen Sie die Option **[!UICONTROL Dateiname wird bei der Erstellung der Versandvorlage angegeben]**. Die Datei wird lokal ausgewählt und auf den Server geladen. Gehen Sie wie folgt vor:

1. Geben Sie im Feld **[!UICONTROL Lokale Datei]** den gewünschten Anhang an.
1. Vergeben Sie gegebenenfalls einen Titel. Die Bezeichnung ersetzt den Dateinamen, wenn er in Messaging-Systemen angezeigt wird. Wenn nichts angegeben ist, wird standardmäßig der Dateiname verwendet.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Wählen Sie, wenn nötig, die Option **[!UICONTROL Datei auf den Server laden]** und klicken Sie auf den Link **[!UICONTROL Auf dem Server aktualisieren...]**, um den Vorgang zu starten.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

Nun kann die Datei als Anhang der auf dieser Vorlage beruhenden Sendungen verwendet werden.

### Personalisierte Nachricht anhängen {#attach-a-personalized-message}

Mit der Option **[!UICONTROL Dateiinhalt wird zum Zeitpunkt der Absendung für jede Nachricht personalisiert und in PDF konvertiert]** können Sie eine Datei mit Personalisierungsfeldern (z. B. für den Vor- und Nachnamen des Empfängers) auswählen.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Gehen Sie wie folgt vor, um diese Art von Anhang zu konfigurieren:

1. Wählen Sie die hochzuladende Datei aus.
1. Vergeben Sie gegebenenfalls einen Titel.
1. Wählen Sie die Option **[!UICONTROL Datei auf den Server laden]**, klicken Sie auf den Link **[!UICONTROL Auf dem Server aktualisieren]** und starten Sie den Upload in dem sich öffnenden Fenster.
1. Sie können eine Vorschau anzeigen. Wählen Sie dazu einen Empfänger aus.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analysieren und starten Sie den Versand.

   Jeder Empfänger enthält eine personalisierte PDF-Datei im E-Mail-Anhang.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)



### Berechnete Datei anhängen {#attach-a-calculated-file}

Sie können den Namen des Anhangs während der Versandvorbereitung berechnen lassen. Wählen Sie dazu die Option **[!UICONTROL Dateiname wird bei der Versandanalyse berechnet (unabhängig vom Empfänger)]** aus.

>[!NOTE]
>
>Diese Option ist nur für Sendungen vorgesehen, die durch einen externen Vorgang oder einen Workflow abgeschickt werden.

1. Geben Sie den Titel an, der für den Anhang verwendet werden soll.
1. Geben Sie den Pfad und den genauen Namen der Datei im Eingabefenster an.

   >[!IMPORTANT]
   >
   >Die Datei muss sich auf dem Server befinden.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analysieren und starten Sie den Versand.

   Im Analyseprotokoll können Sie die Berechnung des Dateinamens nachvollziehen.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Personalisierte Datei anhängen {#attach-a-personalized-file}

Bei der Auswahl des Anhangs können Sie die Option **[!UICONTROL Der Dateiname wird für jeden Empfänger während des Versands berechnet (kann vom Empfänger abhängen)]** auswählen. Anschließend können Sie die Personalisierungsdaten der Empfänger dem Namen der zu sendenden Datei zuordnen.

>[!NOTE]
>
>Diese Option ist nur für Sendungen vorgesehen, die durch einen externen Vorgang oder einen Workflow abgeschickt werden.

1. Geben Sie den Titel an, der für den Anhang verwendet werden soll.
1. Geben Sie den Pfad und den genauen Namen der Datei im Eingabefenster an. Wenn der Dateiname personalisiert ist, können Sie die Personalisierungsfelder für die entsprechenden Werte verwenden.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >Die Datei muss sich auf dem Server befinden.

1. Analysieren und starten Sie den Versand.

   In unten stehendem Beispiel wurde die angehängte Datei über den mithilfe der Zusammenführungsfelder konfigurierten Namen gewählt.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Einstellungen für den Anhang {#attachment-settings}

Für die ersten beiden Optionen können Sie **[!UICONTROL Datei auf den Server hochladen]** durch Auswahl der entsprechenden Option wählen. Über den Link **[!UICONTROL Datei auf dem Server aktualisieren]** können Sie mit dem Hochladen beginnen.

![](assets/s_ncs_user_wizard_email01_137.png)

Eine Nachricht bestätigt, dass die Datei erfolgreich hochgeladen wurde:

![](assets/s_ncs_user_wizard_email01_1371.png)

Ein Warnhinweis erscheint, wenn die Datei geändert wurde:

![](assets/s_ncs_user_wizard_email01_1372.png)

Im **[!UICONTROL Erweitert]**-Tab können Sie für Anhänge die folgenden Optionen konfigurieren:

* Auswahl der Empfänger, die den Anhang erhalten sollen. Kreuzen Sie die Option **[!UICONTROL Empfängerfilter bezüglich des Anhangs aktivieren]** an und geben Sie im Eingabefenster in Form eines JavaScripts das Auswahlkriterium an.
* Erstellung eines Scripts, um den Dateinamen zu personalisieren.

  Geben Sie Ihren Text im Fenster ein und verwenden Sie die Personalisierungsfelder in der Dropdown-Liste. Im folgenden Beispiel wird der Dateiname so personalisiert, dass er das heutige Datum und den Namen des Empfängers enthält.

  ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
