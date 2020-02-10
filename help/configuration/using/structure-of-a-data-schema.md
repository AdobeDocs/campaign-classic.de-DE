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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Datenschemas wird in Form einer Baumstruktur angezeigt. Um es grafisch in der Adobe Campaign-Client-Konsole anzuzeigen, wählen Sie das gewünschte Schema aus und klicken Sie auf die **[!UICONTROL Structure]** Unterregisterkarte.

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst angezeigt (Aktiv, Aktiviert usw.) und in alphabetischer Reihenfolge. Die Strukturierungselemente folgen (Postanschrift, Standort) und schließlich die Links (E-Mail-Informationen, Ordner usw.).

Primärschlüssel werden durch einen roten Schlüssel identifiziert, Fremdschlüssel durch einen gelben Schlüssel.

Links werden grafisch unterschieden, je nachdem, ob sie zur Tabelle gehören. Diejenigen, die von der Tabelle ausgehen, d. h. die den Fremdschlüssel in der Tabelle haben, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Links zur Sammlung &quot;Umkehren&quot;(Abonnement, Bestellungen usw.) am Ende angezeigt.
