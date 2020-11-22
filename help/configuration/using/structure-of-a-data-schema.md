---
solution: Campaign Classic
product: campaign
title: Struktur eines Datenschemas
description: Struktur eines Datenschemas
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%

---


# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Schemas wird als Baumstruktur dargestellt. Um es grafisch in der Adobe Campaign-Client-Konsole Ansicht, wählen Sie das gewünschte Schema aus und klicken Sie auf die Unterregisterkarte **[!UICONTROL Struktur]** .

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst angezeigt (Aktiv, Aktiviert usw.) und in alphabetischer Reihenfolge. Die Strukturierungselemente folgen (Postanschrift, Standort) und schließlich die Links (E-Mail-Informationen, Ordner usw.).

Primär erkannte Schlüssel werden durch einen roten Schlüssel identifiziert, Fremdschlüssel durch einen gelben Schlüssel.

Links werden grafisch unterschieden, je nachdem, ob sie zur Tabelle gehören. Diejenigen Beginn aus der Tabelle, die den Fremdschlüssel in der Tabelle enthalten, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Links zur Sammlung &quot;Umkehren&quot;(Abonnement, Bestellungen usw.) am Ende angezeigt.
