---
solution: Campaign Classic
product: campaign
title: Vergessenes Passwort
description: Vergessenes Passwort
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 7%

---


# Vergessenes Passwort{#lost-password}

Sie können ein verlorenes Kennwort ändern oder wiederherstellen.
Es gibt zwei mögliche Szenarien:

* [Passwort verloren durch Adobe Campaign-Operator](#password-lost-by-campaign-operator)
* [Internes Passwort verloren](#internal-password-lost)  (nur lokale Kunden)

## Passwort verloren durch den Operator {#password-lost-by-campaign-operator} einer Kampagne

Wenn ein Adobe Campaign-Operator sein Kennwort verliert, können Sie es ändern.
Gehen Sie dazu wie folgt vor:

1. Verbinden Sie sich über einen Operator mit Administratorrechten.
1. Klicken Sie mit der rechten Maustaste auf einen Operator.
1. Wählen Sie **[!UICONTROL Aktionen]** > **[!UICONTROL Kennwort zurücksetzen]**.

   ![](assets/operator-passwd.png)

1. Legen Sie das neue Kennwort des Operators fest. Es wird empfohlen, dass der Bediener beim ersten erneuten Verbinden das Kennwort ändert.

## Internes Kennwort verloren {#internal-password-lost}

>[!NOTE]
>
>Dieser Abschnitt gilt nur für lokale Kunden.

Wenn das interne Kennwort verloren geht, müssen Sie es erneut initialisieren.
Gehen Sie dazu wie folgt vor:

1. Bearbeiten Sie die Datei **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Gehen Sie zur Zeile **internalPassword**.

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

1. Sie können jetzt Ihr neues Kennwort verwenden, um eine Verbindung im Modus **Internal** herzustellen.
