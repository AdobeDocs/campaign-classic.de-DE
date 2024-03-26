---
product: campaign
title: Zugriff auf Amazon Redshift konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Amazon Redshift in FDA konfigurieren
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ef2b98bd-441e-4e59-bb41-4e835e250663
source-git-commit: 2ba6066b2999973e64ed3b429af78696f093dd09
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 29%

---

# Zugriff auf Amazon Redshift konfigurieren {#configure-access-to-redshift}

Verwenden von Campaign **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf Amazon Redshift zu konfigurieren.

1. Konfigurieren [Amazon Redshift-Datenbank](#configuring-redshift)
1. Konfigurieren von Amazon Redshift [externes Konto](#redshift-external) in Campaign

## Amazon Redshift unter Linux {#redshift-linux}

So konfigurieren Sie [!DNL Amazon Redshift] Gehen Sie unter Linux wie folgt vor:

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

1. Bevor Sie das Skript ausführen, können Sie mit der `--help` Option:

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

1. In Campaign können Sie dann Ihre [!DNL Amazon Redshift] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#redshift-external).

## Externes Amazon Redshift-Konto {#redshift-external}

Die [!DNL Amazon Redshift] Mit dem externen Konto können Sie Ihre Campaign-Instanz mit Ihrer externen Amazon Redshift-Datenbank verbinden.

1. Konfigurieren Sie in Campaign Classic Ihr externes [!DNL Amazon Redshift]-Konto. Klicken Sie im **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie die **[!UICONTROL Amazon Redshift]** externes Konto angeben:

   * **[!UICONTROL Typ]**: Amazon Redshift

   * **[!UICONTROL Server]**: Name des DNS

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Datenbank]**: Name Ihrer Datenbank, falls nicht im DSN angegeben. Kann leer bleiben, wenn im DSN angegeben

   * **[!UICONTROL Arbeitsschema]**: Name Ihres Arbeitsschemas. [Weitere Informationen](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Zeitzone]**: Zeitzone des Servers

   ![](assets/amazon_redshift.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
