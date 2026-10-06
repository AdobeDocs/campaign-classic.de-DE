---
product: campaign
title: Einfügen eines Barcodes in eine E-Mail
description: Einfügen eines Barcodes in eine E-Mail
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email Design
role: User
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
subfeature_v2:
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 100%
---
# Einfügen eines Barcodes in eine E-Mail{#insert-a-barcode-in-an-email}

Die Barcode-Lösung bietet die Möglichkeit, verschiedene ein- oder zweidimensionale Code-Typen in den gängigsten Normen zu erstellen.

Es ist möglich, einen Barcode dynamisch als Bitmap unter Verwendung eines Werts zu generieren, der mithilfe von Kundenkriterien definiert wurde. Personalisierte Barcodes können in E-Mail-Kampagnen aufgenommen werden. Die Empfängerin bzw. der Empfänger kann die Nachricht drucken und sie dem ausstellenden Unternehmen zum Scannen vorlegen (z. B. beim Auschecken).

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

   * Wählen Sie zum Einfügen eines QR-Codes seinen Typ aus und geben Sie die anzuwendende Fehlerkorrekturrate an. Diese Rate definiert die Menge der wiederholten Informationen und die Toleranz bei Verschlechterung.

     ![](assets/barcode_insert_06.png)

     Beispiel eines QR-Codes:

     ![](assets/barcode_insert_12.png)

1. Geben Sie die gewünschte Größe des Barcodes an. Durch Angabe eines Faktors von x1 bis x10 kann die Größe angepasst werden.
1. Im Feld **[!UICONTROL Wert]** können Sie den Wert des Barcodes definieren. Dieser kann einem Sonderangebot entsprechen und die Funktion von Kriterien übernehmen. Es kann sich um einen Wert eines mit den Kundinnen und Kunden verknüpften Datenbankfelds handeln.

   Unten stehendes Beispiel zeigt einen EAN-8-Barcode, in dem die Kundennummer eines Empfängers enthalten ist. Klicken Sie auf die Personalisierungsschaltfläche rechts vom Feld **[!UICONTROL Wert]** und wählen Sie die Option **[!UICONTROL Empfänger > Kundennummer]**.

   ![](assets/barcode_insert_15.png)

1. Im Feld **[!UICONTROL Höhe]** können Sie die Höhe des Barcodes anpassen, ohne die Breite und somit die Abstände zwischen den Balken zu verändern.

   Es erfolgt keine einschränkende Kontrolle Ihrer Eingaben in Bezug auf den Barcode-Typ. Sollte ein falscher oder nicht kompatibler Wert eingegeben werden, sehen Sie dies erst in der **Vorschau**. In diesem Fall ist der Barcode rot durchkreuzt.

   >[!NOTE]
   >
   >Der einem Barcode zugewiesene Wert hängt von seinem Typ ab. Beispielsweise muss ein EAN-8-Typ genau 8 Ziffern haben.
   >
   >Die Personalisierungsschaltfläche rechts vom Feld **[!UICONTROL Wert]** ermöglicht das Hinzufügen von Daten zusätzlich zum Wert selbst. Dadurch wird der Barcode angereichert, sofern dies vom Barcode-Standard akzeptiert wird.
   >
   >Wenn Sie beispielsweise einen GS1-128-Barcode verwenden und zusätzlich zum Wert die Kontonummer einer Empfängerin bzw. eines Empfängers angeben möchten, klicken Sie auf die Personalisierungsschaltfläche und wählen Sie die Option **[!UICONTROL Empfänger > Kundennummer]**. Wenn die Kontonummer der ausgewählten Empfängerin bzw. des ausgewählten Empfängers korrekt eingegeben wird, wird sie vom Barcode berücksichtigt.

Nachdem diese Elemente konfiguriert wurden, können Sie Ihre E-Mail abschließen und senden. Um Fehler zu vermeiden, sollten Sie vor dem Versand stets sicherstellen, dass Ihr Inhalt korrekt angezeigt wird. Klicken Sie hierzu auf die Registerkarte **[!UICONTROL Vorschau]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Sollte ein Barcode-Wert sich als ungültig erweisen, erscheint das entsprechende Bild in der Vorschau rot durchkreuzt.

![](assets/barcode_insert_11.png)
