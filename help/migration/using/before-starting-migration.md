---
solution: Campaign Classic
product: campaign
title: Vor Beginn der Migration
description: Vor Beginn der Migration
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 2%

---


# Vor Beginn der Migration{#before-starting-migration}

>[!NOTE]
>
>In diesem Dokument werden die mit der Datenbank verknüpften Befehle als Beispiel genannt. Diese können je nach Konfiguration variieren. Wenden Sie sich an Ihren Datenbankadministrator.

## Warnhinweise {#warnings}

* Der Migrationsprozess darf nur von erfahrenen Benutzern durchgeführt werden. Sie müssen von mindestens einem Datenbankexperten, einem Systemadministrator und einem Anwendungsentwickler aus Adobe Campaign unterstützt werden.
* Bevor Sie mit der Migration beginnen, überprüfen Sie, ob die verwendeten Systeme und Systemkomponenten tatsächlich mit v7 kompatibel sind. Lesen Sie die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).
* Wenn Sie Adobe Campaign Cloud Messaging (Mid-Sourcing) verwenden, wenden Sie sich an die Adobe, bevor Sie den gesamten Migrationsvorgang starten.
* Bevor Sie einen Migrationsprozess starten, müssen Sie **Ihre Daten sichern.**
* Der Migrationsvorgang kann mehrere Tage dauern.
* Die Konfiguration von Adobe Campaign v7 ist strenger als die Version 5.11 und 6.02. Dadurch sollen Probleme wie Datenbeschädigung vermieden und die Datenintegrität in der Datenbank gewahrt werden. Daher funktionieren bestimmte Funktionen, die in Version 5.11 und Version 6.02 angeboten werden, möglicherweise nicht mehr in Version 7 und müssen daher nach der Migration angepasst werden. Vor der Inbetriebnahme sollten Sie alle Konfigurationen, insbesondere Workflows, die zur Verwendung von Adobe Campaign erforderlich sind, systematisch testen.

### Installierte Version {#installed-version}

Vor der Migration sollten Sie den neuesten Build der aktuellen Version installieren, die Sie verwenden.

Überprüfen Sie die Version auf Ihrem Server, indem Sie das Menü **[!UICONTROL Hilfe> Info]** auf der Client-Konsole mit dem Befehl **nlserver pdump** aufrufen.

### Datensicherung {#data-backup}

Bevor Sie einen Migrationsprozess starten, müssen Sie **Ihre Daten sichern.**

### Umgebung {#environment}

* Es ist nicht möglich, den Datenbankmodultyp (DBMS) zu ändern. Sie können beispielsweise nicht von einer PostgreSQL-Engine zu einer Oracle-Engine wechseln. Sie können jedoch von einem Oracle 8-Motor auf einen Oracle 10-Motor umstellen.
* Es ist nicht möglich, von einer Nicht-Unicode-Datenbank zu einer Unicode-Datenbank zu wechseln.

### Empfehlung {#recommendation}

Da das Migrationsprozess sensibel ist, empfehlen wir dringend, dieses Dokument gründlich zu lesen, bevor das Verfahren eingeleitet wird.

## Migrationsschritte {#migration-steps}

Das Migrationsverfahren muss auf **allen** Servern und in einer bestimmten Reihenfolge durchgeführt werden.

* Bei einer **eigenständigen Plattform** (Einzelmaschinenmodus) wird die Anwendung vollständig migriert.
* Bei einer **Standardplattform** (Unternehmen) gelten folgende Migrationsschritte:

   1. Migrieren des Marketing-Servers.
   1. Migrieren Sie den Mail-Server (mta).
   1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).

* Bei einer **Cloud Messaging-Plattform** werden die Ausführungsserver im Adobe Campaign gehostet. Wenden Sie sich an Adobe Campaign, um die Migration zwischen verschiedenen Servern zu koordinieren.
* Bei einer **Power-Booster- oder Power-Cluster-Plattform** sind die Migrationsschritte wie folgt:

   1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).
   1. Migrieren Sie die Power Booster/Cluster-Server.
   1. Migrieren des Marketing-Servers.

## Benutzerkennwörter {#user-passwords}

In v7 müssen die Operatorverbindungen **internal** und **admin** durch ein Kennwort gesichert werden. Es wird dringend empfohlen, diesen Konten und allen Operatorkonten vor Migration **Kennwörter zuzuweisen.** Wenn Sie kein Kennwort für **internal** angegeben haben, können Sie keine Verbindung herstellen. Um **internal** ein Kennwort zuzuweisen, geben Sie den folgenden Befehl ein:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Das **internal**-Kennwort muss für alle Tracking-Server identisch sein. Weitere Informationen finden Sie in den Abschnitten [Interne Kennung](../../installation/using/campaign-server-configuration.md#internal-identifier) und [Berechtigungen](../../platform/using/access-management.md).

