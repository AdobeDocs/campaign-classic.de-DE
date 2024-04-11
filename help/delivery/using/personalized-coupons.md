---
product: campaign
title: Personalisierte Gutscheine
description: Erfahren Sie, wie Sie personalisierte Gutscheine erstellen und einfügen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Personalization
role: User
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 72%

---

# Personalisierte Gutscheine{#personalized-coupons}

Durch das Hinzufügen von Gutscheinen können Sie Ihren Empfängern Produkte und Dienstleistungen mit einem Mehrwert anbieten. Mit dem Campaign-Gutscheinmodul können Sie Gutscheine erstellen und zu einem späteren Zeitpunkt Marketing-Angeboten bei deren Erstellung zuweisen. Da Gutscheine nur für einen ausgewählten Zeitraum gültig sind, ist ein zugewiesener Gutschein eindeutig mit einer bestimmten Versandnachricht verknüpft. Zusätzlich wird von Campaign vor dem Versand bestätigt, dass genügend Gutscheine für die Anzahl der Nachrichten vorhanden sind.

>[!NOTE]
>
>Die Couponverwaltung ist ein Package, das installiert werden muss. Um festzustellen, ob Sie dieses Package installiert haben, gehen Sie zu **[!UICONTROL Administration > Konfiguration > Packageverwaltung > Installierte Packages.]**
>
>Gutscheindaten können im CSV- und XML-Format importiert und exportiert werden. Weitere Informationen zum Import und Export finden Sie unter [diesem Abschnitt](../../platform/using/get-started-data-import-export.md).

## Erstellen eines Gutscheins {#creating-a-coupon}

Für die Erstellung von Gutscheinen bietet Ihnen das Gutscheinmodul zwei Möglichkeiten:

* **Anonym**: ein Standardgutschein für ausgewählte Empfänger oder Empfängerlisten
* **Individuell**: ein personalisierter Gutschein für ausgewählte Empfänger

Bevor Sie die folgenden Schritte ausführen, entscheiden Sie sich für einen Gutscheintyp:

1. Wählen Sie im Campaign-Navigationsbaum **[!UICONTROL Ressourcen > Kampagnenverwaltung > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.
1. Geben Sie den Namen des Gutscheins in **[!UICONTROL Titel]** -Feld. Ein eindeutiger Code wurde automatisch in **[!UICONTROL Couponcode]**. Sie können den Code beibehalten oder einen neuen eingeben.

   ![](assets/deliv_coup_02.png)

1. Wählen Sie das **[!UICONTROL Startdatum]** und das **[!UICONTROL Enddatum]**, um den Gültigkeitszeitraum des Gutscheins festzulegen.
1. Wählen Sie in **[!UICONTROL Coupontyp]** zwischen einem anonymen und einem individuellen Gutschein.

   **[!UICONTROL Anonyme Gutscheine]** : Ein anonymer Gutschein ist für alle Empfänger identisch. Vergewissern Sie sich, dass Anonym im **Coupontyp** Menü und klicken Sie **Speichern** , um den Gutschein zu generieren.

   **[!UICONTROL Individuelle Gutscheine]**: Individuelle Gutscheine können mit zusätzlichen Couponcodes weiter personalisiert werden. Beispiel: Für den Ausverkauf in einem Sportgeschäft wird ein individueller Gutschein erstellt. Doch die Empfängerliste ist lang und die Empfänger sind an unterschiedlichen Sportarten interessiert. Deshalb können Sie dem individuellen Gutschein einen Codenamen für die jeweilige Sportart hinzufügen (z. B. Fußball, Baseball) und die Codes an die entsprechenden Empfänger senden.

   1. Bei der Auswahl von Individuell wird links unten ein neuer Tab, Coupons, angezeigt. Navigieren Sie zu **[!UICONTROL Coupons]** Registerkarte und klicken Sie auf **[!UICONTROL Hinzufügen]**.
   1. Geben Sie für den individuellen Gutschein einen eindeutigen Code ein, wenn Sie vom Pop-up dazu aufgefordert werden.
   1. Klicken Sie auf **[!UICONTROL Speichern]**, um den Gutschein zu erstellen.

   Weitere Informationen zum Tab „Gutscheine“ finden Sie unter [Konfigurieren von individuellen Gutscheinen](#configuring-individual-coupons).

   >[!NOTE]
   >
   >Individuelle Gutscheine können stapelweise importiert werden. Weitere Informationen zum Import und Export finden Sie unter [diesem Abschnitt](../../platform/using/get-started-data-import-export.md).

### Konfigurieren von individuellen Gutscheinen {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

Der Coupons-Tab erscheint nur bei individuellen Gutscheinen. Nach der Verknüpfung eines Gutscheins mit einem Versand werden im Coupons-Tab folgende Informationen angezeigt:

* **[!UICONTROL Status]**: Verfügbarkeit des Gutscheins
* **[!UICONTROL Eingelöst am]**: das Datum, an dem der Gutschein eingelöst wurde
* **[!UICONTROL Kanal]**: der für den Versand des Gutscheins verwendete Kanal
* **[!UICONTROL Adresse]**: die E-Mail-Adresse der Empfänger

Werte für **[!UICONTROL status]**, **[!UICONTROL channel]**, und **[!UICONTROL Adresse]** automatisch abgeschlossen werden. Die Werte für **[!UICONTROL eingelöst am]** nicht von Campaign abgerufen werden. Sie können ausgefüllt werden, indem Sie eine Datei importieren, die die Details für die Gutscheineinlösung enthält.

## Einfügen eines Gutscheins in einen E-Mail-Versand {#inserting-a-coupon-into-an-email-delivery}

Im folgenden Beispiel wird der Versand von der Startseite aus erstellt. Detaillierte Anweisungen zur Erstellung eines Versands finden Sie unter [diesem Abschnitt](about-email-channel.md). Sie können einem Versand auch einen Gutschein in einem Workflow hinzufügen.

1. Gehen Sie zu **[!UICONTROL Kampagnen]** und wählen Sie **[!UICONTROL Sendungen]** aus.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   ![](assets/deliv_coup_04.png)

1. Geben Sie im **[!UICONTROL Titelfeld]** einen Namen ein und wählen Sie **[!UICONTROL Fortfahren]** aus.
1. Wählen Sie **[!UICONTROL An]** aus, um Empfänger hinzuzufügen.
1. Klicks **[!UICONTROL Hinzufügen]** um Empfänger für den Versand auszuwählen. Klicken Sie nach Auswahl der Empfänger auf **[!UICONTROL Ok]** , um zum Versand zurückzukehren.

   ![](assets/deliv_coup_05.png)

1. Geben Sie einen Betreff ein und fügen Sie der Nachricht einen Inhalt hinzu.

   ![](assets/deliv_coup_06.png)

1. Wählen Sie in der Symbolleiste **[!UICONTROL Eigenschaften]** und danach den Tab **[!UICONTROL Erweitert]** aus.
1. Wählen Sie das Ordnersymbol für **[!UICONTROL Couponverwaltung]** aus.

   ![](assets/deliv_coup_07.png)

1. Wählen Sie den Gutschein aus und klicken Sie auf **[!UICONTROL Ok]**. Klicks **[!UICONTROL Ok]** erneut.

   ![](assets/deliv_coup_08.png)

1. Klicken Sie auf die Nachricht, um zu kennzeichnen, wo Sie den Gutschein platzieren möchten.

   ![](assets/deliv_coup_09.png)

1. Wählen Sie das Personalisierungssymbol aus, um je nach Gutscheintyp die folgende Auswahl zu treffen:

   * Anonymer Gutschein: **[!UICONTROL Coupon > Couponcode]**

     ![](assets/deliv_coup_10.png)

   * Individueller Gutschein: **[!UICONTROL Couponwert > Couponcode]**

     ![](assets/deliv_coup_11.png)

     Der Coupon wird nicht über den von Ihnen zugewiesenen Namen in die Nachricht eingefügt, sondern in Form von Code. Der Code wird im vorkonfigurierten Datenmodell von Campaign verwendet.

   ![](assets/deliv_coup_12.png)

1. Führen Sie einen Test durch, um den Namen zu bestätigen, den Sie dem Gutschein zugewiesen haben. Navigieren Sie zu **[!UICONTROL Vorschau]** Registerkarte und klicken Sie auf **[!UICONTROL Personalisierung testen]**. Wählen Sie einen Empfänger für den Test aus.

   ![](assets/deliv_coup_13.png)

   Nach dem Test sollte auf dem Gutschein der zugewiesene Name anstatt des Codes angezeigt werden.

   ![](assets/deliv_coup_14.png)

1. Klicken Sie in der Symbolleiste links oben auf **[!UICONTROL Senden]** und wählen Sie aus, wie Sie die Nachricht senden möchten.

   ![](assets/deliv_coup_15.png)

1. Klicken Sie auf **[!UICONTROL Analysieren]**. Wenn im Analyseprotokoll bestätigt wird, dass für alle Empfänger genügend Gutscheine vorhanden sind, klicken Sie auf **[!UICONTROL Versand bestätigen]** , um es zu versenden.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>Eine Anleitung zur Vorgehensweise, wenn nicht genügend Coupons für einen Versand vorhanden sind, finden Sie unter [Verwalten bei unzureichender Anzahl von Gutscheinen](#managing-insufficient-coupons).

So prüfen Sie, ob der Versand erfolgreich war:

1. Gehen Sie zu **[!UICONTROL Explorer > Ressourcen > Kampagnenverwaltung > Coupons]**.
1. Wählen Sie den Tab **[!UICONTROL Sendungen]**.

   ![](assets/deliv_coup_17.png)

   Eine erfolgreiche Sendung ist im Status als **[!UICONTROL Abgeschlossen]** gekennzeichnet.

>[!NOTE]
>
>Standardmäßig verwendet das Couponverwaltungsmodul eine **nms:recipient**-Tabelle. [Weitere Informationen](../../configuration/using/about-data-model.md#default-recipient-table).
>
> [Auf dieser Seite](../../configuration/using/about-custom-recipient-table.md) erfahren Sie, wie Sie eine benutzerdefinierte Empfängertabelle verwenden.

## Verwalten bei unzureichender Anzahl von Gutscheinen {#managing-insufficient-coupons}

Die Versandanalyse wird angehalten, wenn es weniger Gutscheine als Nachrichten gibt. In diesem Fall können Sie zusätzliche Gutscheine importieren oder die Anzahl der Nachrichten beschränken. Im Folgenden erfahren Sie, wie Sie die Anzahl der Nachrichten beschränken können.

1. Gehen Sie zum E-Mail-Versand-Fenster.
1. Wählen Sie **[!UICONTROL An]**.
1. Gehen Sie unter **[!UICONTROL Auswahl der Zielgruppe]** zum Tab **[!UICONTROL Ausschlüsse]**.

   ![](assets/deliv_coup_18.png)

1. Wählen Sie im Bereich für die Einstellungen der Ausschlüsse **[!UICONTROL Bearbeiten]** aus.
1. Geben Sie die Anzahl der zu sendenden Nachrichten in **[!UICONTROL Begrenzung des Versands auf]** ein und bestätigen Sie mit **[!UICONTROL OK]**. Jetzt können Sie den Versand starten.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>Bei der Verwaltung einer beschränkten Anzahl von Gutscheinen können Sie Ihren Versand durch einen Versand-Workflow gemäß Ihren Kriterien aufteilen. Diese Vorgehensweise ist empfehlenswert, wenn Sie Gutscheine an eine ausgewählte Population senden möchten, ohne die Zielgruppe einzuschränken.
