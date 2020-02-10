---
title: Testadressen hinzufügen
seo-title: Testadressen hinzufügen
description: Testadressen hinzufügen
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Testadressen hinzufügen{#adding-seed-addresses}

## Testadressen in einem Versand {#seed-addresses-in-a-delivery}

To add specific seed addresses for a delivery, click the **[!UICONTROL To]** link, then select the **[!UICONTROL Seed addresses]** tab.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Drei Einfügemodi stehen zur Verfügung:

1. Eingabe einzelner Testadressen.

   Klicken Sie dazu auf die **[!UICONTROL Add]** Schaltfläche und definieren Sie den Inhalt der Adressfelder. Wiederholen Sie diese Schritte für jede Adresse. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Import von Adressenvorlagen, die je nach Bedarf angepasst werden können.

   Klicken Sie dazu auf den **[!UICONTROL Import seed templates...]** Link und wählen Sie den Ordner aus, der die Adressvorlagen enthält. Weitere Informationen hierzu finden Sie unter Vorlagen für Startadressen [erstellen](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates).

   If necessary, once they are added, you can doucle-click them or click the **[!UICONTROL Detail...]** button to adapt the content of each address.

1. Dynamische Auswahl der Testadressen durch Erstellen einer Filterbedingung.

   Klicken Sie dazu auf den **[!UICONTROL Edit the dynamic condition...]** Link und geben Sie dann die Auswahlparameter der Startadresse ein. Sie können beispielsweise alle in einem bestimmten Ordner enthaltenen Seed-Adressen oder Seed-Adressen einer bestimmten Abteilung Ihres Unternehmens einschließen.

   Ein Beispiel hierfür finden Sie in diesem Abschnitt: Anwendungsfall: [Auswahl der Saatgutadressen nach Kriterien](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>This option is used when the recipient table used is not the default **nms:recipient** table and you are using the Inbox Rendering functionality provided with Adobe Campaign&#39;s **[!UICONTROL Deliverability]** module.
>
>Weitere Informationen hierzu finden Sie in der [Verwendung einer externen Empfängertabelle](../../delivery/using/using-an-external-recipient-table.md) und in der Dokumentation zum [Inbox-Rendering](../../delivery/using/inbox-rendering.md).

Bei Briefsendungen können Sie die Art der Adresseneinfügung in die Extraktionsdatei anpassen. Standardmäßig werden sie der Sortierreihenfolge der Ausgabedatei entsprechend eingeordnet. Sie haben jedoch die Möglichkeit, sie am Anfang oder am Ende der Datei bzw. zufällig inmitten der Empfänger der Hauptzielgruppe einzufügen.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Testadressen in einer Kampagne {#seed-addresses-in-a-campaign}

To add seed addresses to a target for a campaign, select the operation and click the **[!UICONTROL Edit]** tab.

Klicken Sie auf den **[!UICONTROL Advanced campaign settings...]** Link und dann auf die **[!UICONTROL Seed addresses]** Registerkarte, wie unten dargestellt:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Die auf diese Weise angegebenen Testadressen werden bei jedem Versand dieser Kampagne zur Zielgruppe hinzugefügt.
