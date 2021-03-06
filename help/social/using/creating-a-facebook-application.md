---
product: campaign
title: Erstellen einer Facebook-Anwendung
description: Erstellen einer Facebook-Anwendung
audience: social
content-type: reference
topic-tags: configuration
exl-id: 5c11bd0f-2df7-4c7f-b682-955fedf8e664
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: ht
source-wordcount: '994'
ht-degree: 100%

---

# Erstellen einer Facebook-Anwendung{#creating-a-facebook-application}

![](../../assets/v7-only.svg)

Mit dem Social-Media-Marketing-Modul von Campaign können Sie über Web-Anwendungen personalisierte Inhalte in Ihren Facebook-Anwendungen anzeigen. Dadurch wird es einfacher, über dieses soziale Netzwerk potenzielle Kunden zu gewinnen. Weitere Beispiele von Web-Anwendungen für Facebook finden Sie auf [dieser Seite](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>Es ist auch möglich, Adobe Campaign in eine von einem Partner entwickelte Facebook-Anwendung zu integrieren. In diesem Fall ist es nicht nötig, die Web-Anwendung von Adobe Campaign zu verwenden, um Facebook-Profile zu erhalten. [Weitere Informationen](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Die Konfigurationsschritte sind:

1. Erstellen Sie eine oder mehrere Facebook-Anwendungen.
1. Geben Sie die Links für die **[!UICONTROL Nutzungsbedingungen]** und **[!UICONTROL Datenschutzbestimmungen]** ein, die auf dem Facebook-Bildschirm für Berechtigungsanfragen angezeigt werden sollen. [Weitere Informationen](#entering-the-terms-of-service-and-privacy-policy-links)
1. Erstellen Sie für jede Facebook-Anwendung ein externes **[!UICONTROL Facebook Connect]**-Konto. [Weitere Informationen](#configuring-external-accounts)
1. Erstellen Sie für jede Facebook-Anwendung in Adobe Campaign eine Web-Anwendung vom Typ &quot;Facebook&quot;. [Weitere Informationen](#creating-a-facebook-type-web-application)
1. Konfigurieren Sie Ihre Facebook-Anwendungen so, dass sie als Tabs auf Ihrer Facebook-Seite angezeigt werden. [Weitere Informationen](#configuring-facebook-tabs)

## Konfigurieren externer Konten {#configuring-external-accounts}

Für jede Facebook-Anwendung müssen Sie ein externes **[!UICONTROL Facebook Connect]**-Konto erstellen.

Dieser Schritt erfordert Zugriff auf Ihre Adobe Campaign-Konsole und Ihr Facebook-Administratorkonto:

* In **Facebook**: Wählen Sie die zuvor erstellte Anwendung ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) aus und klicken Sie auf die Registerkarte **[!UICONTROL Einstellungen]** > **[!UICONTROL Einfach]**.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Wenn der Abschnitt **[!UICONTROL Facebook-Web-Spiele]** nicht angezeigt wird, klicken Sie auf die Schaltfläche **[!UICONTROL Plattform hinzufügen]** unten auf der Seite und wählen Sie **[!UICONTROL Facebook-Web-Spiele]** aus.

* In **Adobe Campaign**: Navigieren Sie zu **[!UICONTROL Administration > Plattform > Externe Konten]** und klicken Sie auf **[!UICONTROL Neu]**.

   ![](assets/social_webapp_fb_005.png)

1. Geben Sie einen Titel und einen internen Namen ein und wählen Sie den Typ **[!UICONTROL Facebook Connect]** aus.

   ![](assets/social_webapp_fb_006.png)

1. Wählen Sie den Hosting-Modus der Anwendung aus: **[!UICONTROL von einem Partner gehostet]** oder **[!UICONTROL von dieser Instanz gehostet]**.

   ![](assets/social_webapp_fb_012.png)

   **Bei einem Partner gehostete Anwendung**

   Es ist möglich, Adobe Campaign in eine von einem Partner entwickelte Facebook-Anwendung zu integrieren. In diesem Fall müssen Sie die Adobe Campaign-Webanwendungen nicht verwenden, um Facebook-Profile zu gewinnen. Wenn der Facebook-Benutzer die Anwendung installiert, wird ein Schlüssel (Zugriffstoken) generiert. Der Partner leitet dieses Zugriffstoken an Adobe Campaign weiter, indem er einen Web-Dienst aufruft. Adobe Campaign verwendet dieses Token dann, um sich bei der Facebook-Datenbank anzumelden und die vom Benutzer über die Anwendung freigegebenen Daten zu erfassen.

   >[!NOTE]
   >
   >Die Parameter des Web-Diensts sind in der WSDL-Datei im Folgenden aufgeführt: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Um die Drittanbieteranwendung in Adobe Campaign zu integrieren, müssen Sie den Inhalt der Facebook-Felder **[!UICONTROL App-ID]** und **[!UICONTROL App-Geheimnis]** kopieren und in die Felder **[!UICONTROL Anwendungs-ID]** und **[!UICONTROL Anwendungsgeheimnis]** der Konsole einfügen.

   ![](assets/social_facebook_external_account_013.png)

   **Auf dieser Instanz gehostete Anwendung**

   Wenn Sie die Anwendung auf dieser Instanz hosten möchten (wenn Sie keine Drittanbieter-Anwendung haben), müssen Sie die Adobe Campaign-Webanwendungen verwenden, um Facebook-Profile zu gewinnen. Weitere Informationen hierzu finden Sie auf [dieser Seite](../../social/using/examples-of-facebook-apps.md).

   Kopieren Sie in der Adobe Campaign-Konsole die im Feld **[!UICONTROL Sichere Canvas-URL]** enthaltene Adresse und fügen Sie sie in das Feld **[!UICONTROL Facebook-Web-Spiele (https)]** in Facebook (im Abschnitt **[!UICONTROL Facebook-Web-Spiele]**) ein.

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >Verwenden Sie keine unsicheren URLs.

   Kopieren Sie auf Facebook den Inhalt der Felder **[!UICONTROL App-ID]** und **[!UICONTROL App-Geheimnisr]** und fügen Sie ihn in die Felder **[!UICONTROL Anwendungs-ID]** und **[!UICONTROL Anwendungsgeheimnis]** in der Konsole ein.

   ![](assets/social_facebook_external_account_008.png)

1. Klicken Sie auf Facebook unten auf der Seite auf die Schaltfläche **[!UICONTROL Änderungen speichern]**.
1. Klicken Sie in der Adobe Campaign-Konsole auf die Schaltfläche **[!UICONTROL Abonnieren]**, damit Adobe Campaign die Daten jedes Mal in Echtzeit abrufen kann, wenn ein Fan über diese Anwendung eincheckt. [Weitere Informationen](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_fb_013.png)

## Eingeben der Links für Nutzungsbedingungen und Datenschutzbestimmungen {#entering-the-terms-of-service-and-privacy-policy-links}

Es wird empfohlen, die Links für die **[!UICONTROL Nutzungsbedingungen]** und **[!UICONTROL Datenschutzbestimmungen]** hinzuzufügen, die auf dem Facebook-Bildschirm für Berechtigungsanfragen angezeigt werden sollen.

![](assets/social_fb_terms_of_services_001.png)

Die Konfiguration stellt sich wie folgt dar:

1. Geben Sie folgende Adresse ein: [https://developers.facebook.com/apps](https://developers.facebook.com/apps) und wählen Sie dann die Facebook-Anwendung aus.
1. Wählen Sie den Tab **[!UICONTROL Einstellungen > Einfach]** aus und geben Sie die **[!UICONTROL Datenschutzbestimmungen-URL]** und die **[!UICONTROL Nutzungsbedingungen-URL]** ein.

   ![](assets/social_fb_terms_of_services.png)

## Erstellen einer Web-Anwendung für Facebook. {#creating-a-facebook-type-web-application}

Mit der Facebook-Anwendung von Adobe Campaign können Sie personalisierte Inhalte in Ihrer Facebook-Anwendung anzeigen. Für jede Facebook-Anwendung müssen Sie eine Webanwendung in Adobe Campaign erstellen. Erstellen einer Facebook-Webanwendung:

1. Wechseln Sie zum Tab **[!UICONTROL Soziale Netzwerke]**, klicken Sie auf den Link **[!UICONTROL Anwendungen]** und dann auf die Schaltfläche **[!UICONTROL Erstellen]**.

   ![](assets/social_webapp_001.png)

1. Wählen Sie eine Facebook-Webanwendungsvorlage aus der Liste aus und geben Sie den Titel ein.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Standardmäßig stehen vier Facebook-Webanwendungsvorlagen zur Verfügung:
   >
   >* **[!UICONTROL Neue Facebook-Anwendung]**: Wählen Sie diese Vorlage, wenn Sie mit einer leeren Anwendung beginnen möchten.
   >* **[!UICONTROL Vorausgefülltes Formular]**: Facebook-Anwendung mit einem Formular und einer Schaltfläche „Facebook-Anmeldung“, mit der Benutzer die Felder des Formulars automatisch mit den Daten aus ihrem Profil ausfüllen können. Auf diese Weise können die Benutzer das Formular schneller ausfüllen und Marken bessere Informationen erhalten.
   >* **[!UICONTROL Preisausschreiben „Canvas-Seite“]**: Facebook-Anwendung, die auf dem gesamten Bildschirm angezeigt wird, um eine bessere visuelle Darstellung für die Benutzer zu gewährleisten.
   >* **[!UICONTROL Preisausschreiben „Tab-Seite“]**: Facebook-Anwendung vollständig in den Tabs der Markenseite integriert.


1. Geben Sie im Feld **[!UICONTROL Anwendung]** das externe Konto ein, das mit der Facebook-Anwendung verknüpft ist. [Weitere Informationen](#configuring-external-accounts)

   ![](assets/social_webapp_005.png)

1. Wählen Sie den Tab **[!UICONTROL Bearbeiten]** aus und bearbeiten Sie dann die Web-Anwendung. [Weitere Informationen](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_003.png)

1. Nachdem die Web-Anwendung fertig ist, wählen Sie den Tab **[!UICONTROL Dashboard]** aus und klicken Sie dann auf **[!UICONTROL Veröffentlichen]**, um sie online zu veröffentlichen.

   ![](assets/social_webapp_004.png)

## Facebook-Registerkarten konfigurieren {#configuring-facebook-tabs}

Sie können Ihre Facebook-Anwendungen so konfigurieren, dass sie als Tabs auf Ihrer Facebook-Seite angezeigt werden. Gehen Sie hierzu wie folgt vor:

1. Wählen Sie die Facebook-Anwendung ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) aus und klicken Sie auf den Tab **[!UICONTROL Einstellungen > Einfach]**.

   ![](assets/social_webapp_fb_008.png)

1. Klicken Sie unten auf der Seite auf die Schaltfläche **[!UICONTROL Plattform hinzufügen]** und wählen Sie **[!UICONTROL Seite-Tab]** aus.

   ![](assets/social_webapp_fb_008bis.png)

1. Geben Sie im Feld **[!UICONTROL Name des Seite-Tabs]** des **[!UICONTROL Seite-Tabs]** den Titel so ein, wie er auf der Facebook-Seite angezeigt werden soll.

   ![](assets/social_webapp_fb_001.png)

1. Geben Sie im Feld **[!UICONTROL Sichere Seiten-Tab-URL]** die öffentliche URL der Webanwendung ein, auf die über den Tab **[!UICONTROL Dashboard]** der Webanwendung zugegriffen werden kann. Weiterführende Informationen zur Erstellung von Web-Anwendungen für Facebook finden Sie in [diesem Abschnitt](#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_fb_002.png)

1. Klicken Sie im **[!UICONTROL Dashboard]** der Webanwendung auf den Link **[!UICONTROL Seitentab hinzufügen]**.

   ![](assets/social_webapp_fb_0010.png)

1. Wählen Sie die Facebook-Seite aus, der Sie den Tab hinzufügen möchten, und klicken Sie auf **[!UICONTROL Seitentab hinzufügen]**.

   ![](assets/social_webapp_fb_0011.png)
