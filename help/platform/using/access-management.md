---
product: campaign
title: Erste Schritte mit Berechtigungen
description: Erfahren Sie, wie Sie Zugriff auf Campaign-Funktionen gewähren.
badge: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
TQID: https://experienceleague.adobe.com/03hVUeg0dRIFz0J20RfxH4EdSmAhe9h2c9BfKB-qJUs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
  - id: efa38731-2723-4334-8d8b-a778af834835
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 315
ht-degree: 100%

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

Weitere Informationen zu **Berechtigungen in Adobe Campaign** finden Sie in der **[Dokumentation zu Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=de#_blank){target=_blank}**.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=de#_blank){target=_blank}


>[!TAB Verwalten von Ordnerberechtigungen]

Wie Sie **Ordnerberechtigungen** definieren, finden Sie in der **[Dokumentation zu Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/folder-permissions?lang=de){target=_blank}**.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/folder-permissions?lang=de){target=_blank}


>[!TAB Native Authentifizierung]

Die native Authentifizierung mit Login/Passwort ist in Campaign v7 noch verfügbar. Um die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign jedoch dringend die [Migration des Authentifizierungsmodus für Endbenutzende](../../technotes/using/ac-ims.md) von der nativen Authentifizierung auf das Adobe-Identitäts-Management-System (IMS). Hinweis: In Campaign v8 ist die Verbindung mit nativer Authentifizierung nicht zulässig.

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
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

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