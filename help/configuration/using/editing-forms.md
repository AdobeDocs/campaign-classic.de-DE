---
product: campaign
title: Bearbeiten von Formularen
description: Bearbeiten von Formularen
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 5%

---


# Bearbeiten von Formularen{#editing-forms}

![](../../assets/common.svg)

## Überblick

Marketer und Benutzer verwenden Eingabeformulare, um Datensätze zu erstellen, zu ändern und in der Vorschau anzuzeigen. Forms zeigt eine visuelle Darstellung von Informationen an.

Sie können Eingabeformulare erstellen und ändern:

* Sie können die werkseitigen Eingabeformulare ändern, die standardmäßig bereitgestellt werden. Die werkseitigen Eingabeformulare basieren auf den werkseitigen Datenschemata.
* Sie können benutzerdefinierte Eingabeformulare erstellen, die auf von Ihnen definierten Datenschemata basieren.

Forms sind Entitäten von `xtk:form` Typ. Sie können die Struktur des Eingabeformulars im `xtk:form` Schema. Um dieses Schema anzuzeigen, wählen Sie **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** aus dem Menü. Mehr dazu [Formularstruktur](form-structure.md).

Um auf Eingabeformulare zuzugreifen, wählen Sie **[!UICONTROL Administration] > [!UICONTROL Konfiguration] > [!UICONTROL Formulare]** aus dem Menü:

![](assets/d_ncs_integration_form_arbo.png)

Um Formulare zu entwerfen, bearbeiten Sie den XML-Inhalt im XML-Editor:

![](assets/d_ncs_integration_form_edit.png)

[Mehr dazu](form-structure.md#formatting)

Klicken Sie auf die Schaltfläche **[!UICONTROL Vorschau]** tab:

![](assets/d_ncs_integration_form_preview.png)

## Formulartypen

Sie können verschiedene Arten von Eingabeformularen erstellen. Der Formulartyp bestimmt, wie Benutzer im Formular navigieren:

* Konsolenbildschirm

   Dies ist der Standardformulartyp. Das Formular besteht aus einer einzelnen Seite.

   ![](assets/console_screen_form.png)

* Content-Management

   Verwenden Sie diesen Formulartyp für das Content Management. Siehe dies [Anwendungsfall](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistent

   Dieses Formular umfasst mehrere schwebende Bildschirme, die in einer bestimmten Sequenz angeordnet sind. Benutzer navigieren von einem Bildschirm zum nächsten. [Mehr dazu](form-structure.md#wizards)

* Iconbox

   Dieses Formular umfasst mehrere Seiten. Um durch das Formular zu navigieren, wählen Benutzer auf der linken Seite des Formulars Symbole aus.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Dieses Formular umfasst mehrere Seiten. Um durch das Formular zu navigieren, wählen Benutzer Registerkarten oben im Formular aus.

   ![](assets/notebook_form_preview.png)

* Vertikaler Bereich

   Dieses Formular zeigt eine Navigationsstruktur.

* Horizontaler Bereich

   Dieses Formular zeigt eine Liste von Elementen an.

