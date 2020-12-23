---
solution: Campaign Classic
product: campaign
title: Konfigurieren von Adobe I/O für Adobe Experience Cloud Triggers
description: Erfahren Sie, wie Sie Adobe I/O für Adobe Experience Cloud Triggers konfigurieren.
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 57093a687534ed1e7f77738ca233d4cc86cf40cf
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Konfigurieren von Adobe I/O für Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Wenn Sie eine ältere Version der Triggers-Integration über die oAuth-Authentifizierung verwenden, **müssen Sie wie unten beschrieben zu Adobe I/O wechseln**. Die alte oAuth-Authentifizierungsmethode wird am 30. April 2021 eingestellt. [Mehr dazu](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Voraussetzungen {#adobe-io-prerequisites}

Diese Integration gilt nur ab den Versionen **Campaign Classic 20.3 und Gold Standard 11**.

Bevor Sie mit der Implementierung beginnen, benötigen Sie Folgendes:

* eine gültige **Organisationskennung**: Die Organisations-ID des Identity Management Systems (IMS) ist die eindeutige Kennung innerhalb des Adobe Experience Cloud, die beispielsweise für den VisitorID-Dienst und das IMS Single-Sign-On (SSO) verwendet wird. [Mehr dazu](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **Entwicklerzugriff** auf Ihr Unternehmen.  Sie müssen die Systemadministratorberechtigungen für die IMS-Organisation anfordern, um diesen Zugriff nach dem [auf dieser Seite](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) beschriebenen Verfahren für alle Produktprofile bereitzustellen zu können.
>
## Schritt 1: Erstellen/Aktualisieren eines Adobe I/O-Projekts {#creating-adobe-io-project}

1. Greifen Sie auf Adobe I/O zu und melden Sie sich mit der Systemverwaltungsrechten für die IMS-Organisation an.

   >[!NOTE]
   >
   > Vergewissern Sie sich, dass Sie beim richtigen Organisationsportal angemeldet sind.

1. Entnehmen Sie die vorhandene Integrations-Client-ID aus der Konfigurationsdatei &quot;ims/authIMSTAClientId&quot; der Instanz. Nicht vorhandenes oder leeres Attribut zeigt an, dass die Client-ID nicht konfiguriert ist.

   >[!NOTE]
   >
   >Wenn Ihre Client-ID leer ist, können Sie direkt **[!UICONTROL Neues Projekt]** in Adobe I/O erstellen.

1. Identifizieren Sie das vorhandene Projekt mithilfe der extrahierten Client-ID. Suchen Sie nach vorhandenen Projekten mit derselben Client-ID wie im vorherigen Schritt extrahiert.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Wählen Sie **[!UICONTROL + Add to Project]** (+ Zu Projekt hinzufügen) und dann **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Wählen Sie im Fenster **[!UICONTROL Add an API]** (API hinzufügen) **[!UICONTROL Adobe Analytics]** aus.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Wählen Sie als Authentifizierungstyp **[!UICONTROL Service Account (JWT)]** (Dienstkonto (JWT)).

   ![](assets/do-not-localize/adobe_io_3.png)

1. Wenn Ihre Client-ID leer war, wählen Sie **[!UICONTROL Generate a key pair]** (Schlüsselpaar generieren) aus, um ein Paar aus öffentlichem und privatem Schlüssel zu erstellen.

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

Um die Projektanmeldedaten in Adobe Campaign hinzuzufügen, führen Sie als neolane-Benutzer folgenden Befehl für alle Container der Adobe Campaign-Instanz aus. Damit werden die Anmeldedaten des **[!UICONTROL technischen Kontos]** in die Konfigurationsdatei der Instanz eingefügt.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Sie sollten den privaten Schlüssel im Base 64-UTF-8-Format kodieren. Achten Sie darauf, vor dem Kodieren die neue Zeile aus dem Schlüssel zu entfernen (mit Ausnahme des privaten Schlüssels). Der private Schlüssel muss mit dem für die Erstellung der Integration verwendeten Schlüssel identisch sein.

## Schritt 3: Aktualisieren des Pipelined-Tags {#update-pipelined-tag}

Um das [!DNL pipelined]-Tag zu aktualisieren, müssen Sie den Authentifizierungstyp in der Konfigurationsdatei **config-&lt; Name der Instanz >.xml** wie folgt entsprechend dem Adobe I/O-Projekt aktualisieren:

```
<pipelined ... authType="imsJwtToken"  ... />
```
