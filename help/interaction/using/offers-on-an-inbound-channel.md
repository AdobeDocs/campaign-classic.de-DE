---
title: Eingehender Kanal
seo-title: Eingehender Kanal
description: Eingehender Kanal
seo-description: null
page-status-flag: never-activated
uuid: 45cfc990-da38-451b-b65e-e9703e443a4d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: case-study
discoiquuid: 63245348-0402-4929-9c4f-71f01f97758e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa0eb7acfb5d3b622475544735aed37d6beea892

---


# Eingehender Kanal{#offers-on-an-inbound-channel}

## Anonymen Besuchern Angebote unterbreiten {#presenting-an-offer-to-an-anonymous-visitor}

Das Unternehmen Neobank möchte auf seiner Webseite Besuchern, die sich nicht mit ihren Kundendaten angemeldet haben, ein Angebot anzeigen.

Folgende Etappen sind zur Umsetzung dieser Interaktion zu durchlaufen:

1. [Anonyme Umgebung erstellen](#creating-an-anonymous-environment)
1. [Anonyme Platzierungen erstellen](#creating-anonymous-offer-spaces)
1. [Angebotskategorie und Thema erstellen](#creating-an-offer-category-and-a-theme)
1. [Anonyme Angebote erstellen.](#creating-anonymous-offers)
1. [Angebotsplatzierungen auf der Website konfigurieren](#configure-the-web-offer-space-on-the-website)

### Erstellung einer anonymen Umgebung {#creating-an-anonymous-environment}

Follow the procedure detailed in [Creating an offer environment](../../interaction/using/live-design-environments.md#creating-an-offer-environment) to create your anonymous environment based on the **Visitors**&#39; dimensions.

Das Ergebnis ist eine Navigationsstruktur, welche Ihre neue Umgebung enthält:

![](assets/offer_env_anonymous_003.png)

### Erstellung von anonymen Platzierungen {#creating-anonymous-offer-spaces}

1. In your anonymous environment (**Visitors**) go to the **[!UICONTROL Administration]** > **[!UICONTROL Spaces]** node.
1. Click **[!UICONTROL New]** to create call channels.

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >Die Platzierung wird automatisch der anonymen Umgebung zugeordnet.

1. Ändern Sie die Beschriftung und wählen Sie den **[!UICONTROL Inbound Web]** Kanal aus. Du musst auch das **[!UICONTROL Enable unitary mode]** Kästchen markieren.

   ![](assets/offer_inbound_anonymous_example_006.png)

1. Wählen Sie die für den Angebotsinhalt in dieser Platzierung verwendeten Felder aus und kennzeichnen Sie sie als Pflichtfelder.

   Auf diese Weise werden Angebote, bei denen eins der folgenden Elemente fehlt, für diese Platzierung ausgeschlossen:

   * Title
   * HTML-Inhalt,
   * Bild-URL,
   * Ziel-URL
   ![](assets/offer_inbound_anonymous_example_030.png)

1. Geben Sie die HTML-Rendering-Funktion an. Sie kann beispielsweise folgende Form annehmen:

   ```
   function (imageUrl, targetUrl, shortContent, htmlSource){
         var html = "<p><b>" + shortContent + "</b></p>";
         html += "<p>" + htmlSource + "</p>";
         html += "<a _urlType='11' href='" + targetUrl + "'><img src='" + encodeURI(imageUrl) + "'/></a>";
         return html;
       }   
   ```

   >[!CAUTION]
   >
   >Damit die Angebote korrekt angezeigt werden, muss die Rendering-Funktion die in der Platzierung verwendeten Felder in der gleichen Reihenfolge aufrufen, in der sie zuvor ausgewählt wurden.

   ![](assets/offer_inbound_anonymous_example_031.png)

1. Speichern Sie die Platzierung.

### Erstellung einer Angebotskategorie und eines Themas {#creating-an-offer-category-and-a-theme}

1. Go to the **[!UICONTROL Offer catalog]** node within the environment you have just created.
1. Klicken Sie mit der rechten Maustaste auf die **[!UICONTROL Offer catalog]** Node und wählen Sie **[!UICONTROL Create a new 'Offer category' folder]**.

   Nennen Sie die neue Kategorie, beispielsweise **Finanzprodukte**.

1. Go to the category&#39;s **[!UICONTROL Eligibility]** tab and enter **financing** as a theme, then save changes.

   ![](assets/offer_inbound_anonymous_example_023.png)

### Erstellung anonymer Angebote {#creating-anonymous-offers}

1. Markieren Sie die soeben erstellte Kategorie.
1. Klicks **[!UICONTROL New]**.

   ![](assets/offer_inbound_anonymous_example_013.png)

1. Wählen Sie die native Vorlage für anonyme Angebote oder eine zuvor von Ihnen konfigurierte Vorlage aus.

   ![](assets/offer_inbound_anonymous_example_014.png)

1. Benennen und speichern Sie das Angebot.

   ![](assets/offer_inbound_anonymous_example_015.png)

1. Go to the **[!UICONTROL Eligibility]** tab and specify the weight of the offers according to its application contexts.

   Im vorliegenden Beispiel soll das Angebot bis zum Jahresende auf der Startseite der Webpräsenz mit Priorität erscheinen.

   ![](assets/offer_inbound_anonymous_example_016.png)

1. Go to the **[!UICONTROL Content]** tab and define the content of the offer.

   >[!NOTE]
   >
   >You can select **[!UICONTROL Content definitions]** to display the list of elements required for the web space.

   ![](assets/offer_inbound_anonymous_example_017.png)

1. Erstellen Sie ein zweites Angebot.

   ![](assets/offer_inbound_anonymous_example_018.png)

1. Go to the **[!UICONTROL Eligibility]** tab and apply the same weight as for the first offer.
1. Lassen Sie beide Angebote den Validierungszyklus durchlaufen, um sie und ihre Platzierungen in der Live-Umgebung verfügbar zu machen.

### Konfiguration der Angebotsplatzierung auf der Webseite {#configure-the-web-offer-space-on-the-website}

To make the offers you have just configured visible on the website, insert a JavaScript code into the HTML page of your site to call up the Interaction engine (for more on this, refer to [About inbound channels](../../interaction/using/about-inbound-channels.md)).

1. Go to the HTML page and insert an @id attribute with a value matching the internal name of the anonymous offer space created previously (refer to [Creating anonymous offer spaces](#creating-anonymous-offer-spaces)), preceded by **i_**.

   ![](assets/offer_inbound_anonymous_example_019.png)

1. Fügen Sie die Abfrage-URL ein.

   ![](assets/offer_inbound_anonymous_example_020.png)

   Die blauen URL-Felder oben entsprechen dem Instanznamen, dem internen Namen der Umgebung (siehe [Erstellen einer anonymen Umgebung](#creating-an-anonymous-environment)) und dem Thema, das mit der Kategorie verknüpft ist ([Erstellen einer Angebotskategorie und eines Designs](#creating-an-offer-category-and-a-theme)). Letzteres ist optional.

Wenn ein Besucher auf die Startseite der Webpräsenz zugreift, werden die Angebote des Themas **Finanzierungen** wie zuvor konfiguriert angezeigt.

![](assets/offer_inbound_anonymous_example_022.png)

Besucht er wiederholt die Startseite, wird ihm alternativ das eine oder das andere Angebot der Kategorie angezeigt, da sie die gleiche Gewichtung aufweisen.

## In eine anonyme Umgebung wechseln, wenn ein Kontakt nicht identifiziert wurde {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

Neobank möchte auf seiner Webseite Marketingangebote für zwei verschiedene Zielgruppen präsentieren: Für anonyme Besucher sollen allgemeine Produkte angezeigt werden. Wenn sich einer der Besucher als registrierter Kunde erweist, sollen ihm, sobald er sich in seinem Konto anmeldet, personalisierte Angebote unterbreitet werden.

Es wird von folgendem Szenario ausgegangen:

1. Eine Person besucht die Neobank-Webseite, ohne sich anzumelden.

   ![](assets/offer_inbound_fallback_example_050.png)

   Drei anonyme Angebote werden angezeigt: zwei **Premium**-Angebote, die Neobank-Produkte bewerben, und ein Angebot eines Neobank-Partners.

   ![](assets/offer_inbound_fallback_example_051.png)

1. Da es sich bei dem Besucher um einen Neobank-Kunden handelt, meldet er sich mit seinen Kontodaten an.

   ![](assets/offer_inbound_fallback_example_052.png)

   Nun werden drei für ihn personalisierte Angebote angezeigt.

   ![](assets/offer_inbound_fallback_example_053.png)

Für dieses Anwendungsbeispiel müssen Sie neben der üblichen Umgebung für identifizierte über eine zweite für anonyme Kontakte verfügen. Die Umgebung für identifizierte Kontakte wird dahingehend konfiguriert, dass sie automatisch zur Umgebung für anonyme Kontakte wechselt, wenn der Besucher sich nicht anmeldet, also nicht identifiziert werden kann.

Gehen Sie wie folgt vor:

* Erstellen Sie einen spezifischen Angebotskatalog für eingehende anonyme Interaktionen:

   1. [Erstellung einer Umgebung für anonyme Kontakte](#creating-an-environment-for-anonymous-contacts)
   1. [Konfiguration der Platzierungen für die anonyme Umgebung](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [Erstellung der Angebotskategorien in der anonymen Umgebung](#creating-offer-categories-in-an-anonymous-environment)
   1. [Erstellung der Angebote für anonyme Besucher](#creating-offers-for-anonymous-visitors)

* Erstellen Sie einen spezifischen Angebotskatalog für eingehende identifizierte Interaktionen:

   1. [Konfiguration der Platzierungen für die identifizierte Umgebung](#configure-the-offer-spaces-in-the-identified-environment)
   1. [Erstellung der Angebotskategorien in der identifizierten Umgebung](#creating-offer-categories-in-an-identified-environment)
   1. [Erstellung personalisierter Angebote](#creating-personalized-offers)

* Konfigurieren Sie die Abfrage des Angebotsmoduls:

   1. [Konfiguration der Angebotsplatzierungen auf der Webseite](#configuring-offer-spaces-on-the-web-page)
   1. [Definition der erweiterten Parameter der identifizierten Umgebung](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### Erstellung einer Umgebung für anonyme Kontakte {#creating-an-environment-for-anonymous-contacts}

1. Erstellen Sie eine Angebotsumgebung für anonyme eingehende Interaktionen über den Zuordnungsassistenten (**Besucherzuordnung** ). Weitere Informationen finden Sie unter [Erstellen einer Angebotsumgebung](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

   ![](assets/offer_env_anonymous_003.png)

### Konfiguration der Platzierungen für die anonyme Umgebung {#configuring-offer-spaces-for-the-anonymous-environment}

Die auf der Webseite zu unterbreitenden Angebote stammen aus zwei verschiedenen Kategorien: **Premium** und **Partner**. Im vorliegenden Beispiel wird für jede Kategorie eine spezifische Platzierung erstellt.

Gehen Sie wie folgt vor, um die Platzierung der Kategorie **Premium** zu erstellen:

1. Gehen Sie in die anonyme Design-Umgebung und fügen Sie eine Platzierung hinzu.

   ![](assets/offer_inbound_fallback_example_023.png)

1. Erstellen Sie einen neuen **[!UICONTROL Inbound web]** Typraum.

   ![](assets/offer_inbound_fallback_example_024.png)

1. Benennen Sie die Platzierung, z. B. **Premiumangebote - Web Anonym**.
1. Konfigurieren Sie die Inhaltsfelder und die Rendering-Funktionen.

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!CAUTION]
   >
   >Damit die Angebote korrekt angezeigt werden, muss die Rendering-Funktion die in der Platzierung verwendeten Felder in der gleichen Reihenfolge aufrufen, in der sie zuvor ausgewählt wurden.

1. Erstellen Sie auf die gleiche Weise die Platzierung für die Angebote der Kategorie **Partner**.

   ![](assets/offer_inbound_fallback_example_026.png)

### Erstellung der Angebotskategorien in der anonymen Umgebung {#creating-offer-categories-in-an-anonymous-environment}

Erstellen Sie zwei Angebotskategorien: **Premium** und **Partner**. Jede Kategorie soll zwei Angebote für anonyme Kontakte enthalten.

1. Go to the **[!UICONTROL Offer catalog]** in the anonymous environment that you have just created.
1. Add an **[!UICONTROL Offer category]** folder with **Best Offer** as a label.

   ![](assets/offer_inbound_fallback_example_027.png)

1. Wiederholen Sie den Vorgang und nennen Sie die zweite Kategorie **Partner**.

   ![](assets/offer_inbound_fallback_example_028.png)

### Erstellung der Angebote für anonyme Besucher {#creating-offers-for-anonymous-visitors}

Erstellen Sie nun jeweils zwei Angebote in jeder der zuvor erstellten Kategorien.

1. Markieren Sie hierfür die Kategorie **Premium** und erstellen Sie ein erstes anonymes Angebot.

   ![](assets/offer_inbound_fallback_example_029.png)

1. Go to the **[!UICONTROL Eligibility]** tab and specify the weight of the offers according to its application contexts.

   ![](assets/offer_inbound_fallback_example_030.png)

1. Go to the **[!UICONTROL Content]** tab and define the content of the offer.

   ![](assets/offer_inbound_fallback_example_032.png)

1. Wiederholen Sie den Vorgang für das zweite Angebot der Kategorie **Premium**.

   ![](assets/offer_inbound_fallback_example_031.png)

1. Markieren Sie die Kategorie **Partner** und erstellen Sie das erste anonyme Angebot der Kategorie.
1. Go to the **[!UICONTROL Content]** tab and define the content of the offer.

   ![](assets/offer_inbound_fallback_example_033.png)

1. Go to the **[!UICONTROL Eligibility]** tab and specify the weight of the offers according to its application contexts.

   ![](assets/offer_inbound_fallback_example_034.png)

1. Erstellen Sie analog das zweite Angebot der Kategorie **Partner**.

   ![](assets/offer_inbound_fallback_example_035.png)

1. Go to the **[!UICONTROL Eligibility]** tab and apply the same weight that you applied to the first offer in this category so that the offers are displayed successively on the website.

   ![](assets/offer_inbound_fallback_example_036.png)

1. Lassen Sie alle Angebote den Validierungszyklus durchlaufen, um sie in der Live-Umgebung verfügbar zu machen. Stellen Sie sicher, dass im Zuge der Inhaltsvalidierung je nach Angebot entweder die Platzierung **Partner** oder die Platzierung **Premium** aktiviert wird.

### Konfiguration der Platzierungen für die identifizierte Umgebung {#configure-the-offer-spaces-in-the-identified-environment}

Die auf der Webseite zu unterbreitenden Angebote für identifizierte Kontakte stammen aus zwei verschiedenen Kategorien: **Premium** und **Partner**. Im vorliegenden Beispiel wird für jede Kategorie eine spezifische Platzierung erstellt.

Um die beiden Angebotsräume zu erstellen, wenden Sie das gleiche Verfahren wie für anonyme Angebotsräume an. Refer to [Configuring offer spaces for the anonymous environment](#configuring-offer-spaces-for-the-anonymous-environment).

1. Gehen Sie in die identifizierte Design-Umgebung und fügen Sie die Platzierungen **Premium** und **Partner** hinzu.
1. Wenden Sie den unter Anonyme Umgebung [konfigurieren beschriebenen Prozess an](#configuring-offer-spaces-for-the-anonymous-environment).

   ![](assets/offer_inbound_fallback_example_005.png)

1. Select the **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** option.

   ![](assets/offer_inbound_fallback_example_006.png)

1. Wählen Sie mithilfe der Dropdownliste den zuvor erstellten anonymen Webangebotsraum aus (siehe [Konfigurieren von Angebotseinheiten für die anonyme Umgebung](#configuring-offer-spaces-for-the-anonymous-environment)).

   ![](assets/offer_inbound_fallback_example_007.png)

### Definition der erweiterten Parameter der identifizierten Umgebung {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

Im vorliegenden Beispiel soll der Kontakt über seine E-Mail-Adresse in der Adobe-Campaign-Datenbank identifiziert werden. Fügen Sie die E-Mail-Adresse des Empfängers wie folgt in die Platzierung ein:

1. Gehen Sie in der identifizierten Umgebung in den Platzierungsknoten.
1. Select the **Best Offer** offer space and click **[!UICONTROL Advanced parameters]**.

   ![](assets/offer_inbound_fallback_example_044.png)

1. Klicken Sie auf der **[!UICONTROL Target identification]** Registerkarte auf **[!UICONTROL Add]**.

   ![](assets/offer_inbound_fallback_example_046.png)

1. Click **[!UICONTROL Edit expression]**, go to the recipients table and select the **[!UICONTROL Email]** field.

   ![](assets/offer_inbound_fallback_example_047.png)

1. Click **[!UICONTROL OK]** to close the **[!UICONTROL Advanced parameters]** window and finish configuring the **Best Offer** offer space.
1. Wiederholen Sie den Vorgang für die **Partner**-Platzierung.

   ![](assets/offer_inbound_fallback_example_048.png)

### Erstellung der Angebotskategorien in der identifizierten Umgebung {#creating-offer-categories-in-an-identified-environment}

Erstellen Sie zwei Angebotskategorien: **Premium** und **Partner**. Jede Kategorie soll zwei personalisierte Angebote enthalten.

1. Go to the **[!UICONTROL Offer catalogs]** node in the identified environment.
1. As in the anonymous environment, add two **[!UICONTROL Offer category]** folders with **Best Offer** and **Partner** as a labels.

   ![](assets/offer_inbound_fallback_example_009.png)

### Erstellung personalisierter Angebote {#creating-personalized-offers}

Erstellen Sie nun in jeder Kategorie zwei Angebote, d. h. vier Angebote insgesamt. Gehen Sie wie folgt vor:

1. Markieren Sie die Kategorie **Premium** und erstellen Sie ein erstes personalisiertes Angebot.

   ![](assets/offer_inbound_fallback_example_011.png)

1. Go to the **[!UICONTROL Eligibility]** tab and specify the weight of the offers according to its application contexts.

   ![](assets/offer_inbound_fallback_example_012.png)

1. Go to the **[!UICONTROL Content]** tab and define the content of the offer.

   ![](assets/offer_inbound_fallback_example_013.png)

1. Wiederholen Sie den Vorgang für das zweite Angebot der Kategorie **Premium**.

   ![](assets/offer_inbound_fallback_example_014.png)

1. Markieren Sie jetzt die Kategorie **Partner** und erstellen Sie auch hier ein erstes personalisiertes Angebot.

   ![](assets/offer_inbound_fallback_example_015.png)

1. Go to the **[!UICONTROL Eligibility]** tab and specify the weight of the offers according to its application contexts.

   ![](assets/offer_inbound_fallback_example_016.png)

1. Erstellen Sie analog das zweite Angebot der Kategorie **Partner**.

   ![](assets/offer_inbound_fallback_example_017.png)

1. Go to the **[!UICONTROL Eligibility]** tab and apply the same weight that you applied to the first offer in this category so that the offers are displayed successively on the website.
1. Lassen Sie alle Angebote den Validierungszyklus durchlaufen, um sie in der Live-Umgebung verfügbar zu machen. Stellen Sie sicher, dass im Zuge der Inhaltsvalidierung je nach Angebot entweder die Platzierung **Partner** oder die Platzierung **Premium** aktiviert wird.

### Konfiguration der Angebotsplatzierungen auf der Webseite {#configuring-offer-spaces-on-the-web-page}

Die Neobank-Webseite verfügt über drei Platzierungen zur Anzeige von Angeboten: zwei für Angebote der Kategorie **Premium** und eine für Angebote der Kategorie **Partner**.

![](assets/offer_inbound_fallback_example_038.png)

Gehen Sie wie folgt vor, um die Platzierungen der Angebote in der HTML-Seite der Webpräsenz zu konfigurieren:

1. Fügen Sie im Inhalt der HTML-Seite drei

   -Elemente mit einem @id-Attribut, dessen Wert es uns ermöglicht, die Angebote in den verschiedenen Angebotspaletten der Website aufzurufen.

   ![](assets/offer_inbound_fallback_example_039.png)

1. Im Anschluss daran ist das Script anzugeben, das die Attributwerte definiert.

   ![](assets/offer_inbound_fallback_example_040.png)

   Im vorliegenden Beispiel nehmen **ContBO1** und **ContBO2** den Wert **SPC24** an, d. h. den internen Namen der zuvor in der identifizierten Umgebung erstellten **Premium**-Platzierung. Die Werte **OC10** bzw. **OC12** entsprechen den internen Namen der **Premium**-Kategorie der anonymen bzw. identifizierten Umgebung.

   ![](assets/offer_inbound_fallback_example_041.png)

   Des Weiteren nimmt **ContPtn** den Wert **SPC22** an, was dem internen Namen der in der identifizierten Umgebung erstellten **Partner**-Platzierung entspricht. **OC11** bzw. **OC13** entsprechen den internen Namen der **Partner**-Kategorie der anonymen bzw. identifizierten Umgebung.

   ![](assets/offer_inbound_fallback_example_042.png)

1. Ordnen Sie der Variable **interactionTarget** die Informationen zu, die die Identifizierung des Besuchers ermöglichen, der sich auf der Neobank-Webseite anmeldet.

   ![](assets/offer_inbound_fallback_example_043.png)

   Die Identifizierung der Person kann auf einem Browser-Cookie, einem Leseparameter in der URL, E-Mail oder der Kennung der Person basieren. Wenn ein Feld der Empfängertabelle außer dem Primärschlüssel verwendet wird, muss es in den erweiterten Parametern des Bereichs definiert werden (siehe [Festlegen der erweiterten Einstellungen der angegebenen Angebotseinstellungen](#specifying-the-advanced-settings-of-the-identified-offer-spaces)).

1. Fügen Sie die Abfrage-URL ein.

   ![](assets/offer_inbound_fallback_example_049.png)

   Die URL enthält den internen Namen (**liveRcp**) der identifizierten Umgebung.

Bei Aufruf der Webseite löst das Script die Abfrage des Angebotsmoduls aus, damit der Angebotsinhalt in den hierfür vorgesehenen Platzierungen angezeigt wird. Mit nur einer Abfrage des Adobe-Campaign-Servers erkennt das Angebotsmodul die auszuwählende Umgebung, Platzierung und Angebotskategorie.

Im vorliegenden Beispiel erkennt das Modul die identifizierte Umgebung (**liveRcp**), die Platzierung (**SPC24**) und die **Premium**-Kategorie (**OC10**) für die erste und zweite Platzierung der Webseite sowie die Platzierung (**SPC22**) und die **Partner**-Kategorie (**OC11**) für die dritte Platzierung der Webseite.

Wenn das Modul den Besucher nicht identifizieren kann, wechselt es zu den anonymen Platzierungen, die in den identifizierten Platzierungen referenziert wurden, und zu den anonymen Kategorien (**OC12** bzw. **OC13**), wie im Script angegeben.
