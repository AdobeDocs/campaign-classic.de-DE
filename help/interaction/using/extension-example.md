---
title: Beispiel einer Erweiterung
seo-title: Beispiel einer Erweiterung
description: Beispiel einer Erweiterung
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Beispiel einer Erweiterung{#extension-example}

Im Fall eines eingehenden Kontakts (Callcenter oder Webseite) bestimmt das Angebotsmodul die besten zu unterbreitenden Angebote anhand einer Reihe von Eignungsregeln. Zur Anreicherung der Eignungskriterien Ihrer Angebote ist zunächst das Schema **nms:interaction zu erweitern**.

* Um einen neuen Anwendungskontext hinzuzufügen, erweitern Sie das Schema **nms:interaction** und fügen Sie die benötigte Anzahl an **attribute**-Elementen in das Schema ein.

   Im folgenden Beispiel wurden der Ländercode und die zuletzt besuchte Webseite hinzugefügt:

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Im Anschluss an die Erweiterung können Sie die neuen Attribute in der Definition der Eignungsregeln verwenden.

   Im vorliegenden Beispiel werden Eignungskriterien erstellt, die das Land und die zuletzt besuchte Seite des Kontakts berücksichtigen.

   ![](assets/s_ncs_configuration_offer_context.png)

* When configuring SOAP calls, insert the **context** XML element to reference context information added in the interaction schema. Weitere Informationen finden Sie unter [Integration via SOAP (serverseitig)](../../interaction/using/integration-via-soap--server-side-.md).

