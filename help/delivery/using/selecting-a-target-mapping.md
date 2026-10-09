---
product: campaign
title: Auswählen eines Zielgruppen-Mappings
description: Erfahren Sie, wie man ein Zielgruppen-Mapping durchführt
feature: Delivery Templates
hide: true
role: User
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
TQID: 'https://experienceleague.adobe.com/VpmfQdFoJ2Lfzetqx-s5MAdFdTTEsHxz2ISL15wNXIo'
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
  - id: fc09322a-8f3d-5905-be3d-96adfa806a40
    internal-label: Delivery Templates
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
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 100%
---
# Auswählen eines Zielgruppen-Mappings{#selecting-a-target-mapping}

Standard-Zielgruppe in Versandvorlagen sind die **[!UICONTROL Empfangenden]**. Das Zielgruppen-Mapping verwendet also die Felder der Tabelle **nms:recipient**. Adobe Campaign stellt jedoch auch andere Zielgruppen-Mappings zur Verfügung, auf die Sie je nach Bedarf zurückgreifen können.

![](assets/delivery_select_mapping.png)

Folgende Mappings sind vorhanden:

| Name | Verwendung | Standardschema |
|---|---|---|
| Bereich Empfänger | Versand richtet sich an die in der Adobe Campaign-Datenbank enthaltenen Empfänger | nms:recipient |
| Besuchende | Versand richtet sich an Profile, die beispielsweise durch das Weiterleiten von Nachrichten (Virales Marketing) oder durch soziale Netzwerke (Facebook, X – früher bekannt als Twitter) akquiriert wurden. | mns:visitor |
| Abonnements | Versand richtet sich an Abonnenten eines Informationsdienstes wie z. B. einen Newsletter | nms:subscription |
| Besucher-Abonnements | Versand richtet sich an Besucher, die einen Informationsdienst beziehen | nms:visitorSub |
| Service | Veröffentlichen auf einem X-Konto oder einer Facebook-Seite | nms:service |
| Benutzer | Versand richtet sich an Adobe Campaign-Benutzer | nms:operator |
| Externe Datei | Versand basiert auf einer Datei, die alle notwendigen Informationen enthält | Ohne Schema oder Zielgruppe |

>[!NOTE]
>
>Sie können auch neue Zielgruppen-Mappings erstellen. Diese Option ist erfahrenen Benutzenden vorbehalten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/target-mapping.md).
