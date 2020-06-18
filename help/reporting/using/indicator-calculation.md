---
title: Indikatorberechnung
seo-title: Indikatorberechnung
description: Indikatorberechnung
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5ebea30c743ab416ede879c74735e2c7870d3db9
workflow-type: tm+mt
source-wordcount: '3029'
ht-degree: 98%

---


# Indikatorberechnung {#indicator-calculation}

## Nutzer-Aktivitäten {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Öffnungen<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Summe aller @totalClicks, deren URL-Primärschlüssel gleich 1 ist.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Summe aller @totalClicks, deren URL-Typ gleich "E-Mail-Klick" ist.<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Summe aller @totalClicks, deren URL-Typ gleich "Transaktion" ist.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Der Nutzer-Aktivitäten-Bericht basiert auf der Tabelle **[!UICONTROL Konsolidiertes Tracking]** (nms:trackingStats). Diese Aggregat-Tabelle wird bei der Berichtanzeige aus Leistungsgründen anstelle der Tabelle **[!UICONTROL Trackinglogs der Empfänger]** (nms:trackingLogRcp) verwendet. Sie wird nicht in Echtzeit berechnet, sondern wenige Minuten nach Abruf der Trackinglogs erzeugt. Wenn die Indikatoren aktuell sind, sind die Ergebnisse mit denen der Indikatoren im Bericht **Trackingindikatoren** identisch. Die Kennzahl @totalclicks entspricht der Summe der Klicks über einen Zeitraum von 5 Minuten.

## Fehler und Bounces {#non-deliverables-and-bounces-1}

**Verteilung nach Fehlertyp**

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Versand- und Trackingstatistiken]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Anzahl verarbeiteter Nachrichten<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> Summe aller Nachrichten, deren Status "Vorbereitet", "Gesendet" oder "Fehlgeschlagen" ist.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Unbekannter Nutzer<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Unbekannter Nutzer". <br /> </td> 
   <td> Count(@status=2 und msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Unerreichbar <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Unerreichbar". <br /> </td> 
   <td> Count(@status=2 und msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Zurückgewiesen<br /> </td> 
   <td> @refused<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Abgelehnt". <br /> </td> 
   <td> Count(@status=2 und msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Ungültige Domain<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Ungültige Domain". <br /> </td> 
   <td> Count(@status=2 und msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Konto deaktiviert<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Konto deaktiviert".<br /> </td> 
   <td> Count(@status=2 und msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Postfach voll<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Postfach voll". <br /> </td> 
   <td> Count(@status=2 und msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Fehler<br /> </td> 
   <td> @value<br /> </td> 
   <td> Anzahl fehlgeschlagener Nachrichten mit diesem Fehlertyp.<br /> </td> 
   <td> Count(@status=2 und msg/@failureReason="Wert des Fehlertyps")<br /> </td> 
  </tr> 
  <tr> 
   <td> Beitrag<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der fehlerhaften Nachrichten diesen Typs in Bezug auf die Gesamtzahl der fehlerhaften Nachrichten.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Verteilung<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der fehlerhaften Nachrichten diesen Typs in Bezug auf die Gesamtzahl der zu verarbeiteten Nachrichten.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Verteilung nach Domain**

Der zweite Teil des Berichts zeigt die Verteilung der fehlgeschlagenen Nachrichten, und zwar nicht nach Fehlertyp, sondern nach Domain. In diesem Fall lautet die Formel für die Kennzahl **Fehler** (@value): Count(@status=2 und @domain=&quot;Wert des Domain-Namens&quot;). Gezählt werden also alle Nachrichten mit Status &quot;Fehlgeschlagen&quot; für die entsprechende Domain.

## Browser {#browsers-1}

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Browser-Statistiken]** (nms:userAgentsStats).

**Allgemeine Statistiken**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Besucher<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Gesamtzahl der Zielgruppenempfänger dieser Domain, die mindestens einmal in der betreffenden Nachricht geklickt haben.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Angesehene Seiten<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Gesamtzahl der Klicks auf Links in Sendungen unter Verwendung dieses Browsers, bezogen auf alle Sendungen.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> Nutzungsrate<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Besucher, die diesen Browser verwenden, im Vergleich zur Gesamt-Besucherzahl.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistiken nach Browsern**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nutzungsrate<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Tägliche Besucherrate des ausgewählten Browsers im Vergleich zur höchsten gemessenen Besucherzahl.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Gesamtanteil<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Besucher mit dieser Version im Vergleich zur Gesamt-Besucherzahl, bezogen auf alle Browser.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relativer Anteil<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Besucher mit dieser Version in Bezug auf die Gesamt-Besucherzahl, bezogen auf diesen Browser.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Teilen über soziale Netzwerke {#sharing-to-social-networks-1}

Dieser Bericht basiert auf den Tabellen **[!UICONTROL Versand]** (nms:delivery), **[!UICONTROL Konsolidiertes Tracking]** (nms:trackingStats) und **[!UICONTROL Webtracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Anzahl zu sendender Nachrichten<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Gesamtzahl der bei der Analyse verarbeiteten Nachrichten.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Erfolgreich gesendet<br /> </td> 
   <td> @success<br /> </td> 
   <td> Anzahl erfolgreich verarbeiteter Nachrichten <br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> E-Mail<br /> </td> 
   <td> @email<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "E-Mail".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Facebook" .<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Twitter" .<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> LinkedIn<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "linkedin" ist.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Teilungen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Anz. Teilungen<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Anzahl der in diesem sozialen Netzwerk geteilten Nachrichten.<br /> </td> 
   <td> Sum(iIf([url/@category]="Wert des sozialen Netzwerk-Typs",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Verteilung<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Prozentualer Anteil der Teilungen in diesem Netzwerk in Bezug auf die Gesamt-Teilungszahl.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Teilungsrate<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Prozentualer Anteil der Teilungen in diesem Netzwerk in Bezug auf die Gesamtzahl aller zu sendenden Nachrichten.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Öffnungen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Anz. Öffnungen <br /> </td> 
   <td> @open<br /> </td> 
   <td> Gesamtzahl der Trackingzeilen in der Webtracking-Tabelle.<br /> </td> 
   <td> Count<br /> </td> 
  </tr> 
  <tr> 
   <td> Verteilung<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Prozentualer Anteil der Öffnungen in diesem sozialen Netzwerk in Bezug auf die Gesamt-Öffnungszahl.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Öffnungsrate<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Anzahl der Öffnungen in diesem sozialen Netzwerk in Bezug auf die Gesamtzahl aller zu sendenden Nachrichten.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistiken zu Teilungsaktivitäten {#statistics-on-sharing-activities-1}

Dieser Bericht basiert auf den Tabellen **[!UICONTROL Versand]** (nms:delivery), **[!UICONTROL Konsolidiertes Tracking]** (nms:trackingStats) und **[!UICONTROL Webtracking]** (nms:webTrackingLog).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Neue Kontakte<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> Zählung der mit einem Empfänger verknüpften Besucher.<br /> </td> 
   <td> Formel: count(@id)<br /> Filter: @recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Öffnungen<br /> </td> 
   <td> @opened<br /> </td> 
   <td> Zählung aller @id mit URL-Typ "Öffnungen".<br /> </td> 
   <td> count(Iif([url/@type]=2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Teilungen<br /> </td> 
   <td> @shared<br /> </td> 
   <td> URL-Kategorie, die in 'email' , 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin' enthalten ist<br /> Anzahl aller @totalClicks mit einer URL-Kategorie, die 'email', 'facebook', 'twitter', 'delicious', 'digg', 'google' oder 'linkedin' entspricht.<br /> </td> 
   <td> count (Iif([url/@category] IN ('email' , 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Betriebssysteme {#operating-systems-1}

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Browser-Statistiken]** (nms:userAgentsStats).

**Allgemeine Statistiken**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Besucher<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> Durchschnittliche tägliche Anzahl von Zielgruppenempfängern nach Betriebssystem, die mindestens einmal im betreffenden Versand geklickt haben.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Angesehene Seiten<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Durchschnittliche tägliche Anzahl von Klicks auf Links in Sendungen nach Betriebssystem, bezogen auf alle Sendungen.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> Nutzungsrate<br /> </td> 
   <td> -<br /> </td> 
   <td> Verteilung der Besucher nach Betriebssystem in Bezug auf die Gesamt-Besucherzahl.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistiken nach Betriebssystem**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nutzungsrate<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> Tägliche Besucherrate mit diesem Betriebssystem in Bezug auf die höchste gemessene Besucherzahl.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Gesamtanteil<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Besucher nach Version, bezogen auf die Gesamt-Besucherzahl und auf alle Betriebssysteme.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relativer Anteil<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Besucher nach Version in Bezug auf die Gesamt-Besucherzahl mit diesem Betriebssystem.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Abonnement-Verfolgung {#subscription-tracking-1}

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Dienste]** (nms:service).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Angemeldet<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Zählung der Abonnenten am Vortag.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Abonnements <br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> Zählung der Anmeldungen (@action = 1) des Vortags.<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Abmeldungen<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> Zählung der Abmeldungen (@action = 0) des Vortags.<br /> </td> 
   <td> sum(Iif(@action = 0 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Entwicklung<br /> </td> 
   <td> -<br /> </td> 
   <td> Anzahl Anmeldungen abzüglich Abmeldungen. Der Prozentsatz in Klammern bezieht sich auf die Anzahl der Abonnenten insgesamt.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%)','')<br /> </td> 
  </tr> 
  <tr> 
   <td> Treue<br /> </td> 
   <td> -<br /> </td> 
   <td> Treuerate der Abonnenten über den entsprechenden Zeitraum.<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Trackingindikatoren {#tracking-indicators-1}

Dieser Bericht basiert auf den Tabellen **[!UICONTROL Versand- und Trackingstatistiken]** (nms:deliveryLogStats) und **[!UICONTROL Konsolidiertes Tracking]** (nms:trackingStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Zu sendende Nachrichten<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Zählung aller broadLogs nach der Zielgruppenanalyse.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Erfolg<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Zählung aller Nachrichten mit Feld "Testadresse" gleich "Nein" und Status "Vom Dienstleister berücksichtigt" oder "Gesendet" oder "Auf Mobiltelefon erhalten".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens der erreichten Population<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Hochrechnung der Zahl unterschiedlicher Öffnungen aller E-Mails ausgehend von der Zahl der Öffnungen der E-Mails im HTML-Format.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Summe der Öffnungen der erreichten Population<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Hochrechnung der Gesamt-Öffnungsanzahl aller E-Mails ausgehend von der Gesamt-Öffnungsanzahl der E-Mails im HTML-Format.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks auf den Abmelde-Link<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Zählung aller @id mit URL-Kategorie "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks auf den Mirrorseite-Link<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Zählung aller @id mit URL-Kategorie "Mirrorseite".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Schätzung der Weiterleitungen<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Differenz aus der Anzahl unterschiedlicher Personen und unterschiedlicher Empfänger, die mindestens einmal in der E-Mail-geklickt haben.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Sendungen<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Zählung aller Nachrichten mit Feld "Testadresse" gleich "Nein" und Status "Vom Dienstleister berücksichtigt" oder "Gesendet" oder "Auf Mobiltelefon erhalten".<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Beschwerden<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> Anzahl der Nachrichten mit dem Status "Fehlgeschlagen"und dem Grund "Zur blockierungsliste hinzugefügt".<br /> </td> 
   <td> Count(@status=2 und msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Öffnungen<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Zählung aller @broadLog-id in allen Trackinglogs.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Zählung aller unterschiedlichen @broadLog-id mit URL-Typ "E-Mail-Klick". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Brutto-Reaktionsrate<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Empfänger, die mindestens einmal im betreffenden Versand geklickt haben, in Bezug auf die geschätzte Anzahl der Empfänger, die mindestens einmal den betreffenden Versand geöffnet haben.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Unique Clicks der erreichten Population<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Zählung aller @source-id mit URL-Kategorie "E-Mail-Klick".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks insgesamt<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Zählung aller @id mit URL-Kategorie "E-Mail-Klick".<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Empfänger-Klicks<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> Zählung aller unterschiedlichen @broadLog-id mit URL-Typ "E-Mail-Klick".<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Geschätzte Reaktionsrate<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Zielgruppenempfänger, die mindestens einmal im betreffenden Versand geklickt haben, in Bezug auf die geschätzte Anzahl der Zielgruppenempfänger, die mindestens einmal den betreffenden Versand geöffnet haben.<br /> </td> 
   <td> percent(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Besuchte Seiten<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Zählung aller @id mit URL-Typ "Web" oder "Transaktion".<br /> </td> 
   <td> count(Iif([url/@type]=4 oder [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Zählung aller @id mit URL-Typ "Transaktion".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Gesamtumsatz<br /> </td> 
   <td> @amount<br /> </td> 
   <td> Summe der webTrackingLog/@amounts, deren URL-Typ gleich „Transaktion“ ist.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Durchschnittlicher Transaktionsbetrag<br /> </td> 
   <td> -<br /> </td> 
   <td> Quotient aus Gesamtumsatz und Transaktionsanzahl.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Artikel<br /> </td> 
   <td> @article<br /> </td> 
   <td> Summe der webTrackingLog/@article, deren URL-Typ gleich "Transaktion" ist.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Durchschnittliche Artikelanzahl pro Transaktion<br /> </td> 
   <td> -<br /> </td> 
   <td> Quotient aus Artikelanzahl und Transaktionsanzahl.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Durchschnittlicher Transaktionsbetrag pro Nachricht<br /> </td> 
   <td> -<br /> </td> 
   <td> Quotient aus Gesamtumsatz und Gesamtzahl zu sendender Nachrichten.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> E-Mail<br /> </td> 
   <td> @email<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "E-Mail".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Delicious".<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "Google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> LinkedIn<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Summe aller @totalClicks mit URL-Kategorie "LinkedIn" ist.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URLs und Clickstreams {#urls-and-click-streams-1}

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Versand]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reaktionsrate<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Prozentualer Anteil der Zielgruppenempfänger, die mindestens einmal im betreffenden Versand geklickt haben, in Bezug auf die geschätzte Anzahl der Zielgruppenempfänger, die mindestens einmal den betreffenden Versand geöffnet haben.<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Unterschiedliche Klicks (Unique Clicks)<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> Prozentualer Anteil der unterschiedlichen Personen, die mindestens einmal im betreffenden Versand geklickt haben, in Bezug auf die Gesamtzahl erfolgreich zugestellter Nachrichten.<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks insgesamt<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Prozentualer Anteil der Klicks von Zielgruppenempfängern in Bezug auf die erfolgreich zugestellten Nachrichten.<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Zählung aller @totalClicks mit URL-Primärschlüssel ungleich 1.<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks (in %)<br /> </td> 
   <td> -<br /> </td> 
   <td> Prozentualer Anteil der Klicks in Bezug auf die Gesamt-Klickanzahl.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Versandzusammenfassung {#delivery-summary-1}

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Versand]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Ursprungspopulation<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Gesamtzahl der Empfänger, die den Versand erhalten sollen.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Durch eine Regel zurückgewiesene Nachrichten<br /> </td> 
   <td> @reject<br /> </td> 
   <td> Number of addresses ignored during the analysis in keeping with typology rules: address not specified, quarantined, added to the block list, etc.<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> Zu sendende Nachrichten<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Gesamtzahl der nach erfolgter Versandanalyse zu versendenden Nachrichten.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Erfolg<br /> </td> 
   <td> @success<br /> </td> 
   <td> Anzahl erfolgreich verarbeiteter Nachrichten.<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Fehler<br /> </td> 
   <td> @error<br /> </td> 
   <td> Gesamtzahl an Fehlern in Sendungen und der automatischen Bounce-Verarbeitung.<br /> </td> 
   <td> sum([indicators/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> Neu in Quarantäne<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Anzahl der Adressen, die infolge eines fehlgeschlagenen Zustellversuchs unter Quarantäne gestellt wurden (unbekannter Nutzer, ungültige Domain).<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Klicks {#hot-clicks-1}

Dieser Bericht basiert auf den Tabellen **[!UICONTROL Versand]** (nms:delivery) und Konsolidiertes Tracking (nms:trackingStats).

Er zeigt den Nachrichteninhalt (HTML und/oder Text) mit dem prozentualen Klickanteil für jeden Link. Links in Gestaltungsbausteinen, der Abmelde-Link sowie der Mirrorseite-Link werden in der Gesamtklickzahl berücksichtigt, in diesem Bericht jedoch nicht angezeigt.

## Trackingstatistiken {#tracking-statistics-1}

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Versand]** (nms:delivery).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transactions<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Summe aller @totalClicks, deren URL-Typ gleich "Transaktion" ist.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> Summe aller @totalClicks, deren URL-Typ gleich "E-Mail-Klick" ist.<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Öffnungen<br /> </td> 
   <td> @opens<br /> </td> 
   <td> Summe aller @totalClicks, deren URL-Primärschlüssel gleich 1 ist.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Versandstatistiken {#delivery-statistics-1}

Dieser Bericht basiert auf der Tabelle **[!UICONTROL Versand- und Trackingstatistiken]** (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Verarbeitete E-Mails<br /> </td> 
   <td> @processed<br /> </td> 
   <td> Summe aller Nachrichten, deren Status gleich "Vorbereitet", "Gesendet" oder "Fehlgeschlagen" ist.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Zugestellt<br /> </td> 
   <td> @success<br /> </td> 
   <td> Anzahl erfolgreich verarbeiteter Nachrichten.<br /> </td> 
   <td> indicators/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Hardbounces<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Unbekannter Nutzer".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Softbounces<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Zählung aller Nachrichten mit Status "Fehlgeschlagen" und Grund "Unerreichbar", "Postfach voll", "Ungültige Domain", "Konto deaktiviert", "Nicht angemeldet" oder "Abgelehnt".<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> Öffnungen<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> Zählung aller @broadLog-id in allen Trackinglogs.<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klicks<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Zählung aller @source-id mit URL-Kategorie "E-Mail-Klick". <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Abmeldungen<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Zählung aller @id mit URL-Kategorie "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Öffnungsverteilung {#breakdown-of-opens-1}

Dieser Bericht basiert auf den **Versand-** und **Trackinglog-** Tabellen (nms:delivery bzw. nms:trackingLogRcp).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Titel</strong> <br /> </th> 
   <th> <strong>Feldname</strong> <br /> </th> 
   <th> <strong>Beschreibung des Indikators</strong> <br /> </th> 
   <th> <strong>Formel zur Indikatorberechnung</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Öffnungen<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> Summe aller @id, deren URL-Primärschlüssel gleich 1 ist (Öffnung). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Andere Indikatoren {#other-indicators}

Der über den Knoten **Sendungen(nms:delivery)>Indikatoren** zugängliche Indikator **Gesendet** (@sent) entspricht der Gesamtanzahl der an den Dienstleister gesendeten SMS. Dieser Indikator wird ausschliesslich für SMS-Sendungen verwendet und darf nicht für andere Versandtypen genutzt werden. Er ist nicht zu verwechseln mit den Indikatoren **@success** und **@processed**.

## Indikatoren synchronisieren {#indicator-synchronization}

Falls Sie Abweichungen oder Inkohärenzen in gewissen Indikatoren bemerken, können Sie manuell eine Synchronisation durchführen. Markieren Sie im Adobe-Campaign-Explorer den entsprechenden Versand, klicken Sie mit der rechten Maustaste und wählen Sie die Option **[!UICONTROL Aktionen > Sende- und Berichtindikatoren neu berechnen...]**. Klicken Sie auf **[!UICONTROL Weiter]** und schließlich auf **[!UICONTROL Beenden]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Öffnungstracking {#tracking-opens-}

Damit Adobe Campaign die Öffnung einer Nachricht erkennen kann, muss der Empfänger die Bilder der E-Mail herunterladen. HTML- und Multipart/Alternative-E-Mails enthalten ein Bild mit 0 Pixeln, welches das Öffnungstracking ermöglicht, sobald es angezeigt wird. Nachrichten im Textformat enthalten kein Bild, das Öffnungstracking ist daher nicht möglich. In Bezug auf Öffnungen berechnete Werte sind immer nur Schätzungen. Dies hängt insbesondere mit der durch den Aufruf von Bildern bedingten Fehlerquote zusammen.

## Unterschied zwischen Personen und Zielgruppenempfängern {#targeted-persons---recipients}

Adobe Campaign unterscheidet in den Statistiken gewisser Berichte zwischen Personen und Zielgruppenempfängern.

Zielgruppenempfänger sind die Kontakte, an die der Versand ursprünglich gesendet wurde.

Die Personenanzahl bezeichnet die Zielgruppenempfänger zuzüglich aller Personen, an die die E-Mail weitergeleitet wurde. Jedes Mal, wenn eine Öffnung oder ein Klick in einem neuen Browser erfolgt, d. h. in einem Browser, in dem die Nachricht noch nie geöffnet wurde, wird eine neue Person gezählt.

Wenn Sie beispielsweise eine mit Adobe Campaign gesendete E-Mail erhalten, sie öffnen und darin klicken, werden Sie als Zielgruppenempfänger gezählt (d. h. Empfänger=1, Person=1). Wenn Sie nun die E-Mail an zwei Freunde weiterleiten und diese in die E-Mail klicken oder sie im Browser öffnen, bleibt die Zahl der Zielgruppenempfänger bei eins, die Zahl der Personen jedoch steigt auf drei. Der Wert 3 entspricht also jeder Öffnung/jedem Klick in einem anderen Browser.
