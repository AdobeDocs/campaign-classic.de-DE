---
product: campaign
title: Über die Reaktionsverwaltung
description: Über die Reaktionsverwaltung
feature: Campaigns
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 88%

---

# Erste Schritte mit Campaign Response Manager{#about-response-manager}



Adobe Campaign bietet ein Add-on zur Reaktionsverwaltung (Response Manager), mit dem Sie den Erfolg und die Rentabilität von Marketing-Kampagnen oder Angebotsvorschlägen über alle Kommunikationskanäle hinweg messen können: E-Mail, Mobilgeräte, Briefpost usw.

## Hypothese {#hypothesis-concept}

Um das Verhalten der Empfänger eines Angebots oder Versands vorherzusagen, können für einen bestimmten Zeitraum ab dem Kontaktdatum Hypothesen konfiguriert werden. Diese Hypothesen beziehen sich auf eine **Transaktionen**-Tabelle, in der Bestellungen und deren Details gespeichert werden.

Die Hypothesen sind zeitlich begrenzt und können auf eine Kontrollgruppe angewendet werden, um sie mit der Zielpopulation zu vergleichen. Hypothesenergebnisse werden bereitgestellt von **indicators** die nach Abschluss der Berechnung automatisch aktualisiert werden. Der den Hypothesen zugeordnete ROI wird in den Kampagnenberichten berücksichtigt.

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
