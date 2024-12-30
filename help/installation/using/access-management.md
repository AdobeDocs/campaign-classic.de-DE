---
product: campaign
title: 'Zugriffsverwaltung '
description: Weitere Informationen zu Best Practices für die Zugriffsverwaltung
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 16%

---

# Zugriffsverwaltung  {#access-management}



## WebApp-Benutzer

Standardmäßig ist der WebApp-Benutzer ein Administrator. Befolgen Sie diese Richtlinien, um die Sicherheit zu verbessern:

* Ersetzen Sie den Administrator bzw. die Administratorin mit der entsprechenden Berechtigung von diesem Benutzer bzw. dieser Benutzerin durch einen neuen (kann „Web-App“ heißen). Weitere Informationen dazu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* Fügen Sie den WebApp-Benutzer in Ordnern (hauptsächlich Empfängerordner) hinzu, um Empfängern Lese-/Schreibzugriff zu gewähren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* Bei Verwendung einer Multi-Brand-Instanz (oder Multi-Geo-Instanz) sollten Sie den Zugriff der Web-Anwendung auf verschiedene Empfängerordner aufteilen. Gehen Sie dabei folgendermaßen vor:

   1. Duplizieren des WebApp-Benutzers

   1. Geben Sie für jedes Duplikat einen Namen ein. Beispiel: webapp_brand, webapp_brand2 usw.

   1. Duplizieren Sie eine Web-Anwendungsvorlage, um eine Vorlage pro Marke zu erhalten, und bearbeiten Sie die Eigenschaften, um den Benutzer durch Auswahl von Spezifisches Konto verwenden zu ändern.  Weitere Informationen finden Sie auf [dieser Seite](../../web/using/defining-web-forms-properties.md).

## Sicherheitsgruppen und Admin-Benutzer

Erstellen Sie genügend Sicherheitsgruppen, um Ihren Benutzern gerade genug Rechte zu geben, damit sie tun können, was sie brauchen, und nicht mehr.

Verwenden Sie keinen Admin-Operator (oder geben Sie ihn nicht frei). Erstellen Sie einen Benutzer pro physischem Benutzer (für eine genaue Prüfung/Protokollierung). Fügen Sie Ihre neu benannten Administratoren zur Administratorgruppe hinzu. Wenn Sie den Administrator-Operator nicht verwenden, löschen Sie ihn nicht und deaktivieren Sie ihn nicht: Dieser Operator wird intern verwendet, um die Verarbeitung auszuführen. Sie können jedoch seinen [Zugriff auf die Client-Konsole](../../platform/using/access-management.md) verbieten und seine Sicherheitszone (auf localhost) einschränken.

Nehmen Sie nicht zu viele Benutzer in die Administrator-Gruppe auf (bzw. Benutzer mit spezifischen Administratorberechtigungen). Diese Benutzer verfügen über umfassende Rechte (sie können alle SQL-Anweisungen und Befehle auf dem Server ausführen etc.).

Adobe Campaign bietet drei allgemeine Berechtigungen über [spezifische Berechtigungen](../../platform/using/access-management.md#named-rights):

* **ADMINISTRATION** (admin): Ermöglicht Zugriff auf alle Elemente und deren Ausführung, wobei alle spezifischen Berechtigungsprüfungen umgangen werden, sodass die Berechtigung „PROGRAMMAUSFÜHRUNG“ (createProcess) und die spezifischen SQL-Berechtigungen enthalten sind

* **PROGRAM EXECUTION** (createProcess): ermöglicht das Ausführen externer Programme (auf dem Server)

* **SQL**: ermöglicht die Ausführung von SQL-Skripten in der Datenbank (sodass das Sicherheitsmodell umgangen werden kann). Hinweis: Wenn Sie komplexe Berechnungen (z. B. Filtern) durchführen müssen, können Sie den Datenbankadministrator bitten, eine SQL-Funktion zu erstellen und sie der Zulassungsliste hinzuzufügen. Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/scripting-coding-guidelines.md).

* **Gewähren Sie sie nur sehr wenigen (und vertrauenswürdigen) Benutzern**
