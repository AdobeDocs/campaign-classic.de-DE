---
product: campaign
title: Datenschutz
description: Erfahren Sie mehr über die Best Practices für den Datenschutz.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 45%

---

# Datenschutz {#privacy}

![](../../assets/v7-only.svg)

## Datenschutzanfragen

Adobe Campaign bietet eine Reihe von Tools, die Sie bei der Einhaltung von Datenschutzbestimmungen wie DSGVO und CCPA unterstützen.

Siehe [diese Seite](../../platform/using/privacy-management.md) für allgemeine Informationen zu den Funktionen der Datenschutzverwaltung und den Implementierungsschritten in Adobe Campaign. Darüber hinaus finden Sie Best Practices und einen Überblick über den Benutzerprozess und die Rollen.

## URL-Personalisierung {#url-personalization}

Wenn Sie personalisierte Links zu Ihrem Inhalt hinzufügen, achten Sie darauf, dass im Hostname-Teil der URL keine Personalisierung vorhanden ist. So lassen sich mögliche Sicherheitslücken verhindern. Folgende Beispiele sollten niemals in den URL-Attributen &lt;`a href="">` oder `<img src="">` verwendet werden:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Empfehlung

Um zu überprüfen und sicherzustellen, dass Sie oben nicht verwenden, führen Sie eine Abfrage zur Tracking-URL-Tabelle über aus. [Generischer Kampagnenabfrage-Editor](../../platform/using/steps-to-create-a-query.md) oder erstellen Sie einen Workflow mit Filterkriterien im [Abfrageaktivität](../../workflow/using/query.md).

Beispiel:

1. Erstellen Sie einen Workflow und fügen Sie die Aktivität Abfrage hinzu. Mehr dazu.

1. Öffnen Sie die Aktivität Abfrage und erstellen Sie wie folgt einen Filter für die Tabelle nmsTrackingUrl : Die Quell-URL beginnt mit http://&lt;% oder die Quell-URL beginnt mit https://&lt;%.

1. Führen Sie den Workflow aus und prüfen Sie, ob Ergebnisse vorliegen.

1. Sollte dies der Fall sein, öffnen Sie die ausgehende Transition, um die Liste der URLs anzuzeigen.

<img src="assets/privacy-query-dynamic-url.png">

### URL-Signatur

Um die Sicherheit zu verbessern, wurde ein Signaturmechanismus für das Tracking von Links in E-Mails eingeführt. Sie ist in Build 19.1.4 (9032@3a9dc9c) und Campaign 20.2 verfügbar. Diese Funktion ist standardmäßig aktiviert.

>[!NOTE]
>
>Wenn auf eine fehlerhafte signierte URL geklickt wird, wird dieser Fehler zurückgegeben: &quot;Angeforderte URL &#39;...&#39; wurde nicht gefunden.&quot;

Außerdem wurde seit Campaign 20.2 und der [!DNL Gold Standard] -Version verwenden, können Sie eine Verbesserung verwenden, um in früheren Builds generierte URLs zu deaktivieren. Diese Funktion ist standardmäßig deaktiviert. Sie können sich an [Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) um diese Funktion zu aktivieren.

Wenn Sie [!DNL Gold Standard] 19.1.4 können Probleme beim Versand von Push-Benachrichtigungen mithilfe von Tracking-Links oder bei Sendungen mit Anker-Tags auftreten. In diesem Fall wird empfohlen, die URL-Signatur zu deaktivieren.

Unabhängig davon, ob Sie Campaign vor Ort oder in einer Hybridarchitektur ausführen, müssen Sie sich an folgende Adresse wenden: [Kundenunterstützung](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) , damit die URL-Signatur deaktiviert wird.

Wenn Sie Campaign in einer Hybridarchitektur ausführen, stellen Sie vor der Aktivierung der URL-Signatur sicher, dass die gehostete Mid-Sourcing-Instanz wie folgt aktualisiert wurde:
* Vor der lokalen Marketinginstanz
* Auf dieselbe Version wie die lokale Marketinginstanz oder auf eine etwas höhere Version

Andernfalls können einige dieser Probleme auftreten:
* Bevor die Mid-Sourcing-Instanz aktualisiert wird, werden URLs über diese Instanz ohne Signatur gesendet.
* Nachdem die Mid-Sourcing-Instanz aktualisiert und die URL-Signatur auf beiden Instanzen aktiviert wurde, werden die URLs, die zuvor ohne Signatur gesendet wurden, abgelehnt. Der Grund dafür ist, dass eine Signatur von den Tracking-Dateien angefordert wird, die von der Marketing-Instanz bereitgestellt wurden.

Um in früheren Builds generierte URLs zu deaktivieren, führen Sie die folgenden Schritte auf allen Campaign-Servern gleichzeitig aus:

1. Ändern Sie in der Server-Konfigurationsdatei (serverConf.xml) **blockRedirectForUnsignedTrackingLink** in **true**.
1. Starten Sie den **nlserver**-Service neu.
1. Starten Sie den Webserver (apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows) auf dem Trackingserver neu.

Um die URL-Signatur zu aktivieren, führen Sie die folgenden Schritte auf allen Campaign-Servern gleichzeitig aus:

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
   >Sie können `$(loginId) = 0 or $(login) = 'admin'` mit `hasNamedRight('admin')` , damit alle Benutzer mit Administratorrechten diese Passwörter sehen können.

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

   Informationen zu IIS finden Sie unter [diese Seite](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Für Apache können Sie die Datei in **/var/www/robots.txt** (Debian).

1. Manchmal wird eine **robots.txt** -Datei ist im Hinblick auf die Sicherheit nicht ausreichend. Wenn beispielsweise eine andere Website einen Link zu Ihrer Seite enthält, kann diese in einem Suchergebnis angezeigt werden.

Es ist deshalb empfehlenswert, neben der **robots.txt**-Datei einen **X-Robots-Tag**-Header hinzuzufügen. Dies ist sowohl in Apache als auch in IIS sowie in der Konfigurationsdatei **serverConf.xml** möglich.

Weitere Informationen finden Sie unter [diesem Artikel](https://developers.google.com/search/reference/robots_meta_tag).
