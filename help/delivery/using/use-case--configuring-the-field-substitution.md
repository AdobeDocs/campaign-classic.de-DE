---
title: '"Anwendungsbeispiel: Wertersetzung konfigurieren"'
seo-title: '"Anwendungsbeispiel: Wertersetzung konfigurieren"'
description: '"Anwendungsbeispiel: Wertersetzung konfigurieren"'
seo-description: null
page-status-flag: never-activated
uuid: 7f083dc6-e6d7-4eea-ac66-87674716515c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: a104fcab-75e6-4d73-bc3d-88570de6df7f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 003bac4c5d89290b9d3653d6ddfab7284b68642d

---


# Anwendungsbeispiel: Wertersetzung konfigurieren{#use-case-configuring-the-field-substitution}

Die zufällige Ersetzung von Werten bietet die Möglichkeit, fehlende Werte in Testadressen durch aus der Empfängertabelle stammende Werte zu ersetzen, falls diese in einem Versand benutzt werden (z. B. Name, Stadt usw.).

Auf diese Weise ist es nicht erforderlich, jede Testadresse manuell zu ergänzen. Stattdessen werden Werte aus der für den Versand vorgesehenen Empfängerliste willkürlich ausgewählt und den Testadressen zugewiesen.

## Kontext {#context}

In diesem Anwendungsbeispiel versendet die Webseite **Mein Online-Buchshop** je nach bevorzugtem Genre verschiedene Rabattangebote an seine Kunden.

Der versandverantwortliche Benutzer hat in die E-Mail ein Personalisierungsfeld eingefügt, das dieser Bedingung Rechnung trägt. Der Versand soll auch an Testadressen geschickt werden. In der Tabelle der Testadressen ist das Personalisierungsfeld enthalten, es wurden jedoch keine Werte gespeichert.

Zur Verwendung der zufälligen Wertersetzung benötigen Sie:

* einen Versand mit einem oder mehreren Personalisierungsfeldern,
* Testadressen, deren **Datenschema** um die im Versand verwendeten Personalisierungsfelder erweitert wurde.

## Versanderstellung {#step-1---creating-a-delivery}

Die Schritte zum Erstellen einer Auslieferung finden Sie im Abschnitt [Erstellen einer E-Mail-Auslieferung](../../delivery/using/creating-an-email-delivery.md) .

Im vorliegenden Beispiel wurde der unten gezeigte Newsletter erstellt :

![](assets/dlv_seeds_usecase_24.png)

## Testadressen-Schema erweitern {#editing-the-seed-addresses-data-schema}

Die einzelnen Schritte der Schemaerweiterung werden im Abschnitt  beschrieben.

Im vorliegenden Beispiel übernimmt das Testadressen-Schema einen im Datenschema der Empfänger erstellten Wert:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Diese Auflistung ermöglicht es dem Benutzer, das bevorzugte literarische Genre der Kunden anzugeben.

For this data schema modification to be viewable in the seed addresses **Input form**, you must update it. Weitere Informationen finden Sie im Abschnitt [Aktualisieren des Eingabedrucks](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) .

## Personalisierung konfigurieren {#configuring-personalization}

1. Öffnen Sie den zuvor erstellten Versand.

   In unserem Beispiel weist der Versand zwei Personalisierungsfelder auf: den **Vornamen** des Empfängers und sein **bevorzugtes Genre**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Konfigurieren Sie Ihre Lieferliste und Ihre Startadressen. Siehe [Identifizieren von Zielgruppen](../../delivery/using/steps-defining-the-target-population.md).

   Im vorliegenden Beispiel soll der Versand an alle Kunden mit dem bevorzugten Genre **Science-Fiction** adressiert werden.

   ![](assets/dlv_seeds_usecase_26.png)

   Außerdem werden über eine dynamische Bedingung Testadressen hinzugefügt.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Weitere Informationen zum **[!UICONTROL Edit the dynamic condition...]** Link finden Sie unter [Verwendungsfall: Auswahl der Saatgutadressen nach Kriterien](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

1. Click the **[!UICONTROL Preview]** tab then select a seed address to test the personalization.

   ![](assets/dlv_seeds_usecase_28.png)

   Eines der beiden Personalisierungsfelder bleibt leer. Da die Testadresse keinen Wert im entsprechenden Feld aufweist, wird in der HTML-Vorschau kein Wert angezeigt.

   Die zufällige Wertersetzung erfolgt erst **zum Zeitpunkt der Absendung**.

1. Click the **[!UICONTROL Send]** button.
1. Analysieren Sie den Versand und klicken Sie auf **Absendung bestätigen**.

   Bei Eingang des Versands im Postfach wurde bei den Testadressen-Empfängern der Wert wie gewünscht ersetzt.

   Alle Felder wurden korrekt personalisiert.

   ![](assets/dlv_seeds_usecase_08.png)
