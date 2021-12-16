---
product: campaign
title: Bearbeiten von Formularen
description: Bearbeiten von Formularen
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 2b7341bb7fd5ecd93ccc9abd27789a013fda37fa
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 3%

---


# Bearbeiten von Formularen{#editing-forms}

![](../../assets/common.svg)

## Überblick

Marketer und Benutzer verwenden Eingabeformulare, um Datensätze zu erstellen, zu ändern und in der Vorschau anzuzeigen. Forms zeigt eine visuelle Darstellung von Informationen an.

Sie können Eingabeformulare erstellen und ändern:

* Sie können die werkseitigen Eingabeformulare ändern, die standardmäßig bereitgestellt werden. Die werkseitigen Eingabeformulare basieren auf den werkseitigen Datenschemata.
* Sie können benutzerdefinierte Eingabeformulare erstellen, die auf von Ihnen definierten Datenschemata basieren.

Forms sind Entitäten von `xtk:form` Typ. Sie können die Struktur des Eingabeformulars im `xtk:form` Schema. Um dieses Schema anzuzeigen, wählen Sie **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** aus dem Menü. Mehr dazu [Formularstruktur](form-structure.md).

Um auf Eingabeformulare zuzugreifen, wählen Sie **[!UICONTROL Administration] > [!UICONTROL Konfiguration] > [!UICONTROL Formulare]** aus dem Menü:

![](assets/d_ncs_integration_form_arbo.png)

Um Formulare zu entwerfen, bearbeiten Sie den XML-Inhalt im XML-Editor:

![](assets/d_ncs_integration_form_edit.png)

[Mehr dazu](form-structure.md#formatting)

Klicken Sie auf die Schaltfläche **[!UICONTROL Vorschau]** tab:

![](assets/d_ncs_integration_form_preview.png)

## Formulartypen

Sie können verschiedene Arten von Eingabeformularen erstellen. Der Formulartyp bestimmt, wie Benutzer im Formular navigieren:

* Konsolenbildschirm

   Dies ist der Standardformulartyp. Das Formular besteht aus einer einzelnen Seite.

   ![](assets/console_screen_form.png)

* Content-Management

   Verwenden Sie diesen Formulartyp für das Content Management. Siehe dies [Anwendungsfall](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistent

   Dieses Formular umfasst mehrere schwebende Bildschirme, die in einer bestimmten Sequenz angeordnet sind. Benutzer navigieren von einem Bildschirm zum nächsten. [Mehr dazu](form-structure.md#wizards)

* Iconbox

   Dieses Formular umfasst mehrere Seiten. Um durch das Formular zu navigieren, wählen Benutzer auf der linken Seite des Formulars Symbole aus.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Dieses Formular umfasst mehrere Seiten. Um durch das Formular zu navigieren, wählen Benutzer Registerkarten oben im Formular aus.

   ![](assets/notebook_form_preview.png)

* Vertikaler Bereich

   Dieses Formular zeigt eine Navigationsstruktur.

* Horizontaler Bereich

   Dieses Formular zeigt eine Liste von Elementen an.

## Container

In Formularen können Sie Container für verschiedene Zwecke verwenden:

* Organisieren von Inhalten in Formularen
* Zugriff auf Eingabefelder definieren
* Verschachteln von Formularen in anderen Formularen

[Mehr dazu](form-structure.md#containers)

### Inhalt organisieren

Verwenden Sie Container zum Organisieren von Inhalten in Formularen:

* Sie können Felder in Abschnitten gruppieren.
* Sie können mehrseitigen Formularen Seiten hinzufügen.

Verwenden Sie zum Einfügen eines Containers die `<container>` -Element. [Mehr dazu](form-structure.md#containers)

#### Gruppenfelder

Verwenden Sie Container, um Eingabefelder in organisierte Abschnitte zu gruppieren.

Verwenden Sie dieses Element, um einen Abschnitt in ein Formular einzufügen: `<container type="frame">`. Wenn Sie optional einen Abschnittstitel hinzufügen möchten, verwenden Sie die `label` -Attribut.

Syntax: `<container type="frame" label="`*section_title*`"> […] </container>`

In diesem Beispiel definiert ein Container die **Erstellung** -Abschnitt, der die **[!UICONTROL Erstellt von]** und **[!UICONTROL Name]** Eingabefelder:

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

Dieses Beispiel zeigt Container für **Allgemein** und **Details** Seiten eines Formulars:

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

Verwenden Sie Container zum Verschachteln von Formularen in anderen Formularen. [Mehr dazu](#add-pages-to-multipage-forms)

## Verweise auf Bilder

Um Bilder zu suchen, wählen Sie **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Bilder]** aus dem Menü.

Um ein Bild mit einem Element im Formular zu verknüpfen, z. B. einem Symbol, können Sie einem Bild einen Verweis hinzufügen. Verwenden Sie die `img` -Attribut, beispielsweise im `<container>` -Element.

Syntax: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Dieses Beispiel zeigt Verweise auf die `book.png` und `detail.png` Bilder aus `ncm` namespace:

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
1. Klicken Sie auf **[!UICONTROL Neu]** rechts oben in der Liste.

   ![](assets/input-form-create-1.png)

1. Geben Sie die Formulareigenschaften an:

   * Geben Sie den Formularnamen und den Namespace an.

      Der Formularname und der Namespace können mit dem zugehörigen Datenschema übereinstimmen.  Dieses Beispiel zeigt ein Formular für die `cus:order` Datenschema:

      ```xml
      <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
        […]
      </form>
      ```

      Alternativ können Sie das Datenschema explizit im `entity-schema` -Attribut.

      ```xml
      <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
        […]
      </form>
      ```

   * Geben Sie den Titel an, der im Formular angezeigt werden soll.
   * Geben Sie optional den Formulartyp an. Wenn Sie keinen Formulartyp angeben, wird standardmäßig der Konsolenbildschirmtyp verwendet.

      ![](assets/input-form-create-2.png)

      Wenn Sie ein mehrseitiges Formular entwerfen, können Sie den Formulartyp im `<form>` -Element und geben Sie den Typ in einem Container an.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Fügen Sie die Formularelemente ein.

   Um beispielsweise ein Eingabefeld einzufügen, verwenden Sie die `<input>` -Element. Legen Sie die `xpath` -Attribut der Feldreferenz als XPath-Ausdruck zuweisen. [Mehr dazu](schema-structure.md#referencing-with-xpath)

   Dieses Beispiel zeigt Eingabefelder, die auf dem `nms:recipient` Schema.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Wenn das Formular auf einem bestimmten Schematyp basiert, können Sie die Felder für dieses Schema nachschlagen:

   1. Klicken **[!UICONTROL Einfügen]** > **[!UICONTROL Dokumentfelder]**.

      ![](assets/input-form-create-4.png)

   1. Wählen Sie das Feld aus und klicken Sie auf **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Geben Sie optional den Feld-Editor an.

   Jedem Datentyp ist ein standardmäßiger Feldeditor zugeordnet:
   * Bei einem Feld vom Typ Datum zeigt das Formular einen Eingabekalender an.
   * Bei einem Auflistungsfeld zeigt das Formular eine Auswahlliste an.

   Sie können die folgenden Editor-Typen für Felder verwenden:

   | Feldeditor | Formularattribut |
   | --- | --- |
   | Radiobutton | `type="radiobutton"` |
   | Checkbox | `type="checkbox"` |
   | Bearbeitungsstruktur | `type="tree"` |

   Mehr dazu [Speicherlistensteuerelemente](form-structure.md#memory-list-controls).

1. Definieren Sie optional den Zugriff auf die Felder:

   | Element | Attribut | Beschreibung |
   | --- | --- | --- |
   | `<input>` | `read-only:"true"` | Ermöglicht schreibgeschützten Zugriff auf ein Feld |
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

### Erstellen Sie eine `iconbox` Formular

Verwenden Sie die `iconbox` Formulartyp zum Anzeigen von Symbolen auf der linken Seite des Formulars, über die Benutzer zu verschiedenen Seiten im Formular gelangen.

![](assets/iconbox_form_preview.png)

So ändern Sie den Typ eines vorhandenen Formulars in `iconbox`führen Sie die folgenden Schritte aus:

1. Ändern Sie die `type` -Attribut `<form>` Element zu `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Legen Sie für jede Formularseite einen Container fest:

   1. Hinzufügen einer `<container>` -Element als untergeordnetes Element des `<form>` -Element.
   1. Um eine Beschriftung und ein Bild für das Symbol zu definieren, verwenden Sie die `label` und `img` -Attribute.

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
   Alternativ können Sie die `type="frame"` -Attribut aus dem vorhandenen `<container>` -Elemente.

### Notebook-Formular erstellen

Verwenden Sie die `notebook` Formulartyp zum Anzeigen von Registerkarten oben im Formular, über die Benutzer zu verschiedenen Seiten gelangen.

![](assets/notebook_form_preview.png)

So ändern Sie den Typ eines vorhandenen Formulars in `notebook`führen Sie die folgenden Schritte aus:

1. Ändern Sie die `type` -Attribut `<form>` Element zu `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Fügen Sie für jede Formularseite einen Container hinzu:

   1. Hinzufügen einer `<container>` -Element als untergeordnetes Element des `<form>` -Element.
   1. Um den Titel und das Bild für das Symbol zu definieren, verwenden Sie die `label` und `img` -Attribute.

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

   Alternativ können Sie die `type="frame"` -Attribut aus dem vorhandenen `<container>` -Elemente.

### Verschachteln von Formularen {#nest-forms}

Sie können Formulare in anderen Formularen verschachteln. Sie können beispielsweise Notebook-Formulare in iconbox-Formularen verschachteln.

Die Ebene der Verschachtelung steuert die Navigation. Benutzer können ein Drilldown zu Teilformularen durchführen.