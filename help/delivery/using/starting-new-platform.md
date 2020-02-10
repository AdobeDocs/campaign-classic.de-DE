---
title: Starten einer neuen Plattform mit Adobe Campaign Classic
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit beim Start einer neuen Plattform mit Adobe Campaign Classic.
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


# Einrichten einer neuen Plattform {#starting-new-platform}

Die Wahrung des Namens Ihrer Domäne und IP-Adresse ist unverzichtbar. Nachstehend finden Sie Ratschläge zum Einrichten einer neuen Plattform.

Mit dem Versand von E-Mails von einer neuen Plattform zu beginnen ist ein heikler Schritt, da die Plattform noch keinen Nutzungsverlauf und keine Reputation besitzt (sofern die Versand-IPs noch nie für diesen Zweck verwendet wurden). ISPs sind normalerweise misstrauisch gegenüber IP-Adressen, die noch nie für den E-Mail-Versand verwendet wurden und plötzlich große Mengen an E-Mails versenden. Spammer verwenden normalerweise &quot;unbekannte&quot; IP-Adressen (d. h. Adressen, die auf keiner Blacklist stehen), um eine möglichst große Menge an Nachrichten zu versenden, bevor sie entdeckt werden.

Erwarten Sie nicht, dass der Versand gleich zu Beginn der Produktionsphase in der gewünschten Geschwindigkeit durchgeführt werden kann. Sie sollten auch nicht versuchen, Nachrichten in dieser Geschwindigkeit zu versenden, da dies ISPs veranlassen könnte, die Absenderadresse zu blockieren, was die Anfangsphase erheblich beeinträchtigen würde.

Das Starten einer Plattform geschieht oft, wenn eine Liste von Adressen zum ersten Mal verwendet wird und die möglicherweise nicht vollständig qualifiziert sind. Wenn Sie an ungültige Adressen oder an Honeypot-Adressen senden, wird dies dazu beitragen, den Ruf der Plattform zu mindern. Wenn Sie eine Liste mit ungültigen Adressen haben, liegt es in Ihrem besten Interesse, diese in die Quarantänetabelle (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) zu importieren, bevor Sie sie zum ersten Mal senden. Wenn Sie dennoch die ungültigen Adressen rekalifizieren möchten, ist es bei weitem besser, dies zu tun, sobald der Ruf der Plattform etabliert ist, und nach und nach, um die Verwendung schlechter Adressen im Laufe der Zeit zu &quot;verwässern&quot;.

Zusammenfassend sollten Sie zu Projektbeginn diese Prinzipien befolgen:

* Importieren Sie ungültige Adressen in die Quarantänetabelle (sofern Sie über solche Informationen verfügen).
* Begrenzen Sie die Durchsatzrate (technische Einstellung: Begrenzung der Anzahl der MTA-Kindprozesse).
* Erhöhen Sie schrittweise das Versandvolumen: Versenden Sie nicht von Anfang an E-Mails an die gesamte Datenbank, sondern fügen Sie mit jedem Versand einen weiteren Teil der Liste hinzu. Dies ermöglicht Ihnen, das Volumen Schritt für Schritt zu erhöhen und gleichzeitig den Anteil an ungültigen Adressen zu verringern.
* Legen Sie einen regelmäßigen Versand fest: Es ist besser, regelmäßig kleine Sendungen vorzunehmen als selten große Kampagnen durchzuführen.
* Beachten Sie Versandberichte: Eine hohe Fehlerrate könnte auf eine falsche technische Konfiguration hinweisen.