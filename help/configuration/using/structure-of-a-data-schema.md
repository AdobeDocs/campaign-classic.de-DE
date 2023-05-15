---
product: campaign
title: Struktur eines Datenschemas
description: Struktur eines Datenschemas
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%

---

# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Datenschemas wird in Form einer Baumstruktur dargestellt. Um es grafisch in der Adobe Campaign-Clientkonsole anzuzeigen, wählen Sie das Zielschema aus und klicken Sie auf **[!UICONTROL Struktur]** Unterregisterkarte.

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst angezeigt (Aktiv, Aktiviert usw.) und in alphabetischer Reihenfolge. Die strukturierenden Elemente kommen als Nächstes (Postanschrift, Ort) und schließlich als Links (E-Mail-Informationen, Ordner usw.).

Primäre Schlüssel werden durch einen roten Schlüssel identifiziert, Fremdschlüssel durch einen gelben Schlüssel.

Links werden grafisch unterschieden, je nachdem, ob sie zur Tabelle gehören. Diejenigen, die von der Tabelle ausgehend beginnen, d. h. die den Fremdschlüssel in der Tabelle haben, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Sammlungslinks &quot;Umkehren&quot;(Abonnements, Bestellungen usw.) werden am Ende angezeigt.
