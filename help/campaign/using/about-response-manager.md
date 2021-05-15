---
solution: Campaign Classic
product: campaign
title: Über die Reaktionsverwaltung
description: Über die Reaktionsverwaltung
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: dc3151a77350aa2b2acd989a57f5b489c1a98962
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 91%

---

# Erste Schritte mit der Kampagne Reaktionsverwaltung{#about-response-manager}

Adobe Campaign Angebot bietet ein Antwortmanagement-Add-On, mit dem Sie den Erfolg und die Rentabilität von Marketing-Kampagnen oder -Angebotsvorschlägen in KommunikationsKanälen messen können: E-Mail, Mobil, Direktwerbung usw.

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

Lesen Sie vor der Nutzung von Response Manager den Abschnitt [Konfiguration](../../campaign/using/configuration.md) und nehmen Sie die notwendigen Einstellungen vor.

Bevor eine Hypothese über einen Versand oder ein Angebot gestartet werden kann, muss zunächst ihr Kontext in einer Vorlage bestimmt werden, auf welcher die Hypothese anschließend beruht.

Um Messhypothesen zu definieren und zu messen, gehen Sie also wie folgt vor:

1. Erstellen Sie eine Hypothesenvorlage. Siehe [Hypothesevorlage erstellen](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model).
1. Stellen Sie eine oder mehrere Hypothesen über einen bestehenden Versand auf. Siehe [Referenzieren einer Hypothese im Versand einer Kampagne](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery).

   oder

   Stellen Sie eine oder mehrere Hypothesen über Angebote auf. Siehe [Angebotshypothese erstellen](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer).

1. Überprüfen Sie die Ergebnisse der Hypothesen. Siehe [Hypothesenverfolgung](../../campaign/using/hypothesis-tracking.md).
1. Starten Sie Hypothesen bei Bedarf neu. Siehe [Erstellen einer Hypothese direkt in einem Versand](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery).
