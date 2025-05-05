---
product: campaign
title: Allgemeine Konfigurationen
description: Allgemeine Konfigurationen
feature: Upgrade
audience: migration
content-type: reference
topic-tags: configuration
hide: true
hidefromtoc: true
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
source-git-commit: 349c3dfd936527e50d7d3e03aa3408b395502da0
workflow-type: tm+mt
source-wordcount: '2612'
ht-degree: 3%

---

# Allgemeine Konfigurationen{#general-configurations}

In diesem Abschnitt wird die Konfiguration beschrieben, die in Adobe Campaign v7 bei der Migration von einer Version 5.11 oder 6.02 durchgeführt werden soll.

Achten Sie außerdem auf Folgendes:

* Wenn Sie von Version 5.11 migrieren, müssen Sie auch die in [ Abschnitt beschriebene Konfiguration ](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* Wenn Sie von v6.02 migrieren, müssen Sie auch die Konfiguration abschließen, die in [diesem Abschnitt) beschrieben ](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## Zeitzonen {#time-zones}

### Multi-Zeitzonen-Modus {#multi-time-zone-mode}

In Version 6.02 war der Modus „Multi Time Zone“ nur für PostgreSQL-Datenbank-Engines verfügbar. Es wird nun unabhängig davon angeboten, welcher Datenbankmodultyp verwendet wird. Es wird dringend empfohlen, Ihre Datenbank in eine „Multi-Timezone“-Basis umzuwandeln.

Um den Modus ZEITSTEMPEL MIT ZEITZONE zu verwenden, müssen Sie auch die Option **-userTimestamptz:1** zur Befehlszeile für das Postupgrade hinzufügen.

>[!IMPORTANT]
>
>Wenn der Parameter **-usetimestamptz:1** mit einer inkompatiblen Datenbank-Engine verwendet wird, ist Ihre Datenbank beschädigt und Sie müssen eine Sicherung Ihrer Datenbank wiederherstellen und den obigen Befehl erneut ausführen.

>[!NOTE]
>
>Die Zeitzone kann nach der Migration über die Konsole geändert werden (Knoten **[!UICONTROL Administration > Plattform > Optionen > WdbcTimeZone]**).
>
>Weiterführende Informationen zur Zeitzonenverwaltung finden Sie [diesem Abschnitt](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

Wenn beim Postupgrade ein **ORA 01805**-Fehler auftritt, bedeutet dies, dass die Oracle-Zeitzonendateien zwischen dem Anwendungsserver und dem Datenbankserver nicht synchron sind. Gehen Sie wie folgt vor, um sie erneut zu synchronisieren:

1. Führen Sie den folgenden Befehl aus, um die verwendete Zeitzonendatei zu identifizieren:

   ```
   select * from v$timezone_file
   ```

   Zeitzonendateien befinden sich in der Regel im Ordner **ORACLE_HOME/oracore/zoneinfo/**.

1. Stellen Sie sicher, dass die Zeitzonendateien auf beiden Servern identisch sind.

Weitere Informationen finden Sie unter: [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

Eine Fehlausrichtung der Zeitzone zwischen Client und Server kann ebenfalls zu Verzögerungen führen. Daher empfehlen wir, dieselbe Version der Oracle-Bibliothek Client- und serverseitig zu verwenden. Beide Zeitzonen müssen identisch sein.

So überprüfen Sie, ob sich beide Seiten in denselben Zeitzonen befinden:

1. Überprüfen Sie Client-seitig die Version der Zeitzonendatei, indem Sie den folgenden Befehl ausführen:

   ```
   genezi -v
   ```

   genezi ist eine Binärdatei, die im Repository **$ORACLE_HOME/bin** gefunden wird.

1. Überprüfen Sie die Version der Zeitzonendatei auf der Serverseite, indem Sie den folgenden Befehl ausführen:

   ```
   select * from v$timezone_file
   ```

1. Um die Zeitzonendatei auf Client-Seite zu ändern, verwenden Sie die Umgebungsvariable **ORA_TZFILE**.

## Sicherheit {#security}

### Sicherheitszonen {#security-zones}

>[!IMPORTANT]
>
>Aus Sicherheitsgründen ist die Adobe Campaign-Plattform nicht mehr standardmäßig zugänglich: Sie müssen die Sicherheitszonen konfigurieren und daher IP-Adressen der Benutzer erfassen.

Adobe Campaign v7 beinhaltet das Konzept **Sicherheitszonen**. Jeder Benutzer muss einer Zone zugeordnet sein, um sich bei einer Instanz anmelden zu können, und die IP-Adresse des Benutzers muss in die Adressen oder Adressbereiche aufgenommen werden, die in der Sicherheitszone definiert sind. Die Konfiguration der Sicherheitszonen kann in der Konfigurationsdatei des Adobe Campaign-Servers vorgenommen werden. Die Sicherheitszone, mit der ein Benutzer verknüpft ist, muss in der Konsole definiert werden **[!UICONTROL Administration > Zugriffsverwaltung > Benutzer]**.

**Wenden Sie sich vor** Migration an Ihren Netzwerkadministrator, damit dieser Ihnen bei der Definition der Sicherheitszonen hilft, die nach der Migration aktiviert werden sollen.

**Nach dem Postupgrade** (vor dem Neustart des Servers) müssen Sie die Sicherheitszonen konfigurieren.

Die Konfiguration der Sicherheitszone finden Sie [diesem Abschnitt](../../installation/using/security-zones.md).

### Benutzerkennwörter {#user-passwords}

In v7 **die Benutzerverbindung** intern **und admin** durch ein Passwort gesichert werden. Es wird dringend empfohlen, diesen Konten und allen Benutzerkonten (vor **) Kennwörter**. Wenn Sie kein Kennwort für **intern** angegeben haben, können Sie keine Verbindung herstellen. Geben Sie den folgenden Befehl ein, um **internal** ein Kennwort zuzuweisen:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Das **interne** Kennwort muss für alle Tracking-Server identisch sein. Weitere Informationen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier) und [diesem Abschnitt](../../platform/using/access-management.md).

### Neue Funktionen in v7 {#new-features-in-v7}

* Benutzende ohne -Berechtigungen können keine Verbindung mehr zu Adobe Campaign herstellen. Ihre Berechtigungen müssen manuell hinzugefügt werden, z. B. durch Erstellen einer Berechtigung namens **CONNECT**.

  Die von dieser Änderung betroffenen Benutzer werden während des Postupgrades identifiziert und aufgelistet.

* Das Tracking funktioniert nicht mehr, wenn das Kennwort leer ist. In diesem Fall werden Sie über eine Fehlermeldung informiert und aufgefordert, die Konfiguration neu zu konfigurieren.
* Benutzerkennwörter werden nicht mehr im Schema &quot;**:sessionInfo** gespeichert.
* Für die Verwendung der Funktionen **`xtk:builder:EvaluateJavaScript`** und **`xtk:builder:EvaluateJavaScriptTemplate`** sind jetzt Administratorberechtigungen erforderlich.

Bestimmte vordefinierte Schemata wurden geändert und sind jetzt standardmäßig nur mit Schreibzugriff für Benutzer mit der Berechtigung **admin** zugänglich:

* ncm:publishing
* nl:monitoring
* nms:calendar
* xtk:builder
* xtk:connections
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

### SessionToken-Parameter {#sessiontoken-parameter}

In v5 funktionierte der **sessiontoken**-Parameter sowohl Client-seitig (Liste der Übersichtstypen wie Bildschirme, Link-Editor usw.) als auch Server-seitig (Webanwendungen, Berichte, JSP, JSSP usw.). In v7 funktioniert es nur auf der Server-Seite. Wenn Sie zur vollen Funktionalität wie in Version 5 zurückkehren möchten, müssen Sie die Links mit diesem Parameter ändern und über die Verbindungsseite übergeben:

Link-Beispiel:

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

Neuer Link mit der Verbindungsseite:

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>Wenn Sie einen Operator verwenden, der mit einer vertrauenswürdigen IP-Maske verknüpft ist, überprüfen Sie, ob er über die Mindestrechte verfügt und sich in einer Sicherheitszone im Modus **sessionTokenOnly** befindet.

### SQL-Funktionen {#sql-functions}

Unbekannte SQL-Funktionsaufrufe werden nicht mehr automatisch an den Server gesendet. Derzeit müssen alle SQL-Funktionen zum Schema **xtk:funcList** hinzugefügt werden (weitere Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/adding-additional-sql-functions.md)). Bei der Migration wird während des Postupgrades eine Option hinzugefügt, mit der Sie die Kompatibilität mit alten nicht deklarierten SQL-Funktionen aufrechterhalten können. Wenn Sie diese Funktionen weiterhin verwenden möchten, überprüfen Sie, ob die Option **XtkPassUnknownSQLFunctionsToRDBMS** auf der Knotenebene **[!UICONTROL Administration > Plattform > Optionen]** tatsächlich definiert ist.

>[!IMPORTANT]
>
>Wir empfehlen dringend, diese Option aufgrund der damit verbundenen Sicherheitsrisiken nicht zu verwenden.

### JSSP {#jssp}

Wenn Sie den Zugriff auf bestimmte Seiten über das HTTP-Protokoll (nicht HTTPS) autorisieren möchten, z. B. in Ihren Web-Apps, müssen Sie unabhängig von der in den Sicherheitszonen durchgeführten Konfiguration den Parameter **httpAllowed=„true“** in der entsprechenden Relais-Regel angeben.

Wenn Sie anonyme JSSPs verwenden, müssen Sie den Parameter **httpAllowed=„true“** in einer Relais-Regel für Ihre JSSP-Datei (**[!UICONTROL serverConf.xml]**) hinzufügen:

Beispiel:

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## Syntax {#syntax}

### JavaScript {#javascript}

In Adobe Campaign v7 ist ein neuerer JavaScript-Interpreter integriert. Diese Aktualisierung kann jedoch zu Fehlfunktionen bestimmter Skripte führen. Da die vorherige Engine erlaubter war, würden bestimmte Syntaxen funktionieren, was bei der neuen Version der Engine nicht mehr der Fall ist.

Das **[!UICONTROL myObject.@attribute]** Die Syntax ist jetzt nur noch für XML-Objekte gültig. Diese Syntax kann für die Personalisierung von Sendungen und das Content-Management verwendet werden. Wenn Sie diese Art der Syntax für ein Nicht-XML-Objekt verwenden, funktionieren die Personalisierungsfunktionen nicht mehr.

Für alle anderen Objekttypen lautet die Syntax jetzt **[!UICONTROL myObject`[`„attribute“`]`]**. Beispiel: ein Nicht-XML-Objekt, das die folgende Syntax verwendet: **[!UICONTROL employee.@sn]**, muss jetzt die folgende Syntax verwenden: **[!UICONTROL employee`[`„sn“`]`]**.

* Frühere Syntax:

  ```
  employee.@sn
  ```

* Neue Syntax:

  ```
  employee["sn"]
  ```

Um einen Wert in einem XML-Objekt zu ändern, müssen Sie jetzt zunächst den Wert aktualisieren, bevor Sie den XML-Knoten hinzufügen:

* Alter JavaScript-Code:

  ```
  var cellStyle = node.style.copy();
  this.styles.appendChild(cellStyle);
  cellStyle.@width = column.@width;
  ```

* Neuer JavaScript-Code:

  ```
  var cellStyle = node.style.copy();
  cellStyle.@width = column.@width;
  this.styles.appendChild(cellStyle);
  ```

Ein XML-Attribut kann nicht mehr als Tabellenschlüssel verwendet werden.

* Frühere Syntax:

  ```
  if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
  ```

* Neue Syntax:

  ```
  if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
  ```

### SQLData {#sqldata}

Um die Sicherheit der Instanz zu erhöhen, wurde in Adobe Campaign v7 eine neue Syntax eingeführt, die die auf SQLData basierende Syntax ersetzt. Wenn Sie diese Code-Elemente mit dieser Syntax verwenden, müssen Sie sie ändern. Die wichtigsten Punkte sind:

* Filtern nach Unterabfrage: Die neue Syntax basiert auf dem `<subQuery>`-Element, um eine Unterabfrage zu definieren
* Aggregate: Die neue Syntax lautet „aggregate function(collection)“
* Filtern nach Join: Die neue Syntax ist `[schemaName:alias:xPath]`

Das Schema queryDef (xtk:queryDef) wurde geändert:

* Es ist ein neues `<subQuery>` verfügbar, das die in SQLData enthaltene SELECT-Anweisung ersetzt
* Für das Attribut @setOperator werden zwei neue Werte eingeführt: „IN“ und „NOT IN“
* ein neues `<where>`, das dem `<node>` untergeordnet ist: Dadurch können Sie in SELECT „Unterauswahlen“ vornehmen

Wenn ein &quot;@expr“-Attribut verwendet wird, kann SQLData vorhanden sein. Es kann nach den folgenden Begriffen gesucht werden: „SQLData“, „aliasSqlTable“, „sql“.

Adobe Campaign v7-Instanzen sind standardmäßig gesichert. Sicherheit kommt in Form von Definitionen von Sicherheitszonen in der Datei **[!UICONTROL serverConf.xml]** vor: Das **allowSQLInjection**-Attribut verwaltet die Sicherheit der SQL-Syntax.

Wenn während der Ausführung eines Postupgrades ein SQLData-Fehler auftritt, müssen Sie dieses Attribut ändern, um die Verwendung von SQLData-basierten Syntaxen vorübergehend zuzulassen und so den Code neu zu schreiben. Dazu muss die folgende Option in der Datei „serverConf.xml“ **werden**:

```
allowSQLInjection="true"
```

Starten Sie daher das Postupgrade mit dem folgenden Befehl neu:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Sie müssen die Sicherheitszonen konfigurieren (siehe [Sicherheit](#security)) und dann die Sicherheit reaktivieren, indem Sie die Option ändern:

```
allowSQLInjection="false"
```

Nachfolgend finden Sie Vergleichsbeispiele zwischen der alten und der neuen Syntax.

**Filtern nach Unterabfragen**

* Frühere Syntax:

  ```
  <condition expr="@id NOT IN ([SQLDATA[SELECT iOperatorId FROM XtkOperatorGroup WHERE iGroupId = $(../@owner-id)]])" enabledIf="$(/ignored/@ownerType)=1"/>
  ```

* Neue Syntax:

  ```
  <condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
    <subQuery schema="xtk:operatorGroup">
       <select>
         <node expr="[@operator-id]" />
       </select>
       <where>
         <condition expr="[@group-id]=$long(../@owner-id)"/>
       </where>
     </subQuery>
  </condition>
  ```

* Frühere Syntax:

  ```
  <queryFilter name="dupEmail" label="Emails duplicated in the folder" schema="nms:recipient">
      <where>
        <condition sql="sEmail in (select sEmail from nmsRecipient where iFolderId=$(folderId) group by sEmail having count(sEmail)>1)" internalId="1"/>
      </where>
      <folder _operation="none" name="nmsSegment"/>
    </queryFilter>
  ```

* Neue Syntax:

  ```
  <queryFilter name="dupEmail" label=" Emails duplicated in the folder " schema="nms:recipient">
      <where>
        <condition expr="@email" setOperator="IN" internalId="1">
          <subQuery schema="nms:recipient">
            <select><node expr="@email"/></select>
            <where><condition expr="[@folder-id]=$(folderId)"/></where>
            <groupBy><node expr="@email"/></groupBy>
            <having><condition expr="count(@email)>1"/></having>
          </subQuery>
        </condition>
      </where>
      <folder _operation="none" name="nmsSegment"/>
    </queryFilter>
  ```

**Das Aggregat**

Aggregatfunktion (Sammlung)

* Frühere Syntax:

  ```
  <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
  ```

* Neue Syntax:

  ```
  <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
  ```

  >[!NOTE]
  >
  >Für die Aggregatfunktionen werden automatisch Fugen durchgeführt. Die Bedingung WO O0.iOperationId=iOperationId muss nicht mehr angegeben werden.
  >
  >Die Funktion „count(&#42;)“ kann nicht mehr verwendet werden. Sie müssen „count()“ verwenden.

* Frühere Syntax:

  ```
  <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
  ```

* Neue Syntax:

  ```
  <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                    <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
  ```

**Filter nach Joins**

`[schemaName:alias:xPath]`

Der Alias ist optional

* Frühere Syntax:

  ```
  <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                           aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
  ```

* Neue Syntax:

  ```
  <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
  ```

**Tipps und Tricks**

Referenzieren eines „Feld“-Felds der `<queryDef>` in einem `<subQuery>`-Element   -Element verwenden, die folgende Syntax verwenden: `[../@field]`

Beispiel:

```
<queryDef operation="select" schema="xtk:jobLog" startPath="/" xtkschema="xtk:queryDef">
  <select>
    <node expr="[job/@pid]" alias="@pid"/>
    <node expr="@id" ordered="true"/>
    <node expr="@logType"/>
  </select>
  <where>
    <condition expr="[@job-id]=99"/>
    <condition expr="@logType" setOperator="IN">
      <subQuery schema="xtk:jobLog">
        <select><node expr="@logType"/></select>
        <where><condition expr="[@job-id]=[../job/@id]"/></where>
        <groupBy><node expr="@logType"/></groupBy>
        <having><condition expr="count(@logType)>1"/></having>
      </subQuery>
    </condition>
  </where>
</queryDef>
```

## Konflikte {#conflicts}

Die Migration wird über ein Postupgrade durchgeführt und Konflikte können in Berichten, Formularen oder Web-Anwendungen auftreten. Diese Konflikte können über die Konsole aufgelöst werden.

Nach der Ressourcensynchronisierung können Sie mit dem **postupgrade**-Befehl erkennen, ob die Synchronisierung Fehler oder Warnungen erzeugt.

### Anzeigen des Synchronisierungsergebnisses {#view-the-synchronization-result}

Das Synchronisierungsergebnis kann auf zwei Arten angezeigt werden:

* In der Befehlszeilenschnittstelle werden Fehler durch einen dreifachen Pfeil **>>** materialisiert und die Synchronisierung wird automatisch angehalten. Warnungen werden durch einen doppelten Pfeil **>>** materialisiert und müssen nach Abschluss der Synchronisierung aufgelöst werden. Am Ende des Postupgrades wird in der Eingabeaufforderung eine Zusammenfassung angezeigt. Beispiel:

  ```
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     info    log     =========Summary of the update==========
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Betrifft die Warnung einen Konflikt mit Ressourcen, ist ein Eingreifen des Bedieners erforderlich, um diesen zu beheben.

* Die **postupgrade_`<server version number>`_time_`>`.log** enthält das Synchronisierungsergebnis. Sie ist standardmäßig im folgenden Verzeichnis verfügbar: **Installationsverzeichnis/var/`<instance>`postupgrade**. Fehler und Warnungen werden durch die Attribute **Fehler** und **Warnung** gekennzeichnet.

### Konflikt lösen {#resolve-a-conflict}

Konflikte dürfen nur von fortgeschrittenen Benutzern und Benutzern gelöst werden, denen Administratorrechte erteilt wurden.

Um einen Konflikt zu lösen, wenden Sie den folgenden Prozess an:

1. Platzieren Sie den Cursor in der Adobe Campaign-Baumstruktur über **[!UICONTROL Administration > Konfiguration > Paketverwaltung > Konflikte bearbeiten]**.
1. Wählen Sie in der Liste den Konflikt aus, den Sie auflösen möchten.

Es gibt drei Möglichkeiten, einen Konflikt zu lösen:

* **[!UICONTROL Als aufgelöst deklariert]**: erfordert vorab das Eingreifen des Benutzers.
* **[!UICONTROL Neue Version akzeptieren]**: Wird empfohlen, wenn die mit Adobe Campaign bereitgestellten Ressourcen von den Benutzenden nicht geändert wurden.
* **[!UICONTROL Aktuelle Version beibehalten]** bedeutet, dass die Aktualisierung abgelehnt wird.

  >[!IMPORTANT]
  >
  >Wenn Sie diesen Auflösungsmodus auswählen, riskieren Sie, Patches in der neuen Version zu verlieren. Es wird daher dringend empfohlen, diese Option nicht zu verwenden oder nur für erfahrene Benutzer zu reservieren.

Wenn Sie sich dafür entscheiden, den Konflikt manuell zu lösen, gehen Sie wie folgt vor:

1. Suchen Sie im unteren Bereich des Fensters nach der **`_conflict_ string`**, um die Entitäten mit Konflikten zu finden. Die mit der neuen Version installierte Entität enthält das **new**-Argument. Die Entität, die mit der vorherigen Version übereinstimmt, enthält das **cus**-Argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Löschen Sie die Version, die Sie nicht behalten möchten. Löscht die **`_conflict_argument_ string`** der Entität, die Sie behalten.

   ![](assets/s_ncs_production_conflict003.png)

1. Wechseln Sie zu dem Konflikt, den Sie gelöst hätten. Klicken Sie auf **[!UICONTROL Aktionen]** und wählen Sie **[!UICONTROL Als aufgelöst deklarieren]** aus.
1. Speichern Sie Ihre Änderungen: Der Konflikt ist jetzt gelöst.

<!--
## Tomcat {#tomcat}

The integrated Tomcat server in Adobe Campaign v7 has changed version. Its installation folder (tomcat-6) has therefore also changed (tomcat 7). After the postupgrade, make sure to check that the paths do link to the updated folder (in the **[!UICONTROL serverConf.xml]** file):

```
$(XTK_INSTALL_DIR)/tomcat-X/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-X/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-X/lib/el-api.jar
```
-->

## Interaktion {#interaction}

### Voraussetzungen {#prerequisites}

**Vor dem Postupgrade** müssen Sie alle Schemaverweise aus 6.02 löschen, die in v7 nicht mehr vorhanden sein werden.

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### Angebotsinhalt {#offer-content}

In v7 wurde der Angebotsinhalt verschoben. In Version 6.02 befand sich der Inhalt in jedem Darstellungsschema (**nms:emailOfferView**). In v7 befindet sich der Inhalt jetzt im Angebotsschema. Nach dem Postupgrade ist der Inhalt daher nicht in der Benutzeroberfläche sichtbar. Nach dem Postupgrade müssen Sie den Angebotsinhalt neu erstellen oder ein Skript entwickeln, das den Inhalt automatisch aus dem Darstellungsschema in das Angebotsschema verschiebt.

>[!IMPORTANT]
>
>Wenn einige Sendungen mit konfigurierten Angeboten nach der Migration gesendet werden sollten, müssen Sie alle diese Sendungen löschen und in v7 neu erstellen. Ist dies nicht möglich, wird ein „Kompatibilitätsmodus“ angeboten. Dieser Modus wird nicht empfohlen, da Sie nicht von allen neuen Funktionen in Interaction v7 profitieren werden. Dies ist ein Übergangsmodus, in dem Sie laufende Kampagnen vor der eigentlichen Migration auf 6.1 abschließen können. Für weitere Informationen zu diesem Modus kontaktieren Sie uns bitte.

Ein Beispiel für ein Verschiebungsskript (**interactionTo610_full_XX.js**) ist im Ordner **Migration** im Ordner Adobe Campaign v7 verfügbar. Diese Datei zeigt ein Beispiel für ein Skript für einen Client, bei dem eine einzelne E-Mail-Darstellung pro Angebot verwendet wird (die Felder **[!UICONTROL htmlSource]** und **[!UICONTROL textSource]**). Der Inhalt der Tabelle **NmsEmailOfferView** wurde in die Angebotstabelle verschoben.

>[!NOTE]
>
>Die Verwendung dieses Skripts ermöglicht es Ihnen nicht, die Optionen „Content-Management“ und „Rendering-Funktionen“ zu nutzen. Um von diesen Funktionen zu profitieren, müssen Sie die Katalogangebote überdenken, insbesondere die Angebotsinhalte und Konfigurationsbereiche.

```
loadLibrary("/nl/core/shared/nl.js");

NL.require("/nl/core/shared/xtk.js");

// 1. Restore old emailOfferView schema
logInfo("Restoring old emailOfferView schema");
var oldOfferViewSchemas = <entities schema="xtk:srcSchema"/>;

oldOfferViewSchemas.appendChild(
  <srcSchema img="nms:offerView.png"
             label="Email offer representations"
             labelSingular="Email offer representation"
             name="emailOfferView" namespace="nlmig"
             genAccessors="false" implements="xtk:persist">
    <element name="emailOfferView" template="nms:offerView" sqltable="NmsEmailOfferView">
      <element name="offer" revLabel="Email representation" revIntegrity="owncopy"/>
      <element   name="htmlSource"      type="html" label="HTML content"  xml="true"/>
      <element   name="textSource"      type="CDATA" label="Text content" xml="true"/>
      <element   name="htmlSource_jst"  type="CDATA" label="HTML script"  desc="HTML content calculation script."  xml="true" advanced="true"/>
      <element   name="textSource_jst"  type="CDATA" label="Text script" desc="Text content calculation script." xml="true" advanced="true"/>
    </element>
  </srcSchema>);

var oldOfferViewsPkg = <builder><package buildNumber="*">{oldOfferViewSchemas}</package></builder>;
xtk.builder.InstallPackage(oldOfferViewsPkg);

// 2. Migrate data from old emailOfferView table to nms:offer
logInfo("Moving data from old EmailOfferView table to NmsOffer");
var OFFER_STATUS_VALIDATED = 3;

var queryDef = xtk.queryDef.create(
  <queryDef operation="select" schema="nlmig:emailOfferView">
    <select>
      <node expr="[@offer-id]"/>
      <node expr="[@space-id]"/>
      <node expr="htmlSource_jst"/>
      <node expr="textSource_jst"/>
    </select>
  </queryDef>);
var res = queryDef.ExecuteQuery();

var processedOffers = {};
for each( var emailOfferView in res.emailOfferView )
{
  if( processedOffers[String(emailOfferView.@["offer-id"])] != undefined )
  {
    logWarning("Found 2 or more eff fffffmail representations for offer " + String(emailOfferView.@["offer-id"]) + ". Only keep the first one here.");
    continue;
  }
  xtk.session.Write(
    <offer id={emailOfferView.@["offer-id"]} status={OFFER_STATUS_VALIDATED} xtkschema="nms:offer">
      <view>
        {emailOfferView.mdSource_jst}
        {emailOfferView.textSource_jst}
      </view>
    </offer>
  );
  processedOffers[String(emailOfferView.@["offer-id"])] = 1;
}

// 3. Get rid of emailOfferView schema now that data has been moved.
logInfo("Deleting EmailOfferView schema");
xtk.session.Write(<srcSchema xtkschema="xtk:srcSchema" name="emailOfferView" namespace="nlmig" _operation="delete"/>);

logInfo("Done");
```

### Tests und Konfiguration {#tests-and-configuration}

Im Folgenden finden Sie die Vorgehensweise nach dem Verschieben des Angebotsinhalts, wenn Sie nur eine Umgebung haben. Nehmen wir in diesem Fall „ENV“ als Beispiel.

1. Aktualisieren Sie in allen Platzierungen der Umgebung „ENV“ die Liste der verwendeten Felder. Beispiel: Für eine Platzierung, bei der nur „htmlSource **[!UICONTROL verwendet wird]** müssen Sie &quot;**[!UICONTROL /htmlSource“]**.

   ![](assets/migration_interaction_2.png)

1. Wählen Sie **[!UICONTROL Feld „Umgebungstyp]** auf der Registerkarte **[!UICONTROL Allgemein]** die Option **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. Erstellen Sie eine Design-Umgebung (z. B. „ENV_DESIGN„) und verbinden Sie sie mit der ENV-Online-Umgebung.

   ![](assets/migration_interaction_4.png)

1. Stellen Sie alle Angebotsplatzierungen der „ENV“-Umgebung bereit (Rechtsklick > **[!UICONTROL Aktionen > Bereitstellen]**) und wählen Sie die Umgebung „ENV_DESIGN“ aus.

   ![](assets/migration_interaction_5.png)

1. Tun Sie dasselbe für alle „ENV“-Umgebungsangebote.
1. Aktivieren Sie alle Umgebungsangebote „ENV_DESIGN“ auf den entsprechenden Kanälen.
1. Testen, ob ein Angebot live geschaltet wird. Wenn keine Probleme auftreten, führen Sie ausstehende Aufgaben für die neueste Workflow-Aufgabe **[!UICONTROL Angebotsbenachrichtigung]** (offerMgt) aus, damit alle Angebote live geschaltet werden.

   ![](assets/migration_interaction_6.png)

1. Führen Sie umfassende Tests durch.

   >[!NOTE]
   >
   >Die Namen von Online-Kategorien und -Angeboten werden nach der Live-Schaltung geändert. Aktualisieren Sie im eingehenden Kanal alle Verweise auf Angebote und Kategorien.

## Berichte {#reports}

### Standardberichte {#standard-reports}

Alle Standardberichte verwenden derzeit die Rendering-Engine v6.x. Wenn Sie JavaScript zu diesen Berichten hinzugefügt haben, funktionieren bestimmte Elemente möglicherweise nicht mehr. Die alte Version von JavaScript ist nicht mit der Rendering-Engine v6.x kompatibel. Daher müssen Sie den JavaScript-Code überprüfen und später anpassen. Sie sollten jeden Bericht testen, insbesondere die Exportfunktion.

### Personalisierte Berichte {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
Wenn Sie von den neuen Berichtsfunktionen profitieren möchten, müssen Sie die Berichte erneut veröffentlichen. Überprüfen Sie in diesem Fall alle Ihre Skripte und ändern Sie sie bei Bedarf. Wenn Sie im Hinblick auf den PDF-Export ein bestimmtes Skript für Open Office hinzugefügt haben, funktioniert dies nicht mehr mit der neuen PDF-Export-Engine (PhantomJS).

## Web-Anwendungen {#web-applications}

Es gibt zwei Web-Anwendungsfamilien:

* identifizierte Web-Anwendungen (zusammen gesehen, Genehmigungsformulare, interne Entwicklungen im Extranet),
* Anonyme Web-Anwendungen (Web- oder Umfrageformulare).

### Identifizierte Web-Anwendungen {#identified-web-applications}

Wie bei Berichten ([weitere Informationen](#reports)) müssen Sie, wenn Sie JavaScript hinzugefügt haben, dies überprüfen und bei Bedarf anpassen. Wenn Sie von dem blauen Banner v7 (mit den blauen Registerkarten) profitieren möchten, müssen Sie die Web-Anwendung erneut veröffentlichen.

Die Verbindungsmethoden für Web-Anwendungen wurden in v7 geändert. Wenn Verbindungsprobleme in identifizierten Web-Anwendungen auftreten, müssen Sie die Optionen **allowUserPassword** und **sessionTokenOnly** in der Datei **serverConf.xml** vorübergehend aktivieren. Ändern Sie nach dem Postupgrade diese Optionswerte:

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

Starten Sie daher das Postupgrade mit dem folgenden Befehl neu:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

Testen Sie Ihre Web-Anwendungen in der Rendering-Engine von v6.x, bevor Sie sie veröffentlichen. Deaktivieren Sie dann diese beiden Optionen.

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### Anonyme Web-Anwendungen {#anonymous-web-applications}

Wenn Probleme auftreten, veröffentlichen Sie die Web-Anwendung erneut.
