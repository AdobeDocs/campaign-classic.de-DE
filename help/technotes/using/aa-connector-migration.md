---
product: campaign
title: Migrieren zum Adobe Analytics Connector
description: Häufig gestellte Fragen zum Campaign und Analytics Connector
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
source-git-commit: 6d3e21fa00771a47d846d502e2d4d5971aa39b29
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 88%

---

# Migrieren vorhandener Genesis-Integrationen zu Adobe Analytics Connector {#acc-aa-faq}

![](../../assets/v7-only.svg)

Ab Campaign Classic Version v7 21.1.3 wird der Adobe Analytics Data Connector nicht mehr unterstützt. [Weitere Informationen](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html?lang=de)

Am 1. August 2021 wurde Adobe Campaign Classic aus der alten Data Connectors-Benutzeroberfläche entfernt. Vorhandene Campaign-Integrationen werden jedoch bis zum 1. März 2022 weiterhin Daten erfassen und an Adobe Analytics weitergeben. Nach diesem Datum wird die Integration die Erfassung und Weitergabe von Daten an Adobe Analytics einstellen.

**Sie müssen** die neue Adobe Analytics Connector-Integration in Adobe Exchange implementieren, die die veraltete Data Connectors-Integration ersetzt. Weitere Informationen zu Adobe Analytics Connector finden Sie auf [dieser Seite](../../platform/using/adobe-analytics-connector.md).

>[!NOTE]
>
>Fragen zu diesen Änderungen finden Sie in den [Häufig gestellten Fragen](#faq-aa). Weitere Informationen erhalten Sie bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Was hat sich geändert?

Eine neue Integration zwischen Campaign Classic v7 und Adobe Analytics ist jetzt verfügbar. Die wichtigsten Änderungen sind unten aufgeführt.

* Die Integration zwischen der Adobe Campaign Classic- und Adobe Analytics-Authentifizierung wurde von Benutzer/Passwort zu Adobe Identity Management Service (IMS) geändert. Daher müssen Sie Adobe IMS implementieren und [über eine Adobe ID](../../integrations/using/about-adobe-id.md) eine Verbindung zu Campaign herstellen, bevor Sie die Analytics Connector-Implementierung starten.

* Die Klassifizierung **Kontaktdatum**, die vom Typ Datum ist, wird von Adobe Analytics nicht mehr unterstützt. Bei migrierten Integrationen bleibt sie vom gleichen Typ. Für jedes von Campaign erstellte **Kontaktdatum** ist der Typ **Zeichenfolge**.

* **Verarbeitungsregeln** werden von Adobe Campaign als Teil neuer Integrationen erstellt. Entweder sollten die **Verarbeitungsregeln** manuell aus Adobe Analytics erstellt werden oder direkt die Client-seitige JavaScript-Implementierung verwenden. **Verarbeitungsregeln** bleiben für vorhandene Integrationen intakt.

* Die integrierten technischen Workflows und ihr Verhalten bleiben unverändert. Es wurden nur die Backend-APIs geändert, die von den Workflows zum Push/Pull von Daten zu/von Adobe Analytics verwendet werden.

* Beachten Sie, dass der `nlserver`-Prozess mit dem Benutzer des technischen IMS-Kontos konfiguriert werden muss, damit der neue Connector funktioniert. Diese Änderung muss von Adobe vorgenommen werden. Wenden Sie sich zur Implementierung an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Wenn Sie Adobe Genesis-APIs in benutzerdefinierten Workflows zum Abrufen und Übertragen (Pull/Push) der Daten aus Adobe Analytics verwendet haben, müssen Sie jetzt die neuen Adobe Analytics 1.4/2.0-APIs verwenden. [Weitere Informationen](https://adobeexchangeec.zendesk.com/hc/de-de/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Sind Sie betroffen?

Wenn Sie den vorhandenen Adobe Analytics Data Connector (früher Genesis-Integration genannt) verwenden und die Integration auf einem niedrigeren Build als Campaign 21.1.3 implementiert wurde, sind Sie betroffen.

[In diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Version überprüfen.

## Wie wird die Aktualisierung durchgeführt?

Sie müssen **vor dem 1. März 2022** das Upgrade auf Campaign 21.1.3 (oder höher) vornehmen.

Wenn Sie ein gehosteter Kunde sind, wird Adobe in Kürze auf Sie zukommen, um für Ihre Instanz(en) das Upgrade auf die neuere Version vorzunehmen. Anschließend können Sie [Adobe Analytics-Connector](../../platform/using/adobe-analytics-connector.md) verwenden.

Als On-Premise-/Hybrid-Kunde müssen Sie das Upgrade auf eine der neueren Versionen vornehmen, um von der neuen Integration profitieren zu können.
Sobald alle Instanzen das Upgrade erhalten haben, können Sie [die neue Integration](../../platform/using/adobe-analytics-provisioning.md) in Adobe Analytics Connector implementieren und einen nahtlosen Übergang sicherstellen.

## Häufig gestellte Fragen{#faq-aa}

**Wie erhalte ich Protokolle?**

Die Konfiguration der Benutzeroberfläche und Workflows sind mit der Protokollierung **Verbose** ausgestattet.

Im Verbose-Modus werden für jede API-Anfrage an Adobe Analytics auch Anfrage- und Antwort-Header gedruckt.

Als On-Premise-Benutzer können Sie den Verbose-Modus wie folgt implementieren:

* Um den Verbose-Modus für die Benutzeroberfläche zu aktivieren, führen Sie den `web`-Prozess im Verbose-Modus erneut aus.
* Um den Verbose-Modus für die **webAnalytics**-Workflows zuaktivieren, wählen Sie in den Workflow-Eigenschaften die Option **In der Engine ausführen** und führen Sie `wfserver` im Verbose-Modus erneut aus.

**Was bedeutet der Fehler &quot;Integrationsverantwortlicher nicht Administrator&quot;?**

Weitere Informationen zum Data Connectors-Fehler `Integration Owner Not Admin` finden Sie auf [dieser Seite](https://adobeexchangeec.zendesk.com/hc/de-de/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Was passiert mit alten Daten und Report Suites, wenn die Migration zum neuen Connector abgeschlossen ist?**

Nach der Migration sendet ein neuer Connector (der vom alten Connector migriert wurde) Daten an dieselbe Report Suite und die vorhandenen Daten sind nicht betroffen. Sie werden zu den vorhandenen Daten hinzugefügt.

**Einige vorhandene eVars/Ereignisse/Report Suites, die in Analytics vorhanden sind, sind in Campaign nicht sichtbar. Was soll ich tun?**

Die Integration beruht für die tägliche Verwendung auf Daten aus dem Token für technische Konten. Wenn für eine Dimension/Metrik/Report Suite aus dem Produktprofil, das mit dem Benutzer des technischen Kontos verknüpft ist, keine Berechtigung vorhanden ist, werden die für diese Anfragen verwendeten APIs einfach fehlschlagen.

Wenn Details einer Analytics-Komponente abgefragt werden (z. B. Metriken/Dimensionen/Segmente/Report Suites), gibt die API diese Komponenten nicht im Ergebnis zurück (was so aussehen kann, als würde etwas auf der Analytics-Seite gelöscht oder wäre nicht vorhanden). Die Analytics-API lehnt diese Anfragen ab und gibt eine Fehlermeldung zurück.

Die Lösung besteht darin, das **Produktprofil** im Analytics-Benutzer-Kontext des technischen Benutzer-Tokens mit den neu erstellten/fehlenden Komponenten zu aktualisieren, indem diese Komponenten in der [Adobe Admin Console](https://adminconsole.adobe.com/) hinzugefügt werden. Weitere Informationen erhalten Sie bei der [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Nützliche Links

* [Upgrade Ihrer Umgebung](../../production/using/build-upgrade.md)
* [Häufig gestellte Fragen zum Build-Upgrade](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic-Build herunterladen](https://experience.adobe.com/#/downloads/content/software-distribution/de/campaign.html)
* [Neue Client-Konsole für Benutzer verfügbar machen](../../installation/using/client-console-availability-for-windows.md)
* [Campaign-Client-Konsole installieren](../../installation/using/installing-the-client-console.md)
