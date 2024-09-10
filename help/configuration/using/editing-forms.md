---
product: campaign
title: Bearbeiten von Formularen
description: Bearbeiten von Formularen
feature: Configuration
role: Data Engineer, Developer
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1736'
ht-degree: 3%

---


# Bearbeiten von Formularen{#editing-forms}

## Übersicht

Marketer und Benutzer verwenden Eingabeformulare, um Datensätze zu erstellen, zu ändern und in der Vorschau anzuzeigen. Forms zeigt eine visuelle Darstellung von Informationen an.

Sie können Eingabeformulare erstellen und ändern:

* Sie können die werkseitigen Eingabeformulare ändern, die standardmäßig bereitgestellt werden. Die werkseitigen Eingabeformulare basieren auf den werkseitigen Datenschemata.
* Sie können benutzerdefinierte Eingabeformulare erstellen, die auf von Ihnen definierten Datenschemata basieren.

Forms sind Entitäten vom Typ &quot;`xtk:form`&quot;. Sie können die Struktur des Eingabeformulars im Schema `xtk:form` anzeigen. Um dieses Schema anzuzeigen, wählen Sie **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** aus dem Menü. Weitere Informationen zu [Formularstruktur](form-structure.md).

Um auf Eingabeformulare zuzugreifen, wählen Sie **[!UICONTROL Administration] > [!UICONTROL Konfiguration] > [!UICONTROL Formulare]** aus dem Menü:

![](assets/d_ncs_integration_form_arbo.png)

Um Formulare zu entwerfen, bearbeiten Sie den XML-Inhalt im XML-Editor:

![](assets/d_ncs_integration_form_edit.png)

[Weitere Informationen](form-structure.md#formatting)

Um eine Vorschau eines Formulars anzuzeigen, klicken Sie auf die Registerkarte **[!UICONTROL Vorschau]**:

![](assets/d_ncs_integration_form_preview.png)

## Formulartypen

Sie können verschiedene Arten von Eingabeformularen erstellen. Der Formulartyp bestimmt, wie Benutzer im Formular navigieren:

* Konsolen-Bildschirm

  Dies ist der Standardformulartyp. Das Formular besteht aus einer einzelnen Seite.

  ![](assets/console_screen_form.png)

* Content-Management

  Verwenden Sie diesen Formulartyp für das Content Management. Siehe diesen [Anwendungsfall](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistent

  Dieses Formular umfasst mehrere schwebende Bildschirme, die in einer bestimmten Sequenz angeordnet sind. Benutzer navigieren von einem Bildschirm zum nächsten. [Weitere Informationen](form-structure.md#wizards)

* Iconbox

  Dieses Formular umfasst mehrere Seiten. Um durch das Formular zu navigieren, wählen Benutzer auf der linken Seite des Formulars Symbole aus.

  ![](assets/iconbox_form_preview.png)

* Notebook

  Dieses Formular umfasst mehrere Seiten. Um durch das Formular zu navigieren, wählen Benutzer Registerkarten oben im Formular aus.

  ![](assets/notebook_form_preview.png)

* Vertikale Trennung

  Dieses Formular zeigt eine Navigationsstruktur.

* Horizontale Trennung

  Dieses Formular zeigt eine Liste von Elementen an.

## Container

In Formularen können Sie Container für verschiedene Zwecke verwenden:

* Organisieren von Inhalten in Formularen
* Zugriff auf Eingabefelder definieren
* Verschachteln von Formularen in anderen Formularen

[Weitere Informationen](form-structure.md#containers)

### Inhalt organisieren

Verwenden Sie Container zum Organisieren von Inhalten in Formularen:

* Sie können Felder in Abschnitten gruppieren.
* Sie können mehrseitigen Formularen Seiten hinzufügen.

Verwenden Sie zum Einfügen eines Containers das Element `<container>` . [Weitere Informationen](form-structure.md#containers)

#### Gruppenfelder

Verwenden Sie Container, um Eingabefelder in organisierte Abschnitte zu gruppieren.

Verwenden Sie das folgende Element, um einen Abschnitt in ein Formular einzufügen: `<container type="frame">`. Wenn Sie optional einen Abschnittstitel hinzufügen möchten, verwenden Sie das Attribut `label` .

Syntax: `<container type="frame" label="`*section_title*`"> […] </container>`

In diesem Beispiel definiert ein Container den Abschnitt **Erstellung** , der die Eingabefelder **[!UICONTROL Erstellt von]** und **[!UICONTROL Name]** enthält:

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

Verwenden Sie für mehrseitige Formulare einen Container, um eine Formularseite zu erstellen.

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

Verwenden Sie Container, um zu definieren, was sichtbar ist, und um den Zugriff auf Felder zu definieren. Sie können Gruppen von Feldern aktivieren oder deaktivieren.

### Verschachteln von Formularen

Verwenden Sie Container zum Verschachteln von Formularen in anderen Formularen. [Weitere Informationen](#add-pages-to-multipage-forms)

## Verweise auf Bilder

Um Bilder zu suchen, wählen Sie **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Bilder]** aus dem Menü.

Um ein Bild mit einem Element im Formular zu verknüpfen, z. B. einem Symbol, können Sie einem Bild einen Verweis hinzufügen. Verwenden Sie beispielsweise das Attribut `img` im Element `<container>` .

Syntax: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Dieses Beispiel zeigt Verweise auf die Bilder `book.png` und `detail.png` aus dem Namespace `ncm` :

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
1. Klicken Sie oben rechts in der Liste auf die Schaltfläche **[!UICONTROL Neu]** .

   ![](assets/input-form-create-1.png)

1. Geben Sie die Formulareigenschaften an:

   * Geben Sie den Formularnamen und den Namespace an.

     Der Formularname und der Namespace können mit dem zugehörigen Datenschema übereinstimmen.  Dieses Beispiel zeigt ein Formular für das Datenschema `cus:order` :

     ```xml
     <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
       […]
     </form>
     ```

     Alternativ können Sie das Datenschema explizit im Attribut `entity-schema` angeben.

     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Geben Sie den Titel an, der im Formular angezeigt werden soll.
   * Geben Sie optional den Formulartyp an. Wenn Sie keinen Formulartyp angeben, wird standardmäßig der Konsolenbildschirmtyp verwendet.

     ![](assets/input-form-create-2.png)

     Wenn Sie ein mehrseitiges Formular entwerfen, können Sie den Formulartyp im Element `<form>` auslassen und den Typ in einem Container angeben.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Fügen Sie die Formularelemente ein.

   Verwenden Sie beispielsweise das Element `<input>` , um ein Eingabefeld einzufügen. Setzen Sie das Attribut `xpath` auf die Feldreferenz als XPath-Ausdruck. [Weitere Informationen](schema-structure.md#referencing-with-xpath)

   Dieses Beispiel zeigt Eingabefelder basierend auf dem Schema `nms:recipient` .

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Wenn das Formular auf einem bestimmten Schematyp basiert, können Sie die Felder für dieses Schema nachschlagen:

   1. Klicken Sie auf **[!UICONTROL Einfügen]** > **[!UICONTROL Dokumentfelder]**.

      ![](assets/input-form-create-4.png)

   1. Wählen Sie das Feld aus und klicken Sie auf **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Geben Sie optional den Feld-Editor an.

   Jedem Datentyp ist ein standardmäßiger Feldeditor zugeordnet:
   * Bei einem Feld vom Typ Datum zeigt das Formular einen Eingabekalender an.
   * Bei einem Auflistungsfeld zeigt das Formular eine Auswahlliste an.

   Sie können die folgenden Editor-Typen für Felder verwenden:

   | Feld-Editor | Formularattribut |
   | --- | --- |
   | Radiobutton | `type="radiobutton"` |
   | Kontrollkästchen | `type="checkbox"` |
   | Bearbeitungsstruktur | `type="tree"` |

   Weitere Informationen zu [Speicherlistensteuerelementen](form-structure.md#memory-list-controls).

1. Definieren Sie optional den Zugriff auf die Felder:

   | Element | Attribut | Beschreibung |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Ermöglicht schreibgeschützten Zugriff auf ein Feld |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Zeigt eine Feldergruppe bedingt an |
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

## Mehrseitige Formulare erstellen {#create-multipage-form}

Sie können mehrseitige Formulare erstellen. Sie können Formulare auch in anderen Formularen verschachteln.

### Erstellen eines `iconbox` Formulars

Verwenden Sie den Formulartyp &quot;`iconbox`&quot;, um auf der linken Seite des Formulars Symbole anzuzeigen, über die Benutzer zu verschiedenen Seiten im Formular gelangen.

![](assets/iconbox_form_preview.png)

Gehen Sie wie folgt vor, um den Typ eines vorhandenen Formulars in `iconbox` zu ändern:

1. Ändern Sie das Attribut `type` des Elements `<form>` in `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Legen Sie für jede Formularseite einen Container fest:

   1. Fügen Sie ein Element `<container>` als untergeordnetes Element des Elements `<form>` hinzu.
   1. Verwenden Sie die Attribute `label` und `img` , um eine Beschriftung und ein Bild für das Symbol zu definieren.

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

   Alternativ können Sie das Attribut `type="frame"` aus den vorhandenen `<container>` -Elementen entfernen.

### Notebook-Formular erstellen

Verwenden Sie den Formulartyp &quot;`notebook`&quot;, um Registerkarten oben im Formular anzuzeigen, über die Benutzer zu verschiedenen Seiten gelangen.

![](assets/notebook_form_preview.png)

Gehen Sie wie folgt vor, um den Typ eines vorhandenen Formulars in `notebook` zu ändern:

1. Ändern Sie das Attribut `type` des Elements `<form>` in `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Fügen Sie für jede Formularseite einen Container hinzu:

   1. Fügen Sie ein Element `<container>` als untergeordnetes Element des Elements `<form>` hinzu.
   1. Verwenden Sie die Attribute `label` und `img` , um den Titel und das Bild für das Symbol zu definieren.

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

   Alternativ können Sie das Attribut `type="frame"` aus den vorhandenen `<container>` -Elementen entfernen.

### Verschachteln von Formularen

Sie können Formulare in anderen Formularen verschachteln. Sie können beispielsweise Notebook-Formulare in iconbox-Formularen verschachteln.

Die Ebene der Verschachtelung steuert die Navigation. Benutzer können ein Drilldown zu Teilformularen durchführen.

Um ein Formular in einem anderen Formular zu verschachteln, fügen Sie ein Element `<container>` ein und legen Sie das Attribut `type` auf den Formulartyp fest. Für Formulare der obersten Ebene können Sie den Formulartyp in einem äußeren Container oder im Element `<form>` festlegen.

### Beispiel

Dieses Beispiel zeigt ein komplexes Formular:

* Das Formular der obersten Ebene ist ein Iconbox-Formular. Dieses Formular umfasst zwei Container mit den Bezeichnungen **Allgemein** und **Details**.

  Daher zeigt das äußere Formular die Seiten **Allgemein** und **Details** auf der obersten Ebene. Um auf diese Seiten zuzugreifen, klicken Benutzer auf die Symbole links im Formular.

* Das Teilformular ist ein Notebook-Formular, das im Container **Allgemein** verschachtelt ist. Das Teilformular umfasst zwei Container mit den Bezeichnungen **Name** und **Kontakt**.

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

Um ein Formular in einem anderen Formular zu verschachteln, fügen Sie ein Element `<container>` ein und legen Sie das Attribut `type` auf den Formulartyp fest. Für Formulare der obersten Ebene können Sie den Formulartyp in einem äußeren Container oder im Element `<form>` festlegen.

### Beispiel

Dieses Beispiel zeigt ein komplexes Formular:

* Das Formular der obersten Ebene ist ein Iconbox-Formular. Dieses Formular umfasst zwei Container mit den Bezeichnungen **Allgemein** und **Details**.

  Daher zeigt das äußere Formular die Seiten **Allgemein** und **Details** auf der obersten Ebene. Um auf diese Seiten zuzugreifen, klicken Benutzer auf die Symbole links im Formular.

* Das Teilformular ist ein Notebook-Formular, das im Container **Allgemein** verschachtelt ist. Das Teilformular umfasst zwei Container mit den Bezeichnungen **Name** und **Kontakt**.

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



## Fabrikeingabeformular ändern {#modify-factory-form}

Gehen Sie wie folgt vor, um ein Factory-Formular zu ändern:

1. Ändern Sie das Factory-Eingabeformular:

   1. Wählen Sie im Menü **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Formulare]**.
   1. Wählen Sie ein Formular aus und ändern Sie es.

   Sie können Factory-Datenschemata erweitern, Sie können jedoch keine Factory-Eingabeformulare erweitern. Es wird empfohlen, werksmäßige Eingabeformulare direkt zu ändern, ohne sie neu zu erstellen. Bei Softwareaktualisierungen werden Ihre Änderungen in den Werkseingangsformularen mit den Upgrades zusammengeführt. Wenn die automatische Zusammenführung fehlschlägt, können Sie die Konflikte lösen. [Weitere Informationen](../../production/using/upgrading.md#resolving-conflicts)

   Wenn Sie beispielsweise ein Factory-Schema mit einem zusätzlichen Feld erweitern, können Sie dieses Feld zum zugehörigen Factory-Formular hinzufügen.

## Formulare überprüfen {#validate-forms}

Sie können Überprüfungssteuerelemente in Formulare aufnehmen.

### Schreibgeschützten Zugriff auf Felder gewähren

Verwenden Sie das Attribut `readOnly="true"` , um schreibgeschützten Zugriff auf ein Feld zu gewähren. Beispielsweise können Sie den Primärschlüssel eines Datensatzes anzeigen, jedoch mit schreibgeschütztem Zugriff. [Weitere Informationen](form-structure.md#non-editable-fields)

In diesem Beispiel wird der Primärschlüssel (`iRecipientId`) des Schemas `nms:recipient` schreibgeschützt angezeigt:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Pflichtfelder aktivieren

Sie können obligatorische Informationen überprüfen:

* Verwenden Sie das Attribut `required="true"` für die erforderlichen Felder.
* Verwenden Sie den Knoten `<leave>` , um diese Felder zu überprüfen und Fehlermeldungen anzuzeigen.

In diesem Beispiel ist die E-Mail-Adresse erforderlich und es wird eine Fehlermeldung angezeigt, wenn der Benutzer diese Informationen nicht angegeben hat:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Weitere Informationen zu [Ausdrucksfeldern](form-structure.md#expression-field) und [Formularkontext](form-structure.md#context-of-forms).

### Werte überprüfen

Sie können JavaScript-SOAP-Aufrufe verwenden, um Formulardaten über die Konsole zu überprüfen. Verwenden Sie diese Aufrufe zur komplexen Validierung, um beispielsweise einen Wert mit einer Liste zulässiger Werte zu vergleichen. [Weitere Informationen](form-structure.md#soap-methods)

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

   In diesem Beispiel trägt die Funktion den Namen `checkValue`. Mit dieser Funktion wird der Datentyp `recipient` im Namespace `nms` überprüft. Der Wert, der überprüft wird, wird protokolliert. Wenn der Wert nicht gültig ist, wird eine Fehlermeldung protokolliert. Wenn der Wert gültig ist, wird der Wert 1 zurückgegeben.

   Sie können den zurückgegebenen Wert verwenden, um das Formular zu ändern.

1. Fügen Sie im Formular das Element `<soapCall>` zum Element `<leave>` hinzu.

   In diesem Beispiel wird ein SOAP-Aufruf verwendet, um die `@valueToCheck` -Zeichenfolge zu validieren:

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

   In diesem Beispiel werden die Methode `checkValue` und der Dienst `nms:recipient` verwendet:

   * Der Dienst ist der Namespace und der Datentyp.
   * Die Methode ist der Funktionsname. Beim Namen wird zwischen Groß- und Kleinschreibung unterschieden.

   Der Aufruf wird synchron ausgeführt.

   Alle Ausnahmen werden angezeigt. Wenn Sie das Element `<leave>` verwenden, können Benutzer das Formular erst speichern, wenn die eingegebenen Informationen validiert wurden.

Dieses Beispiel zeigt, wie Sie Dienstaufrufe in Formularen durchführen können:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

In diesem Beispiel ist die Eingabe eine ID, die ein Primärschlüssel ist. Wenn Benutzer das Formular für diese ID ausfüllen, wird SOAP mit dieser ID als Eingabeparameter aufgerufen. Die Ausgabe ist ein boolescher Wert, der in dieses Feld geschrieben wird: `/tmp/@count`. Sie können diesen booleschen Wert innerhalb des Formulars verwenden. Weitere Informationen zu [Formularkontext](form-structure.md#context-of-forms).
