---
product: campaign
title: Zugriff auf PostgreSQL konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf PostgreSQL konfigurieren
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 11%

---

# Zugriff auf PostgreSQL konfigurieren {#configure-fda-postgresql}



Verwenden Sie die Option Campaign **Federated Data Access** (FDA) , um in einer externen PostgreSQL-Datenbank gespeicherte Informationen zu verarbeiten.

## PostgreSQL-Konfiguration {#postgresql-configuration}

Sie müssen zuerst Libpq installieren. Libpq ermöglicht es Clientprogrammen, Abfragen an den PostgreSQL-Backend-Server zu senden und die Ergebnisse dieser Abfragen zu erhalten.

Gehen Sie wie folgt vor, um den Zugriff auf [!DNL PostgreSQL] zu konfigurieren:

* Führen Sie für CentOS den folgenden Befehl `sudo apt-get -y install libpq-dev` aus.

* Führen Sie für Linux den folgenden Befehl aus: `yum install postgresql-devel`.

* Für Windows wird Libpq über `libpq.dll` implementiert, das in der Adobe Campaign-Installation enthalten ist.

In Adobe Campaign können Sie dann Ihr externes [!DNL PostgreSQL] -Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#postgresql-external).

## Externes PostgreSQL-Konto {#postgresql-external}

>[!NOTE]
>
> PostgreSQL ist unter CentOS 7 und 6 verfügbar.

Sie müssen ein externes [!DNL PostgreSQL] -Konto erstellen, um Ihre Campaign-Instanz mit Ihrer externen [!DNL PostgreSQL] -Datenbank zu verbinden.

1. Klicken Sie in Campaign **[!UICONTROL Explorer]** auf **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Wählen Sie unter **[!UICONTROL Konfiguration]** [!DNL PostgreSQL, Greenplum] aus der Dropdown-Liste **[!UICONTROL Typ]** aus.

   ![](assets/postgresql_1.png)

1. Konfigurieren Sie die Authentifizierung des externen PostgreSQL ]**-Kontos:**[!UICONTROL 

   * **[!UICONTROL Server]**: URL des [!DNL PostgreSQL] -Servers.

   * **[!UICONTROL Konto]**: Name des Benutzers.

   * **[!UICONTROL Kennwort]**: Kennwort für Benutzerkonten.

   * **[!UICONTROL Datenbank]**: Name der Datenbank (optional).

   * **[!UICONTROL Arbeitsschema]**: Name Ihres Arbeitsschemas. [Weitere Informationen](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Zeitzone]**: Zeitzone festgelegt in [!DNL PostgreSQL]. [Weitere Informationen](https://www.postgresql.org/docs/7.2/timezones.html)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen bereitstellen]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die SQL-Funktionen von Adobe Campaign in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

1. Klicken Sie auf **[!UICONTROL Speichern]** , wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Maximale Wartezeit auf Verbindung in Sekunden. <br>Weitere Informationen hierzu finden Sie in der [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Anzahl der Sekunden Inaktivität, nach denen das TCP eine Keepalive-Nachricht an den Server senden soll. <br>Weitere Informationen hierzu finden Sie in der [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Anzahl der Sekunden, nach denen die vom Server nicht quittierte TCP-Keepalive-Nachricht erneut übertragen werden soll.  <br>Weitere Informationen hierzu finden Sie in der [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Anzahl der TCP-Keepalives, die verloren gehen können, bevor die Verbindung des Clients zum Server als unterbrochen betrachtet wird. <br>Weitere Informationen hierzu finden Sie in der [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
