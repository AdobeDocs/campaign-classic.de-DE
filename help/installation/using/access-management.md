---
product: campaign
title: Zugriffsverwaltung
description: Erfahren Sie mehr über die Best Practices für die Zugriffsverwaltung
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 16%

---

# Zugriffsverwaltung  {#access-management}



## Webapp-Operator

Standardmäßig ist der WebApp-Benutzer ein Administrator. Um die Sicherheit zu verbessern, befolgen Sie die folgenden Richtlinien:

* Ersetzen Sie die spezifische Berechtigung des Administrators durch eine neue (kann &quot;webapp&quot;genannt werden). Weitere Informationen dazu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* Fügen Sie den WebApp-Operator in Ordnern (hauptsächlich Empfängerordner) hinzu, um Empfängern Lese-/Schreibzugriff zu gewähren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* Wenn Sie eine Instanz mit mehreren Marken (oder mehreren geografischen Standorten) verwenden, sollten Sie den Webanwendungszugriff auf verschiedene Empfängerordner aufteilen. Gehen Sie dabei folgendermaßen vor:

   1. Den WebApp-Operator duplizieren

   1. Geben Sie für jedes Duplikat einen Namen ein. Beispiel: webapp_brand, webapp_brand2 usw.

   1. Duplizieren Sie eine Webanwendungsvorlage, um eine Vorlage pro Marke zu haben, und bearbeiten Sie die Eigenschaften, um den Benutzer durch die Auswahl von Spezifisches Konto verwenden zu ändern.  Weitere Informationen finden Sie auf [dieser Seite](../../web/using/defining-web-forms-properties.md).

## Sicherheitsgruppen und Admin-Benutzer

Erstellen Sie genügend Sicherheitsgruppen, um Ihren Benutzern ausreichend Rechte zu gewähren, damit sie das tun können, was sie benötigen, und nicht mehr.

Verwenden Sie nicht den Administrator-Operator (oder geben Sie ihn nicht frei). Erstellen Sie einen Benutzer pro physischem Benutzer (für eine genaue Prüfung/Protokollierung). Fügen Sie Ihre neu benannten Administratoren zur Administratorgruppe hinzu. Wenn Sie den Administrator-Operator nicht verwenden, löschen Sie ihn nicht und deaktivieren Sie ihn nicht: Dieser Operator wird intern zur Ausführung der Verarbeitung verwendet. Sie können jedoch den [Zugriff auf die Clientkonsole](../../platform/using/access-management.md) verbieten und die Sicherheitszone (auf localhost) einschränken.

Nehmen Sie nicht zu viele Benutzer in die Administrator-Gruppe auf (bzw. Benutzer mit spezifischen Administratorberechtigungen). Diese Benutzer verfügen über umfassende Rechte (sie können alle SQL-Anweisungen und Befehle auf dem Server ausführen etc.).

Adobe Campaign bietet drei allgemeine Berechtigungen über [spezifische Berechtigungen](../../platform/using/access-management.md#named-rights):

* **ADMINISTRATION** (Admin): ermöglicht den Zugriff auf alles und ermöglicht die Durchführung aller Aufgaben, wobei alle benannten Berechtigungsprüfungen umgangen werden, sodass die spezifischen Berechtigungen &quot;PROGRAM EXECUTION&quot;(createProcess) und &quot;SQL&quot; enthalten sind.

* **AUSFÜHRUNG DES PROGRAMMS** (createProcess): ermöglicht die Ausführung externer Programme (auf dem Server)

* **SQL**: ermöglicht das Ausführen von SQL-Skripten in der Datenbank (sodass das Sicherheitsmodell umgangen werden kann). Hinweis: Wenn Sie komplexe Berechnungen durchführen müssen (z. B. Filtern), können Sie Ihren Datenbankadministrator bitten, eine SQL-Funktion zu erstellen und sie der Zulassungsliste hinzuzufügen. Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/scripting-coding-guidelines.md).

* **Gewähren Sie sie nur sehr wenigen (und vertrauenswürdigen) Operatoren**
