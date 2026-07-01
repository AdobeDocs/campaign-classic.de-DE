---
product: campaign
title: Verwalten von Workflow-Berechtigungen
description: Erfahren Sie, wie Sie Workflow-Berechtigungen verwalten.
feature: Workflows
hide: true
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
TQID: https://experienceleague.adobe.com/4H9-yPJl4lST0JYw5wPYYCPn8eZU2eV96dFa7ZUzcgk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 339
ht-degree: 100%

---

# Verwalten von Workflow-Berechtigungen{#managing-rights}



Adobe Campaign-Benutzer, die nicht über Administratorrechte verfügen, müssen die entsprechenden Rechte eingeräumt werden, um Workflows erstellen, ausführen und ändern zu können.

Benutzer, die mit Workflows arbeiten, müssen Zugriff haben auf die Ordner und Unterordner, die die in den verschiedenen Aktivitäten verwendeten Daten enthalten (Empfänger, Empfängerlisten, Abonnements, Sendungen etc.).

Des Weiteren müssen Sie über die spezifischen Berechtigungen verfügen, die den von den Workflows ausgeführten Aktionen entsprechen (Import von Empfängern, Zugriff auf Dateien, Fusion, Ausführung von SQL-Scripts etc.).

Die Verwaltung der Benutzer sowie ihrer Rechte wird in diesem [Abschnitt](../../platform/using/access-management.md) erläutert.

## Benutzergruppen {#operator-groups-wf}

Folgende Benutzergruppen sind im Zusammenhang mit Workflows von Bedeutung:

* Die Gruppe **[!UICONTROL Workflow-Ausführung]** ermöglicht es, die Ausführung und Validierung von Zielgruppenbestimmungs-Workflows zu steuern. Die Berechtigung WORKFLOW wird den Benutzenden dieser Gruppe zugeordnet. Sie ist für alle Aktionen in Workflows erforderlich, zusätzlich zu den Zugriffsrechten auf die Datendateien. Standardmäßig hat die Gruppe **[!UICONTROL Workflow-Ausführung]** schreibgeschützten Zugriff auf standardmäßige Zielgruppen-Workflow-Dateien und Workflow-Vorlagen. Benutzende in dieser Gruppe haben auch Lese- und Schreibzugriff auf die Datei der ausstehenden Validierungen.
* Die Gruppe **[!UICONTROL Workflow-Verantwortliche]** ermöglicht den Benutzern die Verwaltung der Workflow-Validierungen.
* Die Benutzer der Gruppe **[!UICONTROL Kampagnenverantwortliche Benutzer]** haben Zugriff auf Kampagnen-Workflows.

## Spezifische Berechtigungen {#named-rights}

Nur die spezifische Berechtigung WORKFLOW gilt speziell für Workflows: Damit können Sie Workflows erstellen, starten und stoppen. Leserechte für die Workflow-Datei sind erforderlich, damit die spezifische Berechtigung angewendet werden kann. Für Zielgruppen-Workflows ist außerdem der Lesezugriff auf den Ordner **[!UICONTROL Profile und Zielgruppen]** erforderlich.

## Workflow-Ausführungskonto {#workflow-execution-account}

Sie können das Ausführungskonto konfigurieren, das auf Workflow-Vorlagenebene verwendet werden soll. Das Ausführungskonto ermöglicht die direkte Zuordnung der Berechtigungen zum Workflow, unabhängig von den Adobe Campaign-Benutzenden, die die Ausführung starten. Standardmäßig werden alle Workflows mit den Berechtigungen der benutzenden Person ausgeführt, der sie gestartet hat.

Gehen Sie zur Zuordnung eines Ausführungskontos zu einem Workflow in die Liste der Workflow-Vorlagen und klicken Sie mit der rechten Maustaste auf die dem Workflow entsprechende Vorlage. Verwenden Sie die Option **[!UICONTROL Aktionen > Ausführungskonto ändern...]** und wählen Sie das zu verwendende Konto aus.
