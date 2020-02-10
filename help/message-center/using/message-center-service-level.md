---
title: Dienstqualität
seo-title: Dienstqualität
description: Dienstqualität
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Dienstqualität{#message-center-service-level}

Dieser Bericht zeigt die Lieferstatistiken zu Transaktionsmeldungen sowie die Fehleraufschlüsselung an. Sie können auf einen Fehlertyp klicken, um dessen Details anzuzeigen. Dieser Bericht, der an technische Administratoren gerichtet ist, kann auch über das **[!UICONTROL Monitoring]** Universum in der Kontrollinstanz aufgerufen werden.

![](assets/mc_reports_1.png)

In diesem Bericht können Sie die Gesamtstatistik oder die Statistiken zu einer bestimmten Ausführungsinstanz anzeigen.Sie können die Daten auch nach Kanal und über einen bestimmten Zeitraum filtern. Die im **[!UICONTROL Indicators over the period]** Abschnitt angezeigten Indikatoren werden über den ausgewählten Zeitraum berechnet:

* **[!UICONTROL Incoming (throughput event/h)]** : durchschnittliche stündliche Anzahl der Ereignisse, die in die Warteschlange des Nachrichtenzentrums eingegeben wurden.
* **[!UICONTROL Incoming (event vol)]** : Anzahl der Ereignisse, die in die Warteschlange des Nachrichtenzentrums eingegeben wurden.
* **[!UICONTROL Outgoing (throughput msg/h)]** : durchschnittliche stündliche Anzahl erfolgreicher ausgehender Message Center-Ereignisse (gesendet durch eine Bereitstellung).
* **[!UICONTROL Outgoing (msg vol)]** : Anzahl der erfolgreichen ausgehenden Message Center-Ereignisse (gesendet durch eine Bereitstellung).
* **[!UICONTROL Average sending time (seconds)]** : durchschnittliche Besuchszeit im Message Center für erfolgreich verarbeitete Ereignisse. Bei der Berechnung werden die Verarbeitungszeit und die Sendezeit berücksichtigt.
* **[!UICONTROL Error rate]** : Anzahl der Ereignisse mit Fehlern im Vergleich zur Anzahl der Ereignisse, die in die Warteschlange des Message Center eingegeben wurden. Folgende Fehler werden berücksichtigt: Routingfehler, abgelaufenes Ereignis (Ereignis, das sich zu lange in der Warteschlange befindet), Bereitstellungsfehler, der von der Bereitstellung ignoriert wird (Quarantäne usw.).

>[!NOTE]
>
>Die Schwellenwerte für Warnung (orange) und Warnung (rot) können im Bereitstellungsassistenten konfiguriert werden. Siehe [Überwachungsschwellenwerte](../../message-center/using/monitoring-thresholds.md).

