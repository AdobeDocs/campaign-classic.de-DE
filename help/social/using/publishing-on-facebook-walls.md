---
title: Auf Facebook-Pinnwänden publizieren
seo-title: Auf Facebook-Pinnwänden publizieren
description: Auf Facebook-Pinnwänden publizieren
seo-description: null
page-status-flag: never-activated
uuid: 02288473-a0d7-42b5-9f86-3c96550ab1a8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 8577db0b-f1fc-41af-aa0f-ec4d02dac376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0386ae88a1b4d9ebda64283d874e01b14e9e5af4
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 98%

---


# Auf Facebook-Pinnwänden publizieren{#publishing-on-facebook-walls}

Damit Adobe Campaign Publikationen an Facebook-Pinnwände senden kann, müssen Sie den Schreibzugriff für diese Seiten an Adobe Campaign delegieren. Dies umfasst die folgenden Konfigurationsschritte:

1. Erstellen Sie ein Facebook-Konto mit einer oder mehreren Seiten.
1. Erstellen Sie eine Facebook-Testseite zum Senden von Testsendungen.
1. Erstellen Sie eine Facebook-Anwendung.
1. Geben Sie die Einstellungen der Facebook-Anwendung in Adobe Campaign im externen **[!UICONTROL Facebook-Routing]**-Konto ein.

## Voraussetzungen {#prerequisites}

Erstellen Sie zunächst ein Facebook-Konto und mehrere Seiten: Diese werden zum Senden von Publikationen verwendet.

* Verwenden Sie den Link [https://www.facebook.com](https://www.facebook.com), um ein Facebook-Konto zu erstellen.
* To create a Facebook page, use the [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) link.

   Es wird empfohlen, alle Seiten mit demselben Facebook-Konto zu verwalten. Auf diese Weise benötigen Sie nur eine Facebook-Anwendung und ein externes Konto, um auf allen Seiten des Kontos zu schreiben.

   ![](assets/social_diagram_fb_external_account.png)

## Facebook-Testseite erstellen {#creating-a-test-facebook-page}

Es wird empfohlen, eine private Facebook-Seite zu erstellen, um Testsendungen für die Publikation durchzuführen (weitere Informationen hierzu finden Sie unter [Testversand durchführen](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Melden Sie sich bei dem Facebook-Konto an, mit dem Sie Ihre Seiten verwalten.
1. Erstellen Sie eine neue Facebook-Seite.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Einstellungen]** oben rechts.
1. Ändern Sie im Tab **[!UICONTROL Allgemein]** die Sichtbarkeitsparameter der Seite: Markieren Sie das Feld **[!UICONTROL Seite unveröffentlicht]**.
1. Wählen Sie die Schaltfläche **[!UICONTROL Speichern]** aus.

![](assets/social_facebook_test_page.png)

## Erstellen einer Facebook-Anwendung {#creating-a-facebook-application}

Damit Adobe Campaign auf den Pinnwänden Ihrer Seiten publizieren kann, müssen Sie eine Facebook-Anwendung erstellen. Gehen Sie hierzu wie folgt vor:

1. Melden Sie sich bei dem Facebook-Konto an, mit dem Sie Seiten verwalten.
1. Geben Sie folgende Adresse in Ihren Browser ein: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >Je nach dem von Ihnen verwendeten Kontotyp können eine oder mehrere Autorisierungen erforderlich sein.
   >
   >Zum Erstellen einer Facebook-Anwendung benötigen Sie ein **bestätigtes** Facebook-Konto.

1. Klicken Sie oben rechts auf der Seite auf die Schaltfläche **[!UICONTROL Neue App hinzufügen]**. Geben Sie einen App-Namen und eine Kontakt-E-Mail ein und durchlaufen Sie dann die Sicherheitsprüfung.

   ![](assets/social_create_facebook_app_002.png)

1. Klicken Sie unter **[!UICONTROL Einstellungen > Einfach]** auf **[!UICONTROL Plattform hinzufügen]** und wählen Sie den Typ **[!UICONTROL Facebook-Web-Spiele]** aus.

   ![](assets/social_create_facebook_app_003.png)

1. Überprüfen Sie im Abschnitt **[!UICONTROL Produkte]** im linken Menü, ob das Produkt für die **[!UICONTROL Facebook-Anmeldung]** angezeigt wird. Wenn nicht, fügen Sie ein neues Produkt hinzu und wählen Sie **[!UICONTROL Facebook-Anmeldung]** aus.

   ![](assets/social_create_facebook_app_003bis.png)

1. Nachdem die Anwendung erstellt wurde, wählen Sie den Tab **[!UICONTROL App-Überprüfung]** aus und publizieren Sie die Anwendung.

   ![](assets/social_create_facebook_app_004.png)

## Schreibzugriff an Adobe Campaign delegieren {#delegating-write-access-to-adobe-campaign}

Um den Schreibzugriff zum Posten auf den Pinnwänden Ihrer Seiten an Adobe Campaign zu delegieren, müssen Sie die Parameter der zuvor erstellten Facebook-Anwendung eingeben.

Dieser Schritt erfordert Zugriff auf Ihre Adobe Campaign-Konsole und einen Internet-Browser, der beim Facebook-Konto angemeldet ist, das Sie für die Seitenverwaltung verwenden:

>[!IMPORTANT]
>
>Der Adobe Campaign-Benutzer muss über Administratorrechte verfügen, um diese Konfiguration durchführen zu können.

* **Facebook**: Wählen Sie die zuvor erstellte Anwendung ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) aus und klicken Sie auf den Tab **[!UICONTROL Einstellungen > Einfach]**.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Wenn der Abschnitt **[!UICONTROL Facebook-Web-Spiele]** nicht angezeigt wird, klicken Sie auf die Schaltfläche **[!UICONTROL Plattform hinzufügen]** unten auf der Seite und wählen Sie **[!UICONTROL Facebook-Web-Spiele]** aus.

* **Adobe Campaign**: Wechseln Sie zum Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** im Baum, wählen Sie das externe **[!UICONTROL Facebook-Routing]**-Konto aus und klicken Sie auf den Tab **[!UICONTROL Connector]**.

   ![](assets/social_facebook_external_account_001.png)

1. Kopieren Sie in der Adobe Campaign-Konsole die im Feld **[!UICONTROL Sichere Canvas-URL]** enthaltene Adresse und fügen Sie sie in das Feld **[!UICONTROL Sichere Web-Spiele-URL (https)]** in Facebook (im Abschnitt **[!UICONTROL Facebook-Web-Spiele]**) ein.

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >Sie dürfen unter keinen Umständen die unsichere URL verwenden.

   Kopieren Sie diese URL und fügen Sie sie auch unter **[!UICONTROL Produkte]** > **[!UICONTROL Facebook-Anmeldung]** > **[!UICONTROL Einstellungen]** > **[!UICONTROL Gültige OAuth-Redirect-URIs]** ein. Um die Gültigkeit der URL zu überprüfen, speichern Sie die Anwendung, kopieren Sie die URL und fügen Sie sie in das Feld **[!UICONTROL Weiterleitungs-URI zur Prüfung]** ein und klicken Sie auf **[!UICONTROL URI prüfen]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. Kopieren Sie auf Facebook den Inhalt der Felder **[!UICONTROL App-ID]** und **[!UICONTROL App-Geheimnis]** und fügen Sie ihn in die entsprechenden Felder der Konsole ein.

   ![](assets/social_facebook_external_account_007.png)

1. Klicken Sie auf Facebook unten auf der Seite auf die Schaltfläche **[!UICONTROL Änderungen speichern]**.
1. Wechseln Sie zur Adobe Campaign-Konsole und speichern Sie das externe Konto.

   >[!NOTE]
   >
   >Das Feld **[!UICONTROL Marketing-URL]** ist optional.

1. Klicken Sie in der Adobe Campaign-Konsole auf den Link **[!UICONTROL Zulassung von der Anwendung einholen]** unten im Tab **[!UICONTROL Connector]**. Der Workflow **[!UICONTROL Facebook-Seiten-Synchronisation]** wird automatisch ausgelöst und erfasst alle vom Administrator verwalteten Facebook-Seiten. Weitere Informationen hierzu finden Sie unter [Facebook-Seiten-Synchronisation](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Standardmäßig werden die Seiten dem **[!UICONTROL Facebook]**-Dienstordner hinzugefügt, der über den Knoten **[!UICONTROL Profile und Zielgruppen > Dienste und Abonnements]** verfügbar ist. Im Feld **[!UICONTROL Ordner]** im Tab **[!UICONTROL Connector]** können Sie den Dienstordner ändern, in dem die Facebook-Seiten nach der Synchronisierung erstellt werden. Sie können auch mithilfe des Feldes **[!UICONTROL Filter]** die Facebook-Seiten auswählen, die Sie in Adobe Campaign synchronisieren möchten. Wenn Sie dieses Feld leer lassen, werden alle vom Administrator verwalteten Facebook-Seiten synchronisiert.

1. Ein Dialogfeld mit den verschiedenen Facebook-Genehmigungseinstellungen wird angezeigt. Diese ermöglichen es Adobe Campaign, Publikationen an die Facebook-Kontoseiten zu senden.

   Akzeptieren Sie die verschiedenen Berechtigungsanforderungen.

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign wurde das Recht eingeräumt, Inhalte auf den Seiten des Facebook-Kontos zu publizieren.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Wenn das Facebook-Konto mehrere Seiten verwaltet, konfigurieren Sie einfach ein externes Konto, um auf einer beliebigen Seite des Facebook-Kontos zu schreiben. Für jedes neue Facebook-Konto müssen Sie ein neues externes **[!UICONTROL Routing]**-Konto erstellen.

Der Workflow für die **[!UICONTROL Facebook-Seiten-Synchronisation]** synchronisiert alle vom Facebook-Konto verwalteten Seiten, damit Sie direkt über Adobe Campaign auf der Pinnwand posten können. Weitere Informationen hierzu finden Sie unter [Facebook-Seiten-Synchronisation](#synchronizing-facebook-pages).

## Facebook-Seiten-Sychronisation {#synchronizing-facebook-pages}

Mit dem Workflow für die **[!UICONTROL Facebook-Seiten-Synchronisation]**, der über den Knoten **[!UICONTROL Administration > Produktion > Technische Workflows > Social Marketing]** aufgerufen wird, können Sie die Seiten des zuvor konfigurierten Facebook-Kontos (in Adobe Campaign) synchronisieren. Standardmäßig ist dieser Workflow so konfiguriert, dass er einmal am Tag oder immer dann ausgeführt wird, wenn ein Administrator auf den Link **[!UICONTROL Zulassung von der Anwendung einholen]** im Bildschirm zur Dienstkonfiguration klickt (siehe [Schreibzugriff an Adobe Campaign delegieren](#delegating-write-access-to-adobe-campaign)).

Nach Abschluss der Synchronisation werden die erfassten Seiten im Dienstordner angezeigt, der in das externe Konto eingegeben wurde (siehe [Schreibzugriff an Adobe Campaign delegieren](#delegating-write-access-to-adobe-campaign)). Standardmäßig werden die Seiten dem Stammordner des **[!UICONTROL Facebook]**-Dienstordners hinzugefügt, der über das Menü **[!UICONTROL Profile und Zielgruppen > Dienste und Abonnements]** verfügbar ist.

![](assets/social_facebook_service_002.png)

Sie können jetzt direkt über Adobe Campaign auf den Pinnwänden Ihrer Facebook-Seiten publizieren. Weitere Informationen hierzu finden Sie unter [Auf Facebook publizieren](#publishing-on-facebook-walls).
