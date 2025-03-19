---
product: campaign
title: Befehlszeilen
description: Befehlszeilen
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%

---

# Befehlszeilen{#command-lines}



Für die folgenden Befehlszeilen ist der Zugriff auf den Anwendungsserver erforderlich. Bei Bereitstellungen, die von Adobe gehostet werden, können diese Befehle nur von Adobe ausgeführt werden.

## Instanz erstellen {#creating-an-instance}

Die Instanzerstellung kann über Befehlszeilen mit der folgenden Syntax ausgeführt werden:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(wobei **eng** und **fra** mögliche Werte für den `[lang]` sind)

Der Befehl **nlserver config -addinstance:instance1/demo&#42;/eng** ermöglicht die Erstellung einer Instanz namens **instance1** in englischer Sprache mit der DNS-Maske demo&#42;.

## Datenbank deklarieren {#declaring-a-database}

Sie können eine vorhandene Datenbank mit einer -Instanz über die Befehlszeile verknüpfen, indem Sie die folgende Syntax verwenden:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Die folgenden Werte sind für den **`[rdbms]`** Parameter möglich:

* **PostgreSQL**: für PostgreSQL,
* **Oracle**: für Oracle,
* **mssql**: für Microsoft SQL Server,

Mit dem folgenden Befehl wird die **demo**-Instanz mit dem SQL-Servertyp **base6** konfiguriert, der mit dem **campaign**-Konto und dessen **password** auf dem **dbsrv**-Server verknüpft ist:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
