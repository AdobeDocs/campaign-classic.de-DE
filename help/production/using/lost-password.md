---
title: Vergessenes Passwort
seo-title: Vergessenes Passwort
description: Vergessenes Passwort
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 5%

---


# Vergessenes Passwort{#lost-password}

Sie können ein verlorenes Kennwort ändern oder wiederherstellen.

Es gibt zwei mögliche Szenarien:

* Passwort verloren durch einen Adobe Campaign-Operator.

   In diesem Fall können Sie das Kennwort des Betreibers ändern. Dazu stellen Sie über einen Operator mit Administratorrechten eine Verbindung her, klicken Sie mit der rechten Maustaste auf einen Operator, wählen Sie **[!UICONTROL Aktionen]** > Kennwort **[!UICONTROL zurücksetzen]** und legen Sie das neue Kennwort des Operators fest. Es wird empfohlen, dass Operatoren ihr Kennwort ändern, wenn sie die Verbindung zum ersten Mal wiederherstellen.

   ![](assets/operator-passwd.png)

* **Interner** Passwortverlust (nur lokale Kunden).

   Wenn das **interne** Kennwort verloren geht, müssen Sie es erneut initialisieren. Gehen Sie dazu wie folgt vor:

   1. Bearbeiten Sie die **Datei /usr/local/neolane/nl6/conf/serverConf.xml** .
   1. Gehen Sie zur Zeile **internalPassword** .

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. Löschen Sie die Zeichenfolge in Anführungszeichen: **myPassword**

      Sie erhalten daher die folgende Zeile:

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

   1. Sie können jetzt Ihr neues Kennwort verwenden, um eine Verbindung im **internen** Modus herzustellen.

