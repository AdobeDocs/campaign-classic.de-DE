---
product: campaign
title: Personalisierung und Datenschutz
description: Best Practices für die Sicherheit von Datenschutz und Personalisierung
feature: URL Personalization, Privacy
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: f97199e634205742b74a08932a40db2fca138cc3
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 27%

---

# Personalisierung und Datenschutz {#privacy}

![](../../assets/v7-only.svg)


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

1. Erstellen Sie einen Workflow und fügen Sie einen **Abfrage** Aktivität. [Weitere Informationen](../../workflow/using/query.md).

1. Öffnen Sie die **Abfrage** und erstellen Sie einen Filter für die `nmsTrackingUrl` Tabelle wie folgt:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Führen Sie den Workflow aus und prüfen Sie, ob Ergebnisse vorliegen.

1. Sollte dies der Fall sein, öffnen Sie die ausgehende Transition, um die Liste der URLs anzuzeigen.

   ![](assets/privacy-query-dynamic-url.png)


### URL-Signatur

Um die Sicherheit zu verbessern, wurde ein Signaturmechanismus für das Tracking von Links in E-Mails eingeführt. Sie ist ab den Builds 19.1.4 (9032@3a9dc9c) und 20.2 verfügbar. Diese Funktion ist standardmäßig aktiviert.

>[!NOTE]
>
>Wenn auf eine fehlerhafte signierte URL geklickt wird, wird dieser Fehler zurückgegeben: `Requested URL '…' was not found.`

Darüber hinaus können Sie eine Verbesserung verwenden, um in früheren Builds generierte URLs zu deaktivieren. Diese Funktion ist standardmäßig deaktiviert. Sie können sich an [Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) um diese Funktion zu aktivieren.

Wenn Sie mit Build 19.1.4 arbeiten, können Probleme beim Versand von Push-Benachrichtigungen unter Verwendung von Tracking-Links oder bei Sendungen unter Verwendung von Anker-Tags auftreten. In diesem Fall wird empfohlen, die URL-Signatur zu deaktivieren.

Als gehosteter, verwalteter oder hybrider Cloud Services einer Kampagne müssen Sie Kontakt mit [Kundenunterstützung](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) , damit die URL-Signatur deaktiviert wird.

Wenn Sie Campaign in einer Hybridarchitektur ausführen, stellen Sie vor der Aktivierung der URL-Signatur sicher, dass die gehostete Mid-Sourcing-Instanz wie folgt aktualisiert wurde:

* Zunächst die On-Premise-Marketing-Instanz
* Aktualisieren Sie dann auf dieselbe Version wie die On-Premise-Marketing-Instanz oder auf eine etwas höhere Version

Andernfalls können einige dieser Probleme auftreten:

* Bevor die Mid-Sourcing-Instanz aktualisiert wird, werden URLs über diese Instanz ohne Signatur gesendet.
* Nachdem die Mid-Sourcing-Instanz aktualisiert und die URL-Signatur auf beiden Instanzen aktiviert wurde, werden die URLs, die zuvor ohne Signatur gesendet wurden, abgelehnt. Der Grund dafür ist, dass eine Signatur von den Tracking-Dateien angefordert wird, die von der Marketing-Instanz bereitgestellt wurden.

Um in früheren Builds generierte URLs zu deaktivieren, führen Sie die folgenden Schritte auf allen Campaign-Servern gleichzeitig aus:

1. In der Server-Konfigurationsdatei (`serverConf.xml`), ändern Sie die **blockRedirectForUnsignedTrackingLink** -Option **true**.
1. Starten Sie den `nlserver` Dienst.
1. Im `tracking` Server, starten Sie die `web` -Server (Apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows).

Um die URL-Signatur zu aktivieren, führen Sie die folgenden Schritte auf allen Campaign-Servern gleichzeitig aus:

1. In der Server-Konfigurationsdatei (`serverConf.xml`), ändern **signEmailLinks** Option, um **true**.
1. Starten Sie den **nlserver**-Service neu.
1. Im `tracking` Server, starten Sie die `web` -Server (Apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows).

## Dateneinschränkung

Sie müssen sicherstellen, dass die verschlüsselten Kennwörter für authentifizierte Benutzer mit geringer Berechtigung nicht zugänglich sind. Schränken Sie dazu den Zugriff auf Kennwortfelder oder auf die gesamte Entität ein (Build >= 8770 erforderlich).

Mit dieser Einschränkung können Sie Passwortfelder entfernen, das externe Konto jedoch für alle Benutzer über die Benutzeroberfläche zugänglich machen. [Weitere Informationen](../../configuration/using/restricting-pii-view.md).

Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zum **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** Ordner des Campaign-Explorers.

1. Erstellen Sie ein Datenschema als **[!UICONTROL Erweiterung eines Schemas]**.

   ![](assets/privacy-data-restriction.png)

1. Wählen Sie **[!UICONTROL Externes Konto]** aus (extAccount).

1. Bearbeiten Sie im letzten Assistenten-Bildschirm Ihr neues &quot;srcSchema&quot;, um den Zugriff auf alle Kennwortfelder zu beschränken:

   Das Hauptelement (`<element name="extAccount" ... >`) können Sie ersetzen durch:

   ```sql
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

   ```sql
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

## Protect-Seiten mit API

Wir empfehlen On-Premise-Kunden dringend, die Seiten zu schützen, die möglicherweise personenbezogene Daten (PIs) enthalten, z. B. Mirrorseiten, Webanwendungen usw.

Ziel dieses Verfahrens ist es, dass diese Seiten nicht indexiert werden, um ein mögliches Sicherheitsrisiko zu verhindern. Hier finden Sie einige hilfreiche Artikel:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Führen Sie die folgenden Schritte aus, um Ihre Seiten zu schützen:

1. Hinzufügen einer `robots.txt` -Datei im Stammverzeichnis Ihres Webservers (Apache oder IIS). Im Folgenden finden Sie den Inhalt der Datei:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Informationen zu IIS finden Sie unter [diese Seite](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Für Apache können Sie die Datei in **/var/www/robots.txt** (Debian).

1. Manchmal wird eine **robots.txt** -Datei ist im Hinblick auf die Sicherheit nicht ausreichend. Wenn beispielsweise eine andere Website einen Link zu Ihrer Seite enthält, kann diese in einem Suchergebnis angezeigt werden.

   Es ist deshalb empfehlenswert, neben der **robots.txt**-Datei einen **X-Robots-Tag**-Header hinzuzufügen. Dies ist sowohl in Apache als auch in IIS sowie in der Konfigurationsdatei **serverConf.xml** möglich.

   Weitere Informationen finden Sie unter [diesem Artikel](https://developers.google.com/search/reference/robots_meta_tag).


## Datenschutzanfragen

Siehe [diese Seite](../../platform/using/privacy-management.md) für allgemeine Informationen zu den Funktionen der Datenschutzverwaltung und den Implementierungsschritten in Adobe Campaign. Darüber hinaus finden Sie Best Practices und einen Überblick über den Benutzerprozess und die Rollen.
