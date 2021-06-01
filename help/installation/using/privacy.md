---
product: campaign
title: Datenschutz
description: Erfahren Sie mehr über die Best Practices für den Datenschutz.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 57%

---

# Datenschutz {#privacy}

## Datenschutzanfragen

Adobe Campaign bietet eine Reihe von Tools, die Sie bei der Einhaltung von Datenschutzbestimmungen wie DSGVO und CCPA unterstützen.

Allgemeine Informationen dazu, was unter Datenschutzverwaltung zu verstehen ist, und zu den Implementierungsschritten in Adobe Campaign finden Sie auf [dieser Seite](../../platform/using/privacy-management.md) . Darüber hinaus finden Sie Best Practices und einen Überblick über den Benutzerprozess und die Rollen.

## URL-Personalisierung {#url-personalization}

Wenn Sie personalisierte Links zu Ihrem Inhalt hinzufügen, achten Sie darauf, dass im Hostname-Teil der URL keine Personalisierung vorhanden ist. So lassen sich mögliche Sicherheitslücken verhindern. Folgende Beispiele sollten niemals in den URL-Attributen `a href="">` oder `<img src="">` verwendet werden:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Empfehlung

Um zu überprüfen und sicherzustellen, dass Sie oben nicht verwenden, führen Sie eine Abfrage zur Tracking-URL-Tabelle über den [Generischen Abfrage-Editor für Kampagnen](../../platform/using/steps-to-create-a-query.md) aus oder erstellen Sie einen Workflow mit Filterkriterien in der [Abfrageaktivität](../../workflow/using/query.md).

Beispiel:

1. Erstellen Sie einen Workflow und fügen Sie die Aktivität Abfrage hinzu. Mehr dazu.

1. Öffnen Sie die Aktivität Abfrage und erstellen Sie wie folgt einen Filter für die Tabelle nmsTrackingUrl : Die Quell-URL beginnt mit http://&lt;% oder die Quell-URL beginnt mit https://&lt;%.

1. Führen Sie den Workflow aus und prüfen Sie, ob Ergebnisse vorliegen.

1. Sollte dies der Fall sein, öffnen Sie die ausgehende Transition, um die Liste der URLs anzuzeigen.

<img src="assets/privacy-query-dynamic-url.png">

### Signaturmechanismus

Um die Sicherheit zu verbessern, wurde in Build 19.1.4 (9032@3a9dc9c) ein neuer Signaturmechanismus zum Tracking von Links in E-Mails eingeführt, der in Build 19.1.4 (9032@3a9dc9c) und Campaign 20.2 verfügbar ist. Diese Option ist standardmäßig für alle Kunden aktiviert.

>[!NOTE]
>
>Wenn auf eine fehlerhafte signierte URL geklickt wird, wird der folgende Fehler zurückgegeben: „Angeforderte URL &#39;... &#39; wurde nicht gefunden.“

Darüber hinaus können gehostete und hybride Kunden ab Campaign-Version 20.2 und [!DNL Gold Standard] eine Verbesserung verwenden, um aus früheren Builds generierte URLs zu deaktivieren. Standardmäßig ist diese Option deaktiviert. Sie können sich an [Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) wenden, um diese Funktion zu aktivieren.

Um diesen neuen Mechanismus zu aktivieren, müssen On-Premise-Kunden auf allen Campaign-Servern die folgenden Schritte ausführen:

1. Ändern Sie in der Server-Konfigurationsdatei (serverConf.xml) **blockRedirectForUnsignedTrackingLink** in **true**.
1. Starten Sie den **nlserver**-Service neu.
1. Starten Sie den Webserver (apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows) auf dem Trackingserver neu.

Kunden, die mit [!DNL Gold Standard] 19.1.4 arbeiten, können Probleme mit Push-Benachrichtigungsversand über einen Trackinglink oder mit Sendungen über Anker-Tags haben. Wenn ja, empfiehlt Adobe, den neuen Signaturmechanismus für Tracking-Links zu deaktivieren:

**Gehostete und hybride** Kunden müssen sich an die  [Kundenunterstützung wenden, ](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) damit dieser Mechanismus deaktiviert wird.

**Gehen Sie wie folgt vor, um On-Premise-** Kunden-Scan durchzuführen:

1. Ändern Sie in der Server-Konfigurationsdatei (serverConf.xml) den Eintrag für **signEmailLinks** in **false**.
1. Starten Sie den **nlserver**-Service neu.
1. Starten Sie den Webserver (apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows) auf dem Trackingserver neu.

## Dateneinschränkung

Sie müssen sicherstellen, dass keine authentifizierten Benutzer mit unzureichender Berechtigung auf die verschlüsselten Passwörter zugreifen können. Dazu gibt es zwei Möglichkeiten: den Zugriff auf Kennwortfelder oder auf die gesamte Entität beschränken (Build >= 8770 erforderlich).

Mit dieser Einschränkung können Sie Passwortfelder entfernen, das externe Konto jedoch für alle Benutzer über die Benutzeroberfläche zugänglich machen. Mehr dazu erfahren Sie auf [dieser Seite](../../configuration/using/restricting-pii-view.md).

1. Gehen Sie zu **[!UICONTROL Administration]** > **[!UICONTROL Konfigurieren]** > **[!UICONTROL Datenschemata]**.

1. Erstellen Sie eine neue **[!UICONTROL Schemaerweiterung]**.

   ![](assets/privacy-data-restriction.png)

1. Wählen Sie **[!UICONTROL Externes Konto]** aus (extAccount).

1. Bearbeiten Sie im letzten Fenster des Assistenten Ihr neues srcSchema, um den Zugriff auf alle Passwortfelder einzuschränken:

   Das Hauptelement (`<element name="extAccount" ... >`) können Sie ersetzen durch:

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

   Ihr erweitertes srcSchema sieht dann folgendermaßen aus:

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
   >Sie können `$(loginId) = 0 or $(login) = 'admin'` durch `hasNamedRight('admin')` ersetzen, damit alle Benutzer mit Administratorrechten diese Kennwörter sehen können.

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

   Informationen zu IIS finden Sie auf [dieser Seite](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Für Apache können Sie die Datei in **/var/www/robots.txt** (Debian) platzieren.

1. Manchmal reicht das Hinzufügen einer **robots.txt**-Datei aus Sicherheitsgründen nicht aus. Wenn beispielsweise eine andere Website einen Link zu Ihrer Seite enthält, kann diese in einem Suchergebnis angezeigt werden.

Es ist deshalb empfehlenswert, neben der **robots.txt**-Datei einen **X-Robots-Tag**-Header hinzuzufügen. Dies ist sowohl in Apache als auch in IIS sowie in der Konfigurationsdatei **serverConf.xml** möglich.

Weitere Informationen finden Sie in [diesem Artikel](https://developers.google.com/search/reference/robots_meta_tag).
