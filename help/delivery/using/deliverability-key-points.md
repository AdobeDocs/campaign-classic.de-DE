---
title: Wichtige Aspekte bei der Zustellbarkeit
description: Wichtigste Punkte zur Überprüfung der Lieferbarkeit
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 98%

---


# Wichtige Aspekte bei der Zustellbarkeit{#deliverability-key-points}

Um die Zustellbarkeit Ihrer E-Mails in Adobe Campaign zu optimieren, empfehlen wir, die unten aufgeführten Best Practices zu befolgen. Zustellbarkeitsprobleme resultieren im Allgemeinen aus Schutzmaßnahmen gegen Spam, die von Internetdienstanbietern und Mail-Server-Administratoren eingerichtet werden.

**Email Deliverability** bezieht sich auf jene Merkmale, die über die Fähigkeit einer Nachricht entscheiden, innerhalb kurzer Zeit über eine persönliche E-Mail-Adresse ihr Ziel zu erreichen – mit der erwarteten Qualität in Bezug auf Inhalt und Format.

Diese Merkmale fallen in vier Hauptkategorien:
* Datenqualität
* Nachricht und Inhalt
* Versandinfrastruktur
* Reputation

Gemeinsam bilden sie die Grundlage eines erfolgreichen Email Deliverability-Programms.

Die **Zustellrate** ist die Anzahl der E-Mails, die ihren Empfängern erfolgreich zugestellt wurde.

Die Zustellrate hängt u. a. von folgenden Faktoren ab:
* der korrekten Konfiguration Ihrer Instanzen;
* der Reputation Ihrer IP-Adresse;
* der Qualität der Zielkontakte;
* einer niedrigen Anzahl an Beschwerden und Hardbounces;
* Ihren Nachrichteninhalten;
* der Nachrichtenauthentifizierung (SPF, DKIM, DMARC);
* der Reputation des Absenders.

Folgende Faktoren können die Zustellbarkeit Ihrer E-Mails beeinträchtigen.

## Prüfen der Netzwerkkonfiguration {#network-configuration}

Spammer versuchen, ihre Identität zu verschleiern, und erschweren zu diesem Zweck die Identifizierung ihrer Server. Daher ist eine ordnungsgemäße Netzwerkkonfiguration, mit der nicht versucht wird, die Identität des Servers zu verbergen, für den Versand großer E-Mail-Mengen von entscheidender Bedeutung.

## Senden an gültige Adressen {#valid-addresses}

Spammer verwenden oft Adressgeneratoren basierend auf Listen häufiger Namen und Vornamen. Zusätzlich beachten sie nur selten von Mailservern zurückgesendete technische Benachrichtigungen. Eine hohe Menge ungültiger Adressen wird daher oft als Hinweis auf Spam betrachtet. Dies können Sie mit einem doppelten Anmeldeverfahren (Double-Opt-in) und der wirksamen Bearbeitung technischer Bounce Messages vermeiden.

## Reduzieren von Beschwerden und Hardbounces {#reduce-complaint-rates}

ISPs bieten normalerweise die Möglichkeit, eine erhaltene Nachricht als Spam zu melden und dadurch zweifelhafte Quellen zu identifizieren. Sie können die Beschwerderate verringern, indem Sie Abmeldewünsche rasch berücksichtigen, regelmäßig eine entsprechende Liste verwenden, das Einverständnis der Empfänger durch ein doppeltes Anmeldeverfahren verifizieren und Feedback-Schleifen integrieren.

## Senden an eine Spam-Falle (Honeypot){#honeypot-addresses}

ISPs und andere Organisationen (siehe Website von [Project Honey Pot](https://www.projecthoneypot.org/)) verwenden Postfächer, die nicht mit physischen Personen übereinstimmen, sondern ausschließlich eingerichtet werden, um Spammer anzulocken. Diese so genannten &quot;honeypot&quot;-Adressen werden im Web veröffentlicht, um von Spambots gesammelt zu werden und so eine Erkennung illegitimer Absender zu erlauben. Durch ein Anmeldeverfahren mit doppelter Bestätigung wird verhindert, dass solche Adressen einer Liste hinzugefügt werden. Wenn Sie eine Liste eines Drittanbieters nutzen, müssen Sie wissen, welche Methoden der jeweilige Verwalter anwendet.

## Anpassen des Nachrichteninhalts {#message-content}

In geringerem Maß kann auch der Nachrichteninhalt dazu führen, dass E-Mails von manchen Filtern als Spam eingestuft werden. Der Einsatz von bestimmten Wörtern oder Ausrufezeichen im Betreff und Text wird als Hinweis auf Spam betrachtet. Oft ersetzen Spammer auch Text durch Bilder, damit der Text von Anti-Spam-Filtern nicht automatisch analysiert werden kann. Darum kann eine Nachricht (im HTML-Format) mit einem hohen Anteil an Bildern oder mit Bildern im Anhang ggf. blockiert werden.

## Arbeiten an Ihrer Reputation {#reputation}

Spammer führen programmierte Sendungen durch, um langfristig ihre Reputation zu wahren. Manchmal müssen sie ihren Marketingplan an die Best Practices des jeweiligen ISPs anpassen. Deshalb führen sie nach einer Optimierung ihrer Reputation (ramp-up) regelmäßige Sendungen durch.

## Best Practices {#best-practices}

Lernen Sie Best Practices für die Zustellbarkeit mit Adobe Campaign kennen. Verwenden Sie die folgenden Links, um durch die Themen zu navigieren und Anleitungen zu finden.

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="Starten" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>Starten</strong>
    </a>
    </div>
    <p>
    <em>Einrichten einer neuen Plattform</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="Design" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>Design</strong>
    </a>
    </div>
    <p>
    <em>Steuern des Nachrichteninhalts</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="Design" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>Senden</strong>
    </a>
    </div>
    <p>
    <em>Verbessern der Reputation</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="Optimieren" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>Optimieren</strong>
    </a>
    </div>
    <p>
    <em>Technische Empfehlungen</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="Prüfen" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>Überwachen</strong>
    </a>
    </div>
    <p>
    <em>Monitoring-Tools</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="Optimieren" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>Beheben von Fehlern</strong>
    </a>
    </div>
    <p>
    <em>Lösen von Problemen</em>
    <p>
  </td>
</tr>
</table>
