---
product: campaign
title: Konfigurieren der Plattform
description: Konfigurieren der Plattform
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 2%

---

# Konfigurieren der Plattform{#configuring-your-platform}

![](../../assets/v7-only.svg)

Bestimmte wichtige Änderungen in Adobe Campaign v7 erfordern eine Konfiguration, um den effektiven Betrieb sicherzustellen. Diese Parameter können vor oder nach der Migration erforderlich sein. Die betroffenen Änderungen und ihr Konfigurationsmodus werden in diesem Abschnitt beschrieben.

Während der Migration wird die Tabelle **NmsRecipient** aus der Schemadefinition neu erstellt. Änderungen an der SQL-Struktur dieser Tabelle außerhalb von Adobe Campaign gehen verloren.

Zu prüfende Beispielelemente:

* Wenn Sie der Tabelle **NmsRecipient** eine Spalte (oder einen Index) hinzugefügt haben, diese jedoch nicht im Schema detailliert beschrieben haben, wird dies nicht gespeichert.
* Das Attribut **tablespace** nimmt standardmäßig die im Softwareverteilungs-Assistenten definierten Werte zurück.
* Wenn Sie der Tabelle NmsRecipient eine Referenzansicht hinzugefügt haben, müssen Sie diese vor der Migration löschen.

Diese Warnung betrifft auch Oracle-Benutzer: Wenn Sie die Option **usetimestamptz:1** während eines Postupgrades hinzugefügt haben (siehe [Zeitzonen](../../migration/using/general-configurations.md#time-zones)), werden alle Tabellen, die mindestens ein **Datum+Uhrzeit**-Feld enthalten, neu erstellt.

## Vor der Migration {#before-the-migration}

Bei der Migration zu Adobe Campaign v7 müssen die folgenden Elemente konfiguriert werden. Diese Elemente müssen vor dem Starten von **postupgrade** adressiert werden.

* Zeitzonen

   Bei einer Migration von einer Plattform der Version 5.11 müssen Sie die Zeitzone angeben, die während des Postupgrades verwendet werden soll.

   Wenn Sie den Modus &quot;Multi-Timezone&quot;verwenden möchten, lesen Sie den Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) .

   Wenn Sie Oracle als Datenbank verwenden, überprüfen Sie, ob die Oracle-Zeitzonendateien ordnungsgemäß zwischen dem Anwendungsserver und dem Datenbankserver synchronisiert wurden. Weitere Informationen hierzu finden Sie im Abschnitt [Oracle](../../migration/using/general-configurations.md#oracle) .

* Sicherheitszonen

   Aus Sicherheitsgründen ist die Adobe Campaign-Plattform nicht mehr standardmäßig verfügbar: Sie müssen die Sicherheitszonen konfigurieren. Dazu müssen die Benutzer-IP-Adressen vor der Migration erfasst werden.

   Weitere Informationen finden Sie im Abschnitt [Sicherheit](../../migration/using/general-configurations.md#security) .

* Syntax

   Bestimmte Syntaxen in JavaScript können in den Versionen 5.11 und 6.02 akzeptiert und in der Version v7 nicht mehr akzeptiert werden, da ein neuer Interpreter verwendet wird. Weitere Informationen finden Sie im Abschnitt [JavaScript](../../migration/using/general-configurations.md#javascript) .

   In Adobe Campaign v7 wird eine neue Syntax eingeführt, die die SQLData-basierte Syntax ersetzt. Wenn Sie Code-Elemente mit dieser Syntax verwenden, müssen Sie sie anpassen. Weitere Informationen finden Sie im Abschnitt [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Passwörter

   Sie müssen die Kennwörter **Admin** und **Interne** konfigurieren. Weitere Informationen finden Sie im Abschnitt [Benutzerkennwörter](../../migration/using/before-starting-migration.md#user-passwords) .

* Baumstruktur

   Wenn Sie von einer Plattform der Version 5.11 migrieren, müssen Sie die Baumstrukturordner gemäß den Adobe Campaign v6-Normen neu organisieren. Weitere Informationen finden Sie im Abschnitt [Adobe Campaign v7-Baumstruktur](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) .

* Interaction

   Wenn Sie **Interaction** verwenden, müssen Sie alle 6.02 Schemareverweise löschen, die in v7 nicht mehr vorhanden sind. Weiterführende Informationen finden Sie im Abschnitt [Interaction](../../migration/using/general-configurations.md#interaction) .

## Nach der Migration {#after-the-migration}

Nach Ausführung von **postupgrade** müssen die folgenden Elemente berücksichtigt und die entsprechenden Konfigurationen durchgeführt werden.

* Mirrorseiten

   Der Gestaltungsbaustein für die Mirrorseite wurde mit v6.x geändert. Diese neue Version verbessert die Sicherheit beim Zugriff auf diese Seiten.

   Wenn Sie den Gestaltungsbaustein v5 in Ihren Nachrichten verwendet haben, schlägt die Anzeige der Mirrorseite fehl. Adobe empfiehlt dringend, den neuen Gestaltungsbaustein beim Einfügen der Mirrorseite in Ihre Nachrichten zu verwenden.

   Als temporäre Lösung (und da die Mirrorseiten noch live sind) können Sie jedoch zum alten Gestaltungsbaustein zurückkehren, um dieses Problem zu vermeiden, indem Sie die Option **[!UICONTROL XtkAcceptOldPasswords]** ändern und auf **[!UICONTROL 1]** festlegen. Dies hat keine Auswirkungen auf die Verwendung des neuen Gestaltungsbausteins v6.x.

* Syntax

   Wenn während des Postupgrades Syntaxfehler auftreten, müssen Sie die Option **allowSQLInjection** in der Datei **serverConf.xml** vorübergehend aktivieren, da Ihnen dadurch Zeit zum Neuschreiben des Codes gegeben wird. Nachdem der Code angepasst wurde, stellen Sie sicher, dass Sie die Sicherheit reaktivieren. Weitere Informationen hierzu finden Sie im Abschnitt [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Konflikte

   Die Migration wird durch ein Postupgrade durchgeführt und Konflikte können in Berichten, Formularen oder Webanwendungen auftreten. Diese Konflikte können über die Konsole gelöst werden.

   Siehe Abschnitt [Konflikte](../../migration/using/general-configurations.md#conflicts) .

* Tomcat

   Wenn Sie den Installationsordner angepasst haben, stellen Sie sicher, dass er nach der Migration korrekt aktualisiert wurde. Weitere Informationen finden Sie im Abschnitt [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Berichte

   Alle nativen Berichte verwenden derzeit die Rendering-Engine v6.x. Wenn Sie den Berichten JavaScript-Code hinzugefügt haben, können einige Elemente geändert werden.

   Lesen Sie diesbezüglich auch den Abschnitt [Berichte](../../migration/using/general-configurations.md#reports) .

* Webanwendungen

   Wenn nach dem Postupgrade Probleme beim Herstellen einer Verbindung zu Ihren identifizierten Webanwendungen auftreten, müssen Sie die Optionen **allowUserPassword** und **sessionTokenOnly** in der Datei **serverConf.xml** aktivieren. Denken Sie daran, diese beiden Optionen dann zu deaktivieren. Weitere Informationen finden Sie im Abschnitt [Identifizierte Webanwendungen](../../migration/using/general-configurations.md#identified-web-applications) .

   Abhängig vom Typ der Webanwendungen und ihrer Konfiguration müssen Sie zusätzliche Manipulationen durchführen, um sicherzustellen, dass sie ordnungsgemäß funktionieren.

   Siehe Abschnitt [Webanwendungen](../../migration/using/general-configurations.md#web-applications) .

   Bei der Migration von einer v5.11-Plattform müssen zusätzliche Konfigurationen vorgenommen werden: Weitere Informationen finden Sie im Abschnitt [Webanwendungen](../../migration/using/specific-configurations-in-v5-11.md#web-applications) .

* Sicherheitszonen.

   Bevor Sie den Server starten, müssen Sie die Sicherheitszonen konfigurieren. Weitere Informationen finden Sie in [diesem Abschnitt](../../installation/using/security-zones.md) und im Abschnitt [Sicherheit](../../migration/using/general-configurations.md#security) .

* Schemata

   In Red Hat können bei der Bearbeitung bestimmter Schemata Fehler auftreten. Weitere Informationen hierzu finden Sie im Abschnitt [Red-Hat](../../migration/using/general-configurations.md#red-hat) .

* Workflows

   Bei einer Migration von einer v5.11-Plattform müssen Sie das Laufzeitverzeichnis der Workflows steuern. Weitere Informationen hierzu finden Sie im Abschnitt [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) .

* Tracking

   Bei der Migration von einer v5.11-Plattform müssen Sie den Tracking-Modus konfigurieren. Weitere Informationen hierzu finden Sie im Abschnitt [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) .

* Startseite

   Wenn Sie von einer v6.02-Plattform migrieren, können Sie zusätzliche Parameter definieren, um Ihre alte Homepage von v6.02 zu erhalten. Weiterführende Informationen dazu finden Sie im Abschnitt [Benutzerfreundlichkeit: Startseite und Navigation](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interaction

   Wenn Sie **Interaction** verwenden, müssen Sie alle Parameter nach der Migration anpassen. Weitere Informationen hierzu finden Sie im Abschnitt [Interaction](../../migration/using/general-configurations.md#interaction) .
