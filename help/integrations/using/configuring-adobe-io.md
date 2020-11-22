---
solution: Campaign Classic
product: campaign
title: Konfigurieren der Adobe-E/A für Adobe Experience Cloud-Auslöser
description: Erfahren Sie, wie Sie die Adobe-E/A für Adobe Experience Cloud-Auslöser konfigurieren.
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 34%

---


# Configuring Adobe I/O for Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Wenn Sie eine ältere Version der Trigger-Integration über die Auth-Authentifizierung verwenden, müssen **Sie wie unten** beschrieben zur Adobe-E/A wechseln. Der alte Auth-Authentifizierungsmodus wird am 30. April 2021 eingestellt. [Mehr dazu](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Voraussetzungen {#adobe-io-prerequisites}

Diese Integration gilt nur ab Version **20.3** des Campaign Classic.

Bevor Sie mit der Implementierung beginnen, überprüfen Sie bitte, ob Sie:

* eine gültige IMSOrgID: der Organisationsbezeichner des Identity Management-Systems (IMS) ist die eindeutige Kennung innerhalb des Adobe Experience Cloud, die beispielsweise für den VisitorID-Dienst und das IMS-Single-Sign-On (SSO) verwendet wird,
* ein Entwicklerzugriff auf das IMS-Org.

>[!NOTE]
>
>If you need to request the System Administrator privileges of the IMS Org, follow the procedure detailed [in this page](https://helpx.adobe.com/de/enterprise/admin-guide.html/de/enterprise/using/manage-developers.ug.html) to provide this access for the all Product Profiles.


## Schritt 1: I/O-Projekt der Adobe erstellen/aktualisieren {#creating-adobe-io-project}

1. Greifen Sie auf die Adobe I/O zu und melden Sie sich mit der Systemadministrator-Berechtigung für IMSorg an.

   >[!NOTE]
   >
   > Stellen Sie sicher, dass Sie beim richtigen IMSorg-Portal angemeldet sind.

1. Entnehmen Sie die vorhandene Integrations-Client-ID aus der Konfigurationsdatei &quot;ims/authIMSTAClientId&quot; der Instanz. Nicht vorhandenes oder leeres Attribut zeigt an, dass die Client-ID nicht konfiguriert ist.

   >[!NOTE]
   >
   >If your Client ID is empty, you can directly **[!UICONTROL Create a New project]** in Adobe I/O.

1. Identifizieren Sie das vorhandene Projekt mit der extrahierten Client-ID. Suchen Sie nach bestehenden Projekten, die dieselbe Client-ID aufweisen wie die im vorherigen Schritt entnommene.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Wählen Sie **[!UICONTROL + Add to Project]** (+ Zu Projekt hinzufügen) und dann **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. In the **[!UICONTROL Add an API]** window, select **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Wählen Sie als Authentifizierungstyp **[!UICONTROL Service Account (JWT)]** (Dienstkonto (JWT)).

   ![](assets/do-not-localize/adobe_io_3.png)

1. If your Client ID was empty, select **[!UICONTROL Generate a key pair]** to create a Public and Private keypair.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Laden Sie den öffentlichen Schlüssel hoch und klicken Sie auf **[!UICONTROL Next]** (Weiter).

   ![](assets/do-not-localize/adobe_io_5.png)

1. Wählen Sie das Produktprofil namens **Analytics-&lt; Organisationsname >** und klicken Sie auf **[!UICONTROL Save configured API]** (Konfigurierte API speichern).

   ![](assets/do-not-localize/adobe_io_6.png)

1. Wählen Sie in Ihrem Projekt **[!UICONTROL Service Account (JWT)]** (Dienstkonto (JWT)) aus und kopieren Sie die folgenden Informationen:
   * **[!UICONTROL Client ID]** (Client-ID)
   * **[!UICONTROL Client Secret]** (Client-Geheimnis)
   * **[!UICONTROL Technical account ID]** (Kennung des technischen Kontos)
   * **[!UICONTROL Organization ID]** (Organisationskennung)

   ![](assets/do-not-localize/adobe_io_7.png)

## Schritt 2: Hinzufügen der Projektanmeldedaten in Adobe Campaign {#add-credentials-campaign}

To add the project credentials in Adobe Campaign, run the following command as &#39;neolane&#39; user on all the containers of the Adobe Campaign instance to insert the **[!UICONTROL Technical Account]** credentials in the instance configuration file.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Sie sollten den privaten Schlüssel im Base 64-UTF-8-Format kodieren. Achten Sie darauf, vor dem Kodieren die neue Zeile aus dem Schlüssel zu entfernen (mit Ausnahme des privaten Schlüssels). Der private Schlüssel muss mit dem für die Erstellung der Integration verwendeten Schlüssel identisch sein.

## Schritt 3: Aktualisieren des Pipelined-Tags {#update-pipelined-tag}

To update [!DNL pipelined] tag, you need to update the authentication type to Adobe I/O project in the configuration file **config-&lt; instance-name >.xml** as follows:

```
<pipelined ... authType="imsJwtToken"  ... />
```
