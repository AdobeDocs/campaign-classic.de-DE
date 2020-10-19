---
title: Empfehlungen zur Campaign Classic-Datenbank
description: Datenbankempfehlungen
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---


# Datenbank{#database}

Der Datenbankserver kann auf einem beliebigen Betriebssystem ausgeführt werden, unabhängig vom Betriebssystem, das vom Anwendungsserver oder von den Servern verwendet wird, sofern eine Netzwerkverbindung besteht.

Das Betriebssystem des Datenbankservers ist nicht wichtig, solange die Verbindung mit den verschiedenen Komponenten von Adobe Campaign verfügbar ist.

Überprüfen Sie auch den Abschnitt [Datenbankzugriffsebenen](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) .

## Microsoft SQL Server {#microsoft-sql-server}

Der native Client muss auf den Adobe Campaign-Anwendungsservern installiert sein.

Sie können den nativen Client auf dem Server über das ODBC-Treiberkonfigurationsbedienfeld unter **SQL Server Native Client 11.0** suchen.

Die folgende Zugriffs-DLL muss vorhanden sein: **sqlncli11.dll**.

Zugriff auf DLLs finden Sie auf der Microsoft-Website.

>[!NOTE]
>
>Der Zugriff auf Microsoft SQL Server von einem Anwendungsserver, der unter Linux ausgeführt wird, wird nicht unterstützt.

## Oracle {#oracle}

>[!NOTE]
>
>Spaltennamen mit Multibyte-Zeichen werden nicht unterstützt.

Die **Parameter** NLS_NCHAR_CHARACTERSET **und** NLS_CHARACTERSETmüssen ordnungsgemäß konfiguriert sein, damit die Datenbank in Unicode oder ANSI funktioniert.

Adobe Campaign verwendet die standardmäßige Oracle-Kodierung. Die Verwendung anderer Kodierungen kann Kompatibilitätsprobleme auslösen: in diesem Fall wenden Sie sich bitte an den technischen Support.

Um mehr über Ihre Kodierung zu erfahren, verwenden Sie den folgenden **Befehl sqlplus** :

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

Um sich bei **sqlplus** anzumelden, verwenden Sie das Oracle-Profil:

```
su - oracle 
sqlplus 
[login] [password]
```

Sie können auch auf [Oracle Client in Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux)verweisen.

## PostgresSQL {#postgressql}

Es wird empfohlen, die UTF-8-Unterstützung bei der Installation der Datenbank-Engine zu installieren. Auf diese Weise können Sie Unicode-Datenbanken erstellen.

**Verwandtes Thema**

* [Nicht angemeldete Option in Adobe Campaign Classic-Tabellen](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
