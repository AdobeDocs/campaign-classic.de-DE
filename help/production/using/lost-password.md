---
product: campaign
title: Vergessenes Passwort
description: Vergessenes Passwort
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 7%

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
