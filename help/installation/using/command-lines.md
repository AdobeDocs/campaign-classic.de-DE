---
product: campaign
title: Befehlszeilen
description: Befehlszeilen
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 144
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

Mit dem Befehl **nlserver config -addinstance:instance1/demo&#42;/eng** können Sie eine Instanz mit dem Namen **instance1** in englischer Sprache mit der DNS-Maske demo erstellen&#42;.

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
