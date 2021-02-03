---
solution: Campaign Classic
product: campaign
title: Microsoft Dynamics CRM-Connector
description: Campaign und Microsoft Dynamics verbinden
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 521bc3bf9b2507947007d7f458679275d407f910
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 100%

---


# Campaign und Microsoft Dynamics 365 verbinden {#connect-to-msdyn}

Auf dieser Seite erfahren Sie, wie Sie Campaign Classic mit **Microsoft Dynamics CRM 365** verbinden.

Implementierungsmöglichkeiten:

* per **Web-API** (empfohlen). Im [folgenden Abschnitt](#microsoft-dynamics-implementation-step) erfahren Sie, wie Sie die Verbindung mit Microsoft Dynamics herstellen.
* mit **Office 365**. Sehen Sie sich [dieses Video](#microsoft-dynamics-office-365) an, um die wichtigsten Schritte zum Einrichten der Integration kennenzulernen.
* Für eine **On-Premise**-Implementierung wenden Sie die Hauptschritte für Office 365 an.

Die Datensynchronisation erfolgt über eine eigene Workflow-Aktivität. [Weitere Informationen](../../platform/using/crm-data-sync.md).


>[!NOTE]
>
> Die mit Campaign kompatible CRM-Systemversion ist in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#CRMconnectors) aufgeführt.


## Implementierungsschritte{#microsoft-dynamics-implementation-steps}

Um Microsoft Dynamics 365 per **Web-API** mit Adobe Campaign zu verbinden, müssen Sie folgende Schritte ausführen:

In Microsoft Dynamics CRM:
1. Microsoft Dynamics Client-ID abrufen
1. Client-Geheimnis für Microsoft Dynamics generieren
1. Berechtigungen konfigurieren
1. Anwender erstellen
1. Privaten Schlüssel kodieren

[Weitere Informationen finden Sie in diesem Abschnitt](#config-crm-microsoft)

In Campaign Classic:
1. Neues externes Konto erstellen
1. Externes Konto mit Microsoft Dynamics-Einstellungen konfigurieren
1. Konfigurationsassistenten nutzen, um Tabellen zuzuordnen und Auflistungen zu synchronisieren
1. Synchronisations-Workflows erstellen

[Weitere Informationen finden Sie in diesem Abschnitt](#configure-acc-for-microsoft).


>[!CAUTION]
>
> Bei der Verbindung von Adobe Campaign mit Microsoft Dynamics können Sie Folgendes nicht tun:
> * Plugins installieren, die das Verhalten des CRM verändern; dadurch könnte es zu Kompatibilitätsproblemen mit Adobe Campaign kommen
> * Mehrere Auflistungen auswählen
>



## Microsoft Dynamics CRM konfigurieren {#config-crm-microsoft}

Um das Zugriffs-Token und die Schlüssel zum Einrichten des Kontos zu generieren, müssen Sie sich bei [Microsoft Azure Directory](https://portal.azure.com) unter Verwendung von Anmeldedaten für einen **globalen Administrator** anmelden. Gehen Sie dann wie folgt vor:

### Microsoft Dynamics Client-ID abrufen {#get-client-id-microsoft}

Um die Client-ID abzurufen, müssen Sie eine Anwendung in Azure Active Directory registrieren. Die Client-ID ist mit der Anwendungs-ID identisch.

1. Navigieren Sie zu **Azure Active Directory > App-Registrierungen** und klicken Sie auf **Neue Anwendung registrieren**.
1. Geben Sie einen eindeutigen Namen ein, der zur Identifizierung einer Instanz verwendet werden kann, z. B. **adobeccampaign`<instance identifier>`**.
1. Wählen Sie **Anwendungstyp** als **Web-App/API**.
1. Verwenden Sie `http://localhost` für die **Anmelde-URL**.

Nach dem Speichern erhalten Sie eine **Anwendungs-ID**, die der Client-Kennung für Campaign entspricht.

Weiterführende Informationen finden Sie auf [dieser Seite](https://docs.microsoft.com/de-de/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Client-Geheimnis für Microsoft Dynamics generieren {#config-client-secret-microsoft}

Das Client-Geheimnis ist derjenige Schlüssel, der für die Client-ID eindeutig ist. Gehen Sie wie folgt vor, um die Zertifikatschlüsselkennung abzurufen:

1. Navigieren Sie zu **Azure Active Directory > App-Registrierungen** und wählen Sie die zuvor erstellte Anwendung aus.
1. Klicken Sie auf **Zertifikate und Geheimnis**.
1. Klicken Sie auf **Zertifikat hochladen**, bevor Sie Ihr erzeugtes öffentliches Zertifikat suchen und hochladen.
1. Zum Generieren des Zertifikats können Sie &quot;openssl&quot; verwenden.

   Beispiel:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Klicken Sie auf den Link **manifest**, um die **Zertifikatschlüsselkennung** und die **Schlüsselkennung** abzurufen.

### Berechtigungen konfigurieren {#config-permissions-microsoft}

Sie müssen die **erforderlichen Berechtigungen** für die erstellte Anwendung konfigurieren.

1. Navigieren Sie zu **Azure Active Directory > App-Registrierungen** und wählen Sie die zuvor erstellte Anwendung aus.
1. Klicken Sie oben links auf **Einstellungen**.
1. Klicken Sie unter **Erforderliche Berechtigungen** auf **Hinzufügen** und **wählen Sie eine API > Dynamics CRM Online**.
1. Klicken Sie dann auf **Auswählen**, aktivieren Sie das Kontrollkästchen **Access Dynamics 365 als Organisationsbenutzer** und klicken Sie auf **Auswählen**.

### Anwendungsbenutzer erstellen {#create-app-user-microsoft}

Der Anwendungsbenutzer ist derjenige Benutzer, den die oben registrierte Anwendung verwenden wird. Alle Änderungen, die mit der oben registrierten Anwendung an Microsoft Dynamics vorgenommen werden, erfolgen über diesen Benutzer.

**Schritt 1**: Einen nicht interaktiven Benutzer in Azure Active Directory erstellen

1. Klicken Sie auf **Azure Active Directory > Benutzer** und dann auf **Neuer Benutzer**.
1. Geben Sie einen geeigneten Namen ein, den Sie verwenden möchten; der Benutzername sollte im E-Mail-Format vorliegen.
1. Wählen Sie **Dynamics 365-Administrator** in der **Verzeichnisrolle**.

**Schritt 2**: Dem erstellten Benutzer eine ordnungsgemäße Lizenz zuweisen

1. Klicken Sie in [Microsoft Azure](https://portal.azure.com) auf **Admin-App**.
1. Navigieren Sie zu **Benutzer > Aktive Benutzer** und klicken Sie auf den neu erstellten Benutzer.
1. Klicken Sie auf **Produktlizenzen bearbeiten** und wählen Sie **Dynamics 365 Customer Engagement-Plan**.
1. Klicken Sie auf **Schließen**.

**Schritt 3**: Anwendungsbenutzer in Dynamics CRM erstellen

1. Navigieren Sie von [Microsoft Azure](https://portal.azure.com) zu **Einstellungen > Sicherheit > Benutzer**.
1. Klicken Sie auf die Dropdown-Liste; wählen Sie dann **Anwender** und klicken Sie auf **Neu**.
1. Verwenden Sie denselben Benutzernamen wie für den Benutzer, der oben in Active Directory erstellt wurde.

   >[!NOTE]
   >
   >Sollten Sie denselben Namen verwenden, wird der Fehler für doppelte Schlüssel ausgegeben. Nutzen Sie daher einen anderen Benutzernamen und fahren Sie fort, bis Sie eine Bestätigung erhalten haben, ob dieser Schritt erforderlich ist.

1. Weisen Sie die **Anwendungs-ID** für [die zuvor erstellte Anwendung zu](#get-client-id-microsoft).
1. Klicken Sie auf **Rollen verwalten** und wählen Sie den Benutzer die Rolle **Systemadministrator** für aus.

## Campaign konfigurieren {#configure-acc-for-microsoft}

Um Microsoft Dynamics 365 mit Campaign zu verbinden, müssen Sie ein dediziertes externes Konto in Campaign erstellen und konfigurieren.

1. Navigieren Sie zu **[!UICONTROL Administration > Plattform > Externe Konten]**.

1. Erstellen Sie ein neues externes Konto und wählen Sie den Typ **[!UICONTROL Microsoft Dynamics CRM]** sowie die Option **[!UICONTROL Aktivieren]**.

1. Wählen Sie den Freigabetyp **[!UICONTROL Web-API]**:

   Adobe Campaign Classic unterstützt die Dynamics 365 REST-Schnittstelle mit dem OAuth-Protokoll zur Authentifizierung mit einem **[!UICONTROL Zertifikat]** oder **[!UICONTROL Passwort]**.

   Nutzen Sie die Einstellungen, die Sie in Azure Directory [zuvor definiert](#get-client-id-microsoft) haben, um das externe Konto zu konfigurieren.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >Die Konfiguration des externen Microsoft Dynamics CRM-Kontos wird [in diesem Abschnitt ](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account) genauer erläutert.

1. Klicken Sie auf den Link **[!UICONTROL Konfigurationsassistent für Microsoft CRM ...]**: Adobe Campaign erkennt die Tabellen aus der Microsoft Dynamics-Datenvorlage automatisch.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Wählen Sie die Tabellen aus, die abgerufen werden sollen.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**, um die Erstellung des entsprechenden Schemas zu starten.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Zur Übernahme der Konfiguration müssen Sie sich von der Adobe Campaign-Konsole ab- und wieder anmelden.

   Sie können überprüfen, ob das entsprechende Datenschema in Adobe Campaign verfügbar ist.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Klicken Sie auf den Link **[!UICONTROL Auflistungssynchronisation...]**, um mit dem Synchronisieren von Auflistungen zwischen Adobe Campaign und Microsoft Dynamics zu beginnen.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign und Microsoft Dynamics sind nun miteinander verbunden. Sie können eine Datensynchronisation zwischen den beiden Systemen einrichten. Weitere Informationen finden Sie im Abschnitt [Datensynchronisation](../../platform/using/crm-data-sync.md).

## Integration mit Microsoft Dynamics CRM und Office 365 konfigurieren{#microsoft-dynamics-office-365}

Sehen Sie sich dieses Video an, um zu erfahren, wie Sie Dynamics 365 im Rahmen einer Office 365-Implementierung mit Adobe Campaign Classic integrieren können.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


## Unterstützte Felddatentypen {#ms-dyn-supported-types}

Bei Microsoft Dynamics 365 werden folgende Attributtypen unterstützt/nicht unterstützt:


| Attributtyp | Unterstützt |
| --------------------------------------------------------------------------------- | --------- |
| Basistypen: Boolesch, Datum + Uhrzeit, Dezimalzahl, Gleitkommazahl, Dublette, Integer, Bigint, Zeichenfolge | Ja |
| Geld (als Dublette) | Ja |
| memo, entityname, primarykey, uniqueidentifier (als Zeichenfolgen) | Ja |
| Status, Auswahlliste (wir speichern die möglichen Werte in Auflistungen), Status (Zeichenfolge) | Ja |
| owner (als Zeichenfolge) | Ja |
| Suche (nur Referenzsuche einzelner Entitäten) | Ja |
| customer | Nein |
| Regarding | Nein |
| PartyList | Nein |
| ManagedProperty | Nein |
