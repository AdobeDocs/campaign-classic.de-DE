---
product: campaign
title: Über die Schemabearbeitung
description: Erste Schritte mit der Schemabearbeitung
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 63%

---

# Über die Schemabearbeitung{#about-schema-edition}

Adobe Campaign verwendet Datenschemata zum:

* Definieren der Verknüpfung zwischen den Datenobjekten in der Anwendung mit den zugrunde liegenden Datenbanktabellen
* Definieren von Beziehungen zwischen den unterschiedlichen Datenobjekten in der Campaign-Anwendung
* Definieren und Beschreiben der einzelnen Felder eines jeden Objekts

Nähere Erläuterungen zu den in Campaign integrierten Tabellen und ihrer Interaktion finden Sie in [diesem Abschnitt](https://helpx.adobe.com/de/campaign/kb/acc-datamodel.html).

## Erweitern oder Erstellen von Schemata {#extending-or-creating-schemas}

Um ein Feld, einen Index oder ein anderes Element zu einem der Kerndatenschemata in Campaign hinzuzufügen, z. B. die Empfängertabelle (nms:recipient), müssen Sie dieses Schema erweitern. Weitere Informationen hierzu finden Sie im Abschnitt [Erweitern eines Schemas](../../configuration/using/extending-a-schema.md) .

Um einen komplett neuen Datentyp hinzuzufügen, der in Adobe Campaign nicht standardmäßig zur Verfügung gestellt wird (z. B. eine Vertragstabelle), können Sie direkt ein benutzerdefiniertes Schema erstellen. Weitere Informationen hierzu finden Sie im Abschnitt [Datenschemata](../../configuration/using/data-schemas.md) .

![](assets/schemaextension_getting_started_1.png)

Nachdem Sie ein Schema für die Verwendung erweitert oder erstellt haben, empfiehlt es sich, seine XML-Inhaltselemente in der Reihenfolge zu definieren, in der sie unten aufgeführt sind.

## Auflistungen {#enumerations}

Auflistungen werden als Erstes definiert, noch vor dem Hauptelement des Schemas. Über sie können Sie Werte in einer Liste anzeigen, um die Auswahl einzuschränken, die der Benutzer für ein bestimmtes Feld hat.

Beispiel:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Beim Definieren von Feldern können Sie diese Auflistung wie folgt verwenden:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>Sie können auch benutzerseitig verwaltete Auflistungen verwenden (in der Regel unter **[!UICONTROL Administration]** > **[!UICONTROL Platform]**), um die Werte für ein bestimmtes Feld anzugeben. Dabei handelt es sich um globale Auflistungen. Sie sind besser geeignet, wenn Ihre Auflistung außerhalb des von Ihnen eingesetzten Schemas verwendet werden kann.

Weiterführende Informationen zu Auflistungen finden Sie in den Abschnitten [Auflistungen](../../configuration/using/schema-structure.md#enumerations) und [`<enumeration>` Element](../../configuration/using/schema/enumeration.md) .

## Index {#index}

Indizes sind die ersten Elemente, die im Hauptelement des Schemas deklariert werden.

Sie können eindeutig sein oder nicht und auf ein oder mehrere Felder verweisen.

Beispiele:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

Das Attribut **xpath** verweist auf das Feld in Ihrem Schema, das Sie indizieren möchten.

>[!IMPORTANT]
>
>Es ist wichtig zu beachten, dass die von Indizes bereitgestellten Leistungsverbesserungen bei der SQL-Abfrage auch Leistungseinbußen beim Schreiben von Datensätzen verursachen. Die Indizes sollten daher mit Vorsicht verwendet werden.

Weiterführende Informationen zu Indizes finden Sie im Abschnitt [Indexierte Felder](../../configuration/using/database-mapping.md#indexed-fields) .

## Schlüssel {#keys}

Jede Tabelle muss über mindestens einen Schlüssel verfügen. Oft wird sie automatisch im Hauptelement des Schemas erstellt, indem das Attribut **@autopk=true** auf &quot;true&quot;gesetzt wird.

Der Primärschlüssel kann auch mit dem Attribut **internal** definiert werden.

Beispiel:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

In diesem Beispiel geben wir unseren eigenen Primärschlüssel &quot;budgetId&quot;an, anstatt das Attribut **@autopk** einen Standardschlüssel mit dem Namen &quot;id&quot;erstellen zu lassen.

>[!IMPORTANT]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselsequenz (@pkSequence) beibehalten.

Weitere Informationen zu Schlüsseln finden Sie im Abschnitt [Verwaltung von Schlüsseln](../../configuration/using/database-mapping.md#management-of-keys) .

## Attribute (Felder) {#attributes--fields-}

Mit Attributen können Sie die Felder definieren, aus denen Ihr Datenobjekt besteht. Klicken Sie in der Symbolleiste zur Schemabearbeitung auf **[!UICONTROL Einfügen]**, um leere Attributvorlagen an der Stelle in Ihrer XML abzulegen, an der sich Ihr Cursor befindet. Weitere Informationen hierzu finden Sie im Abschnitt [Datenschemata](../../configuration/using/data-schemas.md) .

![](assets/schemaextension_getting_started_2.png)

Die vollständige Liste der Attribute ist im Abschnitt [`<attribute>` element](../../configuration/using/schema/attribute.md) verfügbar. Im Folgenden finden Sie einige der am häufigsten verwendeten Attribute:

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

  Eine Tabelle mit den Zuordnungen der von Adobe Campaign für die verschiedenen Datenbankverwaltungssysteme generierten Datentypen finden Sie im Abschnitt [Zuordnen der Datentypen von Adobe Campaign/DBMS](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) .

Weiterführende Informationen zu den einzelnen Attributen finden Sie im Abschnitt [Attributbeschreibung](../../configuration/using/schema/attribute.md) .

### Beispiele {#examples}

Beispiel für die Definition eines Standardwerts:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Beispiel für die Verwendung eines allgemeinen Attributs als Vorlage für ein Feld, das ebenfalls als obligatorisch gekennzeichnet ist:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Beispiel eines berechneten Felds, das mit dem Attribut **@advanced** ausgeblendet wird:

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Beispiel für ein XML-Feld, das ebenfalls in einem SQL-Feld gespeichert ist und ein **@dataPolicy**-Attribut aufweist.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Die meisten Attribute sind zwar mittels 1-1-Kardinalität mit einem physischen Feld der Datenbank verknüpft. Bei den XML-Feldern oder den berechneten Feldern ist dies jedoch nicht der Fall.\
>Ein XML-Feld wird in einem Memo-Feld (&quot;mData&quot;) der Tabelle gespeichert.\
>Es wird jedoch beim Start jeder Abfrage dynamisch ein berechnetes Feld erstellt, sodass dieses auf Anwendungsebene vorhanden ist.

## Relationen {#links}

Relationen gehören zu den letzten Elementen im Hauptelement Ihres Schemas. Sie definieren, wie die verschiedenen Schemata in Ihrer Instanz miteinander in Beziehung stehen.

Relationen werden in dem Schema deklariert, das den **Fremdschlüssel** der Tabelle enthält, mit der sie verknüpft sind.

Es gibt drei Arten von Kardinalität: 1-1, 1-N und N-N. Standardmäßig wird der Typ 1-N verwendet.

### Beispiele {#examples-1}

Beispiel für eine 1-N-Relation zwischen der Empfängertabelle (vordefiniertes Schema) und einer Tabelle mit benutzerdefinierten Transaktionen:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Beispiel für eine 1-1-Relation zwischen einem benutzerspezifischen Schema &quot;Car&quot; (im Namespace &quot;cus&quot;) und der Empfängertabelle:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Beispiel für eine externe Relation zwischen der Empfängertabelle und einer Tabelle mit Adressen, die auf der E-Mail-Adresse anstatt auf dem Primärschlüssel basiert:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Hier entspricht &quot;xpath-dst&quot; dem Primärschlüssel im Zielgruppenschema und &quot;xpath-src&quot; dem Fremdschlüssel im Quellschema.

## Audit-Protokoll {#audit-trail}

Es kann sich als nützlich erweisen, am Ende Ihres Schemas ein Tracking-Element hinzuzufügen (für das Audit-Protokoll).

Gehen Sie wie im nachfolgenden Beispiel vor, um Felder mit Bezug auf das Erstellungsdatum, den Benutzer, der die Daten erstellt hat, das Datum und den Autor der letzten Änderung für alle Daten in Ihrer Tabelle einzubeziehen:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Datenbankstruktur aktualisieren {#updating-the-database-structure}

Sobald Ihre Änderungen abgeschlossen und gespeichert sind, müssen alle Änderungen, die sich auf die SQL-Struktur auswirken können, auf die Datenbank angewendet werden. Verwenden Sie dazu den Assistenten für das Datenbank-Update.

![](assets/schemaextension_getting_started_3.png)

Weiterführende Informationen finden Sie im Abschnitt [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).

>[!NOTE]
>
>Wenn Änderungen sich nicht auf die Datenbankstruktur auswirken, müssen Sie nur die Schemata neu erstellen. Wählen Sie dazu das zu aktualisierende(n) Schema(e) aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie **[!UICONTROL Aktionen > Ausgewählte Schemas regenerieren...]** . Weitere Informationen hierzu finden Sie im Abschnitt [Regenerating schemas](../../configuration/using/regenerating-schemas.md) .
