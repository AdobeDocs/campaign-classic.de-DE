---
title: Über die Reaktionsverwaltung
seo-title: Über die Reaktionsverwaltung
description: Über die Reaktionsverwaltung
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 100%

---


# Über die Reaktionsverwaltung{#about-response-manager}

## Einleitung {#objectives}

Adobe Campaign bietet eine Anwendung zur Reaktionsverwaltung (Response Manager), die die Messung des Erfolgs und der Rentabilität einer Marketingkampagne oder eines Angebotsvorschlags ermöglicht, unabhängig vom verwendeten Kommunikationskanal (E-Mail, Mobilgeräte, Telefon, Briefpost, Fax, Agentur usw.).

## Hypothesenprinzip {#hypothesis-concept}

Um das Verhalten der Empfänger eines Angebots oder Versands vorherzusagen, können für einen bestimmten Zeitraum ab dem Kontaktdatum Hypothesen konfiguriert werden. Diese Hypothesen beziehen sich auf eine **Transaktionen**-Tabelle, in der Bestellungen und deren Details gespeichert werden.

Hypothesen sind zeitlich begrenzt und können zum Vergleich mit der Zielgruppe auch auf eine Kontrollgruppe angewandt werden. Die Ergebnisse werden von **Indikatoren** dargestellt, die mit Abschluss der Berechnung automatisch aktualisiert werden. Der den Hypothesen zugeordnete ROI wird in den Kampagnenberichten berücksichtigt.

Die standardmäßig mit Response Manager in Adobe Campaign verfügbaren **Berichte** synthetisieren Informationen bezüglich der Umsatzsteigerung, der Spannenberechnung sowie des ROIs des Versands oder des Angebots.

Mithilfe der detaillierten Bestellzeilen können Sie Ihre Hypothesen zudem so einschränken, dass sie sich zum Beispiel nur auf ein bestimmtes Produkt beziehen.

Auf diese Weise besteht die Möglichkeit, im Anschluss an einen für das jeweilige Produkt werbenden Versand den hierdurch erzeugten Umsatz auszuwerten. Stellen Sie hierfür die Hypothese auf, dass jeder Empfänger, der mindestens ein Exemplar des Artikels im auf den Kampagnenbeginn folgenden Monat erwirbt, auf diese Aktion reagiert. Die Reaktionsverwaltung wird entsprechend dieser Hypothese bestimmen, welche Bestellungen der Aktion zugeordnet werden können. Basierend auf diesen Zuordnungen kann der aus der Aktion resultierende Umsatz aus der Summe der zugeordneten Käufe bestimmt werden.

>[!CAUTION]
>
>Response Manager ist eine Option von **[!UICONTROL Campaign]**. Bitte überprüfen Sie Ihren Lizenzvertrag.

Es ist zudem möglich, alle Reaktionen des gesamten Haushalts eines Empfängers eines Versands oder Angebots zu erfassen.

Jede Hypothese wird einer einzigen Transaktionstabelle zugeordnet. Ein Versand oder ein Angebot können jedoch mehreren Hypothesen zugeordnet werden.

## Vorgehensweise {#method}

Lesen Sie vor der Nutzung von Response Manager den Abschnitt [Konfiguration](../../campaign/using/configuration.md) und nehmen Sie die notwendigen Einstellungen vor.

Bevor eine Hypothese über einen Versand oder ein Angebot gestartet werden kann, muss zunächst ihr Kontext in einer Vorlage bestimmt werden, auf welcher die Hypothese anschließend beruht.

Um Messhypothesen zu definieren und zu messen, gehen Sie also wie folgt vor:

1. Erstellen Sie eine Hypothesenvorlage. Siehe [Hypothesevorlage erstellen](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Stellen Sie eine oder mehrere Hypothesen über einen bestehenden Versand auf. Siehe [Referenzieren einer Hypothese im Versand einer Kampagne](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   oder

   Stellen Sie eine oder mehrere Hypothesen über Angebote auf. Siehe [Angebotshypothese erstellen](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Überprüfen Sie die Ergebnisse der Hypothesen. Siehe [Hypothesenverfolgung](../../campaign/using/hypothesis-tracking.md).
1. Starten Sie Hypothesen bei Bedarf neu. Siehe [Erstellen einer Hypothese direkt in einem Versand](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).

