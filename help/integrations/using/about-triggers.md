---
product: campaign
title: Über Adobe Experience Cloud Triggers
description: Erste Schritte mit der Implementierung von Adobe Experience Cloud Triggers.
feature: Triggers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
TQID: https://experienceleague.adobe.com/gWgUCcgsqeMw-mzVdhVodcp91lgTCCL7XGWp0f2ItKo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 100%

---

# Verwenden von Campaign und Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] ist eine Integration zwischen Adobe Campaign und Adobe Analytics mithilfe der Pipeline. Die Pipeline ruft Aktionen oder Auslöser der Benutzer von Ihrer Website ab. Ein Beispiel für einen Auslöser ist ein Warenkorbabbruch. Trigger werden in Adobe Campaign verarbeitet, um in nahezu Echtzeit E-Mails zu senden.

>[!CAUTION]
>
>Diese Funktion ist nicht im Produkt vorkonfiguriert. Wenden Sie sich für diese Implementierung an den Adobe-Support/die Kundenunterstützung. Sie können dann die auf [dieser Seite](../../integrations/using/configuring-pipeline.md#prerequisites) beschriebenen Schritte durchführen.

[!DNL Triggers] führen nach der Aktion einer Benutzerin oder eines Benutzers in einem kurzen Zeitraum Marketing-Aktionen aus. Die typische Reaktionszeit beträgt weniger als eine Stunde.

Dadurch werden flexiblere Integrationen möglich, da der Konfigurationsaufwand minimal ist und keine Drittanbieter beteiligt sind.
Unterstützt werden auch große Traffic-Volumen, ohne dass die Performance von Marketing-Aktivitäten leidet. Beispielsweise kann die Integration eine Million Auslöser pro Stunde verarbeiten.

![](assets/do-not-localize/book.png) Entdecken Sie, wie Sie [einen Experience Cloud-Trigger erstellen](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html?lang=de) und kritische Verbraucherverhaltensweisen identifizieren, definieren und überwachen können.

## [!DNL Triggers]-Architektur {#triggers-architecture}

Der [!DNL pipelined]-Prozess wird auf dem Adobe Campaign-Marketing-Server kontinuierlich ausgeführt. Er stellt eine Verbindung zur Pipeline her, ruft die Ereignisse ab und verarbeitet sie sofort.

![](assets/triggers_2.png)

Der [!DNL pipelined]-Prozess meldet sich mit einem Authentifizierungsdienst bei Experience Cloud an und sendet einen privaten Schlüssel. Der Authentifizierungsdienst gibt ein Token zurück. Das Token dient beim Abrufen der Ereignisse zum Authentifizieren.

## Voraussetzungen {#adobe-io-prerequisites}

Bevor Sie mit dieser Implementierung beginnen, überprüfen Sie, ob Folgendes vorhanden ist:

* eine gültige **Organisationskennung**: Die Organisations-ID ist die eindeutige Kennung innerhalb der Adobe Experience Cloud, die zum Beispiel für den VisitorID-Dienst und das IMS Single-Sign On (SSO) verwendet wird. [Weitere Informationen](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de)
* ein **Entwicklerzugriff** auf Ihr Unternehmen. Der Systemadministrator der Organisation muss das Verfahren zum **Hinzufügen von Entwicklern zu einem einzelnen Produktprofil** befolgen, das [auf dieser Seite](https://helpx.adobe.com/de/enterprise/using/manage-developers.html) beschrieben wird. Damit ermöglicht er den Entwicklerzugriff für das `Analytics - {tenantID}` Produktprofil des Adobe Analytics-Produkts, das mit Triggers verbunden ist.

## Implementierungsschritte {#implement}

Gehen Sie wie folgt vor, um Campaign und Experience Cloud Triggers zu implementieren:

1. Erstellen Sie ein OAuth-Projekt. [Weitere Informationen](oauth-technical-account.md#oauth-service)

1. Fügen Sie Ihre OAuth-Projektanmeldedaten in Adobe Campaign hinzu. [Weitere Informationen](oauth-technical-account.md#add-credentials)

1. Aktualisieren Sie den Authentifizierungstyp für das Developer Console-Projekt in der Konfigurationsdatei **config-&lt; Instanzname >.xml** wie folgt:

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   Führen Sie dann einen `config -reload` und einen Neustart von [!DNL pipelined] aus, damit die Änderungen berücksichtigt werden.

