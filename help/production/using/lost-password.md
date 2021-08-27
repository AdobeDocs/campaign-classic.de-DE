---
product: campaign
title: Vergessenes Passwort
description: Vergessenes Passwort
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 7%

---

# Vergessenes Passwort{#lost-password}

![](../../assets/v7-only.svg)

Sie können ein verlorenes Passwort ändern oder wiederherstellen.
Es gibt zwei mögliche Szenarien:

* [Passwort, das von einem Adobe Campaign-Benutzer verloren geht](#password-lost-by-campaign-operator)
* [Internes Kennwort verloren](#internal-password-lost)  (nur On-Premise-Kunden)

## Passwort, das von einem Campaign-Benutzer verloren geht {#password-lost-by-campaign-operator}

Wenn ein Adobe Campaign-Benutzer sein Kennwort verliert, können Sie es ändern.
Gehen Sie dazu wie folgt vor:

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

1. Bearbeiten Sie die Datei **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Wechseln Sie zur Zeile **internalPassword** .

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

1. Sie können jetzt Ihr neues Kennwort verwenden, um eine Verbindung im Modus **Internal** herzustellen.
