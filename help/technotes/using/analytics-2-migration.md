---
product: campaign
title: Migrieren zur Adobe Analytics 2.0-API
description: Campaign Classic – Handbuch für die Migration zur Adobe Analytics 2.0-API
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: ht
source-wordcount: '910'
ht-degree: 100%

---

# Migrieren zur Adobe Analytics 2.0-API {#analytics-2-migration}

Adobe Analytics 1.4-APIs [erreichen das Ende ihres Lebenszyklus](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}. Der [Web Analytics-Connector](../../integrations/using/gs-aa.md), der Ihre Campaign-Instanz mit Adobe Analytics verbindet, beruht auf diesen APIs. Daher müssen Sie auf einen Build aktualisieren, der die neuen Analytics 2.0-APIs verwendet, damit die Integration weiterhin funktioniert.

>[!CAUTION]
>
>Beim Upgrade werden die beiden integrierten technischen Workflows, die den Connector unterstützen, [!UICONTROL webAnalyticsSendMetrics] und [!UICONTROL webAnalyticsGetWebEvents], erneut importiert (unter [Web Analytics-Workflows-Referenz](../../workflow/using/web-analytics.md) erfahren Sie, was jeder Workflow bewirkt). Alle Anpassungen, die Sie zusätzlich zu diesen Workflows vorgenommen haben, werden durch den erneuten Import überschrieben. Ändern Sie diese integrierten Workflows nicht direkt. Nehmen Sie Ihre Anpassungen stattdessen in einem separaten benutzerdefinierten Workflow vor, damit sie bei zukünftigen Upgrades nicht überschrieben werden. Durch das Upgrade werden auch die integrierten Analytics-JavaScript-Dateien aktualisiert: Wenn einer Ihrer benutzerdefinierten Workflows auf diese Dateien verweist, funktioniert dieser nicht mehr und muss an den neuen Code angepasst werden.

## Sind Sie betroffen? {#are-you-impacted}

Sie sind betroffen, wenn Ihre Instanz das externe [!UICONTROL Web Analytics]-Konto für einen der folgenden Vorgänge verwendet:

* Senden von Indikatoren und Attributen für E-Mail-Kampagnen als Metriken an Adobe Analytics.
* Senden von Klassifizierungsdaten an Adobe Analytics.
* Den Remarketing-Fluss (Identifizieren konvertierter Kontakte nach einer Kampagne).
* Ein externes [!UICONTROL Web Analytics]-Konto, das Sie zum ersten Mal konfigurieren möchten.

Nicht sicher, was davon auf Sie zutrifft? Überprüfen Sie, welche der oben genannten technischen Workflows in Ihrer Instanz aktiv sind, und kontrollieren Sie die Konfiguration Ihres externen [!UICONTROL Web Analytics]-Kontos unter [!UICONTROL Administration > Plattform > Externe Konten] (siehe [Externes Web Analytics-Konto](../../installation/using/external-accounts.md#web-analytics-external-account)).

## Durchführen der Migration {#how-to-migrate}

Wenn Sie über eine **Adobe-gehostete** Instanz verfügen, übernimmt Adobe die SFTP-Bereitstellung, die IP-Zulassungsauflistung und die Schlüsselkonfiguration für Sie als Teil des Upgrades. Sie müssen lediglich Ihre Anwendungsfälle validieren, sobald der neue Build live ist.

Wenn Sie über eine **On-Premise- oder Hybrid-Bereitstellung** verfügen, führen Sie die folgenden Schritte aus.

1. [Führen Sie ein Upgrade der Campaign-Umgebung](../../production/using/build-upgrade.md) auf einen Build durch, der die Adobe Analytics 2.0-Änderungen enthält. Sie können unter [!UICONTROL Hilfe > Info…] überprüfen, welchen Build Sie ausführen (siehe [Überprüfen Ihrer Campaign-Version](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)).
1. Überprüfen Sie, welche der oben genannten Anwendungsfälle auf Ihre Instanz zutreffen, da der nächste Schritt davon abhängt.
1. Wenn Sie den Remarketing-Fluss verwenden, benötigt der Workflow [!UICONTROL webAnalyticsFindConverted] einen dedizierten SFTP-Kanal für den Datenaustausch mit Adobe Analytics 2.0. Richten Sie dies wie folgt ein; andernfalls fahren Sie mit dem nächsten Schritt fort.
   1. Stellen Sie mithilfe der schlüsselbasierten Authentifizierung einen SFTP-Server für die Instanz bereit und befolgen Sie dabei die gleichen [Best Practices für SFTP-Server](../../platform/using/sftp-server-usage.md), die Sie auch für jede andere externe SFTP-Integration anwenden würden. Adobe bietet ein [Beispielskript für die SFTP-Einrichtung](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"}, das Ihnen bei den ersten Schritten hilft.
   1. Registrieren Sie die Verbindungsdetails dieses Servers in Adobe Analytics, indem Sie das mit dem neuen Build bereitgestellte Skript ausführen:

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      Beispiel:

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. Setzen Sie Adobe Analytics auf Ihrem SFTP-Server auf die Zulassungsliste, da Remarketing-Exporte immer nur aus einem festen Satz von Adobe-IP-Bereichen initiiert werden:
      * [Schlagen Sie aktuelle IP-Adressen für die Adobe Analytics-Datenerfassung nach](https://experienceleague.adobe.com/de/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} und fügen Sie sie der Zulassungsliste Ihres SFTP-Servers hinzu. FTP-basierte Analytics-Exporte (einschließlich Daten-Feeds) stammen nur von IPv4-Adressen in den Regionen London, Oregon und Singapur.
      * [Rufen Sie den öffentlichen Adobe Analytics-Schlüssel](https://experienceleague.adobe.com/de/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"} ab und fügen Sie ihn der `authorized_keys`-Datei auf Ihrem SFTP-Server hinzu, damit sich Analytics authentifizieren kann.
1. Aktivieren Sie das Feature Flag `FEATUREFLAG_USE_ANALYTICS_20_API` auf Ihrer Instanz, indem Sie unter **[!UICONTROL Administration] > [!UICONTROL Plattform] > [!UICONTROL Optionen]** in der Campaign-Explorer-Struktur den Wert `longvalue` der Option auf `1` in [!UICONTROL xtkOption] erstellen oder festlegen. Dieser Schritt ist erforderlich, unabhängig davon, welcher der oben genannten Anwendungsfälle auf Sie zutrifft.
1. Validieren Sie die Migration, indem Sie jeden für Ihre Instanz zutreffenden Anwendungsfall ausführen (Senden einer Testkampagne, Überprüfen der Ankunft von Indikatoren in Analytics und Bestätigen der Verfügbarkeit von Remarketing-Daten), bevor Sie eine alte Verbindung deaktivieren.

## Einrichten eines neuen externen Web Analytics-Kontos {#setting-up-a-new-web-analytics-external-account}

Unabhängig davon, ob Ihre Instanz von Adobe gehostet oder On-Premise/Hybrid ist, gilt Folgendes.

Wenn Sie das externe [!UICONTROL Web Analytics]-Konto zum ersten Mal konfigurieren, anstatt ein vorhandenes zu migrieren, befolgen Sie die [Schritte zur Einrichtung externer Konten](../../installation/using/external-accounts.md#web-analytics-external-account) und den [Leitfaden für die ersten Schritte mit Connectoren](../../integrations/using/gs-aa.md).

Da Analytics 2.0 eine neue Klassifizierungsverarbeitung einführt, müssen Sie auch einen Klassifizierungssatz in Adobe Analytics erstellen, bevor Ihr externes Konto die Klassifizierungsdaten Ihrer Report Suite abrufen kann. Dies ist ein neuer Schritt: Führen Sie ihn nach der Konfiguration Ihrer Konversionsvariablen und Erfolgsereignisse sowie vor der Konfiguration des externen Kontos in Campaign durch.

So erstellen Sie einen Klassifizierungssatz:

1. Wählen Sie in der oberen Menüleiste von [!DNL Adobe Analytics] **[!UICONTROL Komponenten]** > **[!UICONTROL Klassifizierungssätze]** aus und klicken Sie dann auf **[!UICONTROL Neu]**.

   ![](assets/analytics-classification-set-menu.png)

1. Führen Sie im Dialogfeld **[!UICONTROL Neuen Klassifizierungssatz hinzufügen]** Folgendes aus:

   ![](assets/analytics-classification-set-dialog.png)

   * Geben Sie einen **[!UICONTROL Namen]** für den Klassifizierungssatz ein.
   * Legen Sie den **[!UICONTROL Typ]** auf **[!UICONTROL Primär]** fest.
   * Wählen Sie in **[!UICONTROL Auftragsbenachrichtigungen]** aus, wer über erfolgreiche oder fehlgeschlagene Ausführung der Klassifizierungssatzaufträge benachrichtigt werden soll, und geben Sie die entsprechenden E-Mail-Adressen an.
   * Wählen Sie in **[!UICONTROL Abonnements]** Ihre Report Suite und die Konversionsvariable aus, die Sie im vorherigen Schritt für den Namen der internen Kampagne erstellt haben.

1. Wählen Sie **[!UICONTROL Speichern]** aus.

Dieser Klassifizierungssatz wird von Campaign automatisch erkannt, wenn Sie im nächsten Schritt Ihr externes Konto konfigurieren. Weitere Informationen zu Klassifizierungssätzen finden Sie in der [Adobe Analytics-Dokumentation](https://experienceleague.adobe.com/de/docs/analytics/components/classifications/sets/create-set){target="_blank"}.

## Hilfe erforderlich? {#need-help}

Wenn während der Migration Probleme auftreten, wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.
