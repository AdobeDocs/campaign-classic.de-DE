---
title: Vor Beginn der Migration
seo-title: Vor Beginn der Migration
description: Vor Beginn der Migration
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 3%

---


# Vor Beginn der Migration{#before-starting-migration}

>[!NOTE]
>
>In diesem Dokument werden die mit der Datenbank verknüpften Befehle als Beispiel genannt. Diese können je nach Konfiguration variieren. Wenden Sie sich an Ihren Datenbankadministrator.

## Warnhinweise {#warnings}

### Installierte Version {#installed-version}

Vor der Migration sollten Sie den neuesten Build der aktuellen Version installieren, die Sie verwenden.

Überprüfen Sie die Version auf Ihrem Server, indem Sie das Menü **[!UICONTROL Hilfe > Info]** auf der Client-Konsole mit dem **nlserver-Befehl pdump** aufrufen.

### Datensicherung {#data-backup}

Bevor Sie einen Migrationsprozess starten, **müssen** Sie Ihre Daten sichern.

### Umgebung {#environment}

* Es ist nicht möglich, den Datenbankmodultyp (DBMS) zu ändern. Sie können beispielsweise nicht von einer PostgreSQL-Engine zu einer Oracle-Engine wechseln. Sie können jedoch von einer Oracle 8-Engine auf eine Oracle 10-Engine umstellen.
* Es ist nicht möglich, von einer Nicht-Unicode-Datenbank zu einer Unicode-Datenbank zu wechseln.

### Empfehlung {#recommendation}

Da der Migrationsvorgang besonders sensibel ist, empfehlen wir dringend, dieses Dokument vor dem Beginn des Verfahrens gründlich zu lesen.

## Migrationsschritte {#migration-steps}

Das Migrationsverfahren muss auf **allen** Servern und in einer bestimmten Reihenfolge durchgeführt werden.

* Bei einer **eigenständigen Plattform** (Einzelmaschinenmodus) wird die Anwendung vollständig migriert.
* Bei einer **Standardplattform** (Unternehmen) werden die folgenden Migrationsschritte ausgeführt:

   1. Migrieren des Marketing-Servers.
   1. Migrieren Sie den Mail-Server (mta).
   1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).

* Bei einer **Cloud Messaging-Plattform** werden die Ausführungsserver im Adobe Campaign gehostet. Wenden Sie sich an Adobe Campaign, um die Migration zwischen verschiedenen Servern zu koordinieren.
* Bei einer **Power Booster- oder Power Cluster-Plattform** werden die folgenden Migrationsschritte ausgeführt:

   1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).
   1. Migrieren Sie die Power Booster/Cluster-Server.
   1. Migrieren des Marketing-Servers.

>[!NOTE]
>
>Die Kommunikation zwischen einem Marketing-Server der Version 6.02 und einem Server der Version 7 Cloud Messaging oder Power Booster/Cluster ist möglich. Wenn Sie sich jedoch entscheiden, Ihren Marketing-Server der Version 6.02 zu behalten, muss dieser mit dem neuesten Build der Version 6.02 aktualisiert werden, bevor Sie zu Cloud Messaging oder Power Booster/Cluster migrieren.

## Benutzerkennwörter {#user-passwords}

In v7 muss die **interne** Verbindung mit dem **Operator** mit einem Kennwort gesichert werden. Es wird dringend empfohlen, diesen Konten und allen Operatorkonten **vor der Migration** Passwörter zuzuweisen. Wenn Sie kein Kennwort für **intern** angegeben haben, können Sie keine Verbindung herstellen. Geben Sie den folgenden Befehl ein, um ein Kennwort **intern** zuzuweisen:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Das **interne** Kennwort muss für alle Tracking-Server identisch sein. Weitere Informationen finden Sie in den Abschnitten [Interne ID](../../installation/using/campaign-server-configuration.md#internal-identifier) und [Berechtigungen](../../platform/using/access-management.md#about-permissions) .

