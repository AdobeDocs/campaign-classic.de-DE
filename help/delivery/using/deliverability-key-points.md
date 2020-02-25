---
title: Wichtige Punkte bei der Verwaltung der Zustellbarkeit in Adobe Campaign Classic
description: Welche Hauptpunkte sind bei der Verwaltung der Zustellbarkeit in Adobe Campaign Classic zu überprüfen?
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
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Wichtigste Punkte zur Lieferbarkeit{#deliverability-key-points}

Die Auslieferung besteht in der Messung des Erfolgs Ihrer Kampagnen, die ohne Absprung oder als Spam an den Posteingang Ihrer Empfänger gelangen.

Um die Auslieferbarkeit Ihrer Adobe Campaign-E-Mails zu optimieren, empfehlen wir die folgenden Best Practices. Probleme mit der Lieferbarkeit stehen in der Regel im Zusammenhang mit Maßnahmen zum Schutz vor Spam, die von Internetdienstanbietern und Mailserveradministratoren implementiert werden.

Die E-Mail-Zustellbarkeit bezieht sich auf die Merkmale, die die Fähigkeit einer Nachricht, ihr Ziel zu erreichen, über eine persönliche E-Mail-Adresse, innerhalb kurzer Zeit und mit der erwarteten Qualität in Bezug auf Inhalt und Format bestimmen.

Diese Merkmale fallen in vier Hauptkategorien:
* Datenqualität
* Nachricht und Inhalt
* Entsendende Infrastruktur
* Reputation

Gemeinsam bilden sie die Grundlage eines erfolgreichen E-Mail-Auslieferungsprogramms.

Die Zustellrate ist die Anzahl der E-Mails, die ihren Empfängern erfolgreich zugestellt wurde.

Die Zustellrate hängt u. a. von folgenden Faktoren ab:
* der korrekten Konfiguration Ihrer Instanzen;
* der Reputation Ihrer IP-Adresse;
* der Qualität der Zielkontakte;
* einer niedrigen Anzahl an Beschwerden und Hardbounces;
* Ihren Nachrichteninhalten;
* der Nachrichtenauthentifizierung (SPF, DKIM, DMARC);
* der Reputation des Absenders.

Folgende Faktoren können die Zustellbarkeit Ihrer E-Mails beeinträchtigen.

## Netzwerkkonfiguration prüfen {#network-configuration}

Spammer versuchen, ihre Identität zu verschleiern, und erschweren zu diesem Zweck die Identifizierung ihrer Server. Daher ist eine ordnungsgemäße Netzwerkkonfiguration, mit der nicht versucht wird, die Identität des Servers zu verbergen, für den Versand großer E-Mail-Mengen von entscheidender Bedeutung.

## Send to valid addresses {#valid-addresses}

Spammer verwenden oft Adressgeneratoren basierend auf Listen häufiger Namen und Vornamen. Zusätzlich beachten sie nur selten von Mailservern zurückgesendete technische Benachrichtigungen. Eine hohe Menge ungültiger Adressen wird daher oft als Hinweis auf Spam betrachtet. Dies können Sie mit einem doppelten Anmeldeverfahren (Double-Opt-in) und der wirksamen Bearbeitung technischer Bounce Messages vermeiden.

## Reduzierung von Beschwerden und Absprungraten {#reduce-complaint-rates}

ISPs bieten normalerweise die Möglichkeit, eine erhaltene Nachricht als Spam zu melden und dadurch zweifelhafte Quellen zu identifizieren. Sie können die Beschwerderate verringern, indem Sie Abmeldewünsche rasch berücksichtigen, regelmäßig eine entsprechende Liste verwenden, das Einverständnis der Empfänger durch ein doppeltes Anmeldeverfahren verifizieren und Feedback-Schleifen integrieren.

## Send to honeypot addresses {#honeypot-addresses}

ISPs und andere Organisationen (siehe https://www.projecthoneypot.org/) verwenden Postfächer, die nicht mit physischen Personen übereinstimmen, sondern ausschließlich eingerichtet werden, um Spammer anzuziehen. Diese so genannten &quot;honeypot&quot;-Adressen werden im Web veröffentlicht, um von Spambots gesammelt zu werden und so eine Erkennung illegitimer Absender zu erlauben. Durch ein Anmeldeverfahren mit doppelter Bestätigung wird verhindert, dass solche Adressen einer Liste hinzugefügt werden. Wenn Sie eine Liste eines Drittanbieters nutzen, müssen Sie wissen, welche Methoden der jeweilige Verwalter anwendet.

## Inhalt der Nachricht anpassen {#message-content}

In geringerem Maß kann auch der Nachrichteninhalt dazu führen, dass E-Mails von manchen Filtern als Spam eingestuft werden. Der Einsatz von bestimmten Wörtern oder Ausrufezeichen im Betreff und Text wird als Hinweis auf Spam betrachtet. Oft ersetzen Spammer auch Text durch Bilder, damit der Text von Anti-Spam-Filtern nicht automatisch analysiert werden kann. Darum kann eine Nachricht (im HTML-Format) mit einem hohen Anteil an Bildern oder mit Bildern im Anhang ggf. blockiert werden.

## Arbeiten Sie an Ihrem Ruf {#reputation}

Spammer führen programmierte Sendungen durch, um langfristig ihre Reputation zu wahren. Manchmal müssen sie ihren Marketingplan an die Best Practices des jeweiligen ISPs anpassen. Deshalb führen sie nach einer Optimierung ihrer Reputation (ramp-up) regelmäßige Sendungen durch.