---
title: Verwenden der Tabelle Adobe Campaign Classic Empfänger
description: Erfahren Sie, wie Sie die vordefinierte Empfängertabelle in Adobe Campaign Classic beim Entwerfen Ihres Datenmodells verwenden.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# Best Practices zum Datenmodell{#data-model-best-practices}

Im Folgenden finden Sie einige Best Practices, die beim Entwerfen Ihres Datenmodells mit großen Tabellen und komplexen Verbindungen befolgt werden sollten.

* Wenn Sie zusätzliche benutzerdefinierte Empfängertabellen verwenden, stellen Sie sicher, dass Sie für jede Zuordnungstabelle über eine dedizierte Protokolltabelle verfügen.
* Reduzieren Sie die Anzahl der Spalten, insbesondere durch Identifizieren der nicht verwendeten Spalten.
* Optimieren Sie die Datenmodellbeziehungen, indem Sie komplexe Verbindungen, wie z. B. Verbindungen mit mehreren Bedingungen und/oder Spalten, vermeiden.
* Verwenden Sie für Verbindungsschlüssel immer numerische Daten anstelle von Zeichenfolgen.
* Verringern Sie so viel wie möglich die Tiefe der Protokollbindung. Wenn Sie einen tieferen Verlauf benötigen, können Sie Berechnungen zusammenstellen und/oder benutzerspezifische Protokolltabellen bearbeiten, um einen größeren Verlauf zu speichern.

Detailliertere Best Practices zur Optimierung des Datenbankentwurfs für größere Volumes finden Sie unter Best Practices für das [Campaign Classic-Datenmodell](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).
