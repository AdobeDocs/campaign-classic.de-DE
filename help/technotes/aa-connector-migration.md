---
product: campaign
title: Migration zum Adobe Analytics Connector
description: Häufig gestellte Fragen zu Campaign und Analytics Connector
hide: true
hidefromtoc: true
source-git-commit: cde4ed65abb2458fc40639b92314f8d56b18b78c
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 8%

---

# Migrieren zu Adobe Analytics Connector {#acc-aa-faq}

Ab Campaign Classic-Version 21.1.3 wird Adobe Analytics Data Connector nicht mehr unterstützt. [Weitere Informationen](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Am 1. August 2021 wird Adobe Campaign Classic aus der veralteten Data Connectors-Benutzeroberfläche entfernt. Vorhandene Campaign-Integrationen werden jedoch bis zum 1. März 2022 weiterhin Daten erfassen und an Adobe Analytics weitergeben. Am 1. März 2022 wird die Integration die Erfassung und Weitergabe von Daten an Adobe Analytics einstellen.

Sie müssen zur neuen Adobe Analytics Connector-Integration in Adobe Exchange migrieren, die die alte Data Connectors-Integration ersetzt, wie auf [dieser Seite](../platform/using/adobe-analytics-connector.md) beschrieben.


>[!NOTE]
>
>Fragen zu diesen Änderungen finden Sie in den [FAQ](#faq-aa). Weitere Informationen erhalten Sie bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Was hat sich geändert?

Eine neue Integration zwischen Campaign Classic v7 und Adobe Analytics ist jetzt verfügbar. Die wichtigsten Änderungen sind unten aufgeführt.

* Die Integration zwischen der Adobe Campaign Classic- und Adobe Analytics-Authentifizierung wurde von Benutzer/Kennwort in Adobe Identity Management Service (IMS) verschoben. Daher müssen Sie Adobe IMS implementieren und über eine Adobe ID](../integrations/using/about-adobe-id.md) eine Verbindung zu Campaign [herstellen, bevor Sie die Analytics Connector-Implementierung starten.

* Die Klassifizierung **Kontaktdatum**, die vom Typ Datum ist, wird von Adobe Analytics nicht mehr unterstützt. Bei migrierten Integrationen bleibt sie vom gleichen Typ. Für jedes von Campaign erstellte **Kontaktdatum** ist der Typ **String**.

* **Verarbeitungsregeln** werden von Adobe Campaign als Teil neuer Integrationen erstellt. Entweder **Verarbeitungsregeln** sollten manuell aus Adobe Analytics erstellt werden oder direkt die clientseitige JavaScript-Implementierung verwenden. **Verarbeitungsregeln bleiben** für vorhandene Integrationen intakt.

* Die integrierten technischen Workflows und ihr Verhalten bleiben unverändert. Es wurden nur die Backend-APIs geändert, die von den Workflows zum Pushen/Pull von Daten zu/von Adobe Analytics verwendet werden.

* Beachten Sie, dass der Prozess `nlserver` mit dem Benutzer des technischen IMS-Kontos konfiguriert werden sollte, damit der neue Connector funktioniert. Diese Änderung muss von der Adobe vorgenommen werden. Wenden Sie sich zur Implementierung an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Wenn Sie Adobe Genesis-APIs in benutzerdefinierten Workflows zum Abrufen und Übertragen der Daten aus Adobe Analytics waren, müssen Sie jetzt die neuen Adobe Analytics 1.4/2.0-APIs verwenden. [Weitere Informationen](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Sind Sie betroffen?

Wenn Sie den vorhandenen Adobe Analytics Data Connector (früher als Genesis-Integration bekannt) verwenden und die Integration auf einem niedrigeren Build als Campaign 21.1.3 implementiert wurde, sind Sie betroffen.

Erfahren Sie [in diesem Abschnitt](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version), wie Sie Ihre Version überprüfen.

## Wie wird die Aktualisierung durchgeführt?

Sie müssen vor dem 1. März 2022 **auf Campaign 21.1.3 (oder höher)** aktualisieren.

Als gehosteter Kunde arbeitet Adobe mit Ihnen zusammen, um Ihre Instanz(en) auf die neuere Version zu aktualisieren.

Als On-Premise-/Hybrid-Kunde müssen Sie auf eine der neueren Versionen aktualisieren, um von der neuen Integration profitieren zu können.

Sobald alle Instanzen aktualisiert wurden, können Sie [die neue Integration](../platform/using/adobe-analytics-connector.md) in Adobe Analytics Connector implementieren und einen nahtlosen Übergang sicherstellen.


## Häufig gestellte Fragen{#faq-aa}

**Wie erhalte ich Protokolle?**

Die Konfiguration der Benutzeroberfläche und Workflows sind mit der Protokollierung **verbose** ausgestattet.

Im ausführlichen Modus werden für jede API-Anfrage an Adobe Analytics auch Anfrage- und Antwortheader gedruckt.

Als On-Premise-Benutzer können Sie den ausführlichen Modus wie folgt implementieren:

* So aktivieren Sie den ausführlichen Modus für die Benutzeroberfläche: Führen Sie den Prozess `web` im ausführlichen Modus erneut aus.
* So aktivieren Sie den ausführlichen Modus für die **webAnalytics**-Workflows: Wählen Sie in den Workflow-Eigenschaften die Option **In der Engine ausführen** und führen Sie `wfserver` im ausführlichen Modus erneut aus.

**Was bedeutet der Fehler &quot;Integrationseigentümer nicht Administrator&quot;?**

Weitere Informationen zum Fehler &quot;Integrationseigentümer nicht Administrator&quot;von Data Connectors finden Sie auf [dieser Seite](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Was passiert mit alten Daten und Report Suites, wenn die Migration zum neuen Connector abgeschlossen ist?**

Nach der Migration sendet ein neuer Connector (der vom alten Connector migriert wurde) Daten an dieselbe Report Suite, und die vorhandenen Daten sind nicht betroffen: werden die vorhandenen Daten hinzugefügt.

**Einige vorhandene eVars/Ereignisse/Report Suites, die in Analytics vorhanden sind, sind in Campaign nicht sichtbar. Was soll ich tun?**

Die Integration beruht für die tägliche Verwendung auf Daten aus dem Token für technische Konten. Wenn für eine Dimension/Metrik/Report Suite aus dem Produktprofil, das mit dem Benutzer des technischen Kontos verknüpft ist, keine Berechtigung vorhanden ist, werden die von uns verwendeten APIs für diese Anfragen einfach fehlschlagen.

Wenn wir nach Details einer Analytics-Komponente lesen (z. B. Metriken/Dimensionen/Segmente/Report Suites), gibt die API diese Komponenten nicht im Ergebnis zurück (was so aussehen kann, als würde etwas auf der Analytics-Seite gelöscht oder nicht vorhanden sein). Die Analytics-API lehnt diese Anfragen ab und führt eine Fehlermeldung aus.

Die Lösung besteht darin, das **Produktprofil** im Analytics-Benutzerkontext des technischen Benutzer-Tokens mit den neu erstellten/fehlenden Komponenten zu aktualisieren, indem diese Komponenten in [Adobe Admin Console](https://adminconsole.adobe.com/) hinzugefügt werden. Weitere Anleitungen erhalten Sie bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Nützliche Links

* [Upgrade Ihrer Umgebung](../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../platform/using/faq-build-upgrade.md)
* [Campaign Classic-Build herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzer verfügbar machen](../installation/using/client-console-availability-for-windows.md)
* [Campaign-Client-Konsole installieren](../installation/using/installing-the-client-console.md)
