---
product: campaign
title: Einschränken der Anzeige von personenbezogenen Daten
description: Erfahren Sie, wie Sie die Anzeige von personenbezogenen Daten einschränken
feature: PI
role: Data Engineer, Developer
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: e198defd60f4b12681025b04b12a1498df015047
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 69%

---

# Einschränken der Anzeige von personenbezogenen Daten{#restricting-pii-view}

## Übersicht {#overview}

Einige Kunden benötigen Marketing-Benutzer, um auf Datensätze zugreifen zu können, möchten aber nicht, dass sie personenbezogene Daten (PII) sehen, wie Vorname, Nachname oder E-Mail-Adresse. Adobe Campaign schlägt eine Möglichkeit vor, die Privatsphäre zu schützen und zu verhindern, dass Daten von regulären Campaign-Benutzenden missbraucht werden.

## Implementierung {#implementation}

Zu den Schemata wurde ein neues Attribut hinzugefügt, das auf beliebige Elemente oder Attribute angewendet werden kann. Es ergänzt das vorhandene Attribut **[!UICONTROL visibleIf]** . Dieses Attribut ist: **[!UICONTROL accessibleIf]**. Wenn ein XTK-Ausdruck im Zusammenhang mit dem aktuellen Benutzerkontext enthalten ist, kann z. B. **[!UICONTROL HasNamedRight]** oder **[!UICONTROL $(login)]** genutzt werden.

Nachfolgend finden Sie ein Beispiel für eine Erweiterung des Empfängerschemas, das diese Nutzung zeigt:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

Die wichtigsten Eigenschaften sind:

* **[!UICONTROL visibleIf]** : Blendet die Felder aus den Metadaten aus, sodass sie nicht in einer Schemaansicht, Spaltenauswahl oder einem Ausdrucksassistenten aufgerufen werden können. Dadurch werden jedoch keine Daten ausgeblendet. Wenn der Feldname manuell in einen Ausdruck eingegeben wird, wird der Wert angezeigt.
* **[!UICONTROL accessibleIf]** : Blendet die Daten aus der resultierenden Abfrage aus (und ersetzt sie durch leere Werte). Wenn „visibleIf“ leer ist, erhält es denselben Ausdruck wie **[!UICONTROL accessibleIf]** .

Die Verwendung dieses Attributs in Campaign hat folgende Folgen:

* Die Daten werden mit dem generischen Abfrage-Tool nicht in der Konsole angezeigt.
* Die Daten sind in Übersichtslisten und der Liste der Einträge (Konsole) nicht sichtbar.
* Die Daten werden in detaillierter Ansicht schreibgeschützt.
* Die Daten sind nur innerhalb von Filtern verwendbar (was bedeutet, dass Sie bei einigen Dichotomie-Strategien immer noch Werte schätzen können).
* Jeder Ausdruck, der unter Verwendung eines eingeschränkten Feldes gebildet wird, wird ebenfalls eingeschränkt: lower(@email) wird genauso zugänglich wie @email.
* In einem Workflow können Sie die eingeschränkte Spalte der Zielpopulation als zusätzliche Spalte des Übergangs hinzufügen, sie ist aber für Adobe Campaign-Benutzer immer noch unzugänglich.
* Beim Speichern der Zielpopulation in einer Gruppe (Liste) sind die Eigenschaften der gespeicherten Felder identisch mit der Datenquelle.
* Die Daten sind standardmäßig nicht für JS-Code verfügbar.

>[!IMPORTANT]
>
>Die Verwendung des Attributs **accessibleIf** bei kritischen Parametern (z. B. bei zusammengesetzten Schlüsseln) kann zu Fehlern für Benutzende führen, die die Daten aufgrund ausgeblendeter Daten nicht lesen dürfen. Dies kann zu Abfragefehlern oder unerwartetem Verhalten führen. Stellen Sie sicher, dass wichtige Parameter verfügbar sind, um Unterbrechungen zu verhindern.

## Empfehlungen {#recommendations}

Bei jedem Versand werden E-Mail-Adressen in die Tabellen **[!UICONTROL broadLog]** und **[!UICONTROL forecastLog]** kopiert. Daher müssen diese Felder auch geschützt werden.

Nachfolgend finden Sie ein Beispiel für die Erweiterung der Protokolltabelle, um Folgendes zu implementieren:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Diese Einschränkung gilt für nicht-technische Benutzer: Ein technischer Benutzer mit den entsprechenden Berechtigungen kann Daten abrufen. Diese Methode ist daher nicht 100% sicher.
