---
title: Profile bearbeiten
seo-title: Profile bearbeiten
description: Profile bearbeiten
seo-description: null
page-status-flag: never-activated
uuid: ad3cd54e-b22f-4fae-8d2a-3e0d3e45fffb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 93dd29e8-cf0a-4010-a3cc-f68c52c0d9ef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 88%

---


# Profile bearbeiten{#editing-a-profile}

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

## Tab &quot;Allgemein&quot;{#general-tab}

Dieser Bildschirm enthält alle allgemeinen Informationen zum ausgewählten Profil, insbesondere Nachname, Vorname, E-Mail-Adresse, E-Mail-Empfangsformat etc.:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>Wenn die Option &quot; **[!UICONTROL Kein Kontakt mehr&quot;(von einem Kanal)]** ausgewählt ist, bedeutet dies, dass das Profil auf der blockierungsliste liegt, d. h. das Profil hat den Wunsch geäußert, nicht kontaktiert zu werden (z. B. durch Klicken auf einen Link in einer Abmeldung in einem Newsletter). Sie werden nicht mehr von Versänden auf einem Kanal (E-Mail, Direktwerbung usw.) angegangen. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../delivery/using/understanding-quarantine-management.md).

## Tab &quot;Kontaktdaten&quot;{#contact-information-tab}

Dieser Bildschirm enthält die Postanschrift des ausgewählten Profils:

![](assets/s_ncs_user_profile_details_tab.png)

Hier werden zudem der Qualitätsindex sowie die Anzahl von fehlgeschlagenen Sendeversuchen in Bezug auf diese Adresse hinterlegt. Diese Informationen werden direkt vom für die Briefpost zuständigen Dienstleister eingespeist und können nicht manuell geändert werden.

## Tab &quot;Sonstige&quot;{#other-tab}

Dieser Bildschirm enthält frei vom Benutzer definierbare Felder. Sie haben über das Menü **[!UICONTROL Feldeigenschaften...]** die Möglichkeit, Felder umzubenennen oder das Format zu ändern, wie das folgende Beispiel zeigt:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Auf [dieser Seite](../../configuration/using/new-field-wizard.md) finden Sie weitere Angaben zu den Feldeigenschaften und zum Hinzufügen von Feldern.

## Tab &quot;Listen&quot;{#lists-tab}

Dieser Bildschirm zeigt an, welchen Gruppen der ausgewählte Empfänger angehört. Durch Klick auf die Schaltfläche **[!UICONTROL Hinzufügen]** kann das Profil zu einer Liste hinzugefügt werden. Klicken Sie auf die Schaltfläche **[!UICONTROL Details]**, um die Beschreibung der Liste und alle enthaltenen Profile anzuzeigen.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Weitere Informationen finden Sie unter [Listen erstellen und verwalten](../../platform/using/creating-and-managing-lists.md).

## Tab &quot;Abonnements&quot;{#subscriptions-tab}

Dieser Bildschirm enthält die Informationsdienste, die das Profil abonniert hat.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

Die Schaltfläche **[!UICONTROL Details]** zeigt die Eigenschaften des ausgewählten Abonnements an. Die Schaltfläche **[!UICONTROL Hinzufügen]** erlaubt die manuelle Anmeldung eines Empfängers für einen Informationsdienst.

Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../delivery/using/managing-subscriptions.md).

## Tab &quot;Sendungen&quot;{#deliveries-tab}

Dieser Bildschirm enthält die Versandlogs für das ausgewählte Profil. Es werden Titel, Datum und Status aller an das Profil adressierten Sendungen für alle Kanäle angezeigt.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Tab Tracking {#tracking-tab}

Dieser Bildschirm enthält die Trackinglogs für das ausgewählte Profil. Mithilfe dieser Informationen können Sie das Verhalten des Profils nach Erhalt eines Versands verfolgen.

![](assets/s_ncs_user_profile_tracking_tab.png)

Dieser Tab zeigt alle in Sendungen getrackten URLs an.

In der Regel enthält die anpassbare Liste folgende Daten: die geklickte URL, Datum und Uhrzeit des Klicks, das Dokument, in dem die URL enthalten war.

>[!NOTE]
>
>Auf [dieser Seite](../../delivery/using/monitoring-a-delivery.md) finden Sie weitere Informationen zur Trackingfunktion.

