---
product: campaign
title: Grundprinzipien
description: Grundprinzipien
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: b13ecfc9-1723-42b2-ab30-d5637cc3d0dd
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 100%

---

# Grundprinzipien{#fundamental-principles}



## Umgebungsbereitstellung {#deploying-environments}

Für jede im Zusammenhang mit der Angebotsverwaltung verwendete Zieldimension existiert ein Umgebungspaar:

* eine Design-Umgebung, in der der Angebotsverantwortliche Angebote erstellt, ändert und kategorisiert sowie ihren Validierungsprozess auslöst, damit sie zum Einsatz kommen können. In dieser Umgebung werden darüber hinaus die für eine Kategorie geltenden Regeln, die Platzierungen, in denen die Angebote unterbreitet werden können und die für die Eignungsprüfung zu verwendenden Filter definiert.

  Kategorien können automatisch durch die Validierung oder manuell in der Live-Umgebung veröffentlicht werden.

  Die Vorgehensweise zum Validieren von Angeboten wird im Abschnitt [Angebotsvalidierung](../../interaction/using/approving-and-activating-an-offer.md) beschrieben.

* eine Live-Umgebung, in der die in der Design-Umgebung validierten bzw. definierten Angebote sowie die verschiedenen Platzierungen, Filter, Kategorien und Regeln zur Verfügung stehen. Bei einer Abfrage des Angebotsmoduls greift dieses ausschließlich auf die Angebote der Live-Umgebung zu.

Ein Angebot wird nur für die bei der Genehmigung ausgewählten Platzierungen bereitgestellt. Dies bedeutet, dass ein Angebot u. U. live sein kann, aber trotzdem nicht in einer Platzierung verwendet werden kann, selbst wenn diese ebenfalls live ist.

![](assets/architecture_interaction1.png)

## Interaktionstypen und Kontaktmodi {#interaction-types-and-contact-methods}

Es gibt zwei grundsätzliche Interaktionstypen: eingehende Interaktionen, die von einem Kontakt ausgelöst werden, und ausgehende Interaktionen, die durch den Angebotsersteller initiiert werden.

Diese beiden Interaktionstypen können entweder im Einzelmodus (Angebot wird für einen einzelnen Kontakt berechnet) oder im Batch-Modus (Angebot wird für eine Gruppe von Kontakten berechnet) durchgeführt werden. Im Allgemeinen werden eingehende Interaktionen im Einzelmodus durchgeführt und ausgehende Interaktionen im Batch-Modus. Es kann jedoch bestimmte Ausnahmen geben, beispielsweise bei Transaktionsnachrichten, bei denen die ausgehende Interaktion im einheitlichen Modus erfolgt (siehe [diesem Abschnitt](../../message-center/using/about-transactional-messaging.md)).

Wenn ein Angebot unterbreitet werden kann oder soll (je nach Konfiguration), spielt das Angebotsmodul eine zentrale Rolle: Es ermittelt automatisch aus einer Reihe von möglichen Angeboten das für den Kontakt am besten geeignete Angebot, indem es die für ihn vorliegenden Daten und die in der Anwendung definierten Regeln kombiniert und abgleicht.

![](assets/architecture_interaction2.png)
