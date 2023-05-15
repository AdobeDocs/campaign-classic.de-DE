---
product: campaign
title: "Anwendungsbeispiel: Konfigurieren der Wertersetzung"
description: "Anwendungsbeispiel: Konfigurieren der Wertersetzung"
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 100%

---

# Anwendungsbeispiel: Konfigurieren der Feld-Ersetzung{#use-case-configuring-the-field-substitution}



Die zufällige Ersetzung von Werten bietet die Möglichkeit, fehlende Werte in Testadressen durch aus der Empfängertabelle stammende Werte zu ersetzen, falls diese in einem Versand benutzt werden (z. B. Name, Stadt usw.).

Auf diese Weise ist es nicht erforderlich, jede Testadresse manuell zu ergänzen. Stattdessen werden Werte aus der für den Versand vorgesehenen Empfängerliste willkürlich ausgewählt und den Testadressen zugewiesen.

## Kontext {#context}

In diesem Anwendungsbeispiel versendet die Website **Meine Online-Bücherei** je nach bevorzugtem Genre verschiedene Rabattangebote an ihre Kunden.

Der Versandverantwortliche hat in seine E-Mail ein Personalisierungsfeld eingefügt, das mit dem bevorzugten Genre verknüpft ist. Ziel ist es, einige Testadressen zu verwenden: Diese Testadressen enthalten das Personalisierungsfeld in ihrer Tabelle, dort wird aber kein Wert gespeichert.

Zur Verwendung der zufälligen Wertersetzung benötigen Sie:

* einen Versand mit einem oder mehreren Personalisierungsfeldern,
* Testadressen, deren **Datenschema** um die im Versand verwendeten Personalisierungsfelder erweitert wurde.

## Erstellen eines Versands {#step-1---creating-a-delivery}

Die Schritte zum Erstellen eines Versands finden Sie im Abschnitt [Erstellen eines E-Mail-Versands](creating-an-email-delivery.md).

Im vorliegenden Beispiel wurde vom Versand-Manager der unten gezeigte Newsletter erstellt.

![](assets/dlv_seeds_usecase_24.png)

## Bearbeiten des Testadressen-Datenschemas {#editing-the-seed-addresses-data-schema}

Die einzelnen Schritte der Schemaerweiterung werden im Abschnitt beschrieben.

Im vorliegenden Beispiel übernimmt das Testadressen-Schema einen im Datenschema der Empfänger erstellten Wert:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Diese Auflistung ermöglicht es dem Benutzer, das bevorzugte literarische Genre der Kunden anzugeben.

Damit diese Änderung des Datenschemas im **Eingabeformular** für Testadressen angezeigt werden kann, müssen Sie es aktualisieren. Weitere Informationen finden Sie im Abschnitt [Aktualisieren des Eingabeformulars](use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form).

## Personalisierung konfigurieren {#configuring-personalization}

1. Öffnen Sie den zuvor erstellten Versand.

   In unserem Beispiel weist der Versand zwei Personalisierungsfelder auf: den **Vornamen** des Empfängers und sein **bevorzugtes Genre**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Konfigurieren Sie Ihre Versandliste und die Testadressen. Siehe [Identifizieren von Zielpopulationen](steps-defining-the-target-population.md).

   Im vorliegenden Beispiel soll der Versand an alle Kunden mit dem bevorzugten Genre **Science-Fiction** adressiert werden.

   ![](assets/dlv_seeds_usecase_26.png)

   Außerdem werden über eine dynamische Bedingung Testadressen hinzugefügt.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Weitere Informationen zum Link **[!UICONTROL Bearbeiten der dynamischen Bedingung....]** finden Sie unter [Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien](use-case--selecting-seed-addresses-on-criteria.md).

1. Klicken Sie auf den **[!UICONTROL Vorschau]**-Tab und wählen Sie eine Testadresse aus, um die Personalisierung zu testen.

   ![](assets/dlv_seeds_usecase_28.png)

   Eines der beiden Personalisierungsfelder bleibt leer. Da die Testadresse keinen Wert im entsprechenden Feld aufweist, wird in der HTML-Vorschau kein Wert angezeigt.

   Die zufällige Wertersetzung erfolgt erst **zum Zeitpunkt der Absendung**.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Senden]**.
1. Analysieren Sie den Versand und klicken Sie auf **Absendung bestätigen**.

   Bei Eingang des Versands im Postfach wurde bei den Testadressen-Empfängern der Wert wie gewünscht ersetzt.

   Alle Felder wurden korrekt personalisiert.

   ![](assets/dlv_seeds_usecase_08.png)
