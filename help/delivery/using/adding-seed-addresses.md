---
product: campaign
title: Hinzufügen von Testadressen
description: Hinzufügen von Testadressen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
TQID: https://experienceleague.adobe.com/pVYaTG48-HiK0RwJXgBbIMWa-o-R7jlEpauXNXvGi5E
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 355
ht-degree: 59%

---

# Testadressen hinzufügen{#adding-seed-addresses}

## Testadressen in einem Versand {#seed-addresses-in-a-delivery}

Wählen Sie zum Hinzufügen spezifischer Testadressen für einen Versand den Link **[!UICONTROL An]** und danach den Tab **[!UICONTROL Testadressen]** aus.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Drei Einfügemodi stehen zur Verfügung:

1. Eingabe einzelner Testadressen.

   Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Hinzufügen]** und definieren Sie den Inhalt der Adressfelder. Für jede Adresse wiederholen.

1. Import von Adressenvorlagen, die je nach Bedarf angepasst werden können.

   Klicken Sie auf den Link **[!UICONTROL Testadressenvorlagen importieren...]** und wählen Sie den die Vorlagen enthaltenden Ordner. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](creating-seed-addresses.md#creating-seed-address-templates).

   Bei Bedarf können Sie nun die Adressfelder anpassen, indem Sie entweder darauf doppelklicken oder **[!UICONTROL Details...]** auswählen.

1. Dynamische Auswahl der Testadressen durch Erstellen einer Filterbedingung.

   Klicken Sie auf den Link **[!UICONTROL Dynamische Bedingung bearbeiten…]** und geben Sie dann die Auswahlkriterien für die Testadressen an. Sie können beispielsweise alle in einem bestimmten Ordner enthaltenen Testadressen oder die zu einer bestimmten Abteilung Ihres Unternehmens gehörigen Testadressen auswählen.

   Ein Beispiel hierfür finden Sie im Abschnitt [Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Diese Option wird verwendet, wenn es sich bei der verwendeten Empfängertabelle nicht um die standardmäßige **nms:recipient**-Tabelle handelt und Sie die im Adobe Campaign-Modul **[!UICONTROL Zustellbarkeit]** bereitgestellte Inbox Rendering-Funktion verwenden.
>
>Weitere Informationen hierzu finden Sie im Abschnitt [Externe Empfängertabelle verwenden](using-an-external-recipient-table.md) und in der Dokumentation zum [Inbox Rendering](inbox-rendering.md).

Bei Sendungen können Sie auch die Art und Weise anpassen, wie Adressen in die Extraktionsdatei eingefügt werden. Standardmäßig werden sie in der Sortierreihenfolge der Ausgabedatei eingefügt. Sie können sie jedoch auch am Ende oder am Anfang der Datei oder nach dem Zufallsprinzip zwischen den Empfängerinnen und Empfängern der Hauptzielgruppe einfügen.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Testadressen in einer Kampagne {#seed-addresses-in-a-campaign}

Um Testadressen auf Kampagnenniveau in die Zielgruppe einzuschließen, wählen Sie den Tab **[!UICONTROL Bearbeiten]** aus.

Wählen Sie nun **[!UICONTROL Erweiterte Kampagnenparameter...]** und anschließend den Tab **[!UICONTROL Testadressen]** aus, wie unten dargestellt:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Die auf diese Weise angegebenen Testadressen werden bei jedem Versand dieser Kampagne zur Zielgruppe hinzugefügt.
