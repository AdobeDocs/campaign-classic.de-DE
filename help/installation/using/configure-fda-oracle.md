---
product: campaign
title: Zugriff auf Oracle konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf Oracle in FDA konfigurieren
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 70%

---

# Zugriff auf Oracle konfigurieren {#configure-access-to-oracle}



Verwenden von Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA), um in externen Datenbanken gespeicherte Informationen zu verarbeiten. Gehen Sie wie folgt vor, um den Zugriff auf Oracle zu konfigurieren.

1. Konfigurieren von Oracle on [Linux](#oracle-linux) oder [Windows](#azure-windows)
1. Oracle konfigurieren [externes Konto](#oracle-external) in Campaign

## Oracle unter Linux {#oracle-linux}

Die Verbindung zu einer externen Oracle-Datenbank über die FDA-Option erfordert die zusätzlichen unten aufgeführten Konfigurationen auf dem Adobe Campaign-Server:

1. Installieren Sie den vollständigen Oracle-Client für Ihre jeweilige Oracle-Version.
1. Fügen Sie der Installation Ihre TNS-Definitionen hinzu. Spezifizieren Sie diese Definitionen dazu in der Datei **tnsnames.ora** im Verzeichnis /etc/oracle. Wenn dieses Verzeichnis nicht vorhanden ist, erstellen Sie es.

   Erstellen Sie dann eine neue TNS_ADMIN-Umgebungsvariable: Exportieren Sie TNS_ADMIN=/etc/oracle und starten Sie das Gerät neu.

1. Integrieren Sie Oracle in Ihren Adobe Campaign-Server (nlserver). Dazu muss die Datei **customer.sh** im Navigationsbaum des Adobe Campaign-Servers im Ordner &quot;nl6&quot; vorhanden sein; und die Datei muss die Links zu den Oracle-Bibliotheken enthalten.

   Beispiel für einen Client in 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Diese Werte (vor allem ORACLE_HOME) hängen von Ihren Installationsverzeichnissen ab. Prüfen Sie Ihren Navigationsbaums, bevor Sie diese Werte referenzieren.

1. Installieren Sie die für Oracle nötigen Bibliotheken:

   * **libclntsh.so**

     ```
     cd /usr/lib/oracle/<version>/client<architecture>/lib
     ln -s libclntsh.so.<version> libclntsh.so
     ```

   * **libaio1**

     ```
     apt install libaio1
     or
     yum install libaio1
     ```

1. In Campaign Classic können Sie dann Ihr externes [!DNL Oracle]-Konto konfigurieren. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#oracle-external).

## Oracle unter Windows {#oracle-windows}

Die Verbindung zu einer externen Oracle-Datenbank über die FDA-Option erfordert die zusätzlichen unten aufgeführten Konfigurationen auf dem Adobe Campaign-Server:

1. Installieren Sie den Oracle-Client.

1. Erstellen Sie im Ordner unter C:\Oracle eine **tnsnames.ora**-Datei, die Ihre TNS-Definition enthält.

1. Fügen Sie eine TNS_ADMIN-Umgebungsvariable mit C:\Oracle als Wert hinzu und starten Sie das Gerät neu.

1. In Campaign Classic können Sie dann Ihr externes [!DNL Oracle]-Konto konfigurieren. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#oracle-external).

## Externes oracle-Konto {#oracle-external}

Die [!DNL Oracle] Mit dem externen Konto können Sie Ihre Campaign-Instanz mit Ihrer externen Oracle-Datenbank verbinden.

1. Von Campaign **[!UICONTROL Explorer]** auswählen **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Auswählen **[!UICONTROL Neu]**.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Konfigurieren Sie das externe **[!UICONTROL Oracle]**-Konto. Geben Sie dazu Folgendes an:

   * **[!UICONTROL Typ]**: Oracle

   * **[!UICONTROL Server]**: Name des DNS

   * **[!UICONTROL Konto]**: Name des Benutzers

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos

   * **[!UICONTROL Zeitzone]**: Zeitzone des Servers

   ![](assets/oracle_config.png)
