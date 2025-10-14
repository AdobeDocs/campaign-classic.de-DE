---
product: campaign
title: Personalisierung und Datenschutz
description: Best Practices für die Sicherheit für Datenschutz und Personalisierung
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 20%

---

# Personalisierung und Datenschutz {#privacy}

## URL-Personalisierung {#url-personalization}

Wenn Sie personalisierte Links zu Ihrem Inhalt hinzufügen, achten Sie darauf, dass im Hostname-Teil der URL keine Personalisierung vorhanden ist. So lassen sich mögliche Sicherheitslücken verhindern. Folgende Beispiele sollten niemals in den URL-Attributen &lt;`a href="">` oder `<img src="">` verwendet werden:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Empfehlung

Um zu validieren und sicherzustellen, dass Sie die oben genannten Funktionen nicht verwenden, führen Sie eine Abfrage in der Tracking-URL-Tabelle über [Campaign Generic Query Editor) ](../../platform/using/about-queries-in-campaign.md) oder erstellen Sie einen Workflow mit Filterkriterien in der Abfrageaktivität. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=de){target="_blank"}.

Beispiel:

1. Erstellen Sie einen Workflow und fügen Sie eine Aktivität **Abfrage** hinzu. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/query.html?lang=de){target="_blank"}.

1. Öffnen Sie die **Abfrage**-Aktivität und erstellen Sie wie folgt einen Filter für die `nmsTrackingUrl`-Tabelle:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Führen Sie den Workflow aus und prüfen Sie, ob Ergebnisse vorliegen.

1. Sollte dies der Fall sein, öffnen Sie die ausgehende Transition, um die Liste der URLs anzuzeigen.

   ![](assets/privacy-query-dynamic-url.png)


### URL-Signatur

Um die Sicherheit zu verbessern, wurde ein Signaturmechanismus zum Tracking von Links in E-Mails eingeführt. Es ist ab den Builds 19.1.4 (9032@3a9dc9c) und 20.2 verfügbar. Diese Funktion ist standardmäßig aktiviert.

>[!NOTE]
>
>Beim Klicken auf eine falsch formatierte signierte URL wird dieser Fehler zurückgegeben: `Requested URL '…' was not found.`

Darüber hinaus können Sie eine Verbesserung verwenden, um in vorherigen Builds generierte URLs zu deaktivieren. Diese Funktion ist standardmäßig deaktiviert. Sie können sich an die [Kundenunterstützung“ wenden](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) um diese Funktion zu aktivieren.

Wenn Sie mit dem Build 19.1.4 arbeiten, können Probleme mit Push-Benachrichtigungs-Sendungen unter Verwendung von Tracking-Links oder Sendungen unter Verwendung von Anker-Tags auftreten. Wenn ja, empfehlen wir, die URL-Signatur zu deaktivieren.

Als gehosteter Campaign-, Managed Cloud Services- oder Hybrid-Kunde müssen Sie sich an die [Kundenunterstützung“ wenden](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die URL-Signatur deaktivieren zu lassen.

Wenn Sie Campaign in einer Hybridarchitektur ausführen, müssen Sie vor dem Aktivieren der URL-Signatur sicherstellen, dass die gehostete Mid-Sourcing-Instanz wie folgt aktualisiert wurde:

* Zuerst die On-Premise-Marketing-Instanz
* Aktualisieren Sie dann auf dieselbe Version wie die On-Premise-Marketing-Instanz oder auf eine etwas höhere Version

Andernfalls können einige dieser Probleme auftreten:

* Vor dem Upgrade der Mid-Sourcing-Instanz werden über diese Instanz URLs ohne Signatur gesendet.
* Nachdem die Mid-Sourcing-Instanz aktualisiert und die URL-Signatur auf beiden Instanzen aktiviert wurde, werden die zuvor ohne Signatur gesendeten URLs zurückgewiesen. Der Grund dafür ist, dass eine Signatur von den Tracking-Dateien angefordert wird, die von der Marketing-Instanz bereitgestellt wurden.

Um URLs zu deaktivieren, die in früheren Builds generiert wurden, führen Sie diese Schritte auf allen Campaign-Servern gleichzeitig aus:

1. Ändern Sie in der Serverkonfigurationsdatei (`serverConf.xml`) die Option **blockRedirectForUnsignedTrackingLink** in **true**.
1. Starten Sie den `nlserver` neu.
1. Starten Sie auf dem `tracking` den `web`-Server neu (apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows).

Um die URL-Signatur zu aktivieren, führen Sie diese Schritte auf allen Campaign-Servern gleichzeitig aus:

1. Ändern Sie in der Serverkonfigurationsdatei (`serverConf.xml`) die Option **signEmailLinks** in **true**.
1. Starten Sie den **nlserver**-Service neu.
1. Starten Sie auf dem `tracking` den `web`-Server neu (apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows).

## Dateneinschränkung

Sie müssen sicherstellen, dass die verschlüsselten Kennwörter von einem authentifizierten Benutzer mit niedrigen Berechtigungen nicht zugänglich sind. Beschränken Sie dazu den Zugriff auf Passwortfelder oder auf die gesamte Entität (erfordert einen Build >= 8770).

Mit dieser Einschränkung können Sie Passwortfelder entfernen, das externe Konto jedoch für alle Benutzer über die Benutzeroberfläche zugänglich machen. [Weitere Informationen](../../configuration/using/restricting-pii-view.md).

Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zum Ordner **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** des Campaign-Explorers.

1. Erstellen Sie ein Datenschema als **[!UICONTROL Erweiterung eines Schemas]**.

   ![](assets/privacy-data-restriction.png)

1. Wählen Sie **[!UICONTROL Externes Konto]** aus (extAccount).

1. Bearbeiten Sie im letzten Bildschirm des Assistenten Ihr neues „srcSchema“, um den Zugriff auf alle Passwortfelder einzuschränken:

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
   >Sie können `$(loginId) = 0 or $(login) = 'admin'` durch `hasNamedRight('admin')` ersetzen, damit diese Kennwörter für alle Benutzer mit Administratorrechten angezeigt werden.

## Schützen von Seiten mit personenbezogenen Daten

Wir empfehlen On-Premise-Kunden dringend, die Seiten zu schützen, die möglicherweise personenbezogene Daten (PI) enthalten, wie Mirror-Seiten, Web-Anwendungen usw.

Ziel dieses Verfahrens ist es, dass diese Seiten nicht indexiert werden, um ein mögliches Sicherheitsrisiko zu verhindern. Hier finden Sie einige hilfreiche Artikel:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Führen Sie die folgenden Schritte aus, um Ihre Seiten zu schützen:

1. Fügen Sie eine `robots.txt` Datei im Stammverzeichnis Ihres Webservers (Apache oder IIS) hinzu. Hier ist der Inhalt der Datei:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Informationen zu IIS finden Sie auf [dieser Seite](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Für Apache können Sie die Datei in **/var/www/robots.txt** (Debian) platzieren.

1. Manchmal reicht das Hinzufügen **Datei** robots.txt“ aus Sicherheitsgründen nicht aus. Wenn beispielsweise eine andere Website einen Link zu Ihrer Seite enthält, kann diese in einem Suchergebnis angezeigt werden.

   Zusätzlich zur Datei **robots.txt** wird empfohlen, den Header **X-Robots-Tag** hinzuzufügen. Dies ist in Apache oder IIS und in der Konfigurationsdatei **serverConf.xml** möglich.

   Weitere Informationen finden Sie in [diesem Artikel](https://developers.google.com/search/reference/robots_meta_tag).


## Datenschutzanfragen

Auf [dieser Seite](../../platform/using/privacy-management.md) finden Sie allgemeine Informationen zur Datenschutzverwaltung und zu den Implementierungsschritten in Adobe Campaign. Außerdem finden Sie hier Best Practices und einen Überblick über den Benutzerprozess und die Rollen.
