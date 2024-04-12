---
product: campaign
title: Profile bearbeiten
description: Profile bearbeiten
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 81%

---

# Bearbeiten von Profilen{#editing-a-profile}



Klicken Sie auf den Namen eines Profils, um seine Profilinformationen anzuzeigen.

Dies geschieht in einem neuen Fenster.

![](assets/s_user_recipient_edit.png)

In verschiedenen Tabs werden die Informationen bezüglich eines Profils nach Themen geordnet.

Tabs und ihr Inhalt sind abhängig von Ihrer Konfiguration und den installierten Packages.

>[!CAUTION]
>
>Auf das XML-Schema und das den Feldern der Profiltabelle entsprechende Formular kann über den Verzeichnisknoten **[!UICONTROL Administration > Konfiguration > Datenschemata]** zugegriffen werden. Eventuelle Änderungen dieser Schemata sollten von erfahrenen Benutzern vorgenommen werden.
>
>Weiterführende Informationen dazu finden Sie auf [dieser Seite](../../configuration/using/about-schema-edition.md).

## Tab &quot;Allgemein&quot; {#general-tab}

Dieser Bildschirm enthält alle allgemeinen Informationen zum ausgewählten Profil, insbesondere Nachnamen, Vornamen, E-Mail-Adresse, E-Mail-Empfangsformat etc.:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Wenn die Option **[!UICONTROL Nicht mehr kontaktieren (alle Kanäle)]** aktiviert ist, bedeutet dies, dass das Profil auf der Blockierungsliste steht; das Profil hat also den Wunsch geäußert, nicht kontaktiert zu werden (z. B. durch Klicken auf einen Abmelde-Link in einem Newsletter). Das Profil wird keine Sendungen mehr erhalten (auf keinem Kanal: ob E-Mail, Briefpost usw.). Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../delivery/using/understanding-quarantine-management.md).

## Tab &quot;Postanschrift&quot; {#contact-information-tab}

Dieser Bildschirm enthält die Postanschrift des ausgewählten Profils:

![](assets/s_ncs_user_profile_details_tab.png)

Hier werden zudem der Qualitätsindex sowie die Anzahl von fehlgeschlagenen Sendeversuchen in Bezug auf diese Adresse hinterlegt. Diese Informationen werden direkt vom für die Briefpost zuständigen Dienstleister eingespeist und können nicht manuell geändert werden.

## Tab &quot;Sonstige&quot; {#other-tab}

Dieser Bildschirm enthält benutzerdefinierte Felder, die je nach Bedarf personalisiert werden können. Sie können auch die Namen der Felder ändern und ihr Format festlegen, indem Sie **[!UICONTROL Feldeigenschaften...]**, wie unten dargestellt:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Auf [dieser Seite](../../configuration/using/new-field-wizard.md) finden Sie weitere Angaben zu den Feldeigenschaften und zum Hinzufügen von Feldern.

## Tab &quot;Listen&quot; {#lists-tab}

Auf diesem Bildschirm werden die Gruppen angezeigt, zu denen das ausgewählte Profil gehört. Klicks **[!UICONTROL Hinzufügen]** , um das Profil für eine Liste anzumelden. Klicks **[!UICONTROL Detail]** um die Beschreibung und die Liste der Profile in der ausgewählten Liste anzuzeigen.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Weitere Informationen finden Sie unter [Listen erstellen und verwalten](../../platform/using/creating-and-managing-lists.md).

## Tab &quot;Abonnements&quot; {#subscriptions-tab}

Dieser Bildschirm enthält die Informationsdienste, die das Profil abonniert hat.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

Die **[!UICONTROL Detail]** zeigt die Eigenschaften des ausgewählten Abonnements an. Die **[!UICONTROL Hinzufügen]** -Schaltfläche wird verwendet, um ein neues Abonnement manuell hinzuzufügen.

Weitere Informationen hierzu finden Sie auf [dieser Seite](../../delivery/using/managing-subscriptions.md).

## Tab &quot;Sendungen&quot; {#deliveries-tab}

Dieser Bildschirm enthält die Versandlogs für das ausgewählte Profil. Es werden Titel, Datum und Status aller an das Profil adressierten Sendungen für alle Kanäle angezeigt.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Tab &quot;Tracking&quot; {#tracking-tab}

Dieser Bildschirm enthält die Trackinglogs für das ausgewählte Profil. Mithilfe dieser Informationen können Sie das Verhalten des Profils nach Erhalt eines Versands verfolgen.

![](assets/s_ncs_user_profile_tracking_tab.png)

Dieser Tab zeigt alle in Sendungen getrackten URLs an.

In der Regel enthält die anpassbare Liste folgende Daten: die geklickte URL, Datum und Uhrzeit des Klicks, das Dokument, in dem die URL enthalten war.

>[!NOTE]
>
>Auf [dieser Seite](../../delivery/using/delivery-dashboard.md) finden Sie weitere Informationen zur Trackingfunktion.
