---
product: campaign
title: Campaign-Salesforce CRM-Connector
description: Erfahren Sie, wie Sie Campaign und Salesforce verbinden.
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 98%

---

# Campaign und Salesforce.com verbinden{#connect-to-sfdc}

![](../../assets/common.svg)

Auf dieser Seite erfahren Sie, wie Sie Campaign Classic mit **Salesforce** verbinden.

Die Datensynchronisation erfolgt über eine eigene Workflow-Aktivität. [Weitere Informationen](../../platform/using/crm-data-sync.md).


Das externe Konto ermöglicht den Import und Export von Salesforce-Daten in Adobe Campaign.
Gehen Sie wie folgt vor, um CRM-Connector für Salesforce zu konfigurieren:

1. Erstellen Sie ein neues externes Konto ausgehend vom Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** im Adobe Campaign-Navigationsbaum.
1. Wählen Sie **[!UICONTROL Salesforce.com]** aus.
1. Geben Sie Einstellungen zum Aktivieren der Verbindung ein.

   ![](assets/ext_account_17.png)

   Um dieses externe Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

   * **[!UICONTROL Konto]**

Konto, mit dem die Anmeldung bei Salesforce CRM erfolgt

   * **[!UICONTROL Passwort]**
Passwort, mit dem die Anmeldung bei Salesforce CRM erfolgt.

   * **[!UICONTROL Clientkennung]**
Informationen darüber, wo Sie Ihre Client-Kennung finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Sicherheits-Token]**
Informationen darüber, wo Sie Ihr Security-Token finden, erfahren Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API-Version]**
Wählen Sie die Version der API aus.
1. Führen Sie den Konfigurationsassistenten aus, um die Tabelle mit verfügbaren CRMs zu generieren: Mit dem Konfigurationsassistenten können Sie Tabellen erfassen und das passende Schema erstellen.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Zur Übernahme der Konfiguration müssen Sie sich von der Konsole ab- und wieder anmelden.

1. Prüfen Sie unter dem Knoten **[!UICONTROL Administration > Konfiguration > Datenschema]** das in Adobe Campaign erzeugte Schema.

   Beispiel für das Schema **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Sobald das Schema erstellt ist, können Sie Aufzählungen in Salesforce automatisch mit Adobe Campaign synchronisieren.

   Klicken Sie hierzu auf den Link **[!UICONTROL Auflistungssynchronisation...]** und wählen Sie die der Salesforce-Auflistung entsprechende Adobe Campaign-Auflistung aus.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Sie können alle Werte einer Adobe-Campaign-Auflistung durch die des CRM-Systems ersetzen: Wählen Sie hierzu in der Spalte **[!UICONTROL Ersetzen]** die Option **[!UICONTROL Ja]**.


   Klicken Sie abschließend auf **[!UICONTROL Weiter]** und **[!UICONTROL Starten]**, um mit dem Listenimport zu beginnen.

1. Prüfen Sie die importierten Werte im Menü **[!UICONTROL Administration > Plattform > Auflistungen]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Auflistungen mit Mehrfachauswahl werden nicht unterstützt.

Campaign und Salesforce.com sind jetzt verbunden. Sie können eine Datensynchronisation zwischen den beiden Systemen einrichten.

Um Daten zwischen Adobe Campaign und SFDC zu synchronisieren, müssen Sie einen Workflow erstellen und die Aktivität **[!UICONTROL CRM-Connector]** verwenden.

![](assets/crm_connectors_sfdc_wf.png)

Weitere Informationen zur Datensynchronisation finden Sie [auf dieser Seite](../../platform/using/crm-data-sync.md).
