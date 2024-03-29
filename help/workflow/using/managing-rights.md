---
product: campaign
title: Verwalten von Workflow-Berechtigungen
description: Erfahren Sie, wie Sie Workflow-Berechtigungen verwalten.
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 76%

---

# Verwalten von Workflow-Berechtigungen{#managing-rights}



Adobe-Campaign-Benutzer, die nicht über Administratorrechte verfügen, müssen die entsprechenden Rechte eingeräumt werden, um Workflows erstellen, ausführen und ändern zu können.

Benutzer, die mit Workflows arbeiten, müssen Zugriff haben auf die Ordner und Unterordner, die die in den verschiedenen Aktivitäten verwendeten Daten enthalten (Empfänger, Empfängerlisten, Abonnements, Sendungen etc.).

Des Weiteren müssen Sie über die spezifischen Berechtigungen verfügen, die den von den Workflows ausgeführten Aktionen entsprechen (Import von Empfängern, Zugriff auf Dateien, Fusion, Ausführung von SQL-Scripts etc.).

Die Verwaltung der Benutzer sowie ihrer Rechte wird in diesem [Abschnitt](../../platform/using/access-management.md) erläutert.

## Benutzergruppen {#operator-groups-wf}

Folgende Benutzergruppen sind im Zusammenhang mit Workflows von Bedeutung:

* Die Gruppe **[!UICONTROL Workflow-Ausführung]** ermöglicht es, die Ausführung und Genehmigung von Zielgruppen-Workflows zu steuern. Die spezifische Berechtigung WORKFLOW wird den Benutzenden dieser Gruppe zugeordnet. Sie ist für alle Aktionen in Workflows erforderlich, zusätzlich zu den Zugriffsrechten auf die Datendateien. Standardmäßig hat die Gruppe **[!UICONTROL Workflow-Ausführung]** schreibgeschützten Zugriff auf standardmäßige Zielgruppen-Workflow-Dateien und Workflow-Vorlagen. Benutzende in dieser Gruppe haben auch Lese- und Schreibzugriff auf die Datei der ausstehenden Validierungen.
* Die Gruppe **[!UICONTROL Workflow-Verantwortliche]** ermöglicht den Benutzern die Verwaltung der Workflow-Validierungen.
* Die Benutzer der Gruppe **[!UICONTROL Kampagnenverantwortliche Benutzer]** haben Zugriff auf Kampagnen-Workflows.

## Spezifische Berechtigungen {#named-rights}

Nur die spezifische Berechtigung WORKFLOW bezieht sich auf Workflows: Sie ermöglicht die Erstellung, den Start und das Anhalten von Workflows. Leserechte für die Workflow-Datei sind erforderlich, damit die spezifische Berechtigung angewendet werden kann. Bei Zielgruppen-Workflows die Leseberechtigung auf der **[!UICONTROL Profile und Zielgruppen]** -Datei erforderlich ist.

## Workflow-Ausführungskonto {#workflow-execution-account}

Das Ausführungskonto eines Workflows wird auf Niveau der Vorlage definiert. Das Ausführungskonto ermöglicht die direkte Zuordnung der Rechte zum Workflow, unabhängig vom Adobe-Campaign-Benutzer, der die Ausführung startet. Standardmäßig wird jeder Workflow mit den Rechten des Benutzers ausgeführt, der ihn gestartet hat.

Gehen Sie zur Zuordnung eines Ausführungskontos zu einem Workflow in die Liste der Workflow-Vorlagen und klicken Sie mit der rechten Maustaste auf die dem Workflow entsprechende Vorlage. Auswählen **[!UICONTROL Aktion > Ausführungskonto ändern...]** und wählen Sie das zu verwendende Konto aus.
