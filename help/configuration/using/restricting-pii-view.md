---
title: Einschränken der PII-Ansicht
seo-title: Einschränken der PII-Ansicht
description: Einschränken der PII-Ansicht
seo-description: null
page-status-flag: never-activated
uuid: 4dddc7f5-dac3-47b3-b3cb-92b47eb595fa
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 550439c1-978c-414e-be5b-a9e1a202c4cd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 3%

---


# Einschränken der PII-Ansicht{#restricting-pii-view}

## Übersicht {#overview}

Einige Kunden benötigen Marketingbenutzer, die auf Datendatensätze zugreifen können, möchten jedoch nicht, dass sie persönliche identifizierbare Informationen (PII) wie Vorname, Nachname oder E-Mail-Adresse sehen. Adobe Campaign schlägt eine Möglichkeit zum Schutz der Privatsphäre und zur Verhinderung der missbräuchlichen Verwendung von Daten durch Betreiber regulärer Kampagnen vor.

## Implementierung{#implementation}

Zu den Schemas wurde ein neues Attribut hinzugefügt, das auf beliebige Elemente oder Attribute angewendet werden kann. Es ergänzt das vorhandene Attribut **[!UICONTROL visibleIf]** . Dieses Attribut ist: **[!UICONTROL accessibleIf]** . Wenn ein XTK-Ausdruck im Zusammenhang mit dem aktuellen Benutzerkontext enthalten ist, kann er beispielsweise **[!UICONTROL HasNamedRight]** oder **[!UICONTROL $(login)]** nutzen.

Nachfolgend finden Sie ein Beispiel für eine Empfänger Schema Extension, die diese Nutzung zeigt:

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

* **[!UICONTROL visibleIf]** : Blendet die Felder aus den Metadaten aus, sodass sie nicht in einer Schema-Ansicht, Spaltenauswahl oder einem Ausdruck-Builder aufgerufen werden können. Dadurch werden jedoch keine Daten ausgeblendet, wenn der Feldname manuell in einen Ausdruck eingegeben wird, wird der Wert angezeigt.
* **[!UICONTROL accessibleIf]** : Blendet die Daten (durch leere Werte ersetzen) aus der resultierenden Abfrage aus. Wenn visibleIf leer ist, erhält es denselben Ausdruck wie **[!UICONTROL accessibleIf]** .

Die Verwendung dieses Attributs in der Kampagne hat folgende Folgen:

* Daten werden nicht mit Generische Abfragetool in der Konsole angezeigt.
* Die Daten sind in Übersichtsregeln und in der Liste der Aufzeichnung (Konsole) nicht sichtbar.
* Daten werden in detaillierter Ansicht schreibgeschützt.
* Daten können nur innerhalb von Filtern verwendet werden (d. h. bei Verwendung einiger Dichotomie-Strategien können Sie trotzdem Werte erraten).
* Jeder Ausdruck, der mit einem eingeschränkten Feld erstellt wurde, wird eingeschränkt auf: lower(@email) wird so barrierefrei wie @email.
* In einem Arbeitsablauf können Sie die eingeschränkte Spalte als zusätzliche Spalte der Transition der Zielgruppe hinzufügen, sie steht aber Adobe Campaign-Benutzern weiterhin nicht zur Verfügung.
* Beim Speichern der Zielgruppe in einer Liste sind die Eigenschaften der gespeicherten Felder identisch mit der Datenquelle.
* Daten sind für JS-Code standardmäßig nicht verfügbar.

## Empfehlungen {#recommendations}

In jedem Versand werden E-Mail-Adressen in die Tabellen **[!UICONTROL wideLog]** und **[!UICONTROL foreLog]** kopiert: Daher müssen diese Felder auch geschützt werden.

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
>Diese Einschränkung gilt für nicht technische Nutzer: Ein technischer Benutzer mit entsprechenden Berechtigungen kann Daten abrufen. Diese Methode ist daher nicht zu 100 % sicher.

