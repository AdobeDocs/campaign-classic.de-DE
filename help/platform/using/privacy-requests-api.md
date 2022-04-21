---
product: campaign
title: Automatischer Prozess für Datenschutzanfragen
description: Erfahren Sie, wie Sie einen automatischen Prozess für Datenschutzanfragen einrichten
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 98%

---

# Automatischer Prozess für Datenschutzanfragen {#automatic-privacy-request-api}

![](../../assets/v7-only.svg)

Adobe Campaign verfügt über eine **API**, mit der ein automatischer Prozess für Datenschutzanfragen eingerichtet werden kann.

Der allgemeine Datenschutzprozess mit der API ist mit dem der [Benutzeroberfläche](privacy-requests-ui.md) identisch. Der einzige Unterschied besteht in der Erstellung der Datenschutzanfrage. Statt die Anfrage in Adobe Campaign zu erstellen, werden die Informationen über eine POST-Anfrage an Campaign gesendet. Für jede Anfrage wird ein neuer Eintrag auf dem Bildschirm **[!UICONTROL Datenschutzanfragen]** hinzugefügt. Die technischen Datenschutz-Workflows verarbeiten daraufhin die Anfrage auf dieselbe Weise wie eine über die Benutzeroberfläche eingegebene Anfrage.

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

## Die API extern aufrufen {#invoking-api-externally}

Im Folgenden finden Sie ein Beispiel dafür, wie Sie die API extern aufrufen können (Authentifizierung über die API und Details zur Datenschutz-API). Weitere Informationen über die Datenschutz-API finden Sie in der [API-Dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=de). Lesen Sie auch die [Dokumentation zu Web-Dienst-Aufrufen](../../configuration/using/web-service-calls.md).

Führen Sie zuerst die Authentifizierung über die API durch.

1. Laden Sie die **xtk:session**-WSDL über diese URL herunter: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Verwenden Sie die Anmeldemethode und geben Sie in der Anfrage einen Benutzernamen und ein Passwort als Parameter ein. Sie erhalten eine Antwort mit einem Sitzungs-Token. In unserem Beispiel wird SoapUI verwendet.

   ![](assets/do-not-localize/privacy-api.png)

1. Verwenden Sie dieses Sitzungs-Token zur Authentifizierung für alle folgenden API-Aufrufe. Das Token ist 24 Stunden lang gültig.

Rufen Sie dann die Datenschutz-API auf:

1. Laden Sie die WSDL von dieser URL herunter: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Verwenden Sie **[!UICONTROL CreateRequestByName]**, um eine Datenschutzanfrage zu erstellen.

   In diesem Beispiel wird **[!UICONTROL CreateRequestByName]** verwendet. Beachten Sie, wie das oben bereitgestellte Sitzungs-Token zur Authentifizierung verwendet wird. In der Antwort erhalten Sie die ID der erstellten Anfrage.

   ![](assets/do-not-localize/privacy-api-2.png)

   Beachten Sie bei der Durchführung der oben erläuterten Schritte Folgendes:

   * Sie können eine **queryDef** im Schema **nms:gdprRequest** verwenden, um den Status der Zugriffsanfrage zu überprüfen.
   * Mit einer **queryDef** im Schema **nms:gdprRequestData** können Sie das Ergebnis der Zugriffsanfrage abrufen.
   * Um die XML-Datei von **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;** herunterladen zu können, müssen Sie angemeldet sein und der Zugriff muss von einer in der Zulassungsliste enthaltenen IP-Adresse erfolgen. Erstellen Sie dazu ein Web-Programm für den Zugriff auf die von der JSSP generierte Datei.

## Die API über ein JS abrufen {#invoking-api-from-js}

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
   This code calls an API to create new Privacy request on the DB.
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
   This code calls an API to create new Privacy request on the DB.
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
   This code calls an API to create new Privacy request on the DB.
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
