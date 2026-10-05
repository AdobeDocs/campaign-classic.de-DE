---
product: campaign
title: Struktur eines Datenschemas
description: Struktur eines Datenschemas
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: 'https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 10%
---
# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Datenschemas wird in Form einer Baumstruktur angezeigt. Um es grafisch in der Adobe Campaign-Client-Konsole anzuzeigen, wählen Sie das Zielschema aus und klicken Sie auf die Unterregisterkarte **[!UICONTROL Struktur]**.

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst angezeigt (aktiv, aktiviert usw.) und in alphabetischer Reihenfolge. Als Nächstes folgen die Strukturierungselemente (Postanschrift, Standort) und schließlich die Links (E-Mail-Informationen, Ordner usw.).

Primäre Schlüssel werden durch einen roten Schlüssel und Fremdschlüssel durch einen gelben Schlüssel identifiziert.

Relationen werden grafisch danach unterschieden, ob sie zur Tabelle gehören. Diejenigen, die von der Tabelle ausgehen, d. h. die den Fremdschlüssel in der Tabelle haben, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Sammlungslinks für „Umkehren“ (Abonnement, Bestellungen usw.) werden am Ende angezeigt.
