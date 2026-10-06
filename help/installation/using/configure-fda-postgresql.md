---
product: campaign
title: Zugriff auf PostgreSQL konfigurieren
description: Informationen zum Konfigurieren des Zugriffs auf PostgreSQL
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
TQID: 'https://experienceleague.adobe.com/LtYc7Rs7gJon-uE44-UlW0egGg8wdkmDaTY-XWurxUg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 10%
---
# Zugriff auf PostgreSQL konfigurieren {#configure-fda-postgresql}



Verwenden Sie die **-Option (Federated Data Access** (FDA) von Campaign, um in einer externen PostgreSQL-Datenbank gespeicherte Informationen zu verarbeiten.

## PostgreSQL-Konfiguration {#postgresql-configuration}

Zuerst müssen Sie Libpq installieren. Mit libpq können Clientprogramme Abfragen an den PostgreSQL-Backend-Server senden und die Ergebnisse dieser Abfragen empfangen.

Gehen Sie wie folgt vor, um den Zugriff auf [!DNL PostgreSQL] zu konfigurieren:

* Führen Sie für CentOS den folgenden `sudo apt-get -y install libpq-dev` aus.

* Führen Sie unter Linux den folgenden Befehl `yum install postgresql-devel` aus.

* Für Windows wird Libpq über `libpq.dll` implementiert, das in der Adobe Campaign-Installation enthalten ist.

In Adobe Campaign können Sie dann Ihr externes [!DNL PostgreSQL]-Konto konfigurieren. Weiterführende Informationen zur Konfiguration Ihres externen Kontos finden Sie in [diesem Abschnitt](#postgresql-external).

## Externes PostgreSQL-Konto {#postgresql-external}

>[!NOTE]
>
> PostgreSQL ist unter CentOS 7 und 6 verfügbar.

Sie müssen ein [!DNL PostgreSQL] externes Konto erstellen, um Ihre Campaign-Instanz mit Ihrer [!DNL PostgreSQL] externen Datenbank zu verbinden.

1. Klicken Sie **[!UICONTROL Campaign-]** auf **[!UICONTROL Administration]** &quot;>&quot; **[!UICONTROL Plattform]** &quot;>&quot; **[!UICONTROL Externe Konten]**.

1. Wählen Sie **[!UICONTROL Neu]** aus.

1. Wählen Sie **[!UICONTROL Externe Datenbank]** als **[!UICONTROL Typ]** Ihres externen Kontos aus.

1. Wählen **[!UICONTROL unter &quot;]**&quot; [!DNL PostgreSQL, Greenplum] aus der Dropdown **[!UICONTROL Typ]** aus.

   ![](assets/postgresql_1.png)

1. Konfigurieren Sie die **[!UICONTROL PostgreSQL]** Authentifizierung für externe Konten:

   * **[!UICONTROL Server]**: URL des [!DNL PostgreSQL].

   * **[!UICONTROL Konto]**: Name des Benutzers.

   * **[!UICONTROL Password]**: Kennwort für Benutzerkonto.

   * **[!UICONTROL Datenbank]**: Name der Datenbank (optional).

   * **[!UICONTROL Arbeitsschema]**: Name Ihres Arbeitsschemas. [Weitere Informationen](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Zeitzone]**: Die Zeitzone wird in [!DNL PostgreSQL] festgelegt. [Weitere Informationen](https://www.postgresql.org/docs/7.2/timezones.html)

1. Klicken Sie auf den Tab **[!UICONTROL Parameter]** und dann auf die Schaltfläche **[!UICONTROL Funktionen bereitstellen]**, um Funktionen zu erstellen.

   >[!NOTE]
   >
   >Damit alle Funktionen verfügbar sind, müssen Sie die Adobe Campaign SQL-Funktionen in der Remote-Datenbank erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../configuration/using/adding-additional-sql-functions.md).

1. Klicken Sie **[!UICONTROL Speichern]** wenn Ihre Konfiguration abgeschlossen ist.

Der Connector unterstützt die folgenden Optionen:

| Option | Beschreibung |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Maximale Wartezeit auf Verbindung in Sekunden. <br>Weiterführende Informationen hierzu finden Sie in der [Dokumentation zu PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Anzahl der Sekunden Inaktivität, nach denen das TCP eine Keepalive-Nachricht an den Server senden sollte. <br>Weiterführende Informationen hierzu finden Sie in der [Dokumentation zu PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Anzahl der Sekunden, nach denen die TCP-Keepalive-Nachricht, die nicht vom Server quittiert wurde, erneut übertragen werden soll.  <br>Weiterführende Informationen hierzu finden Sie in der [Dokumentation zu PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Anzahl der TCP-Keepalives, die verloren gehen können, bevor die Verbindung des Clients zum Server als inaktiv angesehen wird. <br>Weiterführende Informationen hierzu finden Sie in der [Dokumentation zu PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
