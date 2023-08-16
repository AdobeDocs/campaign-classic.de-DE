---
product: campaign
title: Häufige Fragen
description: Häufig gestellte Fragen zu Adobe Campaign Classic
feature: Overview
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 9f1b0974-f8bd-430f-88fe-9c09b0074d3b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 100%

---

# Häufige Fragen{#common-questions}



Benötigen Sie Hilfe bei der Arbeit mit Campaign Classic? Dann lesen Sie im Folgenden die 10 wichtigsten Fragen sowie weitere häufig gestellte Fragen auf dieser Seite. Außerdem können Sie:

* [Anleitungsvideos ansehen](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de)
* [Angebote zur Selbsthilfe nutzen](../../platform/using/tutorials.md#how-to-videos)
* [Erste Schritte und Anwendungsfälle lesen](../../platform/using/tutorials.md#step-by-step-guides)
* Sie konnten keine Antwort finden? [Experten konsultieren](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community?profile.language=de)
* Sie benötigen Support? [Hilfe- und Support-Angebote für Campaign aufrufen](../../support.md)

## 1. Wie kann ich Campaign auf die neuste Version aktualisieren? {#how-can-i-upgrade-campaign-to-the-latest-version-}

Adobe Campaign Classic verwendet spezielle Technologien, um Mehrwert zu erzielen. Diese Kombination von Technologien erfordert eine regelmäßige Aktualisierung Ihrer Campaign Classic-Instanzen, um sicherzustellen, dass Sie die aktuellsten Versionen verwenden und über maximale Sicherheit, Stabilität und Leistung verfügen.

Als gehosteter Kunde können Sie von einer jährlichen Campaign-Aktualisierung profitieren. Weiterführende Informationen hierzu finden Sie in [diesem Artikel](../../rn/using/rn-overview.md#yearly-upgrade).

[Lesen Sie diesen Abschnitt](../../production/using/build-upgrade.md), um zu erfahren, wie Sie Ihre Umgebung aktualisieren können, und konsultieren Sie die [häufigen Fragen](../../platform/using/faq-build-upgrade.md) zu diesem Thema.

## 2. Was ist der Workflow &quot;Bereinigung der Datenbank&quot;? {#what-is-the-database-cleanup-workflow-}

Dieser technische Workflow ermöglicht das Löschen veralteter Daten, um das exponentielle Anwachsen der Datenbank zu verhindern. Dieser integrierte technische Workflow wird automatisch ohne das Eingreifen des Benutzers ausgelöst. Der Zugriff erfolgt über den Knoten **[!UICONTROL Administration > Betreibung > Technische Workflows]**.

[Hier erfahren Sie mehr](../../production/using/database-cleanup-workflow.md) über den Datenbankbereinigungs-Workflow.

## 3. Wie kann ich Sicherheitszonen konfigurieren? {#how-can-i-configure-security-zones-}

Die Konfiguration der VPN-Sicherheitszone in Adobe Campaign Classic erfolgt über die Sicherheitszonen-Benutzeroberfläche durch den Administrator. Lesen Sie [diesen Abschnitt](../../installation/using/security-zones.md), um mehr über Sicherheitszonen in Campaign zu erfahren.

[Hier erfahren Sie mehr](https://helpx.adobe.com/de/campaign/kb/configuring-security-zones-self-service.html) über die Sicherheitszonen-Benutzeroberfläche.

## 4. Wie weiß ich, dass mein Versand fehlerfrei durchgeführt wird? {#how-can-i-make-sure-my-delivery-is-sent-without-errors-}

Adobe Campaign ist mit einer Reihe von Dashboards und Tools zur Überwachung des E-Mail-Versands ausgestattet.

[Hier erfahren Sie](../../delivery/using/about-delivery-monitoring.md), wie Sie Ihre Nachrichten senden, die Durchführung überwachen und Fehler beheben können.

## 5. Kann ich die Ausführung von Workflows überwachen? {#can-i-monitor-workflow-execution}

Informationen zur Überwachung der Workflow-Ausführung in Campaign [finden Sie auf dieser Seite](../../workflow/using/starting-a-workflow.md).

## 6. Wie kann ich eine Verbindung zu Campaign Classic herstellen? {#how-can-i-connect-to-campaign-classic-}

Starten Sie die Adobe Campaign-Clientkonsole und geben Sie Ihr Login und Passwort in Ihre Instanz ein.

[Hier erfahren Sie mehr darüber](../../platform/using/launching-adobe-campaign.md).

## 7. Mit welchen Systemen und Komponenten ist Campaign Classic kompatibel? {#which-systems-and-components-campaign-classic-is-compatible-with-}

Eine Liste mit allen Systemen und Komponenten, die vom aktuellen Build von Campaign unterstützt werden, finden Sie in der [Kompatibilitätsmatrix von Adobe Campaign Classic](../../rn/using/compatibility-matrix.md).

## 8. Wo finde ich die Versionshinweise für Campaign Classic? {#where-are-campaign-classic-release-notes-}

Die aktuellen Versionshinweise für Campaign Classic finden Sie [auf dieser Seite](../../rn/using/latest-release.md).

## 9. Wie funktioniert das Verfahren der Domain-Konfiguration? {#what-is-the-procedure-for-domain-delegation-}

Sie können Ihre Domain in Subdomains unterteilen, um Ihre Marken oder unterschiedlichen Textsorten (Transaktionsnachrichten, Marketing-Informationen usw.) voreinander zu trennen.
Adobe nutzt das Domain Name System (DNS) für den E-Mail-Versand. Dadurch kann der Kunde seinen Markenauftritt beibehalten, indem ein DNS-Alias mit seinem Domain-Namen verwendet wird, und Adobe kann autonom alle technischen Best Practices umsetzen, um die Zustellbarkeit von E-Mails zu optimieren.

[Hier erfahren Sie mehr darüber](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=de).
