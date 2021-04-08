---
solution: Campaign Classic
product: campaign
title: Datenschutzanfragen
description: Erfahren Sie, wie Sie Datenschutzanfragen verwalten.
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
translation-type: tm+mt
source-git-commit: 5b1c4426a0d59861aa61a7e53154b9adfda31d71
workflow-type: tm+mt
source-wordcount: '2562'
ht-degree: 100%

---

# Verwalten von Datenschutzanfragen {#privacy-requests}

Allgemeine Informationen zum Thema Datenschutzverwaltung finden Sie in [diesem Abschnitt](../../platform/using/privacy-management.md).

Diese Informationen gelten für DSGVO, CCPA, PDPA und LGPD. Weitere Informationen zu diesen Verordnungen finden Sie in [diesem Abschnitt](../../platform/using/privacy-management.md#privacy-management-regulations).

Die Möglichkeit zum Opt-out aus dem Verkauf von personenbezogenen Daten, die sich speziell auf den CCPA bezieht, wird in [diesem Abschnitt](#sale-of-personal-information-ccpa) erläutert.

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

## Über Datenschutzanfragen {#about-privacy-requests}

Um Sie bei der Einhaltung von Datenschutzvorschriften zu unterstützen, ermöglicht Ihnen Adobe Campaign die Durchführung von Zugriffs- und Löschanfragen. Das **Recht auf Zugriff** und das **Recht auf Vergessenwerden** (Löschanfrage) werden in [diesem Abschnitt](../../platform/using/privacy-management.md#right-access-forgotten) beschrieben.

Im Folgenden wird beschrieben, wie Zugriffs- und Löschanfragen erstellt und in Adobe Campaign verarbeitet werden.

### Grundsätze {#principles}

Adobe Campaign bietet Datenverantwortlichen zwei Möglichkeiten zur Durchführung von Zugriffs- und Löschanfragen:

* Über die **Adobe Campaign-Benutzeroberfläche**: Für jede Datenschutzanfrage erstellt der Datenverantwortliche eine neue Datenschutzanfrage in Adobe Campaign. Siehe [diesen Abschnitt](#create-privacy-request-ui).
* Über die **API**: Adobe Campaign verfügt über eine API, mit der Datenschutzanfragen automatisch per SOAP verarbeitet werden können. Siehe [diesen Abschnitt](#automatic-privacy-request-api).

>[!NOTE]
>
>Weitere Informationen zu personenbezogenen Daten und zu den verschiedenen Entitäten, die Daten verwalten (Datenverantwortlicher, Auftragsverarbeiter und betroffene Person), finden Sie unter [Personenbezogene Daten und Personas](../../platform/using/privacy-and-recommendations.md#personal-data).

### Voraussetzungen {#prerequesites}

Adobe Campaign bietet Datenverantwortlichen Tools zum Erstellen und Verarbeiten von Datenschutzanfragen für in Adobe Campaign gespeicherte Daten. Für den Kontakt mit den betroffenen Personen ist jedoch der Datenverantwortliche allein zuständig (über E-Mail, Kundenunterstützung oder ein Web-Portal).

Als Datenverantwortlicher sind Sie daher außerdem verpflichtet, die Identität der betroffenen Person zu überprüfen, die die Anfrage stellt, und sicherzustellen, dass die dem Anfragenden übermittelten Daten zur betroffenen Person gehören.

### Installieren des Datenschutz-Packages {#install-privacy-package}

Um diese Funktion nutzen zu können, müssen Sie das Package **[!UICONTROL Datenschutzbestimmung]** über das Menü **[!UICONTROL Werkzeuge]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package-Import]** > **[!UICONTROL Adobe-Campaign-Package]** installieren. Weitere Informationen zum Installieren von Packages finden Sie im [entsprechenden Handbuch](../../installation/using/installing-campaign-standard-packages.md).

Zwei neue speziell für den Datenschutz vorgesehene Ordner werden unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** erstellt:

* **[!UICONTROL Datenschutzanfragen]**: In diesem Ordner erstellen Sie Ihre Datenschutzanfragen und verfolgen ihren Verlauf.
* **[!UICONTROL Namespaces]**: Hier definieren Sie das Feld, das zur Identifikation der betroffenen Person in der Adobe Campaign-Datenbank herangezogen wird.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Betreibung]** > **[!UICONTROL Technische Workflows]** werden täglich drei technische Workflows ausgeführt, um Datenschutzanfragen zu verarbeiten.

![](assets/privacy-workflows.png)

* **[!UICONTROL Datenschutzanfragen erfassen]**: Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten abgerufen und im Datenschutzanfrage-Fenster für den Download bereitgestellt.
* **[!UICONTROL Datenschutz-Anfragedaten löschen]**: Mit diesem Workflow werden die in Adobe Campaign gespeicherten Empfängerdaten gelöscht.
* **[!UICONTROL Bereinigung der Datenschutzanfrage]**: Mit diesem Workflow werden Zugriffsanfragedateien gelöscht, die älter als 90 Tage sind.

Unter **[!UICONTROL Administration]** > **[!UICONTROL Zugriffe]** > **[!UICONTROL Spezifische Berechtigungen]** wurde die Berechtigung **[!UICONTROL Datenschutzrecht]** hinzugefügt. Datenverantwortliche benötigen diese spezifische Berechtigung, um Datenschutz-Tools verwenden zu können. Damit können Sie neue Anfragen erstellen, ihren Verlauf verfolgen, die API verwenden etc.

![](assets/privacy-right.png)

### Namespaces{#namesspaces}

Bevor Sie Datenschutzanfragen erstellen können, müssen Sie den Namespace definieren, den Sie verwenden möchten. Dies ist der Schlüssel, der zur Identifikation der betroffenen Person in der Adobe Campaign-Datenbank herangezogen wird.

Standardmäßig sind drei Namespaces verfügbar: E-Mail, Telefon und Mobiltelefon. Wenn Sie einen anderen Namespace benötigen (z. B. ein benutzerdefiniertes Empfängerfeld), können Sie unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Namespaces]** einen neuen erstellen.

## Erstellen einer Datenschutzanfrage {#create-privacy-request-ui}

Mit der **Adobe Campaign-Oberfläche** können Sie Ihre Datenschutzanfragen erstellen und ihren Fortschritt verfolgen. Gehen Sie wie folgt vor, um eine neue Datenschutzanfrage zu erstellen:

1. Öffnen Sie den Datenschutzanfrage-Ordner in **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Datenschutzanfragen]**.

   ![](assets/privacy-requests-folder.png)

1. Auf diesem Bildschirm können Sie alle aktuellen Datenschutzanfragen, deren Status und die Logs einsehen. Klicken Sie auf **[!UICONTROL Neu]**, um eine Datenschutzanfrage zu erstellen.

   ![](assets/privacy-request-new.png)

1. Wählen Sie die **[!UICONTROL Verordnung]** (DSGVO, CCPA, PDPA oder LGPD) und den **[!UICONTROL Anfragetyp]** (Zugriff oder Löschen) aus. Wählen Sie einen **[!UICONTROL Namespace]** aus und geben Sie den **[!UICONTROL Abstimmwert]** ein. Wenn Sie E-Mail als Namespace verwenden, geben Sie die E-Mail der betroffenen Person ein.

   ![](assets/privacy-request-properties.png)

Die technischen Datenschutz-Workflows werden einmal täglich ausgeführt. Dabei werden auch alle neuen Anfragen verarbeitet.

* Löschanfrage: Die in Adobe Campaign gespeicherten Empfängerdaten werden gelöscht.
* Zugriffsanfragen: Die in Adobe Campaign gespeicherten Empfängerdaten werden erstellt und als XML-Datei auf der linken Seite des Anfragefensters bereitgestellt.

![](assets/privacy-request-download.png)

### Liste der Tabellen {#list-of-tables}

Bei der Durchführung einer Lösch- oder Zugriffsanfrage durchsucht Adobe Campaign alle Daten der betroffenen Person auf der Basis des **[!UICONTROL Abstimmwerts]**. Gesucht wird in allen Tabellen, in denen eine Relation mit der Tabelle des Empfängers besteht (vom Typ &quot;own&quot;).

Dies sind die Tabellen, die bei der Durchführung von Datenschutzanfragen standardmäßig berücksichtigt werden:

* Empfänger (recipient)
* Versandlog eines Empfängers (broadLogRcp)
* Trackinglogs der Empfänger (trackingLogRcp)
* Versandlog eines Ereignisses mit Verlauf (broadLogEventHisto)
* Inhalte der Empfängerlisten (rcpGrpRel)
* Angebotsvorschlag für einen Besucher (propositionVisitor)
* Besucher (visitor)
* Abonnementverlauf (subHisto)
* Abonnements (subscription)
* Angebotsvorschlag für einen Empfänger (propositionRcp)

Wenn Sie benutzerdefinierte Tabellen erstellt haben, für die eine Relation zur Empfängertabelle (Typ &quot;own&quot;) besteht, werden auch diese berücksichtigt. Wenn Sie beispielsweise eine Transaktionen-Tabelle haben, für die eine Relation mit der Empfängertabelle vorhanden ist, und eine Transaktionendetails-Tabelle, für die eine Relation mit der Transaktionen-Tabelle besteht, werden beide berücksichtigt.

>[!IMPORTANT]
>
>Wenn Sie Datenschutz-Batch-Anfragen mithilfe von Profillöschungs-Workflows ausführen, beachten Sie Folgendes:
>* Beim Löschen von Profilen mit Workflows werden keine untergeordneten Tabellen verarbeitet.
>* Alle untergeordneten Tabellen müssen manuell gelöscht werden.
>* Es wird empfohlen, einen ETL-Workflow zu erstellen, mit dem der Datenschutz-Zugriffstabelle die zu löschenden Zeilen hinzugefügt werden, und den Löschvorgang mit dem Workflow **[!UICONTROL Datenschutz-Anfragedaten löschen]** auszuführen Wir empfehlen, maximal 200 Profile täglich zu löschen, um die Systemleistung nicht zu beeinträchtigen.


### Status von Datenschutzanfragen {#privacy-request-statuses}

Dies sind die unterschiedlichen Status einer Datenschutzanfrage:

* **[!UICONTROL Neu]** / **[!UICONTROL Erneuter Versuch steht aus]**: Durchführung läuft, der Workflow hat die Anfrage noch nicht verarbeitet.
* **[!UICONTROL Verarbeitungsvorgang läuft]** / **[!UICONTROL Erneuter Versuch läuft]**: Der Workflow verarbeitet gerade die Anfrage.
* **[!UICONTROL Löschen steht aus]**: Der Workflow hat alle zu löschenden Empfängerdaten identifiziert.
* **[!UICONTROL Löschvorgang läuft]**: Der Workflow führt gerade die Löschung durch.
* **[!UICONTROL Löschbestätigung steht aus]**: (Löschanfrage im zweistufigen Prozessmodus) Der Workflow hat die Zugriffsanfrage verarbeitet. Für die Löschung ist eine manuelle Bestätigung erforderlich. Die Schaltfläche ist 15 Tage lang verfügbar.
* **[!UICONTROL Beendet]**: Die Verarbeitung der Anfrage wurde ohne Fehler abgeschlossen.
* **[!UICONTROL Fehler]**: Beim Workflow ist ein Fehler aufgetreten. Die Ursache wird in der Liste der Datenschutzanfragen in der **[!UICONTROL Anfragestatus]**-Spalte angezeigt. Beispielsweise bedeutet **[!UICONTROL Fehlerhafte Daten nicht gefunden]**, dass keine Empfängerdaten in der Datenbank gefunden wurden, die dem **[!UICONTROL Abstimmwert]** der betroffenen Person entsprechen.

### Zweistufiger Prozess {#two-step-process}

Standardmäßig ist der **zweistufige Prozess** aktiviert. Wenn Sie in diesem Modus eine neue Löschanfrage erstellen, führt Adobe Campaign immer zuerst eine Zugriffsanfrage aus. Auf diese Weise können Sie die Daten überprüfen, bevor Sie die Löschung bestätigen.

Sie können diesen Modus im Datenschutzanfrage-Bearbeitungsfenster ändern. Klicken Sie auf **[!UICONTROL Erweiterte Einstellungen]**.

![](assets/privacy-request-advanced-settings.png)

Wenn der zweistufige Modus aktiviert ist, ändert sich der Status einer neuen Löschanfrage in **[!UICONTROL Löschungsbestätigung ausstehend]**. Laden Sie die generierte XML-Datei aus dem Datenschutzanfrage-Bildschirm herunter und überprüfen Sie die Daten. Um das Löschen der Daten zu bestätigen, klicken Sie auf die Schaltfläche **[!UICONTROL Löschung der Daten bestätigen]**.

![](assets/privacy-request-delete-data.png)

### JSSP-URL {#jspp-url}

Bei der Verarbeitung von Zugriffsanfragen erzeugt Adobe Campaign JSSP, mit deren Hilfe die Empfängerdaten aus der Datenbank abgerufen und in eine auf einem lokalen Gerät gespeicherte XML-Datei exportiert werden. Die JSSP-URL ist folgendermaßen definiert:

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

wobei @id die Kennung der Datenschutzanfrage ist.

Die URL wird im Feld **[!UICONTROL &quot;Speicherort der Datei&quot; (@urlFile)]** des Schemas der **[!UICONTROL Datenschutzanfragen (gdprRequest)]** gespeichert.

Die Daten sind in der Datenbank 90 Tage lang verfügbar. Wenn die Anfrage durch den technischen Workflow bereinigt wird, werden die Daten aus der Datenbank entfernt und die URL wird ungültig. Achten Sie deshalb darauf, dass die URL noch gültig ist, wenn Sie die Daten von einer Website herunterladen.

Hier ist ein Beispiel für die Datendatei einer betroffenen Person:

![](assets/privacy-access-file.png)

Der Datenverantwortliche kann einfach eine Web-Anwendung erstellen, die die jeweilige JSSP-URL enthält, und so die Datendatei der betroffenen Person auf einer Website verfügbar machen.

![](assets/privacy-gdpr-jssp.png)

Im Folgenden finden Sie ein Beispiel eines Code-Snippets, das Sie in der **[!UICONTROL Seite]**-Aktivität der Web-Anwendung verwenden können.

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

Da der Zugriff auf die Datendatei der betroffenen Person eingeschränkt ist, muss der anonyme Zugriff auf die Website deaktiviert sein. Nur Benutzer mit der spezifischen Berechtigung **[!UICONTROL Datenschutz-Daten]** können sich bei der Seite anmelden und die Daten herunterladen.

## Automatischer Prozess für Datenschutzanfragen {#automatic-privacy-request-api}

Adobe Campaign verfügt über eine **API**, mit der ein automatischer Prozess für Datenschutzanfragen eingerichtet werden kann.

Der allgemeine Datenschutzprozess mit der API ist mit dem der [Benutzeroberfläche](#create-privacy-request-ui) identisch. Der einzige Unterschied besteht in der Erstellung der Datenschutzanfrage. Statt die Anfrage in Adobe Campaign zu erstellen, werden die Informationen über eine POST-Anfrage an Campaign gesendet. Für jede Anfrage wird ein neuer Eintrag auf dem Bildschirm **[!UICONTROL Datenschutzanfragen]** hinzugefügt. Die technischen Datenschutz-Workflows verarbeiten daraufhin die Anfrage auf dieselbe Weise wie eine über die Benutzeroberfläche eingegebene Anfrage.

Wenn Sie die API zum Senden von Datenschutzanfragen verwenden, wird empfohlen, den **zweistufigen Prozess** für die ersten Löschanfragen aktiviert zu lassen, um den Datenabruf zu testen. Wenn Ihre Tests abgeschlossen sind, können Sie den zweistufigen Prozess deaktivieren, damit der Prozess für Löschanfragen automatisch ausgeführt werden kann.

Die JS API **[!UICONTROL CreateRequestByName]** ist folgendermaßen definiert.

>[!NOTE]
>
>Wenn Sie bisher die **gdprRequest**-API verwendet haben, können Sie dies weiterhin tun. Es wird jedoch empfohlen, auf die neue **privacyRequest**-API umzusteigen.

>[!IMPORTANT]
>
>Für die Verwendung der API ist die spezifische Berechtigung **[!UICONTROL Datenschutzrecht]** erforderlich.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>Das Feld &quot;Verordnung&quot; steht nur zur Verfügung, wenn Sie Campaign Classic 20.2 (Build 9178 oder höher) verwenden.
>
>Wenn Sie auf 20.2 migrieren und die API bereits verwendet haben, müssen Sie das Feld „Vorschrift“ wie oben gezeigt hinzufügen. Wenn Sie einen früheren Build verwenden, können Sie die API weiterhin ohne das Feld „Vorschrift“ verwenden.

### Die API extern aufrufen {#invoking-api-externally}

Im Folgenden finden Sie ein Beispiel dafür, wie Sie die API extern aufrufen können (Authentifizierung über die API und Details zur Datenschutz-API). Weitere Informationen über die Datenschutz-API finden Sie in der [API-Dokumentation](https://docs.adobe.com/de/content/help/en/campaign-classic/technicalresources/api/s-nms-privacyRequest.html). Lesen Sie auch die [Dokumentation zu Web-Dienst-Aufrufen](../../configuration/using/web-service-calls.md).

Führen Sie zuerst die Authentifizierung über die API durch.

1. Laden Sie die **xtk:session**-WSDL über diese URL herunter: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Verwenden Sie die Anmeldemethode und geben Sie in der Anfrage einen Benutzernamen und ein Passwort als Parameter ein. Sie erhalten eine Antwort mit einem Sitzungs-Token. In unserem Beispiel wird SoapUI verwendet.

   ![](assets/privacy-api.png)

1. Verwenden Sie dieses Sitzungs-Token zur Authentifizierung für alle folgenden API-Aufrufe. Das Token ist 24 Stunden lang gültig.

Rufen Sie dann die Datenschutz-API auf:

1. Laden Sie die WSDL von dieser URL herunter: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Verwenden Sie **[!UICONTROL CreateRequestByName]**, um eine Datenschutzanfrage zu erstellen.

   In diesem Beispiel wird **[!UICONTROL CreateRequestByName]** verwendet. Beachten Sie, wie das oben bereitgestellte Sitzungs-Token zur Authentifizierung verwendet wird. In der Antwort erhalten Sie die ID der erstellten Anfrage.

   ![](assets/privacy-api-2.png)

   Beachten Sie bei der Durchführung der oben erläuterten Schritte Folgendes:

   * Sie können eine **queryDef** im Schema **nms:gdprRequest** verwenden, um den Status der Zugriffsanfrage zu überprüfen.
   * Mit einer **queryDef** im Schema **nms:gdprRequestData** können Sie das Ergebnis der Zugriffsanfrage abrufen.
   * Um die XML-Datei von **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;** herunterladen zu können, müssen Sie angemeldet sein und von einer in der Zulassungsliste enthaltenen IP-Adresse darauf zugreifen. Erstellen Sie dazu eine Web-Anwendung für den Zugriff auf die von der JSSP generierte Datei.

### Die API über ein JS abrufen {#invoking-api-from-js}

Hier ist ein Beispiel dafür, wie Sie die API innerhalb von Campaign Classic über ein JS abrufen können.

>[!NOTE]
>
>Das Feld &quot;Verordnung&quot; steht nur zur Verfügung, wenn Sie Campaign Classic 20.2 (Build 9178 oder höher) verwenden.
>
>Wenn Sie auf Version 20.2 migrieren und die API bereits verwendet haben, müssen Sie das Feld &quot;Verordnung&quot; hinzufügen. Wenn Sie einen früheren Build verwenden, können Sie die API weiterhin ohne das Feld &quot;Verordnung&quot; verwenden.

* Wenn Sie **einen früheren Build verwenden (der ein DSGVO-Package beinhaltet)**, können Sie die API weiterhin ohne das Feld &quot;Verordnung&quot; verwenden, wie unten dargestellt:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Wenn Sie **auf Version 20.2 migrieren** und die API bereits verwendet haben, müssen Sie das Feld &quot;Verordnung&quot; hinzufügen, wie unten dargestellt:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Wenn Sie **Campaign Classic 20.2 oder höher (Build 9178 oder höher) verwenden**, ist das Feld &quot;Verordnung&quot; optional, wie unten dargestellt:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

## Opt-out aus dem Verkauf von personenbezogenen Daten (CCPA) {#sale-of-personal-information-ccpa}

Der **California Consumer Privacy Act** (CCPA) gibt in Kalifornien ansässigen Personen neue Rechte in Bezug auf ihre personenbezogenen Daten und verpflichtet bestimmte in Kalifornien tätige Unternehmen zur Einhaltung von Datenschutzvorschriften.

Die Konfiguration und Verwendung von Zugriffs- und Löschanfragen sind für DSGVO (GDPR) und CCPA identisch. In diesem Abschnitt geht es um den Opt-out aus dem Verkauf von personenbezogenen Daten, der spezifisch für den CCPA ist.

Zusätzlich zu den von Adobe Campaign bereitgestellten Werkzeugen für die [Einverständnisverwaltung](../../platform/using/privacy-management.md#consent-management) können Sie verfolgen, ob ein Benutzer dem Verkauf seiner personenbezogenen Daten widersprochen hat.

Ein Verbraucher entscheidet über Ihr System, dass er nicht mit dem Verkauf seiner personenbezogenen Daten einverstanden ist. In Adobe Campaign können Sie diese Informationen speichern und verfolgen.

Erweitern Sie dazu die Profiltabelle und fügen Sie ein Feld mit der Bezeichnung **[!UICONTROL Opt-out für CCPA]** hinzu.

>[!IMPORTANT]
>
>Es liegt in Ihrer Verantwortung als Datenverantwortlicher, die Anfrage der betroffenen Person zu erhalten und die Anfragedaten für CCPA zu verfolgen. Als Technologieanbieter bieten wir nur eine Opt-out-Möglichkeit. Weitere Informationen zu Ihrer Rolle als Datenverantwortlicher finden Sie unter [Personenbezogene Daten und Personas](../../platform/using/privacy-and-recommendations.md#personal-data).

### Voraussetzung {#ccpa-prerequisite}

Um diese Informationen nutzen zu können, müssen Sie dieses Feld in Adobe Campaign Classic erstellen. Fügen Sie dazu der Tabelle **[!UICONTROL Empfänger]** ein boolesches Feld hinzu. Wenn ein neues Feld erstellt wird, wird es automatisch von der Campaign-API unterstützt.

Wenn Sie eine benutzerdefinierte Empfängertabelle verwenden, müssen Sie diesen Vorgang ebenfalls durchführen.

Ausführlichere Informationen zum Erstellen eines neuen Felds finden Sie in der [Dokumentation zur Schemabearbeitung](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Die Änderung von Schemata ist eine sensible Aufgabe, die nur von erfahrenen Benutzern durchgeführt werden kann.

1. Gehen Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Felder hinzufügen]**, wählen Sie **[!UICONTROL Empfänger]** als den **[!UICONTROL Dokumenttyp]** aus und klicken Sie auf **[!UICONTROL Weiter]**. Weitere Informationen zum Hinzufügen von Feldern zu einer Tabelle finden Sie in [diesem Abschnitt](../../configuration/using/new-field-wizard.md).

   ![](assets/privacy-ccpa-1.png)

1. Wählen Sie für **[!UICONTROL Feldtyp]** die Option **[!UICONTROL SQL-Feld]** aus. Geben Sie als Titel die Bezeichnung **[!UICONTROL Opt-out für CCPA]** an. Wählen Sie den Typ **[!UICONTROL Ganze Zahl 8 Bits (boolean)]** aus und legen Sie für **[!UICONTROL Relativer Pfad]** den folgenden eindeutigen Pfad fest: @OPTOUTCCPA. Klicken Sie auf **[!UICONTROL Beenden]**.

   ![](assets/privacy-ccpa-2.png)

   Dadurch wird das Schema **[!UICONTROL Empfänger (cus)]** erweitert oder erstellt. Klicken Sie darauf, um zu überprüfen, ob das Feld korrekt hinzugefügt wurde.

   ![](assets/privacy-ccpa-3.png)

1. Klicken Sie im Explorer auf den Knoten **[!UICONTROL Konfiguration]** > **[!UICONTROL Formulare]**. Fügen Sie in **[!UICONTROL Empfänger (nms)]** unter &quot;General Package&quot; ein `<input>`-Element hinzu und geben Sie als xpath-Wert den in Schritt 2 festgelegten relativen Pfad an. Weitere Informationen zum Identifizieren eines Formulars finden Sie in [diesem Abschnitt](../../configuration/using/identifying-a-form.md).

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Trennen Sie die Verbindung und stellen Sie sie wieder her. Führen Sie die im nächsten Abschnitt beschriebenen Schritte aus, um sicherzustellen, dass das Feld in den Details eines Empfängers verfügbar ist.

### Verwendung {#usage}

Der Datenverantwortliche muss dafür sorgen, dass das Feld ausgefüllt wird und die CCPA-Richtlinien und -Regeln bezüglich des Datenverkaufs eingehalten werden.

Um die Werte auszufüllen, können mehrere Methoden verwendet werden:

* Bearbeiten der Details des Empfängers über die Campaign-Oberfläche
* API verwenden
* Über einen Workflow zum Datenimport

Stellen Sie sicher, dass Sie die personenbezogenen Daten in den Profilen von Benutzern, die sich für eine Opt-out-Regelung entschieden haben, niemals an Dritte verkaufen.

1. Um den Opt-out-Status zu ändern, gehen Sie zu **[!UICONTROL Profile und Zielgruppen]** > **[!UICONTROL Empfänger]** und wählen Sie einen Empfänger aus. Auf der Registerkarte **[!UICONTROL Allgemein]** sehen Sie das im vorherigen Abschnitt konfigurierte Feld.

   ![](assets/privacy-ccpa-5.png)

1. Konfigurieren Sie die Empfängerliste so, dass die Opt-out-Spalte angezeigt wird. Wie Sie Listen konfigurieren, erfahren Sie im [entsprechenden Handbuch](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

   ![](assets/privacy-ccpa-6.png)

1. Sie können auf die Spalte klicken, um die Empfänger nach den Opt-out-Informationen zu sortieren. Sie können auch einen Filter erstellen, um nur Empfänger anzuzeigen, die sich abgemeldet haben. Weitere Informationen zum Erstellen von Filtern finden Sie in [diesem Abschnitt](../../platform/using/creating-filters.md).

   ![](assets/privacy-ccpa-7.png)
