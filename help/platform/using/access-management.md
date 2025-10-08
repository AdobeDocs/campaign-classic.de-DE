---
product: campaign
title: Erste Schritte mit Berechtigungen
description: Erfahren Sie, wie Sie Zugriff auf Campaign-Funktionen gewähren.
badge: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: 34f875f583dd81c2229b66f3344f23965532e802
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 64%

---

# Erste Schritte mit Berechtigungen{#access-management}


>[!CAUTION]
>
>Ab Campaign Classic v7.3.1 sollten alle Benutzenden das [Adobe-Identitäts-Management-System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} verwenden, um eine Verbindung mit Campaign herzustellen.
>
>Im Rahmen der Bemühungen, die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, den Authentifizierungsmodus aller vorhandenen Benutzenden von der nativen Authentifizierung mit Login/Passwort auf das Adobe Identity Management System (IMS) zu migrieren. Auf [dieser Seite](../../technotes/using/migrate-users-to-ims.md) erfahren Sie, wie Sie Ihre Benutzenden migrieren können.
> 
>Beachten Sie, dass nach dieser Migration der folgende Abschnitt nicht mehr gilt.  In der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=de){target="_blank"} erfahren Sie, wie Sie mit Adobe IMS Berechtigungen einrichten können.


Mit Adobe Campaign können Sie die den verschiedenen Benutzerinnen und Benutzern zugewiesenen Rechte definieren und verwalten. Diese bestehen aus einem Satz von Rechten und Einschränkungen, die Folgendes erlauben bzw. verweigern:

* Zugriff auf bestimmte Funktionen (über spezifische Berechtigungen);
* Zugriff auf bestimmte Datensätze;
* Erstellung, Veränderung und/oder Löschung von Datensätzen (Aktionen, Kontakte, Kampagnen, Gruppen etc.).

>[!BEGINTABS]

>[!TAB Dokumentation zu Berechtigungen]

Weitere Informationen zu **Berechtigungen in Adobe Campaign** finden Sie in der Dokumentation zu **[Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=de#_blank){target=_blank}**.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=de#_blank){target=_blank}


>[!TAB Berechtigungen für Ordner verwalten]

Informationen zum Definieren von **Berechtigungen für Ordner** finden Sie in der Dokumentation **[Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}**.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}


>[!TAB Native Authentifizierung]

Die native Authentifizierung mit Anmeldung/Kennwort ist in Campaign v7 weiterhin verfügbar. Um jedoch den Sicherheits- und Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, [den Endbenutzer-Authentifizierungsmodus) &#x200B;](../../technotes/using/ac-ims.md) der nativen Anmelde-/Kennwortauthentifizierung zum Adobe Identity Management System (IMS) zu migrieren. Beachten Sie, dass in Campaign v8 eine Verbindung mit Benutzer/Kennwort (auch als native Authentifizierung bezeichnet) nicht zulässig ist.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](../../technotes/using/ac-ims.md)


>[!ENDTABS]



<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/de/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->