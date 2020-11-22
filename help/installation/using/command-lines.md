---
solution: Campaign Classic
product: campaign
title: Befehlszeilen
description: Befehlszeilen
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Befehlszeilen{#command-lines}

Die folgenden Befehlszeilen erfordern die Möglichkeit, auf den Anwendungsserver zuzugreifen. Bei Bereitstellungen, die von der Adobe gehostet werden, können diese Befehle nur von der Adobe ausgeführt werden.

## Erstellen einer Instanz {#creating-an-instance}

Die Instanzerstellung kann mithilfe von Befehlszeilen mit der folgenden Syntax ausgeführt werden:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(wobei **eng** und **fra** mögliche Werte für den `[lang]` Parameter sind)

Mit dem Befehl **nlserver config -addinstance:instance1/demo*/eng** können Sie eine Instanz mit dem Namen **instance1** in englischer Sprache mit der DNS-Maske demo* erstellen.

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

Mit dem folgenden Befehl wird die **Demo** -Instanz mit dem SQL-Typserver **base6** konfiguriert, der mit dem **Kampagne** -Konto und dem zugehörigen **Kennwort** auf dem **dbsrv** -Server verknüpft ist:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

