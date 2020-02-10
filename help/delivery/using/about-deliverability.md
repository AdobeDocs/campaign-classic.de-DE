---
title: Informationen zur Lieferbarkeit in Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Über die Zustellbarkeit{#about-deliverability}

Adobe Campaign bietet eine Reihe von Tools zur Verfolgung der Leistung Ihrer Plattform im Hinblick auf die Bereitstellung. In diesem Abschnitt werden auch die wichtigsten Grundsätze hervorgehoben, die Sie bei der Verwaltung und Optimierung der Zustellbarkeit beachten sollten.

## Konfiguration {#configuration}

Diese Funktion ist über ein dediziertes Paket in Adobe Campaign verfügbar. Um es zu verwenden, muss dieses Paket installiert sein. Starten Sie nach Abschluss des Vorgangs den Server neu, damit das Paket berücksichtigt wird.
* Bei gehosteten und hybriden Clients wird die **Überwachung** der Auslieferbarkeit auf Ihrer Instanz vom technischen Support und von Beratern von Adobe konfiguriert. Weitere Informationen erhalten Sie von Ihrem Adobe-Kundenbetreuer.

* Bei lokalen Installationen müssen Sie das **[!UICONTROL Deliverability monitoring (Email Deliverability)]** Paket über das Menü **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** installieren. Weitere Informationen hierzu finden Sie unter [Installieren der Standardpakete](../../installation/using/installing-campaign-standard-packages.md)von Campaign Classic.

In Adobe Campaign Classic wird die **Überwachung** der Auslieferbarkeit vom **[!UICONTROL Refresh for deliverability]** Workflow verwaltet. Es wird standardmäßig auf allen Instanzen installiert und ermöglicht es Ihnen, die Liste der Regeln für die Absprung-E-Mail-Qualifizierung, die Liste der Domänen und die Liste der MXs zu initialisieren. Sobald das **[!UICONTROL Deliverability monitoring (Email Deliverability)]** Paket installiert ist, wird dieser Arbeitsablauf jeden Abend ausgeführt, um die Regelliste regelmäßig zu aktualisieren und Sie können die Plattformbereitstellung aktiv verwalten.

## Hintergrund {#background}

Die Zustellbarkeit von E-Mails stellt eine große Herausforderung für Marketingspezialisten dar – egal, ob sie ein paar tausend Nachrichten oder mehrere Milliarden senden. Jede fünfte Nachricht erreicht nie den Posteingang oder den gewünschten Empfänger.

Einst als &quot;technisches Problem&quot; abgetan und der IT-Abteilung überlassen, wird heute im Marketing immer stärkeres Augenmerk auf die E-Mail-Zustellbarkeit gelegt. Clevere Marketer haben nämlich erkannt, dass zwar viele Aspekte technischer Natur sind, Zustellbarkeit aber letztlich ein geschäftliches Problem ist, das bedeutende Auswirkungen auf die Umsatzzahlen hat.

Betrachten wir einmal den E-Mail-Marketing-Trichter. Die Zustellbarkeit bezeichnet die Anzahl der empfangenen Nachrichten, die sich wiederum auf jede darauf folgende Phase des Trichters auswirkt. Wenn weniger E-Mails empfangen werden, werden weniger geöffnet, weniger angeklickt und weniger Konversionen erzielt. **Für Unternehmen mit einer großen Datenbank könnte die Differenz zwischen einer durchschnittlichen und einer hervorragenden Zustellbarkeit hunderttausende bis Millionen von Dollar Umsatz bedeuten.**

![](assets/deliverability_overview_1.png)

Wenn sich Marketer mit einer durchschnittlichen Zustellbarkeit (80 %) zufrieden geben, verzichten sie auf eine enorme Menge von Konversionen – und Einnahmen.

Was genau ist E-Mail-Zustellbarkeit? Und wie können Marketer die Zustellbarkeitsraten steigern, um den Trichtermund zu vergrößern und aus ihren E-Mail-Kampagnen höhere Gewinne zu erzielen?

Die Zustellbarkeit von E-Mails hängt von verschiedenen Faktoren ab, die bestimmen, ob eine Nachricht innerhalb kurzer Zeit über eine persönliche E-Mail-Adresse ihr Ziel in der erwarteten Qualität bezüglich Inhalt und Format erreicht. Diese Faktoren können in vier Bereiche zusammengefasst werden: Datenqualität, Nachricht und Inhalt, Versandinfrastruktur und Reputation. Gemeinsam bilden sie die Grundlage für ein erfolgreiches E-Mail-Zustellprogramm. Im Folgenden werden diese vier Grundelemente erläutert und Best Practices beschrieben, mit denen sichergestellt werden kann, dass E-Mails den gewünschten Posteingang erreichen und E-Mail-Marketing-Programme profitabel sind.

![](assets/deliverability_overview_2.png)
