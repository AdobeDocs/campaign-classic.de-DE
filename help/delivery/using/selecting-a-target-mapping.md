---
product: campaign
title: Auswählen eines Zielgruppen-Mappings
description: Erfahren Sie, wie man ein Zielgruppen-Mapping durchführt
feature: Delivery Templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: ht
source-wordcount: '181'
ht-degree: 100%

---

# Auswählen eines Zielgruppen-Mappings{#selecting-a-target-mapping}

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
