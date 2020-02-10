---
title: Erstellen einer Facebook-Anwendung
seo-title: Erstellen einer Facebook-Anwendung
description: Erstellen einer Facebook-Anwendung
seo-description: null
page-status-flag: never-activated
uuid: f02129b9-6f64-41ee-8b56-d85211a58f69
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: c1d880bb-256e-451c-8c52-198711907f8e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Erstellen einer Facebook-Anwendung{#creating-a-facebook-application}

Dank Webanwendungen können Sie mit Social Marketing personalisierte Inhalte in Ihren Facebook-Anwendungen anzeigen, um potenzielle Kunden über dieses soziale Netzwerk besser zu gewinnen. Weitere Beispiele für Webanwendungen vom Typ Facebook finden Sie unter [Beispiele für Facebook-Apps](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>Es ist auch möglich, Adobe Campaign in eine von einem Partner entwickelte Facebook-Anwendung zu integrieren. In diesem Fall müssen Sie die Adobe Campaign-Webanwendung nicht verwenden, um Facebook-Profile zu erwerben. For more on this, refer to [Configuring external accounts](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Befolgen Sie zur Konfiguration die nachstehenden Etappen:

1. Erstellen Sie eine oder mehrere Facebook-Anwendungen. Weitere Informationen finden Sie unter: Erstellen [einer Facebook-Anwendung](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).
1. Geben Sie die Links **[!UICONTROL terms of service]** und **[!UICONTROL Privacy policy]** Links ein, die im Bildschirm &quot;Facebook-Berechtigungsanforderung&quot;angezeigt werden sollen. Weitere Informationen finden Sie unter: [Eingeben der Links](#entering-the-terms-of-service-and-privacy-policy-links)zu den Servicebedingungen und den Datenschutzrichtlinien.
1. Erstellen Sie für jede Facebook-Anwendung einen **[!UICONTROL Facebook Connect]** Typ eines externen Kontos. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).
1. Erstellen Sie für jede Facebook-Anwendung in Adobe Campaign eine Webanwendung vom Typ Facebook. Weitere Informationen finden Sie unter: [Erstellen einer Webanwendung](#creating-a-facebook-type-web-application)vom Typ &quot;Facebook&quot;.
1. Konfigurieren Sie Ihre Facebook-Anwendungen so, dass sie als Registerkarten auf Ihrer Facebook-Seite angezeigt werden. For more on this, refer to: [Configuring Facebook tabs](#configuring-facebook-tabs).

## Konfigurieren von externen Konten {#configuring-external-accounts}

Für jede Facebook-Anwendung müssen Sie ein externes **[!UICONTROL Facebook Connect]** Konto erstellen.

Dieser Schritt erfordert Zugriff auf Ihre Adobe Campaign-Konsole und einen Internetbrowser, der beim Facebook-Konto angemeldet ist, das Sie für die Seitenverwaltung verwenden:

* **Facebook**: Wählen Sie die zuvor erstellte Anwendung ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) und klicken Sie auf die Registerkarte **[!UICONTROL Settings]** > **[!UICONTROL Basic]** .

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Wenn der **[!UICONTROL Facebook Web Games]** Abschnitt nicht angezeigt wird, klicken Sie auf die **[!UICONTROL Add Platform]** Schaltfläche am unteren Rand der Seite und wählen Sie **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**: gehen Sie zum **[!UICONTROL Administration > Platform > External accounts]** Knoten der Struktur und klicken Sie auf **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Geben Sie eine Beschriftung und einen internen Namen ein und wählen Sie den **[!UICONTROL Facebook Connect]** Typ.

   ![](assets/social_webapp_fb_006.png)

1. Wählen Sie einen Hosting-Modus für die Anwendung aus: **[!UICONTROL hosted by a partner]** oder **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Von einem Partner gehostete Anwendungen**

   Adobe Campaign kann in eine von einem Partner entwickelte Facebook-Anwendung integriert werden. In diesem Fall müssen die Adobe Campaign-Webanwendungen nicht zum Erwerb von Facebook-Profilen verwendet werden. Wenn der Facebook-Benutzer die Anwendung installiert, wird ein Schlüssel (Zugriffstoken) generiert. Der Partner leitet dieses Zugriffstoken an Adobe Campaign weiter, indem er einen Webdienst aufruft. Adobe Campaign verwendet dieses Token dann, um sich bei der Facebook-Datenbank anzumelden und die vom Benutzer über die Anwendung freigegebenen Daten zu erfassen.

   >[!NOTE]
   >
   >Die Parameter des Webdiensts sind in der WSDL-Datei im Folgenden aufgeführt: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Um die Drittanbieteranwendung in Adobe Campaign zu integrieren, müssen Sie den Inhalt der Felder **[!UICONTROL App ID]** und **[!UICONTROL App Secret]** Facebook kopieren und in die Felder **[!UICONTROL Application ID]** und **[!UICONTROL Application secret]** Felder der Konsole einfügen.

   ![](assets/social_facebook_external_account_013.png)

   **Von dieser Instanz gehostete Anwendung**

   Wenn Sie die Anwendung auf dieser Instanz hosten möchten (wenn Sie keine Anwendung eines Drittanbieters haben), müssen Sie die Adobe Campaign-Webanwendungen verwenden, um Facebook-Profile zu erwerben. Weitere Informationen finden Sie unter [Beispiele für Facebook-Apps](../../social/using/examples-of-facebook-apps.md).

   Kopieren Sie in der Adobe Campaign-Konsole die im **[!UICONTROL Secure Canvas URL]** Feld enthaltene Adresse und fügen Sie sie in das **[!UICONTROL Facebook Web games (https)]** Feld auf Facebook ein (im **[!UICONTROL Facebook Web Games]** Abschnitt).

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >Sie dürfen die unsichere URL unter keinen Umständen verwenden.

   Kopieren Sie auf Facebook den Inhalt der **[!UICONTROL App ID]** und **[!UICONTROL App Secret]** Felder und fügen Sie ihn in die Felder **[!UICONTROL Application ID]** **[!UICONTROL Application secret]** und in die Konsole ein.

   ![](assets/social_facebook_external_account_008.png)

1. Klicken Sie auf Facebook auf die **[!UICONTROL Save Changes]** Schaltfläche am unteren Rand der Seite.
1. Klicken Sie in der Adobe Campaign-Konsole auf die **[!UICONTROL Subscribe]** Schaltfläche, damit Adobe Campaign die Daten jedes Mal in Echtzeit wiederherstellen kann, wenn ein Fan über diese Anwendung eincheckt. Weitere Informationen finden Sie unter: Beispiele [für Facebook-Apps](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_fb_013.png)

## Eingeben der Links zu den Servicebedingungen und den Datenschutzrichtlinien {#entering-the-terms-of-service-and-privacy-policy-links}

Es wird dringend empfohlen, die Links **[!UICONTROL Terms of service]** und **[!UICONTROL Privacy policy]** Links hinzuzufügen, die im Bildschirm &quot;Facebook-Berechtigungsanforderung&quot;angezeigt werden sollen.

![](assets/social_fb_terms_of_services_001.png)

Die Konfigurationsschritte lauten wie folgt:

1. Geben Sie folgende Adresse ein: [https://developers.facebook.com/apps](https://developers.facebook.com/apps)und wählen Sie dann die Facebook-Anwendung aus.
1. Wählen Sie die **[!UICONTROL Settings > Basic]** Registerkarte aus und geben Sie die Felder **[!UICONTROL Privacy Policy URL]** und **[!UICONTROL Terms of Service URL]** ein.

   ![](assets/social_fb_terms_of_services.png)

## Erstellen einer Webanwendung mit Facebook-Typ {#creating-a-facebook-type-web-application}

Mit der Facebook-Anwendung von Adobe Campaign können Sie personalisierte Inhalte in Ihrer Facebook-Anwendung anzeigen. Für jede Facebook-Anwendung müssen Sie eine Webanwendung in Adobe Campaign erstellen. So erstellen Sie eine Facebook-Webanwendung:

1. Gehen Sie zum **[!UICONTROL Social networks]** Universum, klicken Sie auf den **[!UICONTROL Applications]** Link und dann auf die **[!UICONTROL Create]** Schaltfläche.

   ![](assets/social_webapp_001.png)

1. Wählen Sie eine Facebook-Webanwendungsvorlage aus der Liste und geben Sie die Bezeichnung ein.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Standardmäßig stehen vier Facebook-Webanwendungsvorlagen zur Verfügung:
   >
   >* **[!UICONTROL New Facebook application]**: Wählen Sie diese Vorlage, wenn Sie mit einer leeren Anwendung beginnen möchten.
   >* **[!UICONTROL Pre-entered form]**: Facebook-Anwendung mit einem Formular und einer Schaltfläche &quot;Facebook-Anmeldung&quot;, mit der Benutzer die Felder des Formulars automatisch mit den Daten aus ihrem Profil ausfüllen können. Auf diese Weise können die Benutzer das Formular schneller ausfüllen und für Marken bessere Informationen erhalten.
   >* **[!UICONTROL "Canvas page" competition]**: Facebook-Anwendung, die auf dem gesamten Bildschirm angezeigt wird, um eine bessere visuelle Darstellung für die Benutzer zu gewährleisten.
   >* **[!UICONTROL "Page Tab" competition]**: Facebook-Anwendung vollständig in die Registerkarten der Markenseite integriert.


1. Geben Sie in das **[!UICONTROL Application]** Feld das externe Konto ein, das mit der Facebook-Anwendung verknüpft ist. For more on this, refer to: [Configuring external accounts](#configuring-external-accounts).

   ![](assets/social_webapp_005.png)

1. Wählen Sie die **[!UICONTROL Edit]** Registerkarte und bearbeiten Sie dann die Webanwendung. Weitere Informationen finden Sie unter: Beispiele [für Facebook-Apps](../../social/using/examples-of-facebook-apps.md).

   ![](assets/social_webapp_003.png)

1. Nachdem die Webanwendung abgeschlossen ist, wählen Sie die **[!UICONTROL Dashboard]** Registerkarte und klicken Sie dann auf , um die Online-Veröffentlichung **[!UICONTROL Publish]** durchzuführen.

   ![](assets/social_webapp_004.png)

## Konfigurieren von Facebook-Registerkarten {#configuring-facebook-tabs}

Sie können Ihre Facebook-Anwendungen so konfigurieren, dass sie als Registerkarten auf Ihrer Facebook-Seite angezeigt werden. Gehen Sie hierzu wie folgt vor:

1. Wählen Sie die Facebook-Anwendung ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) und dann die **[!UICONTROL Settings > Basic]** Registerkarte aus.

   ![](assets/social_webapp_fb_008.png)

1. Klicken Sie am unteren Rand der Seite auf die **[!UICONTROL Add Platform]** Schaltfläche und wählen Sie **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. Geben Sie im **[!UICONTROL Page Tab Name]** Feld des **[!UICONTROL Page Tab]** Abschnitts die Bezeichnung ein, die auf der Facebook-Seite angezeigt werden soll.

   ![](assets/social_webapp_fb_001.png)

1. Geben Sie in das **[!UICONTROL Secure Page Tab URL]** Feld die öffentliche URL der Webanwendung ein, auf die über die Registerkarte der Webanwendung zugegriffen werden **[!UICONTROL Dashboard]** kann. Weitere Informationen zum Erstellen von Webanwendungen vom Typ Facebook finden Sie unter [Erstellen einer Webanwendung](#creating-a-facebook-type-web-application)vom Typ Facebook.

   ![](assets/social_webapp_fb_002.png)

1. Klicken Sie auf **[!UICONTROL Dashboard]** der Website auf den **[!UICONTROL Add a page tab]** Link.

   ![](assets/social_webapp_fb_0010.png)

1. Wählen Sie die Facebook-Seite aus, der Sie die Registerkarte hinzufügen möchten, und klicken Sie auf **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)

