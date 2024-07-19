---
product: campaign
title: Vergessenes Passwort
description: Vergessenes Passwort
feature: Monitoring, Access Management
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 12%

---

# Vergessenes Passwort{#lost-password}

>[!NOTE]
>
>Diese Seite betrifft nur Benutzende, die mit nativer Authentifizierung eine Verbindung zu Campaign herstellen.

Sie können ein verlorenes Passwort ändern oder wiederherstellen.
Es gibt zwei mögliche Szenarien:

* [Passwort, das von einem Adobe Campaign-Benutzer verloren geht](#password-lost-by-campaign-operator)
* [Internes Kennwort verloren ](#internal-password-lost) (nur On-Premise-Kunden)

## Passwort, das von einem Campaign-Benutzer verloren geht {#password-lost-by-campaign-operator}

Wenn ein Adobe Campaign-Benutzer sein Kennwort verliert, können Sie es ändern.

>[!NOTE]
>
>Dieses Verfahren gilt nur für Benutzer, die mit nativer Authentifizierung eine Verbindung zu Campaign herstellen. Informationen zur Adobe IMS-Authentifizierung finden Sie in [dieser Dokumentation](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

Gehen Sie wie folgt vor, um ein Campaign-Kennwort zurückzusetzen:

1. Verbindung über einen Benutzer mit Administratorrechten
1. Klicken Sie mit der rechten Maustaste auf einen Operator.
1. Wählen Sie **[!UICONTROL Aktionen]** > **[!UICONTROL Kennwort zurücksetzen]** aus.

   ![](assets/operator-passwd.png)

1. Legen Sie das neue Kennwort des Benutzers fest. Es wird empfohlen, dass der Benutzer sein Kennwort ändert, wenn er sich zum ersten Mal erneut anmeldet.

## Internes Kennwort verloren {#internal-password-lost}

>[!NOTE]
>
>Dieser Abschnitt gilt nur für On-Premise-Kunden.

Wenn das interne Kennwort verloren geht, müssen Sie es erneut initialisieren.

Gehen Sie dazu wie folgt vor:

1. Bearbeiten Sie die Datei &quot;**/usr/local/neolane/nl6/conf/serverConf.xml**&quot;.

1. Wechseln Sie zur Zeile **internalPassword** .

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Löschen Sie die Zeichenfolge in Anführungszeichen, in diesem Fall: `myPassword`. Sie erhalten die folgende Zeile:

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. Speichern Sie die Änderungen und schließen Sie die Datei.

1. Beenden Sie den `nlserver`-Prozess.

1. Konfigurieren Sie das neue Kennwort. Geben Sie dazu die folgenden Befehle ein:

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Starten Sie den `nlserver`-Prozess.

1. Sie können jetzt Ihr neues Kennwort verwenden, um eine Verbindung im Modus **Intern** herzustellen.
