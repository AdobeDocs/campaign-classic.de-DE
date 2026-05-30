---
product: campaign
title: Gestaltungsbausteine
description: Erfahren Sie, wie Sie Gestaltungsbausteine verwenden
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Personalization
role: User
hide: true
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
TQID: https://experienceleague.adobe.com/KfD6zudZg8B6r8ftdINuXjWAqRiHLP9dtGi--H-E6RU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1002
ht-degree: 86%

---

# Gestaltungsbausteine{#personalization-blocks}

Gestaltungsbausteine sind dynamisch und personalisiert und enthalten ein spezifisches Rendering, das Sie in Ihre Sendungen einfügen können. Sie können zum Beispiel ein Logo, eine Grußnachricht oder einen Link zur Mirrorseite hinzufügen. Siehe [Einfügen von Gestaltungsbausteinen](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png) [&#x200B; Mehr zu dieser Funktion erfahren Sie im Video.](#personalization-blocks-video).

Auf Gestaltungsbausteine kann im Adobe Campaign-Explorer über den Knoten **[!UICONTROL Ressourcen > Kampagnenverwaltung > Gestaltungsbausteine]** zugegriffen werden. Standardmäßig sind verschiedene Bausteine verfügbar (siehe [Native Gestaltungsbausteine](#out-of-the-box-personalization-blocks)).

Sie haben die Möglichkeit, neue Bausteine zu definieren, mit denen Sie die Personalisierung Ihrer Sendungen verbessern können. Weitere Informationen hierzu finden Sie unter [Definieren von benutzerdefinierten Gestaltungsbausteinen](#defining-custom-personalization-blocks).

>[!NOTE]
>
>Gestaltungsbausteine sind auch im **[!UICONTROL Digital Content Editor (DCE)]** verfügbar. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../web/using/editing-content.md#inserting-a-personalization-block).

## Einfügen von Gestaltungsbausteinen {#inserting-personalization-blocks}

Gehen Sie folgendermaßen vor, um Gestaltungsbausteine in eine Nachricht einzufügen:

1. Wählen Sie im Inhaltseditor des Versandassistenten das Personalisierungssymbol und danach das Menü **[!UICONTROL Einfügen]** aus.
1. Wählen Sie einen Gestaltungsbaustein aus der Liste aus (die Liste zeigt die 10 zuletzt verwendeten Bausteine an), oder klicken Sie auf das Menü **[!UICONTROL Sonstiges...]**, um die vollständige Liste aufzurufen.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Das Menü **[!UICONTROL Sonstige...]** ermöglicht den Zugriff auf alle standardmäßigen und benutzerdefinierten Gestaltungsbausteine (siehe [Standardmäßige Gestaltungsbausteine](#out-of-the-box-personalization-blocks) und [Definieren von benutzerdefinierten Gestaltungsbausteinen](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Der Gestaltungsbaustein wird dann als Skript eingefügt. Er wird bei der Personalisierung automatisch an das Empfängerprofil angepasst.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Klicken Sie nun auf den **[!UICONTROL Vorschau]**-Tab und wählen Sie einen Empfänger aus, um das Ergebnis der Personalisierung anzusehen.

   ![](assets/s_ncs_user_personalized_block04.png)

Sie können den Quell-Code eines Gestaltungsbausteins in den Versandinhalt einfügen. Wählen Sie die Option **[!UICONTROL HTML-Quell-Code des Bausteins einfügen]** aus.

![](assets/s_ncs_user_personalized_block05.png)

Der HTML-Quell-Code wird in den Versandinhalt eingefügt. Beispielsweise wird der Gestaltungsbaustein **[!UICONTROL Grußformeln]** wie folgt angezeigt:

![](assets/s_ncs_user_personalized_block06.png)

## Beispiel für Gestaltungsbausteine {#personalization-blocks-example}

In diesem Beispiel erstellen wir eine E-Mail, in der wir Gestaltungsbausteine verwenden, durch die der Empfänger die Mirrorseite ansehen, den Newsletter in sozialen Netzwerken teilen und sich von künftigen Sendungen abmelden kann.

Zu diesem Zweck müssen wir folgende Gestaltungsbausteine einfügen:

* **[!UICONTROL Link zur Mirrorseite]** .
* **[!UICONTROL Teilen-Links der sozialen Netzwerke]** .
* **[!UICONTROL Abmelde-Link]** .

>[!NOTE]
>
>Weitere Informationen zur Erstellung der Mirrorseite finden Sie unter [Erzeugen der Mirrorseite](sending-messages.md#generating-the-mirror-page).

1. Erstellen Sie einen neuen Versand oder öffnen Sie einen existierenden E-Mail-Versand.
1. Klicken Sie im Versandassistenten auf den **[!UICONTROL Betreff]**, um den Betreff der Nachricht zu bearbeiten und einen Betreff einzugeben.
1. Fügen Sie die Gestaltungsbausteine in den Nachrichtentext ein. Klicken Sie dazu in das Inhaltsfeld der Nachricht und danach auf die Schaltfläche zum Einfügen von Personalisierungsfeldern. Wählen Sie danach das Menü **[!UICONTROL Einfügen]** aus.
1. Den ersten einzufügenden Block auswählen. Erneuern Sie das Verfahren, um die beiden anderen Blöcke einzubeziehen.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Klicken Sie auf **[!UICONTROL Vorschau]**, um das Personalisierungsergebnis anzuzeigen. Sie müssen einen Empfänger auswählen, um die Nachricht dieses Empfängers anzuzeigen.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Bestätigen Sie, dass die Inhalte der Bausteine korrekt angezeigt werden.

## Native Gestaltungsbausteine {#out-of-the-box-personalization-blocks}

Standardmäßig ist eine Liste mit Gestaltungsbausteinen verfügbar, um den Inhalt einer Nachricht zu personalisieren.

>[!NOTE]
>
>Die Liste der Gestaltungsbausteine hängt von den Modulen und Optionen ab, die auf Ihrer Instanz installiert sind.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Grußformeln]** : Hiermit werden Grußformeln zum Empfängernamen hinzugefügt. Beispiel: „Sehr geehrter Herr Mustermann,“.
* **[!UICONTROL Logo einfügen]**: Hiermit wird ein natives Logo eingefügt, das beim Konfigurieren der Instanz definiert wurde.
* **[!UICONTROL Powered by Adobe Campaign]**: Hiermit wird das Logo &quot;Powered by Adobe Campaign&quot; eingefügt.
* **[!UICONTROL Mirrorseiten-URL]**: Hiermit wird die Mirrorseiten-URL eingefügt, damit Versanddesigner den Link prüfen können.

  >[!NOTE]
  >
  >Weitere Informationen zur Erstellung der Mirrorseite finden Sie unter [Erzeugen der Mirrorseite](sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link zur Mirrorseite]**: Hiermit wird der Link zur Mirrorseite „Wenn die Nachricht nicht richtig angezeigt wird, bitte hier klicken“ eingefügt.
* **[!UICONTROL Abmelde-Link]**: Hiermit wird ein Link zur Abmeldung von allen Nachrichten (Blockierungsliste) eingefügt.
* **[!UICONTROL Formatierungsfunktion für Eigennamen]**: Hiermit wird die JavaScript-Funktion **[!UICONTROL toSmartCase]** erstellt, mit der der erste Buchstabe eines jeden Worts in einen Großbuchstaben umgewandelt wird.
* **[!UICONTROL Anmeldungsseiten-URL]**: Hiermit wird eine Anmelde-URL eingefügt (siehe [Über Dienste und Abonnements](about-services-and-subscriptions.md)).
* **[!UICONTROL Anmelde-Link]**: Hiermit wird ein Anmelde-Link eingefügt. der beim Konfigurieren der Instanz definiert wurde.
* **[!UICONTROL Anmelde-Link (mit Werber)]**: Hiermit wird ein Anmelde-Link eingefügt, über den der Besucher bzw. die Besucherin sowie der Versand identifiziert werden können. Der Link wurde beim Konfigurieren der Instanz definiert.

  >[!NOTE]
  >
  >Dieser Baustein kann in Sendungen verwendet werden, die nur an Besucher gerichtet sind.

* **[!UICONTROL Anmeldebestätigung]**: Hiermit wird ein Link eingefügt, mit dem die Anmeldung bestätigt werden kann.
* **[!UICONTROL Links zum Teilen in sozialen Netzwerken]**: fügt Schaltflächen ein, die es den Empfängerinnen und Empfängern ermöglichen, einen Link zum Inhalt der Mirrorseite mit dem E-Mail-Client, Facebook, X (früher bekannt als Twitter) und LinkedIn zu teilen (weitere Informationen finden Sie unter [Virales Marketing: Weiterleiten an eine Freundin oder einen Freund](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Stil der Inhalts-E-Mails]** und **[!UICONTROL Stil der Benachrichtigungen]**: Hiermit wird Code erstellt, mit dem eine E-Mail mit nativen HTML-Stilen formatiert werden kann. Diese Bausteine müssen in den Quell-Code des Versands im Abschnitt **[!UICONTROL ...]** in **`<style>...</style>`**-Tags eingefügt werden.
* **[!UICONTROL Annahme-URL eines Angebots im Einzelmodus]**: Hiermit wird eine URL eingefügt, mit der ein Interaction-Angebot auf **[!UICONTROL Angenommen]** gesetzt werden kann (siehe [diesen Abschnitt](../../interaction/using/offer-analysis-report.md)).

## Definieren von benutzerdefinierten Gestaltungsbausteinen {#defining-custom-personalization-blocks}

Über das Symbol Personalisierte Felder können Sie neue Personalisierungsfelder definieren, die über das Menü **[!UICONTROL Einfügen…]** eingefügt werden sollen. Diese Felder werden in Gestaltungsbausteinen definiert.

Gehen Sie im Explorer wie folgt vor, um Gestaltungsbausteine zu erstellen:

1. Gehen Sie in den Knoten **[!UICONTROL Ressourcen > Kampagnenverwaltung > Gestaltungsbausteine]**.
1. Klicken Sie mit der rechten Maustaste in der Bausteinliste und wählen Sie die Option **[!UICONTROL Neu]** .
1. Konfigurieren Sie den Gestaltungsbaustein:

   ![](assets/s_ncs_user_personalized_block.png)

   * Geben Sie den Titel des Bausteins ein. Dieser Titel wird im Einfügefenster des Personalisierungsfelds angezeigt.
   * Wählen Sie die Option **[!UICONTROL Im Personalisierungsmenü anzeigen]**, um den Baustein in der Dropdown-Liste der Personalisierungsfelder verfügbar zu machen.
   * Bei Bedarf können Sie die Option **[!UICONTROL Der Inhalt des Bausteins ist formatabhängig (HTML oder Text)]** ankreuzen, um für jedes Format einen separaten Baustein zu konfigurieren.

     In diesem Fall wird das Fenster in zwei Tabs – HTML- und Textinhalt – unterteilt, um die formatbedingten Inhalte separat erfassen zu können.

     ![](assets/s_ncs_user_personalized_block_b.png)

   * Inhalt eingeben (in HTML, Text, JavaScript usw.) der Gestaltungsbausteine und klicken Sie auf **[!UICONTROL Speichern]**.

## Anleitungsvideo {#personalization-blocks-video}

Erfahren Sie, wie Sie dynamische Inhaltsbausteine erstellen und diese zur Personalisierung des Inhalts Ihres E-Mail-Versands verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
