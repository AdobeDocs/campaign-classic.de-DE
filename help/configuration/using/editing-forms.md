---
product: campaign
title: Bearbeiten von Formularen
description: Bearbeiten von Formularen
feature: Configuration
role: Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '1736'
ht-degree: 3%

---


# Bearbeiten von Formularen{#editing-forms}

## Übersicht

Marketer und Operatoren verwenden Eingabeformulare, um Datensätze zu erstellen, zu ändern und in der Vorschau anzuzeigen. Forms zeigt eine visuelle Darstellung von Informationen an.

Sie können Formulare erstellen und ändern:

* Sie können die werkseitigen Eingabeformulare ändern, die standardmäßig bereitgestellt werden. Die werkseitigen Eingabeformulare basieren auf den werkseitigen Datenschemata.
* Sie können benutzerdefinierte Eingabeformulare erstellen, die auf von Ihnen definierten Datenschemata basieren.

Forms sind Entitäten `xtk:form` Typs. Sie können die Struktur des Eingabeformulars im `xtk:form`-Schema anzeigen. Um dieses Schema anzuzeigen, wählen Sie **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** aus dem Menü aus. Weitere Informationen über [Formularstruktur](form-structure.md).

Um auf Eingabeformulare zuzugreifen, wählen Sie **[!UICONTROL Administration] > [!UICONTROL Konfiguration] > [!UICONTROL Eingabeformulare]** aus dem Menü:

![](assets/d_ncs_integration_form_arbo.png)

Um Formulare zu entwerfen, bearbeiten Sie den XML-Inhalt im XML-Editor:

![](assets/d_ncs_integration_form_edit.png)

[Weitere Informationen](form-structure.md#formatting)

Um ein Formular in der Vorschau anzuzeigen, klicken Sie auf die **[!UICONTROL Vorschau]**:

![](assets/d_ncs_integration_form_preview.png)

## Formulartypen

Sie können verschiedene Arten von Eingabeformularen erstellen. Der Formulartyp bestimmt, wie Benutzer im Formular navigieren:

* Konsolen-Bildschirm

  Dies ist der Standardformulartyp. Das Formular besteht aus einer einzelnen Seite.

  ![](assets/console_screen_form.png)

* Content-Management

  Verwenden Sie diesen Formulartyp für das Content-Management. Siehe diesen [Anwendungsfall](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistent

  Dieses Formular umfasst mehrere unverankerte Bildschirme, die in einer bestimmten Reihenfolge angeordnet sind. Benutzer navigieren von einem Bildschirm zum nächsten. [Weitere Informationen](form-structure.md#wizards)

* Iconbox

  Dieses Formular umfasst mehrere Seiten. Um im Formular zu navigieren, klicken Benutzer auf die Symbole links neben dem Formular.

  ![](assets/iconbox_form_preview.png)

* Notebook

  Dieses Formular umfasst mehrere Seiten. Um im Formular zu navigieren, wählen Benutzer Registerkarten oben im Formular aus.

  ![](assets/notebook_form_preview.png)

* Vertikale Trennung

  Dieses Formular zeigt einen Navigationsbaum an.

* Horizontale Trennung

  Dieses Formular zeigt eine Liste von Elementen an.

## Container

In Formularen können Sie Container für verschiedene Zwecke verwenden:

* Organisieren von Inhalten in Formularen
* Definieren des Zugriffs auf Eingabefelder
* Verschachteln von Formularen in anderen Formularen

[Weitere Informationen](form-structure.md#containers)

### Inhalt organisieren

Verwenden von Containern zum Organisieren von Inhalten in Formularen:

* Sie können Felder in Abschnitten gruppieren.
* Sie können Seiten zu mehrseitigen Formularen hinzufügen.

Verwenden Sie zum Einfügen eines Containers das `<container>`. [Weitere Informationen](form-structure.md#containers)

#### Felder gruppieren

Verwenden Sie Container, um Eingabefelder in strukturierte Abschnitte zu gruppieren.

Um einen Abschnitt in ein Formular einzufügen, verwenden Sie dieses Element: `<container type="frame">`. Um optional einen Abschnittstitel hinzuzufügen, verwenden Sie das Attribut `label` .

Syntax: `<container type="frame" label="`*section_title*`"> […] </container>`

In diesem Beispiel definiert ein Container den Abschnitt **Erstellung**, der die Eingabefelder **[!UICONTROL Erstellt von]** und **[!UICONTROL Name]** umfasst:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Hinzufügen von Seiten zu mehrseitigen Formularen

Verwenden Sie für mehrseitige Formulare einen Container , um eine Formularseite zu erstellen.

Dieses Beispiel zeigt Container für die Seiten **Allgemein** und **Details** eines Formulars:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Zugriff auf Felder definieren

Verwenden Sie Container, um zu definieren, was sichtbar ist, und um den Zugriff auf Felder zu definieren. Sie können Feldergruppen aktivieren oder deaktivieren.

### Verschachteln von Formularen

Verwenden Sie Container, um Formulare in anderen Formularen zu verschachteln. [Weitere Informationen](#add-pages-to-multipage-forms)

## Verweise auf Bilder

Um Bilder zu finden, wählen Sie **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Bilder]** aus dem Menü aus.

Um ein Bild mit einem Element im Formular zu verknüpfen, z. B. mit einem Symbol, können Sie einen Verweis auf ein Bild hinzufügen. Verwenden Sie das `img`-Attribut beispielsweise im `<container>`.

Syntax: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Dieses Beispiel zeigt Verweise auf die `book.png` und `detail.png` Bilder aus dem `ncm` Namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Diese Bilder werden für Symbole verwendet, auf die Benutzer klicken, um in einem mehrseitigen Formular zu navigieren:

![](assets/nested_forms_preview.png)


## Einfaches Formular erstellen {#create-simple-form}

Gehen Sie wie folgt vor, um ein Formular zu erstellen:

1. Wählen Sie im Menü **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Formulare]**.
1. Klicken Sie **[!UICONTROL oben rechts in]** Liste auf „Neu“.

   ![](assets/input-form-create-1.png)

1. Geben Sie die Formulareigenschaften an:

   * Geben Sie den Formularnamen und den Namespace an.

     Der Formularname und der Namespace können mit dem zugehörigen Datenschema übereinstimmen.  Dieses Beispiel zeigt ein Formular für das `cus:order` Datenschema:

     ```xml
     <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
       […]
     </form>
     ```

     Alternativ können Sie das Datenschema explizit im `entity-schema` angeben.

     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Geben Sie den Titel an, der auf dem Formular angezeigt werden soll.
   * Geben Sie optional den Formulartyp an. Wenn Sie keinen Formulartyp angeben, wird standardmäßig der Konsolenbildschirmtyp verwendet.

     ![](assets/input-form-create-2.png)

     Wenn Sie ein mehrseitiges Formular entwerfen, können Sie den Formulartyp im `<form>` auslassen und den Typ in einem Container angeben.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Fügen Sie die Formularelemente ein.

   Um beispielsweise ein Eingabefeld einzufügen, verwenden Sie das `<input>`. Legen Sie das `xpath`-Attribut als XPath-Ausdruck auf den Feldverweis fest. [Weitere Informationen](schema-structure.md#referencing-with-xpath)

   Dieses Beispiel zeigt Eingabefelder, die auf dem `nms:recipient` basieren.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Wenn das Formular auf einem bestimmten Schematyp basiert, können Sie die Felder für dieses Schema nachschlagen:

   1. Klicken Sie **[!UICONTROL Einfügen]** > **[!UICONTROL Dokumentfelder]**.

      ![](assets/input-form-create-4.png)

   1. Wählen Sie das Feld aus und klicken Sie auf **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Geben Sie optional den Feldeditor an.

   Jedem Datentyp ist ein Standardeditor für Felder zugeordnet:
   * Für ein Feld vom Typ Datum zeigt das Formular einen Eingabekalender an.
   * Für ein Feld vom Typ Auflistung zeigt das Formular eine Auswahlliste an.

   Sie können die folgenden Typen von Feldeditoren verwenden:

   | Feld-Editor | Formularattribut |
   | --- | --- |
   | Optionsfeld | `type="radiobutton"` |
   | Kontrollkästchen | `type="checkbox"` |
   | Baum bearbeiten | `type="tree"` |

   Lesen Sie mehr über [Eingabefeld mit Speicherliste](form-structure.md#memory-list-controls).

1. Definieren Sie optional den Zugriff auf die Felder:

   | Element | Attribut | Beschreibung |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Bietet schreibgeschützten Zugriff auf ein Feld |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Zeigt bedingt eine Gruppe von Feldern an |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | Bedingte Aktivierung einer Feldergruppe |

   Beispiel:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. Verwenden Sie optional Container, um Felder in Abschnitte zu gruppieren.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Erstellen eines mehrseitigen Formulars {#create-multipage-form}

Sie können mehrseitige Formulare erstellen. Sie können Formulare auch in anderen Formularen verschachteln.

### Erstellen eines `iconbox` Formulars

Verwenden Sie den `iconbox` Formulartyp, um Symbole auf der linken Seite des Formulars anzuzeigen, über die Benutzende zu verschiedenen Seiten im Formular gelangen.

![](assets/iconbox_form_preview.png)

Gehen Sie wie folgt vor, um den Typ eines vorhandenen Formulars in `iconbox` zu ändern:

1. Ändern Sie das `type` des `<form>` Elements in `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Legen Sie einen Container für jede Formularseite fest:

   1. Fügen Sie ein `<container>` Element als untergeordnetes Element des `<form>` Elements hinzu.
   1. Um eine Beschriftung und ein Bild für das Symbol zu definieren, verwenden Sie die Attribute `label` und `img` .

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```

   Alternativ können Sie das `type="frame"`-Attribut aus den vorhandenen `<container>` entfernen.

### Notebook-Formular erstellen

Verwenden Sie den `notebook` Formulartyp, um Registerkarten oben im Formular anzuzeigen, über die Benutzende zu verschiedenen Seiten gelangen.

![](assets/notebook_form_preview.png)

Gehen Sie wie folgt vor, um den Typ eines vorhandenen Formulars in `notebook` zu ändern:

1. Ändern Sie das `type` des `<form>` Elements in `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Fügen Sie für jede Formularseite einen Container hinzu:

   1. Fügen Sie ein `<container>` Element als untergeordnetes Element des `<form>` Elements hinzu.
   1. Um die Beschriftung und das Bild für das Symbol zu definieren, verwenden Sie die Attribute `label` und `img` .

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   Alternativ können Sie das `type="frame"`-Attribut aus den vorhandenen `<container>` entfernen.

### Verschachteln von Formularen

Sie können Formulare in anderen Formularen verschachteln. Sie können beispielsweise Notebook-Formulare in iconbox-Formularen verschachteln.

Die Verschachtelungsebene steuert die Navigation. Benutzer können einen Drilldown in Teilformulare durchführen.

Um ein Formular in einem anderen Formular zu verschachteln, fügen Sie ein `<container>` ein und legen Sie das Attribut `type` auf den Formulartyp fest. Für das Formular der obersten Ebene können Sie den Formulartyp in einem äußeren Container oder im `<form>` festlegen.

### Beispiel

Dieses Beispiel zeigt ein komplexes Formular:

* Das Formular der obersten Ebene ist ein Formular für Symbolboxen. Dieses Formular enthält zwei Container mit der Beschriftung **Allgemein** und **Details**.

  Daher zeigt das äußere Formular die Seiten **Allgemein** und **Details** auf der obersten Ebene an. Um auf diese Seiten zuzugreifen, klicken Benutzer auf die Symbole links im Formular.

* Das Teilformular ist ein Notebook-Formular, das im Container **Allgemein** verschachtelt ist. Das Teilformular besteht aus zwei Containern mit der Beschriftung **Name** und **Kontakt**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Daher werden auf der Seite **Allgemein** des äußeren Formulars die Registerkarten **Name** und **Kontakt** angezeigt.

![](assets/nested_forms_preview.png)

Um ein Formular in einem anderen Formular zu verschachteln, fügen Sie ein `<container>` ein und legen Sie das Attribut `type` auf den Formulartyp fest. Für das Formular der obersten Ebene können Sie den Formulartyp in einem äußeren Container oder im `<form>` festlegen.

### Beispiel

Dieses Beispiel zeigt ein komplexes Formular:

* Das Formular der obersten Ebene ist ein Formular für Symbolboxen. Dieses Formular enthält zwei Container mit der Beschriftung **Allgemein** und **Details**.

  Daher zeigt das äußere Formular die Seiten **Allgemein** und **Details** auf der obersten Ebene an. Um auf diese Seiten zuzugreifen, klicken Benutzer auf die Symbole links im Formular.

* Das Teilformular ist ein Notebook-Formular, das im Container **Allgemein** verschachtelt ist. Das Teilformular besteht aus zwei Containern mit der Beschriftung **Name** und **Kontakt**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Daher werden auf der Seite **Allgemein** des äußeren Formulars die Registerkarten **Name** und **Kontakt** angezeigt.

![](assets/nested_forms_preview.png)



## Ändern eines werkseitigen Eingabeformulars {#modify-factory-form}

Gehen Sie wie folgt vor, um ein Factory-Formular zu ändern:

1. Ändern des werkseitigen Eingabeformulars:

   1. Wählen Sie im Menü **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Formulare]**.
   1. Wählen Sie ein Eingabeformular aus und ändern Sie es.

   Sie können Factory-Datenschemata erweitern, aber nicht Factory-Eingabeformulare. Es wird empfohlen, die werkseitigen Eingabeformulare direkt zu ändern, ohne sie neu zu erstellen. Bei Software-Upgrades werden Ihre Änderungen in den werkseitigen Eingabeformularen mit den Upgrades zusammengeführt. Wenn die automatische Zusammenführung fehlschlägt, können Sie die Konflikte auflösen. [Weitere Informationen](../../production/using/upgrading.md#resolving-conflicts)

   Wenn Sie beispielsweise ein Factory-Schema mit einem zusätzlichen Feld erweitern, können Sie dieses Feld dem zugehörigen Factory-Formular hinzufügen.

## Formulare validieren {#validate-forms}

Sie können Validierungssteuerelemente in Formulare einbeziehen.

### Nur-Lese-Zugriff auf Felder gewähren

Um schreibgeschützten Zugriff auf ein Feld zu gewähren, verwenden Sie das Attribut `readOnly="true"` . Beispiel: Sie möchten den Primärschlüssel eines Datensatzes anzeigen, jedoch mit schreibgeschütztem Zugriff. [Weitere Informationen](form-structure.md#non-editable-fields)

In diesem Beispiel wird der Primärschlüssel (`iRecipientId`) des `nms:recipient` Schemas im schreibgeschützten Zugriff angezeigt:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Pflichtfelder überprüfen

Sie können die obligatorischen Informationen überprüfen:

* Verwenden Sie das Attribut `required="true"` für die erforderlichen Felder.
* Verwenden Sie den Knoten `<leave>` , um diese Felder zu überprüfen und Fehlermeldungen anzuzeigen.

In diesem Beispiel ist die E-Mail-Adresse erforderlich und eine Fehlermeldung wird angezeigt, wenn der Benutzer diese Informationen nicht bereitgestellt hat:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Lesen Sie mehr über [Ausdrucksfelder](form-structure.md#expression-field) und [Formularkontext](form-structure.md#context-of-forms).

### Validieren von Werten

Sie können JavaScript SOAP-Aufrufe verwenden, um Formulardaten in der Konsole zu überprüfen. Verwenden Sie diese Aufrufe für eine komplexe Validierung, z. B. um einen Wert mit einer Liste autorisierter Werte zu vergleichen. [Weitere Informationen](form-structure.md#soap-methods)

1. Erstellen Sie eine Validierungsfunktion in einer JS-Datei.

   Beispiel:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   In diesem Beispiel trägt die Funktion den Namen `checkValue`. Mit dieser Funktion wird der `recipient` Datentyp im `nms`-Namespace überprüft. Der zu überprüfende Wert wird protokolliert. Wenn der Wert ungültig ist, wird eine Fehlermeldung protokolliert. Wenn der Wert gültig ist, wird der Wert 1 zurückgegeben.

   Sie können den zurückgegebenen Wert verwenden, um das Formular zu ändern.

1. Fügen Sie im Formular das `<soapCall>` Element zum `<leave>` Element hinzu.

   In diesem Beispiel wird ein SOAP-Aufruf verwendet, um die `@valueToCheck` Zeichenfolge zu validieren:

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   In diesem Beispiel werden die `checkValue`-Methode und der `nms:recipient`-Service verwendet:

   * Der Service ist der Namespace und der Datentyp.
   * Die Methode ist der Funktionsname. Beim Namen wird zwischen Groß- und Kleinschreibung unterschieden.

   Der Aufruf erfolgt synchron.

   Alle Ausnahmen werden angezeigt. Wenn Sie das `<leave>` verwenden, können Benutzer das Formular erst speichern, nachdem die eingegebenen Informationen validiert wurden.

Dieses Beispiel zeigt, wie Sie Service-Aufrufe in Formularen durchführen können:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

In diesem Beispiel ist die Eingabe eine ID, bei der es sich um einen Primärschlüssel handelt. Wenn Benutzende das Formular für diese ID ausfüllen, wird ein SOAP-Aufruf mit dieser ID als Eingabeparameter durchgeführt. Die Ausgabe ist ein boolescher Wert, der in dieses Feld geschrieben wird: `/tmp/@count`. Sie können diesen booleschen Wert im Formular verwenden. Weitere Informationen über [Formularkontext](form-structure.md#context-of-forms).
