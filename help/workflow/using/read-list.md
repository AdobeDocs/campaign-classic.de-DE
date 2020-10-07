---
title: Liste lesen
seo-title: Liste lesen
description: Liste lesen
seo-description: null
page-status-flag: never-activated
uuid: 34e28675-f28b-407f-8d60-41a5383af0db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 96a7aea4-4799-4ac7-8dff-666b075a1c43
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 100%

---


# Liste lesen{#read-list}

In Workflows genutzte Daten können aus Listen stammen, deren Daten zuvor aufbereitet und strukturiert wurden, beispielsweise in einer früheren Segmentierung oder im Zuge eines Datei-Ladevorgangs.

Die Aktivität **[!UICONTROL Liste lesen]** kopiert Daten aus einer Liste in eine Workflow-Arbeitstabelle (analog zu Daten aus Abfragen). Auf diese Weise stehen sie während der gesamten Workflow-Ausführung zur Verfügung.

Die zu verarbeitende Liste kann explizit angegeben, von einem Script berechnet oder dynamisch abgerufen werden. Dies hängt von den in der Aktivität **[!UICONTROL Liste lesen]** aktivierten Optionen oder angegebenen Parametern ab.

![](assets/list_edit_select_option_01.png)

Wenn die Liste nicht explizit bezeichnet wird, ist eine Beispielliste anzugeben, die als Strukturvorlage verwendet wird.

![](assets/s_advuser_list_template_select.png)

Nach erfolgter Konfiguration der Liste können Sie über die Option **[!UICONTROL Abfrage bearbeiten...]** einen Filter hinzufügen, um die für den weiteren Workflow-Verlauf zu nutzende Population einzuschränken.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>Um in einer Liste-lesen-Aktivität Filter verwenden zu können, muss die Liste als Datei vorliegen.

Listen können direkt in der Adobe-Campaign-Startseite über die Schaltfläche **[!UICONTROL Profile und Zielgruppen > Listen]** erstellt werden oder aber im Rahmen eines Workflows über die Aktivität **[!UICONTROL Listen-Update]**.

**Anwendungsbeispiel: Ausschluss einer Adressenliste von einem Versand**

Im folgenden Beispiel soll eine Datei mit Adressen importiert werden, die gundsätzlich vom E-Mail-Versand auszuschließen sind (beispielsweise, weil die Empfänger nicht mehr existieren).

![](assets/s_advuser_list_read_sample_1.png)

Die im **Premiumkunden**-Ordner enthaltenen Profile sollen im Rahmen einer Marketingkampagne kontaktiert werden. Eine externe Liste enthält vom Versand auszuschließende Adressen. Für das vorliegende Beispiel werden nur die E-Mail-Adressen benötigt, um den Ausschluss vorzunehmen.

1. Die zum Laden der im **Premiumkunden**-Ordner enthaltenen Empfänger erstellte Abfrage muss die E-Mail-Adressen der Empfänger ausgeben, um die Abstimmung mit der Ausschlussliste zu ermöglichen.

   ![](assets/s_advuser_list_read_sample_0.png)

1. Im vorliegenden Beispiel ist die Liste im Ordner **Listen** gespeichert und der Titel wird berechnet.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Konfigurieren Sie die Ausschlussaktivität, indem Sie den Ordner **Premiumkunden** als Hauptmenge angeben. Dies bedeutet, dass dieser Ordner die beizubehaltenden Daten enthält, dass jedoch alle Datensätze, die sowohl in diesem Ordner als auch in einer anderen in die Ausschlussaktivität eingehenden Datei enthalten sind, von der Zielgruppe ausgeschlossen werden.

   ![](assets/s_advuser_list_read_sample_3.png)

   Die Ausschlussregeln werden im mittleren Bereich des Fensters konfiguriert. Klicken Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um den Ausschlusstyp zu definieren.

   Sie können für jede in die Aktivität eingehende Transition einen Ausschluss definieren.

1. Wählen Sie im Feld **[!UICONTROL Ausschlussmenge]** die Aktivität **[!UICONTROL Liste lesen]** aus. Die von dieser Aktivität übermittelten Daten werden somit von der Hauptmenge ausgeschlossen.

   Im vorliegenden Beispiel handelt es sich um einen Ausschluss über einen Join: Die Daten der Liste werden über das E-Mail-Feld mit der Hauptmenge abgestimmt. Wählen Sie zur Konfiguration des Joins im Feld **[!UICONTROL Dimensionsänderung]** die Option **[!UICONTROL Join]** aus.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Wählen Sie dann für die Quelle und das Bestimmungsziel das der E-Mail-Adresse entsprechende Feld aus. Die Spalten werden entsprechend zugeordnet und die Empfänger, deren E-Mail-Adresse in der importierten Liste enthalten ist, werden aus der Zielgruppe ausgeschlossen.

