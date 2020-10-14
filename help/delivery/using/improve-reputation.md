---
title: Ihre Reputation bei der Verwendung von Adobe Campaign Classic verbessern
description: Erfahren Sie mehr über die Verbesserung Ihrer Reputation bei der Verwendung von Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 96%

---


# Verbessern Ihrer Reputation{#improve-reputation}

Um zu vermeiden, dass sich Ihre Empfänger belästigt fühlen, löschen Sie doppelte E-Mail-Adressen aus Ihrer Zielgruppe. Dies sichert Ihre Reputation als Absender und ermöglicht eine ordnungsgemäße Quarantäneverwaltung. Adobe Campaign Angebot die erforderlichen Instrumente zur Umsetzung dieser Empfehlungen und zur Vermeidung der Gefahr der Hinzufügung von Empfehlungen durch den ISP.

Gehen Sie folgendermaßen vor, um Duplikate zu vermeiden:

* Achten Sie auf die korrekte Konfiguration von Importen.
* Gehen Sie bei der Änderung von E-Mail-Adressen sorgfältig vor
* Gehen Sie bei automatischen Importen sorgfältig vor
* Sortieren Sie die Profile und speichern Sie sie in unterschiedlichen Ordnern

Die Quarantäneverwaltung wird in diesem [Abschnitt](../../delivery/using/understanding-quarantine-management.md) beschrieben.

Unten finden Sie Details zur Duplikaten- und Quarantäneverwaltung.

Sie können die Menge des E-Mail-Versands gemäß der IP-Adresse überwachen. Dazu ist eine Schemaerweiterung erforderlich. Erweitern Sie die BroadLog-Tabelle um die &quot;Öffentliche Kennung&quot; und erstellen Sie einen Workflow, um die Daten zu extrahieren und anzuzeigen. Kontaktieren Sie dazu Adobe.

## Duplikate {#duplicates}

Das Vorhandensein doppelter E-Mail-Adressen kann unterschiedliche Konsequenzen haben:

* Dieselbe Nachricht wird mehrfach gesendet. Selbst wenn Campaign vor dem Versand standardmäßig eine Deduplizierung vornimmt, kann die Nachricht durch unterschiedliche Aktionen dennoch mit demselben Inhalt gesendet werden, beispielsweise bei Verwendung einer Aufspaltung der Zielpopulation.
* Abmeldungen werden missachtet. Wenn sich ein Empfänger nach dem Erhalt einer Nachricht abmeldet, können an sein dupliziertes Profil weiterhin Nachrichten gesendet werden.

Von der Umgehung des Anmeldeverfahrens abgesehen, führt dies wahrscheinlich dazu, dass Benutzer diese Nachrichten als Spam betrachten und der ISP die Adresse auf die Blockierungsliste setzt.

Bei der Bearbeitung der Datenbank muss besonders vorsichtig vorgegangen werden:

* Importe müssen sorgfältig konfiguriert werden, insbesondere bei der Auswahl des Abstimmschlüssels.
* Die Änderung von E-Mail-Adressen kann ebenfalls eine Ursache für Duplikate sein. So können zwei Adressen mit unterschiedlichen Domains zum selben Postfach gesendet werden, beispielsweise wenn ein Unternehmen seinen Namen geändert hat, aber für eine gewisse Zeit seine frühere Domain behält: max.mustermann@amce-co.com und max.mustermann@acme-rebranded.com.
* Automatische Importe, ob von Listen oder anderen Datenbanken, müssen bei der Profilverwaltung ebenfalls berücksichtigt werden. Wenn Sie ein Profil löschen oder in eine andere Partition verschieben, könnte es beispielsweise in der ursprünglichen Partition durch einen automatischen Import während einer Bestellung erneut erstellt werden.
* Speichern Sie Profile in unterschiedlichen Ordnern, indem Sie Ansichten anstelle von Partitionen verwenden. Auf diese Weise stellen Sie sicher, dass sich die Profile in derselben physischen Partition befinden und die entsprechenden Berechtigungen angezeigt und verwaltet werden können.

In gewissen Fällen sind Duplikate in unterschiedlichen Partitionen jedoch normal. Bei Sendungen an Drittparteien oder unterschiedliche Abteilungen in einem Unternehmen kann es beispielsweise vorkommen, dass dieselbe Person mehrfache Sendungen mit unterschiedlichem Zweck empfängt. Duplikate innerhalb derselben Partition treten jedoch nur sehr selten auf.

## Quarantänen {#quarantines}

Adobe Campaign verwaltet eine Liste von unter Quarantäne gestellten Adressen. Empfänger, deren Adressen unter Quarantäne gestellt wurden, werden bei der Versandanalyse standardmäßig ausgeschlossen: Sie gehören nicht zur Zielgruppe. Eine E-Mail-Adresse kann zum Beispiel unter Quarantäne gestellt werden, weil das Postfach voll ist oder die Adresse nicht existiert. Nachfolgend werden die Regeln, die eine Quarantäne auslösen, näher erläutert.

Die Quarantäneverwaltung wird in diesem [Abschnitt](../../delivery/using/understanding-quarantine-management.md) beschrieben.