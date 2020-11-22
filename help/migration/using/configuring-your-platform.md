---
solution: Campaign Classic
product: campaign
title: Konfigurieren der Plattform
description: Konfigurieren der Plattform
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 2%

---


# Konfigurieren der Plattform{#configuring-your-platform}

Bestimmte wichtige Änderungen in Adobe Campaign v7 erfordern eine Konfiguration, um den effektiven Betrieb sicherzustellen. Diese Parameter können vor oder nach der Migration benötigt werden. Die betreffenden Änderungen und ihr Konfigurationsmodus werden in diesem Abschnitt vorgestellt.

Während der Migration wird die **NmsRecipient** -Tabelle aus der Definition der Schemas neu erstellt. Änderungen an der SQL-Struktur dieser Tabelle außerhalb von Adobe Campaign gehen verloren.

Zu prüfende Beispielelemente:

* Wenn Sie eine Spalte (oder einen Index) zur **NmsRecipient** -Tabelle hinzugefügt haben, diese aber nicht im Schema detailliert angegeben haben, wird dies nicht gespeichert.
* Das Attribut **tablespace** nimmt standardmäßig seine Werte zurück, d. h. die im Bereitstellungsassistenten definierten Werte.
* Wenn Sie der NmsRecipient-Tabelle eine Referenz-Ansicht hinzugefügt haben, müssen Sie diese vor der Migration löschen.

Diese Warnung betrifft auch Oracle-Nutzer: Wenn Sie die Option **usetimestamptz:1** während einer Nachrüstung hinzugefügt haben (siehe [Zeitzonen](../../migration/using/general-configurations.md#time-zones)), werden alle Tabellen mit mindestens einem **Datums- und Uhrzeitfeld** neu erstellt.

## Vor der Migration {#before-the-migration}

Bei der Migration zu Adobe Campaign v7 müssen die folgenden Elemente konfiguriert werden. Diese Elemente müssen vor dem Start der **Nachrüstung** behoben werden.

* Zeitzonen

   Bei einer Migration von einer v5.11-Plattform müssen Sie die Zeitzone angeben, die nach der Aktualisierung verwendet werden soll.

   Wenn Sie den &quot;multi timezone&quot;-Modus verwenden möchten, lesen Sie den Abschnitt [Zeitzonen](../../migration/using/general-configurations.md#time-zones) .

   Wenn Sie Oracle als Datenbank verwenden, überprüfen Sie, ob die Oracle-Zeitzonendateien ordnungsgemäß zwischen dem Anwendungsserver und dem Datenbankserver synchronisiert wurden. For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

* Sicherheitszonen

   Aus Sicherheitsgründen ist die Adobe Campaign-Plattform standardmäßig nicht mehr verfügbar: Sie müssen die Sicherheitszonen konfigurieren. Dies erfordert die Erfassung der IP-Adressen der Benutzer vor der Migration.

   For more information, refer to the [Security](../../migration/using/general-configurations.md#security) section.

* Syntax

   Bestimmte Syntaxen in JavaScript können in den Versionen 5.11 und 6.02 akzeptiert und in der Version 7 nicht mehr akzeptiert werden, da ein neuer Interpreter verwendet wird. For more information, refer to the [JavaScript](../../migration/using/general-configurations.md#javascript) section.

   Ebenso wird in Adobe Campaign v7 eine neue Syntax eingeführt, um die SQLData-basierte Syntax zu ersetzen. Wenn Sie Codeelemente mit dieser Syntax verwenden, müssen Sie diese anpassen. For more information, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Kennwörter

   Sie müssen die **Admin** - und **internen** Kennwörter konfigurieren. For more information, refer to the [User passwords](../../migration/using/before-starting-migration.md#user-passwords) section.

* Baumstruktur

   Bei einer Migration von einer v5.11-Plattform müssen Sie die Strukturordner gemäß den Adobe Campaign v6-Normen neu organisieren. Weitere Informationen finden Sie im [Adobe Campaign v7-Strukturabschnitt](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) .

* Interaction

   Wenn Sie **Interaktion** verwenden, müssen Sie alle 6.02-Schema-Verweise löschen, die nicht mehr in v7 vorhanden sind. For more information, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

## Nach der Migration {#after-the-migration}

Nach der **Aktualisierung** müssen die folgenden Elemente berücksichtigt und die entsprechenden Konfigurationen durchgeführt werden.

* Mirrorseiten

   Der Personalisierungsblock der Mirrorseite wurde mit v6.x geändert. Diese neue Version verbessert die Sicherheit beim Zugriff auf diese Seiten.

   Wenn Sie den v5-Personalisierungsblock in Ihren Nachrichten verwendet haben, schlägt die Anzeige der Mirrorseite fehl. Adobe empfiehlt dringend, den neuen Personalisierungsblock zu verwenden, wenn Sie Mirrorseite in Ihre Nachrichten einfügen.

   Als temporäre Lösung (und da die Mirrorseiten noch live sind) können Sie jedoch zum alten Personalisierungsblock zurückkehren, um dieses Problem zu vermeiden, indem Sie die Option **[!UICONTROL XtkAcceptOldPasswords]** ändern und auf **[!UICONTROL 1]** einstellen. Dies hat keine Auswirkungen auf die Verwendung des neuen Personalisierungsblocks v6.x.

* Syntax

   Sollten Sie während der Aktualisierung auf Syntaxfehler stoßen, müssen Sie die Option **allowSQLInject** in der Datei &quot; **serverConf.xml** &quot;vorübergehend aktivieren, da Sie so Zeit zum Umschreiben des Codes haben. Nachdem der Code angepasst wurde, stellen Sie sicher, dass Sie die Sicherheit reaktivieren. For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Konflikte

   Die Migration wird nach der Aktualisierung durchgeführt und Konflikte können in Berichten, Formularen oder Webanwendungen auftreten. Diese Konflikte können über die Konsole gelöst werden.

   See the [Conflicts](../../migration/using/general-configurations.md#conflicts) section.

* Tomcat

   Wenn Sie den Installationsordner angepasst haben, überprüfen Sie, ob er nach der Migration korrekt aktualisiert wurde. Weitere Informationen finden Sie im Abschnitt [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Berichte 

   Alle vordefinierten Berichte verwenden derzeit die Rendering-Engine v6.x. Wenn Sie den Berichten JavaScript-Code hinzugefügt haben, können einige Elemente geändert werden.

   Lesen Sie den Abschnitt [Berichte](../../migration/using/general-configurations.md#reports) .

* Webanwendungen

   Wenn Sie nach der Aktualisierung Probleme bei der Verbindung mit Ihren identifizierten Webanwendungen haben, müssen Sie die Optionen **allowUserPassword** und **sessionTokenOnly** in der Datei **serverConf.xml** aktivieren. Denken Sie daran, diese beiden Optionen zu deaktivieren. Weitere Informationen finden Sie im Abschnitt [Identifizierte Webanwendungen](../../migration/using/general-configurations.md#identified-web-applications) .

   Abhängig vom Typ der Webanwendungen und ihrer Konfiguration müssen Sie zusätzliche Manipulationen durchführen, um sicherzustellen, dass sie ordnungsgemäß funktionieren.

   Siehe Abschnitt [Webanwendungen](../../migration/using/general-configurations.md#web-applications) .

   Bei Migration von einer v5.11-Plattform müssen zusätzliche Konfigurationen durchgeführt werden: Weitere Informationen finden Sie im Abschnitt [Webanwendungen](../../migration/using/specific-configurations-in-v5-11.md#web-applications) .

* Sicherheitszonen.

   Bevor Sie den Server starten, müssen Sie die Sicherheitszonen konfigurieren. Weitere Informationen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#defining-security-zones) und im Abschnitt [Sicherheit](../../migration/using/general-configurations.md#security) .

* Schemata

   In Red Hat treten möglicherweise Fehler auf, wenn Sie bestimmte Schema bearbeiten. For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* Workflows

   Bei einer Migration von einer v5.11-Plattform müssen Sie den Workflows-Laufzeitordner steuern. For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* Tracking

   Bei der Migration von einer v5.11-Plattform müssen Sie den Verfolgungsmodus konfigurieren. For more on this, refer to the [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) section.

* Startseite        

   Wenn Sie von einer v6.02-Plattform migrieren, können Sie zusätzliche Parameter definieren, um Ihre alte Startseite von v6.02 zu erhalten. Weitere Informationen finden Sie unter [Benutzerfreundlichkeit: Startseite und Navigation](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) .

* Interaction

   Wenn Sie **Interaktion** verwenden, müssen Sie nach der Migration alle Parameter anpassen. For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

