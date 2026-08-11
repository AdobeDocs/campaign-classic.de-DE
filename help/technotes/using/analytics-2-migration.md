---
product: campaign
title: Migrieren zur Adobe Analytics 2.0-API
description: Campaign Classic - Migrationshandbuch zur Adobe Analytics 2.0-API
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 2%

---

# Migrieren zur Adobe Analytics 2.0-API {#analytics-2-migration}

Adobe Analytics 1.4-APIs [ das Ende der Lebensdauer ](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}. Der [Web Analytics-Connector](../../integrations/using/gs-aa.md) der Ihre Campaign-Instanz mit Adobe Analytics verbindet, beruht auf diesen APIs. Daher müssen Sie auf einen Build aktualisieren, der die neuen Analytics 2.0-APIs verwendet, um die Integration am Laufen zu halten.

>[!CAUTION]
>
>Beim Upgrade werden die beiden integrierten technischen Workflows, die den Connector unterstützen, [!UICONTROL webAnalyticsSendMetrics] und [!UICONTROL webAnalyticsGetWebEvents], erneut importiert (siehe [Web Analytics Workflows-](../../workflow/using/web-analytics.md)). Alle Anpassungen, die Sie zusätzlich zu diesen Workflows vorgenommen haben, werden durch den erneuten Import überschrieben. Vermeiden Sie die direkte Änderung dieser integrierten Workflows . Erstellen Sie stattdessen Ihre Anpassung in einem separaten benutzerdefinierten Workflow, damit sie bei zukünftigen Upgrades nicht überschrieben wird. Durch das Upgrade werden auch die integrierten Analytics JavaScript-Dateien aktualisiert: Wenn einer Ihrer benutzerdefinierten Workflows auf diese Dateien verweist, sind sie beschädigt und müssen an den neuen Code angepasst werden.

## Sind Sie betroffen? {#are-you-impacted}

Sie sind betroffen, wenn Ihre Instanz das externe [!UICONTROL Web Analytics]-Konto für einen der folgenden Vorgänge verwendet:

* Senden von Indikatoren und Attributen für E-Mail-Kampagnen als Metriken an Adobe Analytics.
* Senden von Klassifizierungsdaten an Adobe Analytics.
* Der Remarketing-Fluss (Identifizieren konvertierter Kontakte nach einer Kampagne).
* Ein [!UICONTROL Web Analytics] externes Konto, das Sie zum ersten Mal konfigurieren möchten.

Nicht sicher, welche davon auf Sie zutreffen? Überprüfen Sie, welche der oben genannten technischen Workflows in Ihrer Instanz aktiv sind, und überprüfen Sie Ihre Konfiguration [!UICONTROL Web Analytics] externen Kontos in [!UICONTROL Administration > Plattform > Externe ]&#x200B;(siehe [Externes Web Analytics-Konto](../../installation/using/external-accounts.md#web-analytics-external-account)).

## So migrieren Sie {#how-to-migrate}

Wenn Sie sich in einer **Adobe gehosteten** Instanz befinden, übernimmt Adobe die SFTP-Bereitstellung, die IP-Zulassungsauflistung und die Schlüsselkonfiguration für Sie als Teil des Upgrades. Sie müssen Ihre Anwendungsfälle nur validieren, sobald der neue Build live ist.

Wenn Sie sich in einer **On-Premise- oder Hybrid**-Bereitstellung befinden, führen Sie die folgenden Schritte aus.

1. [Campaign-Umgebung aktualisieren](../../production/using/build-upgrade.md) auf einen Build, der die Änderungen in Adobe Analytics 2.0 enthält. Sie können überprüfen, welchen Build Sie über ausführen [!UICONTROL Hilfe > Über…] (siehe [So überprüfen Sie Ihre Campaign-Version](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)).
1. Überprüfen Sie, welche der oben genannten Anwendungsfälle auf Ihre Instanz zutreffen, da der nächste Schritt davon abhängt.
1. Wenn Sie den Remarketing-Fluss verwenden, [!UICONTROL  der Workflow „webAnalyticsFindConverted] einen dedizierten SFTP-Kanal für den Datenaustausch mit Adobe Analytics 2.0. Richten Sie dies wie folgt ein, andernfalls fahren Sie mit dem nächsten Schritt fort.
   1. Stellen Sie mithilfe der schlüsselbasierten Authentifizierung einen SFTP-Server für die Instanz bereit [ befolgen Sie dabei die gleichen Best Practices für ](../../platform/using/sftp-server-usage.md) SFTP-Server, die Sie auch für jede andere externe SFTP-Integration anwenden würden. Adobe bietet ein [SFTP-Beispielsetup-](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"}), das Ihnen bei den ersten Schritten hilft.
   1. Registrieren Sie die Verbindungsdetails dieses Servers in Adobe Analytics, indem Sie das mit dem neuen Build bereitgestellte Skript ausführen:

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      Beispiel:

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. Setzen Sie Adobe Analytics auf Ihrem SFTP-Server auf die Zulassungsliste, da Remarketing-Exporte immer nur aus einem festen Satz von Adobe-IP-Bereichen initiiert werden:
      * [Aktuelle IP-Adressen der Adobe Analytics-Datenerfassung nachschlagen](https://experienceleague.adobe.com/en/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} und zur Zulassungsliste Ihres SFTP-Servers hinzufügen. FTP-basierte Analytics-Exporte (einschließlich Daten-Feeds) stammen nur von IPv4-Adressen in den Regionen London, Oregon und Singapur.
      * [Rufen Sie den öffentlichen Adobe Analytics-](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"} ab und fügen Sie ihn zur `authorized_keys`-Datei auf Ihrem SFTP-Server hinzu, damit sich Analytics authentifizieren kann.
1. Aktivieren Sie das Feature Flag `FEATUREFLAG_USE_ANALYTICS_20_API` Ihrer Instanz, indem Sie die `longvalue` der Option erstellen oder festlegen, die in [!UICONTROL xtkOption] unter **[!UICONTROL Administration] > [!UICONTROL Platform] > [!UICONTROL Options]** in der Explorer-Struktur von Campaign `1` werden soll. Dieser Schritt ist erforderlich, unabhängig davon, welcher der oben genannte Anwendungsfälle auf Sie zutrifft.
1. Validieren Sie die Migration, indem Sie jeden Anwendungsfall ausführen, der für Ihre Instanz gilt (Senden Sie eine Testkampagne, überprüfen Sie, ob die Indikatoren in Analytics landen, und bestätigen Sie ggf. Remarketing-Daten), bevor Sie eine alte Konnektivität deaktivieren.

## Einrichten eines neuen externen Web-Analytics-Kontos {#setting-up-a-new-web-analytics-external-account}

Unabhängig davon, ob Ihre Instanz in Adobe gehostet oder On-Premise/Hybrid ist, gilt Folgendes.

Wenn Sie das externe [!UICONTROL Web Analytics]-Konto zum ersten Mal konfigurieren, anstatt ein vorhandenes zu migrieren, befolgen Sie die [Schritte zur Einrichtung externer Konten](../../installation/using/external-accounts.md#web-analytics-external-account) und das [Erste Schritte mit dem Connector](../../integrations/using/gs-aa.md).

Da Analytics 2.0 eine neue Klassifizierungsverarbeitung einführt, müssen Sie auch einen Klassifizierungssatz in Adobe Analytics erstellen, bevor Ihr externes Konto die Klassifizierungsdaten Ihrer Report Suite abrufen kann. Dies ist ein neuer Schritt: Erstellen Sie ihn nach der Konfiguration Ihrer Konversionsvariablen und Erfolgsereignisse sowie vor der Konfiguration des externen Kontos in Campaign.

So erstellen Sie einen Klassifizierungssatz:

1. Wählen Sie in der oberen [!DNL Adobe Analytics] Menüleiste die Option **[!UICONTROL Komponenten]** > **[!UICONTROL Klassifizierungssätze]** und klicken Sie dann auf **[!UICONTROL Neu]**.

   ![](assets/analytics-classification-set-menu.png)

1. Im Dialogfeld **[!UICONTROL Neuen Klassifizierungssatz hinzufügen]**:

   ![](assets/analytics-classification-set-dialog.png)

   * Geben Sie **[!UICONTROL Klassifizierungssatz einen]** Namen“ ein.
   * Legen Sie **[!UICONTROL Typ]** auf **[!UICONTROL Primär fest]**.
   * Wählen **[!UICONTROL in &quot;]**&quot; aus, wer über Erfolg oder Misserfolg der Klassifizierungssatzaufträge benachrichtigt werden soll, und geben Sie die entsprechenden E-Mail-Adressen an.
   * Wählen **[!UICONTROL in]** Ihre Report Suite und die Konversionsvariable aus, die Sie im vorherigen Schritt für den Namen der internen Kampagne erstellt haben.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

Dieser Klassifizierungssatz wird von Campaign automatisch erkannt, wenn Sie im nächsten Schritt Ihr externes Konto konfigurieren. Weitere Informationen zu Klassifizierungssätzen finden Sie in der [Dokumentation zu Adobe Analytics](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/create-set){target="_blank"}.

## Hilfe erforderlich? {#need-help}

Wenn während der Migration Probleme auftreten, wenden Sie sich an die [Adobe-](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.
