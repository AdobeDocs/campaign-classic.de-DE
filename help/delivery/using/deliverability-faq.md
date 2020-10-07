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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1371'
ht-degree: 98%

---


# Behebung von Problemen bei der Zustellbarkeit{#deliverability-faq}

Haben Sie ein Problem mit der Zustellbarkeit? Möglicherweise finden Sie hier eine Lösung.

## MX-Regelfehler {#mx-rule-error}

**Was bedeutet die Fehlermeldung &quot;Kontingent ausgeschöpft&quot;?**

Diese Meldung bedeutet, dass Sie das Limit für einen gewissen MX (Mail eXchanger) erreicht haben und warten müssen, bis Sie wieder eine E-Mail an diesen Anbieter senden können.

In Adobe Campaign gibt es eine Konfiguration bezüglich der Anzahl an E-Mails, die pro Stunde gesendet werden können. Bei dieser Konfiguration ist Vorsicht geboten, weil sich die in der Instanz definierte Anzahl nicht auf die Anzahl tatsächlich gesendeter E-Mails, sondern auf die mit den ISP erfolgten Verbindungen bezieht.

Das heißt, eine Verbindung kann sich einer MX-Regel bedienen, ohne dass der erfolgreiche Versand einer E-Mail erfolgt. In diesem Fall muss eine Konfiguration mit IP oder einer Domain von schwacher Reputation mehrere Verbindungen ausprobieren, bevor die E-Mail erfolgreich versendet wird. Bei jedem Versuch wird ein Guthaben vom Typ &quot;Nachrichten pro Stunde&quot; verbraucht. Dadurch wird die Leistung von Marketingkampagnen stark beeinflusst.

Somit ist &quot;Kontingente ausgeschöpft&quot; nicht nur eine Frage der Konfiguration, sondern kann auch mit der Reputation zusammenhängen. Fehlermeldungen im [SMTP-Protokoll](../../production/using/monitoring-processes.md#smtp-errors-per-domain) sollten unbedingt analysiert werden.

Weiterführende Informationen zur MX-Konfiguration finden Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#mx-configuration).

## Gleiche Fehlermeldung bei einem ISP {#same-error-for-an-isp}

**Warum erhalte ich bei einem bestimmten ISP immer dieselbe Fehlermeldung?**

Wenn Sie bei einem ISP immer dieselbe Fehlermeldung erhalten, hat der ISP möglicherweise festgestellt, dass Ihre E-Mail- oder IP-Adresse fehlerhaft ist. Wir empfehlen in diesem Fall folgende Schritte:
* Prüfen Sie, ob Sie eine große Menge an Fehlschlägen in Verbindung mit nicht bestehenden E-Mail-Adressen erhalten (**Unbekannter Nutzer**).
* Aktualisieren Sie Ihre Anmeldeformulare und achten Sie auf etwaige Fehler im Domain-Namen (z. B. gmaul.com oder yaho.com).
* Wenn Fehlermeldungen auftreten, die Ihre E-Mails als Spam einstufen, oder wenn Ihre E-Mails blockiert werden, versuchen Sie, alle Empfänger auszuschließen, die innerhalb von 12 Monaten ab dem Versand ihre E-Mail nicht geöffnet oder darauf geklickt haben.

Wenn das Problem fortbesteht, kontaktieren Sie den Zustellbarkeitsservice oder die entsprechende Geschäftsabteilung, den Kundendienst von Adobe Campaign oder den Support von Adobe Campaign.

## Blockierungsliste versus Quarantäne {#block-list-versus-quarantine}

* **Was ist der Unterschied zwischen einer E-Mail-Adresse auf der Blockierungsliste und einer isolierten E-Mail-Adresse?**

   * Der Status **[!UICONTROL Auf Blockierungsliste]** ist das Ergebnis eines Feedback-Loops (wenn ein Empfänger eine E-Mail als Spam meldet).

   * Der Status **[!UICONTROL In Quarantäne]** ist das Ergebnis eines Soft- oder Hardbounce.
   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-block-list).

* **Was bedeuten die unterschiedlichen Gründe für Quarantäne-Fehler?**

   Es gibt zehn Gründe: Unbestimmt, Unbekannter Nutzer, Ungültige Domain, Adresse auf der Blockierungsliste, Zurückgewiesen, Fehler ignoriert, Unerreichbar, Konto deaktiviert, Postfach voll, Nicht angemeldet.

   Weitere Informationen hierzu finden Sie unter [Funktionsweise der Quarantäneverwaltung](../../delivery/using/understanding-quarantine-management.md).

## Aus Blockierungsliste entfernen {#remove-from-block-list}

* **Einer meiner Empfänger wurde versehentlich der Blockierungsliste hinzugefügt. Wie kann ich ihn aus der Blockierungsliste entfernen, damit ich ihm wieder Nachrichten senden kann?**

   * Gehen Sie zu **[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Adressen unzustellbarer Sendungen]**.
   * Setzen Sie in den Details des entsprechenden Datensatzes den Wert des **[!UICONTROL Status]**-Feldes auf **[!UICONTROL Gültig]**.
   * Speichern Sie die Daten.

* **Wie kann ich feststellen, ob eine meiner IP-Adressen auf einer Blockierungsliste steht? Wie kann ich meine IP-Adresse(n) wieder aus der Blockierungsliste entfernen?**

   Um zu überprüfen, ob Ihre IP-Adresse auf einer Blockierungsliste steht, können Sie verschiedene Websites verwenden, um sie zu überprüfen, z. B.:
   * [MX Toolbox](https://mxtoolbox.com/)
   * [Wie lautet meine IP-Adresse?](https://whatismyipaddress.com)

   Nach der IP-Adressen-Prüfung erhalten Sie eine Liste mit Details zur Blockierungsliste und auch den Namen der Website, von der die IP-Adresse auf die Blockierungsliste gesetzt wurde.

   Durch Anklicken des entsprechenden Links können Sie die Details der Website aufrufen. Dann können Sie diese Website ersuchen, Ihre Website von der Blockierungsliste zu löschen.

   >[!NOTE]
   >
   >Dieser Prozess ist je nach Website unterschiedlich. Auf manchen Websites müssen Sie ein Konto erstellen, während andere nur die Angabe der IP-Adresse verlangen.

## Best Practices {#best-practices}

Nachstehend finden Sie einige Best Practices, die Ihnen helfen können, Probleme mit der Zustellbarkeit zu erkennen und zu beheben.

### Ein Problem mit der Zustellbarkeit erkennen {#identify-deliverability-issue}

Achten Sie auf folgende Elemente:

* Mailing- oder Kampagnenmetriken: Abmeldungen, Beschwerden wegen Missbrauch und/oder ungewöhnlich hohe Bounce-Raten.
* Aktivitäten von Abonnenten: Öffnungen, Klicks und/oder Transaktionen sind niedriger als gewöhnlich.
* Testadresskonten zeigen gefilterte oder nicht zugestellte Mailings an.

### Mögliche Gründe ermitteln {#potential-causes}

Stellen Sie sich folgende Fragen, um die möglichen Ursachen für Ihr Zustellbarkeitsproblem zu ermitteln:

* Wurde die Listensegmentierung in letzter Zeit geändert?
* Sind neue Datenquellen dazugekommen?
* Habe ich versehentlich eine Datei, die in Quarantäne war, versendet?
* Hängt das Problem eventuell mit meinen Nachrichteninhalten zusammen?
* Sende ich oft genug, um Warming-IPs zu erhalten?
* Segmentiere ich meine Mailings nach Aktivität/Interaktion oder sende ich ganze Dateien?
* Was ist das &quot;sichere&quot; Segment in meiner Datei in Bezug auf Aktualität?
* Verfüge ich über Reaktivierungs- und Wiederbestätigungsstrategien für Segmente, die nicht als sicher definiert sind?

### Problem beheben {#address-issue}

**Beschwerden**

Beschwerden werden durch Abonnenten definiert, die **E-Mails als Spam melden**, indem sie in ihrem Posteingang auf die entsprechende Schaltfläche klicken.

Wenn Ihr Versandproblem durch Beschwerden verursacht wurde:
* Versuchen Sie herauszufinden, warum sich Empfänger beschweren.
* Sie können auch überlegen, den Link zum Abmelden an den Anfang Ihrer E-Mail zu verschieben. So werden Abonnenten dazu ermutigt, sich abzumelden, anstatt sich über die Spam-Schaltfläche zu beschweren.

Absender können aus ihren [Feedback Loop](../../delivery/using/technical-recommendations.md#feedback-loop) -Beschwerden eine Vielzahl von Daten sammeln:
* Diese Daten sollten erfasst und mit Blick auf Opt-in-Quelle, Länge des Abonnements der Adresse oder auch bestimmte Verhaltensdemografien nach Mustern durchsucht werden.
* Beschwerden weisen vielfach auf eine riskante Datenquelle oder ein riskantes Segment in der Datei hin. &quot;Riskant&quot; wird definiert als die höchste Beschwerdewahrscheinlichkeit, da Beschwerden den Ruf schädigen und so Posteingangsraten beeinträchtigen können.

Beschwerden stammen zum Teil auch von Abonnenten, die einfach keine E-Mails mehr erhalten möchten:
* Das kann an einer zu großen Anzahl von Nachrichten, der Wahrnehmung einer Nachricht durch Ihre Abonnenten oder daran liegen, dass sie die Nachricht nicht erwartet haben bzw. sich nicht mehr an die Anmeldung erinnern können.
* Außerdem sollten Sie eine Prüfung durchführen, um sicherzustellen, dass alle Sammlungspunkte klar und bei Ihren Akquisepunkten keine Kontrollkästchen aktiviert sind.
* Sie sollten auch eine Willkommens-E-Mail senden, wenn Abonnenten sich anmelden, um eine Einführung zu bieten und zu erklären, wie oft sie E-Mails von Ihnen erwarten können.

**Datengültigkeit**

**Hardbounces** treten auf, wenn Sie bei einem ISP an eine **nicht zustellbare Adresse** senden. Eine Adresse kann aus zahlreichen Gründen unzustellbar sein, z. B.:
* Falsch geschriebene Adresse. Das kann mit einem echtzeitbasierten Datenvalidierungsdienst oder durch Vorschreiben eines Opt-in mit Bestätigung behoben werden, bevor Marketing-E-Mails an diese Adresse gesendet werden.
* Fehlerhafte Liste oder Datenquelle. Wenn die Adresse aus einer neuen Quelle stammt, überprüfen Sie, wie sie erfasst wurde, und stellen Sie sicher, dass die entsprechende Berechtigung erteilt wurde.
* Senden an eine Adresse, die einmal aktiv war, aber nach einer gewissen Phase der Inaktivität geschlossen oder beendet wurde.

**Interaktion**

Neben Beschwerden und Datenvalidität konzentrieren sich ISPs bei Versandentscheidungen mehr denn je auf **positive Interaktion**. Sie versuchen herauszufinden, ob Abonnenten Ihre E-Mails öffnen oder aber löschen, ohne sie gelesen zu haben. Da sie diese Daten nicht mit den Absendern teilen, müssen wir die verfügbaren Daten nutzen und Öffnungen/Klicks/Transaktionen als Interaktion übersetzen.

Im Rahmen der laufenden Reputationssicherung ist es wichtig, zu verstehen, wie engagiert Abonnenten auf Ihrer Liste sind, und eine **Aktualitäts-Risikohierarchie** für die Abonnenten in jeder Datei zu erstellen. Neuigkeit wird als letztes Öffnungs-, Klick-, Transaktions- oder Anmeldedatum definiert. Dieser Zeitrahmen kann sich je nach Vertikale unterscheiden. Gehen Sie dazu wie folgt vor:

1. Bestimmen Sie für jede Vertikale aktive (&quot;sichere&quot;) Segmente. Das sind typischerweise Abonnenten, die in den letzten drei bis sechs Monaten aktiv waren.
1. Verringern Sie die Häufigkeit bei Inaktiven.
1. Erstellen Sie eine Serie zur [Rückgewinnung](../../delivery/using/re-engagement-best-practices.md) für Inaktive mit mittlerem Risiko. In der Regel sind dies Benutzer, die sechs bis neun Monate keine Interaktion gezeigt haben.
1. Entwickeln Sie eine Kampagne zur Wiederbestätigung für Inaktive mit höherem Risiko. Dies sind typischerweise Abonnenten, die seit neun bis zwölf Monaten nicht mehr mit einer E-Mail interagiert haben.
1. Legen Sie abschließend eine Ausschlussregel fest und entfernen Sie alle Abonnenten, die Ihre E-Mails seit &quot;x&quot; Monaten nicht mehr geöffnet haben. Normalerweise empfehlen wir zwölf Monate oder mehr, je nach Umsatz und Kaufzyklus können Sie jedoch einen anderen Wert wählen.
