---
solution: Campaign Classic
product: campaign
title: Konfigurieren von Adobe I/O für Adobe Experience Cloud Triggers
description: Erfahren Sie, wie Sie Adobe I/O für Adobe Experience Cloud Triggers konfigurieren.
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 98%

---

# Konfigurieren von Adobe I/O für Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Wenn Sie eine ältere Version der Triggers-Integration über die oAuth-Authentifizierung verwenden, **müssen Sie wie unten beschrieben zu Adobe I/O wechseln**. Der ältere OAuth-Authentifizierungsmodus für Campaign wird am 30. November 2021 eingestellt. [Mehr dazu](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>Beachten Sie, dass während dieser Umstellung auf [!DNL Adobe I/O] einige eingehende Trigger verloren gehen können.

## Voraussetzungen {#adobe-io-prerequisites}

Diese Integration gilt nur ab den Versionen **Campaign Classic 20.3, 20.2.4, 19.1.8 und [!DNL Gold Standard] 11**.

Bevor Sie mit dieser Implementierung beginnen, überprüfen Sie, ob Folgendes vorhanden ist:

* eine gültige **Organisationskennung**: Die IMS-Organisationskennung (Identity Management System) ist die eindeutige Kennung innerhalb von Adobe Experience Cloud, die z. B. für den Besucher-ID-Dienst und die einfache Anmeldung (Single Sign-on, SSO) verwendet wird, [Mehr dazu](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=de)
* ein **Entwicklerzugriff** auf Ihr Unternehmen. Sie müssen die Systemadministratorberechtigungen für die IMS-Organisation anfordern, um diesen Zugriff nach dem [auf dieser Seite](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) beschriebenen Verfahren für alle Produktprofile bereitzustellen zu können.

## Schritt 1: Erstellen/Aktualisieren eines Adobe I/O-Projekts {#creating-adobe-io-project}

1. Rufen Sie [!DNL Adobe I/O] auf und melden Sie sich mit der Systemadministratorberechtigung für die IMS-Organisation an.

   >[!NOTE]
   >
   > Stellen Sie sicher, dass Sie beim richtigen Portal der Organisation angemeldet sind.

1. Entnehmen Sie die vorhandene Integrations-Clientkennung (Client-ID) aus der Konfigurationsdatei &quot;ims/authIMSTAClientId&quot; der Instanz. Ist das Attribut nicht vorhanden oder leer, bedeutet dies, dass die Client-Kennung nicht konfiguriert ist.

   >[!NOTE]
   >
   >Wenn die Client-Kennung leer ist, können Sie in Adobe I/O direkt ein **[!UICONTROL neues Projekt erstellen]**.

1. Identifizieren Sie das vorhandene Projekt mit der gefundenen Client-ID. Suchen Sie nach bestehenden Projekten, die dieselbe Client-Kennung aufweisen wie die im vorherigen Schritt entnommene.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Wählen Sie **[!UICONTROL + Zu Projekt hinzufügen]** und dann **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. Wählen Sie im Fenster **[!UICONTROL Add an API]** (API hinzufügen) **[!UICONTROL Adobe Analytics]** aus.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Wählen Sie als Authentifizierungstyp **[!UICONTROL Service Account (JWT)]** (Dienstkonto (JWT)).

   ![](assets/do-not-localize/adobe_io_3.png)

1. Wenn Ihre Client-ID leer war, wählen Sie **[!UICONTROL Generate a key pair]** (Schlüsselpaar generieren) aus, um ein Paar aus öffentlichem und privatem Schlüssel zu erstellen.

   Die Schlüssel werden dann automatisch mit einem Standardablaufdatum von 365 Tagen heruntergeladen. Nach dem Ablaufdatum müssen Sie ein neues Schlüsselpaar erstellen und die Integration in der Konfigurationsdatei aktualisieren. Mit Option 2 können Sie Ihren **[!UICONTROL öffentlichen Schlüssel]** manuell mit einem längeren Ablaufdatum erstellen und hochladen.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Wählen Sie ein vorhandenes **[!UICONTROL Produktprofil]** aus oder erstellen Sie ggf. ein neues. Klicken Sie dann auf **[!UICONTROL Konfigurierte API speichern]**.

   Weitere Informationen zu [!DNL Analytics] **[!UICONTROL Produktprofilen]** finden Sie in der [Adobe Analytics-Dokumentation](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console?lang=de).

   ![](assets/do-not-localize/adobe_io_6.png)

1. Wählen Sie in Ihrem Projekt **[!UICONTROL Adobe Analytics]** aus und kopieren Sie die folgenden Informationen unter **[!UICONTROL Dienstkonto (JWT)]**:

   * **[!UICONTROL Client ID]** (Client-ID)
   * **[!UICONTROL Client Secret]** (Client-Geheimnis)
   * **[!UICONTROL Technical account ID]** (Kennung des technischen Kontos)
   * **[!UICONTROL Organization ID]** (Organisationskennung)

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Das Adobe I/O-Zertifikat läuft nach 12 Monaten ab. Sie müssen jedes Jahr ein neues Schlüsselpaar generieren.

## Schritt 2: Hinzufügen der Projektanmeldedaten in Adobe Campaign {#add-credentials-campaign}

Um die Projektanmeldedaten in Adobe Campaign hinzuzufügen, führen Sie als neolane-Benutzer folgenden Befehl für alle Container der Adobe Campaign-Instanz aus. Damit werden die Anmeldedaten des **[!UICONTROL technischen Kontos]** in die Konfigurationsdatei der Instanz eingefügt.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

Der private Schlüssel sollte im Base64-UTF-8-Format kodiert werden. Gehen Sie dabei folgendermaßen vor:

1. Verwenden Sie den privaten Schlüssel, der im Abschnitt [Schritt 1: Erstellen/Aktualisieren eines Adobe I/O-Projekts](#creating-adobe-io-project) generiert wurde. Der private Schlüssel muss mit dem für die Erstellung der Integration verwendeten Schlüssel identisch sein.

1. Codieren Sie den privaten Schlüssel mit dem folgenden Befehl: ```base64 ./private.key```.

   >[!NOTE]
   >
   >Manchmal werden beim Kopieren/Einfügen des privaten Schlüssels automatisch zusätzliche Zeilen hinzugefügt. Vergessen Sie nicht, diese zu entfernen, bevor Sie Ihren privaten Schlüssel codieren.

1. Verwenden Sie Ihren neu generierten privaten Schlüssel, der im Base64-UTF-8-Format kodiert ist, um den oben beschriebenen Befehl auszuführen. 

## Schritt 3: Aktualisieren des Pipelined-Tags {#update-pipelined-tag}

Um das [!DNL pipelined]-Tag zu aktualisieren, müssen Sie den Authentifizierungstyp in der Konfigurationsdatei **config-&lt; Name der Instanz >.xml** wie folgt entsprechend dem Adobe I/O-Projekt aktualisieren:

```
<pipelined ... authType="imsJwtToken"  ... />
```
