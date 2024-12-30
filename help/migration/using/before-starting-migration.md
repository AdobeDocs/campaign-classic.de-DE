---
product: campaign
title: Vor Beginn der Migration
description: Vor Beginn der Migration
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Voraussetzungen{#before-starting-migration}



Auf dieser Seite werden spezifische Schritte aufgelistet, die vor dem Starten des Migrationsprozesses ausgeführt werden müssen. Weitere Anleitungen finden Sie auch [dieser Seite](about-migration.md) .

>[!NOTE]
>
>In diesem Dokument werden Befehle als Beispiele angegeben. Sie können je nach Ihrer Konfiguration variieren.

1. Überprüfen Sie Ihre Adobe Campaign-Version: Installieren Sie vor der Migration den neuesten Build der aktuellen Version, die Sie verwenden.
1. Sichern Sie Ihre Daten.
1. Überprüfen Sie Ihre Umgebung: Sie können Ihr Datenbank-Engine-System (DBMS) nicht ändern. Sie können beispielsweise nicht von einer PostgreSQL-Engine zu einer Oracle-Engine wechseln. Sie können jedoch zur neuesten Version Ihrer Datenbank-Engine wechseln. Beachten Sie, dass es nicht möglich ist, von einer Nicht-Unicode-Datenbank zu einer Unicode-Datenbank zu wechseln.

## Migrationsschritte {#migration-steps}

Der Migrationsprozess muss auf allen Servern **alle** und in einer bestimmten Reihenfolge durchgeführt werden.

* Im Falle einer **eigenständigen Plattform** (Einzelcomputermodus) wird die Anwendung vollständig migriert.
* Im Fall einer **Standardplattform)** Unternehmen) die Migrationsschritte wie folgt:

   1. Migrieren Sie den Marketing-Server.
   1. Migrieren Sie den Mail-Server (MTA).
   1. Migrieren Sie die Weiterleitungs- und Tracking-Server (Apache/IIS).

* Im Falle einer **Cloud Messaging-Plattform** werden die Ausführungsserver auf Adobe Campaign gehostet. Bitte Adobe Campaign kontaktieren, um die Migration zwischen verschiedenen Servern zu koordinieren.
* Im Fall einer **Power Booster- oder Power Cluster-**) werden die folgenden Migrationsschritte ausgeführt:

   1. Migrieren Sie die Weiterleitungs- und Tracking-Server (Apache/IIS).
   1. Migrieren Sie die Power Booster-/Cluster-Server.
   1. Migrieren Sie den Marketing-Server.

## Benutzerkennwörter {#user-passwords}

In v7 **die Benutzerverbindung** intern **und admin** durch ein Passwort gesichert werden. Es wird dringend empfohlen, diesen Konten und allen Benutzerkonten (vor **) Kennwörter**. Wenn Sie kein Kennwort für **intern** angegeben haben, können Sie keine Verbindung herstellen. Geben Sie den folgenden Befehl ein, um **internal** ein Kennwort zuzuweisen:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>Das **interne** Kennwort muss für alle Tracking-Server identisch sein. Weitere Informationen finden Sie in den Abschnitten [Interne Kennung](../../installation/using/configuring-campaign-server.md#internal-identifier) und [Berechtigungen](../../platform/using/access-management.md) .
