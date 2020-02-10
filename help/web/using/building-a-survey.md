---
title: Umfrage zusammenstellen
seo-title: Umfrage zusammenstellen
description: Umfrage zusammenstellen
seo-description: null
page-status-flag: never-activated
uuid: 50d501b9-2b4f-48d1-b394-f7f71c413990
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 6850851d-1dbe-44f0-bbff-18dbac2cad9a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Umfrage zusammenstellen{#building-a-survey}

## Neue Umfrage erstellen {#creating-a-new-survey}

In diesem Abschnitt werden die Erstellung eines Formulars vom Typ **Umfrage** in Adobe Campaign sowie die verfügbaren Optionen und Konfigurationen beschrieben. Mit Adobe Campaign können Sie diese Umfrage Benutzern zur Verfügung stellen sowie Antworten erfassen und in der Datenbank archivieren.

Der Zugriff auf Webformulare erfolgt über den **[!UICONTROL Resources > Online > Web applications]** Knoten der Struktur. Um eine Umfrage zu erstellen, klicken Sie auf die **[!UICONTROL New]** Schaltfläche über der Liste der Anwendungen oder klicken Sie mit der rechten Maustaste auf die Liste und wählen Sie **[!UICONTROL New]**.

Wählen Sie die Umfragenvorlage (standardmäßig **[!UICONTROL newSurvey]**) aus.

![](assets/s_ncs_admin_survey_select_template.png)

Die Seiten des Formulars werden mit einem speziellen Editor erstellt, mit dem Sie Eingabefelder, Auswahlfelder (Listen, Kontrollkästchen usw.) und statische Elemente (Bilder, HTML-Inhalte usw.) definieren und konfigurieren können. Sie können in &quot;Behältern&quot;gesammelt und entsprechend den Anforderungen angeordnet werden (siehe [Hinzufügen von Fragen](#adding-questions)).

>[!NOTE]
>
>Weiterführende Informationen zur Definition von Inhalten und zur Erstellung von Bildschirmlayouts für ein Webformular finden Sie in [diesem Abschnitt](../../web/using/about-web-forms.md).

## Felder hinzufügen {#adding-fields}

Mithilfe der Felder in einem Formular können Benutzer Informationen eingeben und Optionen auswählen. Sie werden für jede Seite im Formular über die erste Schaltfläche in der Symbolleiste mithilfe des **[!UICONTROL Add using the wizard]** Menüs erstellt.

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>Sie können ein Eingabefeld auch mit einem Rechtsklick einfügen. Standardmäßig wird das Eingabefeld am Ende des ausgewählten Baums eingefügt. Sie können es dann mit den Pfeilen in der Symbolleiste verschieben.

### Typen von Feldern {#types-of-fields}

Beim Hinzufügen eines Felds zu einer Umfrage müssen Sie den Typ des Felds auswählen. Die folgenden Optionen sind verfügbar:

1. **[!UICONTROL Answer a question]**: Mit dieser Option können Sie ein neues Feld (als &quot;archiviertes Feld&quot;bezeichnet) zum Speichern von Antworten deklarieren. In diesem Fall werden alle erfassten Werte gespeichert, auch wenn ein Teilnehmer das Formular mehrmals ausfüllt. Dieser Speichermodus ist nur in **Umfragen** verfügbar. Weitere Informationen finden Sie unter [Speichern erfasster Antworten](../../web/using/managing-answers.md#storing-collected-answers).
1. **[!UICONTROL Edit a recipient]**: Mit dieser Option können Sie ein Feld in der Datenbank auswählen. In diesem Fall werden Benutzerantworten in diesem Feld gespeichert. Für jeden Teilnehmer wird nur der zuletzt gespeicherte Wert beibehalten und den Profildaten hinzugefügt.
1. **[!UICONTROL Add a variable]**: Mit dieser Option können Sie ein Setup erstellen, sodass Informationen nicht in der Datenbank gespeichert werden.  Lokale Variablen können im Upstream deklariert werden. Sie können sie auch direkt beim Erstellen des Felds hinzufügen.
1. **[!UICONTROL Import an existing question]**: Mit dieser Option können Sie vorhandene Fragen importieren, die in anderen Umfragen erstellt wurden.

   >[!NOTE]
   >
   >Speichermodi und Feldimporte werden unter [Speichern der erfassten Antworten](../../web/using/managing-answers.md#storing-collected-answers)ausführlich beschrieben.

Die Art des hinzuzufügenden Felds (Dropdown-Liste, Textfeld, Kontrollkästchen usw.) passt sich an den ausgewählten Speichermodus an. Sie können sie mithilfe des **[!UICONTROL Type]** Felds auf der **[!UICONTROL General]** Registerkarte ändern, stellen Sie jedoch sicher, dass sie mit dem Datentyp konsistent bleibt.

![](assets/s_ncs_admin_survey_change_type.png)

Die unterschiedlichen Typen verfügbarer Felder werden in [diesem Abschnitt](../../web/using/about-web-forms.md) beschrieben.

## Elemente einer Umfrage {#survey-specific-elements}

Online-Umfragen verwenden die Funktionen von Webanwendungen. Die spezifischen Funktionen in Verbindung mit Umfragefeldern werden unten beschrieben.

### Multiple Choice {#multiple-choice}

Für **[!UICONTROL Multiple choice]** Typsteuerelemente können Sie eine Mindest- und eine Höchstanzahl von Auswahlen definieren. Beispielsweise können Sie mit dieser Option die Auswahl auf mindestens **2** Werte und höchstens **4** Werte aus den verfügbaren Optionen erzwingen:

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

Wenn die Anzahl der ausgewählten Optionen zu groß oder zu klein ist, wird eine entsprechende Nachricht angezeigt.

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>In diesem Fall werden die Optionen mithilfe von Checkboxes ausgewählt. Wenn nur eine Option möglich ist, wird ein Radiobutton verwendet.

Die entsprechende Konfiguration sieht folgendermaßen aus:

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

In addition, the storage location for this input field must be a **[!UICONTROL Multiple values]** type **archived field**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* Diese Funktion ist nur für Formulare vom Typ **Umfrage** verfügbar.
>* Diese Option ist nicht mit der Anzeige zufälliger Fragen kompatibel. For more on this, refer to [Adding questions](#adding-questions).


### Fragen hinzufügen {#adding-questions}

Es gibt zwei Typen von Containern: Standard und Frage. Standard-Container werden zur Konfiguration des Seitenlayouts und zur bedingten Anzeige auf einer Seite verwendet. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../web/using/about-web-forms.md).

Mit einem **Frage**-Container können Sie eine Frage zur Seite hinzufügen und die möglichen Antworten darunter in der Hierarchie einfügen. Benutzerantworten zu Fragen, die in diesem Containertyp abgelegt werden, können in Berichten analysiert werden.

>[!CAUTION]
>
>Fügen Sie niemals einen **Frage-** Container unterhalb eines anderen **Frage**-Containers in der Hierarchie ein.

![](assets/s_ncs_admin_question_label.png)

Die Bezeichnung der Frage wird in das Beschriftungsfeld eingegeben. In diesem Fall wird der Stil aus dem Stylesheet des Formulars angewendet. Wählen Sie die **[!UICONTROL Enter the title in HTML format]** Option aus, um sie zu personalisieren. Dadurch erhalten Sie Zugriff auf den HTML-Editor.

>[!NOTE]
>
>Weiterführende Informationen zur Verwendung des HTML-Editors finden Sie in [diesem Abschnitt](../../web/using/about-web-forms.md).

Beispiel:

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

Im obigen Beispiel wird das Rendering wie folgt ausgeführt:

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>Jede Frage hat einen Container vom Typ **Frage**.

Sie können die zufällige Anzeige von Fragen durch Adobe Campaign aktivieren. Danach können Sie im Feld am unteren Rand des Konfigurationsfensters angeben, wie viele Fragen auf der Seite angezeigt werden sollen.

![](assets/s_ncs_admin_survey_containers_qu_display.png)

Die Grafik stellt sich folgendermaßen dar:

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

Wenn die Seite aktualisiert wird, ändert sich die Anzeige der Fragen.

>[!CAUTION]
>
>When you display a question randomly (**[!UICONTROL Display randomly]** option checked on the page), be careful not to use multiple choice questions for which one or more selections are mandatory.

