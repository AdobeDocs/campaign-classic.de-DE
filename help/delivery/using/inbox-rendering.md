---
title: Inbox Rendering
seo-title: Inbox Rendering
description: Inbox Rendering
seo-description: null
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 30f313cecf1c3d7c65f6524a3f86a1c28b35f679

---


# Inbox Rendering{#inbox-rendering}

## Über Inbox Rendering {#about-inbox-rendering}

Bevor Sie die Schaltfläche **Senden** betätigen, sollten Sie sicherstellen, dass Ihre Nachricht den Empfängern in unterschiedlichen Webclients, Webmails und Geräten optimal dargestellt wird.

Zu diesem Zweck nutzt Adobe Campaign die webbasierte E-Mail-Test-Software [Litmus](https://litmus.com/email-testing), mit der die Darstellung der Seiten sichtbar und in einem Bericht verfügbar gemacht werden kann. Dadurch haben Sie die Möglichkeit, sich die gesendete Nachricht als Vorschau in den unterschiedlichen Umgebungen der Empfänger anzusehen und die Kompatibilität mit den wichtigsten Desktops und Anwendungen zu überprüfen.

Litmus verfügt über zahlreiche Funktionen zur E-Mail-Validierung und Vorschau. Autoren von E-Mail-Inhalten können Nachrichten in der Vorschau in über 70 E-Mail-Rendering-Systemen betrachten, wie z. B. im Gmail-Posteingang oder im Apple Mail Client.

Die für das **Inbox Rendering** in Adobe Campaign verfügbaren Clients für Mobilgeräte, SMS und Webmail finden Sie auf der Litmus-[Website](https://litmus.com/email-testing) (wählen Sie dazu die Option zum **Anzeigen aller E-Mail-Clients** aus).

>[!NOTE]
>
>Das Inbox-Rendering ist nicht erforderlich, um die Personalisierung in Auslieferungen zu testen. Die Personalisierung kann mit Adobe Campaign-Tools wie **[!UICONTROL Preview]** und [Proofs](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)überprüft werden.

## Aktivieren des Inbox-Renderings{#activating-inbox-rendering}

Für gehostete und hybride Clients wird das Inbox-Rendering auf Ihrer Instanz vom technischen Support und von Beratern von Adobe konfiguriert. Weitere Informationen erhalten Sie von Ihrem Adobe-Kundenbetreuer.

Gehen Sie bei lokalen Installationen wie folgt vor, um das Rendering von Posteingängen zu konfigurieren.

1. Installieren Sie das **[!UICONTROL Inbox rendering (IR)]** Paket über das Menü **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Weitere Informationen hierzu finden Sie unter [Installieren der Standardpakete](../../installation/using/installing-campaign-standard-packages.md)von Campaign Classic.
1. Konfigurieren Sie ein externes Konto des HTTP-Typs über den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** . For more on this, see [Creating an external account](../../platform/using/external-accounts.md#creating-an-external-account).
1. Legen Sie die Parameter für das externe Konto wie folgt fest:
   * **[!UICONTROL Label]**: Informationen zum Bereitstellungsserver
   * **[!UICONTROL Internal name]**: deliveryInstance
   * **[!UICONTROL Type]**:HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Keiner
   * Aktivieren Sie die **[!UICONTROL Enabled]** Option.
   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Wechseln Sie zum Knoten **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** . Suchen Sie nach der **[!UICONTROL DmRendering_cuid]** Option und wenden Sie sich an den Support, um die ID der Lieferberichte abzurufen, die in das **[!UICONTROL Value (text)]** Feld kopiert werden muss.
1. Bearbeiten Sie die Datei &quot; **serverConf.xml** &quot;, um einen Aufruf an den Litmus-Server zuzulassen. Fügen Sie dem `<urlPermission>` Abschnitt die folgende Zeile hinzu:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Laden Sie die Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Möglicherweise müssen Sie sich von der Konsole abmelden und sich wieder anmelden, um das Inbox-Rendering verwenden zu können.

## Über Litmus-Token {#about-litmus-tokens}

Da Litmus ein Dienst eines Drittanbieters ist, wird für jede Nutzung eine Gebühr erhoben. Jedes Mal, wenn ein Benutzer die Litmus-Funktion aufruft, wird ein bestimmter Betrag vom Guthaben abgezogen.

In Adobe Campaign entspricht das Guthaben der Anzahl der verfügbaren Renderings (auch Tokens genannt).

>[!NOTE]
>
>Die Anzahl der verfügbaren Litmus-Token hängt von der von Ihnen erworbenen Campaign-Lizenz ab. Diese Information können Sie Ihrem Lizenzabkommen entnehmen.

Jedes Mal, wenn Sie in einem Versand die Funktion **[!UICONTROL Inbox rendering]** verwenden, wird die verfügbare Anzahl der Token um jeweils eins verringert.

>[!IMPORTANT]
>
>Token werden für jedes einzelne Rendering abgezogen, und nicht für den gesamten Inbox-Rendering-Bericht.
>
>* Das bedeutet, dass jedes Mal, wenn ein Inbox-Rendering-Bericht erstellt wird, pro E-Mail-Client ein Token abgezogen wird: ein Token für das Rendering in Outlook 2000, einer für das Rendering in Outlook 2010, einer für das Rendering in Apple Mail 9 usw.
>* Wenn Sie für denselben Versand das Inbox Rendering wiederholen, wird die Anzahl der verfügbaren Token nochmals um die Anzahl der erzeugten Renderings reduziert.
>



Die Anzahl der verbleibenden verfügbaren Token wird im Bericht **[!UICONTROL General summary]** zum Rendern [ des ](#inbox-rendering-report)Posteingangs angezeigt.

![](assets/s_tn_inbox_rendering_tokens.png)

Normalerweise wird die Inbox-Rendering-Funktion zum Testen des HTML-Gerüsts einer neu erstellten E-Mail verwendet. Pro Rendering sind ca. 70 Token erforderlich (abhängig von der Anzahl der getesteten Umgebungen). In manchen Fällen sind aber mehrere Inbox-Rendering-Berichte erforderlich, um Ihren Versand vollständig zu testen. Es könnte deshalb eine größere Anzahl von Token nötig sein, um mehrere Prüfungen durchzuführen.

>[!NOTE]
>
>Wenn Sie Litmus-Kunde sind, können Sie Ihr eigenes Litmus-Konto für das Inbox Rendering in Adobe Campaign verwenden. Weiterführende Informationen dazu erhalten Sie von Ihrem Adobe-Kundenbetreuer.
>
>Bitte beachten Sie, dass eine Änderung Ihrer Litmus-Zugangsdaten Authentifizierungsprobleme innerhalb Adobe Campaign verursachen kann.

## Inbox-Rendering-Bericht aufrufen {#accessing-the-inbox-rendering-report}

Nachdem Sie Ihren E-Mail-Versand erstellt und seinen Inhalt sowie die Zielpopulation definiert haben, folgen Sie den unten stehenden Schritten.

Weiterführende Informationen zur Erstellung, Konzeption und Ausrichtung eines Versands finden Sie in [diesem Abschnitt](../../delivery/using/about-email-channel.md).

1. Wählen Sie in der Symbolleiste des Versands die Schaltfläche **[!UICONTROL Inbox rendering]** aus.
1. Select **[!UICONTROL Analyze]** to start the capture process.

   ![](assets/s_tn_inbox_rendering_button.png)

   Ein Testversand wird durchgeführt. Nur wenige Minuten nach dem Absenden der E-Mails kann auf die Rendering-Miniaturansichten in diesem Testversand zugegriffen werden. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. Nach dem Absenden erscheint der Testversand in der Versandliste. Dort kann er durch einen Doppelklick geöffnet werden.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Gehen Sie zum Tab **Inbox Rendering** des Testversands.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Der Inbox-Rendering-Bericht wird angezeigt.

## Inbox-Rendering-Bericht {#inbox-rendering-report}

Dieser Bericht enthält Informationen zum Inbox Rendering, d. h. zur Darstellung der E-Mail in der Inbox des Empfängers. Die Renderings können unterschiedlich aussehen, je nachdem ob die E-Mail in einem Browser, auf einem Mobilgerät oder über eine E-Mail-Anwendung geöffnet wird.

The **[!UICONTROL General summary]** presents the number of messages received, unwanted (spam), not received, or pending reception, as a list and through a graphical color-coded representation.

![](assets/s_tn_inbox_rendering_summary.png)

Bewegen Sie die Maus über das Diagramm, um Informationen zu jeder Farbe aufzurufen.

Der Bericht ist in drei Teile untergliedert: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** und **[!UICONTROL Webmails]**. Scrollen Sie im Bericht nach unten, um alle in diese drei Kategorien eingeteilten Renderings anzusehen.

![](assets/s_tn_inbox_rendering_report.png)

Klicken Sie auf eine der Karten, um das entsprechende Rendering im Detail anzusehen. Das Rendering wird für das jeweils ausgewählte Empfangsmedium angezeigt.

![](assets/s_tn_inbox_rendering_example.png)
