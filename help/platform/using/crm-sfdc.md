---
product: campaign
title: Campaign-Salesforce CRM-Connector
description: Erfahren Sie, wie Sie Campaign und Salesforce verbinden
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
TQID: https://experienceleague.adobe.com/LeUJ-F5dAECUrtkbvgwL0BN88Alofnh2rBWe7hIVGgI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 351
ht-degree: 100%

---

# Campaign und Salesforce.com verbinden{#connect-to-sfdc}



Auf dieser Seite erfahren Sie, wie Sie Campaign Classic mit **Salesforce** verbinden.

Die Datensynchronisation erfolgt über eine eigene Workflow-Aktivität. [Weitere Informationen](../../platform/using/crm-data-sync.md).


Das externe Konto ermöglicht Ihnen das Importieren und Exportieren von Salesforce-Daten in Adobe Campaign.
Um den CRM-Connector für Salesforce zu konfigurieren, gehen Sie wie folgt vor:

1. Erstellen Sie ein neues externes Konto ausgehend vom Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** im Adobe Campaign-Navigationsbaum.
1. Wählen Sie **[!UICONTROL Salesforce.com]** aus.
1. Geben Sie Einstellungen zum Aktivieren der Verbindung ein.

   ![](assets/ext_account_17.png)

   Um dieses externe Konto für die gemeinsame Verwendung mit Adobe Campaign zu konfigurieren, müssen Sie die folgenden Informationen eingeben:

   * **[!UICONTROL Konto]**
Für die Anmeldung bei Salesforce CRM verwendetes Konto.

   * **[!UICONTROL Passwort]**
Für die Anmeldung bei Salesforce CRM verwendetes Passwort.

   * **[!UICONTROL Client-Kennung]**
Informationen darüber, wo Sie Ihre Client-Kennung finden, erhalten Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&type=1).

   * **[!UICONTROL Sicherheits-Token]**
Informationen darüber, wo Sie Ihr Sicherheits-Token finden, erhalten Sie auf dieser [Seite](https://help.salesforce.com/articleView?id=000205876&type=1).

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

   Klicken Sie hierzu auf den Link **[!UICONTROL Aufzählungssynchronisation...]** und wählen Sie die der Salesforce-Aufzählung entsprechende Adobe Campaign-Aufzählung aus.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Sie können alle Werte einer Adobe Campaign-Aufzählung durch die des CRM-Systems ersetzen: Wählen Sie hierzu in der Spalte **[!UICONTROL Ersetzen]** die Option **[!UICONTROL Ja]**.


   Klicken Sie abschließend auf **[!UICONTROL Weiter]** und **[!UICONTROL Starten]**, um mit dem Listenimport zu beginnen.

1. Prüfen Sie die importierten Werte im Menü **[!UICONTROL Administration > Plattform > Aufzählungen]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Aufzählungen mit Mehrfachauswahl werden nicht unterstützt.

Campaign und Salesforce.com sind jetzt verbunden. Sie können eine Datensynchronisation zwischen den beiden Systemen einrichten.

Um Daten zwischen Adobe Campaign und SFDC zu synchronisieren, müssen Sie einen Workflow erstellen und die Aktivität **[!UICONTROL CRM-Connector]** verwenden.

![](assets/crm_connectors_sfdc_wf.png)

Weitere Informationen zur Datensynchronisation finden Sie [auf dieser Seite](../../platform/using/crm-data-sync.md).
