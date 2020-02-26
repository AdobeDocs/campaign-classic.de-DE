---
title: Veröffentlichen auf Facebook-Wänden
seo-title: Veröffentlichen auf Facebook-Wänden
description: Veröffentlichen auf Facebook-Wänden
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
source-git-commit: 8ef56aa04a3ecc94e9e3dda24562760d6a93739d

---


# Veröffentlichen auf Facebook-Wänden{#publishing-on-facebook-walls}

Damit Adobe Campaign Veröffentlichungen an Facebook-Wände senden kann, müssen Sie den Schreibzugriff für diese Seiten an Adobe Campaign delegieren. Dies umfasst die folgenden Konfigurationsschritte:

1. Erstellen Sie ein Facebook-Konto mit einer oder mehreren Seiten.
1. Erstellen Sie eine Facebook-Testseite zum Senden von Proofs.
1. Erstellen Sie eine Facebook-Anwendung.
1. Geben Sie die Facebook-Anwendungseinstellungen in Adobe Campaign im **[!UICONTROL Facebook routing]** externen Konto ein.

## Voraussetzungen {#prerequisites}

Erstellen Sie zunächst ein Facebook-Konto und mehrere Seiten: Diese werden zum Versenden von Veröffentlichungen verwendet.

* Um ein Facebook-Konto zu erstellen, verwenden Sie den Link [https://www.facebook.com](https://www.facebook.com) .
* Um eine Facebook-Seite zu erstellen, verwenden Sie den Link [https://www.facebook.com/pages/create.php](https://www.facebook.com/pages/create.php) .

   Es wird empfohlen, alle Seiten mit demselben Facebook-Konto zu verwalten. Auf diese Weise benötigen Sie nur eine Facebook-Anwendung und ein externes Konto, um auf allen Seiten des Kontos zu schreiben.

   ![](assets/social_diagram_fb_external_account.png)

## Erstellen einer Facebook-Testseite {#creating-a-test-facebook-page}

Es wird empfohlen, eine private Facebook-Seite für die Bereitstellung von Proofs für Veröffentlichungen zu erstellen (weitere Informationen hierzu finden Sie unter [Senden des Beweises](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. Melden Sie sich bei dem Facebook-Konto an, mit dem Sie Ihre Seiten verwalten.
1. Erstellen Sie eine neue Facebook-Seite.
1. Klicken Sie auf die **[!UICONTROL Settings]** Schaltfläche oben rechts.
1. Ändern Sie auf der **[!UICONTROL General]** Registerkarte die Sichtbarkeitsparameter der Seite: aktivieren Sie das **[!UICONTROL Page unpublished]** Kästchen.
1. Click the **[!UICONTROL Save Changes]** button.

![](assets/social_facebook_test_page.png)

## Erstellen einer Facebook-Anwendung {#creating-a-facebook-application}

Damit Adobe Campaign auf den Wänden Ihrer Seiten veröffentlichen kann, müssen Sie eine Facebook-Anwendung erstellen. Gehen Sie hierzu wie folgt vor:

1. Melden Sie sich bei dem Facebook-Konto an, mit dem Sie Seiten verwalten.
1. Geben Sie folgende Adresse in Ihren Browser ein: [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!IMPORTANT]
   >
   >Je nach dem von Ihnen verwendeten Kontotyp können eine oder mehrere Autorisierungen erforderlich sein.
   >
   >Zum Erstellen einer Facebook-Anwendung benötigen Sie ein **bestätigtes** Facebook-Konto.

1. Klicken Sie auf die **[!UICONTROL Add a New App]** Schaltfläche oben rechts auf der Seite. Geben Sie einen App-Namen und eine Kontakt-E-Mail ein und übergeben Sie dann die Sicherheitsprüfung.

   ![](assets/social_create_facebook_app_002.png)

1. Klicken Sie **[!UICONTROL Settings > Basic]** unter auf **[!UICONTROL Add a platform]** und wählen Sie den **[!UICONTROL Facebook Web Games]** Typ aus.

   ![](assets/social_create_facebook_app_003.png)

1. Überprüfen Sie im **[!UICONTROL Products]** Abschnitt im Menü links, ob das **[!UICONTROL Facebook Login]** Produkt angezeigt wird. Wenn nicht, fügen Sie ein neues Produkt hinzu und wählen Sie **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. Nachdem die Anwendung erstellt wurde, wählen Sie die **[!UICONTROL App Review]** Registerkarte und veröffentlichen Sie die Anwendung.

   ![](assets/social_create_facebook_app_004.png)

## Delegieren von Schreibzugriff auf Adobe Campaign {#delegating-write-access-to-adobe-campaign}

Um den Schreibzugriff auf Adobe Campaign zum Posten auf den Wänden Ihrer Seiten zu delegieren, müssen Sie die Parameter der zuvor erstellten Facebook-Anwendung eingeben.

Dieser Schritt erfordert Zugriff auf Ihre Adobe Campaign-Konsole und einen Internetbrowser, der beim Facebook-Konto angemeldet ist, das Sie für die Seitenverwaltung verwenden:

>[!IMPORTANT]
>
>Der Adobe Campaign-Operator muss über Administratorrechte verfügen, um diese Konfiguration durchführen zu können.

* **Facebook**: Wählen Sie die zuvor erstellte Anwendung ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) und dann die **[!UICONTROL Settings > Basic]** Registerkarte aus.

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >Wenn der **[!UICONTROL Facebook Web Games]** Abschnitt nicht angezeigt wird, klicken Sie auf die **[!UICONTROL Add Platform]** Schaltfläche am unteren Rand der Seite und wählen Sie **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: gehen Sie zum **[!UICONTROL Administration > Platform > External Accounts]** Knoten der Struktur, wählen Sie das **[!UICONTROL Facebook routing]** externe Konto und klicken Sie auf die **[!UICONTROL Connector]** Registerkarte.

   ![](assets/social_facebook_external_account_001.png)

1. Kopieren Sie in der Adobe Campaign-Konsole die im **[!UICONTROL Secure Canvas URL]** Feld enthaltene Adresse und fügen Sie sie in das **[!UICONTROL Secure Web Games URL (https)]** Feld auf Facebook ein (im **[!UICONTROL Facebook Web Games]** Abschnitt).

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >Sie dürfen die unsichere URL unter keinen Umständen verwenden.

   Kopieren Sie diese URL und fügen Sie sie auch unter **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. Um die Gültigkeit der URL zu überprüfen, speichern Sie die Anwendung, kopieren Sie die URL in das **[!UICONTROL Redirect URI to Check]** Feld und klicken Sie auf **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. Kopieren Sie auf Facebook den Inhalt der **[!UICONTROL App ID]** und der **[!UICONTROL App Secret]** Felder und fügen Sie ihn in die entsprechenden Felder der Konsole ein.

   ![](assets/social_facebook_external_account_007.png)

1. Klicken Sie auf Facebook auf die **[!UICONTROL Save Changes]** Schaltfläche am unteren Rand der Seite.
1. Wechseln Sie zur Adobe Campaign-Konsole und speichern Sie das externe Konto.

   >[!NOTE]
   >
   >Das **[!UICONTROL Marketing URL]** Feld ist optional.

1. Klicken Sie in der Adobe Campaign-Konsole auf den **[!UICONTROL Request the authorization from the application]** Link unten auf der **[!UICONTROL Connector]** Registerkarte. Der **[!UICONTROL Synchronize Facebook pages]** Workflow wird automatisch ausgelöst und erfasst alle vom Administrator verwalteten Facebook-Seiten. Weitere Informationen finden Sie unter [Synchronisieren von Facebook-Seiten](#synchronizing-facebook-pages).

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >Standardmäßig werden die Seiten dem **[!UICONTROL Facebook]** Dienstordner hinzugefügt, der über den **[!UICONTROL Profiles and Targets > Services and Subscriptions]** Knoten verfügbar ist. Im **[!UICONTROL Folder]** Feld der **[!UICONTROL Connector]** Registerkarte können Sie den Dienstordner ändern, in dem die Facebook-Seiten nach der Synchronisierung erstellt werden. Sie können auch die Facebook-Seiten auswählen, die Sie dank des **[!UICONTROL Filter]** Felds in Adobe Campaign synchronisieren möchten. Wenn Sie dieses Feld leer lassen, werden alle vom Administrator verwalteten Facebook-Seiten synchronisiert.

1. Ein Dialogfeld mit den verschiedenen Facebook-Berechtigungseinstellungen wird angezeigt. Diese ermöglichen es Adobe Campaign, Veröffentlichungen an die Facebook-Kontoseiten zu senden.

   Akzeptieren Sie die verschiedenen Berechtigungsanforderungen.

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign wurde das Recht eingeräumt, Inhalte auf den Seiten des Facebook-Kontos zu veröffentlichen.

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>Wenn das Facebook-Konto mehrere Seiten verwaltet, konfigurieren Sie einfach ein externes Konto, um es auf einer beliebigen Seite des Facebook-Kontos zu schreiben. Für jedes neue Facebook-Konto müssen Sie einen neuen **[!UICONTROL Routing]** Typ eines externen Kontos erstellen.

Der **[!UICONTROL Synchronization of Facebook pages]** Arbeitsablauf synchronisiert alle Seiten, die vom Facebook-Konto verwaltet werden, damit Sie direkt über Adobe Campaign auf der Pinnwand posten können. Weitere Informationen finden Sie unter [Synchronisieren von Facebook-Seiten](#synchronizing-facebook-pages).

## Facebook-Seiten-Sychronisation {#synchronizing-facebook-pages}

Mit dem **[!UICONTROL Synchronization of Facebook pages]** Workflow, auf den über den **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** Knoten zugegriffen wird, können Sie (in Adobe Campaign) die Seiten des zuvor konfigurierten Facebook-Kontos synchronisieren. Standardmäßig ist dieser Workflow so konfiguriert, dass er einmal am Tag oder immer dann ausgeführt wird, wenn ein Administrator auf den **[!UICONTROL Request an authorization from the application]** Link im Bildschirm &quot;Dienstkonfiguration&quot;klickt (siehe [Delegieren des Schreibzugriffs auf Adobe Campaign](#delegating-write-access-to-adobe-campaign)).

Nach Abschluss der Synchronisierung werden die erfassten Seiten im Dienstordner angezeigt, der in das externe Konto eingegeben wurde (siehe [Delegieren des Schreibzugriffs auf Adobe Campaign](#delegating-write-access-to-adobe-campaign)). Standardmäßig werden Seiten zum Stammordner des **[!UICONTROL Facebook]** Dienstordners hinzugefügt, der über das **[!UICONTROL Profiles and Targets > Services and subscriptions]** Menü verfügbar ist.

![](assets/social_facebook_service_002.png)

Sie können jetzt direkt über Adobe Campaign auf den Wänden Ihrer Facebook-Seiten veröffentlichen. Weitere Informationen finden Sie unter [Veröffentlichen auf Facebook](#publishing-on-facebook-walls).
