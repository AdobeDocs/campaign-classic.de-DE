---
product: campaign
title: Campaign Classic-Datenbankempfehlungen
description: Datenbankempfehlungen
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
TQID: https://experienceleague.adobe.com/1rAC8pXCS8aKbzDrjv1HCa4W-Ieh3fx-nBzFbe8nMjg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 310
ht-degree: 11%

---

# Datenbank{#database}



Der Datenbankserver kann auf jedem beliebigen Betriebssystem ausgeführt werden, unabhängig vom Betriebssystem, das vom Anwendungsserver bzw. den Anwendungsservern verwendet wird, sofern eine Netzwerkverbindung zwischen ihnen besteht.

Das Betriebssystem des Datenbankservers ist nicht wichtig, solange eine Verbindung mit den verschiedenen Komponenten von Adobe Campaign verfügbar ist.

Überprüfen Sie auch den [Datenbankzugriffsebenen](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).

## Microsoft SQL Server {#microsoft-sql-server}

Der native Client muss auf den Adobe Campaign-Anwendungsservern installiert werden.

Sie können über das Bedienfeld für die ODBC-Treiberkonfiguration unter **SQL Server Native Client 11.0** prüfen, ob der native Client auf dem Server vorhanden ist.

Die folgende Zugriffs-DLL muss vorhanden sein: **sqlncli11.dll**.

Zugriffs-DLLs befinden sich auf der Microsoft-Website.

>[!NOTE]
>
>Der Zugriff auf Microsoft SQL Server von einem Anwendungsserver unter Linux wird nicht unterstützt.

## Oracle {#oracle}

>[!NOTE]
>
>Spaltennamen mit Multibyte-Zeichen werden nicht unterstützt.

Die **NLS_NCHAR_CHARACTERSET** und **NLS_CHARACTERSET** müssen ordnungsgemäß konfiguriert sein, damit die Datenbank in Unicode oder ANSI funktioniert.

Adobe Campaign verwendet die standardmäßige Oracle-Kodierung. Die Verwendung anderer Kodierungen kann zu Problemen mit der Trigger-Kompatibilität führen: Wenden Sie sich in diesem Fall an den technischen Support.

Verwenden Sie den folgenden Befehl **sqlplus**, um Ihre Kodierung zu ermitteln:

```
SELECT * FROM nls_database_parameters ;
```

* Bei einer Unicode-Installation werden folgende Kodierungen unterstützt:

  ```
  NLS_NCHAR_CHARACTERSET         AL16UTF16
  NLS_CHARACTERSET         AL32UTF8
  ```

* Für eine ANSI-Installation (ohne Unicode) wird nur die folgende Kodierung unterstützt:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Verwenden Sie zum Anmelden bei **sqlplus** das Oracle-Benutzerprofil:

```
su - oracle 
sqlplus 
[login] [password]
```

Weitere Informationen finden Sie unter [Oracle-Client unter Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

Es wird empfohlen, bei der Installation der Datenbank-Engine die UTF-8-Unterstützung zu installieren. Auf diese Weise können Sie Unicode-Datenbanken erstellen.

**Verwandtes Thema**

* [Nicht protokollierte Option in Adobe Campaign Classic-Tabellen](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
