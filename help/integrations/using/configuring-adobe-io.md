---
title: Konfigurieren der Adobe IO für Adobe Experience Cloud Trigger
seo-title: Konfigurieren der Adobe IO für Adobe Experience Cloud Trigger
description: Konfigurieren der Adobe IO für Adobe Experience Cloud Trigger
seo-description: null
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
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 1%

---


# Konfigurieren der Adobe IO für Adobe Experience Cloud Trigger {#configuring-adobe-io}

Vorausgesetzte Konfigurationen sind:

* Adobe Campaign Classic erstellen ACC-19.1.9 oder ACC-20.2.1 und höher.
* eine gültige IMSOrgID.
* ein Entwicklerzugriff auf das IMS-Org. Sie müssen die Systemadministrator-Berechtigungen des IMS Org anfordern, um das auf dieser [Seite](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) beschriebene Verfahren zu befolgen, um diesen Zugriff für alle Produkt-Profil bereitzustellen.

## Schritt 1: Adobe-IO-Projekt erstellen/aktualisieren {#creating-adobe-io-project}

1. Greifen Sie auf Adobe IO zu und melden Sie sich mit der Systemadministrator-Berechtigung für IMSorg an.

   >[!NOTE]
   >
   > Stellen Sie sicher, dass Sie beim richtigen IMSorg Portal angemeldet sind.

1. Extrahieren Sie die vorhandene Integrations-Client-ID aus der Konfigurationsdatei ims/authIMSTAClientId. Nicht vorhandenes oder leeres Attribut zeigt an, dass die Client-ID nicht konfiguriert ist.

   >[!NOTE]
   >
   >Wenn Ihre Client-ID leer ist, können Sie in Adobe IO direkt ein neues Projekt **[!UICONTROL erstellen]** .

1. Sie müssen jetzt das vorhandene Projekt mit der extrahierten Client-ID identifizieren. Suchen Sie nach vorhandenen Projekten mit derselben Client-ID wie die im vorherigen Schritt extrahierte.

   ![](assets/adobe_io_8.png)

1. Wählen Sie **[!UICONTROL + Hinzufügen zu Projekt]** und wählen Sie **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. Wählen Sie im Fenster **[!UICONTROL Hinzufügen API]** die Option **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Wählen Sie als Authentifizierungstyp **[!UICONTROL Dienstkonto (JWT)]** .

   ![](assets/adobe_io_3.png)

1. Wenn Sie keine Client-ID haben, wählen Sie **[!UICONTROL Generate a key pair (Erstellen eines Schlüsselpaars]** ), um einen öffentlichen und privaten Schlüssel zu erstellen.

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

Um die Projektberechtigungen in Adobe Campaign hinzuzufügen, führen Sie den folgenden Befehl als neolaner Benutzer auf allen Containern der Adobe Campaign-Instanz aus, um die Anmeldeinformationen des **[!UICONTROL technischen Kontos]** in die Konfigurationsdatei der Instanz einzufügen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Sie sollten den privaten Schlüssel im Base64 UTF-8-Format kodieren. Denken Sie daran, die neue Zeile vor der Kodierung aus dem Schlüssel zu entfernen, mit Ausnahme des privaten Schlüssels. Der private Schlüssel muss mit dem für die Erstellung der Integration verwendeten identisch sein.

## Schritt 3: Pipeline-Tag aktualisieren {#update-pipelined-tag}

Um [!DNL pipelined] Tag zu aktualisieren, müssen Sie den Authentifizierungstyp wie folgt auf Adobe IO-Projekt in der Konfigurationsdatei **config-&lt; instance-name >.xml** aktualisieren:

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>Wenn Sie die ältere Version der Trigger-Integration mit Legacy-JWT-Token verwenden, sollten Sie auch die Adobe-IO-API hinzufügen, um im ersten Schritt [!DNL Adobe Analytics] ausführlich darauf hinzuweisen, dass eine automatische Migration zur neuen Trigger-Authentifizierung durchgeführt wird.
