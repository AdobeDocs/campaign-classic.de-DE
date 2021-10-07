---
solution: Campaign Classic
product: campaign
title: Adobe Analytics-Connector
description: Erfahren Sie mehr über den Adobe Analytics-Connector. Bereitstellung
feature: Overview
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 0830e7b8a430fa18bc1326b972741e2e4dc76342
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 7%

---

# Adobe Analytics Connector-Bereitstellung {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> Diese Schritte sollten nur von Hybrid- und On-Premise-Implementierungen durchgeführt werden.
>
>Bei gehosteten Implementierungen wenden Sie sich an das [Adobe-Kundenunterstützungs-](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)-Team.

Die Integration zwischen Adobe Campaign Classic und Adobe Analytics-Authentifizierung unterstützt Adobe Identity Management Service (IMS). Sie müssen Adobe IMS implementieren und eine Verbindung zu Campaign [über eine Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en) herstellen, bevor Sie die Analytics Connector-Implementierung starten.

Damit diese Integration funktioniert, müssen Sie ein Adobe Analytics-Produktprofil erstellen, das ausschließlich für den Analytics-Connector verwendet wird. Anschließend müssen Sie ein Adobe I/O-Projekt erstellen.

## Erstellen eines Adobe Analytics-Produktprofils {#analytics-product-profile}

Das Produktprofil bestimmt die Zugriffsebene eines Benutzers auf Ihre verschiedenen Analytics-Komponenten.

Wenn Sie bereits über ein Analytics-Produktprofil verfügen, sollten Sie weiterhin ein neues Adobe Analytics-Produktprofil erstellen, das ausschließlich für den Analytics-Connector verwendet wird. Dadurch wird sichergestellt, dass Ihr Produktprofil mit den richtigen Berechtigungen für diese Integration ausgestattet ist.

Weitere Informationen zu Produktprofilen finden Sie in der [Dokumentation zur Admin Console](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. Wählen Sie in der [Admin Console](https://adminconsole.adobe.com/) Ihre Adobe Analytics **[!UICONTROL Product]** aus.

   ![](assets/do-not-localize/triggers_1.png)

1. Klicken Sie auf **[!UICONTROL Neues Profil]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Fügen Sie einen **[!UICONTROL Produktprofilnamen]** hinzu. Wir empfehlen, die folgende Syntax zu verwenden: `reserved_campaign_classic_<Company Name>`. Klicken Sie dann auf **[!UICONTROL Weiter]**.

   Dieses **[!UICONTROL Produktprofil]** sollte ausschließlich für den Analytics Connector verwendet werden, um Konfigurationsfehler zu vermeiden.

1. Öffnen Sie das neu erstellte **[!UICONTROL Produktprofil]** und wählen Sie die Registerkarte **[!UICONTROL Berechtigungen]** aus.

   ![](assets/do-not-localize/triggers_3.png)

1. Konfigurieren Sie die verschiedenen Funktionen, die auf **[!UICONTROL Bearbeiten]** klicken, und wählen Sie die Berechtigungen aus, die Sie Ihrem **[!UICONTROL Produktprofil]** zuweisen möchten, indem Sie auf das Pluszeichen (+) klicken.

   Weitere Informationen zum Verwalten von Berechtigungen finden Sie in der [Dokumentation zur Admin Console](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. Fügen Sie für die Funktion **[!UICONTROL Report Suites]** die **[!UICONTROL Report Suites]** hinzu, die Sie später verwenden müssen.

   Wenn Sie über keine Report Suites verfügen, können Sie diese wie folgt erstellen: [Diese Schritte](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. Fügen Sie für die Funktion **[!UICONTROL Metriken]** die Funktion **[!UICONTROL Metriken]** hinzu, die Sie später konfigurieren müssen.

   Bei Bedarf können Sie die Option Automatisch einschließen aktivieren, mit der jedes Berechtigungselement zur eingeschlossenen Liste hinzugefügt und automatisch neue Berechtigungselemente hinzugefügt werden.

   ![](assets/do-not-localize/triggers_13.png)

1. Fügen Sie für die Funktion **[!UICONTROL Dimensionen]** die **[!UICONTROL Dimensionen]** hinzu, die Sie später konfigurieren müssen.

1. Fügen Sie für die Funktion **[!UICONTROL Report Suite-Tools]** die folgenden Berechtigungen hinzu:

   * **[!UICONTROL Report Suite-Verwaltung]**
   * **[!UICONTROL Konversionsvariablen]**
   * **[!UICONTROL Erfolgsereignisse]**
   * **[!UICONTROL Benutzerdefinierter Data Warehouse-Bericht]**
   * **[!UICONTROL Data Sources Manager]**
   * **[!UICONTROL Klassifizierungen]**

1. Fügen Sie für die Funktion **[!UICONTROL Analytics Tools]** die folgenden Berechtigungen hinzu:

   * **[!UICONTROL Code-Manager - Webdienste]**
   * **[!UICONTROL Protokolle - Webdienste]**
   * **[!UICONTROL Webdienste]**
   * **[!UICONTROL Webdienstzugriff]**
   * **[!UICONTROL Erstellung berechneter Metriken]**
   * **[!UICONTROL Segmenterstellung]**

Ihr Produktprofil ist jetzt konfiguriert. Anschließend müssen Sie das Adobe I/O-Projekt erstellen.

## Erstellen eines Adobe I/O-Projekts {#create-adobe-io}

1. Greifen Sie auf die Adobe I/O zu und melden Sie sich als **Systemadministrator** der IMS-Organisation an.

   Weiterführende Informationen zu Admin-Rollen finden Sie auf dieser [Seite](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Klicken Sie auf **[!UICONTROL Zum Projekt hinzufügen]** und wählen Sie **[!UICONTROL API]** aus.

   ![](assets/do-not-localize/triggers_6.png)

1. Wählen Sie [!DNL Adobe Analytics] und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Wählen Sie **[!UICONTROL Dienstkonto (JWT)]** als Authentifizierungstyp aus und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Wählen Sie die Option **[!UICONTROL 1 aus: Generieren Sie ein Schlüsselpaar]** und klicken Sie auf **[!UICONTROL Generieren Sie ein Schlüsselpaar]**.

   Die Datei config.zip wird dann automatisch heruntergeladen.

   ![](assets/do-not-localize/triggers_9.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Wählen Sie das **[!UICONTROL Produktprofil]** aus, das in den vorherigen Schritten erstellt wurde, die in diesem Abschnitt [Abschnitt](#analytics-product-profile) beschrieben sind.

1. Klicken Sie dann auf **[!UICONTROL Konfigurierte API speichern]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Wählen Sie in Ihrem Projekt [!DNL Adobe Analytics] aus und kopieren Sie die folgenden Informationen unter **[!UICONTROL Dienstkonto (JWT)]**:

   * **[!UICONTROL Client ID]** (Client-ID)
   * **[!UICONTROL Client Secret]** (Client-Geheimnis)
   * **[!UICONTROL Technical account ID]** (Kennung des technischen Kontos)
   * **[!UICONTROL Organization ID]** (Organisationskennung)

   ![](assets/do-not-localize/triggers_12.png)

1. Fügen Sie diese Anmeldedaten für Dienstkonten mithilfe des folgenden Befehls in den nlserver ein:

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

Sie können jetzt mit der Verwendung des Analytics-Connectors beginnen und Ihr Kundenverhalten verfolgen.
