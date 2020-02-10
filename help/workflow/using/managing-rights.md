---
title: Rechte
seo-title: Rechte
description: Rechte
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Rechte{#managing-rights}

Adobe-Campaign-Benutzer, die nicht über Administratorrechte verfügen, müssen die entsprechenden Rechte eingeräumt werden, um Workflows erstellen, ausführen und ändern zu können.

Benutzer, die mit Workflows arbeiten, müssen Zugriff haben auf die Ordner und Unterordner, die die in den verschiedenen Aktivitäten verwendeten Daten enthalten (Empfänger, Empfängerlisten, Abonnements, Sendungen etc.).

Des Weiteren müssen Sie über die spezifischen Berechtigungen verfügen, die den von den Workflows ausgeführten Aktionen entsprechen (Import von Empfängern, Zugriff auf Dateien, Fusion, Ausführung von SQL-Scripts etc.).

Die Verwaltung der Benutzer sowie ihrer Rechte wird in diesem [Abschnitt](../../platform/using/access-management.md) erläutert.

## Benutzergruppen {#operator-groups}

Folgende Benutzergruppen sind im Zusammenhang mit Workflows von Bedeutung:

* Mit der **[!UICONTROL Workflow execution]** Gruppe können Sie die Ausführung und Genehmigung von Targeting-Workflows steuern: der WORKFLOW mit dem Namen right wird den Operatoren dieser Gruppe zugeordnet. Es ist für alle Aktionen in Workflows erforderlich, zusätzlich zu den Zugriffsrechten auf die Datendateien. Standardmäßig hat die **[!UICONTROL Workflow execution]** Gruppe schreibgeschützten Zugriff auf Standard-Targeting-Workflow-Dateien und Workflow-Vorlagen. Operatoren dieser Gruppe haben auch Lese- und Schreibzugriff auf die ausstehende Genehmigungsdatei.
* The **[!UICONTROL Workflow supervisors]** group lets operators manage workflow approvals.
* Die **[!UICONTROL Operation Managers]** Gruppe, die auf Kampagnen-Workflows zugreifen soll.

## Spezifische Berechtigungen {#named-rights}

Nur der rechts benannte WORKFLOW ist spezifisch für Workflows: Damit können Sie Workflows erstellen, starten und beenden. Die Leserechte in der Workflow-Datei sind erforderlich, damit das benannte Recht angewendet werden kann. Für Targeting-Arbeitsabläufe ist das Lesen direkt in der **[!UICONTROL Profiles and Targets]** Datei erforderlich.

## Workflow-Ausführungskonto {#workflow-execution-account}

Das Ausführungskonto eines Workflows wird auf Niveau der Vorlage definiert. Das Ausführungskonto ermöglicht die direkte Zuordnung der Rechte zum Workflow, unabhängig vom Adobe-Campaign-Benutzer, der die Ausführung startet. Standardmäßig wird jeder Workflow mit den Rechten des Benutzers ausgeführt, der ihn gestartet hat.

Um einem Workflow ein Ausführungskonto zuzuordnen, navigieren Sie zur Liste der Workflow-Vorlagen und klicken Sie mit der rechten Maustaste auf die mit dem Workflow verknüpfte Vorlage. Wählen Sie **[!UICONTROL Action > Change execution account...]** dann das zu verwendende Konto aus.
