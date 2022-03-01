---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8278228a6610e99f9400343bc967e16f2759dfbe
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 83%

---

# Aktuelle Version{#latest-release}

![](../../assets/v7-only.svg)

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.2.2 – Build 4349 {#release-7-2-2}

_1. März 2022_

**Patches**

* Fehlerkorrektur - Beim Konfigurieren der **Web Analytics** externes Konto, wodurch der Integrationsstatus immer &quot;Integration erfolgreich&quot;angezeigt wurde, selbst wenn Fehler aufgetreten sind. (NEO-36672)
* Fehlerkorrektur - diverse Postupgrade-Fehler im Zusammenhang mit dem Sequenz-ID-Mechanismus bei negativen IDs wurden behoben. (NEO-43205, NEO-42846, NEO-42845)
* Es wurde ein Problem bei der Verwendung der **Web Analytics** externes Konto mit wiederkehrenden und kontinuierlichen Sendungen, wodurch Daten aus dem externen Konto teilweise verloren gingen. (NEO-38548)
* Fehlerkorrektur - Postupgrade wird jetzt nicht mehr verlangsamt, wenn die NmsActiveContact -Tabelle aktualisiert wird. (NEO-43206)
* Fehlerkorrektur - Es wurde ein Problem mit einem Postupgrade behoben, das auftrat, wenn native Ordner aus dem **Administration** Knoten an einen anderen Speicherort. (NEO-42875)
* Fehlerkorrektur - Die Verwendung von **Daten aktualisieren** Workflow-Aktivität, die verhindern könnte, dass das Empfängerschema mit Empfängerdaten aus einer externen Google Cloud-Datenbank aktualisiert wird. (NEO-42343)
* Fehlerkorrektur - Beim Postupgrade tritt jetzt kein Fehler mehr im Zusammenhang mit dem Adobe Analytics-Connector auf. (NEO-43318, NEO-38136)
* Fehlerkorrektur - Es wurde ein Problem behoben, bei dem die CUID während des Postupgrades durch &#39;VALUE_TO_CHANGE&#39; überschrieben wurde. (NEO-43267)
* Fehlerkorrektur - Beim Synchronisieren der Mid-Sourcing- und Marketing-Instanzen in einer Multi-Mid-Konfiguration treten jetzt keine Fehler mehr auf. (NEO-10432)
* Fehlerkorrektur - Beim Aktualisieren des Zustellbarkeits-Workflows tritt jetzt kein Fehler mehr auf, wenn mehr als 1000 Broadlogs gleichzeitig verwendet werden. (NEO-40276)
* Fehlerkorrektur - Die Versandindikatoren Öffnungsverhältnis und Klick-Verhältnis werden jetzt automatisch aktualisiert. (NEO-43253)

## ![](assets/do-not-localize/green_2.png) Version 7.2.1 – Build 9346 {#release-7-2-1}

_10. Januar 2022_

**Sicherheitsverbesserung**

An den FDA-Konten wurden verschiedene Sicherheitsverbesserungen vorgenommen:

* Bei der Konfiguration Ihres externen FDA-Kontos können Sie sich jetzt mit der Schlüsselpaar-Authentifizierung bei Ihrem Snowflake-Konto anmelden, wodurch die Authentifizierungssicherheit verbessert ist. [Mehr dazu](../../installation/using/configure-fda-snowflake.md)
* Beim Konfigurieren Ihres externen FDA-Kontos können Sie sich jetzt mit der vom System zugewiesenen verwalteten Identität bei Ihrem Azure Synapse Analytics-Konto anmelden. [Mehr dazu](../../installation/using/configure-fda-synapse.md#azure-external)
* Alle Verweise auf die log4j-Bibliothek wurden aus Campaign entfernt, um optimale Sicherheit zu gewährleisten.

**Verbesserungen**

* Microsoft Dynamics CRM 365-Connector

   Es wurden kritische Fehlerbehebungen bei der Web-API des Microsoft Dynamics-Connectors vorgenommen:

   * Fehlerkorrektur – Beim Import, der durch einen Workflow ausgelöst wird, werden jetzt die Nullwerte von Feldern vom Typ Zeichenfolge als leere Werte statt als Null gespeichert.
   * Fehlerkorrektur – Beim Datenimport oder -export mithilfe von Web-API-Aufrufen tritt jetzt nicht mehr der Fehler „Ungültiger URI: Das URI-Schema ist zu lang“ auf:
   * Es wurden verschiedene Probleme beim Importieren von Daten mit Suchfeldern aus Microsoft Dynamics 365 behoben.

* Google BigQuery FDA-Connector

   * Der Google BigQuery FDA-Connector ist jetzt für gehostete Bereitstellungen verfügbar. [Mehr dazu](../../installation/using/configure-fda-google-big-query.md)
   * Es wurde Unterstützung zum Aktivieren von Verbindungen zu einem Proxy-Server für den Google BigQuery FDA-Connector hinzugefügt. Die erforderlichen Proxy-Optionen können über das Feld &quot;Optionen&quot; in der Konfiguration des externen Kontos festgelegt werden. [mehr dazu](../../installation/using/configure-fda-google-big-query.md#google-external)

**Sonstige Änderungen**

* Nach der Einstellung wurden die Aktionsaktivitäten von Microsoft CRM, Salesforce und Oracle CRM On Demand aus der Benutzeroberfläche entfernt. Um die Datensynchronisation zwischen Adobe Campaign und einem CRM-System zu konfigurieren, können Sie die Aktivität &quot;CRM-Connector&quot; verwenden. [Mehr dazu](../../workflow/using/crm-connector.md)
* Das Feld **[!UICONTROL Verschlüsselte Kennung]** wurde zum Besucherschema hinzugefügt (nms:visitor). Dieses Feld wird berechnet und ist für Web-Programme vorgesehen. Dies gilt, wenn der Kanal &quot;Line&quot; in der Mid-Sourcing-Instanz konfiguriert ist.
* CRM-Datenquellen können jetzt mit der Aktivität **Datenquelle ändern** verwendet werden.
* Eine neue Option wurde in den Eigenschaften zum **Umgang mit Fehlern** bei Workflow-Aktivitäten ergänzt: Die Option **Abbruch bei Fehler** sorgt dafür, dass der Workflow automatisch angehalten wird. Danach können Sie ihn nicht mehr neu starten (NEO-29661). [Mehr dazu](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Die Primärschlüssel der nmsGroup-Tabelle, die zur Erstellung statistischer Empfängergruppen verwendet wird, werden jetzt in einer speziellen Sequenz erzeugt. Zuvor wurde die Sequenz &quot;xtknewId&quot; verwendet. (NEO-30832)
* Es wurde Unterstützung für Batch-Aktualisierungsvorgänge mit der Aktivität &quot;CRM-Connector&quot; hinzugefügt.
* Die Leistung bei der Verarbeitungszeit für Transaktionsnachrichten wurde verbessert. (NEO-40370)

**Patches**

* Fehlerkorrektur – Bei der Erstellung eines Versands tritt jetzt kein Fehler mehr auf, der zu einem Fehler auf der Registerkarte **Bilder** im Fenster **Tracking &amp; Bilder** führt. Dies trat bei der Verwendung einer automatischen Proxy-Konfiguration auf. (NEO-33260)
* Es wurde ein Problem behoben, das das Hochladen einer Datei auf einen Debian 10-Server (HTTPS) im synchronen Modus verhindern konnte.
* Fehlerkorrektur – Es kommt jetzt nicht mehr vor, dass Datensätze aus der Versandstatistiktabelle (`nmsDeliveryLogStats`) während der Datenbankbereinigung nicht korrekt aus der Mid-Sourcing-Instanz bereinigt werden, nachdem die entsprechenden Sendungen gelöscht wurden. (NEO-31034)
* Fehlerkorrektur – Es tritt jetzt kein Fehler mehr auf, durch den auf iOS während der Token-basierten Authentifizierung keine Mobile-App-Benachrichtigungen gesendet werden können (NEO-38640).
* Fehlerkorrektur – Beim Erstellen und Konfigurieren von Berichten kommt es jetzt nicht mehr zur Anzeige von Skriptfehlermeldungen. (NEO-38393)
* Fehlerkorrektur – Auf Oracle kommt es jetzt nicht mehr zu einem Fehlschlagen des Tracking-Workflows, wenn zahlreiche Versandindikatoren gleichzeitig aktualisiert werden (NEO-39653).
* Fehlerkorrektur – Bei der Ausführung einer Kontrolltypologie kommt es jetzt nicht mehr dazu, dass ein Versand nicht erfolgt (NEO-39833).
* Fehlerkorrektur – Auf Landingpages kommt es jetzt nicht mehr dazu, dass Sonderzeichen auf den HTML-Seiten von Online-Umfrageantworten nicht korrekt angezeigt werden (NEO-39438).
* Fehlerkorrektur – In der Campaign Classic-Konsole tritt beim Rechtsklick auf einen der Ordner auf der Registerkarte &quot;Explorer&quot; kein Fehler mehr auf (NEO-38884).
* Fehlerkorrektur – Bei einem neuen Versand, bei dem die Web Analytics-Konfiguration fehlt, tritt jetzt kein Fehler mehr auf wenn eine zuvor erstellte Versandvorlage verwendet wird, die mit einem Web Analytics-Konto verknüpft ist. (NEO-28666)
* Fehlerkorrektur – Die Vorschau von Mobile-Sendungen, die mit einem Workflow verbunden sind, wird jetzt angezeigt.
* Fehlerkorrektur – Personalisierte Tracking-URLs werden jetzt umgeleitet, wenn der URL-Signaturmechanismus für Tracking-Links aktiviert ist.
* Fehlerkorrektur – Das Indexverwaltungsproblem wurde behoben, das zu Ausfällen nach einem Upgrade führen konnte.
* Fehlerkorrektur – Bei der Verwendung von Such-Felddatentypen mit Microsoft Dynamics CRM bei Aktivitäten in den Workflows **Import** oder **Export** tritt jetzt kein Fehler mehr auf.
* Fehlerkorrektur – Das Proxy-Konfigurationsproblem wurde behoben, aufgrund dessen eine Anmeldung bei der Konsole nicht möglich war. (NEO-38388)
* Es wurde ein Regressionsproblem behoben, das dazu führte, dass die Funktion **Ordner bereinigen** nicht ordnungsgemäß funktionierte. (NEO-37459)
* Fehlerkorrektur – Bei Verwendung von XML-Datenfeldern mit dem Microsoft Dynamics CRM-Konto kommt es jetzt nciht mehr zu einer fehlerhaften Anfrage, wenn die referenzierte XML doppelte Anführungszeichen enthält.
* Fehlerkorrektur – Probleme mit Netzwerküberschreitungen werden jetzt nicht mehr fälschlicherweise als Skriptunterbrechungsprobleme anstatt als Netzwerkfehler protokolliert. Dieses Problem trat bei HTTP-Anfragen auf, die in JavaScript-Aktivitäten enthalten waren. (NEO-38079)
* Es wurde ein Problem behoben, durch das beim Ausführen der HoursDiff- und MinutesDiff-Funktionen von Amazon Redshift beim Versuch, die Zeitkomponente zu extrahieren, falsche Ergebnisse ausgegeben wurden.(NEO-31673)
* Fehlerkorrektur – Der Fehler beim Laden des Berichts **Klicks** für Sendungen, der seit Build 9182 vorlag, tritt jetzt nicht mehr auf. (NEO-28900)
* Fehlerkorrektur – Das Symbol &quot;&amp;&quot; in einer URL wird jetzt nicht mehr durch die Zeichenentitätsreferenz (`&amp;`) ersetzt wurde, was Benutzer daran hinderte, auf die mit einem QR-Code verknüpfte URL zuzugreifen. (NEO-28621)
* Fehlerkorrektur – Es wird jetzt kein neues externes Konto mehr erstellt, wenn ein Benutzer einen neuen Kampagnen-Workflow und eine mit einem Web Analytics-Konto verknüpfte Versandaktivität erstellt. Dies wurde durch eine fehlende ID im Versandobjekt &quot;webAnalyticsAccount&quot; verursacht. (NEO-39691)
* Es wurde ein Problem behoben, das dazu führen konnte, dass die Workflow-Aktivität **Liste lesen** nicht funktionierte, wenn die Liste in der Datenbank mit einer negativen ID identifiziert wurde. (NEO-39607)
* Fehlerkorrektur – Der Workflow **Mid-Sourcing (Versandlogs)** schlägt jetzt nicht mehr fehl. (NEO-39662)
* Fehlerkorrektur – Bei der Vorschau von E-Mail-Sendungen, die mit einem Workflow verbunden sind, treten jetzt keine Anzeigefehler mehr auf. (NEO-37840)
* Fehlerkorrektur – Gültige Tabellen mit Listenwerten werden jetzt nicht mehr vom Datenbankbereinigungs-Workflow gelöscht. (NEO-34911)
* Fehlerkorrektur – Der Abrechnungs-Workflows bei Marketing-Instanzen stürzt jetzt nicht mehr ab.
