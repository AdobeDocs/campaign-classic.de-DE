---
product: campaign
title: Struktur eines Datenschemas
description: Struktur eines Datenschemas
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%

---

# Struktur eines Datenschemas{#structure-of-a-data-schema}

Die Struktur eines Datenschemas wird in Form einer Baumstruktur angezeigt. Um es grafisch in der Adobe Campaign-Client-Konsole anzuzeigen, wählen Sie das Zielschema aus und klicken Sie auf die Unterregisterkarte **[!UICONTROL Struktur]**.

![](assets/d_ncs_integration_schema_arbo.png)

Standardmäßig werden die Felder zuerst (Aktiv, Aktiviert usw.) und in alphabetischer Reihenfolge angezeigt. Als Nächstes folgen die Strukturierungselemente (Postanschrift, Standort) und schließlich die Links (E-Mail-Informationen, Ordner usw.).

Primäre Schlüssel werden durch einen roten Schlüssel und Fremdschlüssel durch einen gelben Schlüssel identifiziert.

Relationen werden grafisch danach unterschieden, ob sie zur Tabelle gehören. Diejenigen, die von der Tabelle ausgehen, d. h. die den Fremdschlüssel in der Tabelle haben, werden zuerst angezeigt (E-Mail-Informationen, Ordner, Land). Sammlungslinks, die den Status „umgekehrt“ haben (Abonnement, Bestellungen usw.) werden am Ende angezeigt.
