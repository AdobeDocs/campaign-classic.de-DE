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

Während der Migration wird die Variable **NmsRecipient** -Tabelle aus der Schemadefinition neu erstellt. Änderungen an der SQL-Struktur dieser Tabelle außerhalb von Adobe Campaign gehen verloren.

Zu prüfende Beispielelemente:

* Wenn Sie eine Spalte (oder einen Index) zum **NmsRecipient** -Tabelle, aber Sie haben sie nicht im Schema detailliert, wird dies nicht gespeichert.
* Die **tablespace** -Attribut nimmt standardmäßig seine Werte zurück, d. h. die im Softwareverteilungs-Assistenten definierten Werte.
* Wenn Sie der Tabelle NmsRecipient eine Referenzansicht hinzugefügt haben, müssen Sie diese vor der Migration löschen.

Diese Warnung betrifft auch Oracle-Benutzer: Wenn Sie die **usetimestamptz:1** -Option während eines Postupgrades (siehe [Zeitzonen](../../migration/using/general-configurations.md#time-zones)), alle Tabellen, die mindestens eine **Datum+Uhrzeit** -Feld neu erstellt.

## Vor der Migration {#before-the-migration}

Bei der Migration zu Adobe Campaign v7 müssen die folgenden Elemente konfiguriert werden. Diese Elemente müssen vor dem Start der **postupgrade**.

* Zeitzonen

   Bei einer Migration von einer Plattform der Version 5.11 müssen Sie die Zeitzone angeben, die während des Postupgrades verwendet werden soll.

   Wenn Sie den Modus &quot;Multi-Timezone&quot;verwenden möchten, lesen Sie den Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) Abschnitt.

   Wenn Sie Oracle als Datenbank verwenden, überprüfen Sie, ob die Oracle-Zeitzonendateien ordnungsgemäß zwischen dem Anwendungsserver und dem Datenbankserver synchronisiert wurden. Weitere Informationen hierzu finden Sie im Abschnitt [Oracle](../../migration/using/general-configurations.md#oracle) Abschnitt.

* Sicherheitszonen

   Aus Sicherheitsgründen ist die Adobe Campaign-Plattform nicht mehr standardmäßig verfügbar: Sie müssen die Sicherheitszonen konfigurieren. Dazu müssen die Benutzer-IP-Adressen vor der Migration erfasst werden.

   Weitere Informationen finden Sie im Abschnitt [Sicherheit](../../migration/using/general-configurations.md#security) Abschnitt.

* Syntax

   Bestimmte Syntaxen in JavaScript können in den Versionen 5.11 und 6.02 akzeptiert und in der Version v7 nicht mehr akzeptiert werden, da ein neuer Interpreter verwendet wird. Weitere Informationen finden Sie im Abschnitt [JavaScript](../../migration/using/general-configurations.md#javascript) Abschnitt.

   In Adobe Campaign v7 wird eine neue Syntax eingeführt, die die SQLData-basierte Syntax ersetzt. Wenn Sie Code-Elemente mit dieser Syntax verwenden, müssen Sie sie anpassen. Weitere Informationen finden Sie im Abschnitt [SQLData](../../migration/using/general-configurations.md#sqldata) Abschnitt.

* Passwörter

   Sie müssen die **Admin** und **intern** Kennwörter. Weitere Informationen finden Sie im Abschnitt [Benutzerkennwörter](../../migration/using/before-starting-migration.md#user-passwords) Abschnitt.

* Baumstruktur

   Wenn Sie von einer Plattform der Version 5.11 migrieren, müssen Sie die Baumstrukturordner gemäß den Adobe Campaign v6-Normen neu organisieren. Weitere Informationen finden Sie im Abschnitt [Baumstruktur von Adobe Campaign v7](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) Abschnitt.

* Interaction

   Wenn Sie **Interaction** müssen Sie alle 6.02 Schemareinweise löschen, die in v7 nicht mehr vorhanden sind. Weitere Informationen finden Sie im Abschnitt [Interaction](../../migration/using/general-configurations.md#interaction) Abschnitt.

## Nach der Migration {#after-the-migration}

Nach Ausführung **postupgrade** müssen die folgenden Elemente und die entsprechenden Konfigurationen berücksichtigt werden.

* Mirrorseiten

   Der Gestaltungsbaustein für die Mirrorseite wurde mit v6.x geändert. Diese neue Version verbessert die Sicherheit beim Zugriff auf diese Seiten.

   Wenn Sie den Gestaltungsbaustein v5 in Ihren Nachrichten verwendet haben, schlägt die Anzeige der Mirrorseite fehl. Adobe empfiehlt dringend, den neuen Gestaltungsbaustein beim Einfügen der Mirrorseite in Ihre Nachrichten zu verwenden.

   Als temporäre Lösung (und da die Mirrorseiten noch live sind) können Sie jedoch zum alten Gestaltungsbaustein zurückkehren, um dieses Problem zu vermeiden, indem Sie die Option ändern **[!UICONTROL XtkAcceptOldPasswords]** und legen Sie **[!UICONTROL 1]**. Dies hat keine Auswirkungen auf die Verwendung des neuen Gestaltungsbausteins v6.x.

* Syntax

   Wenn während des Postupgrades Syntaxfehler auftreten, müssen Sie die **allowSQLInjection** in der **serverConf.xml** -Datei, da Sie dadurch Zeit haben, den Code neu zu schreiben. Nachdem der Code angepasst wurde, stellen Sie sicher, dass Sie die Sicherheit reaktivieren. Weitere Informationen hierzu finden Sie im Abschnitt [SQLData](../../migration/using/general-configurations.md#sqldata) Abschnitt.

* Konflikte

   Die Migration wird durch ein Postupgrade durchgeführt und Konflikte können in Berichten, Formularen oder Webanwendungen auftreten. Diese Konflikte können über die Konsole gelöst werden.

   Siehe [Konflikte](../../migration/using/general-configurations.md#conflicts) Abschnitt.

* Tomcat

   Wenn Sie den Installationsordner angepasst haben, stellen Sie sicher, dass er nach der Migration korrekt aktualisiert wurde. Weitere Informationen finden Sie im Abschnitt [Tomcat](../../migration/using/general-configurations.md#tomcat) Abschnitt.

* Berichte

   Alle nativen Berichte verwenden derzeit die Rendering-Engine v6.x. Wenn Sie den Berichten JavaScript-Code hinzugefügt haben, können einige Elemente geändert werden.

   Lesen Sie die [Berichte](../../migration/using/general-configurations.md#reports) Abschnitt.

* Webanwendungen

   Wenn nach dem Postupgrade Probleme beim Herstellen einer Verbindung zu Ihren identifizierten Webanwendungen auftreten, müssen Sie die **allowUserPassword** und **sessionTokenOnly** Optionen in **serverConf.xml** -Datei. Denken Sie daran, diese beiden Optionen dann zu deaktivieren. Weitere Informationen finden Sie im Abschnitt [Identifizierte Webanwendungen](../../migration/using/general-configurations.md#identified-web-applications) Abschnitt.

   Abhängig vom Typ der Webanwendungen und ihrer Konfiguration müssen Sie zusätzliche Manipulationen durchführen, um sicherzustellen, dass sie ordnungsgemäß funktionieren.

   Siehe [Webanwendungen](../../migration/using/general-configurations.md#web-applications) Abschnitt.

   Bei der Migration von einer v5.11-Plattform müssen zusätzliche Konfigurationen vorgenommen werden: Weitere Informationen finden Sie im Abschnitt [Webanwendungen](../../migration/using/specific-configurations-in-v5-11.md#web-applications) Abschnitt.

* Sicherheitszonen.

   Bevor Sie den Server starten, müssen Sie die Sicherheitszonen konfigurieren. Weitere Informationen finden Sie unter [diesem Abschnitt](../../installation/using/security-zones.md) und [Sicherheit](../../migration/using/general-configurations.md#security) Abschnitt.

* Schemata

   In Red Hat können bei der Bearbeitung bestimmter Schemata Fehler auftreten. Weitere Informationen hierzu finden Sie im Abschnitt [Red-Hat](../../migration/using/general-configurations.md#red-hat) Abschnitt.

* Workflows

   Bei einer Migration von einer v5.11-Plattform müssen Sie das Laufzeitverzeichnis der Workflows steuern. Weitere Informationen hierzu finden Sie im Abschnitt [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) Abschnitt.

* Tracking

   Bei der Migration von einer v5.11-Plattform müssen Sie den Tracking-Modus konfigurieren. Weitere Informationen hierzu finden Sie im Abschnitt [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) Abschnitt.

* Startseite

   Wenn Sie von einer v6.02-Plattform migrieren, können Sie zusätzliche Parameter definieren, um Ihre alte Homepage von v6.02 zu erhalten. Weiterführende Informationen dazu finden Sie im Abschnitt [Benutzerfreundlichkeit: Startseite und Navigation](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) Abschnitt.

* Interaction

   Wenn Sie **Interaction** müssen Sie alle Parameter nach der Migration anpassen. Weitere Informationen hierzu finden Sie im Abschnitt [Interaction](../../migration/using/general-configurations.md#interaction) Abschnitt.
