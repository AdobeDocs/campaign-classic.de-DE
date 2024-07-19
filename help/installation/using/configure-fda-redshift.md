---
product: campaign
title: Zugriff auf Amazon Redshift konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Amazon Redshift in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ef2b98bd-441e-4e59-bb41-4e835e250663
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 27%

---

# Zugriff auf Amazon Redshift konfigurieren {#configure-access-to-redshift}

Verwenden Sie die Option Campaign **Federated Data Access** (FDA) , um in externen Datenbanken gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf Amazon Redshift zu konfigurieren.

1. Konfigurieren der [Amazon Redshift-Datenbank](#configuring-redshift)
1. Konfigurieren des externen Amazon Redshift [account](#redshift-external) in Campaign

## Amazon Redshift unter Linux {#redshift-linux}

Gehen Sie wie folgt vor, um [!DNL Amazon Redshift] unter Linux zu konfigurieren:

1. Überprüfen Sie vor der ODBC-Installation, ob die folgenden Pakete auf Ihrer Linux-Distribution installiert sind:

   * Für Red Hat/CentOS:

     ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
     ```

   * Für Debian:

     ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
     ```

1. Bevor Sie das Skript ausführen, können Sie mit der Option `--help` auf weitere Informationen zugreifen:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./redshift_odbc-setup.sh --help
   ```

1. Rufen Sie den Ordner auf, in dem sich das Skript befindet, und führen Sie das folgende Skript als Stammbenutzer aus:

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. Nach der Installation der ODBC-Treiber müssen Sie Campaign Classic neu starten. Führen Sie dazu den folgenden Befehl aus:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign können Sie dann Ihr externes [!DNL Amazon Redshift] -Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#redshift-external).

## Externes Amazon Redshift-Konto {#redshift-external}

Mit dem externen Konto [!DNL Amazon Redshift] können Sie Ihre Campaign-Instanz mit Ihrer externen Amazon Redshift-Datenbank verbinden.

1. Konfigurieren Sie in Campaign Classic Ihr externes [!DNL Amazon Redshift]-Konto. Klicken Sie im **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe Konto **[!UICONTROL Amazon Redshift]** , indem Sie Folgendes angeben:

   * **[!UICONTROL Typ]**: Amazon Redshift

   * **[!UICONTROL Server]**: Name des DNS

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name Ihrer Datenbank, falls nicht im DSN angegeben. Kann leer bleiben, wenn im DSN angegeben

   * **[!UICONTROL Arbeitsschema]**: Name Ihres Arbeitsschemas. [Weitere Informationen](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Zeitzone]**: Zeitzone des Servers

   ![](assets/amazon_redshift.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
