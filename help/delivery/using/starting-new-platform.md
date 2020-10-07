---
title: Einrichten einer neuen Plattform mit Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit beim Einrichten einer neuen Plattform mit Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 94%

---


# Einrichten einer neuen Plattform {#starting-new-platform}

Bei der Einrichtung einer neuen Plattform ist die Wahrung der Reputation Ihrer Domain sowie Ihrer IP-Adressen überaus wichtig.

* Der Versand von E-Mails ist ein heikler Schritt, da die Plattform keine Nutzungsgeschichte und – wenn die sendenden IPs zu diesem Zweck noch nie verwendet wurden – auch keine Reputation aufweist.

* ISPs sind naturgemäß argwöhnisch gegenüber IP-Adressen, die noch nie zum Senden von E-Mails verwendet wurden und plötzlich große Mengen von E-Mail-Traffic verursachen. Tatsächlich verwenden Spammer in der Regel &quot;unbekannte&quot;IP-Adressen (Adressen, die einer Blockierungsliste noch nie hinzugefügt wurden), um die größtmögliche Anzahl von Nachrichten vor der Erkennung zu senden.

* Erwarten Sie nicht, dass der Versand gleich zu Beginn der Produktionsphase in der gewünschten Geschwindigkeit durchgeführt werden kann. Sie sollten auch nicht versuchen, Nachrichten in dieser Geschwindigkeit zu versenden, da dies ISPs veranlassen könnte, die Absenderadresse zu blockieren, was die Anfangsphase erheblich beeinträchtigen würde.

Nachfolgend sind die wichtigsten Grundsätze aufgeführt, die Sie beim Start einer neuen Plattform beachten müssen:

* Wenn Sie über solche Daten verfügen, **importieren Sie ungültige Adressen in die Quarantänetabelle**.
Oft werden Plattformen gestartet, wenn eine Adressliste zum ersten Mal verwendet wird; diese ist möglicherweise nicht vollständig qualifiziert. Wenn Sie an ungültige Adressen oder Honeypot-Adressen senden, verschlechtert sich die Reputation der Plattform.

   * Wenn Sie über eine Liste ungültiger Adressen verfügen, ist es in Ihrem Interesse, diese in die Quarantänetabelle zu importieren (über das Menü **[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Adressen unzustellbarer Sendungen]**), bevor Sie zum ersten Mal senden.
   * Wenn Sie die ungültigen Adressen trotzdem erneut qualifizieren möchten, ist es viel besser, dies zu tun, sobald die Reputation der Plattform etabliert ist – und zwar nach und nach, um die Verwendung schlechter Adressen im Laufe der Zeit zu &quot;verwässern&quot;.

   Weiterführende Informationen hierzu finden Sie unter [Optimieren Ihres Versands durch Quarantänen](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Begrenzen Sie die Durchsatzrate**, indem Sie die Anzahl der &quot;mtachilds&quot; einschränken. Wenden Sie sich für weitere Informationen zum Anpassen dieser technischen Einstellung an Ihren Adobe Campaign-Administrator.
* **Erhöhen Sie die gesendeten Volumen schrittweise**, damit diese nicht als Spam gekennzeichnet werden. Senden Sie nicht gleich an die gesamte Datenbank, sondern fügen Sie bei jedem Senden einen weiteren Anteil der Liste hinzu. So sollten Sie das Volumen bei jedem Schritt erhöhen und gleichzeitig die Gesamtrate ungültiger Adressen reduzieren können. Um eine reibungslose Anfangsphase zu gewährleisten, können Sie Schübe verwenden. Weiterführende Informationen finden Sie unter [In mehreren Schüben versenden](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Senden Sie regelmäßig**. Es ist besser, regelmäßig kleine Sendungen vorzunehmen als selten große Kampagnen durchzuführen.
* **Beachten Sie dabei die Versandberichte**. Hohe Fehlerindikatoren können darauf hindeuten, dass eine technische Einstellung nicht richtig konfiguriert ist. Weiterführende Informationen dazu finden Sie unter [Sendungen beobachten](../../delivery/using/monitoring-a-delivery.md).

**Verwandte Themen**:
* [E-Mail-Reputation mit IP-Warming verbessern](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Alles über Spam-Fallen](https://helpx.adobe.com/campaign/kb/spam-traps.html)