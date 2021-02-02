---
solution: Campaign Classic
product: campaign
title: CRM-Connectoren
description: Erste Schritte mit CRM-Connectoren in Campaign
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 100%

---


# CRM-Connectoren{#crm-connectors}

## Erste Schritte mit CRM-Connectoren {#about-crm-connectors}

Adobe Campaign stellt verschiedene CRM-Connectoren zur Verfügung, die die Verbindung der Adobe Campaign-Plattform mit Drittsystemen ermöglichen. So erlauben die CRM-Connectoren z. B. das Synchronisieren von Kontakten, Konten und Bestellungen. Zudem vereinfachen sie die Integration der Anwendung in bestehende Systeme.

Dank der Connectoren ist eine schnelle und einfache Datenintegration möglich. Mithilfe eines spezifischen Assistenten lassen sich Daten aus den im CRM-System verfügbaren Tabellen auswählen und sammeln. Die Zwei-Wege-Synchronisation der Informationen gewährleistet einen einheitlichen Datenstand auf den verschiedenen Systemen.

>[!NOTE]
>
>Diese Funktion ist in Adobe Campaign über das **CRM Connectoren-** Package verfügbar.


### Kompatible Systeme {#compatible-crm-systems-and-limitations}

Unterstützte CRM-Systeme und Versionen werden in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md) von Campaign erläutert.

>[!NOTE]
>
>Die CRM-Connectoren funktionieren ausschließlich unter Verwendung einer sicheren URL (https).

### Umsetzung {#crm-implementation-steps}

Eine schrittweise Anleitung zum Verbinden von Campaign und Microsoft Dynamics finden Sie [in diesem Abschnitt](../../platform/using/crm-ms-dynamics.md).

Zur Verwendung von CRM-Connectoren in Adobe Campaign führen Sie generell folgende Schritte aus:

1. Erstellen Sie ein neues externes Konto ausgehend vom Knoten **[!UICONTROL Administration > Plattform > Externe Konten]** im Adobe Campaign-Navigationsbaum.
1. Wählen Sie das CRM-System aus, mit dem Sie Campaign verbinden möchten.
1. Geben Sie Einstellungen zum Aktivieren der Verbindung ein.
1. Führen Sie den Konfigurationsassistenten aus, um die Tabelle mit verfügbaren CRMs zu generieren: Mit dem Konfigurationsassistenten können Sie Tabellen erfassen und das passende Schema erstellen.

   Beispiel für den Konfigurationsassistenten **Salesforce**:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Zur Übernahme der Konfiguration müssen Sie sich von der Konsole ab- und wieder anmelden.

1. Prüfen Sie unter dem Knoten **[!UICONTROL Administration > Konfiguration > Datenschema]** das in Adobe Campaign erzeugte Schema.

   Beispiel für das Schema **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Anschließend können Sie automatisch die Auflistungen aus dem CRM-System mit Adobe Campaign synchronisieren.

   Klicken Sie hierzu auf den Link **[!UICONTROL Auflistungen synchronisieren...]** und wählen Sie die der Auflistung des CRM-Systems entsprechende Adobe-Campaign-Auflistung aus.

   >[!NOTE]
   >
   >Sie können alle Werte einer Adobe-Campaign-Auflistung durch die des CRM-Systems ersetzen: Wählen Sie hierzu in der Spalte **[!UICONTROL Ersetzen]** die Option **[!UICONTROL Ja]**.

   Beispiel für Auflistungen in **Salesforce**:

   ![](assets/crm_connectors_sfdc_enum.png)

   Klicken Sie abschließend auf **[!UICONTROL Weiter]** und **[!UICONTROL Starten]**, um mit dem Listenimport zu beginnen.

1. Prüfen Sie die importierten Werte im Menü **[!UICONTROL Administration > Plattform > Auflistungen]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Auflistungen mit Mehrfachauswahl in Salesforce werden nicht unterstützt.

1. Um Daten zwischen Adobe Campaign und dem CRM-System zu synchronisieren, müssen Sie einen Workflow erstellen und die Aktivität **[!UICONTROL CRM-Connector]** verwenden.

   ![](assets/crm_connectors_sfdc_wf.png)

   Weitere Informationen zur Datensynchronisation finden Sie [auf dieser Seite ](../../platform/using/crm-data-sync.md).
