---
product: campaign
title: Über die Reaktionsverwaltung
description: Über die Reaktionsverwaltung
feature: Campaigns
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
TQID: https://experienceleague.adobe.com/ScwRjZlHoAjXQBxig5Mt3HuNkpPiZ9J-FQTm9FuCY4g
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2: id: ede6e1ec-9279-415e-b828-a09735018d48
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 65%

---

# Erste Schritte mit Campaign Response Manager{#about-response-manager}



Adobe Campaign bietet ein Add-on zur Reaktionsverwaltung (Response Manager), mit dem Sie den Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen über alle Kommunikationskanäle hinweg messen können: E-Mail, Mobilgeräte, Briefpost usw.

## Hypothese {#hypothesis-concept}

Hypothesen können über einen bestimmten Zeitraum ab dem Kontaktdatum konfiguriert werden, um das Verhalten der Zielgruppen nach Erhalt eines Versands abzuleiten. Diese Hypothesen basieren auf einer **Transaktions** Tabelle, die Käufe und Details dieser Käufe speichert.

Hypothesen sind zeitlich begrenzt und können zum Vergleich mit der Zielgruppe auch auf eine Kontrollgruppe angewandt werden. Die Ergebnisse werden von **Indikatoren** dargestellt, die mit Abschluss der Berechnung automatisch aktualisiert werden. Der den Hypothesen zugeordnete ROI wird in den Kampagnenberichten berücksichtigt.

Die standardmäßig mit Response Manager in Adobe Campaign verfügbaren **Berichte** synthetisieren Informationen bezüglich der Umsatzsteigerung, der Spannenberechnung sowie des ROIs des Versands oder des Angebots.

Mithilfe der detaillierten Bestellzeilen können Sie Ihre Hypothesen zudem so einschränken, dass sie sich zum Beispiel nur auf ein bestimmtes Produkt beziehen.

Beispielsweise möchten wir im Anschluss an einen Versand, der einen Artikel befördert, den erzielten Umsatz bewerten. Wir wenden die Hypothese an, dass jeder Empfänger, der mindestens einen Artikel in dem Monat gekauft hat, der auf die Auslösung des Versands folgt, auf diese Aktion reagiert hat. Basierend auf dieser Hypothese bestimmt das Antwort-Management, welche Kaufanfragezeilen zugewiesen werden sollen. Auf dieser Grundlage wird es dann möglich sein, den resultierenden Umsatz als Summe dieser Zeilen zu bestimmen.

>[!CAUTION]
>
>Response Manager ist eine **[!UICONTROL Campaign]**-Option. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

Es ist zudem möglich, alle Reaktionen des gesamten Haushalts eines Empfängers eines Versands oder Angebots zu erfassen.

Jede Hypothese ist mit einer einzelnen Transaktionstabelle verknüpft. Ein Versand bzw. Angebot kann mit mehreren Hypothesen verknüpft werden.

## Umsetzung {#method}

Lesen Sie vor der Nutzung von Response Manager den Abschnitt [Konfiguration](configuration.md) und nehmen Sie die notwendigen Einstellungen vor.

Bevor eine Hypothese über einen Versand oder ein Angebot gestartet werden kann, muss zunächst ihr Kontext in einer Vorlage bestimmt werden, auf welcher die Hypothese anschließend beruht.

Um Messhypothesen zu definieren und zu messen, gehen Sie also wie folgt vor:

1. Erstellen Sie eine Hypothesenvorlage. [Weitere Informationen](hypothesis-templates.md#creating-a-hypothesis-model)
1. Stellen Sie eine oder mehrere Hypothesen über einen bestehenden Versand auf. [Weitere Informationen](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   oder

   Stellen Sie eine oder mehrere Hypothesen über Angebote auf. [Weitere Informationen](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. Überprüfen Sie die Ergebnisse der Hypothesen. [Weitere Informationen](hypothesis-tracking.md)
1. Starten Sie Hypothesen bei Bedarf neu. [Weitere Informationen](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
