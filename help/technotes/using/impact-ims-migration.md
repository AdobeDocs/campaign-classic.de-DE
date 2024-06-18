---
title: Campaign-Benutzeroberfläche nach IMS-Migration aktualisieren
description: Erfahren Sie, wie sich die Adobe Identity Management-Systemmigration auf die Benutzeroberfläche auswirkt.
source-git-commit: ab1bb91bdbc9961b4f3f0feba7cfd354b02b6511
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 4%

---

# Campaign-Benutzeroberfläche nach IMS-Migration aktualisieren {#impact-ims-migration}

Einmal [die technischen Campaign-Benutzer in die Developer Console migriert haben](ims-migration.md) und [zur Authentifizierung des Endbenutzers auf IMS umgestellt](migrate-users-to-ims.md), besteht der letzte Schritt darin, die Benutzeroberfläche und API-Beschränkungen zu aktivieren, um Optionen und Funktionen zu entfernen, die für die native Authentifizierung spezifisch sind. Dieses Update ist ab Campaign v7.4.1 verfügbar.

## IMS-Einschränkungen aktivieren {#ims-restrictions}

Um Ihre Migration zum Adobe Identify Management System (IMS) abzuschließen, müssen Sie die Erstellung neuer nativer Benutzer, die Anmeldung nativer Benutzer und den API-Zugriff für native Benutzer blockieren. Ihre Umgebung ist dann gesichert und standardisiert.

Wenden Sie sich als verwalteter/gehosteter Cloud Service an Adobe, um diese Einschränkung und die damit verbundenen Updates in der Benutzeroberfläche des Produkts zu aktivieren.

Führen Sie als On-Premise-/Hybrid-Benutzer die folgenden Schritte aus:

1. Navigieren Sie zum `<imsConfig>` -Abschnitt Ihrer Instanzkonfigurationsdatei.
1. Um die UI-Einschränkungen zu aktivieren, aktualisieren Sie die `nonIMSOperatorMgmtInClientConsoleRestricted` -Option innerhalb der `nonIMSOperatorMgmtInClientConsole` -Element zu `true`, wie unten dargestellt:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Um die API-Einschränkungen zu aktivieren, aktualisieren Sie die `disableAPI` -Option innerhalb der `nonIMSAuthnAPI` -Element zu `true`, wie unten dargestellt:

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

Beachten Sie, dass einige Benutzer mit einer nativen Authentifizierung eine Verbindung zu Adobe Campaign herstellen dürfen. Diese technischen Operatoren sind standardmäßig aktiviert und dürfen nicht geändert werden. Um diese Ausnahme zu ermöglichen, werden diese technischen Operatoren standardmäßig der Zulassungsliste hinzugefügt. Sie finden diese Liste im `<imsConfig>` Abschnitt Ihrer Instanzkonfigurationsdatei im `allowOperator` -Option innerhalb der `nonIMSAuthnAPI` -Element.

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

Wenn Sie einen Operator zur Zulassungsliste hinzufügen müssen, fügen Sie einen neuen hinzu `allowOperator` -Element mit dem Namen des Benutzers. Wenn Sie beispielsweise einen neuen Operator mit dem Namen hinzufügen möchten `test`aktualisieren Sie diesen Abschnitt wie folgt:

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

Sobald die Migration abgeschlossen und die Einschränkungen wie unten beschrieben angewendet wurden, werden die folgenden Änderungen auf das Produkt und seine Benutzeroberfläche angewendet.

### Benutzerverwaltung {#manage-admin}

Sie können Operatoren mit nativer Authentifizierung nicht mehr über die Clientkonsole erstellen, bearbeiten, aktualisieren oder löschen.

Daher wurden diese Aktionen in der Clientkonsole deaktiviert.

Die Verwaltung der Benutzer erfolgt zentral in der Adobe Admin Console. Die folgenden Aufgaben werden nun ausschließlich über diese Konsole verwaltet. Erfahren Sie, wie Sie Benutzer erstellen und Berechtigungen zuweisen in [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Nicht verfügbare Optionen {#unavailable-migration}

Nach der Migration sind die folgenden Aufgaben nicht mehr in der Clientkonsole verfügbar:

* Verwenden Sie die [Option &quot;Ausgewählte Zeilen zusammenführen&quot;](../../platform/using/updating-data.md#merge-data) , um Operatoren zusammenzuführen.

* Aktualisieren Sie die folgenden Felder für Ihre Benutzer:
   * Name
   * Passwort
   * Titel
   * E-Mail

* [Campaign-Kennwort zurücksetzen](../../production/using/lost-password.md)

* XML-Quelle der Operatoren bearbeiten

* Duplizieren Sie Operatoren.


>[!MORELIKETHIS]
>
>* [Migration von Endbenutzern zu IMS](migrate-users-to-ims.md)
>* [Migration technischer Benutzer zur Adobe Developer-Konsole](ims-migration.md)
>* [Versionshinweise zu Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Was ist das Adobe Identity Management System (IMS)?](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"}

