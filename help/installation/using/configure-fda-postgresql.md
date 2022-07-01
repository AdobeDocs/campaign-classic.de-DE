---
product: campaign
title: Zugriff auf PostgreSQL konfigurieren
description: Erfahren Sie, wie Sie den Zugriff auf PostgreSQL konfigurieren
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 14%

---

# Zugriff auf PostgreSQL konfigurieren {#configure-fda-postgresql}

![](../../assets/v7-only.svg)

Verwenden von Campaign **Federated Data Access** (FDA), um in einer externen PostgreSQL-Datenbank gespeicherte Informationen zu verarbeiten.

## PostgreSQL-Konfiguration {#postgresql-configuration}

Sie müssen zuerst Libpq installieren. Libpq ermöglicht es Clientprogrammen, Abfragen an den PostgreSQL-Backend-Server zu senden und die Ergebnisse dieser Abfragen zu erhalten.

Gehen Sie wie folgt vor, um den Zugriff auf [!DNL PostgreSQL]:

* Führen Sie für CentOS den folgenden Befehl aus `sudo apt-get -y install libpq-dev`.

* Führen Sie für Linux den folgenden Befehl aus `yum install postgresql-devel`.

* Für Windows wird Libpq über implementiert. `libpq.dll` , die in der Adobe Campaign-Installation enthalten ist.

In Adobe Campaign können Sie dann Ihre [!DNL PostgreSQL] externes Konto. Weitere Informationen zur Konfiguration Ihres externen Kontos finden Sie unter [diesem Abschnitt](#postgresql-external).

## Externes PostgreSQL-Konto {#postgresql-external}

>[!NOTE]
>
> PostgreSQL ist unter CentOS 7 und 6 verfügbar.

Sie müssen eine [!DNL PostgreSQL] externes Konto, um Ihre Campaign-Instanz mit Ihrer [!DNL PostgreSQL] externe Datenbank.

1. Von Campaign **[!UICONTROL Explorer]** klicken **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Plattform]** &#39;>&#39; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. under **[!UICONTROL Konfiguration]** auswählen [!DNL PostgreSQL, Greenplum] von **[!UICONTROL Typ]** Dropdown-Liste.

   ![](assets/postgresql_1.png)

1. Konfigurieren Sie die **[!UICONTROL PostgreSQL]** Externe Kontoauthentifizierung:

   * **[!UICONTROL Server]**: URL des [!DNL PostgreSQL]-Servers.

   * **[!UICONTROL Konto]**: Name des Benutzers.

   * **[!UICONTROL Passwort]**: Passwort des Benutzerkontos.

   * **[!UICONTROL Datenbank]**: Name der Datenbank (optional).

   * **[!UICONTROL Arbeitsschema]**: Name Ihres Arbeitsschemas. [Weitere Informationen](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Zeitzone]**: Zeitzone festgelegt in [!DNL PostgreSQL]. [Weitere Informationen](https://www.postgresql.org/docs/7.2/timezones.html)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen freigeben]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die SQL-Funktionen von Adobe Campaign in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

1. Klicken **[!UICONTROL Speichern]** wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung  |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Maximale Wartezeit auf Verbindung in Sekunden. <br>Weitere Informationen hierzu finden Sie unter [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Anzahl der Sekunden Inaktivität, nach denen das TCP eine Keepalive-Nachricht an den Server senden soll. <br>Weitere Informationen hierzu finden Sie unter [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Anzahl der Sekunden, nach denen die vom Server nicht quittierte TCP-Keepalive-Nachricht erneut übertragen werden soll.  <br>Weitere Informationen hierzu finden Sie unter [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Anzahl der TCP-Keepalives, die verloren gehen können, bevor die Verbindung des Clients zum Server als unterbrochen betrachtet wird. <br>Weitere Informationen hierzu finden Sie unter [PostgreSQL-Dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
