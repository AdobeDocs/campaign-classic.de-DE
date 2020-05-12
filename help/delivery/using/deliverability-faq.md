---
title: Wichtige Aspekte bei der Verwaltung der Zustellbarkeit in Adobe Campaign Classic
description: Welche Hauptaspekte sind bei der Verwaltung der Zustellbarkeit in Adobe Campaign Classic zu beachten?
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
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 42%

---


# Fehlerbehebung bei der Bereitstellbarkeit{#deliverability-faq}

Haben Sie ein Problem mit der Lieferbarkeit? Die Lösung finden Sie hier.

## MX-Regelfehler {#mx-rule-error}

**Was bedeutet die Fehlermeldung &#39;quota met&#39;?**

Diese Meldung bedeutet, dass Sie das Limit für einen gewissen MX (Mail eXchanger) erreicht haben und warten müssen, bis Sie wieder eine E-Mail an diesen Anbieter senden können.

In Adobe Campaign gibt es eine Konfiguration bezüglich der Anzahl an E-Mails, die pro Stunde gesendet werden können. Bei dieser Konfiguration ist Vorsicht geboten, weil sich die in der Instanz definierte Anzahl nicht auf die Anzahl tatsächlich gesendeter E-Mails, sondern auf die mit den ISP erfolgten Verbindungen bezieht.

Das heißt, eine Verbindung kann sich einer MX-Regel bedienen, ohne dass der erfolgreiche Versand einer E-Mail erfolgt. In diesem Fall muss eine Konfiguration mit IP oder einer Domain von schwacher Reputation mehrere Verbindungen ausprobieren, bevor die E-Mail erfolgreich versendet wird. Bei jedem Versuch wird ein Guthaben vom Typ Nachrichten pro Stunde verbraucht. Dadurch wird die Leistung von Marketingkampagnen stark beeinflusst.

Daher ist &quot;erfüllte Quoten&quot; nicht nur eine Konfigurationsfrage, sondern kann auch mit dem Ruf verknüpft werden. It is important to analyze error messages in the [SMTP log](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

For more on MX configuration, see [this section](../../installation/using/email-deliverability.md#mx-configuration).

## Gleiche Fehlermeldung für einen ISP {#same-error-for-an-isp}

**Warum erhalte ich bei einem bestimmten ISP immer dieselbe Fehlermeldung?**

Wenn Sie bei einem ISP immer dieselbe Fehlermeldung erhalten, hat der ISP möglicherweise festgestellt, dass Ihre E-Mail- oder IP-Adresse fehlerhaft ist. Wir empfehlen in diesem Fall folgende Schritte:
* Prüfen Sie, ob Sie eine große Menge an Fehlschlägen in Verbindung mit nicht bestehenden E-Mail-Adressen erhalten (**Unbekannter Nutzer**).
* Aktualisieren Sie Ihre Anmeldeformulare und achten Sie auf etwaige Fehler im Domain-Namen (z. B. gmaul.com oder yaho.com).
* Wenn Fehlermeldungen auftreten, die Ihre E-Mails als Spam einstufen, oder wenn Ihre E-Mails blockiert werden, versuchen Sie, alle Empfänger auszuschließen, die innerhalb von 12 Monaten ab dem Versand ihre E-Mail nicht geöffnet oder darauf geklickt haben.

Wenn das Problem weiterhin besteht, wenden Sie sich an den kommerziellen oder den Bereitstellungsdienst, den Adobe Campaign Client Care oder den Adobe Campaign Support.

## Blacklisting versus Quarantäne {#blacklisting-versus-quarantine}

* **Was ist der Unterschied zwischen einer auf eine Blacklist gesetzten E-Mail-Adresse und einer unter Quarantäne gestellten E-Mail-Adresse?**

   * Der Status **[!UICONTROL Auf Blacklist]** ist das Ergebnis eines Feedback-Loops (wenn ein Empfänger eine E-Mail als Spam meldet).

   * Der Status **[!UICONTROL In Quarantäne]** ist das Ergebnis eines Soft- oder Hardbounce.
   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-blacklisting).

* **Was bedeuten die unterschiedlichen Gründe für Quarantäne-Fehler?**

   Es gibt zehn Gründe: Unbestimmt, Unbekannter Nutzer, Ungültige Domain, Adresse auf der Blacklist, Zurückgewiesen, Fehler ignoriert, Unerreichbar, Konto deaktiviert, Postfach voll, Nicht angemeldet.

   Weitere Informationen hierzu finden Sie unter [Funktionsweise der Quarantäneverwaltung](../../delivery/using/understanding-quarantine-management.md).

## Nicht schwarze Liste {#unblacklisting}

* **Einer meiner Empfänger wurde irrtümlich auf die Blacklist gesetzt. Wie lässt er sich daraus streichen, sodass ich ihm wieder Nachrichten senden kann?**

   * Gehen Sie zu **[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Adressen unzustellbarer Sendungen]**.
   * Setzen Sie in den Details des entsprechenden Datensatzes den Wert des **[!UICONTROL Status]**-Feldes auf **[!UICONTROL Gültig]**.
   * Speichern Sie die Daten.

* **Wie kann ich feststellen, ob eine meiner IP-Adressen auf einer Blacklist steht? Wie kann ich meine IP-Adresse wieder aus der Blacklist entfernen?**

   Sie können auf den folgenden Webseiten überprüfen, ob Ihre IP-Adresse auf einer Blacklist steht:
   * [https://mxtoolbox.com/](https://mxtoolbox.com/)
   * [https://whatismyipaddress.com/blacklist-check](https://whatismyipaddress.com/blacklist-check)
   * [https://www.blacklistalert.org/](https://www.blacklistalert.org/)
   Nach der IP-Adressen-Prüfung erhalten Sie eine Liste mit Details zur Blacklist und auch den Namen der Webseite, von der die IP-Adresse auf die Blacklist gesetzt wurde.

   Durch Klicken auf den entsprechenden Link können Sie auf die Website-Details zugreifen. Dann können Sie diese Webseite ersuchen, Ihre Webseite von der Blacklist zu löschen.

   >[!NOTE]
   >
   >Dieser Prozess ist je nach Webseite unterschiedlich. Auf manchen Webseiten müssen Sie ein Konto erstellen, während andere nur die Angabe der IP-Adresse verlangen.

## Best Practices {#best-practices}

Nachstehend finden Sie einige Best Practices, die Ihnen helfen können, Probleme mit der Lieferbarkeit zu identifizieren und zu beheben.

### Identifizieren Sie ein Bereitstellungsproblem. {#identify-deliverability-issue}

Die folgenden Punkte können Sie hervorheben:

* Mailing- oder Kampagnen-Metriken: Abmelden, Missbrauchsbeschwerden und/oder Absprungraten sind höher als üblich.
* Abonnenten-Aktivität: geöffnet werden, sind Klicks und/oder Transaktionen niedriger als gewöhnlich.
* Saatgutkonten zeigen gefilterte oder nicht zugestellte Postings an.

### Hypothetisches Potenzial verursacht {#potential-causes}

Stellen Sie sich die folgenden Fragen, um die möglichen Ursachen für Ihr Bereitstellungsproblem zu ermitteln:

* Gab es in letzter Zeit eine Änderung bei der Segmentierung der Liste?
* Habe ich neue Datenquellen erworben?
* Habe ich versehentlich eine Quarantäne geschickt?
* Könnte das Problem durch meinen Nachrichteninhalt verursacht werden?
* Kann ich so oft eine E-Mail versenden, dass warme IPs erhalten bleiben?
* Werde ich meine Mailings nach Aktivität/Interaktion segmentieren oder ganze Dateien senden?
* Was ist das &quot;sichere&quot;Segment in meiner Datei in Bezug auf die Aktualität?
* Verfüge ich über Reaktivierungs- und Bestätigungsstrategien für Segmente, die nicht als sicher definiert sind?

### Beheben Sie das Problem {#address-issue}

**Beschwerden**

Beschwerden werden von Abonnenten definiert, die E-Mails als Spam **** melden, indem sie auf die entsprechende Schaltfläche in ihrem Posteingang klicken.

Wenn Ihr Versand durch Beschwerden verursacht wurde:
* Sie müssen versuchen zu ermitteln, warum Empfänger sich beschweren.
* Sie können auch erwägen, den Link zum Abmelden an den Anfang Ihrer E-Mail zu verschieben. Dadurch werden die Abonnenten dazu angeregt, sich abzumelden, anstatt sich über die Spam-Schaltfläche zu beschweren.

Sender können aus ihren [Feedback-Schleife](../../delivery/using/technical-recommendations.md#feedback-loop) -Beschwerden eine Vielzahl von Informationen abrufen:
* Es ist wichtig, die Daten zu sammeln und nach Mustern in Dingen wie Opt-in-Quelle, wie lange die Adresse abonniert wurde oder sogar bestimmte Verhaltensdemographie zu suchen.
* Beschwerden können häufig eine riskante Datenquelle oder ein Segment in der Datei identifizieren. &quot;Risky&quot;wird als am wahrscheinlichsten zu beschweren definiert, was den Ruf schädigen kann und damit auch die Inbox-Rate.

Beschwerden stammen auch von Abonnenten, die einfach nicht mehr E-Mail erhalten möchten:
* Dies kann oft auf Übernachrichten, die Wahrnehmung der Nachricht durch Ihre Abonnenten, dass sie die Nachricht nicht erwartet haben oder sich nicht daran erinnern, sich zu beteiligen.
* Es ist auch wichtig, eine Prüfung durchzuführen, um sicherzustellen, dass alle Sammelstellen klar sind und dass keine Kontrollkästchen in den Akquise-Punkten vorhanden sind.
* Sie sollten auch eine Begrüßungs-E-Mail senden, wenn Abonnenten sich anmelden, um den Ton festzulegen und zu erklären, wie oft sie E-Mails von Ihnen erwarten können.

**Datengültigkeit**

**Eine feste Abgrenzung** tritt auf, wenn Sie an eine **nicht auslieferbare Adresse** eines ISP senden. Eine Adresse kann aus zahlreichen Gründen unauslöschbar sein, z. B.:
* Falsch geschriebene Adresse Dies kann mit einem Datenvalidierungsdienst in Echtzeit oder durch eine bestätigte Anmeldung behoben werden, bevor Marketing-E-Mails an diese Adresse gesendet werden.
* Fehlerhafte Liste oder Datenquelle. Wenn die Adresse aus einer neuen Quelle stammt, überprüfen Sie, wie die Adressen erfasst wurden, und stellen Sie sicher, dass die Berechtigung vorhanden ist.
* Versand an eine Adresse, die zu einem Zeitpunkt aktiv war, aber nach einer Inaktivität geschlossen oder beendet wurde.

**Interaktion**

Neben Beschwerden und Datenvalidität konzentrieren sich die ISPs mehr denn je auf **positive Bemühungen** , Entscheidungen über Versände zu treffen. Sie suchen danach, ob Ihre Abonnenten Ihre E-Mails öffnen oder löschen, ohne sie zu lesen. Da sie diese Daten nicht an Absender weitergeben, müssen wir die verfügbaren Informationen nutzen und open/clicks/transaction als Interaktion übersetzen.

Im Rahmen der laufenden Reputationssicherung ist es wichtig, zu verstehen, wie engagierte Abonnenten auf Ihrer Liste sind, und eine **Rangordnung** für die Abonnenten in jeder Datei zu entwickeln. Neuigkeit wird als letztes &quot;open/click/transact&quot;- oder &quot;sign-up&quot;-Datum definiert. Dieser Zeitrahmen kann sich vertikal unterscheiden. Gehen Sie dazu wie folgt vor:

1. Stellen Sie für jede Vertikale aktive Segmente (&quot;sichere&quot;Segmente fest. Dies sind typischerweise Abonnenten, die in den letzten 3-6 Monaten aktiv waren.
1. Verringerung der Häufigkeit von Inaktivitäten.
1. Erstellen Sie eine [Re-Interaktionsserie](../../delivery/using/re-engagement-best-practices.md) für mittelgradige Risikoinactive. In der Regel sind dies 6-9 Monate ohne Interaktion.
1. Entwickeln Sie eine Kampagne zur Bestätigung von Inaktives mit höherem Risiko. Dies sind typischerweise Abonnenten, die seit 9-12 Monaten keine E-Mail erhalten haben.
1. Legen Sie abschließend eine Dropdownregel fest und entfernen Sie Abonnenten, die Ihre E-Mails in &#39;x&#39; Monaten nicht geöffnet haben. Normalerweise empfehlen wir 12 Monate oder mehr, aber je nach Umsatz und Kaufzyklus kann dies unterschiedlich sein.
