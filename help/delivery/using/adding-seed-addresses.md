---
product: campaign
title: Hinzufügen von Testadressen
description: Hinzufügen von Testadressen
feature: Seed Address
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 100%

---

# Hinzufügen von Testadressen{#adding-seed-addresses}

![](../../assets/common.svg)

## Testadressen in einem Versand {#seed-addresses-in-a-delivery}

Wählen Sie zum Hinzufügen spezifischer Testadressen für einen Versand den Link **[!UICONTROL An]** und danach den Tab **[!UICONTROL Testadressen]** aus.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Drei Einfügemodi stehen zur Verfügung:

1. Eingabe einzelner Testadressen.

   Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** und füllen Sie die Adressfelder aus. Dies ist für jede zu erstellende Adresse zu wiederholen.

1. Import von Adressenvorlagen, die je nach Bedarf angepasst werden können.

   Klicken Sie auf den Link **[!UICONTROL Testadressenvorlagen importieren...]** und wählen Sie den die Vorlagen enthaltenden Ordner. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](creating-seed-addresses.md#creating-seed-address-templates).

   Bei Bedarf können Sie nun die Adressfelder anpassen, indem Sie entweder darauf doppelklicken oder **[!UICONTROL Details...]** auswählen.

1. Dynamische Auswahl der Testadressen durch Erstellen einer Filterbedingung.

   Klicken Sie auf den Link **[!UICONTROL Dynamische Bedingung bearbeiten...]** und geben Sie dann die Auswahlkriterien für die Testadressen an. Sie können beispielsweise alle in einem bestimmten Ordner enthaltenen Adressen oder die zu einer bestimmten Abteilung Ihres Unternehmens gehörigen Testadressen auswählen.

   Ein Beispiel hierfür finden Sie im Abschnitt [Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien](use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Diese Option wird insbesondere dann verwendet, wenn dem Versand eine andere als die Standard-Empfängertabelle **nms:recipient** zugrunde liegt und die Inbox-Rendering-Funktion des Moduls **[!UICONTROL Zustellbarkeit]** von Adobe Campaign genutzt werden soll.
>
>Weitere Informationen hierzu finden Sie im Abschnitt [Externe Empfängertabelle verwenden](using-an-external-recipient-table.md) und in der Dokumentation zum [Inbox Rendering](inbox-rendering.md).

Bei Briefsendungen können Sie die Art der Adresseneinfügung in die Extraktionsdatei anpassen. Standardmäßig werden sie der Sortierreihenfolge der Ausgabedatei entsprechend eingeordnet. Sie haben jedoch die Möglichkeit, sie am Anfang oder am Ende der Datei bzw. zufällig inmitten der Empfänger der Hauptzielgruppe einzufügen.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Testadressen in einer Kampagne {#seed-addresses-in-a-campaign}

Um Testadressen auf Kampagnenniveau in die Zielgruppe einzuschließen, wählen Sie den Tab **[!UICONTROL Bearbeiten]** aus.

Wählen Sie nun **[!UICONTROL Erweiterte Kampagnenparameter...]** und anschließend den Tab **[!UICONTROL Testadressen]** aus, wie unten dargestellt:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Die auf diese Weise angegebenen Testadressen werden bei jedem Versand dieser Kampagne zur Zielgruppe hinzugefügt.
