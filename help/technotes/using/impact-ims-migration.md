---
title: Aktualisieren der Campaign-Benutzeroberfläche nach IMS-Migration
description: Informationen zur Aktivierung der Auswirkungen der Adobe Identity Management System-Migration auf die Benutzeroberfläche
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 100%

---

# Aktualisieren der Campaign-Benutzeroberfläche nach IMS-Migration {#impact-ims-migration}

Nachdem Sie [Ihre technischen Campaign- Benutzenden in die Developer Console migriert](ims-migration.md) und [auf IMS für die Endbenutzer-Authentifizierung](migrate-users-to-ims.md) umgestellt haben, besteht der letzte Schritt darin, die Benutzeroberfläche und die API-Einschränkungen zu aktivieren, um Optionen und Fähigkeiten zu entfernen, die für die native Authentifizierung spezifisch sind. Dieses Update ist ab Campaign v7.4.1 verfügbar.

## Aktivieren von IMS-Einschränkungen {#ims-restrictions}

Um Ihre Migration zum Adobe Identify Management System (IMS) abzuschließen, müssen Sie die Erstellung neuer nativer Benutzender, die Anmeldung nativer Benutzender und den API-Zugriff für native Benutzende blockieren. Ihre Umgebung ist dann gesichert und standardisiert.

Benutzende von Managed Cloud Services und gehostete Benutzende sollten sich an Adobe wenden, um diese Einschränkung und die damit verbundenen Updates in der Benutzeroberfläche des Produkts aktivieren zu lassen.

On-Premise-/Hybrid-Benutzende müssen die folgenden Schritte ausführen:

1. Navigieren Sie zum Abschnitt `<imsConfig>` Ihrer Instanzkonfigurationsdatei.
1. Um die UI-Einschränkungen zu aktivieren, aktualisieren Sie die Option `nonIMSOperatorMgmtInClientConsoleRestricted` innerhalb des Elements `nonIMSOperatorMgmtInClientConsole` zu `true`, wie unten dargestellt:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Um die API-Einschränkungen zu aktivieren, aktualisieren Sie die Option `disableAPI` innerhalb des Elements `nonIMSAuthnAPI` zu `true`, wie unten dargestellt:

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

Beachten Sie, dass einige Benutzende mit einer nativen Authentifizierung eine Verbindung zu Adobe Campaign herstellen dürfen. Diese technischen Benutzenden sind standardmäßig aktiviert und dürfen nicht geändert werden. Um diese Ausnahme zu ermöglichen, werden diese technischen Benutzenden standardmäßig der Zulassungsliste hinzugefügt. Sie finden diese Liste im Abschnitt `<imsConfig>` Ihrer Instanzkonfigurationsdatei unter der Option `allowOperator` innerhalb des Elements `nonIMSAuthnAPI`.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

Wenn Sie neue Benutzende zur Zulassungsliste hinzufügen müssen, fügen Sie ein neues `allowOperator`-Element mit dem Namen der Person hinzu. Wenn Sie beispielsweise neue Benutzende mit dem Namen `test` hinzufügen möchten, aktualisieren Sie diesen Abschnitt wie folgt:

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## Auswirkungen auf die Benutzeroberfläche {#ims-impacts}

Sobald die Migration abgeschlossen und die Einschränkungen wie unten beschrieben angewendet wurden, werden die im Folgenden aufgeführten Änderungen auf das Produkt und seine Benutzeroberfläche angewendet.

### Benutzerverwaltung {#manage-admin}

Sie können Benutzende mit nativer Authentifizierung nicht mehr über die Client-Konsole erstellen, bearbeiten, aktualisieren oder löschen.

Daher wurden diese Aktionen in der Client-Konsole deaktiviert.

Die Administration der Benutzenden erfolgt zentral in der Adobe Admin Console. Die folgenden Aufgaben werden nun ausschließlich über diese Konsole verwaltet. In der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/manage-permissions) erfahren Sie, wie Sie Benutzende erstellen und Berechtigungen erteilen{target="_blank"}.

### Nicht verfügbare Optionen {#unavailable-migration}

Nach der Migration sind die folgenden Aufgaben nicht mehr in der Client-Konsole verfügbar:

* Verwenden Sie die [Option „Ausgewählte Zeilen zusammenführen“](../../platform/using/updating-data.md#merge-data), um Benutzende zusammenzuführen.

* Aktualisieren Sie die folgenden Felder für Ihre Benutzenden:
   * Name
   * Passwort
   * Titel
   * E-Mail

* [Zurücksetzen des Campaign-Passworts](../../production/using/lost-password.md)

* Bearbeiten der XML-Quelle der Benutzenden

* Duplizieren von Benutzenden.


>[!MORELIKETHIS]
>
>* [Migration von Endbenutzenden zu IMS](migrate-users-to-ims.md)
>* [Migration von technischen Benutzenden zur Adobe Developer Console](ims-migration.md)
>* [Neueste Versionshinweise zu Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Was ist das Adobe Identity Management System (IMS)?](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}
