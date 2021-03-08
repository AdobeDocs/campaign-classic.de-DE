---
solution: Campaign Classic
product: campaign
title: Dokumente und Versandentwurf der Marketing-Kampagne
description: Weitere Informationen zu Dokumenten und Versandentwürfen von Marketing-Kampagnen
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 64%

---


# Zugehörige Dokumente {#managing-associated-documents} verwalten

Sie können einer Kampagne verschiedene Dokumente zuordnen: Berichte, Fotos, Webseiten, Diagramme usw. Diese Dokumente können in jedem beliebigen Format vorliegen (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF usw.).

>[!IMPORTANT]
>
>Diese Funktion ist für kleine Assets und Dokumente reserviert.

In einer Kampagne können Sie auch auf andere Artikel, wie z.B. Promo-Gutscheine, besondere Angebote in Bezug auf eine bestimmte Marke oder ein Geschäft, usw. verweisen. Wenn diese Elemente in einer Umrisslinie enthalten sind, können sie mit einem Versand für Direktwerbung verknüpft werden. Siehe [Verknüpfen und Strukturieren von Ressourcen, die über einen Versandentwurf](#associating-and-structuring-resources-linked-via-a-delivery-outline) verknüpft sind.

>[!NOTE]
>
>Wenn Sie das Kampagne Marketing-Ressource Management-Modul verwenden, können Sie auch eine Bibliothek mit Marketing-Ressourcen verwalten, die mehreren Benutzern für die Zusammenarbeit zur Verfügung stehen. [Weitere Informationen](../../campaign/using/managing-marketing-resources.md).

## hinzufügen Dokumente {#adding-documents}

Dokumente können einer Kampagne (kontextrelevante Dokumente) oder einem Programm (allgemeine Dokumente) zugeordnet werden.

Der Tab **[!UICONTROL Dokumente]** enthält:

* die Liste aller für den Inhalt notwendigen Dokumente (Vorlagen, Bilder usw.), die von berechtigten Adobe-Campaign-Benutzern lokal heruntergeladen werden können;
* Informationen für den Router enthaltende Dokumente, wenn vorhanden.

Die Dokumente werden über den Tab **[!UICONTROL Bearbeiten > Dokumente]** einem Programm oder einer Kampagne zugeordnet.

![](assets/s_ncs_user_op_add_document.png)

Es besteht darüber hinaus die Möglichkeit, Dokumente über einen im Dashboard angebotenen Link einer Kampagne zuzuordnen.

![](assets/add_a_document_in_op.png)

Klicken Sie auf das Symbol **[!UICONTROL Details]**, um den Inhalt einer Datei anzusehen und ergänzende Informationen hinzuzufügen.

![](assets/s_ncs_user_op_add_document_details.png)

Im Abschnitt **[!UICONTROL Dokument(e)]** des Kampagnen-Dashboards werden alle der Kampagne zugeordneten Dokumente aufgelistet, wie im folgenden Beispiel:

![](assets/s_ncs_user_op_edit_document.png)

Über die Links können die Dokumente geöffnet und bearbeitet werden.

## Verknüpfen und Strukturieren von Ressourcen, die über einen Versandentwurf {#associating-and-structuring-resources-linked-via-a-delivery-outline} verknüpft sind

>[!NOTE]
>
>Versandentwürfe werden ausschließlich im Rahmen von Briefversand-Kampagnen verwendet.

Ein Versandentwurf bezeichnet einen strukturierten Elementsatz (Dokumente, Geschäfte, Werbecoupons usw.) erstellt von der Firma und für eine bestimmte Kampagne.

Diese Elemente sind in Versandentwurf gruppiert und jeder Versandentwurf wird mit einem Versand verknüpft. Es wird in der an den **Dienstleister** gesendeten Extraktion referenziert, um an den Versand angehängt zu werden. Sie können beispielsweise einen Versandentwurf erstellen, der sich auf eine Verzweigung und die verwendeten Marketingbroschüren bezieht.

Versandentwürfe ermöglichen es, in Kampagnen externe Elemente zu strukturieren, die einem Versand nach bestimmten Kriterien hinzugefügt werden: bewilligtes Sonderangebot, Einladung zu einem lokalen Event etc.

### Erstellen eines Umrisses {#creating-an-outline}

Um einen Versandentwurf zu erstellen, klicken Sie auf den Untertab **[!UICONTROL Versandentwürfe]** im Tab **[!UICONTROL Bearbeiten > Dokumente]** der betreffenden Kampagne.

>[!NOTE]
>
>Sollte dieser Tab nicht vorhanden sein, ist die Funktionalität für diese Kampagne nicht verfügbar. Überprüfen Sie in diesem Fall die Konfiguration der Kampagnenvorlage.
>   
>Weitere Informationen zu Vorlagen finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Klicken Sie anschließend auf **[!UICONTROL Versandentwurf hinzufügen]**. Es wird ein Navigationsbaum für die Kampagne erstellt:

1. Machen Sie einen Rechtsklick auf den Wurzelknoten und wählen Sie **[!UICONTROL Neu > Versandentwürfe]** aus, um einen neuen Versandentwurf hinzuzufügen.
1. Machen Sie einen Rechtsklick auf den soeben erstellten Versandentwurf und wählen Sie beispielsweise **[!UICONTROL Neu > Artikel]** oder **[!UICONTROL Neu > Personalisierungsfelder]** aus.

![](assets/s_ncs_user_op_add_composition.png)

Ein Versandentwurf kann Artikel, Personalisierungsfelder, Ressourcen und Angebote enthalten:

* Artikel sind beispielsweise physische Dokumente, die an dieser Stelle referenziert und beschrieben und schließlich dem Versand angehängt werden.
* Personalisierungsfelder ermöglichen die Erstellung von mit Sendungen (und nicht Empfängern) verbundenen Personalisierungselementen. So können Werte erstellt werden, die in Sendungen mit einer spezifischen Zielgruppe verwendet werden (z. B. Willkommensangebot, prozentuale Ermäßigung). Sie werden in Adobe Campaign erstellt und über den Link **[!UICONTROL Personalisierungsfelder importieren...]** in den jeweiligen Entwurf importiert.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   Über das Symbol **[!UICONTROL Hinzufügen]** rechts vom Bereich der Liste können dem Entwurf auch direkt Personalisierungselemente hinzugefügt werden.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Die Ressourcen sind Marketing-Ressourcen, die im Dashboard Marketing-Ressource generiert werden, auf das über den Link **[!UICONTROL Resources]** der Registerkarte **[!UICONTROL Kampagnen]** zugegriffen wird.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Weitere Informationen zu Marketing-Ressourcen finden Sie in [diesem Abschnitt](../../campaign/using/managing-marketing-resources.md).

### Auswählen eines Umrisses {#selecting-an-outline}

Sie können für jeden Versand über den Bereich der Extraktionskonfiguration einen Entwurf auswählen, wie im folgenden Beispiel:

![](assets/s_ncs_user_op_select_composition.png)

Der ausgewählte Entwurf wird daraufhin im unteren Abschnitt des Fenster angezeigt. Er kann über das rechts vom Feld gelegene Lupensymbol geöffnet oder über die Dropdown-Liste durch einen anderen ersetzt werden:

![](assets/s_ncs_user_op_select_composition_b.png)

Diese Information wird ebenfalls im Tab **[!UICONTROL Zusammenfassung]** des Versands angezeigt:

![](assets/s_ncs_user_op_select_composition_c.png)

### Extraktionsergebnis {#extraction-result}

In der dem Dienstleister übermittelten Extraktionsdatei werden der Name des Entwurfs sowie gegebenenfalls seine Eigenschaften (Kosten, Beschreibung usw.) dem Inhalt hinzugefügt, entsprechend der Informationen in der Exportvorlage, die dem Dienstleister zugeordnet wurde.

Im folgenden Beispiel werden der Titel, die Plankosten sowie die Beschreibung des dem Versand zugeordneten Entwurfs der Extraktionsdatei hinzugefügt.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Die Exportvorlage muss dem gewählten Dienstleister für den betreffenden Versand zugeordnet sein. Siehe [diesen Abschnitt](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Weitere Informationen zu Exporten finden Sie im Abschnitt [dieser Abschnitt](../../platform/using/get-started-data-import-export.md).
