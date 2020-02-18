---
title: Zugriff auf externe Datenbanken
seo-title: Zugriff auf externe Datenbanken
description: Zugriff auf externe Datenbanken
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a0698ad55afb391bdc652a00b43b20df6fb9851b

---


# Über Federated Data Access - FDA {#about-federated-data-access}

Adobe Campaign bietet die Option **Federated Data Access** (FDA), um in externen Datenbanken gespeicherte Informationen nutzen zu können. Auf diese Weise ist der Zugriff auf externe Daten möglich, ohne die Datenstruktur in Adobe Campaign zu verändern.

>[!CAUTION]
>
>Der Zugriff auf eine externe Datenbank über FDA ist nur für lokale oder hybride Installationen möglich, mit Ausnahme der Snowflake Connectors. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Grundprinzip {#operating-principle}

Mit der FDA-Option können Sie Ihr Datenmodell in einer Datenbank eines Drittanbieters erweitern. Es erkennt automatisch die Struktur der zielgerichteten Tabellen und verwendet Daten aus den SQL-Quellen.


Um diese Funktion zu verwenden, gehen Sie folgendermaßen vor:

1. Sie benötigen eine externe Datenbank, die mit dem FDA-Modul von Adobe Campaign kompatibel ist. Die Liste mit Datenbanksystemen und kompatiblen Versionen finden Sie in der [Kompatibilitätsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). Benutzer benötigen zudem die [entsprechenden Berechtigungen](#remote-database-access-rights) für Adobe Campaign und die externe Datenbank.
1. [Installieren Sie die entsprechenden Treiber](#specific-configurations-by-database-type) für Ihre Datenbank auf dem Adobe-Campaign-Server.
1. [Erstellen und konfigurieren Sie ein externes Konto](#connecting-to-the-database), über das Sie die Verbindung zwischen Adobe Campaign und der externen Datenbank herstellen können. Weitere Informationen zu verfügbaren externen Konten finden Sie auf dieser [Seite](../../platform/using/external-accounts.md).
1. [Erstellen Sie das Schema](#creating-the-data-schema) der externen Datenbank in Adobe Campaign. Dadurch können Sie die Datenstruktur der externen Datenbank erkennen.
1. [Erstellen Sie abschließend ein neues Zielgruppen-Mapping](#defining-data-mapping) aus dem zuvor erstellten Schema, wenn die Empfänger Ihrer Sendungen aus der externen Datenbank stammen. Dies bringt gewisse Einschränkungen mit sich, vor allem in Bezug auf die Personalisierung der Sendungen.

Nachdem das Datenschema erstellt wurde, können Daten in Adobe Campaign-Workflows verarbeitet werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../workflow/using/executing-a-workflow.md#architecture).

## Best Practices und Empfehlungen {#best-practices-and-recommendations}

Die FDA-Option ist so konzipiert, dass Daten in externen Datenbanken mithilfe von Workflows im Batch-Modus bearbeitet werden können. Die Verwendung von FDA für andere Zwecke, z. B. für Einzeloperationen, erfordert besondere Vorsicht (Personalisierung, Interaction, Echtzeit-Sendungen etc.).

Vermeiden Sie möglichst Vorgänge, bei denen sowohl Adobe Campaign als auch die externe Datenbank zum Einsatz kommen. Gehen Sie dazu folgendermaßen vor:

* Exportieren Sie die Adobe-Campaign-Datenbank in die externe Datenbank und führen Sie die Aktionen nur in der externen Datenbank aus. Importieren Sie danach die Ergebnisse wieder in Adobe Campaign.
* Rufen Sie die Daten aus der externen Adobe-Campaign-Datenbank ab und führen Sie die Aktionen lokal durch.

Wenn Sie Ihre Sendungen unter Verwendung von Daten aus der externen Datenbank personalisieren möchten, rufen Sie die entsprechenden Daten über einen Workflow ab und stellen Sie sie in einer temporären Tabelle bereit. Personalisieren Sie dann Ihren Versand mit den Daten aus der temporären Tabelle.

## Einschränkungen {#limitations}

Die FDA-Option unterliegt den Einschränkungen des von Ihnen verwendeten externen Datenbanksystems.

Um die Leistung nicht zu beeinträchtigen, empfehlen wir, diese Funktionalität nicht zur Durchführung von Einzeloperationen zu verwenden (Versandpersonalisierung, Interaction-Modul, Echtzeit).
