---
title: Struktur eines Datenschemas
seo-title: Struktur eines Datenschemas
description: Struktur eines Datenschemas
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 13%

---


# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Schemas wird als Baumstruktur dargestellt. Um es grafisch in der Adobe Campaign-Client-Konsole Ansicht, wählen Sie das gewünschte Schema aus und klicken Sie auf die Unterregisterkarte **[!UICONTROL Struktur]** .

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst angezeigt (Aktiv, Aktiviert usw.) und in alphabetischer Reihenfolge. Die Strukturierungselemente folgen (Postanschrift, Standort) und schließlich die Links (E-Mail-Informationen, Ordner usw.).

Primär erkannte Schlüssel werden durch einen roten Schlüssel identifiziert, Fremdschlüssel durch einen gelben Schlüssel.

Links werden grafisch unterschieden, je nachdem, ob sie zur Tabelle gehören. Diejenigen Beginn aus der Tabelle, die den Fremdschlüssel in der Tabelle enthalten, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Links zur Sammlung &quot;Umkehren&quot;(Abonnement, Bestellungen usw.) am Ende angezeigt.
