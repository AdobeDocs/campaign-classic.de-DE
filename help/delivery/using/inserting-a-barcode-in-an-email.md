---
product: campaign
title: Einfügen eines Barcodes in eine E-Mail
description: Einfügen eines Barcodes in eine E-Mail
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Email Design
role: User
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 59%

---

# Einfügen eines Barcodes in eine E-Mail{#insert-a-barcode-in-an-email}

Die Barcode-Lösung bietet die Möglichkeit, verschiedene ein- oder zweidimensionale Code-Typen in den gängigsten Normen zu erstellen.

Es ist möglich, einen Barcode dynamisch als Bitmap unter Verwendung eines Werts zu generieren, der mithilfe von Kundenkriterien definiert wurde. Personalisierte Barcodes können in E-Mail-Kampagnen aufgenommen werden. Der Empfänger kann die Nachricht drucken und sie dem ausstellenden Unternehmen zum Scannen vorlegen (z. B. beim Auschecken).

Positionieren Sie den Cursor im Inhalt an der Stelle, an der der Barcode eingefügt werden soll, und klicken Sie auf die Personalisierungsschaltfläche. Wählen Sie **[!UICONTROL Einfügen > Barcode...]**.

![](assets/barcode_insert_14.png)

Konfigurieren Sie dann die verschiedenen Elemente je nach Bedarf:

1. Wählen Sie den Barcode-Typ aus.

   * Für das 1D-Format stehen in Adobe Campaign folgende Typen zur Verfügung: Codabar, Code 128, GS1-128 (vormals EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET und Royal Mail (RM4SCC).

     Beispiel eines 1D-Barcodes:

     ![](assets/barcode_insert_08.png)

   * Die Typen DataMatrix und PDF417 betreffen das 2D-Format.

     Beispiel eines 2D-Barcodes:

     ![](assets/barcode_insert_09.png)

   * Um einen QR-Code einzufügen, wählen Sie diesen Typ und geben Sie die anzuwendende Fehlerkorrekturrate ein. Dieser Satz definiert die Menge der wiederholten Informationen und die Toleranz gegenüber Verschlechterung.

     ![](assets/barcode_insert_06.png)

     Beispiel eines QR-Codes:

     ![](assets/barcode_insert_12.png)

1. Geben Sie die gewünschte Größe des Barcodes an. Durch Angabe eines Faktors von x1 bis x10 kann die Größe angepasst werden.
1. Im **[!UICONTROL Wert]** können Sie den Wert des Barcodes definieren. Ein Wert kann mit einem speziellen Angebot übereinstimmen und die Funktion eines Kriteriums sein. Er kann der Wert eines mit den Kunden verknüpften Datenbankfelds sein.

   Unten stehendes Beispiel zeigt einen EAN-8-Barcode, in dem die Kundennummer eines Empfängers enthalten ist. Klicken Sie auf die Personalisierungsschaltfläche rechts vom Feld **[!UICONTROL Wert]** und wählen Sie die Option **[!UICONTROL Empfänger > Kundennummer]**.

   ![](assets/barcode_insert_15.png)

1. Im Feld **[!UICONTROL Höhe]** können Sie die Höhe des Barcodes anpassen, ohne die Breite und somit die Abstände zwischen den Balken zu verändern.

   Es erfolgt keine einschränkende Kontrolle Ihrer Eingaben in Bezug auf den Barcode-Typ. Sollte ein falscher oder nicht kompatibler Wert eingegeben werden, sehen Sie dies erst in der **Vorschau**. In diesem Fall ist der Barcode rot durchkreuzt.

   >[!NOTE]
   >
   >Der einem Barcode zugewiesene Wert hängt von seinem Typ ab. Beispielsweise muss ein EAN-8-Typ genau 8 Nummern haben.
   >
   >Über die Personalisierungsschaltfläche rechts neben dem Feld **[!UICONTROL Wert]** können Sie zusätzlich zum Wert selbst Daten hinzufügen. Dadurch wird der Barcode angereichert, sofern er vom Barcode-Standard akzeptiert wird.
   >
   >Wenn Sie beispielsweise einen Barcode vom Typ GS1-128 verwenden und die Kontonummer eines Empfängers zusätzlich zum Wert eingeben möchten, klicken Sie auf die Schaltfläche Personalisierung und wählen Sie **[!UICONTROL Empfänger > Kontonummer]**. Wenn die Kontonummer des ausgewählten Empfängers korrekt eingegeben wurde, wird sie vom Barcode berücksichtigt.

Nachdem diese Elemente konfiguriert wurden, können Sie Ihre E-Mail abschließen und senden. Um Fehler zu vermeiden, sollten Sie vor dem Versand stets sicherstellen, dass Ihr Inhalt korrekt angezeigt wird. Klicken Sie hierzu auf die Registerkarte **[!UICONTROL Vorschau]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Sollte ein Barcode-Wert sich als ungültig erweisen, erscheint das entsprechende Bild in der Vorschau rot durchkreuzt.

![](assets/barcode_insert_11.png)
