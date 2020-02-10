---
title: Angebotsplatzierungen
seo-title: Angebotsplatzierungen
description: Angebotsplatzierungen
seo-description: null
page-status-flag: never-activated
uuid: 2ad38697-db14-4dc0-abb8-9b71d57e0e35
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 0fae2149-0980-466d-ac9e-8afec2e278be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Angebotsplatzierungen{#creating-offer-spaces}

Die Erstellung von Platzierungen erfolgt in der Design-Umgebung. Sie erfordert ein Benutzerprofil vom Typ **Technischer Administrator** mit Zugriff auf den Platzierungs-Unterordner. Die Platzierungen eines Angebots werden automatisch in die Live-Umgebung dupliziert, sobald das entsprechende Angebot validiert wurde.

Der Inhalt der Katalogangebote wird in den Angebotseinheiten konfiguriert. Standardmäßig kann der Inhalt die folgenden Felder umfassen: **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** und **[!UICONTROL Text content]**. Die Feldsequenz wird im Angebotsumfeld konfiguriert.

Mit erweiterten Parametern können Sie einen Kontaktkennungsschlüssel angeben (der aus verschiedenen Elementen, dem Namen und dem E-Mail-Feld bestehen kann, z. B.). For more on this, refer to the [Presenting an identified offer](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) section.

Die HTML- oder XML-Darstellungen werden über Rendering-Funktionen definiert. Die in der jeweiligen Rendering-Funktion definierte Reihenfolge der Felder muss mit der im Inhalt definierten übereinstimmen.

![](assets/offer_space_create_009.png)

Gehen Sie wie folgt vor, um eine neue Platzierung zu erstellen:

1. Go to the list of offer spaces and click **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. Benennen Sie die Platzierung und wählen Sie aus der Dropdown-Liste den E-Mail-Kanal aus.

   ![](assets/offer_space_create_002.png)

1. Check the **[!UICONTROL Enable unitary mode]** box if one of the following cases applies to you:

   * Sie verwenden Interaction in Kombination mit Message Center,
   * Sie verwenden den Interaction-Einzelmodus (eingehende Interaktionen).

1. Gehen Sie zum **[!UICONTROL Content field]** Fenster und klicken Sie auf **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Gehen Sie zum **[!UICONTROL Content]** Knoten und wählen Sie die Felder in der folgenden Reihenfolge aus: **[!UICONTROL Title]**, dann **[!UICONTROL Image URL]**, dann **[!UICONTROL HTML content]**, dann **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Check the **[!UICONTROL Required]** box to make each field mandatory.

   >[!NOTE]
   >
   >Dieser Parameter wird bei der Vorschau verwendet und verhindert die Publikation der Platzierungen, falls eines der Pflichtfelder nicht ausgefüllt wurde. Wenn ein Angebot jedoch bereits für eine Platzierung freigegeben wurde, wird diese Bedingung nicht berücksichtigt.

   ![](assets/offer_space_create_005.png)

1. Klicken Sie auf **[!UICONTROL Edit functions]** , um eine Renderfunktion zu erstellen.

   Diese Funktionen dienen der Erzeugung der Angebotsdarstellung in einer Platzierung. Sie haben die Wahl zwischen verschiedenen Formaten: HTML oder Text für ausgehende Interaktionen und XML für eingehende Interaktionen.

   ![](assets/offer_space_create_006.png)

1. Gehen Sie zur **[!UICONTROL HTML rendering]** Registerkarte und wählen Sie **[!UICONTROL Overload the HTML rendering function]**.
1. Geben Sie nun Ihre Rendering-Funktion ein.

   ![](assets/offer_space_create_007.png)

Bei Bedarf können Sie die XML-Renderfunktionen für eingehende Interaktionen überladen. Sie können auch HTML- und Textwiedergabefunktionen für ausgehende Interaktionen überladen. For more on this, refer to [About inbound channels](../../interaction/using/about-inbound-channels.md).

## Status von Angebotsvorschlägen {#offer-proposition-statuses}

Angebotsvorschläge können je nach Interaktion mit der Zielgruppe verschiedene Status aufweisen. Interaction enthält hierfür werksmäßig eine Reihe von Werten, die dem Angebotsvorschlag über seinen Lebenszyklus hinweg zugewiesen werden können. Es ist jedoch an Ihnen, die Plattform dahingehend zu konfigurieren, dass der bei Angebotsvorschlagserzeugung zugewiesene Status bei Annahme des Vorschlags durch einen Kontakt wechselt.

>[!NOTE]
>
>Die Aktualisierung des Vorschlagsstatus geschieht zeitverzögert. Sie erfolgt durch den Tracking-Workflow, der stündlich startet.

### Werksmäßig enthaltene Status {#status-list}

Folgende Status sind bereits in Interaction enthalten und können zur Kennzeichnung der Angebotsvorschläge verwendet werden:

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

Diese Status werden nicht standardmäßig angewendet, sie müssen zuvor konfiguriert werden.

>[!NOTE]
>
>Der Status eines Angebotsvorschlags wird automatisch in &quot;Unterbreitet&quot; geändert, wenn das Angebot mit einem Versand verknüpft ist, dessen Status &quot;Gesendet&quot; lautet.

### Konfiguration des Status bei Erzeugung des Vorschlags {#configuring-the-status-when-the-proposition-is-created}

Wenn ein Angebotsprojekt von der Interaktions-Engine erstellt wird, wird sein Status geändert, unabhängig davon, ob es sich um eine Inbound- oder eine Outbound-Interaktion handelt. Die Wahl zwischen diesen beiden Werten hängt davon ab, wie die Angebotsobjekte in der **[!UICONTROL Design]** Umgebung konfiguriert wurden

Sie können je nach Platzierung unterschiedliche, bei der Angebotserzeugung zuzuweisende Status konfigurieren, je nachdem, welche Informationen Sie in den Angebotsberichten anzeigen möchten.

Gehen Sie dazu wie folgt vor:

1. Go to the **[!UICONTROL Storage]** tab of the desired space.
1. Wählen Sie den Status aus, der bei der Vorschlagserzeugung zugewiesen werden soll.

   ![](assets/offer_update_status_001.png)

### Konfiguration des Status bei Annahme des Vorschlags {#configuring-the-status-when-the-proposition-is-accepted}

Konfigurieren Sie den bei Annahme eines Vorschlags anzuzeigenden Status, indem Sie einen der werksmäßig gelieferten Werte auswählen. Sobald ein Empfänger auf einen der im Angebot enthaltenen Links klickt, wird das Angebotsmodul abgefragt und dadurch der Statuswechsel ausgelöst.

Gehen Sie dazu wie folgt vor:

1. Go to the **[!UICONTROL Storage]** tab of the desired space.
1. Wählen Sie den Status aus, den der Vorschlag erhalten soll, nachdem er akzeptiert wurde.

   ![](assets/offer_update_status_002.png)

**Eingehende Interaktionen**

Auf der **[!UICONTROL Storage]** Registerkarte können Sie nur Status für **vorgeschlagene** und **akzeptierte** Angebotsprojekte definieren. Bei einer eingehenden Interaktion sollte der Status der Angebotsprojekte direkt in der URL für den Aufruf der Angebotsmaschine und nicht über die Schnittstelle angegeben werden. Auf diese Weise können Sie festlegen, welcher Status in anderen Fällen angewendet werden soll, z. B. wenn ein Angebot abgelehnt wird.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

So enthält beispielsweise der auf der **Neobank**-Webseite angezeigte Vorschlag mit Kennung **40004** zum Abschluss einer **Hausratsversicherung** folgende URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

As soon as a visitor clicks the offer, and therefore the URL, the **[!UICONTROL Accepted]** status (value **3**) is applied to the proposition and the visitor is redirected to a new page of the **Neobank** site to take out the insurance contract.

>[!NOTE]
>
>Wenn Sie einen anderen Status in der URL angeben möchten (z. B. wenn ein Angebotsvorschlag abgelehnt wird), verwenden Sie den Wert, der dem gewünschten Status entspricht. Beispiel: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; usw.
>
>Status und ihre Werte können im Datenschema **[!UICONTROL Offer propositions (nms)]** abgerufen werden. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../configuration/using/data-schemas.md).

**Ausgehende Interaktionen**

Bei einer ausgehenden Interaktion können Sie den **[!UICONTROL Interested]** Status automatisch auf ein Angebotsangebot anwenden, wenn die Bereitstellung einen Link enthält. Fügen Sie dem Link einfach den Wert **_urlType=&quot;11&quot;** hinzu:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Vorschau der Angebote in der Platzierung {#offer-preview-per-space}

Im Vorschau-Tab können Sie die für einen Empfänger infrage kommenden Angebote einer einzelnen Platzierung ansehen. In unten stehenden Beispiel kommen für den ausgewählten Empfänger drei Vorschläge für die Briefpost-Platzierung infrage:

![](assets/offer_space_overview_002.png)

Sollte kein Angebot für einen Empfänger infrage kommen, ist dies in der Vorschau leicht erkennbar:

![](assets/offer_space_overview_001.png)

Die Vorschau kann Kontexte ignorieren, wenn sie auf einen Bereich beschränkt sind. Dies ist der Fall, wenn das Interaktionsschema erweitert wurde, um Felder hinzuzufügen, auf die in einem Bereich mithilfe eines eingehenden Kanals verwiesen wird (weitere Informationen hierzu finden Sie im [Erweiterungsbeispiel](../../interaction/using/extension-example.md)).
