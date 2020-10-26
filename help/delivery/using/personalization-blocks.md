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
translation-type: ht
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: ht
source-wordcount: '996'
ht-degree: 100%

---


# Gestaltungsbausteine{#personalization-blocks}

Gestaltungsbausteine sind dynamisch und personalisierbar und weisen ein spezifisches Rendering auf. Sie können Gestaltungsbausteine in Nachrichten einfügen, z. B. ein Logo, eine Grußbotschaft oder einen Mirror-Seiten-Link. Siehe [Gestaltungsbausteine einfügen](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png)[ Mehr zu dieser Funktion erfahren Sie im Video.](#personalization-blocks-video).

Auf Gestaltungsbausteine kann im Adobe Campaign-Explorer über den Knoten **[!UICONTROL Ressourcen > Kampagnenverwaltung > Gestaltungsbausteine]** zugegriffen werden. Standardmäßig sind verschiedene Bausteine verfügbar (siehe [Native Gestaltungsbausteine](#out-of-the-box-personalization-blocks)).

Sie haben die Möglichkeit, neue Bausteine zu definieren, mit denen Sie die Personalisierung Ihrer Sendungen verbessern können. Weitere Informationen finden Sie unter [Benutzerdefinierte Gestaltungsbausteine definieren](#defining-custom-personalization-blocks).

>[!NOTE]
>
>Gestaltungsbausteine sind auch im **[!UICONTROL Digital Content Editor (DCE)]** verfügbar. Weiterführende Informationen dazu finden Sie auf [dieser Seite](../../web/using/editing-content.md#inserting-a-personalization-block).

## Gestaltungsbausteine einfügen {#inserting-personalization-blocks}

Gehen Sie folgendermaßen vor, um Gestaltungsbausteine in eine Nachricht einzufügen:

1. Wählen Sie im Inhaltseditor des Versand-Assistenten die Personalisierungsfelder-Schaltfläche und danach das Menü **[!UICONTROL Einfügen]**.
1. Wählen Sie einen Gestaltungsbaustein aus der Liste aus (in der Liste werden die zehn zuletzt verwendeten Gestaltungsbausteine angezeigt) oder greifen Sie über das Menü **[!UICONTROL Sonstige...]** auf die vollständige Liste zu.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Das Menü **[!UICONTROL Sonstige...]** bietet Ihnen Zugriff auf alle nativen und benutzerdefinierten Gestaltungsbausteine (siehe [Native Gestaltungsbausteine](#out-of-the-box-personalization-blocks) und [Benutzerdefinierte Gestaltungsbausteine definieren](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Der Gestaltungsbaustein wird in Form eines Scripts eingefügt und in der Personalisierungsphase automatisch an das Empfängerprofil angepasst.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Klicken Sie nun auf den **[!UICONTROL Vorschau]**-Tab und wählen Sie einen Empfänger aus, um das Ergebnis der Personalisierung anzusehen.

   ![](assets/s_ncs_user_personalized_block04.png)

Sie können auch den Quellcode eines Gestaltungsbausteins im Versandinhalt verwenden, indem Sie die Option **[!UICONTROL HTML-Quellcode des Bausteins einfügen]** auswählen.

![](assets/s_ncs_user_personalized_block05.png)

Der HTML-Quellcode wird im Versandinhalt eingefügt. Beispielsweise wird der Gestaltungsbaustein **[!UICONTROL Grußformeln]** wie folgt angezeigt:

![](assets/s_ncs_user_personalized_block06.png)

## Beispiel für Gestaltungsbausteine {#personalization-blocks-example}

In diesem Beispiel erstellen wir eine E-Mail, in der wir Gestaltungsbausteine verwenden, durch die der Empfänger die Mirrorseite ansehen, den Newsletter in sozialen Netzwerken teilen und sich von künftigen Sendungen abmelden kann.

Zu diesem Zweck müssen wir folgende Gestaltungsbausteine einfügen:

* **[!UICONTROL Link zur Mirrorseite]** .
* **[!UICONTROL Teilen-Links der sozialen Netzwerke]** .
* **[!UICONTROL Abmelde-Link]** .

>[!NOTE]
>
>Weitere Informationen zur Erstellung der Mirror-Seite finden Sie unter [Mirror-Seite erstellen](../../delivery/using/sending-messages.md#generating-the-mirror-page).

1. Erstellen Sie einen neuen Versand oder öffnen Sie einen existierenden E-Mail-Versand.
1. Klicken Sie im Versand-Assistenten auf den **[!UICONTROL Betreff]**-Link, um einen Betreff einzugeben.
1. Im nächsten Schritt wird der Nachrichten-Textkörper angepasst. Klicken Sie dazu in das Inhaltsfeld der Nachricht und danach auf die Schaltfläche zum Einfügen von Personalisierungsfeldern. Wählen Sie danach das Menü **[!UICONTROL Einfügen]** aus.
1. Wählen Sie den ersten einzufügenden Gestaltungsbaustein aus. Wiederholen Sie diesen Vorgang, um die beiden anderen Bausteine einzufügen.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Klicken Sie nun auf den **[!UICONTROL Vorschau]**-Tab und wählen Sie einen Empfänger aus, um sich das Ergebnis der Personalisierung anzusehen.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Bestätigen Sie, dass die Inhalte der Bausteine korrekt angezeigt werden.

## Native Gestaltungsbausteine {#out-of-the-box-personalization-blocks}

Standardmäßig ist eine Liste mit Gestaltungsbausteinen verfügbar, um den Inhalt einer Nachricht zu personalisieren.

>[!NOTE]
>
>Die Liste der Gestaltungsbausteine hängt von den Modulen und Optionen ab, die auf Ihrer Instanz installiert sind.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Grußformeln]**: Hiermit werden Grußformeln mit dem Empfängernamen eingefügt, z. B. &quot;Guten Tag, Max Mustermann&quot;.
* **[!UICONTROL Logo einfügen]**: Hiermit wird ein natives Logo eingefügt, das beim Konfigurieren der Instanz definiert wurde.
* **[!UICONTROL Powered by Adobe Campaign]**: Hiermit wird das Logo &quot;Powered by Adobe Campaign&quot; eingefügt.
* **[!UICONTROL Mirrorseiten-URL]**: Hiermit wird die Mirrorseiten-URL eingefügt, damit Versanddesigner den Link prüfen können.

   >[!NOTE]
   >
   >Weitere Informationen zur Erstellung der Mirror-Seite finden Sie unter [Mirror-Seite erstellen](../../delivery/using/sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Mirrorseiten-Link]**: Hiermit wird der Link zur Mirrorseite &quot;Wenn die Nachricht nicht richtig angezeigt wird, bitte hier klicken&quot; eingefügt.
* **[!UICONTROL Abmelde-Link]**: Hiermit wird ein Link zur Abmeldung von allen Nachrichten (Blockierungsliste) eingefügt.
* **[!UICONTROL Formatierungsfunktion für Eigennamen]**: Hiermit wird die JavaScript-Funktion **[!UICONTROL toSmartCase]** erstellt, mit der der erste Buchstabe eines jeden Worts in einen Großbuchstaben umgewandelt wird. Dieser Baustein muss in den Quell-Code des Versands in **`<script>...</script>`**-Tags eingefügt werden.

   Im unten stehenden Beispiel wird mithilfe dieser Funktion das Element „Mein Header“ durch „Mein neuer Header“ mit Großbuchstaben für jedes Wort ersetzt:

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Anmeldungsseiten-URL]**: Hiermit wird eine Anmelde-URL eingefügt (siehe [Über Dienste und Abonnements](../../delivery/using/about-services-and-subscriptions.md)).
* **[!UICONTROL Anmelde-Link]**: Hiermit wird ein Anmelde-Link eingefügt, der beim Konfigurieren der Instanz definiert wurde.
* **[!UICONTROL Registrierungslink (mit Werber)]**: Hiermit wird ein Anmelde-Link eingefügt, über den der Besucher und der Versand identifiziert werden kann. Der Link wurde beim Konfigurieren der Instanz definiert.

   >[!NOTE]
   >
   >Dieser Baustein kann in Sendungen verwendet werden, die nur an Besucher gerichtet sind.

* **[!UICONTROL Anmeldebestätigung]**: Hiermit wird ein Link eingefügt, mit dem die Anmeldung bestätigt werden kann.
* **[!UICONTROL Teilen-Links der sozialen Netzwerke]**: Hiermit werden Schaltflächen eingefügt, mit denen der Empfänger mit dem E-Mail-Client sowie mit Facebook, Twitter, Google + und LinkedIn einen Link zum Mirror-Seiten-Inhalt teilen kann (siehe [Weiterleiten von Nachrichten](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Stil der Inhalts-E-Mails]** und **[!UICONTROL Stil der Benachrichtigungen]**: Hiermit wird Code erstellt, mit dem eine E-Mail mit nativen HTML-Stilen formatiert werden kann. Diese Bausteine müssen in den Quell-Code des Versands im Abschnitt **[!UICONTROL ...]** in **`<style>...</style>`**-Tags eingefügt werden.
* **[!UICONTROL Annahme-URL eines Angebots im Einzelmodus]**: Hiermit wird eine URL eingefügt, mit der ein Interaction-Angebot auf **[!UICONTROL Angenommen]** gesetzt werden kann (siehe [diesen Abschnitt](../../interaction/using/offer-analysis-report.md)).

## Benutzerdefinierte Gestaltungsbausteine definieren {#defining-custom-personalization-blocks}

Sie haben die Möglichkeit, neue Personalisierungsfelder zu konfigurieren, die dann über die entsprechende Schaltfläche ausgehend von der Option **[!UICONTROL Einfügen...]** verfügbar sind. Diese Felder werden in Gestaltungsbausteinen erstellt.

Gehen Sie wie folgt vor, um Gestaltungsbausteine zu erstellen:

1. Gehen Sie in den Knoten **[!UICONTROL Ressourcen > Kampagnenverwaltung > Gestaltungsbausteine]**.
1. Klicken Sie mit der rechten Maustaste in der Bausteinliste und wählen Sie die Option **[!UICONTROL Neu]** .
1. Konfigurieren Sie den Gestaltungsbaustein:

   ![](assets/s_ncs_user_personalized_block.png)

   * Benennen Sie den Baustein. Der hier angegebene Titel wird im Einfügefenster der Personalisierungsfelder angezeigt.
   * Wählen Sie die Option **[!UICONTROL Im Personalisierungsmenü anzeigen]**, um den Baustein in der Dropdown-Liste der Personalisierungsfelder verfügbar zu machen.
   * Bei Bedarf können Sie die Option **[!UICONTROL Der Inhalt des Bausteins ist formatabhängig (HTML oder Text)]** ankreuzen, um für jedes Format einen separaten Baustein zu konfigurieren.

      In diesem Fall wird das Fenster in zwei Tabs – HTML- und Textinhalt – unterteilt, um die formatbedingten Inhalte separat erfassen zu können.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Geben Sie den Inhalt der Gestaltungsbausteine (in HTML, Text, JavaScript usw.) ein und klicken Sie auf **[!UICONTROL Speichern]**.

## Personalisieren von E-Mails mit dynamischen Inhaltsbausteinen {#personalization-blocks-video}

Erfahren Sie, wie Sie dynamische Inhaltsblöcke erstellen und diese zur Personalisierung des Inhalts Ihres E-Mail-Versands verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12&captions=ger)
