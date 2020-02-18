---
title: Informationen zur Schemaausgabe
seo-title: Informationen zur Schemaausgabe
description: Informationen zur Schemaausgabe
seo-description: null
page-status-flag: never-activated
uuid: edb4d47d-b507-4d86-9873-ebd5f6acefc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: d5b08e4e-060c-4185-9dac-af270918e2b9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Informationen zur Schemaausgabe{#about-schema-edition}

Adobe Campaign verwendet Datenschemata für:

* Definieren der Verknüpfung zwischen den Datenobjekten in der Anwendung mit den zugrunde liegenden Datenbanktabellen
* Definieren von Beziehungen zwischen den unterschiedlichen Datenobjekten in der Campaign-Anwendung
* Definieren und Beschreiben der einzelnen Felder eines jeden Objekts

Ein besseres Verständnis der integrierten Kampagnentabellen und ihrer Interaktion finden Sie im Datenmodell [Campaign Classic](https://helpx.adobe.com/campaign/kb/acc-datamodel.html).

## Erweitern oder Erstellen von Schemata {#extending-or-creating-schemas}

Um einem der Kerndatenschemata in Campaign ein Feld, einen Index oder ein anderes Element hinzuzufügen, z. B. die Empfängertabelle (nms:empfänger), müssen Sie dieses Schema erweitern. Weitere Informationen hierzu finden Sie im Abschnitt [Erweitern eines Schemas](../../configuration/using/extending-a-schema.md) .

Um einen völlig neuen Datentyp hinzuzufügen, der in Adobe Campaign nicht standardmäßig vorhanden ist (z. B. eine Tabelle mit Verträgen), können Sie direkt ein benutzerdefiniertes Schema erstellen. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_1.png)

Nachdem Sie ein Schema für die Verwendung erweitert oder erstellt haben, sollten Sie seine XML-Inhaltselemente in der Reihenfolge definieren, in der sie unten aufgeführt sind.

## Auflistungen {#enumerations}

Aufzählungen werden zuerst definiert, vor dem Hauptelement des Schemas. Sie ermöglichen es Ihnen, Werte in einer Liste anzuzeigen, um die Auswahl zu beschränken, die der Benutzer für ein bestimmtes Feld hat.

Beispiel:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Beim Definieren von Feldern können Sie diese Aufzählung wie folgt verwenden:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>Sie können auch benutzerdefinierte Aufzählungen verwenden (normalerweise unter **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ), um die Werte für ein bestimmtes Feld anzugeben. Dabei handelt es sich im Grunde um globale Aufzählungen und eine bessere Wahl, wenn Ihre Aufzählung außerhalb des spezifischen Schemas, in dem Sie arbeiten, verwendet werden kann.

Weitere Informationen zu Enumerationen finden Sie in den Abschnitten [Enumerations](../../configuration/using/schema-structure.md#enumerations) und [`<enumeration>` element](../../configuration/using/elements-and-attributes.md#enumeration--element) .

## Index {#index}

Indizes sind die ersten Elemente, die im Hauptelement des Schemas deklariert wurden.

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

Das **xpath** -Attribut verweist auf das Feld im Schema, das Sie indizieren möchten.

>[!IMPORTANT]
>
>Es ist wichtig zu bedenken, dass die Leistungssteigerungen der SQL-Abfrage beim Lesen von Datensätzen, die von Indizes bereitgestellt werden, auch mit einem Leistungsschlag beim Schreiben von Datensätzen einhergehen. Die Indizes sollten daher mit Vorsicht verwendet werden.

Weitere Informationen zu Indizes finden Sie im Abschnitt [Indizierte Felder](../../configuration/using/database-mapping.md#indexed-fields) .

## Keys {#keys}

Jede Tabelle muss über mindestens einen Schlüssel verfügen. Oft wird sie automatisch im Hauptelement des Schemas erstellt, indem das Attribut **@autopk=true** auf &quot;true&quot;gesetzt wird.

Der Primärschlüssel kann auch mithilfe des **internen** Attributs definiert werden.

Beispiel:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

In diesem Beispiel geben wir anstelle des Attributs **@autopk** einen standardmäßigen primären Schlüssel mit dem Namen &quot;id&quot;unseren eigenen primären Schlüssel &quot;budgetId&quot;an.

>[!IMPORTANT]
>
>Beim Anlegen eines neuen Schemas oder bei einer Schema-Erweiterung müssen Sie für das gesamte Schema den gleichen Wert für die Primärschlüsselfolge (@pkSequence) beibehalten.

Weitere Informationen zu Schlüsseln finden Sie im Abschnitt [Verwaltung von Schlüsseln](../../configuration/using/database-mapping.md#management-of-keys) .

## Attribute (Felder) {#attributes--fields-}

Mit Attributen können Sie die Felder definieren, aus denen Ihr Datenobjekt besteht. Sie können die **[!UICONTROL Insert]** Schaltfläche in der Symbolleiste der Schemaausgabe verwenden, um leere Attributvorlagen in Ihrer XML-Datei abzulegen, wo sich der Cursor befindet. For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_2.png)

Die vollständige Liste der Attribute ist im Abschnitt [`<attribute>` Element](../../configuration/using/elements-and-attributes.md#attribute--element) verfügbar. Im Folgenden finden Sie einige der gebräuchlichsten Attribute:

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
* **@Typ**

   Eine Tabelle mit den Zuordnungen der von Adobe Campaign für die verschiedenen Datenbankverwaltungssysteme generierten Datentypen finden Sie im Abschnitt [Zuordnen der Typen von Adobe Campaign-/DBMS-Daten](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) .

Weitere Informationen zu den einzelnen Attributen finden Sie im Abschnitt [Attributbeschreibung](../../configuration/using/elements-and-attributes.md#attribute-description) .

### Beispiele {#examples}

Beispiel für die Definition eines Standardwert:

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

Beispiel für ein XML-Feld, das auch in einem SQL-Feld gespeichert ist und das ein **@dataPolicy** -Attribut hat.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Obwohl die meisten Attribute gemäß einer 1-1-Kardinalität mit einem physischen Feld der Datenbank verknüpft sind, ist dies bei den XML-Feldern oder den berechneten Feldern nicht der Fall.\
>Ein XML-Feld wird in einem Memofeld (&quot;mData&quot;) der Tabelle gespeichert.\
>Ein berechnetes Feld wird jedoch bei jedem Starten einer Abfrage dynamisch erstellt und existiert daher nur in der Anwendungsebene.

## Relationen {#links}

Links sind einige der letzten Elemente im Hauptelement Ihres Schemas. Sie definieren, wie sich alle verschiedenen Schemata in Ihrer Instanz zueinander verhalten.

Links werden im Schema deklariert, das den **Fremdschlüssel** der Tabelle enthält, mit der sie verknüpft sind.

Es gibt drei Arten von Kardinalität: 1-1, 1-N und N-N. Es ist der 1-N-Typ, der standardmäßig verwendet wird.

### Beispiele {#examples-1}

Beispiel für eine 1-N-Verknüpfung zwischen der Empfängertabelle (vordefiniertes Schema) und einer Tabelle mit benutzerdefinierten Transaktionen:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Ein Beispiel für eine 1-1-Verknüpfung zwischen einem benutzerdefinierten Schema &quot;Auto&quot;(im Namespace &quot;cus&quot;) und der Empfängertabelle:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Beispiel für eine externe Verknüpfung zwischen der Empfängertabelle und einer Adresstabelle, die auf der E-Mail-Adresse und nicht einem Primärschlüssel basiert:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Hier entspricht &quot;xpath-dst&quot;dem primären Schlüssel im Zielschema und &quot;xpath-src&quot;dem Fremdschlüssel im Quellschema.

## Audit trail {#audit-trail}

Ein nützliches Element, das Sie am unteren Rand des Schemas einfügen möchten, ist ein Verfolgungselement (Audit-Protokoll).

Verwenden Sie das unten stehende Beispiel, um Felder mit Bezug auf das Erstellungsdatum, den Benutzer, der die Daten erstellt hat, das Datum und den Autor der letzten Änderung für alle Daten in Ihrer Tabelle einzuschließen:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Datenbankstruktur aktualisieren {#updating-the-database-structure}

Sobald Ihre Änderungen abgeschlossen und gespeichert sind, müssen alle Änderungen, die sich auf die SQL-Struktur auswirken können, auf die Datenbank angewendet werden. Verwenden Sie dazu den Datenbankaktualisierungsassistenten.

![](assets/schemaextension_getting_started_3.png)

Weiterführende Informationen finden Sie im Abschnitt [Datenbankstruktur aktualisieren](../../configuration/using/updating-the-database-structure.md).

>[!NOTE]
>
>Wenn Änderungen sich nicht auf die Datenbankstruktur auswirken, müssen Sie nur Schemata neu generieren. Wählen Sie dazu die zu aktualisierenden Schemata aus, klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Actions > Regenerate selected schemas...]** . For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

