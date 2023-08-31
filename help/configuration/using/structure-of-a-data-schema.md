---
product: campaign
title: Struktur eines Datenschemas
description: Struktur eines Datenschemas
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 14%

---

# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Datenschemas wird in Form einer Baumstruktur dargestellt. Um es grafisch in der Adobe Campaign-Clientkonsole anzuzeigen, wählen Sie das Zielschema aus und klicken Sie auf **[!UICONTROL Struktur]** Unterregisterkarte.

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst angezeigt (aktiv, aktiviert usw.) und in alphabetischer Reihenfolge. Die strukturierenden Elemente kommen als Nächstes (Postanschrift, Ort) und schließlich als Links (E-Mail-Informationen, Ordner usw.).

Primäre Schlüssel werden durch einen roten Schlüssel identifiziert, Fremdschlüssel durch einen gelben Schlüssel.

Links werden grafisch unterschieden, je nachdem, ob sie zur Tabelle gehören. Diejenigen, die von der Tabelle ausgehend beginnen, d. h. die den Fremdschlüssel in der Tabelle haben, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Sammlungslinks &quot;Umkehren&quot;(Abonnements, Bestellungen usw.) werden am Ende angezeigt.
