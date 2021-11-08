---
product: campaign
title: Befehlszeilen
description: Befehlszeilen
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Befehlszeilen{#command-lines}

![](../../assets/v7-only.svg)

Die folgenden Befehlszeilen erfordern die Möglichkeit, auf den Anwendungsserver zuzugreifen. Bei Bereitstellungen, die von Adobe gehostet werden, können diese Befehle nur von Adobe ausgeführt werden.

## Erstellen einer Instanz {#creating-an-instance}

Die Instanzerstellung kann mithilfe von Befehlszeilen mit der folgenden Syntax ausgeführt werden:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

, **eng** und **fra** sind mögliche Werte für `[lang]` Parameter)

Der Befehl **nlserver config -addinstance:instance1/demo*/eng** ermöglicht Ihnen die Erstellung einer Instanz mit dem Namen **instance1** Englisch mit der DNS-Maske demo*.

## Datenbank deklarieren {#declaring-a-database}

Sie können eine vorhandene Datenbank über die Befehlszeile mit einer Instanz verknüpfen, indem Sie die folgende Syntax verwenden:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Die folgenden Werte sind für die **`[rdbms]`** Parameter:

* **postgresql**: für PostgreSQL,
* **oracle**: für Oracle,
* **mssql**: für Microsoft SQL Server,
* **DB2**: für die DB2-Engine.

Der folgende Befehl konfiguriert die **Demo** -Instanz mit dem SQL-Typ-Server, bekannt als **base6**, verknüpft mit der **Kampagne** und **password** auf **dbsrv** server:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
