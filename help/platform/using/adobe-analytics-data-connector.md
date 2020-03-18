---
title: Der Data Connector von Adobe Analytics
seo-title: Der Data Connector von Adobe Analytics
description: Der Data Connector von Adobe Analytics
seo-description: null
page-status-flag: never-activated
uuid: 5a1de443-04de-49a8-9057-5d8381e48630
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: 5ff1577f-0809-46fd-ac1e-11b24637e35c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: becdffadaaaa40359b61a6ad786b9fd8ebecc6e9

---


# Der Data Connector von Adobe Analytics{#adobe-analytics-data-connector}

## Über die Integration des Data Connectors {#about-data-connector-integration}

>[!CAUTION]
>
>Adobe Analytics Data Connector ist nicht kompatibel mit Transaktionsnachrichten (Message Center).

Der Data Connector (vormals Adobe-Genesis-Connector) ermöglicht Adobe Campaign und Adobe Analytics die Interaktion über das Package **Web-Analytics-Connectoren**. Dabei werden Daten an Adobe Campaign in Form von Segmenten zum Nutzerverhalten nach einer E-Mail-Kampagne weitergeleitet. Im Gegenzug werden Indikatoren und Attribute von E-Mail-Kampagnen von Adobe Campaign an Adobe Analytics – Data Connector gesendet.

Adobe Campaign verfügt mit dem Data Connector über eine Funktion zur Messung der Performance von Online-Marketingkampagnen (Web Analytics). Adobe Campaign ist somit in der Lage, Daten zum Verhalten von Webseitenbesuchern, die auf eine Marketingkampagne reagieren, abzurufen und nach Analyse gezielte Remarketing-Kampagnen zu schalten, um die Konversionsrate zu steigern. Zugleich ermöglichen die Web-Analytics-Tools die Übermittlung der in Adobe Campaign erzeugten Kampagnenindikatoren und -attribute an die entsprechenden Plattformen.

Weitere Informationen zur Implementierung der Integration von Adobe Analytics mit Adobe Campaign finden Sie in diesem [Handbuch](https://helpx.adobe.com/marketing-cloud/how-to/analytics-ac.html).

Der Aktionsradius der verschiedenen Tools gestaltet sich wie folgt:

* Web-Analytics-Connector:

   1. markiert die mit Adobe Campaign ausgeführten E-Mail-Kampagnen,
   1. speichert in Form von Segmenten das Verhalten der Empfänger auf der Webseite, auf die sie nach Klick auf einen in der E-Mail enthaltenen Link gelangt sind. Die Segmente beziehen sich auf aufgegebene Produkte (auf der Webseite angesehen aber weder gekauft noch in den Warenkorb gelegt), Bestellungen und Transaktionsabbrüche.

* Adobe Campaign:

   1. sendet die Indikatoren und Attribute der Kampagne an den Connector, welcher sie an das Web-Analytics-Tool übermittelt,
   1. ruft Segmente ab und analysiert sie,
   1. löst eine Remarketing-Kampagne aus.

## Integration einrichten {#setting-up-the-integration}

Um den Data Connector einzurichten, verbinden Sie sich mit Ihrer Adobe-Campaign-Instanz und gehen Sie folgendermaßen vor:

* [1. Schritt: Integration in Analytics konfigurieren](#step-1--configure-integration-in-analytics)
* [2. Schritt: Externes Konto in Adobe Campaign erstellen](#step-2--create-the-external-account-in-campaign)
* [3. Schritt: Adobe Campaign und Adobe Analytics synchronisieren](#step-3--synchronize-adobe-campaign-and-adobe-analytics)

### 1. Schritt: Integration in Analytics konfigurieren {#step-1--configure-integration-in-analytics}

Im Folgenden wird die Konfiguration des Data Connectors mithilfe eines Assistenten beschrieben.

1. Melden Sie sich mit einer Adobe-ID oder einer Unternehmenskennung bei Adobe Experience Cloud an.

   ![](assets/adobe_genesis_install_001.png)

1. Wählen Sie aus der Liste der Experience Cloud-Lösungen die Option **[!UICONTROL Analytics]** aus.

   ![](assets/adobe_genesis_install_013.png)

1. Wählen Sie auf der **[!UICONTROL Admin]** Registerkarte **[!UICONTROL Data Connectors]**.

   Für den Zugriff auf das **[!UICONTROL Data Connectors]** Menü benötigen Sie die folgenden Analytics-Tools. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://docs.adobe.com/content/help/en/analytics/admin/admin-console/permissions/analytics-tools.html)
   * Integrationen (Erstellen)
   * Integrationen (Aktualisieren)
   * Integrationen (Löschen)
   ![](assets/adobe_genesis_install_002.png)

1. From the list of partners, select **[!UICONTROL Neolane - Enterprise Marketing Platform]**.

   ![](assets/adobe_genesis_install_014.png)

1. Klicken Sie im **[!UICONTROL Add integration]** Dialogfeld auf **[!UICONTROL Activate]**.
1. Markieren Sie **[!UICONTROL I accept these terms and conditions]** die mit dieser Integration **[!UICONTROL Report suite]** verknüpften Elemente und geben Sie die Verbindungsbeschriftung ein.

   Klicken Sie abschließend auf **[!UICONTROL Create and configure this integration]**.

   ![](assets/adobe_genesis_install_015.png)

1. Enter the email address that will receive the notifications on behalf of the connector, then copy the **[!UICONTROL Account ID]** as it appears in the external Adobe Campaign account (for more on this, refer to the [Step 2: Create the external account in Campaign](#step-2--create-the-external-account-in-campaign)).

   ![](assets/adobe_genesis_install_005.png)

1. Spezifizieren Sie die für die Wirkungsmessung der E-Mail-Kampagne erforderlichen Kennungen, d. h. den internen Kampagnennamen (cid) und die iNmsBroadlog (bid)-Tabellen-ID. Die Indikatoren für die abzurufenden Ereignisse sollten ebenfalls festgelegt werden.
Achten Sie darauf, dass Ihre **[!UICONTROL Events]** Werte numerisch sind, andernfalls werden sie nicht im Dropdown-Menü angezeigt.

   ![](assets/adobe_genesis_install_006.png)

1. Spezifizieren Sie nötigenfalls die personalisierten Segmente.

   ![](assets/adobe_genesis_install_007.png)

1. In **[!UICONTROL Data collection]**, select a method for recovering data, in this case the **[!UICONTROL cid]** and **[!UICONTROL bid]** identifiers specified in step 6.

   ![](assets/adobe_genesis_install_009.png)

1. Wählen Sie die Informationen aus, die im Dashboard dargestellt werden sollen.

   ![](assets/adobe_genesis_install_0112.png)

1. Prüfen Sie die Konfiguration auf der Seite, in der die vorherigen Schritte zusammengefasst werden.

   ![](assets/adobe_genesis_install_011.png)

1. Click **[!UICONTROL Activate Now]** to approve configuration and activate the connector.

   ![](assets/adobe_genesis_install_012.png)

   Der Data Connector ist jetzt konfiguriert.

### 2. Schritt: Externes Konto in Adobe Campaign erstellen {#step-2--create-the-external-account-in-campaign}

Die Integration von Adobe Campaign in die Analytics-Plattformen geschieht mithilfe eines Connectors. Gehen Sie zur Synchronisation wie folgt vor:

1. Installieren Sie das Package **Web-Analytics-Connectoren** in Adobe Campaign.
1. Wechseln Sie zum **[!UICONTROL Administration > Platform > External accounts]** Ordner der Adobe Campaign-Struktur.
1. Right-click the list of external accounts and select **[!UICONTROL New]** in the drop-down menu (or click the **[!UICONTROL New]** button above the list of external accounts).
1. Use the drop-down list to select the **[!UICONTROL Web Analytics]** type.
1. Wählen Sie den Anbieter aus, hier z. B. **[!UICONTROL Adobe Analytics - Data Connector]**.

   ![](assets/webanalytics_ext_account_create_001.png)

1. Click the **[!UICONTROL Enrich the formula...]** link to change the URL calculation formula to specify the Web analytics tool integration information (campaign IDs) and the domains of the sites whose activity must be tracked.
1. Geben Sie den oder die Namen der betroffenen Webseitendomains ein.

   ![](assets/webanalytics_tracking_001.png)

1. Click **[!UICONTROL Next]** and make sure the domain names have been saved.

   ![](assets/webanalytics_tracking_002.png)

1. Bei Bedarf können Sie die Formel überschreiben. Kreuzen Sie hierfür das entsprechende Feld an und ändern Sie die Formel direkt im angezeigten Fenster.

   ![](assets/webanalytics_tracking_003.png)

   >[!CAUTION]
   >
   >Diese Konfigurationsoption sollte erfahrenen Nutzern vorbehalten bleiben, da Fehler in der Formel die Versendung der Nachrichten blockieren können.

1. The **[!UICONTROL Advanced]** tab lets you configure or modify more technical settings.

   * **[!UICONTROL Lifespan]**: können Sie die Verzögerung angeben (in tagen_, nach der die Web-Ereignis in Adobe Campaign nach Technischen Workflows wiederhergestellt wurden). Standard: 180 Tage.
   * **[!UICONTROL Persistence]**: ermöglicht Ihnen den Zeitraum, in dem alle Web-Ereignis (z. B. ein Kauf) einem Remarketing-Campaign zugeordnet werden können (Standard: 7 Tage.

>[!NOTE]
>
>Wenn Sie mehrere Audiencen-Messwerkzeuge verwenden, können Sie beim Erstellen des Externen Kontos **[!UICONTROL Other]** in der **[!UICONTROL Partners]** Dropdown-Liste auswählen. Sie können nur auf ein Externe Konto in den Eigenschaften des Versands verweisen: Sie müssen daher die Formel der verfolgten URLs anpassen, indem Sie die von Adobe und allen anderen Messwerkzeugen erwarteten Parameter hinzufügen.

### 3. Schritt: Adobe Campaign und Adobe Analytics synchronisieren {#step-3--synchronize-adobe-campaign-and-adobe-analytics}

Nach Erstellung des externen Kontos ist eine Synchronisation der beiden Anwendungen erforderlich.

1. Gehen Sie zum zuvor erstellten externen Konto.
1. Change the account **[!UICONTROL Label]** as needed.
1. Change the **[!UICONTROL Internal name]** so that it matches the **[!UICONTROL Name]** chosen while configuring the Data Connector.

   ![](assets/webanalytics_ext_account_setting_001.png)

1. Klicken Sie auf den **[!UICONTROL Approve connection]** Link.

   ![](assets/webanalytics_ext_account_setting_002.png)

   Make sure the **[!UICONTROL Internal name]** matches the **[!UICONTROL Name]** specified in the Data Connector configuration wizard.

1. Enter the **[!UICONTROL Account ID]** in the Data Connector configuration wizard.

   ![](assets/webanalytics_ext_account_setting_003.png)

1. Durchlaufen Sie alle Schritte des Data Connector-Assistenten bis zum Ende und kehren Sie zum externen Konto in Adobe Campaign zurück.
1. Click **[!UICONTROL Next]** in order for the data exchange to take place between Adobe Campaign and Adobe Analytics - Data connector.

   Nach erfolgter Synchronisation wird die Liste der Segmente angezeigt:

   ![](assets/webanalytics_ext_account_setting_004.png)

When the synchronization of data between Adobe Campaign and Adobe Analytics - Data connector is effective, the three default segments defined in the Data Connector wizard are recovered by Adobe Campaign and become accessible in the **[!UICONTROL Segments]** tab of the Adobe Campaign external account.

![](assets/webanalytics_segments.png)

Wenn im Data Connector-Assistenten weitere Segmente konfiguriert wurden, können Sie diese zu Adobe Campaign hinzufügen. Klicken Sie dazu auf den **[!UICONTROL Update segment list]** Link und befolgen Sie die im Externe Konto-Assistenten beschriebenen Schritte. Sobald der Vorgang durchgeführt wurde, werden die neuen Segmente in der Liste angezeigt.

![](assets/webanalytics_segments_update.png)

### Technische Workflows der Web-Analytics-Prozesse {#technical-workflows-of-web-analytics-processes}

Der Datenaustausch zwischen Adobe Campaign und Adobe Analytics – Data Connector wird durch vier im Hintergrund ablaufende technische Workflows gesteuert.

Sie sind in der Adobe Campaign-Struktur unter dem **[!UICONTROL Administration > Production > Technical workflows > Web analytics process]** Ordner verfügbar.

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**: einmal pro Stunde werden in diesem Arbeitsablauf Segmente zum Verhalten von Benutzern auf einer bestimmten Site heruntergeladen, in die Adobe Campaign-Datenbank aufgenommen und der Remarketing-Arbeitsablauf Beginn.
* **[!UICONTROL Event purge]**: Mit diesem Arbeitsablauf können Sie alle Ereignis je nach dem im **[!UICONTROL Lifespan]** Feld konfigurierten Zeitraum aus der Datenbank löschen. Weitere Informationen finden Sie in [Schritt 2: Erstellen Sie das Externe Konto in Campaign](#step-2--create-the-external-account-in-campaign).
* **[!UICONTROL Identification of converted contacts]**: Verzeichnis der Besucher, die nach einem Remarketing-Campaign einen Kauf tätigten. Die von diesem Arbeitsablauf erfassten Daten können im **[!UICONTROL Re-marketing efficiency]** Bericht abgerufen werden, siehe diese [Seite](#creating-a-re-marketing-campaign).* **[!UICONTROL Sending of indicators and campaign attributes]**: lets you send email campaign indicators via Adobe Campaign to the Adobe Experience Cloud using Adobe Analytics - Data connector. Dieser Arbeitsablauf wird jeden Tag um 4 Uhr ausgelöst und es kann 24 Stunden dauern, bis die Daten an Analytics gesendet werden.

   Bitte beachten Sie, dass dieser Workflow nicht neu gestartet werden sollte, da sonst alle vorherigen Daten erneut gesendet werden, was die Analyseergebnisse verfälschen könnte.

   Folgende Indikatoren werden übermittelt:

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@processed)
   * **[!UICONTROL Success]** (@success)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@recipientOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personClick)
   * **[!UICONTROL Number of distinct clicks]** (@recipientClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@error)
   >[!NOTE]
   >
   >Die gesendete Daten sind die Differenz zur letzten Übermittlung, was zu einem negativen Wert in den Metrikdaten führen kann.

   Folgende Attribute werden übermittelt:

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** Titel (operation/@): nur bei installiertem **Campaign**-Package
   * **[!UICONTROL Nature]** Art (operation/@): nur bei installiertem **Campaign**-Package
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (Scheduling/@contactDate)


* **Identifizierung konvertierter Kontakte**: Verzeichnis der Besucher, die nach einem Remarketing-Campaign einen Kauf tätigten. Die von diesem Workflow erfassten Daten können im **[!UICONTROL Re-marketing efficiency]** Bericht abgerufen werden (siehe diese [Seite](../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign)).

## Versandverfolgung in Adobe Campaign {#tracking-deliveries-in-adobe-campaign}

Damit die Adobe Experience Cloud nach Versand der Nachrichten durch Adobe Campaign die Aktivitäten auf den Webseiten verfolgen kann, muss der entsprechende Connector in den Versandeigenschaften angegeben werden. Gehen Sie wie folgt vor:

1. Öffnen Sie den Versand der zu verfolgenden Kampagne.

   ![](assets/webanalytics_delivery_properties_003.png)

1. Öffnen Sie die Versandeigenschaften.
1. Go to the **[!UICONTROL Web Analytics]** tab and select the previously created external account. Refer to [Step 2: Create the external account in Campaign](#step-2--create-the-external-account-in-campaign)).

   ![](assets/webanalytics_delivery_properties_002.png)

1. Jetzt können Sie Ihre Nachrichten senden und auf den entsprechenden Bericht in Adobe Analytics zugreifen.

## Remarketing-Kampagne erstellen {#creating-a-re-marketing-campaign}

Zur Vorbereitung von Remarketing-Kampagnen ist die Erstellung von spezifischen Versandvorlagen erforderlich. Anschließend ist die Remarketing-Kampagne zu konfigurieren und einem Segment zuzuweisen. Jedem Segment muss eine andere Remarketing-Kampagne entsprechen.

Remarketing-Kampagnen werden automatisch gestartet, sobald Adobe Campaign Daten zur Verhaltensanalyse der Zielgruppe der ursprünglichen Kampagne abgerufen hat. Wenn eine Transaktion abgebrochen oder ein Artikel ohne Kauf angesehen wurde, erhalten die entsprechenden Zielpersonen einen Versand, um die Kaufentscheidung auszulösen.

Adobe Campaign stellt vorkonfigurierte Versandvorlagen zur Verfügung, die Sie verwenden oder als Anregung für Ihre Kampagnen nutzen können.

1. Wechseln Sie von der **[!UICONTROL Explorer]** Seite zum **[!UICONTROL Resources > Templates > Delivery templates]** Ordner der Adobe Campaign-Struktur.
1. Duplicate the **[!UICONTROL Email delivery (re-marketing)]** template or the re-marketing template examples offered by Adobe Campaign.
1. Passen Sie die Vorlage Ihren Bedürfnissen an und speichern Sie sie.

   ![](assets/webanalytics_delivery_model.png)

1. Create a new campaign and select the **[!UICONTROL Re-marketing campaign]** template from the drop-down list.

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. Click the **[!UICONTROL Configure...]** link to specify the segment and delivery template linked to the campaign.
1. Wählen Sie zunächst das zuvor konfigurierte externe Konto aus;

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. Wählen Sie das betreffende Segment aus;

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. Select the delivery template to be used for this re-marketing campaign, then click **[!UICONTROL Finish]** to close the window.

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. Klicken Sie nun auf **[!UICONTROL OK]**, um das Kampagnenfenster zu schließen.

Der Zugriff auf den **[!UICONTROL Re-marketing efficiency]** Bericht erfolgt über die Seite &quot;Globale Berichte&quot;. Damit können Sie die Anzahl der umgerechneten Kontakte (d. h. die gekaufte Ware) im Verhältnis zur Anzahl der Warenkorbabbrüche nach dem Adobe Campaign-Remarketing-Campaign Ansicht werden. Der Konversionsrate wird pro Woche, Monat oder seit dem Beginn der Synchronisierung zwischen Adobe Campaign- und Webanalysetools berechnet.

![](assets/webanalytics_reporting.png)

