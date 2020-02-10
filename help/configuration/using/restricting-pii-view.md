---
title: Einschränkung der PII-Ansicht
seo-title: Einschränkung der PII-Ansicht
description: Einschränkung der PII-Ansicht
seo-description: null
page-status-flag: never-activated
uuid: 4dddc7f5-dac3-47b3-b3cb-92b47eb595fa
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 550439c1-978c-414e-be5b-a9e1a202c4cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Einschränkung der PII-Ansicht{#restricting-pii-view}

## Übersicht {#overview}

Einige Kunden benötigen Marketingbenutzer, die auf Datensätze zugreifen können, möchten jedoch nicht, dass sie persönliche identifizierbare Informationen (PII) wie Vorname, Nachname oder E-Mail-Adresse sehen. Adobe Campaign bietet eine Möglichkeit, die Privatsphäre zu schützen und zu verhindern, dass Daten von regulären Kampagnenbetreibern missbraucht werden.

## Umsetzung {#implementation}

Ein neues Attribut, das auf ein Element oder Attribut angewendet werden kann, wurde zu den Schemas hinzugefügt und ergänzt das vorhandene Attribut **[!UICONTROL visibleIf]** . Dieses Attribut ist: **[!UICONTROL accessibleIf]** . Wenn ein XTK-Ausdruck in Bezug auf den aktuellen Benutzerkontext enthalten ist, kann er zum Beispiel genutzt werden **[!UICONTROL HasNamedRight]** oder **[!UICONTROL $(login)]** .

Nachfolgend finden Sie ein Beispiel für eine Schema-Erweiterung des Empfängerschemas, die diese Verwendung zeigt:

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

Die Haupteigenschaften sind:

* **[!UICONTROL visibleIf]** : Blendet die Felder aus den Metadaten aus, sodass sie nicht in einer Schemaansicht, Spaltenauswahl oder einem Ausdrucksgenerator aufgerufen werden können. Dadurch werden jedoch keine Daten ausgeblendet, wenn der Feldname manuell in einen Ausdruck eingegeben wird, wird der Wert angezeigt.
* **[!UICONTROL accessibleIf]** : Blendet die Daten aus der resultierenden Abfrage aus (durch leere Werte ersetzen). Wenn visibleIf leer ist, erhält es denselben Ausdruck wie **[!UICONTROL accessibleIf]** .

Die Verwendung dieses Attributs in Campaign hat folgende Konsequenzen:

* Daten werden nicht mit einem generischen Abfrageeditor in der Konsole angezeigt.
* Die Daten sind in Übersichtslisten und in der Datensatzliste (Konsole) nicht sichtbar.
* Daten werden in der Detailansicht schreibgeschützt.
* Daten können nur innerhalb von Filtern verwendet werden (d. h. bei Verwendung einiger Dichotomie-Strategien können Sie trotzdem Werte erraten).
* Alle Ausdrücke, die mit einem eingeschränkten Feld erstellt werden, sind eingeschränkt auf: lower(@email) wird so barrierefrei wie @email.
* In einem Workflow können Sie die eingeschränkte Spalte der Zielgruppe als zusätzliche Spalte des Übergangs hinzufügen, sie steht Adobe Campaign-Benutzern jedoch weiterhin nicht zur Verfügung.
* Beim Speichern der Zielgruppe in einer Gruppe (Liste) sind die Eigenschaften der gespeicherten Felder mit der Datenquelle identisch.
* Daten sind für JS-Code standardmäßig nicht verfügbar.

## Empfehlungen {#recommendations}

Bei jeder Auslieferung werden E-Mail-Adressen in die **[!UICONTROL broadLog]** und die **[!UICONTROL forecastLog]** Tabellen kopiert: Daher müssen diese Felder auch geschützt werden.

Nachfolgend finden Sie ein Beispiel für die Protokolltabellenerweiterung, um Folgendes zu implementieren:

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
>Diese Einschränkung gilt für nicht technische Nutzer: Ein technischer Benutzer mit entsprechenden Berechtigungen kann Daten abrufen. Diese Methode ist daher nicht hundertprozentig sicher.

