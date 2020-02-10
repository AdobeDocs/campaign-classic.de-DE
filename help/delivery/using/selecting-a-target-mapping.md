---
title: Zielgruppen-Mapping wählen
seo-title: Zielgruppen-Mapping wählen
description: Zielgruppen-Mapping wählen
seo-description: null
page-status-flag: never-activated
uuid: 29a666a3-2ecc-4732-b068-c93935929771
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: e2c6e273-1640-4f46-a80e-0cecb06e2769
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Zielgruppen-Mapping wählen{#selecting-a-target-mapping}

Standardmäßig werden Bereitstellungsvorlagen als Ziel ausgewählt **[!UICONTROL Recipients]**. Ihre Zielzuordnung verwendet daher die Felder der Tabelle **nms:empfänger** . Adobe Campaign bietet weitere Zielzuordnungen für Ihre Auslieferungen, die je nach Bedarf verwendet werden.

![](assets/delivery_select_mapping.png)

Folgende Mappings sind vorhanden:

| Name | Verwendung | Standardschema |
|---|---|---|
| Bereich Empfänger | Versand richtet sich an die in der Adobe-Campaign-Datenbank enthaltenen Empfänger | nms:recipient |
| Besucher | Versand richtet sich an Profile, die beispielsweise durch das Weiterleiten von Nachrichten (Virales Marketing) oder durch soziale Netzwerke (Facebook, Twitter) akquiriert wurden. | mns:visitor |
| Abonnements  | Versand richtet sich an Abonnenten eines Informationsdienstes wie z. B. einen Newsletter | nms:subscription |
| Besucher-Abonnements | Versand richtet sich an Besucher, die einen Informationsdienst beziehen | nms:visitorSub |
| Service | Publikationen auf Twitter oder Facebook | nms:service |
| Benutzer | Versand richtet sich an Adobe-Campaign-Benutzer | nms:operator |
| Externe Datei | Versand basiert auf einer Datei, die alle notwendigen Informationen enthält | Ohne Schema oder Zielgruppe |

>[!NOTE]
>
>Es besteht die Möglichkeit, weitere Zielgruppen-Mappings zu erstellen. Dies sollte jedoch erfahrenen Nutzern vorbehalten bleiben. Weiterführende Informationen finden Sie im [Konfigurationshandbuch](../../configuration/using/target-mapping.md).
