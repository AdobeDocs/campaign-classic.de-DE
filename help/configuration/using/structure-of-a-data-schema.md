---
product: campaign
title: Struktur eines Datenschemas
description: Struktur eines Datenschemas
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 143
ht-degree: 10%

---

# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Datenschemas wird in Form einer Baumstruktur angezeigt. Um es grafisch in der Adobe Campaign-Client-Konsole anzuzeigen, wählen Sie das Zielschema aus und klicken Sie auf die Unterregisterkarte **[!UICONTROL Struktur]**.

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst angezeigt (aktiv, aktiviert usw.) und in alphabetischer Reihenfolge. Als Nächstes folgen die Strukturierungselemente (Postanschrift, Standort) und schließlich die Links (E-Mail-Informationen, Ordner usw.).

Primäre Schlüssel werden durch einen roten Schlüssel und Fremdschlüssel durch einen gelben Schlüssel identifiziert.

Relationen werden grafisch danach unterschieden, ob sie zur Tabelle gehören. Diejenigen, die von der Tabelle ausgehen, d. h. die den Fremdschlüssel in der Tabelle haben, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Sammlungslinks für „Umkehren“ (Abonnement, Bestellungen usw.) werden am Ende angezeigt.
