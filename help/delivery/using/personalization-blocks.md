---
title: Gestaltungsbausteine
seo-title: Gestaltungsbausteine
description: Gestaltungsbausteine
seo-description: null
page-status-flag: never-activated
uuid: f9867f8d-f6ce-4a5f-b6b4-fd8056d28576
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: e68d1435-70e6-479e-a347-9ff9f9f11b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Gestaltungsbausteine{#personalization-blocks}

Personalisierungsblöcke sind dynamisch, personalisiert und enthalten ein bestimmtes Rendering, das Sie in Ihre Auslieferungen einfügen können. Sie können beispielsweise ein Logo, eine Grußmeldung oder einen Link zu einer Spiegelseite hinzufügen. Siehe [Einfügen von Personalisierungsblöcken](#inserting-personalization-blocks).

>[!NOTE]
>
>Personalization blocks are also available from the **[!UICONTROL Digital Content Editor (DCE)]** . For more on this, refer to [this page](../../web/using/editing-content.md#inserting-a-personalization-block).

Auf Personalisierungsblöcke wird über den **[!UICONTROL Resources > Campaign Management > Personalization blocks]** Knoten des Adobe Campaign-Explorers zugegriffen. Standardmäßig sind mehrere Blöcke verfügbar (siehe [Vordefinierte Personalisierungsblöcke](#out-of-the-box-personalization-blocks)).

Sie haben die Möglichkeit, neue Blöcke zu definieren, mit denen Sie die Personalisierung Ihrer Auslieferungen optimieren können. Weitere Informationen finden Sie unter [Definieren benutzerdefinierter Personalisierungsblöcke](#defining-custom-personalization-blocks).

## Gestaltungsbausteine einfügen {#inserting-personalization-blocks}

Gehen Sie folgendermaßen vor, um Gestaltungsbausteine in eine Nachricht einzufügen:

1. In the content editor of the delivery wizard, click the personalized field icon and select the **[!UICONTROL Include]** menu.
1. Select a personalization block from the list (the list displays the 10 last used blocks), or click the **[!UICONTROL Other...]** menu to access the full list.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Das **[!UICONTROL Other...]** Menü bietet Zugriff auf alle vordefinierten und benutzerdefinierten Personalisierungsblöcke (siehe [Vordefinierte Personalisierungsblöcke](#out-of-the-box-personalization-blocks) und [Definieren benutzerdefinierter Personalisierungsblöcke](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Der Gestaltungsbaustein wird in Form eines Scripts eingefügt und in der Personalisierungsphase automatisch an das Empfängerprofil angepasst.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Click the **[!UICONTROL Preview]** tab and select a recipient to view the personalization.

   ![](assets/s_ncs_user_personalized_block04.png)

Sie können den Quellcode eines Personalisierungsblocks in den Bereitstellungsinhalt aufnehmen. Wählen Sie dazu **[!UICONTROL Include the HTML source code of the block]** beim Auswählen aus.

![](assets/s_ncs_user_personalized_block05.png)

Der HTML-Quellcode wird in den Bereitstellungsinhalt eingefügt. Der **[!UICONTROL Greetings]** Personalisierungsblock wird beispielsweise wie folgt angezeigt:

![](assets/s_ncs_user_personalized_block06.png)

## Beispiel für Gestaltungsbausteine {#personalization-blocks-example}

In diesem Beispiel erstellen wir eine E-Mail, in der wir Gestaltungsbausteine verwenden, durch die der Empfänger die Mirrorseite ansehen, den Newsletter in sozialen Netzwerken teilen und sich von künftigen Sendungen abmelden kann.

Zu diesem Zweck müssen wir folgende Gestaltungsbausteine einfügen:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Weitere Informationen zur Erzeugung der Spiegelseite finden Sie unter [Generieren der Spiegelseite](../../delivery/using/sending-messages.md#generating-the-mirror-page).

1. Erstellen Sie einen neuen Versand oder öffnen Sie einen existierenden E-Mail-Versand.
1. In the delivery wizard, click **[!UICONTROL Subject]** to edit the subject of the message and enter a subject.
1. Fügen Sie die Personalisierungsblöcke in den Nachrichtentext ein. Klicken Sie dazu auf den Inhalt der Nachricht, klicken Sie auf das Symbol für das personalisierte Feld und wählen Sie das **[!UICONTROL Include]** Menü aus.
1. Wählen Sie den ersten einzufügenden Gestaltungsbaustein aus. Wiederholen Sie diesen Vorgang, um die beiden anderen Bausteine einzufügen.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Klicken Sie auf die **[!UICONTROL Preview]** Registerkarte, um das Personalisierungsergebnis anzuzeigen. Sie müssen einen Empfänger auswählen, um die Nachricht des Empfängers anzuzeigen.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Bestätigen Sie, dass die Inhalte der Bausteine korrekt angezeigt werden.

## Native Gestaltungsbausteine {#out-of-the-box-personalization-blocks}

Standardmäßig ist eine Liste mit Gestaltungsbausteinen verfügbar, um den Inhalt einer Nachricht zu personalisieren.

>[!NOTE]
>
>Die Liste der Gestaltungsbausteine hängt von den Modulen und Optionen ab, die auf Ihrer Instanz installiert sind.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : fügt Grüße mit dem Namen des Empfängers ein. Beispiel: &quot;Hallo John Doe.&quot;
* **[!UICONTROL Insert logo]** : fügt ein vordefiniertes Logo ein, das beim Konfigurieren der Instanz definiert wurde.
* **[!UICONTROL Powered by Adobe Campaign]** : fügt das Logo &quot;Powered by Adobe Campaign&quot;ein.
* **[!UICONTROL Mirror page URL]** : fügt die URL der Spiegelseite ein, sodass die Entwickler der Auslieferung den Link überprüfen können.

   >[!NOTE]
   >
   >Weitere Informationen zur Erzeugung der Spiegelseite finden Sie unter [Generieren der Spiegelseite](../../delivery/using/sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : fügt einen Link zur Spiegelseite ein: &quot;Wenn Sie diese Meldung nicht richtig anzeigen können, klicken Sie hier.&quot;
* **[!UICONTROL Unsubscription link]** : fügt einen Link ein, der es ermöglicht, sich von allen Auslieferungen abzumelden (schwarze Liste).
* **[!UICONTROL Formatting function for proper nouns]** : generiert die **[!UICONTROL toSmartCase]** JavaScript-Funktion, die den ersten Buchstaben jedes Wortes in Großbuchstaben ändert. Dieser Block muss in den Quellcode der Lieferung in **`<script>...</script>`** -Tags eingefügt werden.

   Im Beispiel unten wird mit der Funktion das Element &quot;My header&quot;durch &quot;My new header&quot;durch Großbuchstaben bei jedem Wort ersetzt:

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** : fügt eine Abonnement-URL ein (siehe [Informationen zu Diensten und Abonnements](../../delivery/using/about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : fügt einen Abonnementlink ein. die beim Konfigurieren der Instanz definiert wurde.
* **[!UICONTROL Registration link (with referrer)]** : fügt einen Abonnementlink ein, über den der Besucher und die Auslieferung identifiziert werden können. Der Link wurde beim Konfigurieren der Instanz definiert.

   >[!NOTE]
   >
   >Dieser Baustein kann in Sendungen verwendet werden, die nur an Besucher gerichtet sind.

* **[!UICONTROL Registration confirmation]** : fügt einen Link zur Bestätigung des Abonnements ein.
* **[!UICONTROL Social network sharing links]** : fügt Schaltflächen ein, mit denen der Empfänger einen Link zum Inhalt der Spiegelseite mit dem E-Mail-Client, Facebook, Twitter, Google + und LinkedIn teilen kann (siehe [Virales Marketing: an einen Freund weitergeleitet](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** und **[!UICONTROL Notification style]** : Code generieren, der eine E-Mail mit vordefinierten HTML-Stilen formatiert. Diese Blöcke müssen in den Quellcode der Lieferung, im **[!UICONTROL ...]** Abschnitt, in **`<style>...</style>`** -Tags eingefügt werden.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : fügt eine URL ein, mit der ein Interaktionsangebot festgelegt werden kann **[!UICONTROL Accepted]** (siehe [diesen Abschnitt](../../interaction/using/offer-analysis-report.md)).

## Benutzerdefinierte Gestaltungsbausteine definieren {#defining-custom-personalization-blocks}

Sie können neue Personalisierungsfelder definieren, die über das **[!UICONTROL Include...]** Menü aus dem personalisierten Feldsymbol eingefügt werden sollen. Diese Felder werden in Personalisierungsblöcken definiert.

Gehen Sie wie folgt vor, um Gestaltungsbausteine zu erstellen:

1. Klicken Sie auf die **[!UICONTROL Resources > Campaign Management > Personalization blocks]** Node.
1. Right-click the list of blocks and select **[!UICONTROL New]** .
1. Konfigurieren Sie den Gestaltungsbaustein:

   ![](assets/s_ncs_user_personalized_block.png)

   * Benennen Sie den Baustein. Der hier angegebene Titel wird im Einfügefenster der Personalisierungsfelder angezeigt.
   * Wählen Sie **[!UICONTROL Visible in the customization menus]** diese Option, um über das Symbol zum Einfügen des Personalisierungsfelds auf diesen Block zuzugreifen.
   * Legen Sie bei Bedarf zwei separate Blöcke für E-Mails im HTML-Format und im Textformat **[!UICONTROL The content of the personalization block depends upon the format]** fest.

      In diesem Fall wird das Fenster in zwei Tabs – HTML- und Textinhalt – unterteilt, um die formatbedingten Inhalte separat erfassen zu können.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Enter the content (in HTML, text, JavaScript, etc.) of the personalization block(s) and click **[!UICONTROL Save]** .
