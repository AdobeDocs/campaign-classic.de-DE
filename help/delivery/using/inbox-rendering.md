---
product: campaign
title: Inbox Rendering in Campaign
description: Erfahren Sie, wie Sie E-Mail-Renderings erfassen und in einem speziellen Bericht verfügbar machen
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
TQID: 'https://experienceleague.adobe.com/d0fFXi4Ma-PwY8vsSBOmvbhRD4631kUoagNXlf4Rmek'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: 2317b1ea-6db4-58c7-851f-717a69c0f5c0
    internal-label: Inbox Rendering
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: aef0b685-fc31-54d4-b831-a87fdb9d69de
    internal-label: Email Rendering
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 82%
---
# Rendering im Posteingang{#inbox-rendering}

Adobe Campaign nutzt die [Litmus](https://litmus.com/email-testing) Web-basierte E-Mail-Testlösung, um E-Mail-Renderings zu erfassen und in einem dedizierten Bericht verfügbar zu machen.

Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zum Inbox Rendering finden Sie in der [Campaign v8-Dokumentation](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}

## Inbox Rendering aktivieren {#activating-inbox-rendering}

[!BADGE Hybrid und On-Premise]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"}

Für gehostete und hybride Clients wird das Inbox Rendering auf Ihrer Instanz vom technischen Support und von Beratern von Adobe konfiguriert. Weiterführende Informationen dazu erhalten Sie von Ihrem Adobe-Kundenbetreuer.

Gehen Sie bei On-Premise-Installationen wie folgt vor, um das Inbox Rendering zu konfigurieren.

1. Installieren Sie das **[!UICONTROL Inbox Rendering (IR)]**-Package über das Menü **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package-Import]**. Weitere Informationen hierzu finden Sie unter [Installieren von nativen Campaign Classic-Packages](../../installation/using/installing-campaign-standard-packages.md).
1. Konfigurieren Sie ein externes HTTP-Konto über den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]**. Weitere Informationen hierzu finden Sie unter [Externes Konto erstellen](../../installation/using/external-accounts.md#creating-an-external-account).
1. Legen Sie die Parameter für das externe Konto wie folgt fest:
   * **[!UICONTROL Titel]**: Zustellbarkeits-Server-Information
   * **[!UICONTROL Interner Name]**: deliverabilityInstance
   * **[!UICONTROL Typ]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Verschlüsselung]**: Keine
   * Kreuzen Sie die Option **[!UICONTROL Aktiviert]** an.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Wechseln Sie zum Knoten **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]**. Suchen Sie nach der Option **[!UICONTROL DmRendering_cuid]** und wenden Sie sich an den Support, um die ID der Versandberichte abzurufen, die in das Feld **[!UICONTROL Wert (Text)]** kopiert werden muss.
1. Bearbeiten Sie die Datei **serverConf.xml**, um einen Aufruf an den Litmus-Server zuzulassen. Fügen Sie dem Abschnitt `<urlPermission>` die folgende Zeile hinzu:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Laden Sie die Konfiguration mit dem folgenden Befehl neu:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Möglicherweise müssen Sie sich von der Konsole abmelden und sich wieder anmelden, um das Inbox Rendering verwenden zu können.
