---
product: campaign
title: Bereitstellung des Adobe Analytics-Connectors
description: Erfahren Sie mehr über die Bereitstellung des Adobe Analytics-Connectors.
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen für v7"
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 24e002aa-4e86-406b-92c7-74f242ee4b86
source-git-commit: 514f390b5615a504f3805de68f882af54e0c3949
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 82%

---

# Bereitstellung des Adobe Analytics-Connectors {#adobe-analytics-connector-provisioning}

>[!CAUTION]
>
> Diese Schritte sollten nur von Hybrid- und On-Premise-Implementierungen durchgeführt werden.
>
>Bei gehosteten und Campaign Managed Services-Implementierungen wenden Sie sich bitte die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

Die Integration zwischen Adobe Campaign Classic und der Adobe Analytics-Authentifizierung unterstützt Adobe Identity Management Service (IMS):

* Wenn Sie ein migriertes externes Konto verwalten, müssen Sie Adobe IMS implementieren und über eine Adobe ID eine Verbindung zu Adobe Campaign herstellen.

  Bitte beachten Sie, dass eine über Adobe ID IMS angemeldete Person die Eigentümerin bzw. der Eigentümer des **Daten-Connector**-Kontos in Adobe Analytics sein muss und über die Berechtigungen für das [unten](#analytics-product-profile) aufgeführte **Produktprofil** verfügen muss.

Das Problem bestand darin, dass die Eigentümerin bzw. der Eigentümer des Daten-Connectors eine andere Person war als die, die bei Campaign angemeldet war und die Integration mit Analytics ausprobiert hatte.

* Wenn Sie einen neuen Connector implementieren, ist die Implementierung von Adobe IMS optional. Ohne einen Adobe ID-Benutzer verwendet Adobe Campaign einen technischen Anwender zur Synchronisierung mit Adobe Analytics.

Damit diese Integration funktioniert, müssen Sie ein Adobe Analytics-Produktprofil erstellen, das ausschließlich für den Analytics-Connector verwendet wird. Anschließend müssen Sie ein Adobe I/O-Projekt erstellen.

>[!AVAILABILITY]
>
> Die Berechtigung für Dienstkonten (JWT) wird von Adobe nicht mehr unterstützt. Campaign-Integrationen mit Adobe-Lösungen müssen jetzt auf OAuth Server-zu-Server-Anmeldedaten angewiesen sein. </br>
>
> * Wenn Sie eingehende Integrationen mit Campaign implementiert haben, müssen Sie Ihr technisches Konto migrieren, wie im Abschnitt [diese Dokumentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Die bestehenden JWT-Anmeldedaten (Service Account) funktionieren weiterhin bis zum 27. Januar 2025. Darüber hinaus ist die Erstellung neuer JWT-Anmeldedaten (Service Account) in der Developer Console ab dem 3. Juni 2024 nicht mehr möglich. Eine neue JWT-Berechtigung (Service Account) kann nach diesem Datum nicht mehr erstellt oder einem Projekt hinzugefügt werden. </br>
>
> * Wenn Sie ausgehende Integrationen implementiert haben, z. B. die Integration von Campaign mit Analytics oder Experience Cloud Trigger, funktionieren diese bis zum 27. Januar 2025 weiterhin. Vor diesem Datum müssen Sie jedoch Ihre Campaign-Umgebung auf Version 7.4.1 aktualisieren und Ihr technisches Konto auf oAuth migrieren. Da die Erstellung neuer Service Account (JWT)-Anmeldedaten in der Developer Console ab dem 3. Juni 2024 nicht mehr möglich ist, können Sie nach diesem Datum keine neue ausgehende Integration erstellen, die auf JWT basiert

## Erstellen eines Adobe Analytics-Produktprofils {#analytics-product-profile}

Das Produktprofil bestimmt die Zugriffsebene eines Benutzers auf Ihre verschiedenen Analytics-Komponenten.

Wenn Sie bereits über ein Analytics-Produktprofil verfügen, sollten Sie dennoch ein neues Adobe Analytics-Produktprofil erstellen, das ausschließlich für den Analytics-Connector verwendet wird. Dadurch wird sichergestellt, dass Ihr Produktprofil mit den richtigen Berechtigungen für diese Integration ausgestattet ist.

Weiterführende Informationen zu Produktprofilen finden Sie in der [Dokumentation zur Admin Console](https://helpx.adobe.com/de/enterprise/admin-guide.html).

1. Wählen Sie in der [Admin Console](https://adminconsole.adobe.com/) Ihr Adobe Analytics-**[!UICONTROL Produkt]** aus.

   ![](assets/do-not-localize/triggers_1.png)

1. Klicken Sie auf **[!UICONTROL Neues Profil]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Fügen Sie einen **[!UICONTROL Produktprofilnamen]** hinzu. Wir empfehlen, die folgende Syntax zu verwenden: `reserved_campaign_classic_<Company Name>`. Klicken Sie dann auf **[!UICONTROL Weiter]**.

   Dieses **[!UICONTROL Produktprofil]** sollte ausschließlich für den Analytics-Connector verwendet werden, um Konfigurationsfehler zu vermeiden.

1. Öffnen Sie das neu erstellte **[!UICONTROL Produktprofil]** und wählen Sie die Registerkarte **[!UICONTROL Berechtigungen]** aus.

   ![](assets/do-not-localize/triggers_3.png)

1. Konfigurieren Sie die verschiedenen Funktionen, indem Sie auf **[!UICONTROL Bearbeiten]** klicken, und wählen Sie die Berechtigungen aus, die Sie Ihrem **[!UICONTROL Produktprofil]** zuweisen möchten, indem Sie auf das Pluszeichen (+) klicken.

   Weitere Informationen zum Verwalten von Berechtigungen finden Sie in der [Dokumentation zur Admin Console](https://helpx.adobe.com/de/enterprise/using/manage-permissions-and-roles.html).

1. Fügen Sie für die Funktion **[!UICONTROL Report Suites]** die **[!UICONTROL Report Suites]** hinzu, die Sie später verwenden müssen.

   Wenn Sie über keine Report Suites verfügen, können Sie diese mit [diesen Schritten](../../platform/using/gs-aa.md) erstellen.

   ![](assets/do-not-localize/triggers_4.png)

1. Fügen Sie für die Funktion **[!UICONTROL Metriken]** die **[!UICONTROL Metriken]** hinzu, die Sie später konfigurieren müssen.

   Bei Bedarf können Sie die Option &quot;Automatisch einschließen&quot; aktivieren, mit der jedes Berechtigungselement zur eingeschlossenen Liste hinzugefügt wird und automatisch neue Berechtigungselemente hinzugefügt werden.

   ![](assets/do-not-localize/triggers_13.png)

1. Fügen Sie für die Funktion **[!UICONTROL Dimensionen]** die für zukünftige Konfigurationen benötigten **[!UICONTROL Dimensionen]** hinzu.

   Stellen Sie sicher, dass die ausgewählten Dimensionen mit den unter dem externen Konto konfigurierten Dimensionen übereinstimmen, und stimmen Sie sie mit den entsprechenden Nummern der eVars aus Adobe Analytics ab.

1. Fügen Sie für die Funktion **[!UICONTROL Report Suite-Tools]** die folgenden Berechtigungen hinzu:

   * **[!UICONTROL Report Suite-Verwaltung]**
   * **[!UICONTROL Konversionsvariablen]**
   * **[!UICONTROL Erfolgsereignisse]**
   * **[!UICONTROL Benutzerdefinierter Data Warehouse-Bericht]**
   * **[!UICONTROL Datenquellen-Manager]**
   * **[!UICONTROL Klassifizierungen]**

1. Fügen Sie für die Funktion **[!UICONTROL Analytics-Tools]** die folgenden Berechtigungen hinzu:

   * **[!UICONTROL Code-Manager - Web-Services]**
   * **[!UICONTROL Protokolle - Web-Services]**
   * **[!UICONTROL Web-Services]**
   * **[!UICONTROL Web-Service-Zugriff]**
   * **[!UICONTROL Erstellung berechneter Metriken]**
   * **[!UICONTROL Segmenterstellung]**

Ihr Produktprofil ist jetzt konfiguriert. Anschließend müssen Sie das Adobe I/O-Projekt erstellen.

## Erstellen eines Adobe I/O-Projekts {#create-adobe-io}

1. Greifen Sie auf Adobe I/O zu und melden Sie sich als **Systemadministrator** Ihrer Organisation an.

   Weiterführende Informationen zu Administratorrollen finden Sie auf dieser [Seite](https://helpx.adobe.com/de/enterprise/using/admin-roles.html).

1. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Klicken Sie auf **[!UICONTROL Zum Projekt hinzufügen]** und wählen Sie **[!UICONTROL API]** aus.

   ![](assets/do-not-localize/triggers_6.png)

1. Wählen Sie [!DNL Adobe Analytics] und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Wählen Sie **[!UICONTROL Dienstkonto (JWT)]** als Authentifizierungstyp aus und klicken Sie auf **[!UICONTROL Weiter]**. 

   ![](assets/do-not-localize/triggers_8.png)

1. Wählen Sie die **[!UICONTROL Option 1: Schlüsselpaar generieren]** aus und klicken Sie auf **[!UICONTROL Schlüsselpaar generieren]**.

   Die Datei config.zip wird dann automatisch heruntergeladen.

   ![](assets/do-not-localize/triggers_9.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Wählen Sie das **[!UICONTROL Produktprofil]** aus, das in den vorherigen Schritten erstellt wurde, die in diesem [Abschnitt](#analytics-product-profile) beschrieben sind.

1. Klicken Sie dann auf **[!UICONTROL Konfigurierte API speichern]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Wählen Sie in Ihrem Projekt [!DNL Adobe Analytics] aus und kopieren Sie die folgenden Informationen unter **[!UICONTROL Dienstkonto (JWT)]**:

   * **[!UICONTROL Client ID]** (Client-ID)
   * **[!UICONTROL Client Secret]** (Client-Geheimnis)
   * **[!UICONTROL Technical account ID]** (Kennung des technischen Kontos)
   * **[!UICONTROL Organization ID]** (Organisationskennung)

   ![](assets/do-not-localize/triggers_12.png)

1. Verwenden Sie den in Schritt 6 generierten privaten Schlüssel.

   Wenn Sie Triggers bereits mit diesen Anmeldedaten eingerichtet haben, muss der private Schlüssel für diese Connector-Konfiguration identisch sein.

1. Codieren Sie den privaten Schlüssel mit dem folgenden Befehl: `base64 ./private.key > private.key.base64`. Dadurch wird der base64-Inhalt in einer neuen Datei `private.key.base64` gespeichert.

   >[!NOTE]
   >
   >Manchmal werden beim Kopieren/Einfügen des privaten Schlüssels automatisch zusätzliche Zeilen hinzugefügt. Vergessen Sie nicht, diese zu entfernen, bevor Sie Ihren privaten Schlüssel codieren.

1. Kopieren Sie die Inhalte aus der Datei `private.key.base64`.

1. Melden Sie sich über SSH bei jedem Container an, in dem die Adobe Campaign-Instanz installiert ist, und fügen Sie die Projektanmeldeinformationen in Adobe Campaign hinzu, indem Sie den folgenden Befehl als `neolane`-Benutzer ausführen. Dadurch werden die Anmeldeinformationen für das **[!UICONTROL Technische Konto]** in die Konfigurationsdatei der Instanz eingefügt.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

Sie können jetzt mit der Verwendung des Analytics-Connectors beginnen und Ihr Kundenverhalten verfolgen.
