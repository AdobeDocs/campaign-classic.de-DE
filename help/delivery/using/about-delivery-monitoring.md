---
product: campaign
title: Erste Schritte bei der Überwachung eines Versands
description: Erfahren Sie mehr über die Funktionen zur Überwachung eines Versands in Campaign Classic
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 100%

---

# Erste Schritte bei der Überwachung eines Versands {#about-delivery-monitoring}

Die Überwachung Ihrer Sendungen nach deren Versand ist ein wichtiger Schritt, um sicherzustellen, dass Ihre Marketing-Kampagnen effizient sind und Ihre Kunden erreichen.

In diesem Abschnitt erfahren Sie mehr über die Informationen, die Sie nach einem Versand überwachen können, sowie darüber, wie fehlgeschlagene Sendungen und Quarantänen verwaltet werden.

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Sendungen überwachen**

Mit der Versandliste können Sie alle erstellten Sendungen an einem Ort anzeigen.

Für jeden Versand steht ein eigenes Dashboard zur Verfügung. Sie können damit eventuelle Probleme während des Versands sowie verschiedene Arten von Informationen zum Versand überwachen: Berichte, Mirrorseiten, Ausschlüsse, Trackinglogs, Rendering usw.

* [Auf die Versandliste zugreifen](list-of-deliveries.md)
* [Versand-Dashboard](delivery-dashboard.md)

<img src="assets/do-not-localize/icon_guidelines.svg" width="60px">

**Versand-Performance sicherstellen**

Sie sollten einige Richtlinien befolgen, um sicherzustellen, dass Ihre Sendungen gut funktionieren. Informationen zu häufigen Problemen, die bei Sendungen auftreten können, sind ebenfalls verfügbar, damit Sie Ihre Sendungen effizient ausführen können.

* [Versand-Performance und Best Practices](delivery-performances.md)
* [Fehlerbehebung beim Versand](delivery-troubleshooting.md)

<img src="assets/do-not-localize/icon_failure.svg" width="60px">

**Fehlgeschlagene Sendungen**

Wenn einem Profil eine Nachricht nicht zugestellt werden kann, sendet der Remote-Server automatisch eine Fehlermeldung, die von der Adobe Campaign-Plattform erfasst und ausgewertet wird, um festzustellen, ob die E-Mail-Adresse oder Telefonnummer unter Quarantäne gestellt werden soll.

[Fehlgeschlagene Sendungen zu verstehen](understanding-delivery-failures.md) ist wichtig, um Ihre Marketing-Kampagnen zu verbessern.

<img src="assets/do-not-localize/icon_quarantine.svg" width="60px">

**Funktionsweise der Quarantäneverwaltung**

Adobe Campaign verwaltet eine Liste von unter Quarantäne gestellten Adressen. Empfänger, deren Adressen unter Quarantäne gestellt wurden, werden bei der Versandanalyse standardmäßig ausgeschlossen und gehören nicht zur Zielgruppe.

In [diesem Abschnitt](understanding-quarantine-management.md) finden Sie Informationen zum Identifizieren und Verwalten von unter Quarantäne stehenden Adressen und erhalten weitere Informationen über die Bedingungen, die erfüllt werden müssen, um eine Adresse unter Quarantäne zu stellen.
