---
solution: Campaign Classic
product: campaign
title: Zugriffsverwaltung
description: Weitere Informationen zu Best Practices für das Zugriffsmanagement.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 31%

---


# Zugriffsverwaltung {#access-management}

## Webapp-Operator

Standardmäßig ist der WebApp-Operator ein Administrator. Um die Sicherheit zu verbessern, befolgen Sie folgende Richtlinien:

* Ersetzen Sie den Administrator, der direkt über diesen Operator benannt wurde, durch einen neuen Operator (kann als &quot;webapp&quot;bezeichnet werden). Weitere Informationen dazu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* hinzufügen Sie den WebApp-Operator in Ordnern (hauptsächlich Empfänger-Ordnern), um Empfängern Lese-/Schreibzugriff zu gewähren. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../platform/using/access-management.md).

* Wenn Sie in einer Instanz mehrere Marken (oder mehrere regionale Standorte) verwalten, ist es empfehlenswert, die WebApp-Zugriffsberechtigung auf verschiedene Empfängerordner aufzuteilen. Gehen Sie dabei folgendermaßen vor:

   1. Duplikat des WebApp-Operators

   1. Geben Sie für jedes Duplikat einen Namen ein. Beispiel: webapp_brand, webapp_brand2 usw.

   1. Duplikat einer Webanwendungsvorlage auf eine Vorlage pro Marke und bearbeiten Sie die Eigenschaften, um den Operator durch Auswahl von Verwenden Sie ein bestimmtes Konto zu ändern.  Weiterführende Informationen finden Sie auf [dieser Seite](../../web/using/defining-web-forms-properties.md).

## Sicherheitsgruppen und Administratoren

Erstellen Sie genügend Sicherheitsgruppen, um Ihren Betreibern ausreichend Rechte einzuräumen, damit sie das tun können, was sie brauchen, und nicht mehr.

Verwenden Sie nicht den Admin-Operator (oder geben Sie ihn nicht frei). Erstellen Sie einen Operator pro physischen Benutzer (für eine genaue Prüfung/Protokollierung). hinzufügen Sie die neu benannten Administratoren zur Administratorgruppe. Wenn Sie den Administrator-Operator nicht verwenden, löschen Sie ihn nicht und deaktivieren Sie ihn nicht: dieser Operator wird intern zum Ausführen der Verarbeitung verwendet. Sie können jedoch den Zugriff auf die Client-Konsole [und deren Sicherheitszone (auf localhost) verbieten.](../../platform/using/access-management.md)

Nehmen Sie nicht zu viele Benutzer in die Administrator-Gruppe auf (bzw. Benutzer mit spezifischen Administratorberechtigungen). Diese Benutzer verfügen über umfassende Rechte (sie können alle SQL-Anweisungen und Befehle auf dem Server ausführen etc.).

Adobe Campaign bietet über [Spezifische Berechtigungen](../../platform/using/access-management.md#named-rights) drei hochrangige Berechtigungen:

* **ADMINISTRATION**  (Admin): ermöglicht den Zugriff auf alles und erlaubt, alles zu tun, wobei alle benannten richtigen Prüfungen umgangen werden, sodass das PROGRAMM EXECUTION (createProcess) und SQL-Spezifische Berechtigungen enthalten sind

* **Programm EXECUTION** (createProcess): ermöglicht die Ausführung externer Programm (auf dem Server)

* **SQL**: erlaubt die Ausführung von SQL-Skripten in der Datenbank (sodass es das Sicherheitsmodell umgehen kann). Hinweis: Wenn Sie komplexe Berechnungen durchführen müssen (z. B. Filtern), können Sie Ihren Datenbankadministrator ersuchen, eine SQL-Funktion zu erstellen und sie auf die Zulassungsliste zu setzen. Weiterführende Informationen finden Sie auf [dieser Seite](../../installation/using/scripting-coding-guidelines.md).

* **Gewähren Sie diese Privilegien nur sehr wenigen (und vertrauenswürdigen) Benutzern.**
