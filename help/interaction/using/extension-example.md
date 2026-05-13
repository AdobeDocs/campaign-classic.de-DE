---
product: campaign
title: Beispiel einer Erweiterung
description: Beispiel einer Erweiterung
feature: Interaction, Offers
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
TQID: https://experienceleague.adobe.com/TQZaYrJop03HAw47XPFqgmoxb073iC-xztTp-f-5dEk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 160
ht-degree: 79%

---

# Beispiel einer Erweiterung{#extension-example}



Im Fall eines eingehenden Kontakts (Callcenter oder Webseite) bestimmt das Angebotsmodul die besten zu unterbreitenden Angebote anhand einer Reihe von Eignungsregeln. Um die Eignungskriterien Ihrer Angebote anzureichern, erweitern Sie das Schema **nms:interaction** .

* Um einen neuen Interaktionskontext hinzuzufügen, erweitern Sie das **nms:interaction**-Schema und erstellen Sie so viele **attribute**-Elemente wie nötig im Schema.

  Im folgenden Beispiel wurden der Ländercode und die zuletzt besuchte Webseite hinzugefügt:

  ![](assets/s_ncs_configuration_offer_schemas.png)

* Im Anschluss an die Erweiterung können Sie die neuen Attribute in der Definition der Eignungsregeln verwenden.

  Im vorliegenden Beispiel werden Eignungskriterien erstellt, die das Land und die zuletzt besuchte Seite des Kontakts berücksichtigen.

  ![](assets/s_ncs_configuration_offer_context.png)

* Fügen Sie bei der Konfiguration der SOAP-Aufrufe das XML-Element **context** ein, um die kontextbezogenen Informationen, um die Sie zuvor das Interaction-Schema erweitert haben, zu referenzieren. Weitere Informationen hierzu finden Sie unter [SOAP-Integration (Server-seitig)](../../interaction/using/integration-via-soap-server-side.md).
