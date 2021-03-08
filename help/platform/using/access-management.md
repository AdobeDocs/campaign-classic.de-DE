---
solution: Campaign Classic
product: campaign
title: Erste Schritte mit Berechtigungen
description: Erfahren Sie, wie Sie den Zugriff auf die Funktionen der Kampagne gewähren
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: f7e4f129a96e80ec169428057f661165d8b967c9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 60%

---


# Erste Schritte mit Berechtigungen{#access-management}

Adobe Campaign ermöglicht es, die den unterschiedlichen Benutzern zugeteilten Rechte zu bestimmen und zu verwalten. Es handelt es sich um Berechtigungen und Beschränkungen folgender Aktivitäten:

* Zugriff auf bestimmte Funktionen (über spezifische Berechtigungen);
* Zugriff auf bestimmte Datensätze;
* Erstellung, Veränderung und/oder Löschung von Datensätzen (Aktionen, Kontakte, Kampagnen, Gruppen etc.).

Die Rechte können sowohl für einzelne Benutzerprofile als auch Benutzergruppen gelten.

Sie werden durch Sicherheitsparameter ergänzt, die mit dem Verbindungsmodus des Betreibers mit dem Adobe Campaign verbunden sind. Weitere Informationen zu Sicherheitszonen in [dieser Seite](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Es gibt zwei Arten von Berechtigungen, die einem Benutzer erteilt werden können:

* Sie können Benutzergruppen bestimmen, denen Sie Berechtigungen einräumen und Benutzer zuordnen. Diese Vorgehensweise ermöglicht eine gemeinsame Nutzung der Rechte und eine Vereinheitlichung der Benutzerprofile. Zudem wird auf diese Weise die Verwaltung der Profile vereinfacht. Gruppenerstellung und -verwaltung werden in [diesem Abschnitt](access-management-groups.md) vorgestellt.

* Sie können den Benutzern direkt spezifische Berechtigungen einräumen, gegebenenfalls, um über Gruppen eingeräumte Berechtigungen zu überschreiben. Diese Rechte werden in [dieser Seite](access-management-named-rights.md) angezeigt.

>[!NOTE]
>
>Adobe empfiehlt, vor der Definition von Berechtigungen die [Checkliste zur Sicherheitskonfiguration](https://helpx.adobe.com/de/campaign/kb/acc-security.html) zu lesen.

In den folgenden Abschnitten erfahren Sie, wie Sie Zugriff gewähren und Berechtigungen einrichten:

* [Operatoren erstellen](access-management-operators.md)

* [Gruppen definieren](access-management-groups.md)

* [hinzufügen Spezifische Berechtigungen](access-management-named-rights.md)

* [Zugriff auf Kampagnen verwalten](access-management-folders.md)

* [Matrix der Zugriffsberechtigungen](access-management-named-rights.md#access-rights-matrix)


Siehe auch:

* [Berechtigungen für Workflows verwalten](../../workflow/using/managing-rights.md)
* [Berechtigungen für verteiltes Marketing verwalten](../../campaign/using/about-distributed-marketing.md#operators-and-entities)
* [Berechtigungen für das Interaktionsmodul verwalten](../../interaction/using/operator-profiles.md)
* [Filterzugriff auf Schema](../../configuration/using/filtering-schemas.md)
* [Einschränkung der PI-Ansicht](../../configuration/using/restricting-pii-view.md)
