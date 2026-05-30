---
product: campaign
title: Umfrage entwerfen
description: Wichtige Schritte zum Entwerfen einer Umfrage
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
TQID: https://experienceleague.adobe.com/aeRP0GoE5lu3eUsJ4kg8DoUnqFeipazoax--zX8Lv60
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2:
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 836
ht-degree: 51%

---

# Umfrage entwerfen{#building-a-survey}



## Neue Umfrage erstellen {#creating-a-new-survey}

In diesem Kapitel werden die Gestaltung eines **Umfrage**-Formulars mit Adobe Campaign sowie die verfügbaren Optionen und Konfigurationen beschrieben. Mit Adobe Campaign können Sie diese Umfrage für Benutzende verfügbar machen und Antworten in der Datenbank erfassen und archivieren.

Der Zugriff auf Webformulare erfolgt über den Knoten **[!UICONTROL Ressourcen > Online > Webanwendungen]** des Baums. Wählen Sie zur Erstellung einer neuen Umfrage oberhalb der Liste der Anwendungen die Schaltfläche **[!UICONTROL Neu]** aus oder rechtsklicken Sie auf die Liste und wählen Sie **[!UICONTROL Neu]** aus.

Wählen Sie die Umfragenvorlage (standardmäßig **[!UICONTROL newSurvey]**) aus.

![](assets/s_ncs_admin_survey_select_template.png)

Die Seiten des Formulars werden mit einem speziellen Editor erstellt, mit dem Sie (Text-)Eingabefelder, Auswahlfelder (Listen, Kontrollkästchen usw.) definieren und konfigurieren können und statischen Elementen (Bildern, HTML-Inhalten usw.). Sie können in „Behältern“ gesammelt und nach Bedarf ausgelegt werden. [Weitere Informationen](#adding-questions).

>[!NOTE]
>
>Weiterführende Informationen zur Definition von Inhalten und zur Erstellung von Bildschirm-Layouts für ein Web-Formular finden Sie in [diesem Dokument](../../web/using/about-web-forms.md).

## Felder hinzufügen {#adding-fields}

Über Formularfelder können Benutzer Informationen eingeben und Optionen auswählen. Diese Felder werden für jede Formularseite mit der ersten Schaltfläche der Symbolleiste im Menü **[!UICONTROL Mithilfe des Assistenten hinzufügen]** erstellt.

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>Sie können auch mit der rechten Maustaste klicken und einen Eingabebereich einfügen. Standardmäßig wird die Zone am Ende der ausgewählten Struktur eingefügt. Verwenden Sie die Pfeile in der Symbolleiste, um sie zu verschieben.

### Typen von Feldern {#types-of-fields}

Wenn Sie ein Feld zu einer Umfrage hinzufügen, müssen Sie dessen Typ auswählen. Folgende Optionen stehen zur Verfügung:

1. **[!UICONTROL Antwort auf eine Frage]**: Mit dieser Option können Sie ein neues Feld (auch als „archiviertes Feld“ bezeichnet) zum Speichern von Antworten deklarieren. In diesem Fall werden alle erfassten Werte gespeichert, auch wenn ein Teilnehmer das Formular mehrmals ausfüllt. Dieser Speichermodus ist nur in **Fragebögen** verfügbar. [Weitere Informationen](../../surveys/using/managing-answers.md#storing-collected-answers).
1. **[!UICONTROL Empfänger bearbeiten]**: Mit dieser Option können Sie ein Feld in der Datenbank auswählen. In diesem Fall werden die Antworten der Benutzer in diesem Feld gespeichert. Für jeden Teilnehmer wird nur der zuletzt gespeicherte Wert beibehalten und zu den Profildaten hinzugefügt.
1. **[!UICONTROL Variable hinzufügen]**: Mit dieser Option können Sie eine Einrichtung erstellen, damit Informationen nicht in der Datenbank gespeichert werden. Lokale Variablen können zuvor deklariert werden. Sie können sie auch direkt beim Erstellen des Felds hinzufügen.
1. **[!UICONTROL Existierende Frage importieren]**: Mit dieser Option können Sie bereits vorhandene, in anderen Umfragen erstellte Fragen importieren.

   >[!NOTE]
   >
   >Speichermodi und Feldimporte werden in [diesem Abschnitt](../../surveys/using/managing-answers.md#storing-collected-answers) beschrieben.

Die Art des hinzuzufügenden Felds (Dropdown-Liste, Textfeld, Kontrollkästchen usw.) Passt sich dem ausgewählten Speichermodus an. Der Feldtyp kann im Feld **[!UICONTROL Typ]** auf der Registerkarte **[!UICONTROL Allgemein]** geändert werden. Achten Sie dabei aber darauf, dass der Feldtyp zum Datentyp passt.

![](assets/s_ncs_admin_survey_change_type.png)

Die unterschiedlichen Typen verfügbarer Felder werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

## Elemente einer Umfrage {#survey-specific-elements}

Online-Umfragen basieren auf den Funktionen von Web-Anwendungen. Im Folgenden werden die umfragespezifischen Funktionen beschrieben.

### Multiple Choice {#multiple-choice}

Für Steuerelemente des Typs **[!UICONTROL Multiple Choice]** können Sie eine Mindest- und Höchstanzahl von Auswahlmöglichkeiten definieren. Beispielsweise können Sie mit dieser Option die Auswahl auf mindestens **2** Werte und höchstens **4** Werte aus den verfügbaren Optionen erzwingen:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Wenn die Anzahl der ausgewählten Optionen zu groß oder zu klein ist, wird eine entsprechende Nachricht angezeigt.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>In diesem Fall werden die Optionen mithilfe von Kontrollkästchen ausgewählt. Wenn nur eine Option möglich ist, werden Optionsschaltflächen verwendet.

Die entsprechende Konfiguration sieht folgendermaßen aus:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

Zusätzlich muss der Speicherort für dieses Eingabefeld ein **archiviertes Feld** vom Typ **[!UICONTROL Mehrfachwerte]** sein:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Diese Funktion ist nur für Formulare vom Typ **Umfrage** verfügbar.
>* Diese Option ist nicht mit der Anzeige zufälliger Fragen kompatibel. [Weitere Informationen](#adding-questions).

### Fragen hinzufügen {#adding-questions}

Es gibt zwei Arten von Containern: Standard und Frage. Standard-Container werden verwendet, um das Seiten-Layout und die bedingte Anzeige auf einer Seite zu konfigurieren. [Weitere Informationen](../../web/using/about-web-forms.md).

Verwenden Sie **Container &quot;**&quot;, um der Seite eine Frage hinzuzufügen und die möglichen Antworten unten in die Hierarchie einzufügen. Benutzerantworten auf Fragen, die in diesem Container platziert werden, können in Berichten analysiert werden.

>[!CAUTION]
>
>Fügen Sie niemals einen **Frage-** Container unterhalb eines anderen **Frage**-Containers in der Hierarchie ein.

![](assets/s_ncs_admin_question_label.png)

Der Titel der Frage wird im Feld Titel eingegeben. In diesem Fall wird der Stil aus dem Stylesheet des Formulars angewendet. Wählen Sie die Option **[!UICONTROL Titel im HTML-Format angeben]** aus, um die Frage zu personalisieren. Dadurch erhalten Sie Zugriff auf den HTML-Editor.

>[!NOTE]
>
>Weiterführende Informationen zur Verwendung des HTML-Editors finden Sie in [diesem Dokument](../../web/using/about-web-forms.md).

Beispiel:

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

Im obigen Beispiel wird das Rendering wie folgt ausgeführt:

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Jede Frage hat einen Container vom Typ **Frage**.

Sie können die zufällige Zeichnung von Fragen durch Adobe Campaign aktivieren. Sie können dann die Anzahl der Fragen, die auf der Seite angezeigt werden sollen, im Feld unten im Konfigurationsfenster angeben.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

Die Grafik stellt sich folgendermaßen dar:

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

Wenn die Seite aktualisiert wird, ändert sich die Anzeige der Fragen.

>[!CAUTION]
>
>Achten Sie bei der zufälligen Anzeige von Fragen darauf (die Option **[!UICONTROL Zufällige Anzeige]** ist auf der Seite aktiviert), dass Sie keine Multiple-Choice-Fragen verwenden, für die mindestens eine Auswahl zwingend erforderlich ist.
