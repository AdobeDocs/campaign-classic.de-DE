---
title: Angebotsunterbreitung
seo-title: Angebotsunterbreitung
description: Angebotsunterbreitung
seo-description: null
page-status-flag: never-activated
uuid: cf4614b9-a322-4170-aa6d-4f138f8ca2d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: f6e44634-3a13-480e-ab44-f3c744054a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Angebotsunterbreitung{#managing-offer-presentation}

## Unterbreitungsregeln – Übersicht {#presentation-rules-overview}

Interaction bietet die Möglichkeit, die Menge der Angebotsvorschläge mithilfe von s. g. Unterbreitungsregeln zu regulieren. Diese speziell in Interaction zur Anwendung kommenden Regeln gehören zur Gruppe der Typologieregeln. Sie erlauben es, basierend auf den einem Kontakt zuvor vorgeschlagenen Angeboten bestimmte Angebote von der Unterbreitung auszuschließen. Die Zuweisung der Regeln erfolgt auf Umgebungsebene.

## Unterbreitungsregeln erstellen und zuweisen {#creating-and-referencing-an-offer-presentation-rule}

1. Gehen Sie zum Knoten **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typology rules]** .
1. Create a typology rule and choose the **[!UICONTROL Offer presentation]** type.

   ![](assets/offer_typology_001.png)

1. Geben Sie gegebenenfalls den Kanal an, auf den die Regel angewendet werden soll.

   ![](assets/offer_typology_002.png)

1. Konfigurieren Sie die Anwendungskriterien der Regel. Weitere Informationen finden Sie unter Einstellungen für [Präsentationsregeln](#presentation-rule-settings).
1. Wechseln Sie zum Knoten **[!UICONTROL Administration]** > **[!UICONTROL Campaign execution]** > **[!UICONTROL Typology management]** > **[!UICONTROL Typologies]** und erstellen Sie eine Typologie, die alle **[!UICONTROL Offer presentation]** Typregeln gruppiert.

   ![](assets/offer_typology_003.png)

1. Kehren Sie nun zurück zu den Regeln und ordnen Sie sie der zuvor erstellten Typologie zu.

   ![](assets/offer_typology_004.png)

1. Weisen Sie abschließend auf Ebene der Angebotsumgebung die Typologie zu.

   ![](assets/offer_typology_005.png)

## Parameter der Unterbreitungsregeln {#presentation-rule-settings}

### Anwendungskriterien {#application-criteria-}

Mit den auf der **[!UICONTROL General]** Registerkarte verfügbaren Anwendungskriterien können Sie die Angebote angeben, für die die Darstellungsregel gilt. Dazu müssen Sie eine Abfrage erstellen und die entsprechenden Angebote auswählen, wie nachfolgend beschrieben.

1. Klicken Sie in Ihrer Typologieregel auf den **[!UICONTROL Edit the rule application conditions...]** Link, um Ihre Abfrage zu erstellen.

   ![](assets/offer_typology_006.png)

1. Konfigurieren Sie im Abfragefenster den Filter, dem die von der Typologieregel betroffenen Angebote entsprechen müssen.

   Dieser kann beispielsweise eine Angebotskategorie betreffen.

   ![](assets/offer_typology_008.png)

### Angebotsdimensionen {#offer-dimensions}

In the **[!UICONTROL Offer presentation]** tab, you must specify the same dimensions for the presentation rule as those configured in the environment.

Die Tabelle **[!UICONTROL Targeting dimension]** fällt mit der Empfängertabelle zusammen (standardmäßig: nms:empfänger), die die Angebotsvorschläge erhalten. Die Tabelle **[!UICONTROL Storage dimension]** fällt mit dem mit der Targeting-Dimension verknüpften Angebotsverlauf zusammen (standardmäßig: nms:propositionRcp).

![](assets/offer_typology_009.png)

>[!NOTE]
>
>Sie können auch nicht standardmäßige Tabellen verwenden. Wenn Sie eine bestimmte Targeting-Dimension verwenden möchten, müssen Sie Tabellen sowie eine dedizierte Umgebung mithilfe der Zielzuordnung erstellen. Weitere Informationen finden Sie unter [Erstellen einer Angebotsumgebung](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

### Beweglicher Zeitraum {#period}

Es handelt sich um den Zeitraum, während dessen die Vorschläge von der Regel einbezogen werden. Er definiert, für welche Dauer der Vorschlagsverlauf bei Anwendung der Regel berücksichtigt wird. Die Regel kommt somit nicht bei Vorschlägen zum Tragen, die außerhalb dieses Zeitraums unterbreitet werden.

The period starts **n** days before the proposition date and ends **n** days afterwards, where **n** corresponds to the number entered in the **[!UICONTROL Period considered]** field:

* Bei Platzierungen vom Typ &quot;eingehend&quot; entspricht das Vorschlagsdatum dem Unterbreitungsdatum.
* Bei Platzierungen vom Typ &quot;ausgehend&quot; entspricht das Vorschlagsdatum dem Kontaktdatum des Versands (z. B. das in einem Zielgruppen-Workflow angegebene Versanddatum).

Verwenden Sie die Pfeile des Felds, um die Anzahl an Tagen zu ändern, oder geben Sie direkt die gewünschte Dauer ein (z. B. &quot;2T 6h&quot;).

![](assets/offer_typology_010.png)

### Maximale Vorschlagsanzahl {#number-of-propositions}

An dieser Stelle können Sie angeben, wie oft die Angebote maximal vorgeschlagen werden dürfen, bevor sie ausgeschlossen werden.

Verwenden Sie die Pfeile des Felds, um die Anzahl zu ändern, oder geben Sie direkt die gewünschte Zahl ein.

![](assets/offer_typology_011.png)

## Vorschläge und Empfänger konfigurieren {#defining-propositions-and-recipients}

The **[!UICONTROL Propositions to count]** section lets you specify both the recipients and the propositions which will lead to the exclusion of the offers defined in the **[!UICONTROL General]** tab if they appear a certain number of times in the propositions history.

### Vorschläge filtern {#filtering-propositions}

Standardmäßig kann nach Kanal, betroffenen Angeboten und Vorschlagstatus gefiltert werden.

![](assets/offer_typology_014.png)

Diese Kriterien stellen die häufigsten Anwendungen von Präsentationsregeln dar. Um andere Kriterien zu verwenden, können Sie eine Abfrage über den **[!UICONTROL Limit propositions...]** Link erstellen. For more on this, refer to the [Creating a query on propositions](#creating-a-query-on-propositions) section.

* **Kanalfilter**

   **[!UICONTROL On the same channel only]** : können Sie Angebotsvorschläge auf dem in der **[!UICONTROL General]** Registerkarte angegebenen Kanal ausschließen.

   Der für die Regel auf der Registerkarte angegebene Kanal ist beispielsweise E-Mail. **[!UICONTROL General]** Wenn die Angebote, für die die Regel gilt, bisher nur auf dem Webkanal angeboten wurden, kann die Interaktions-Engine die Angebote in einer E-Mail-Zustellung präsentieren. Sobald die Angebote jedoch per E-Mail präsentiert wurden, wählt die Interaktions-Engine einen anderen Kanal, um die Angebote anzuzeigen.

   >[!NOTE]
   >
   >Es handelt sich hier um den Kanal, nicht um die Platzierung. Wenn die Regel beispielsweise den Ausschluss eines Angebots im Web-Kanal betrifft, wird ein Angebot, das auf einer Webseite in zwei Platzierungen (z. B. in einem Banner und im Textkörper) vorgeschlagen werden soll, weder in der einen noch in der anderen Platzierung auf der Webseite angezeigt, wenn es zuvor bereits auf der Webseite unterbreitet wurde.
   >
   >For a workflow involving offer presentation, the rules are only correctly taken into account if they are configured on **[!UICONTROL All channels]**.

* **Angebotsfilter**

   Dieses Feld ermöglicht es, die Zählung der Angebote auf gewisse Angebotsgruppen zu beschränken.

   **[!UICONTROL All offers]** : Standardwert. Auf die Angebote wird kein Filter angewendet.

   **[!UICONTROL Offer being presented]** : das auf der **[!UICONTROL General]** Registerkarte angegebene Angebot wird ausgeschlossen, wenn es bereits präsentiert wurde.

   **[!UICONTROL Offers from the same category]** : Ein Angebot wird ausgeschlossen, wenn bereits ein Angebot aus derselben Kategorie vorgelegt wurde.

   **[!UICONTROL The offers which the rule applies to]** : Wenn mehrere Angebote auf der **[!UICONTROL General]** Registerkarte definiert sind, wird jeder Angebotsvorschlag aus diesem Angebotsset berücksichtigt und endet mit dem Ausschluss aller Angebote, wenn der Angebotsschwellenwert erreicht wird.

   Angebote 2, 3 und 5 werden beispielsweise auf der **[!UICONTROL General]** Registerkarte definiert. Die maximale Anzahl der Vorschläge ist auf 2 eingestellt. Wenn die Angebote 2 und 5 einmal präsentiert werden, beträgt die Anzahl der gezählten Vorschläge 2. Daher wird Angebot 3 nie präsentiert.

* **Vorschlagsstatusfilter**

   Dieses Feld ermöglicht die direkte Auswahl der gängigsten Vorschlagsstatus, die zu berücksichtigen sind, wenn sie im Verlauf erscheinen.

   **[!UICONTROL Regardless of the proposition status]** : Standardwert. Auf den Status des Vorschlags wird kein Filter angewendet.

   **[!UICONTROL Accepted or rejected propositions]** : ermöglicht Ihnen, zuvor angebotene Angebote, die angenommen oder abgelehnt wurden, auszuschließen.

   **[!UICONTROL Accepted propositions]** : ermöglicht Ihnen, zuvor angebotene Angebote, die akzeptiert wurden, auszuschließen.

   **[!UICONTROL Rejected propositions]** : können Sie zuvor angezeigte Angebote, die abgelehnt wurden, ausschließen.

### Empfänger definieren {#defining-recipients}

Um die Empfänger anzugeben, klicken Sie auf den **[!UICONTROL Edit the query from the targeting dimension...]** Link und wählen Sie die von der Regel betroffenen Empfänger aus.

![](assets/offer_typology_012.png)

### Abfrage bezüglich der Vorschläge erstellen {#creating-a-query-on-propositions}

To specify the propositions to be counted via a query, click the **[!UICONTROL Limit propositions...]** link and specify the criteria to be taken into account.

In unten stehendem Beispiel werden ab der zweiten Unterbreitung die Angebote der Kategorie **Spezialangebote** in der Platzierung **Callcenter** mit einer Gewichtung von unter **20** gezählt.

![](assets/offer_typology_013.png)

