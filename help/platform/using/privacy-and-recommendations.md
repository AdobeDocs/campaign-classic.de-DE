---
title: Datenschutz und Empfehlungen
seo-title: Datenschutz und Empfehlungen
description: Datenschutz und Empfehlungen
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ed5390b4f620c3cddaf9b856f3354dc5f06f4d98

---


# Datenschutz und Empfehlungen{#privacy-and-recommendations}

## Über Datenschutz und Einverständniserklärung {#about-privacy-and-consent}

Adobe Campaign bietet leistungsstarke Möglichkeiten der Datenerhebung und ‑verarbeitung, einschließlich personenbezogener Daten. Wir erwarten von allen Adobe Campaign-Anwendern, dass sie sich an die geltenden gesetzlichen Vorschriften (DPA, CAN-SPAM, die EU-Datenschutzrichtlinie für die elektronische Kommunikation, die EU-DSGVO usw.) halten und die Nutzungsbedingungen hinsichtlich des Datenschutzes und der Unterlassung unerwünschter kommerzieller E-Mails, Push-Benachrichtigungen oder SMS (&quot;Spam&quot;) strikt beachten. Wir sind davon überzeugt, dass autorisiertes Direktmarketing die Basis für eine vertrauensvolle, dauerhafte und rentable Kundenbeziehung darstellt. Eine Verwendung der Adobe Campaign-Software für den Versand unerwünschter Nachrichten ist somit strengstens untersagt.

Weiterführende Informationen finden Sie in den [Datenschutzbestimmungen von Adobe Experience Cloud](https://www.adobe.com/privacy/marketing-cloud.html).

Adobe Campaign bietet die verfügbaren Tools und Funktionen sowie Best Practices, die Ihnen helfen, die DSGVO bei der Nutzung unseres Dienstes einzuhalten. Weitere Informationen hierzu finden Sie in [diesem Dokument](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html).

Lesen Sie auch die [Checkliste zu Sicherheit und Datenschutz](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), um sich über die wichtigsten Elemente zu informieren, die in Bezug auf Sicherheit und Datenschutz zu überprüfen sind.

## Cookies und Tracking-Funktionen {#cookies-and-tracking-capabilities}

Dank der Trackingfunktionen ermöglicht Adobe Campaign die Verfolgung des Surfverhaltens von Versandempfängern auf einer gegebenen Webseite. Diesbezüglich kommen mit Adobe Campaign Sitzungs-Cookies und permanente Cookies zum Einsatz.

Die europäische &quot;E-Privacy-Richtlinie&quot; (2009/136/EG) und die europäische Datenschutz-Grundverordnung (DSGVO) sehen vor, dass Unternehmen vor dem Setzen von Cookies das Einverständnis der Webseitenbesucher einzuholen haben. Eine Möglichkeit besteht darin, Besucher der von Webtracking betroffenen Seiten zur Zustimmung aufzufordern, indem im oberen Bereich auf der ersten besuchten Seite ein Banner eingeblendet und zum Ankreuzen eines Feldes aufgefordert wird. Vermeiden Sie jedoch Pop-ups, da diese häufig von Browsern blockiert werden.

Bei der Benutzer-Tracking-Verwaltung steht für Webanwendungen und Landingpages ein Opt-out-Banner zur Verfügung. Weitere Informationen dazu finden Sie auf [dieser Seite](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign verwendet zwei Arten von Cookies:

1. Sitzungs-Cookies (nlid): Diese Art von Cookie enthält die Kennung der an den Kontakt gesandten E-Mail (broadlogId) und die Kennung der Nachrichtenvorlage (deliveryId). Er wird gesetzt, wenn ein Kunde auf eine in einer von Adobe Campaign versandten E-Mail enthaltene URL klickt, und ermöglicht die Verfolgung des Kundenverhaltens im Internet. Der Sitzungs-Cookie wird beim Schließen des Browsers automatisch gelöscht. Durch Anpassung der Browsereinstellungen kann der Kontakt das Setzen dieser Cookies untersagen.
1. Permanente Cookies (uuid230): Diese Art von Cookie ermöglicht die Identifizierung eines Internetusers, der mit Adobe Campaign bei Webseitenbesuchen interagiert. Er wird von Adobe Campaign verwendet, um die Anzahl an Klicks zu erfassen und die Weiterleitungsrate anlässlich einer Marketingkampagne zu schätzen. Er wird gesetzt, wenn ein Kontakt in einer E-Mail klickt, ein Adobe-Campaign-Formular ausfüllt oder auf eigene Initiative hin Kontakt aufnimmt. Der Kontakt kann diese Cookies löschen oder durch Anpassung der Browsereinstellungen das Setzen untersagen.

## Unversehrtheit der Datenbank {#database-integrity}

Adobe Campaign ist eine Software mit einer großen Funktionsvielfalt. Diese Vielfalt erfordert den Einsatz einer komplexen Datenbankstruktur. Die Datenbank enthält daher eine große Zahl an Tabellen, Feldern, Relationen und Indexen. Gewisse zwischengeschaltete Tabellen werden nicht auf der grafischen Oberfläche angezeigt. Relationen, Felder und Indexe werden teilweise automatisch von der Software erstellt, gelöscht oder geändert. Nur die von Adobe Campaign vorgesehenen Werkzeuge (grafische Benutzeroberfläche, Importfunktion, Server- und Web-Module, Versand-, Feldhinzufügungs- und Datenbankerweiterungsserver usw.) gewährleisten bei Änderungen des Datenbankinhalts ihre Unversehrtheit.

**Versuchen Sie nicht, den Inhalt oder die Struktur der Datenbank mit anderen als den von der Software vorgesehenen Mitteln zu ändern**. Derartige Eingriffe ziehen mit hoher Wahrscheinlichkeit Beschädigungen der Datenbank nach sich, die sich wie folgt äußern können: Verlust oder ungewollte Änderungen von Daten und Relationen, Erzeugung von Phantomrelationen und -datensätzen, schwerwiegende Fehlermeldungen usw. Aus derartigen Eingriffen resultierende Fehlfunktionen der Datenbank ziehen den Verfall von Ansprüchen auf Garantie und die Betreuung durch den Adobe-Campaign-Support nach sich.

Das Adobe-Campaign-System beruht auf der kontinuierlichen Speicherung aller Informationen in der Datenbank. Ihre Verfügbarkeit bildet die Voraussetzung für eine korrekte Ausführung der Adobe-Campaign-Software und insbesondere der Web-Module zur Registrierung, Administration und Abmeldung, der Administrationsbildschirme, Versandwarteschlangen, Mechanismen zur Versandoptimierung usw.

## Apache Tomcat {#apache-tomcat}

Adobe Campaign beinhaltet Apache Tomcat, eine von der Apache Software Foundation entwickelte Software ([https://www.apache.org/](https://www.apache.org/)).
