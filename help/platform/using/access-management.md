---
product: campaign
title: Erste Schritte mit Berechtigungen
description: Erfahren Sie, wie Sie Zugriff auf Campaign-Funktionen gewähren.
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
TQID: 'https://experienceleague.adobe.com/03hVUeg0dRIFz0J20RfxH4EdSmAhe9h2c9BfKB-qJUs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: f529d0bd-1401-4c88-9833-43228cc1d40f
    internal-label: Profiles
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
  - id: f5293531-9312-4099-bfa3-9e67df6a8750
    internal-label: Query Editor
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
    internal-label: Permissions
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: 0fdce84d7da1ff42a406ace8f1a180f6a426646a
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 57%
---
# Erste Schritte mit Berechtigungen{#access-management}

Mit Adobe Campaign können Sie die den verschiedenen Benutzerinnen und Benutzern zugewiesenen Rechte definieren und verwalten. Diese bestehen aus einem Satz von Rechten und Einschränkungen, die Folgendes erlauben bzw. verweigern:

* Zugriff auf bestimmte Funktionen (über spezifische Berechtigungen);
* Zugriff auf bestimmte Datensätze;
* Erstellung, Veränderung und/oder Löschung von Datensätzen (Aktionen, Kontakte, Kampagnen, Gruppen etc.).

>[!NOTE]
>
>Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zu Berechtigungen und zum Definieren von Berechtigungen für Ordner finden Sie in der Dokumentation zu Campaign v8:
>
>* [Erste Schritte mit Berechtigungen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}
>* [Berechtigungen für Ordner hinzufügen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/permissions/folder-permissions){target="_blank"}
>
>[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}

## Authentifizierungsmodus {#authentication-mode}

>[!CAUTION]
>
>Ab Campaign Classic v7.3.1 sollten alle Benutzenden das [Adobe-Identitäts-Management-System (IMS)](https://helpx.adobe.com/de/enterprise/using/identity.html){target="_blank"} verwenden, um eine Verbindung mit Campaign herzustellen.
>
>Die native Authentifizierung mit Anmeldung/Kennwort ist in Campaign v7 weiterhin verfügbar. Um jedoch die Sicherheit und den Authentifizierungsprozess zu verbessern, empfiehlt Adobe Campaign dringend, alle vorhandenen Operatoren von der nativen Authentifizierung zu Adobe IMS zu migrieren. Hinweis: In Campaign v8 ist die Verbindung mit nativer Authentifizierung nicht zulässig.

* Informationen zum Migrieren Ihrer Benutzer finden Sie unter [Migrieren von Benutzern zu IMS](../../technotes/using/migrate-users-to-ims.md).
* Informationen zum Migrieren des Authentifizierungsmodus für Endbenutzer finden Sie unter [Authentifizierungsmodus für Endbenutzer migrieren](../../technotes/using/ac-ims.md).

Nach dieser Migration werden die Berechtigungen mit Adobe IMS verwaltet. Wie Sie sie einrichten, erfahren Sie in der [&#x200B; zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"}.


<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/permissions/manage-permissions){target="_blank"} (Campaign v8 documentation).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/de/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/permissions/manage-permissions){target="_blank"} (Campaign v8 documentation)

* [Manage Campaign folder access](access-management.md)

* [Access rights matrix](assets/access-rights-matrix.pdf)


See also:

* [Manage permissions for workflows](https://experienceleague.adobe.com/de/docs/campaign/automation/workflows/advanced-management/managing-rights){target="_blank"} (Campaign v8 documentation)
* [Manage permissions for distributed marketing](https://experienceleague.adobe.com/de/docs/campaign/automation/distributed-marketing/about-distributed-marketing#operators-and-entities){target="_blank"} (Campaign v8 documentation)
* [Manage permissions for the interaction module](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/offers/interaction-settings/interaction-operators){target="_blank"} (Campaign v8 documentation)
* [Filter access to schemas](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/filter-schema){target="_blank"} (Campaign v8 documentation)
* [Restricting PI view](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/schemas-forms/restrict-pi-view){target="_blank"} (Campaign v8 documentation)
-->