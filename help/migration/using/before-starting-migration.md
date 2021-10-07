---
product: campaign
title: Vor Beginn der Migration
description: Vor Beginn der Migration
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 2%

---

# Vor Beginn der Migration{#before-starting-migration}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>In diesem Dokument werden die mit der Datenbank verknüpften Befehle als Beispiel dargestellt. Diese können je nach Konfiguration variieren. Wenden Sie sich an Ihren Datenbankadministrator.

## Warnhinweise {#warnings}

* Der Migrationsprozess darf nur von erfahrenen Benutzern durchgeführt werden. Sie müssen von mindestens einem Datenbankexperten, einem Systemadministrator und einem Anwendungsentwickler von Adobe Campaign unterstützt werden.
* Bevor Sie mit der Migration beginnen, überprüfen Sie, ob die von Ihnen verwendeten Systeme und Systemkomponenten tatsächlich mit v7 kompatibel sind. Konsultieren Sie die [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md).
* Wenn Sie Adobe Campaign Cloud Messaging (Mid-Sourcing) verwenden, wenden Sie sich an Adobe , bevor Sie mit dem gesamten Migrationsverfahren beginnen.
* Bevor Sie einen Migrationsprozess starten, müssen Sie **Ihre Daten sichern.**
* Der Migrationsprozess kann mehrere Tage in Anspruch nehmen.
* Adobe Campaign v7 ist hinsichtlich der Konfiguration strenger als die Versionen 5.11 und 6.02. Dies dient hauptsächlich dazu, Probleme wie Datenbeschädigung zu vermeiden und die Datenintegrität in der Datenbank zu wahren. Folglich funktionieren bestimmte Funktionen, die in den Versionen 5.11 und v6.02 angeboten werden, möglicherweise nicht mehr in v7 und müssen daher nach der Migration möglicherweise angepasst werden. Bevor Sie etwas in die Produktionsumgebung übernehmen, sollten Sie alle Konfigurationen, insbesondere Workflows, die für die Verwendung von Adobe Campaign erforderlich sind, systematisch testen.

### Installierte Version {#installed-version}

Vor der Migration sollten Sie den neuesten Build der aktuellen Version installieren, die Sie verwenden.

Überprüfen Sie die Version auf Ihrem Server, indem Sie das Menü **[!UICONTROL Hilfe> Versionsinformationen]** in der Clientkonsole mit dem Befehl **nlserver pdump** aufrufen.

### Datensicherung {#data-backup}

Bevor Sie einen Migrationsprozess starten, müssen Sie **Ihre Daten sichern.**

### Umgebung {#environment}

* Es ist nicht möglich, den Datenbankmodultyp (DBMS) zu ändern. Sie können beispielsweise nicht von einer PostgreSQL-Engine zu einer Oracle-Engine wechseln. Sie können jedoch von einem Oracle 8-Motor auf einen Oracle 10-Motor umsteigen.
* Es ist nicht möglich, von einer Nicht-Unicode-Datenbank zu einer Unicode-Datenbank zu wechseln.

### Empfehlung {#recommendation}

Da der Migrationsprozess sensibel ist, empfehlen wir dringend, dieses Dokument gründlich zu lesen, bevor Sie den Vorgang starten.

## Migrationsschritte {#migration-steps}

Das Migrationsverfahren muss auf **allen**-Servern und in einer bestimmten Reihenfolge durchgeführt werden.

* Im Fall einer **eigenständigen Plattform** (Einzelmodus) wird die Anwendung vollständig migriert.
* Bei einer **Standardplattform** (Unternehmen) sind die Migrationsschritte wie folgt:

   1. Migrieren Sie den Marketing-Server.
   1. Migrieren Sie den Mailserver (mta).
   1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).

* Bei einer **Cloud Messaging-Plattform** werden die Ausführungsserver in Adobe Campaign gehostet. Wenden Sie sich an Adobe Campaign, um die Migration zwischen verschiedenen Servern zu koordinieren.
* Bei einer **Power Booster- oder Power Cluster-Plattform** sind die Migrationsschritte wie folgt:

   1. Migrieren Sie die Umleitungs- und Tracking-Server (Apache/IIS).
   1. Migrieren Sie die Power Booster-/Cluster-Server.
   1. Migrieren Sie den Marketing-Server.

## Benutzerkennwörter {#user-passwords}

In v7 muss die Benutzerverbindung für **internal** und **admin** durch ein Kennwort gesichert werden. Es wird dringend empfohlen, diesen Konten und allen Benutzerkonten **vor der Migration** Passwörter zuzuweisen. Wenn Sie kein Kennwort für **internal** angegeben haben, können Sie keine Verbindung herstellen. Geben Sie den folgenden Befehl ein, um **internal** ein Kennwort zuzuweisen:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Das Kennwort **internal** muss für alle Tracking-Server identisch sein. Weitere Informationen finden Sie in den Abschnitten [Interne Kennung](../../installation/using/configuring-campaign-server.md#internal-identifier) und [Berechtigungen](../../platform/using/access-management.md) .
