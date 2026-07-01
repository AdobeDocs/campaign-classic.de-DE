---
product: campaign
title: Personalisierte Gutscheine
description: Erfahren Sie, wie Sie personalisierte Gutscheine erstellen und einfügen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Personalization
role: User
hide: true
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
TQID: https://experienceleague.adobe.com/KFX8BeFujupcQEKCfHrTxf71axwDi0RMe3zquaDVG7c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1004
ht-degree: 100%

---

# Personalisierte Gutscheine{#personalized-coupons}

Indem Sie Coupons zu Ihren Sendungen hinzufügen, können Ihre Empfängerinnen und Empfänger einen größeren Wert aus Ihren Produkten und Services erzielen. Mit dem Campaign-Coupon-Modul können Sie eine Reihe von Coupons erstellen, die Sie künftigen Marketing-Angeboten hinzufügen möchten. Wenn Sie bereit zum Erstellen eines Versands sind, weisen Sie die entsprechenden Coupons zu. Da Coupons für einen bestimmten Zeitraum gültig sind, ist ein zugewiesener Coupon eindeutig mit der Versandnachricht verknüpft. Außerdem bestätigt Campaign vor Durchführen des Versands, dass ausreichend Coupons für die Anzahl der Nachrichten vorhanden sind.

>[!AVAILABILITY]
>
>Die Couponverwaltung ist in Campaign v8 nicht im Kontext einer Enterprise-Bereitstellung (FFDA) verfügbar. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}.

Die Couponverwaltung basiert auf einem Kit, das installiert werden muss. Um festzustellen, ob Sie dieses Kit zur Couponverwaltung installiert haben, gehen Sie zu **[!UICONTROL Administration > Konfiguration > Kit-Verwaltung > Installierte Kits.]**

Coupondaten können im CSV- und XML-Format importiert und exportiert werden. [Weitere Informationen](../../platform/using/get-started-data-import-export.md).

## Erstellen eines Coupons {#creating-a-coupon}

Für die Erstellung von Coupons bietet Ihnen das Couponverwaltungsmodul zwei Möglichkeiten:

* **Anonym**: ein Standardgutschein für ausgewählte Empfänger oder Empfängerlisten
* **Individuell**: ein personalisierter Gutschein für ausgewählte Empfänger

Bevor Sie die folgenden Schritte ausführen, entscheiden Sie sich für einen Gutscheintyp:

1. Wählen Sie im Campaign-Navigationsbaum **[!UICONTROL Ressourcen > Kampagnenverwaltung > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Neu]**.
1. Geben Sie im **[!UICONTROL Titelfeld]** den Namen des Gutscheins ein. In das Feld **[!UICONTROL Couponcode]** wurde automatisch ein eindeutiger Code eingefügt. Sie können den Code beibehalten oder einen neuen eingeben.

   ![](assets/deliv_coup_02.png)

1. Wählen Sie das **[!UICONTROL Startdatum]** und das **[!UICONTROL Enddatum]**, um den Gültigkeitszeitraum des Gutscheins festzulegen.
1. Wählen Sie in **[!UICONTROL Coupontyp]** zwischen einem anonymen und einem individuellen Gutschein.

   **[!UICONTROL Anonyme Gutscheine]**: Anonyme Gutscheine sind für alle Empfänger gleich. Bestätigen Sie im Menü **Coupontyp** Ihre Auswahl eines anonymen Gutscheins und wählen Sie danach **Speichern**, um den Gutschein zu erstellen.

   **[!UICONTROL Individueller Coupon]**: Ein individueller Coupon kann mit zusätzlichen Coupon-Codes weiter personalisiert werden. Nehmen wir beispielsweise an, ein individueller Coupon wird für einen Abverkauf in einem Sportgeschäft erstellt. Die Liste der Empfängerinnen und Empfänger ist jedoch lang und sie teilen nicht alle dasselbe Interesse für eine bestimmte Sportart. Sie können den individuellen Coupons Code-Namen basierend auf der Sportart (z. B. Fußball, American Football, Baseball usw.) hinzufügen und jeden Code an die entsprechenden Empfängerinnen und Empfänger schicken.

   1. Bei der Auswahl individueller Gutscheine erscheint links unten ein neuer Coupons-Tab. Wählen Sie in diesem **[!UICONTROL Coupons]**-Tab **[!UICONTROL Hinzufügen]** aus.
   1. Geben Sie für den individuellen Gutschein einen eindeutigen Code ein, wenn Sie vom Pop-up dazu aufgefordert werden.
   1. Klicken Sie auf **[!UICONTROL Speichern]**, um den Gutschein zu erstellen.

   Weitere Informationen zum Tab „Gutscheine“ finden Sie unter [Konfigurieren von individuellen Gutscheinen](#configuring-individual-coupons).

   >[!NOTE]
   >
   >Individuelle Gutscheine können gesammelt importiert werden. Weiterführende Informationen zum Importieren und Exportieren finden Sie in [diesem Abschnitt](../../platform/using/get-started-data-import-export.md).

### Konfigurieren von individuellen Gutscheinen {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

Die Registerkarte „Coupons“ ist nur für individuelle Coupons verfügbar. Nachdem ein Coupon mit einem Versand verknüpft wurde, werden in der Registerkarte „Coupons“ folgende Details angezeigt:

* **[!UICONTROL Status]**: Verfügbarkeit des Gutscheins
* **[!UICONTROL Eingelöst am]**: das Datum, an dem der Gutschein eingelöst wurde
* **[!UICONTROL Kanal]**: der für den Versand des Gutscheins verwendete Kanal
* **[!UICONTROL Adresse]**: die E-Mail-Adresse der Empfänger

Die Werte für **[!UICONTROL Status]**, **[!UICONTROL Kanal]** und **[!UICONTROL Adresse]** werden automatisch ausgefüllt. Nur die Werte für **[!UICONTROL Eingelöst am]** werden nicht von Campaign abgerufen. Sie können aber durch den Import einer Datei eingefügt werden, in der die Details für die Gutscheineinlösung enthalten sind.

## Einfügen eines Gutscheins in einen E-Mail-Versand {#inserting-a-coupon-into-an-email-delivery}

Im folgenden Beispiel wird von der Startseite aus ein Versand erstellt. Weiterführende Informationen zum Erstellen eines Versands finden Sie in [diesem Abschnitt](about-email-channel.md). Sie können auch in einem Workflow einem Versand einen Gutschein hinzufügen.

1. Gehen Sie zu **[!UICONTROL Kampagnen]** und wählen Sie **[!UICONTROL Sendungen]** aus.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.

   ![](assets/deliv_coup_04.png)

1. Geben Sie im **[!UICONTROL Titelfeld]** einen Namen ein und wählen Sie **[!UICONTROL Fortfahren]** aus.
1. Wählen Sie **[!UICONTROL An]** aus, um Empfänger hinzuzufügen.
1. Wählen Sie **[!UICONTROL Hinzufügen]** aus, um Empfänger für den Versand auszuwählen. Wählen Sie nach der Auswahl der Empfänger **[!UICONTROL OK]**, um zum Versand zurückzukehren.

   ![](assets/deliv_coup_05.png)

1. Geben Sie einen Betreff ein und fügen Sie der Nachricht einen Inhalt hinzu.

   ![](assets/deliv_coup_06.png)

1. Wählen Sie in der Symbolleiste **[!UICONTROL Eigenschaften]** und danach den Tab **[!UICONTROL Erweitert]** aus.
1. Wählen Sie das Ordnersymbol für **[!UICONTROL Couponverwaltung]** aus.

   ![](assets/deliv_coup_07.png)

1. Wählen Sie den Gutschein und danach **[!UICONTROL OK]** aus. Wählen Sie erneut **[!UICONTROL OK]** aus.

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

1. Führen Sie einen Test durch, um den von Ihnen dem Gutschein zugewiesenen Namen zu überprüfen. Klicken Sie dazu auf der Registerkarte **[!UICONTROL Vorschau]** auf **[!UICONTROL Personalisierung testen]**. Wählen Sie eine Empfängerin bzw. einen Empfänger für den Test aus.

   ![](assets/deliv_coup_13.png)

   Nach dem Test sollte auf dem Gutschein der zugewiesene Name anstatt des Codes angezeigt werden.

   ![](assets/deliv_coup_14.png)

1. Klicken Sie in der Symbolleiste links oben auf **[!UICONTROL Senden]** und wählen Sie aus, wie Sie die Nachricht senden möchten.

   ![](assets/deliv_coup_15.png)

1. Klicken Sie auf **[!UICONTROL Analysieren]**. Wenn im Analyseprotokoll bestätigt wird, dass für alle Empfänger genügend Gutscheine vorhanden sind, versenden Sie die Nachrichten durch die Auswahl von **[!UICONTROL Absendung bestätigen]**.

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
>Standardmäßig verwendet das Modul zur Couponverwaltung eine **nms:recipient**-Tabelle. [Weitere Informationen](../../configuration/using/about-data-model.md#default-recipient-table).
>
>[Auf dieser Seite](../../configuration/using/about-custom-recipient-table.md) erfahren Sie, wie Sie eine benutzerdefinierte Empfängertabelle verwenden.

## Verwalten bei unzureichender Anzahl von Gutscheinen {#managing-insufficient-coupons}

Die Versandanalyse wird angehalten, wenn weniger Coupons als Nachrichten vorhanden sind. In diesem Fall können Sie weitere Coupons importieren oder die Anzahl der Nachrichten einschränken. Folgen Sie den nachfolgenden Anweisungen, wenn Sie die Anzahl der Nachrichten begrenzen möchten.

1. Gehen Sie zum E-Mail-Versand-Fenster.
1. Wählen Sie **[!UICONTROL An]**.
1. Gehen Sie unter **[!UICONTROL Auswahl der Zielgruppe]** zum Tab **[!UICONTROL Ausschlüsse]**.

   ![](assets/deliv_coup_18.png)

1. Wählen Sie im Bereich für die Einstellungen der Ausschlüsse **[!UICONTROL Bearbeiten]** aus.
1. Geben Sie die Anzahl der zu sendenden Nachrichten in **[!UICONTROL Versand begrenzen auf … Nachrichten]** ein und klicken Sie auf **[!UICONTROL OK]**. Sie können den Versand jetzt durchführen.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>Bei der Verwaltung einer beschränkten Anzahl von Coupons können Sie Ihren Versand durch einen Versand-Workflow gemäß Ihren Kriterien aufspalten. Diese Vorgehensweise ist empfehlenswert, wenn Sie Coupons an eine ausgewählte Population senden möchten, ohne die Zielgruppe einzuschränken.
