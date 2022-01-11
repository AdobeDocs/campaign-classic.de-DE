---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 630a62c5e5c9782c5c55fdebd651493a2d68fc54
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 30%

---

# Aktuelle Version{#latest-release}

![](../../assets/v7-only.svg)

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.2.1 – Build 9346 {#release-7-2-1}

_10. Januar 2022_

**Sicherheitsverbesserung**

An den FDA-Konten wurden verschiedene Sicherheitsverbesserungen vorgenommen:

* ODBC-Treiber werden jetzt direkt bei Adobe Campaign-Drittanbietern installiert. Für die Installation dieser Treiber sind keine manuellen Schritte mehr erforderlich.
* Bei der Konfiguration Ihres externen FDA-Kontos können Sie sich jetzt mit der Schlüsselpaar-Authentifizierung bei Ihrem Snowflake-Konto anmelden, um die Authentifizierungssicherheit zu verbessern. [Mehr dazu](../../installation/using/configure-fda-snowflake.md)
* Beim Konfigurieren Ihres externen FDA-Kontos können Sie sich jetzt mit der systemzugewiesenen verwalteten Identität bei Ihrem Azure synapse Analytics-Konto anmelden. [Mehr dazu](../../installation/using/configure-fda-synapse.md#azure-external)
* Alle Verweise auf die Bibliothek log4j wurden aus Campaign entfernt, um eine optimale Sicherheit zu gewährleisten.

**Verbesserungen**

* Microsoft Dynamics CRM 365 Connector

   Es wurden kritische Fehlerbehebungen bei der Web-API des Microsoft Dynamics-Connectors vorgenommen:

   * Fehlerkorrektur – Beim Import, der durch einen Workflow ausgelöst wird, werden jetzt die Nullwerte von Feldern vom Typ Zeichenfolge als leere Werte statt als Null gespeichert.
   * Fehlerkorrektur – Beim Datenimport oder -export mithilfe von Web-API-Aufrufen tritt jetzt nicht mehr der Fehler „Ungültiger URI: Das URI-Schema ist zu lang“ auf:
   * Es wurden verschiedene Probleme beim Importieren von Daten mit Suchfeldern aus Microsoft Dynamics 365 behoben.

* Google BigQuery FDA-Connector

   * Google BigQuery FDA Connector ist jetzt für gehostete Bereitstellungen verfügbar. [Mehr dazu](../../installation/using/configure-fda-google-big-query.md)
   * Unterstützung zum Aktivieren von Verbindungen zu einem Proxy-Server für den Google BigQuery FDA-Connector hinzugefügt. Die erforderlichen Proxy-Optionen können über das Feld Optionen in der Konfiguration des externen Kontos festgelegt werden. [mehr dazu](../../installation/using/configure-fda-google-big-query.md#google-external)

**Sonstige Änderungen**

* Nach der Einstellung wurden die Aktionsaktivitäten Microsoft CRM, Salesforce und Oracle CRM On Demand aus der Benutzeroberfläche entfernt. Um die Datensynchronisation zwischen Adobe Campaign und einem CRM-System zu konfigurieren, können Sie die Aktivität „CRM-Connector“ verwenden. [Mehr dazu](../../workflow/using/crm-connector.md)
* Die **[!UICONTROL Verschlüsselte Kennung]** wurde dem Besucherschema (nms:visitor) hinzugefügt. Dieses Feld wird berechnet und ist für Web-Programme vorgesehen. Dies gilt, wenn der Kanal Line in der Mid-Sourcing-Instanz konfiguriert ist.
* CRM-Datenquellen können jetzt mit der **Datenquelle ändern** Aktivität.
* Eine neue Option wurde im **Umgang mit Fehlern** Eigenschaften von Workflow-Aktivitäten: Die **Abbruch bei Fehler** wird der Workflow automatisch angehalten. Danach können Sie es nicht mehr neu starten (NEO-29661). [Mehr dazu](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* Die Primärschlüssel der nmsGroup -Tabelle werden jetzt in einer speziellen Sequenz erzeugt, die zur Erstellung statistischer Empfängergruppen verwendet wird. Zuvor wurde die Sequenz &quot;xtknownId&quot;verwendet. (NEO-30832)
* Unterstützung für Batch-Aktualisierungsvorgänge mit der Aktivität CRM-Connector hinzugefügt.
* Verbesserte Leistung bei der Verarbeitungszeit für Transaktionsnachrichten. (NEO-40370)

**Patches**

* Fehlerkorrektur - bei der Erstellung eines Versands tritt kein Fehler mehr in der **Bilder** des **Tracking und Bilder** Fenster. Dies trat bei der Verwendung einer automatischen Proxy-Konfiguration auf. (NEO-33260)
* Fehlerkorrektur - Es wurde ein Problem behoben, das das Hochladen einer Datei auf einen Debian 10-Server (HTTPS) im synchronen Modus verhindern konnte.
* Fehlerkorrektur - Datensätze der Versandstatistiken werden jetzt korrekt erfasst (`nmsDeliveryLogStats`) nicht aus der Mid-Sourcing-Instanz während der Datenbankbereinigung gelöscht werden, nachdem die entsprechenden Sendungen gelöscht wurden. (NEO-31034)
* Fehlerkorrektur - Mobile-App-Benachrichtigungen können jetzt unter Verwendung der Token-basierten Authentifizierung an iOS gesendet werden. (NEO-38640)
* Fehlerkorrektur - Beim Erstellen und Konfigurieren von Berichten werden jetzt keine Skriptfehlermeldungen mehr angezeigt. (NEO-38393)
* Fehlerkorrektur - Der Tracking-Workflow schlägt auf dem Oracle nicht mehr fehl, da zahlreiche Versandindikatoren gleichzeitig aktualisiert werden. (NEO-39653)
* Fehlerkorrektur - Versand ist jetzt möglich, wenn bei der Ausführung einer Kontrolltypologie ein Fehler auftritt (NEO-39833).
* Fehlerkorrektur - Auf Landingpages werden Sonderzeichen jetzt auf den HTML-Seiten von Online-Umfrageantworten korrekt angezeigt. (NEO-39438)
* Fehlerkorrektur - Die Campaign Classic-Konsole funktioniert jetzt, wenn Sie mit der rechten Maustaste auf einen der Ordner im Explorer-Tab klicken (NEO-38884).
* Fehlerkorrektur - bei der Verwendung einer zuvor erstellten Versandvorlage, die mit einem Web Analytics-Konto verknüpft ist, in einem neuen Versand, in dem die Web Analytics-Konfiguration fehlt, tritt kein Fehler mehr auf. (NEO-28666)
* Es wurde ein Problem behoben, das dazu führen konnte, dass die Vorschau von Mobile-Sendungen, die mit einem Workflow verbunden waren, nicht angezeigt wurde.
* Fehlerkorrektur - personalisierte Tracking-URLs können jetzt umgeleitet werden, wenn der URL-Signaturmechanismus für Tracking-Links aktiviert ist.
* Fehlerkorrektur - Postupgrade-Fehler können jetzt aufgrund eines Indexverwaltungsproblems auftreten.
* Fehlerkorrektur - bei der Verwendung von Lookup-Felddatentypen mit Microsoft Dynamics CRM in **Import** oder **Export** Workflow-Aktivitäten.
* Fehlerkorrektur - Jetzt können Sie sich wegen eines Proxy-Konfigurationsproblems nicht mehr bei der Konsole anmelden. (NEO-38388)
* Es wurde ein Regressionsproblem behoben, das dazu führte, dass die Funktion **Ordner bereinigen** nicht ordnungsgemäß funktionierte. (NEO-37459)
* Fehlerkorrektur - Bei der Verwendung von XML-Datenfeldern mit dem Microsoft Dynamics CRM-Konto tritt jetzt kein Fehler mehr auf, wenn die referenzierte XML doppelte Anführungszeichen enthält.
* Es wurde ein Fehler behoben, der dazu führte, dass Probleme mit Netzwerküberschreitungen fälschlicherweise als Skriptunterbrechungsprobleme anstatt als Netzwerkfehler protokolliert wurden. Dieses Problem trat bei HTTP-Anfragen auf, die in JavaScript-Aktivitäten enthalten waren. (NEO-38079)
* Es wurde ein Problem behoben, durch das beim Ausführen der HoursDiff- und MinutesDiff-Funktionen von Amazon Redshift beim Versuch, die Zeitkomponente zu extrahieren, falsche Ergebnisse ausgegeben wurden.(NEO-31673)
* Fehlerkorrektur - Die **Klicks** -Bericht aus dem Laden für Sendungen seit Build 9182. (NEO-28900)
* Fehlerkorrektur - das Symbol &amp; in einer URL wird nun auch dann korrekt ersetzt, wenn die Entitätsreferenz (`&amp;`) verhindert, dass Benutzer auf die mit einem QR-Code verknüpfte URL zugreifen können. (NEO-28621)
* Fehlerkorrektur - Jetzt wird kein neues externes Konto mehr erstellt, wenn ein Benutzer einen neuen Kampagnen-Workflow und eine mit einem Web Analytics-Konto verknüpfte Versandaktivität erstellt. Dies wurde durch eine fehlende ID im Bereitstellungsobjekt webAnalyticsAccount verursacht. (NEO-39691)
* Es wurde ein Problem behoben, das dazu führen konnte, dass die Workflow-Aktivität **Liste lesen** nicht funktionierte, wenn die Liste in der Datenbank mit einer negativen ID identifiziert wurde. (NEO-39607)
* Es wurde ein Problem behoben, durch das die **Mid-Sourcing (Versandlogs)** fehlgeschlagener Workflow. (NEO-39662)
* Fehlerkorrektur - E-Mail-Sendungen, die an einen Workflow angehängt sind, können jetzt in der Vorschau angezeigt werden. (NEO-37840)
* Fehlerkorrektur - jetzt werden vom Datenbankbereinigungs-Workflow keine gültigen Tabellen mehr gelöscht, die Listenwerte enthalten. (NEO-34911)
* Es wurde ein Problem behoben, das zum Absturz des Abrechnungs-Workflows bei Marketing-Instanzen führen konnte.
