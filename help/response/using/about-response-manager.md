---
product: campaign
title: Über die Reaktionsverwaltung
description: Über die Reaktionsverwaltung
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 878ba2b532d5cb59af77b6450b12ae5d2ff149b2
workflow-type: ht
source-wordcount: '407'
ht-degree: 100%

---

# Erste Schritte mit Campaign Response Manager{#about-response-manager}

![](../../assets/common.svg)

Adobe Campaign bietet ein Add-on zur Reaktionsverwaltung (Response Manager), mit dem Sie den Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen über alle Kommunikationskanäle hinweg messen können: E-Mail, Mobilgeräte, Briefpost usw.

## Hypothese {#hypothesis-concept}

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
