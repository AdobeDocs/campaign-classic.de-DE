---
solution: Campaign Classic
product: campaign
title: Datenschutz
description: Erfahren Sie mehr über die Best Practices zum Schutz der Privatsphäre.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 47%

---


# Datenschutz {#privacy}

## Datenschutzanfragen

Adobe Campaign bietet eine Reihe von Tools, die Sie bei der Einhaltung von Datenschutzbestimmungen wie DSGVO und CCPA unterstützen.

Auf [dieser Seite](../../platform/using/privacy-management.md) finden Sie allgemeine Informationen zu den Schritten in Adobe Campaign zum Datenschutzmanagement. Darüber hinaus finden Sie Best Practices und einen Überblick über den Benutzerprozess und die Personas.

## URL-Personalisierung

Wenn Sie personalisierte Links zu Ihrem Inhalt hinzufügen, achten Sie darauf, dass im Hostname-Teil der URL keine Personalisierung vorhanden ist. So lassen sich mögliche Sicherheitslücken verhindern. Die folgenden Beispiele sollten niemals in allen URL-Attributen &lt;`a href="">` oder `<img src="">` verwendet werden:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Empfehlung

Um zu überprüfen und sicherzustellen, dass Sie oben nicht verwenden, führen Sie eine Abfrage zur Verfolgung der URL-Tabelle über [Kampagne-Generische Abfragetool](../../platform/using/steps-to-create-a-query.md) aus oder erstellen Sie einen Arbeitsablauf mit Filterkriterien in der Aktivität [Abfrage](../../workflow/using/query.md).

Beispiel:

1. Erstellen Sie einen Workflow und fügen Sie eine Abfrage-Aktivität hinzu. Mehr dazu.

1. Öffnen Sie die Aktivität &quot;Abfrage&quot;und erstellen Sie in der Tabelle &quot;nmsTrackingUrl&quot;einen Filter wie folgt: Quell-URL-Beginn mit http://&lt;% oder Quell-URL-Beginn mit https://&lt;%.

1. Führen Sie den Workflow aus und prüfen Sie, ob Ergebnisse vorliegen.

1. Sollte dies der Fall sein, öffnen Sie die ausgehende Transition, um die Liste der URLs anzuzeigen.

<img src="assets/privacy-query-dynamic-url.png">

### Signaturmechanismus

Um die Sicherheit zu verbessern, wurde in Build 19.1.4 (9032@3a9dc9c) ein neuer Signaturmechanismus für die Verfolgung von Links in E-Mails eingeführt und ist in Build 19.1.4 (9032@3a9dc9c) und Kampagne 20.2 verfügbar. Diese Option ist standardmäßig für alle Kunden aktiviert.

>[!NOTE]
>
>Wenn auf eine fehlerhafte signierte URL geklickt wird, wird der folgende Fehler zurückgegeben: „Angeforderte URL &#39;... &#39; wurde nicht gefunden.“

Darüber hinaus können gehostete und hybride Kunden auf Build 19.1.4 (9032@3a9dc9c und 9032@800be2e) und auf Kampagne 20.2 eine Verbesserung verwenden, um URLs zu deaktivieren, die aus vorherigen Builds generiert wurden. Standardmäßig ist diese Option deaktiviert. Sie können sich an [Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) wenden, um diese Funktion zu aktivieren.

Um diesen neuen Mechanismus zu aktivieren, müssen On-Premise-Kunden auf allen Campaign-Servern die folgenden Schritte ausführen:

1. Ändern Sie in der Server-Konfigurationsdatei (serverConf.xml) **blockRedirectForUnsignedTrackingLink** in **true**.
1. Starten Sie den **nlserver**-Dienst neu.
1. Starten Sie auf dem Tracking-Server den Webserver neu (Apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows).

Bei Kunden, die auf Build 19.1.4 (9032@3a9dc9c) ausgeführt werden, kann es zu Problemen mit Push-Benachrichtigungs-Versänden mit einem Verfolgungslink oder Versänden mit Anker-Tags kommen. In diesem Fall empfiehlt Adobe, den neuen Signaturmechanismus für die Verfolgung von Links zu deaktivieren:

**Hosted- und Hybrid-** Kunden müssen sich an die  [Kundenbetreuung wenden, damit dieser Mechanismus deaktiviert ](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) wird.

**Gehen Sie wie folgt vor, um den lokalen** Kunden Folgendes anzuzeigen:

1. Ändern Sie in der Serverkonfigurationsdatei (serverConf.xml) **signEmailLinks** in **false**.
1. Starten Sie den **nlserver**-Dienst neu.
1. Starten Sie auf dem Tracking-Server den Webserver neu (Apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows).

## Dateneinschränkung

Sie müssen sicherstellen, dass keine authentifizierten Benutzer mit unzureichender Berechtigung auf die verschlüsselten Passwörter zugreifen können. Dazu gibt es zwei Möglichkeiten: den Zugriff auf Kennwortfelder oder die gesamte Entität einschränken (Erstellen >= 8770 erforderlich).

Mit dieser Einschränkung können Sie Passwortfelder entfernen, das externe Konto jedoch für alle Benutzer über die Benutzeroberfläche zugänglich machen. Mehr dazu erfahren Sie auf [dieser Seite](../../configuration/using/restricting-pii-view.md).

1. Gehen Sie zu **[!UICONTROL Administration]** > **[!UICONTROL Konfigurieren]** > **[!UICONTROL Datenschemata]**.

1. Erstellen Sie eine neue **[!UICONTROL Schemaerweiterung]**.

   ![](assets/privacy-data-restriction.png)

1. Wählen Sie **[!UICONTROL Externes Konto]** aus (extAccount).

1. Bearbeiten Sie im letzten Fenster des Assistenten Ihr neues srcSchema, um den Zugriff auf alle Passwortfelder einzuschränken:

   Sie können das Hauptelement (`<element name="extAccount" ... >`) wie folgt ersetzen:

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   So kann Ihr erweitertes srcSchema aussehen:

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >Sie können `$(loginId) = 0 or $(login) = 'admin'` durch `hasNamedRight('admin')` ersetzen, damit alle Benutzer mit Admin-Recht diese Kennwörter sehen können.

## Schutz von Seiten, die personenbezogene Daten enthalten

Wir empfehlen On-Premise-Kunden dringend, Seiten zu schützen, die möglicherweise personenbezogene Daten enthalten (z. B. Mirrorseiten, Webanwendungen usw.).

Ziel dieses Verfahrens ist es, dass diese Seiten nicht indexiert werden, um ein mögliches Sicherheitsrisiko zu verhindern. Hier finden Sie einige hilfreiche Artikel:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Führen Sie die folgenden Schritte aus, um Ihre Seiten zu schützen:

1. Fügen Sie eine robots.txt-Datei zur Wurzel Ihres Webservers hinzu (Apache oder IIS). Hier der Dateiinhalt:

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Bei IIS finden Sie auf [diese Seite](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Für Apache können Sie die Datei in **/var/www/robots.txt** (Debian) platzieren.

1. Manchmal reicht das Hinzufügen einer **robots.txt**-Datei hinsichtlich der Sicherheit nicht aus. Wenn eine andere Website beispielsweise einen Link zu Ihrer Seite enthält, könnte sie in einem Suchergebnis angezeigt werden.

Es ist deshalb empfehlenswert, neben der **robots.txt**-Datei einen **X-Robots-Tag**-Header hinzuzufügen. Dies ist sowohl in Apache als auch in IIS sowie in der Konfigurationsdatei **serverConf.xml** möglich.

Weitere Informationen finden Sie in [diesem Artikel](https://developers.google.com/search/reference/robots_meta_tag).
