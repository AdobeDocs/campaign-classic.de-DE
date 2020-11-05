---
title: Konfigurieren der Adobe-E/A für Adobe Experience Cloud-Auslöser
description: Erfahren Sie, wie Sie die Adobe-E/A für Adobe Experience Cloud-Auslöser konfigurieren.
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 1%

---


# Konfigurieren der Adobe-E/A für Adobe Experience Cloud-Auslöser {#configuring-adobe-io}

>[!CAUTION]
>
>Wenn Sie eine ältere Version der Trigger-Integration über JWT-Token oder Auth-Authentifizierung verwenden, müssen **Sie wie unten** beschrieben zur Adobe-E/A wechseln. Die Authentifizierungsmodi JWT und oAuth werden jetzt nicht mehr unterstützt. [Mehr dazu](https://github.com/AdobeDocs/analytics-1.4-apis)

## Voraussetzungen {#adobe-io-prerequisites}

Bevor Sie mit der Implementierung beginnen, überprüfen Sie bitte, ob Sie:

* eine aktuelle Version von Adobe Campaign: 19.1.8 oder 20.2.1 Builds und höher,
* eine gültige IMSOrgID: der Organisationsbezeichner des Identity Management-Systems (IMS) ist die eindeutige Kennung innerhalb des Adobe Experience Cloud, die beispielsweise für den VisitorID-Dienst und das IMS-Single-Sign-On (SSO) verwendet wird,
* ein Entwicklerzugriff auf das IMS-Org.

>[!NOTE]
>
>Wenn Sie die Systemadministrator-Berechtigungen des IMS Org anfordern müssen, befolgen Sie das [in dieser Seite](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) beschriebene Verfahren, um diesen Zugriff für alle Product-Profil bereitzustellen.


## Schritt 1: I/O-Projekt der Adobe erstellen/aktualisieren {#creating-adobe-io-project}

1. Greifen Sie auf die Adobe I/O zu und melden Sie sich mit der Systemadministrator-Berechtigung für IMSorg an.

   >[!NOTE]
   >
   > Stellen Sie sicher, dass Sie beim richtigen IMSorg Portal angemeldet sind.

1. Extrahieren Sie die vorhandene Integrations-Client-ID aus der Konfigurationsdatei ims/authIMSTAClientId. Nicht vorhandenes oder leeres Attribut zeigt an, dass die Client-ID nicht konfiguriert ist.

   >[!NOTE]
   >
   >Wenn Ihre Client-ID leer ist, können Sie direkt ein neues Projekt **[!UICONTROL in der Adobe I/O]** erstellen.

1. Identifizieren Sie das vorhandene Projekt mit der extrahierten Client-ID. Suchen Sie nach vorhandenen Projekten mit derselben Client-ID wie die im vorherigen Schritt extrahierte.

   ![](assets/adobe_io_8.png)

1. Wählen Sie **[!UICONTROL + Hinzufügen zu Projekt]** und wählen Sie **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. Wählen Sie im Fenster **[!UICONTROL Hinzufügen API]** die Option **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Wählen Sie als Authentifizierungstyp **[!UICONTROL Dienstkonto (JWT)]** .

   ![](assets/adobe_io_3.png)

1. Wenn Ihre Client-ID leer war, wählen Sie **[!UICONTROL Generate a key pair (Erstellen eines Schlüsselpaars]** ), um einen öffentlichen und privaten Schlüssel zu erstellen.

   ![](assets/adobe_io_4.png)

1. Laden Sie den öffentlichen Schlüssel hoch und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/adobe_io_5.png)

1. Wählen Sie das Profil **Analytics-&lt; Organisationsname>** und klicken Sie auf Konfigurierte API **[!UICONTROL speichern]**.

   ![](assets/adobe_io_6.png)

1. Wählen Sie in Ihrem Projekt &quot; **[!UICONTROL Dienstkonto (JWT)]** &quot;und kopieren Sie die folgenden Informationen:
   * **[!UICONTROL Client-ID]**
   * **[!UICONTROL geheimer Clientschlüssel]**
   * **[!UICONTROL Technische Konto-ID]**
   * **[!UICONTROL Organisationskennung]**

   ![](assets/adobe_io_7.png)

## Schritt 2: hinzufügen der Projektanmeldeinformationen in Adobe Campaign {#add-credentials-campaign}

Um die Projektberechtigungen in Adobe Campaign hinzuzufügen, führen Sie den folgenden Befehl als &quot;neolane&quot;Benutzer auf allen Containern der Adobe Campaign-Instanz aus, um die Anmeldeinformationen für das **[!UICONTROL technische Konto]** in die Konfigurationsdatei der Instanz einzufügen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Sie sollten den privaten Schlüssel im Base64 UTF-8-Format kodieren. Denken Sie daran, die neue Zeile vor der Kodierung aus dem Schlüssel zu entfernen, mit Ausnahme des privaten Schlüssels. Der private Schlüssel muss mit dem für die Erstellung der Integration verwendeten identisch sein.

## Schritt 3: Pipeline-Tag aktualisieren {#update-pipelined-tag}

Um [!DNL pipelined] Tag zu aktualisieren, müssen Sie den Authentifizierungstyp wie folgt auf Adobe-E/A-Projekt in der Konfigurationsdatei **config-&lt; instance-name >.xml** aktualisieren:

```
<pipelined ... authType="imsJwtToken"  ... />
```
