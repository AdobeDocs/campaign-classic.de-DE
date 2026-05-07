---
product: campaign
title: Inbox Rendering in Campaign
description: Erfahren Sie, wie Sie E-Mail-Renderings erfassen und in einem speziellen Bericht verfügbar machen
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 72%

---

# Rendern des Posteingangs{#inbox-rendering}

## Über Inbox Rendering {#about-inbox-rendering}

Bevor Sie die Schaltfläche **Senden** betätigen, sollten Sie sicherstellen, dass Ihre Nachricht den Empfängern in unterschiedlichen Webclients, Webmails und Geräten optimal dargestellt wird.

Um dies zu ermöglichen, nutzt Adobe Campaign die [Litmus](https://litmus.com/email-testing) Web-basierte E-Mail-Testlösung, um die Renderings zu erfassen und in einem dedizierten Bericht verfügbar zu machen. Auf diese Weise können Sie eine Vorschau der gesendeten Nachricht in den verschiedenen Kontexten anzeigen, in denen sie empfangen werden kann, und die Kompatibilität mit den wichtigsten Desktops und Anwendungen überprüfen.

>[!CAUTION]
>Inbox Rendering ist nicht kompatibel mit dem [wiederkehrenden Versand](communication-channels.md#recurring-delivery).
>

Litmus ist eine funktionsreiche E-Mail-Validierungs- und Vorschau-Anwendung. Damit können Ersteller von E-Mail-Inhalten ihren Nachrichteninhalt in über 70 E-Mail-Renderern in der Vorschau anzeigen, z. B. im Gmail-Posteingang oder im Apple Mail-Client.

Die für das **Inbox Rendering** in Adobe Campaign verfügbaren Clients für Mobilgeräte, SMS und Webmail finden Sie auf der Litmus-[Website](https://litmus.com/email-testing) (wählen Sie dazu die Option zum **Anzeigen aller E-Mail-Clients** aus).

>[!NOTE]
>
>Zum Testen der Personalisierung in Sendungen ist kein Inbox Rendering nötig. Die Personalisierung kann auch mit Adobe Campaign-Tools wie der **[!UICONTROL Vorschau]** und mit Testsendungen überprüft werden. Weiterführende Informationen dazu finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=de){target="_blank"}.

## Inbox Rendering aktivieren {#activating-inbox-rendering}

[!BADGE Hybrid und On-Premise]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"}

Für gehostete und hybride Clients wird das Inbox Rendering auf Ihrer Instanz vom technischen Support und von Beratern von Adobe konfiguriert. Weiterführende Informationen dazu erhalten Sie von Ihrem Adobe-Kundenbetreuer.

Gehen Sie bei On-Premise-Installationen wie folgt vor, um das Inbox Rendering zu konfigurieren.

1. Installieren Sie das **[!UICONTROL Inbox Rendering (IR)]**-Package über das Menü **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package-Import]**. Weitere Informationen hierzu finden Sie unter [Installieren von nativen Campaign Classic-Packages](../../installation/using/installing-campaign-standard-packages.md).
1. Konfigurieren Sie ein externes HTTP-Konto über den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]**. Weitere Informationen hierzu finden Sie unter [Externes Konto erstellen](../../installation/using/external-accounts.md#creating-an-external-account).
1. Legen Sie die Parameter für das externe Konto wie folgt fest:
   * **[!UICONTROL Titel]**: Zustellbarkeits-Server-Information
   * **[!UICONTROL Interner Name]**: deliverabilityInstance
   * **[!UICONTROL Typ]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Verschlüsselung]**: Keine
   * Kreuzen Sie die Option **[!UICONTROL Aktiviert]** an.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Wechseln Sie zum Knoten **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]**. Suchen Sie nach der Option **[!UICONTROL DmRendering_cuid]** und wenden Sie sich an den Support, um die ID der Versandberichte abzurufen, die in das Feld **[!UICONTROL Wert (Text)]** kopiert werden muss.
1. Bearbeiten Sie die Datei **serverConf.xml**, um einen Aufruf an den Litmus-Server zuzulassen. Fügen Sie dem Abschnitt `<urlPermission>` die folgende Zeile hinzu:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Laden Sie die Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Möglicherweise müssen Sie sich von der Konsole abmelden und sich wieder anmelden, um das Inbox Rendering verwenden zu können.

## Über Litmus-Token {#about-litmus-tokens}

Da Litmus ein Drittanbieterdienst ist, funktioniert es nach einem Kredit-pro-Nutzung-Modell. Jedes Mal, wenn ein Benutzer die Litmus-Funktion aufruft, wird eine Gutschrift abgezogen.

In Adobe Campaign entspricht das Guthaben der Anzahl der verfügbaren Renderings (auch Tokens genannt).

>[!NOTE]
>
>Die Anzahl der verfügbaren Litmus-Token hängt von der von Ihnen erworbenen Campaign-Lizenz ab. Überprüfen Sie Ihre Lizenzvereinbarung.

Jedes Mal, wenn Sie in einem Versand die Funktion **[!UICONTROL Inbox Rendering]** verwenden, wird die verfügbare Anzahl der Token um jeweils eins verringert.

>[!IMPORTANT]
>
>Token werden für jedes einzelne Rendering abgezogen, und nicht für den gesamten Inbox-Rendering-Bericht.
>
>* Das bedeutet, dass jedes Mal, wenn ein Inbox-Rendering-Bericht erstellt wird, pro E-Mail-Client ein Token abgezogen wird: ein Token für das Rendering in Outlook 2000, einer für das Rendering in Outlook 2010, einer für das Rendering in Apple Mail 9 usw.
>* Wenn Sie für denselben Versand das Inbox Rendering wiederholen, wird die Anzahl der verfügbaren Token nochmals um die Anzahl der erzeugten Renderings reduziert.
>

Die Anzahl der restlichen verfügbaren Token wird im [Inbox-Rendering-Bericht](#inbox-rendering-report) angezeigt.

![](assets/s_tn_inbox_rendering_tokens.png)

Normalerweise wird die Rendering-Funktion für den Posteingang verwendet, um das HTML-Framework einer neu entworfenen E-Mail zu testen. Für jedes Rendering sind etwa 70 Token erforderlich (je nach der Anzahl der Umgebungen, in denen im Allgemeinen getestet wird). In einigen Fällen benötigen Sie jedoch möglicherweise mehrere Inbox Rendering-Berichte, um Ihren Versand vollständig zu testen. Daher kann es mehr Token erfordern, um mehrere Prüfungen durchzuführen.

## Inbox-Rendering-Bericht aufrufen {#accessing-the-inbox-rendering-report}

Nachdem Sie Ihren E-Mail-Versand erstellt und seinen Inhalt sowie die Zielpopulation definiert haben, folgen Sie den unten stehenden Schritten.

Weiterführende Informationen zur Erstellung, Konzeption und Ausrichtung eines Versands finden Sie in [diesem Abschnitt](about-email-channel.md).

1. Wählen Sie in der Symbolleiste des Versands die Schaltfläche **[!UICONTROL Inbox Rendering]** aus.
1. Wählen Sie **[!UICONTROL Analysieren]** aus, um den Aufnahmeprozess zu starten.

   ![](assets/s_tn_inbox_rendering_button.png)

   Ein Testversand wird durchgeführt. Die Rendering-Miniaturen können in diesem Korrekturabzug einige Minuten nach dem Senden der E-Mails aufgerufen werden. Weitere Informationen zum Durchführen eines Testversands finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=de){target="_blank"}.

1. Nach dem Versand wird der Testversand in der Versandliste angezeigt. Doppelklicken Sie darauf.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Gehen Sie zum Tab **Inbox Rendering** des Testversands.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Der Inbox-Rendering-Bericht wird angezeigt.

## Inbox-Rendering-Bericht {#inbox-rendering-report}

Dieser Bericht zeigt die Inbox Renderings so an, wie sie dem Empfänger angezeigt werden. Die Renderings können je nachdem, wie der Empfänger den E-Mail-Versand öffnet, unterschiedlich sein: im Browser, auf einem Mobilgerät oder über eine E-Mail-Anwendung.

Im oberen Bereich wird in einer grafischen, farbcodierten Darstellung die Aufteilung der Anzahl der empfangenen, unerwünschten (Spam) und nicht empfangenen Nachrichten angezeigt und die Anzahl der Nachrichten, deren Empfang aussteht.

![](assets/s_tn_inbox_rendering_summary.png){width="40%" align="left"}

Bewegen Sie den Mauszeiger über das Diagramm, um Informationen zu jeder Farbe aufzurufen. Klicken Sie auf ein Element in der Liste, um die entsprechende Kategorie im Diagramm auszublenden oder anzuzeigen.

Der Hauptteil des Berichts ist in drei Teile unterteilt: **[!UICONTROL Mobilgerät]**, **[!UICONTROL Desktop]** und **[!UICONTROL Webmails]**. Scrollen Sie im Bericht nach unten, um alle in diese drei Kategorien eingeteilten Renderings anzusehen.

![](assets/s_tn_inbox_rendering_report.png)

Klicken Sie auf eine der Karten, um das entsprechende Rendering im Detail anzusehen. Das Rendering wird für das jeweils ausgewählte Empfangsmedium angezeigt.

![](assets/s_tn_inbox_rendering_example.png)
