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



Die folgenden Befehlszeilen erfordern die Möglichkeit, auf den Anwendungsserver zuzugreifen. Bei Bereitstellungen, die von Adobe gehostet werden, können diese Befehle nur von Adobe ausgeführt werden.

## Erstellen einer Instanz {#creating-an-instance}

Die Instanzerstellung kann mithilfe von Befehlszeilen mit der folgenden Syntax ausgeführt werden:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(wobei **eng** und **fra** mögliche Werte für den Parameter `[lang]` sind)

Mit dem Befehl **nlserver config -addinstance:instance1/demo&#42;/eng** können Sie eine Instanz mit dem Namen **instance1** in englischer Sprache mit der DNS-Maske demo&#42; erstellen.

## Datenbank deklarieren {#declaring-a-database}

Sie können eine vorhandene Datenbank über die Befehlszeile mit einer Instanz verknüpfen, indem Sie die folgende Syntax verwenden:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Die folgenden Werte sind für den Parameter **`[rdbms]`** möglich:

* **postgresql**: für PostgreSQL,
* **oracle**: für Oracle,
* **mssql**: für Microsoft SQL Server,

Mit dem folgenden Befehl wird die Instanz **demo** mit dem SQL-Typ-Server namens **base6** konfiguriert, der mit dem Konto **campaign** und seinem **password** auf dem Server **dbsrv** verknüpft ist:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
