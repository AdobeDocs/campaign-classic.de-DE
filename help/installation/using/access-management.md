---
product: campaign
title: 'Zugriffsverwaltung '
description: Weitere Informationen zu Best Practices bei der Zugriffsverwaltung
feature: Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 23%

---

# Zugriffsverwaltung  {#access-management}

![](../../assets/v7-only.svg)

## Webapp-Operator

Standardmäßig ist der WebApp-Benutzer ein Administrator. Um die Sicherheit zu verbessern, befolgen Sie die folgenden Richtlinien:

* Ersetzen Sie die spezifische Berechtigung des Administrators durch eine neue (kann &quot;webapp&quot;genannt werden). Weitere Informationen dazu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* Fügen Sie den WebApp-Operator in Ordnern (hauptsächlich Empfängerordner) hinzu, um Empfängern Lese-/Schreibzugriff zu gewähren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* Wenn Sie in einer Instanz mehrere Marken (oder mehrere regionale Standorte) verwalten, ist es empfehlenswert, die WebApp-Zugriffsberechtigung auf verschiedene Empfängerordner aufzuteilen. Gehen Sie dabei folgendermaßen vor:

   1. Den WebApp-Operator duplizieren

   1. Geben Sie für jedes Duplikat einen Namen ein. Beispiel: webapp_brand, webapp_brand2 usw.

   1. Duplizieren Sie eine Webanwendungsvorlage, um eine Vorlage pro Marke zu haben, und bearbeiten Sie die Eigenschaften, um den Benutzer durch die Auswahl von Spezifisches Konto verwenden zu ändern.  Weiterführende Informationen finden Sie auf [dieser Seite](../../web/using/defining-web-forms-properties.md).

## Sicherheitsgruppen und Admin-Benutzer

Erstellen Sie genügend Sicherheitsgruppen, um Ihren Benutzern ausreichend Rechte zu gewähren, damit sie das tun können, was sie benötigen, und nicht mehr.

Verwenden Sie nicht den Administrator-Operator (oder geben Sie ihn nicht frei). Erstellen Sie einen Benutzer pro physischem Benutzer (für eine genaue Prüfung/Protokollierung). Fügen Sie Ihre neu benannten Administratoren zur Administratorgruppe hinzu. Wenn Sie den Admin-Operator nicht verwenden, löschen Sie ihn nicht und deaktivieren Sie ihn nicht: Dieser Operator wird intern zum Ausführen der Verarbeitung verwendet. Aber man kann seine [Zugriff auf die Clientkonsole](../../platform/using/access-management.md) und beschränken Sie die Sicherheitszone (auf localhost).

Nehmen Sie nicht zu viele Benutzer in die Administrator-Gruppe auf (bzw. Benutzer mit spezifischen Administratorberechtigungen). Diese Benutzer verfügen über umfassende Rechte (sie können alle SQL-Anweisungen und Befehle auf dem Server ausführen etc.).

Adobe Campaign bietet drei allgemeine Berechtigungen durch [spezifische Berechtigungen](../../platform/using/access-management.md#named-rights):

* **VERWALTUNG** (admin): gibt Zugriff auf alles und ermöglicht die Durchführung aller Aufgaben, wobei alle benannten Rechtsprüfungen umgangen werden, sodass es die spezifischen Berechtigungen &quot;PROGRAM EXECUTION&quot;(createProcess) und &quot;SQL&quot; enthält

* **AUSFÜHRUNG DES PROGRAMMS** (createProcess): ermöglicht die Ausführung externer Programme (auf dem Server).

* **SQL**: ermöglicht das Ausführen von SQL-Skripten in der Datenbank (sodass es das Sicherheitsmodell umgehen kann). Hinweis: Wenn Sie komplexe Berechnungen durchführen müssen (z. B. Filtern), können Sie Ihren Datenbankadministrator bitten, eine SQL-Funktion zu erstellen und sie der Zulassungsliste hinzuzufügen. Weiterführende Informationen finden Sie auf [dieser Seite](../../installation/using/scripting-coding-guidelines.md).

* **Gewähren Sie diese Privilegien nur sehr wenigen (und vertrauenswürdigen) Benutzern.**
