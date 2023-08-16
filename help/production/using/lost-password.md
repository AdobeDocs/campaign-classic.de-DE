---
product: campaign
title: Vergessenes Passwort
description: Vergessenes Passwort
feature: Monitoring, Access Management
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 18%

---

# Vergessenes Passwort{#lost-password}



Sie können ein verlorenes Passwort ändern oder wiederherstellen.
Es gibt zwei mögliche Szenarien:

* [Passwort, das von einem Adobe Campaign-Benutzer verloren geht](#password-lost-by-campaign-operator)
* [Internes Kennwort verloren](#internal-password-lost) (nur On-Premise-Kunden)

## Passwort, das von einem Campaign-Benutzer verloren geht {#password-lost-by-campaign-operator}

Wenn ein Adobe Campaign-Benutzer sein Kennwort verliert, können Sie es ändern.
Gehen Sie dazu wie folgt vor:

1. Verbindung über einen Benutzer mit Administratorrechten
1. Klicken Sie mit der rechten Maustaste auf einen Operator.
1. Auswählen **[!UICONTROL Aktionen]** > **[!UICONTROL Kennwort zurücksetzen]**.

   ![](assets/operator-passwd.png)

1. Legen Sie das neue Kennwort des Benutzers fest. Es wird empfohlen, dass der Benutzer sein Kennwort ändert, wenn er sich zum ersten Mal erneut anmeldet.

## Internes Kennwort verloren {#internal-password-lost}

>[!NOTE]
>
>Dieser Abschnitt gilt nur für On-Premise-Kunden.

Wenn das interne Kennwort verloren geht, müssen Sie es erneut initialisieren.
Gehen Sie dazu wie folgt vor:

1. Bearbeiten Sie die **/usr/local/neolane/nl6/conf/serverConf.xml** -Datei.

1. Navigieren Sie zu **internalPassword** Linie.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Löschen Sie in diesem Fall die Zeichenfolge in Anführungszeichen: **myPassword**

   Sie erhalten somit die folgende Zeile:

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. Speichern Sie die Änderungen und schließen Sie die Datei.

1. Konfigurieren Sie das neue Kennwort. Geben Sie dazu die folgenden Befehle ein:

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Sie können jetzt Ihr neues Kennwort verwenden, um eine Verbindung herzustellen in **intern** -Modus.
