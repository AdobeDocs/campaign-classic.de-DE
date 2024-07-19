---
product: campaign
title: Konfigurieren der Developer Console für Adobe Experience Cloud Triggers
description: Informationen zum Konfigurieren der Developer Console für Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 100%

---

# Konfigurieren der Developer Console für Adobe Experience Cloud Triggers {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Voraussetzungen {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Bevor Sie mit dieser Implementierung beginnen, überprüfen Sie, ob Folgendes vorhanden ist:

* eine gültige **Organisationskennung**: Die Organisations-ID ist die eindeutige Kennung innerhalb der Adobe Experience Cloud, die zum Beispiel für den VisitorID-Dienst und das IMS Single-Sign On (SSO) verwendet wird. [Weitere Informationen](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=de)
* ein **Entwicklerzugriff** auf Ihr Unternehmen. Der Systemadministrator der Organisation muss das Verfahren zum **Hinzufügen von Entwicklern zu einem einzelnen Produktprofil** befolgen, das [auf dieser Seite](https://helpx.adobe.com/de/enterprise/using/manage-developers.html) beschrieben wird. Damit ermöglicht er den Entwicklerzugriff für das `Analytics - {tenantID}` Produktprofil des Adobe Analytics-Produkts, das mit Triggers verbunden ist.

## Schritt 1: Erstellen/Aktualisieren des OAuth-Projekts {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> Die Anmeldedaten für Service-Konten (JWT) werden von Adobe demnächst eingestellt. Campaign-Integrationen mit Adobe-Lösungen und -Apps müssen jetzt mit OAuth-Server-to-Server-Anmeldedaten arbeiten. </br>
>
> * Wenn Sie eingehende Integrationen in Campaign implementiert haben, müssen Sie Ihr technisches Konto migrieren, wie in [dieser Dokumentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank) beschrieben. Bestehende Anmeldedaten für Service-Konten (JWT) sind noch bis zum 27. Januar 2025 gültig.</br>
>
> * Wenn Sie ausgehende Integrationen implementiert haben, z. B. die Integration von Campaign mit Analytics oder Experience Cloud Triggers, funktionieren diese noch bis zum 27. Januar 2025. Vor diesem Datum müssen Sie jedoch Ihre Campaign-Umgebung auf v7.4.1 aktualisieren und Ihr technisches Konto auf OAuth migrieren.

Um mit der Konfiguration Ihres Adobe Analytics-Connectors fortzufahren, greifen Sie auf die Adobe Developer Console zu und erstellen Sie Ihr OAuth-Server-zu-Server-Projekt.

Auf [dieser Seite](oauth-technical-account.md#oauth-service) finden Sie die ausführliche Dokumentation.

## Schritt 2: Hinzufügen der Projektanmeldedaten in Adobe Campaign {#add-credentials-campaign}

Führen Sie die Schritte aus, die auf [dieser Seite](oauth-technical-account.md#add-credentials) beschrieben sind, um Ihre OAuth-Projektanmeldedaten in Adobe Campaign hinzuzufügen.

## Schritt 3: Aktualisieren des Pipelined-Tags {#update-pipelined-tag}

Um das [!DNL pipelined]-Tag zu aktualisieren, müssen Sie den Authentifizierungstyp in der Konfigurationsdatei **config-&lt; Instanzname >.xml** wie folgt entsprechend dem Developer Console-Projekt aktualisieren:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Führen Sie dann einen `config -reload` und einen Neustart von [!DNL pipelined] aus, damit die Änderungen berücksichtigt werden.
