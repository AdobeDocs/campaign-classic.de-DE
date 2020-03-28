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
translation-type: ht
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Einrichten einer neuen Plattform {#starting-new-platform}

Die Wahrung der Reputation Ihrer Domain und IP-Adresse ist unverzichtbar. Nachstehend finden Sie Ratschläge zum Einrichten einer neuen Plattform.

Mit dem Versand von E-Mails von einer neuen Plattform zu beginnen ist ein heikler Schritt, da die Plattform noch keinen Nutzungsverlauf und keine Reputation besitzt (sofern die Versand-IPs noch nie für diesen Zweck verwendet wurden). ISPs sind normalerweise misstrauisch gegenüber IP-Adressen, die noch nie für den E-Mail-Versand verwendet wurden und plötzlich große Mengen an E-Mails versenden. Spammer verwenden normalerweise &quot;unbekannte&quot; IP-Adressen (d. h. Adressen, die auf keiner Blacklist stehen), um eine möglichst große Menge an Nachrichten zu versenden, bevor sie entdeckt werden.

Erwarten Sie nicht, dass der Versand gleich zu Beginn der Produktionsphase in der gewünschten Geschwindigkeit durchgeführt werden kann. Sie sollten auch nicht versuchen, Nachrichten in dieser Geschwindigkeit zu versenden, da dies ISPs veranlassen könnte, die Absenderadresse zu blockieren, was die Anfangsphase erheblich beeinträchtigen würde.

Bei der erstmaligen Nutzung einer Plattform ist die anfangs verwendete Adressliste möglicherweise fehlerhaft. Wenn Sie einen Versand an ungültige Adressen oder an eine Spam-Falle (honeypot) durchführen, schadet dies der Reputation Ihrer Plattform. Sollten Sie bereits über eine Liste ungültiger Adressen verfügen, importieren Sie diese daher vor dem ersten Versand in die Quarantänetabelle (**[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Adressen unzustellbarer Sendungen]**). Wenn Sie die ungültigen Adressen wieder aktivieren möchten, empfehlen wir, dies erst dann zu tun, wenn die Reputation der Plattform sichergestellt ist, und nur schrittweise, um die Verwendung ungültiger Adressen über einen längeren Zeitraum zu „verwässern“.

Zusammenfassend sollten Sie zu Projektbeginn diese Prinzipien befolgen:

* Importieren Sie ungültige Adressen in die Quarantänetabelle (sofern Sie über solche Informationen verfügen).
* Begrenzen Sie die Durchsatzrate (technische Einstellung: Begrenzung der Anzahl der MTA-Kindprozesse).
* Erhöhen Sie schrittweise das Versandvolumen: Versenden Sie nicht von Anfang an E-Mails an die gesamte Datenbank, sondern fügen Sie mit jedem Versand einen weiteren Teil der Liste hinzu. Dies ermöglicht Ihnen, das Volumen Schritt für Schritt zu erhöhen und gleichzeitig den Anteil an ungültigen Adressen zu verringern.
* Legen Sie einen regelmäßigen Versand fest: Es ist besser, regelmäßig kleine Sendungen vorzunehmen als selten große Kampagnen durchzuführen.
* Beachten Sie Versandberichte: Eine hohe Fehlerrate könnte auf eine falsche technische Konfiguration hinweisen.