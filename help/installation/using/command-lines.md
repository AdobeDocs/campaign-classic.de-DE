---
title: Befehlszeilen
seo-title: Befehlszeilen
description: Befehlszeilen
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Befehlszeilen{#command-lines}

Die folgenden Befehlszeilen erfordern die Möglichkeit, auf den Anwendungsserver zuzugreifen. Bei Bereitstellungen, die von Adobe gehostet werden, können diese Befehle nur von Adobe ausgeführt werden.

## Erstellen einer Instanz {#creating-an-instance}

Die Instanzerstellung kann mithilfe von Befehlszeilen mit der folgenden Syntax ausgeführt werden:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(wobei **eng** und **fra** mögliche Werte für den `[lang]` Parameter sind)

Mit dem Befehl **nlserver config -addinstance:instance1/demo*/eng** können Sie eine Instanz namens **instance1** in englischer Sprache mit der DNS-Maske demo* erstellen.

## Datenbank deklarieren {#declaring-a-database}

Sie können eine vorhandene Datenbank mit einer Instanz über die Befehlszeile verknüpfen, indem Sie die folgende Syntax verwenden:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Folgende Werte sind für den **`[rdbms]`** Parameter möglich:

* **postgresql**: für PostgreSQL,
* **oracle**: für Oracle,
* **mssql**: für Microsoft SQL Server,
* **DB2**: für die DB2-Engine.

Mit dem folgenden Befehl wird die **Demo** -Instanz mit dem SQL-Typ-Server **base6** konfiguriert, der mit dem **Kampagnenkonto** und seinem **Kennwort** auf dem **dbsrv** -Server verknüpft ist:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

