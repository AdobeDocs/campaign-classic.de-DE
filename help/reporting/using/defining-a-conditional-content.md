---
title: Bedingte Inhalte erstellen
seo-title: Bedingte Inhalte erstellen
description: Bedingte Inhalte erstellen
seo-description: null
page-status-flag: never-activated
uuid: 2b49958d-6429-445d-a7dc-caaca072f4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0ca5e0f6-cc81-4da9-aecf-a095cc1a19f9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Bedingte Inhalte erstellen{#defining-a-conditional-content}

Sie können die Anzeige bestimmter Elemente in einem Bericht oder einer Berichtsseite an Bedingungen knüpfen.

Um bestimmte Elemente an Bedingungen anzupassen, passen Sie deren Sichtbarkeitseinstellungen an. For more on this, refer to [Conditioning item display](#conditioning-item-display).

Um die Anzeige einer oder mehrerer Seiten an Bedingungen zu knüpfen, verwenden Sie eine **[!UICONTROL Test]** Typaktivität. Weitere Informationen finden Sie unter [Bedingungen zur Anzeige von Seiten definieren](#conditioning-page-display).

## Bedingungen zur Anzeige von Elementen definieren {#conditioning-item-display}

Die Anzeige von Berichtelementen wird über Sichtbarkeitsbedingungen gesteuert. Wenn diese Bedingungen nicht erfüllt sind, werden die entsprechenden Elemente nicht angezeigt.

Die Sichtbarkeit kann zum Beispiel vom Status des Benutzers oder den von ihm in der Seite des Berichts ausgewählten oder angegebenen Elementen abhängen.

Beispiele bedingter Anzeige von Seitenelementen werden in [diesem Abschnitt](../../web/using/form-rendering.md#defining-fields-conditional-display) bereitgestellt.

Im folgenden Beispiel hängt die Anzeige von der Sprache ab:

![](assets/reporting_display_condition.png)

## Bedingungen zur Anzeige von Seiten definieren {#conditioning-page-display}

Im Diagramm eines Berichts ermöglicht die Aktivität **[!UICONTROL Test]** es, die Abfolge der Berichtseiten von Bedingungen abhängig zu machen.

Gehen Sie wie folgt vor:

1. Positionieren Sie die **[!UICONTROL Test]**-Aktivität im Diagramm und öffnen Sie sie.
1. Click the **[!UICONTROL Add]** button to create the various possible cases.

   ![](assets/reporting_test_sample.png)

   Für jeden Fall wird der **[!UICONTROL Test]**-Aktivität eine zusätzliche ausgehende Transition hinzugefügt.

   ![](assets/reporting_test_transitions.png)

1. Select the **[!UICONTROL Enable default transition]** to add a transition, in case one of the configured conditions isn&#39;t met.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

Eine **[!UICONTROL Test]**-Aktivität sollte zu Beginn des Diagramms positioniert werden, um die Anzeige beispielsweise vom Kontext oder dem Benutzerprofil abhängig zu machen.
