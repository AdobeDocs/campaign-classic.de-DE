---
product: campaign
title: Erste Schritte mit Upgrades
description: Weiterführende Informationen zu Campaign Classic-Upgrades
feature: Overview
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: d59e9f55275bac303a5ed1450bb28ef7fa0f84cd
workflow-type: ht
source-wordcount: '921'
ht-degree: 100%

---

# Versionsaktualisierungen{#rn-overview}

![](../../assets/v7-only.svg)

Adobe Campaign Classic veröffentlicht regelmäßig Produktaktualisierungen, die neue Funktionen und Fehlerkorrekturen beinhalten und die Leistung, Sicherheit und Benutzerfreundlichkeit verbessern. Diese Aktualisierungen werden als Produkt-Builds veröffentlicht. Detaillierte Informationen zu den einzelnen neuen Builds finden Sie in den [Versionshinweisen](latest-release.md).

## Versionsstatus{#rn-statuses}

Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe in den [Versionshinweisen](latest-release.md) gekennzeichnet ist.

![](assets/do-not-localize/green3.png) **Allgemeine Verfügbarkeit** (GA) – Aktueller stabiler Build, in der Produktion validiert und von Adobe empfohlen.

![](assets/do-not-localize/limited3.png) **Eingeschränkte Verfügbarkeit** (LA) – Implementierung nur auf Anfrage.

![](assets/do-not-localize/blue3.png) **Release Candidate** (RC) – Aktuelle Version mit neuen Funktionen.

![](assets/do-not-localize/orange3.png) **Nicht mehr verfügbar** - Keine Implementierung. Keine Fehlerbehebung. Es wird empfohlen, auf einen neueren Build zu aktualisieren.

![](assets/do-not-localize/red3.png) **Eingestellt** – Keine Implementierung. Keine Fehlerbehebung. Bestehende Implementierungen müssen aktualisiert werden.

## Versionszyklus{#rn-cycle}

Adobe Campaign wird regelmäßig aktualisiert. Dieser regelmäßige Aktualisierungsrhythmus zielt darauf ab, Ihnen die neuesten und besten Funktionen bereitzustellen, Ihre Umgebung sicher zu halten und Ihr Produkterlebnis zu verbessern.

Deshalb ist es außerordentlich wichtig, dass Sie **die aktuelle stabile Version** von Adobe Campaign verwenden. Dadurch wird auch Ihr Support-Erlebnis verbessert, da das Erkennen, Reproduzieren und Beheben eines Problems in einem kürzlich erstellten Build normalerweise viel schneller erfolgt. Außerdem wurden viele potenzielle Probleme bereits in den letzten Builds behoben.

Als gehosteter Kunde profitieren Sie automatisch von Aktualisierungen mit der neuesten stabilen Version, ohne aktiv werden zu müssen. Weitere Informationen finden Sie im [Abschnitt zur jährlichen Aktualisierung](#yearly-upgrade). Wenn Sie von einem alten Build migrieren, empfiehlt Adobe, zunächst ein Upgrade auf diese Version durchzuführen.

## Empfehlungen{#recommendations}

Um eine stabile Konfiguration sicherzustellen, empfiehlt Adobe, **denselben Build** auf allen Servern zu installieren, die dieselbe Client-Konfiguration besitzen.

Außerdem muss sich die Client-Konsole, sofern in den [Versionshinweisen](latest-release.md) nicht anders angegeben, auf **demselben Build** wie die Server-Instanz befinden.

Um Ihre Implementierung auf dem neuesten Stand zu halten, lesen Sie bei jeder neuen Version die Seiten [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md) und [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).

## Upgrade-Prozess{#process-upgrade}

Wenden Sie sich als gehosteter Kunde (Managed Services oder Hybrid) an das Team der Kundenunterstützung, um Ihre Umgebung aktualisieren zu lassen.

Als On-Premise-Benutzer können Sie das Upgrade durchführen. Laden Sie dazu den [neuesten stabilen Build (GA) herunter](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html) und aktualisieren Sie alle Ihre Umgebungen.

Erfahren Sie mehr über den [Upgrade-Prozess](../../production/using/build-upgrade.md) und lesen Sie die [häufig gestellten Fragen zu Build-Upgrades](../../platform/using/faq-build-upgrade.md).

## Jährliche Aktualisierung {#yearly-upgrade}

Adobe ist bestrebt, Ihnen mit unseren Software-Lösungen das bestmögliche Erlebnis und den optimalen Nutzen zu bieten. Adobe stellt sicher, dass Sie Zugriff auf die aktuellen Versionen der in unseren Lösungen verwendeten Technologien haben.

Adobe Campaign Classic verwendet spezielle Technologien, um Mehrwert zu erzielen. Diese Kombination von Technologien erfordert eine regelmäßige Aktualisierung Ihrer Campaign Classic-Instanzen, um sicherzustellen, dass Sie die jeweils aktuellen Versionen verwenden und über maximale Sicherheit, Stabilität und Leistung verfügen.

Als gehosteter Benutzer erhalten Sie automatisch das Upgrade mit dem aktuellen GA-Build, ohne dass Sie aktiv werden müssen. Weitere Informationen finden Sie in den häufig gestellten Fragen weiter unten.

### Warum benötigt mein Unternehmene Organisation dieses Upgrade?

Als gehosteter Kunde werden Sie von Adobe direkt benachrichtigt, wenn für Ihr Konto ein Upgrade einer oder mehrerer Technologien im Zusammenhang mit Campaign Classic sowie eine Aktualisierung des aktuellen Builds und/oder der Version erforderlich ist.

Wenn Sie als On-Premise- oder Hybrid-Kunde mit einer älteren Version arbeiten, empfiehlt Ihnen Adobe, zum aktuellen stabilen Build (GA) zu wechseln.

Dadurch wird sichergestellt, dass Ihr Konto vor Sicherheitslücken geschützt ist und die aktuelle Technologie verwendet wird. Außerdem wird Ihr Konto durch dieses Upgrade in Zukunft auf einfachere, regelmäßige Upgrades vorbereitet, die weniger manuelle Arbeit und Eingriffe erfordern.

### Wie sieht das Verfahren und der Zeitplan für dieses Upgrade aus?

Das Adobe-Team begleitet Ihr Unternehmen durch diesen Prozess.

Ein Team aus engagierten Kundenbetreuern, Produkt-Managern, Ingenieuren, TechOps-Spezialisten und Produktberatern wurde zusammengestellt, um diesen Prozess möglichst reibungslos zu gestalten.

### Vorteile

<tr>
  <td>
      <img alt="Sicherheit" src="assets/do-not-localize/security.png"/>
    <div>
    <strong>Verbesserte Sicherheit</strong>
    </div>
    <ul>
    <li>Eine Kombination von Technologien, die bei Adobe Campaign Classic zum Einsatz kommen, sorgen gemeinsam für einen Mehrwert.</li>
    <li>Alle Instanzen müssen aktualisiert werden, um die nötige Sicherheit zu gewährleisten.</li>
    <li>Sicherheit erfordert ständige Überwachung und vorausschauende Wartung.</li>
    <li>Sicherheitsrisiken sind allgegenwärtig und können nicht ignoriert werden. Jedes Upgrade von Campaign Classic verbessert die Sicherheit.</li>
    </ul>
  </td>

<td>
      <img alt="Support" src="assets/do-not-localize/support.png" />
    <div>
    <strong>Verbesserter Support</strong>
    </div>
    <ul>
    <li>Die meisten kritischen Probleme werden mit Upgrades behoben und können so vermieden werden.</li>
    <li>Regelmäßige Upgrades tragen dazu bei, Schwierigkeiten zu beseitigen und dadurch die Effizienz zu steigern.</li>
    <li>Der Bedarf an Kundenunterstützung wird reduziert, was schnellere Lösungen und mehr Zeit für Probleme ermöglicht, die nicht mit Upgrades in Verbindung stehen.</li>
    </ul>
  </td>
</tr>

<tr>
  <td>
      <img alt="Wartung" src="assets/do-not-localize/maintenance.png"/>
    <div>
    <strong>Verbesserte Wartung und Stabilität</strong>
    </div>
    <ul>
    <li>Im Laufe der Zeit ermittelt das Adobe Campaign-Team Möglichkeiten zur Verbesserung der Stabilität und Leistung des Produkts sowie zur Behebung bekannter Probleme.</li>
    <li>Durch das Upgrade wird Ihre Instanz mit diesen Verbesserungen auf den neuesten Stand gebracht. Außerdem werden damit häufige Schwierigkeiten von Organisationen beseitigt, deren Campaign Classic-Instanzen schnell anwachsen und deren Struktur eine hohe Komplexität aufweist.</li>
    <li>Verbesserungen im gesamten Technologie-Stack von Campaign Classic werden sowohl dem Marketing- als auch dem IT-Team Ihres Unternehmens zugutekommen.</li>
    </ul>
  </td>

<td>
      <img alt="Build-Upgrade" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>Einfachere Upgrades</strong>
    </a>
    </div>
    <ul>
    <li>Der Aufwand und die Komplexität eines Upgrades Ihrer Campaign Classic-Instanz steigen mit dem Abstand zwischen zwei Versionen (V6 -&gt; V7).</li>
    <li>Je länger Ihr Unternehmen wartet, desto komplexer ist das Upgrade (und desto mehr Sicherheitsrisiken sind Sie ausgesetzt).</li>
    <li>Regelmäßige Aktualisierungen verringern Ausfallzeiten und das Risiko einer Regression.</li>
    </ul>
  </td>
</tr>
</table>

## Zusätzliche Ressourcen{#support}

* [Finden Sie Ihre Campaign-Version](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
* [Hilfe und Support](../../support.md)
* [Control Panel-Versionen](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=de)
* [Aktuelle Dokumentationsaktualisierungen](../../rn/using/documentation-updates.md)
* [Eingestellte und entfernte Funktionen](../../rn/using/deprecated-features.md)
* [Häufig gestellte Fragen zur Build-Aktualisierung](../../platform/using/faq-build-upgrade.md)

Abonnieren Sie das [Prioritätsprodukt-Update von Adobe](https://www.adobe.com/de/subscription/priority-product-update.html), um über neue Versionen der Experience Cloud-Lösungen informiert zu werden.
