---
product: campaign
title: Konfigurieren der Integration mit Adobe Experience Manager
description: Hier erfahren Sie, wie Sie die Integration von Campaign mit AEM konfigurieren.
feature: Experience Manager Integration
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
exl-id: 54ee88b2-e646-4fb9-abec-957f0096f15f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 95%

---

# Konfigurieren der Integration von Campaign mit AEM{#configuring-the-integration}



## Konfigurationsschritte in Adobe Campaign {#configuring-in-adobe-campaign}

Um die kombinierte Nutzung von Adobe Campaign und Adobe Experience Manager zu ermöglichen, ist zunächst eine Konfiguration beider Lösungen erforderlich.

Führen Sie die unten aufgeführten Schritte aus, um die Konfiguration in Adobe Campaign zu beginnen:

1. [Installieren Sie das AEM-Integrations-Package in Adobe Campaign.](#install-the-aem-integration-package-in-adobe-campaign)
1. [Konfigurieren Sie das externe Konto.](#configure-the-external-account)
1. [Konfigurieren Sie AEM-Ressourcenfilter.](#configure-aem-resources-filtering)

Erweiterte Konfigurationen wie die Verwaltung von Personalisierungsfeldern und -bausteinen finden Sie im [Handbuch](https://helpx.adobe.com/de/experience-manager/6-5/sites/administering/using/campaignonpremise.html) von Adobe Experience Manager.

### Installieren Sie das AEM-Integrations-Package in Adobe Campaign. {#install-the-aem-integration-package-in-adobe-campaign}

Installieren Sie zunächst das **[!UICONTROL AEM-Integrations]**-Package.

1. Wählen Sie in Ihrer Adobe-Campaign-Instanz aus der oberen Symbolleiste die Option **[!UICONTROL Werkzeuge]** aus.
1. Wählen Sie **[!UICONTROL Tools > Erweitert > Package-Import...]** aus.

   ![](assets/aem_config_1.png)

1. Wählen Sie **[!UICONTROL Standard-Package installieren]** aus.
1. Aktivieren Sie die Option **[!UICONTROL Integration mit Adobe Experience Manager]** und wählen Sie dann die Schaltfläche **[!UICONTROL Weiter]** aus.

   ![](assets/aem_config_2.png)

1. Wählen Sie im nächsten Fenster die Schaltfläche **[!UICONTROL Starten]** aus, um mit der Installation des Package zu beginnen. Schließen Sie das Fenster, nachdem die Installation beendet wurde.

### Sicherheitszone für AEM-Operator konfigurieren {#configure-the-security-zone-for-aem-operator}

Das Package **[!UICONTROL Integration mit Adobe Experience Manager]** definiert den **[!UICONTROL aemserver]**-Operator in Campaign. Mit diesem Operator wird der Adobe-Experience-Manager-Server mit Adobe Campaign verbunden.

Sie müssen für diesen Operator eine Sicherheitszone konfigurieren, um über Adobe Experience Manager eine Verbindung mit Adobe Campaign herzustellen.

>[!CAUTION]
>
>Es wird dringend empfohlen, eine Sicherheitszone für AEM zu erstellen, um Sicherheitsprobleme zu vermeiden. Weitere Informationen hierzu finden Sie im Abschnitt Installation . [Handbuch](../../installation/using/security-zones.md).

Wenn Ihre Campaign-Instanz von Adobe gehostet wird, wenden Sie sich an das Team der [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Gehen Sie wie folgt vor, wenn Sie eine On-Premise-Bereitstellung von Campaign verwenden:

1. Öffnen Sie die Konfigurationsdatei **serverConf.xml**.
1. Gehen Sie zum Attribut **allowUserPassword** der ausgewählten Sicherheitszone und setzen Sie es auf **true**.

   Dadurch kann Adobe Experience Manager mit Adobe Campaign per Anmeldung/Passwort eine Verbindung herstellen.

### Externes Konto konfigurieren {#configure-the-external-account}

Mit dem Package **[!UICONTROL Integration mit Adobe Experience Manager]** wurde das externe Konto für Adobe Experience Cloud erstellt. Jetzt muss es konfiguriert werden, um eine Verbindung mit Ihrer Adobe Experience Manager-Instanz herzustellen.

Gehen Sie zur Konfiguration des externen AEM-Kontos folgendermaßen vor:

1. Wählen Sie die **[!UICONTROL Explorer]**-Schaltfläche aus.

   ![](assets/aem_config_3.png)

1. Wählen Sie **[!UICONTROL Administration > Plattform > Externe Konten]** aus.
1. Wählen Sie in der Liste **[!UICONTROL Externes Konto]** die Option **[!UICONTROL AEM-Instanz]** aus.
1. Geben Sie die Parameter für Ihre AEM-Authoring-Instanz ein:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Konto]**
   * **[!UICONTROL Passwort]**

   >[!NOTE]
   >
   >Achten Sie darauf, dass Ihre **[!UICONTROL Server]**-Adresse nicht mit einem Schrägstrich endet.

   ![](assets/aem_config_4.png)

1. Kreuzen Sie die Option **[!UICONTROL Aktiviert]** an.
1. Wählen Sie die Schaltfläche **[!UICONTROL Speichern]** aus.

### AEM-Ressourcenfilter konfigurieren {#configure-aem-resources-filtering}

Mit der Option **AEMResourceTypeFilter** werden die Typen von Experience-Manager-Ressourcen herausgefiltert, die in Adobe Campaign verwendet werden können. Dadurch kann Adobe Campaign Inhalte von Experience Manager abrufen, die speziell für die Verwendung in Adobe Campaign konzipiert sind.

So prüfen Sie, ob die Option **[!UICONTROL AEMResourceTypeFilter]** konfiguriert ist:

1. Wählen Sie die **[!UICONTROL Explorer]**-Schaltfläche aus.
1. Wählen Sie **[!UICONTROL Administration > Plattform > Optionen]** aus.
1. Wählen Sie in der Liste **[!UICONTROL Optionen]** die Option **[!UICONTROL AEMResourceTypeFilter]** aus.
1. Im Feld **[!UICONTROL Wert (text)]** sollte der Pfad folgendermaßen dargestellt sein:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   In manchen Fällen sieht er auch so aus:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Konfigurationsschritte in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Führen Sie die unten aufgeführten Schritte aus, um die Konfiguration in Adobe Experience Manager zu beginnen:

1. Konfigurieren Sie die **Replikation** zwischen der AEM-Autoreninstanz und der AEM-Veröffentlichungsinstanz.

   Weiterführende Informationen zur Konfiguration der Replikation finden Sie im [Handbuch](https://helpx.adobe.com/de/experience-manager/6-5/sites/deploying/using/replication.html) von Adobe Experience Manager.

1. Stellen Sie die Verbindung zwischen Adobe Experience Manager und Adobe Campaign her, indem Sie einen dedizierten **Cloud Service** konfigurieren.

   Weiterführende Informationen zur Verbindung beider Lösungen über Cloud Services finden Sie im [Handbuch](https://helpx.adobe.com/de/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) von Adobe Experience Manager .

1. Konfigurieren Sie den **Externalizer-Dienst**.

   Weiterführende Informationen zur Konfiguration finden Sie im [Handbuch](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/externalizer.html) von Adobe Experience Manager.
