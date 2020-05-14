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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a1192bc804e752d13af869da66ba0505c077ed19
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 17%

---


# Einrichten einer neuen Plattform {#starting-new-platform}

Die Wahrung des Namens Ihrer Domäne und IP-Adresse ist bei der Einrichtung einer neuen Plattform unverzichtbar.

* E-Mails zu senden ist ein sensibler Schritt, da die Plattform keine Nutzungsgeschichte hat und wenn die sendenden IPs zu diesem Zweck nie verwendet wurden, kein Ruf vorhanden ist.

* ISPs sind naturgemäß verdächtig gegenüber IP-Adressen, die nie zum Senden von E-Mails verwendet wurden und die plötzlich Beginn haben, um große Mengen E-Mail-Traffic zu senden. Tatsächlich verwenden Spammer im Allgemeinen &quot;unbekannte&quot;IP-Adressen (Adressen, die noch nie auf der Blacklist waren), um die größtmögliche Anzahl von Nachrichten vor der Erkennung zu senden.

* Erwarten Sie nicht, dass der Versand gleich zu Beginn der Produktionsphase in der gewünschten Geschwindigkeit durchgeführt werden kann. Sie sollten auch nicht versuchen, Nachrichten in dieser Geschwindigkeit zu versenden, da dies ISPs veranlassen könnte, die Absenderadresse zu blockieren, was die Anfangsphase erheblich beeinträchtigen würde.

Nachfolgend sind die wichtigsten Grundsätze aufgeführt, die beim Starten einer neuen Plattform befolgt werden müssen:

* Wenn Sie über diese Informationen verfügen, **importieren Sie ungültige Adressen in die Tabelle**Quarantäne.
Das Starten einer Plattform erfolgt oft, wenn eine Liste von Adressen zum ersten Mal verwendet wird und die möglicherweise nicht vollständig qualifiziert sind. Wenn Sie an ungültige Adressen oder an Honeypot-Adressen senden, wird dadurch der Ruf der Plattform verringert.

   * Wenn Sie über eine Liste ungültiger Adressen verfügen, ist es in Ihrem besten Interesse, diese in die Tabelle &quot;Quarantäne&quot;zu importieren (verfügbar über das Menü &quot; **[!UICONTROL Administration&quot;> &quot;Kampagnenverwaltung&quot;> &quot;Verwaltung nicht bereitgestellter Dateien&quot;> &quot;Nicht bereitgestellte Adressen]** &quot;), bevor Sie sie zum ersten Mal senden.
   * Wenn Sie dennoch die ungültigen Adressen rekalifizieren möchten, ist es bei weitem besser, dies zu tun, sobald der Ruf der Plattform etabliert ist, und nach und nach, um die Verwendung schlechter Adressen im Laufe der Zeit zu &quot;verwässern&quot;.
   Weitere Informationen hierzu finden Sie unter [Optimieren Ihres Versands durch Quarantänen](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Schränken Sie die Durchsatzrate** ein, indem Sie die Anzahl der Mtachilds begrenzen. Wenden Sie sich für weitere Informationen zum Anpassen dieser technischen Einstellung an Ihren Adobe Campaign-Administrator.
* **Erhöhen Sie die gesendeten** Volumes schrittweise, um nicht als Spam gekennzeichnet zu werden. Zielgruppe nicht die gesamte Datenbank vom Beginn, sondern fügen Sie bei jedem Senden einen zusätzlichen Bruchteil der Liste hinzu. Dies sollte es Ihnen ermöglichen, das Volumen bei jedem Schritt zu erhöhen und gleichzeitig die Gesamtrate ungültiger Adressen zu reduzieren. Um eine reibungslose Entwicklung der Beginn-up-Phase zu gewährleisten, können Sie Schübe verwenden. Weitere Informationen finden Sie unter [Senden mit mehreren Schüben](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Schick regelmäßig**. Bis zu einem gewissen Grad ist es besser, regelmäßig kleine Schüsse zu senden, anstatt große Kampagnen sporadisch.
* **Achte genau auf die Versandberichte**! Hohe Fehleranzeigen können bedeuten, dass eine technische Einstellung schlecht konfiguriert ist. Weiterführende Informationen dazu finden Sie unter [Sendungen beobachten](../../delivery/using/monitoring-a-delivery.md).

**Verwandte Themen**:
* [Erhöhen Sie Ihren Ruf als E-Mail mit IP-Erwärmung.](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Alles über Spam-Fallen](https://helpx.adobe.com/campaign/kb/spam-traps.html)