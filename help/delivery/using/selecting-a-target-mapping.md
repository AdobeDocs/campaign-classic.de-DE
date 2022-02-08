---
product: campaign
title: Zielgruppen-Mapping auswählen
description: Erfahren Sie, wie Sie Zielgruppen-Mapping
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 89%

---

# Zielgruppen-Mapping auswählen{#selecting-a-target-mapping}

![](../../assets/common.svg)

Standard-Zielgruppe in Versandvorlagen sind die **[!UICONTROL Empfänger]**. Das Zielgruppen-Mapping verwendet also die Felder der Tabelle **nms:recipient**. Adobe Campaign stellt jedoch auch andere Zielgruppen-Mappings zur Verfügung, auf die Sie je nach Bedarf zurückgreifen können.

![](assets/delivery_select_mapping.png)

Folgende Mappings sind vorhanden:

| Name | Verwendung | Standardschema |
|---|---|---|
| Bereich Empfänger | Versand richtet sich an die in der Adobe-Campaign-Datenbank enthaltenen Empfänger | nms:recipient |
| Besucher | Versand richtet sich an Profile, die beispielsweise durch das Weiterleiten von Nachrichten (Virales Marketing) oder durch soziale Netzwerke (Facebook, Twitter) akquiriert wurden. | mns:visitor |
| Abonnements  | Versand richtet sich an Abonnenten eines Informationsdienstes wie z. B. einen Newsletter | nms:subscription |
| Besucher-Abonnements | Versand richtet sich an Besucher, die einen Informationsdienst beziehen | nms:visitorSub |
| Service | Veröffentlichungen auf Twitter oder Facebook | nms:service |
| Benutzer | Versand richtet sich an Adobe-Campaign-Benutzer | nms:operator |
| Externe Datei | Versand basiert auf einer Datei, die alle notwendigen Informationen enthält | Ohne Schema oder Zielgruppe |

>[!NOTE]
>
>Sie können auch neue Zielgruppen-Mappings erstellen. Dieser Vorgang ist erfahrenen Benutzern vorbehalten. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../configuration/using/target-mapping.md).
