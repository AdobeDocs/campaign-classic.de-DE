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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 6%

---

# Datenbank{#database}



Der Datenbankserver kann unabhängig vom vom vom Anwendungsserver oder den Servern verwendeten Betriebssystem auf einem beliebigen Betriebssystem ausgeführt werden, sofern eine Netzwerkverbindung besteht.

Das Betriebssystem des Datenbankservers ist nicht wichtig, solange die Verbindung mit den verschiedenen Komponenten von Adobe Campaign verfügbar ist.

Überprüfen Sie auch den Abschnitt [Datenbankzugriffsebenen](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) .

## Microsoft SQL Server {#microsoft-sql-server}

Der native Client muss auf den Adobe Campaign-Anwendungsservern installiert sein.

Sie können über das Konfigurationsfenster des ODBC-Treibers unter **SQL Server Native Client 11.0** nach dem nativen Client auf dem Server suchen.

Die folgende Zugriffs-DLL muss vorhanden sein: **sqlncli11.dll**.

Zugriffs-DLLs finden Sie auf der Microsoft-Website.

>[!NOTE]
>
>Der Zugriff auf Microsoft SQL Server von einem Anwendungsserver, der unter Linux ausgeführt wird, wird nicht unterstützt.

## Oracle {#oracle}

>[!NOTE]
>
>Spaltennamen mit Multibytezeichen werden nicht unterstützt.

Die Parameter **NLS_NCHAR_CHARACTERSET** und **NLS_CHARACTERSET** müssen ordnungsgemäß konfiguriert sein, damit die Datenbank in Unicode oder ANSI funktioniert.

Adobe Campaign verwendet die standardmäßige Oracle-Kodierung. Bei Verwendung einer anderen Kodierung kann es zu Problemen mit der Kompatibilität der Trigger kommen. Wenden Sie sich in diesem Fall an den technischen Support.

Verwenden Sie den folgenden Befehl **sqlplus** , um mehr über Ihre Kodierung zu erfahren:

```
SELECT * FROM nls_database_parameters ;
```

* Bei einer Unicode-Installation werden folgende Kodierungen unterstützt:

  ```
  NLS_NCHAR_CHARACTERSET         AL16UTF16
  NLS_CHARACTERSET         AL32UTF8
  ```

* Bei einer ANSI-Installation (Nicht-Unicode) wird nur die folgende Kodierung unterstützt:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Um sich bei **sqlplus** anzumelden, verwenden Sie das Oracle-Benutzerprofil:

```
su - oracle 
sqlplus 
[login] [password]
```

Sie können auch auf den [Oracle-Client unter Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux) verweisen.

## PostgresSQL {#postgressql}

Es wird empfohlen, die UTF-8-Unterstützung bei der Installation der Datenbank-Engine zu installieren. Auf diese Weise können Sie Unicode-Datenbanken erstellen.

**Verwandtes Thema**

* [Nicht angemeldete Option in Adobe Campaign Classic-Tabellen](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
