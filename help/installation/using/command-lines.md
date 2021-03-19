---
solution: Campaign Classic
product: campaign
title: Befehlszeilen
description: Befehlszeilen
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Befehlszeilen{#command-lines}

Die folgenden Befehlszeilen erfordern die Möglichkeit, auf den Anwendungsserver zuzugreifen. Bei Bereitstellungen, die von der Adobe gehostet werden, können diese Befehle nur von der Adobe ausgeführt werden.

## Instanz {#creating-an-instance} erstellen

Die Instanzerstellung kann mithilfe von Befehlszeilen mit der folgenden Syntax ausgeführt werden:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(wobei **eng** und **fra** mögliche Werte für den Parameter `[lang]` sind)

Mit dem Befehl **nlserver config -addinstance:instance1/demo*/eng** können Sie eine Instanz namens **instance1** in englischer Sprache mit der DNS-Maske demo* erstellen.

## Datenbank {#declaring-a-database} deklarieren

Sie können eine vorhandene Datenbank mit einer Instanz über die Befehlszeile verknüpfen, indem Sie die folgende Syntax verwenden:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Folgende Werte sind für den Parameter **`[rdbms]`** möglich:

* **postgresql**: für PostgreSQL,
* **oracle**: für Oracle,
* **mssql**: für Microsoft SQL Server,
* **DB2**: für die DB2-Engine.

Mit dem folgenden Befehl wird die **demo**-Instanz mit dem SQL-Typserver namens **base6** konfiguriert, der mit dem **Kampagne**-Konto und dem **password** auf dem **dbsrv**-Server verknüpft ist:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

