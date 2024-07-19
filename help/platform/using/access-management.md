---
product: campaign
title: Erste Schritte mit Berechtigungen
description: Erfahren Sie, wie Sie Zugriff auf Campaign-Funktionen gewähren.
badge: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: e1a085384fb27ec165c487c112fbc70fe9738d9e
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 100%

---

# Erste Schritte mit Berechtigungen{#access-management}


>[!CAUTION]
>
>Ab Campaign Classic v7.3.1 sollten alle Benutzenden das [Adobe Identity Management System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} verwenden, um eine Verbindung mit Campaign herzustellen.
>
>Im Rahmen der Bemühungen, die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, den Authentifizierungsmodus aller vorhandenen Benutzenden von der nativen Authentifizierung mit Login/Passwort auf das Adobe Identity Management System (IMS) zu migrieren. Auf [dieser Seite](../../technotes/using/migrate-users-to-ims.md) erfahren Sie, wie Sie Ihre Benutzenden migrieren können.
> 
>Beachten Sie, dass nach dieser Migration der folgende Abschnitt nicht mehr gilt.  In der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=de){target="_blank"} erfahren Sie, wie Sie mit Adobe IMS Berechtigungen einrichten können.


Mit Adobe Campaign können Sie die den verschiedenen Benutzerinnen und Benutzern zugewiesenen Rechte definieren und verwalten. Diese bestehen aus einem Satz von Rechten und Einschränkungen, die Folgendes erlauben bzw. verweigern:

* Zugriff auf bestimmte Funktionen (über spezifische Berechtigungen);
* Zugriff auf bestimmte Datensätze;
* Erstellung, Veränderung und/oder Löschung von Datensätzen (Aktionen, Kontakte, Kampagnen, Gruppen etc.).

Die Rechte können sowohl für einzelne Benutzerprofile als auch Benutzergruppen gelten.

Sie werden durch Sicherheitsparameter ergänzt, die mit dem vom Benutzer zur Verbindung mit Adobe Campaign verwendeten Modus verknüpft sind. Weitere Informationen zu Sicherheitszonen finden Sie auf [dieser Seite](../../installation/using/security-zones.md).

Es gibt zwei Arten von Berechtigungen, die einer Benutzerin oder einem Benutzer erteilt werden können:

* Sie können Benutzergruppen bestimmen, denen Sie Berechtigungen einräumen, und dann die Benutzerinnen und Benutzer einer oder mehreren Gruppen zuweisen. Diese Vorgehensweise ermöglicht die Wiederverwendung von Rechten und eine Vereinheitlichung der Benutzerprofile. Außerdem wird dadurch die Verwaltung und Pflege von Profilen erleichtert. Die Erstellung und Verwaltung von Gruppen wird in [diesem Abschnitt](access-management-groups.md) näher beschrieben.

* Sie können den Benutzern direkt spezifische Berechtigungen einräumen, gegebenenfalls, um über Gruppen eingeräumte Berechtigungen zu überschreiben. Diese Rechte werden auf [dieser Seite](access-management-named-rights.md) näher beschrieben.

>[!NOTE]
>
>Adobe empfiehlt, vor der Definition von Berechtigungen die [Checkliste zur Sicherheitskonfiguration](https://helpx.adobe.com/de/campaign/kb/acc-security.html) zu lesen.

In den folgenden Abschnitten erfahren Sie, wie Sie Zugriff gewähren und Berechtigungen einrichten:

* [Benutzer erstellen](access-management-operators.md)

* [Gruppen definieren](access-management-groups.md)

* [Spezifische Berechtigungen hinzufügen](access-management-named-rights.md)

* [Zugriff auf Campaign-Ordner verwalten](access-management-folders.md)

* [Matrix der Zugriffsberechtigungen](access-management-named-rights.md#access-rights-matrix)


Siehe auch:

* [Berechtigungen für Workflows verwalten](../../workflow/using/managing-rights.md)
* [Berechtigungen für verteiltes Marketing verwalten](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Berechtigungen für das Interaktionsmodul verwalten](../../interaction/using/operator-profiles.md)
* [Filterzugriff auf Schemata](../../configuration/using/filtering-schemas.md)
* [Einschränkung der PI-Ansicht](../../configuration/using/restricting-pii-view.md)
