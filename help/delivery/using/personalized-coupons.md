---
title: Personalisierte Gutscheine
seo-title: Personalisierte Gutscheine
description: Personalisierte Gutscheine
seo-description: null
page-status-flag: never-activated
uuid: c840e2de-f0ef-478b-af9f-82e1b6534933
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: f324afa5-304c-470e-a592-290f76a11ccb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Personalisierte Gutscheine{#personalized-coupons}

Durch das Hinzufügen von Gutscheinen können Sie Ihren Empfängern Produkte und Dienstleistungen mit einem Mehrwert anbieten. Mit dem Campaign-Gutscheinmodul können Sie Gutscheine erstellen und zu einem späteren Zeitpunkt Marketingangeboten bei deren Erstellung zuweisen. Da Gutscheine nur für einen ausgewählten Zeitraum gültig sind, ist ein zugewiesener Gutschein eindeutig mit einer bestimmten Versandnachricht verknüpft. Zusätzlich wird von Campaign vor dem Versand bestätigt, dass genügend Gutscheine für die Anzahl der Nachrichten vorhanden sind.

>[!NOTE]
>
>Coupon-Management ist ein Paket, das installiert werden muss. Überprüfen Sie, ob Sie über eine Gutscheinverwaltung verfügen, **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>Gutscheindaten können im CSV- und XML-Format importiert und exportiert werden. Weiterführende Informationen zum Importieren und Exportieren finden Sie in [diesem Abschnitt](../../platform/using/generic-imports-and-exports.md).

## Gutscheine erstellen {#creating-a-coupon}

Für die Erstellung von Gutscheinen bietet Ihnen das Gutscheinmodul zwei Möglichkeiten:

* **Anonym**: ein Standardgutschein für ausgewählte Empfänger oder Empfängerlisten
* **Individuell**: ein personalisierter Gutschein für ausgewählte Empfänger

Bevor Sie die folgenden Schritte ausführen, entscheiden Sie sich für einen Gutscheintyp:

1. Gehen Sie in der Kampagnenstruktur zu **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. Click the **[!UICONTROL New]** button.
1. Geben Sie den Namen des Coupons in das **[!UICONTROL Label]** Feld ein. Ein eindeutiger Code wurde automatisch eingegeben **[!UICONTROL Coupon code]**. Sie können den Code beibehalten oder einen neuen eingeben.

   ![](assets/deliv_coup_02.png)

1. Wählen Sie **[!UICONTROL Start date]** und **[!UICONTROL End date]** legen Sie den Zeitraum fest, in dem der Coupon gültig ist.
1. Wählen Sie **[!UICONTROL Coupon type]** unter &quot;Anonym&quot;oder &quot;Individuell&quot;aus.

   **[!UICONTROL Anonymous coupons]** : Ein anonymer Coupon ist für alle Empfänger identisch. Vergewissern Sie sich, dass im Menü &quot; **Coupon-Typ** &quot;die Option &quot;Anonym&quot;ausgewählt ist, und klicken Sie auf **Speichern** , um den Coupon zu generieren.

   **[!UICONTROL Individual coupons]** : Ein einzelner Coupon kann mit zusätzlichen Coupon-Codes weiter personalisiert werden. So wird beispielsweise ein einzelner Coupon für den Verkauf in einem Sportartikelladen erstellt. Die Liste der Empfänger ist jedoch lang und sie teilen nicht die gleiche Begeisterung für einen einzigen Sport. Sie können Codenamen für den einzelnen Coupon hinzufügen, der auf einem Sport basiert (z. B. Fußball, Fußball, Baseball usw.) und senden Sie jeden Code an die jeweiligen Empfänger.

   1. Wenn Sie &quot;Individuell&quot;auswählen, wird unten links eine neue Registerkarte, Coupons, angezeigt. Gehen Sie zur **[!UICONTROL Coupons]** Registerkarte und klicken Sie auf **[!UICONTROL Add]**.
   1. Geben Sie für den individuellen Gutschein einen eindeutigen Code ein, wenn Sie vom Pop-up dazu aufgefordert werden.
   1. Click **[!UICONTROL Save]** to generate the coupon.
   Weitere Informationen zur Registerkarte Coupons finden Sie unter [Konfigurieren einzelner Coupons](#configuring-individual-coupons).

   >[!NOTE]
   >
   >Individuelle Gutscheine können gesammelt importiert werden. Weiterführende Informationen zum Importieren und Exportieren finden Sie in [diesem Abschnitt](../../platform/using/generic-imports-and-exports.md).

### Individuelle Gutscheine konfigurieren {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

Der Coupons-Tab erscheint nur bei individuellen Gutscheinen. Nach der Verknüpfung eines Gutscheins mit einem Versand werden im Coupons-Tab folgende Informationen angezeigt:

* **[!UICONTROL Status]** : Coupon-Verfügbarkeit.
* **[!UICONTROL Redeemed on]** : Das Datum, an dem der Coupon eingelöst wird.
* **[!UICONTROL Channel]** : Der Kanal, über den der Coupon gesendet wurde.
* **[!UICONTROL Address]** : Die E-Mail-Adressen der Empfänger.

Die Werte für **[!UICONTROL status]**, **[!UICONTROL channel]** und **[!UICONTROL address]** werden automatisch ausgefüllt. Die Werte für **[!UICONTROL redeemed on]** werden jedoch nicht von Campaign wiederhergestellt. Sie können ausgefüllt werden, indem Sie eine Datei importieren, die die Details für die Gutscheineinlösung enthält.

## Gutschein in einen E-Mail-Versand einfügen {#inserting-a-coupon-into-an-email-delivery}

Im folgenden Beispiel wird von der Startseite aus ein Versand erstellt. Weiterführende Informationen zum Erstellen eines Versands finden Sie in [diesem Abschnitt](../../delivery/using/about-email-channel.md). Sie können auch in einem Workflow einem Versand einen Gutschein hinzufügen.

1. Gehen Sie zu **[!UICONTROL Campaigns]** und wählen Sie **[!UICONTROL Deliveries]**.
1. Klicks **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. Geben Sie einen Namen in ein **[!UICONTROL Label]** und klicken Sie auf **[!UICONTROL Continue]**.
1. Click **[!UICONTROL To]** to add recipients.
1. Klicken Sie auf **[!UICONTROL Add]** , um die Empfänger für die Bereitstellung auszuwählen. Nachdem Sie die Empfänger ausgewählt haben, klicken Sie auf **[!UICONTROL Ok]** , um zur Auslieferung zurückzukehren.

   ![](assets/deliv_coup_05.png)

1. Geben Sie einen Betreff ein und fügen Sie der Nachricht einen Inhalt hinzu.

   ![](assets/deliv_coup_06.png)

1. In the toolbar, click **[!UICONTROL Properties]** and choose the **[!UICONTROL Advanced]** tab.
1. Klicken Sie auf das Ordnersymbol für **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. Wählen Sie den Coupon aus und klicken Sie auf **[!UICONTROL Ok]**. Klicken Sie **[!UICONTROL Ok]** erneut.

   ![](assets/deliv_coup_08.png)

1. Klicken Sie auf die Nachricht, um zu kennzeichnen, wo Sie den Gutschein platzieren möchten.

   ![](assets/deliv_coup_09.png)

1. Wählen Sie das Personalisierungssymbol aus, um je nach Gutscheintyp die folgende Auswahl zu treffen:

   * Anonymer Coupon: **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * Individueller Coupon: **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      Der Gutschein wird in die Nachricht als Code eingefügt und nicht mit dem von Ihnen zugewiesenen Namen. Der Code wird innerhalb des Campaign-Standard-Datenmodells verwendet.
   ![](assets/deliv_coup_12.png)

1. Führen Sie einen Test aus, um den Namen zu bestätigen, den Sie dem Coupon zugewiesen haben. Gehen Sie zur **[!UICONTROL Preview]** Registerkarte und klicken Sie auf **[!UICONTROL Test personalization]**. Wählen Sie einen Empfänger für den Test aus.

   ![](assets/deliv_coup_13.png)

   Nach dem Test sollte auf dem Gutschein der zugewiesene Name anstatt des Codes angezeigt werden.

   ![](assets/deliv_coup_14.png)

1. In the toolbar, click **[!UICONTROL Send]** (upper left) and choose how you want to send the delivery.

   ![](assets/deliv_coup_15.png)

1. Klicks **[!UICONTROL Analyze]**. If the analysis log confirms that there are enough coupons for all recipients, click **[!UICONTROL Confirm delivery]** to send it.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>For instructions on how to manage insufficient coupons for a delivery, see [Managing insufficient coupons](#managing-insufficient-coupons)

So prüfen Sie, ob der Versand erfolgreich war:

1. Go to **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1.  Klicken Sie auf die **[!UICONTROL Deliveries]** Registerkarte.

   ![](assets/deliv_coup_17.png)

   The status reads as **[!UICONTROL Finished]** for a successful delivery.

>[!NOTE]
>
>Standardmäßig wird vom Gutscheinverwaltungsmodul eine **nms:recipient**-Tabelle verwendet. Eine Anleitung zur Verwendung einer anderen Tabelle finden Sie unter [Schemabearbeitung](../../configuration/using/data-schemas.md).

## Ungenügende Anzahl von Gutscheinen verwalten {#managing-insufficient-coupons}

Die Versandanalyse wird angehalten, wenn es weniger Gutscheine als Nachrichten gibt. In diesem Fall können Sie zusätzliche Gutscheine importieren oder die Anzahl der Nachrichten beschränken. Im Folgenden erfahren Sie, wie Sie die Anzahl der Nachrichten beschränken können.

1. Gehen Sie zum E-Mail-Versand-Fenster.
1. Klicks **[!UICONTROL To]**.
1. Gehen Sie **[!UICONTROL Select target]** zur **[!UICONTROL Exclusions]** Registerkarte.

   ![](assets/deliv_coup_18.png)

1. In the exclusion settings section, click **[!UICONTROL Edit]**.
1. Geben Sie die Anzahl der Nachrichten ein, die Sie senden möchten, **[!UICONTROL Limit delivery to...messages]** und klicken Sie auf **[!UICONTROL Ok]**. Sie können die Lieferung senden.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>Bei der Verwaltung einer beschränkten Anzahl von Gutscheinen können Sie Ihren Versand durch einen Versand-Workflow gemäß Ihren Kriterien aufteilen. Diese Vorgehensweise ist empfehlenswert, wenn Sie Gutscheine an eine ausgewählte Population senden möchten, ohne die Zielgruppe einzuschränken.
