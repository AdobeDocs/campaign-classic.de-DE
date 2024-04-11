---
product: campaign
title: Verwalten von Abonnements
description: Erfahren Sie mehr über das Verwalten von Abonnements in Adobe Campaign.
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Subscriptions
role: User
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 63%

---

# Verwalten von Abonnements{#managing-subscriptions}

## Über Informations-Services {#about-information-services}

Ein Informationsdienst zeichnet sich durch folgende Merkmale aus:

* erfordert eine Anmeldung oder ein Abonnement (Opt-in);
* bietet die Möglichkeit einer gewollten (Opt-out) oder automatischen Abmeldung (begrenzter Service, z. B. bei einem Testangebot);
* verfügt über Mechanismen zur Bestätigung von An- und/oder Abmeldung (einfache Bestätigung, Double-Opt-in usw.);
* protokolliert die Handlungen der angemeldeten Nutzer.

Diese Dienste bieten standardmäßig spezifische Berichte und Statistiken: Verfolgung der angemeldeten Nutzer, Treuegrad, Abmeldekurven usw.

In E-Mail-Sendungen werden die erforderlichen Abmelde-Links automatisch erzeugt. Der gesamte Opt-in- bzw. Opt-out-Prozess läuft vollautomatisch ab und wird dokumentiert, um im Einklang mit der herrschenden Rechtsprechung zu stehen.

Drei verschiedene Anmelde- bzw. Abmeldemodi stehen zur Auswahl:

1. manuell,
1. durch Import (nur Anmeldung),
1. über ein Webformular.

>[!NOTE]
>
>Ein Muster zum Erstellen eines Anmeldeformulars mit zweifacher Bestätigung finden Sie in [diesem Abschnitt](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

## Informations-Services erstellen {#creating-an-information-service}

Sie haben die Möglichkeit, Abonnements für Informations-Services zu erstellen und zu verwalten und ihnen Bestätigungsnachrichten oder andere automatische Mitteilungen zuzuordnen.

Der Tab **[!UICONTROL Profile und Zielgruppen]** bietet unter dem Link **[!UICONTROL Dienste und Abonnements]** eine Übersicht über alle existierenden Informationsdienste.

![](assets/s_ncs_user_services_new.png)

Um einen vorhandenen Dienst zu bearbeiten, klicken Sie auf seinen Namen. Um einen Dienst zu erstellen, klicken Sie auf die **[!UICONTROL Erstellen]** oberhalb der Liste.

![](assets/s_ncs_user_services_add.png)

* Geben Sie im Feld **[!UICONTROL Titel]** einen Namen für den neuen Dienst ein und wählen Sie den Versandkanal aus: E-Mail, Mobile, Facebook, X (früher bekannt als Twitter) oder Mobile App.

  >[!NOTE]
  >
  >Facebook- und X-Abonnements werden in [diesem Abschnitt](../../social/using/about-social-marketing.md) ausführlich beschrieben. Mobile App-Abonnements werden im Abschnitt [Über den Mobile-App-Kanal](about-mobile-app-channel.md) beschrieben.

* Wählen Sie für einen Dienst vom Typ E-Mail die **Versandmodus**. Die möglichen Modi sind: **[!UICONTROL Newsletter]** oder **[!UICONTROL Viral]**.
* Sie können **Bestätigungsnachrichten** für eine An- oder Abmeldung. Wählen Sie dazu die Versandvorlagen aus, die zur Erstellung der entsprechenden Sendungen verwendet werden sollen. **[!UICONTROL Abonnement]** und **[!UICONTROL Abmeldung]** -Felder. Diese Vorlagen müssen mit einer **[!UICONTROL Abonnement]** Geben Sie Zielgruppen-Mapping ohne definierte Zielgruppe ein. Siehe Abschnitt [Über den E-Mail-Kanal](about-email-channel.md).
* Standardmäßig sind Abonnements unbegrenzt. Sie können die Auswahl der **[!UICONTROL Unbegrenzt]** -Option, um eine Gültigkeitsdauer für den Dienst festzulegen. Die Dauer kann in Tagen (**[!UICONTROL d]** ) oder Monate (**[!UICONTROL m]** ).

Nachdem der Dienst gespeichert wurde, wird er der Liste Dienste und Abonnements hinzugefügt: Klicken Sie auf seinen Namen, um ihn zu bearbeiten. Es stehen mehrere Registerkarten zur Verfügung. Die **[!UICONTROL Abonnements]** bietet die Möglichkeit, die Liste der Abonnenten des Informationsdienstes (**[!UICONTROL Aktive Abonnements]** oder den Verlauf der An-/Abmeldung (**[!UICONTROL Geschichte]** Registerkarte). An dieser Stelle können Sie auch Abonnenten hinzufügen und löschen. Siehe [Abonnenten hinzufügen und löschen](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Die Schaltfläche **[!UICONTROL Details...]** bietet die Möglichkeit, die Eigenschaften des Abonnements für den markierten Empfänger anzuzeigen und zu ändern.

Sie können die Eigenschaften des Abonnements für einen Empfänger ändern.

![](assets/s_ncs_user_services_modify.png)

Klicken Sie zur Verfolgung der Abonnements (Anmeldungen, Abonnentenanzahl usw.) im Dashboard auf den Tab **[!UICONTROL Berichte]**. Hier können Sie außerdem Berichte archivieren und auf Verläufe zugreifen.

## Abonnenten hinzufügen und löschen {#adding-and-deleting-subscribers}

Aus dem **[!UICONTROL Abonnements]** Registerkarte eines Informationsdienst-Klicks **[!UICONTROL Hinzufügen]** , um Abonnenten hinzuzufügen. Sie können auch mit der rechten Maustaste auf die Abonnentenliste klicken und **[!UICONTROL Hinzufügen]**. Wählen Sie den Ordner aus, in dem die abonnierten Profile gespeichert werden sollen, wählen Sie die Profile aus, die abonniert werden sollen, und klicken Sie auf **[!UICONTROL OK]** validieren.

Um Abonnenten zu löschen, wählen Sie sie aus und klicken Sie auf **[!UICONTROL Löschen]**. Sie können auch mit der rechten Maustaste auf die Teilnehmerliste klicken und **[!UICONTROL Löschen]**.

In beiden Fällen können Sie eine Bestätigungsnachricht an die betreffenden Benutzer senden, wenn eine Versandvorlage für Abmeldungen mit dem Dienst verknüpft wurde (siehe [Informationsdienste erstellen](#creating-an-information-service)). Mit einem Warnhinweis können Sie diesen Versand validieren oder nicht validieren:

![](assets/s_ncs_user_services_update.png)

Siehe [An- und Abmeldungen](#subscription-and-unsubscription-mechanisms).

## An Abonnenten eines Service versenden {#delivering-to-the-subscribers-of-a-service}

Um einen Versand an alle Abonnenten eines bestimmten Informationsdienstes zu erstellen, muss die Zielgruppe wie nachfolgend beschrieben definiert werden:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>Das Zielgruppen-Mapping muss **[!UICONTROL Abonnements]** sein.

Wählen Sie **[!UICONTROL Abonnenten eines Informationsdienstes]** und klicken Sie auf **[!UICONTROL Weiter]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Markieren Sie nun den gewünschten Dienst und klicken Sie auf **[!UICONTROL Beenden]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

Im **[!UICONTROL Vorschau]**-Tab können Sie die Liste der Abonnenten des entsprechenden Informationsdienstes ansehen.

## An- und Abmeldungen {#subscription-and-unsubscription-mechanisms}

Sie haben die Möglichkeit, An- und Abmeldevorgänge sowie die Abonnentenverwaltung zu automatisieren.

>[!NOTE]
>
>Sie können neuen Abonnenten und jenen, die sich abmelden, eine Bestätigungsnachricht senden.\
>Der Inhalt dieser Nachricht wird im Informationsdienst im Abschnitt Bestätigungsnachrichten im Feld **[!UICONTROL Anmeldung]** bzw. **[!UICONTROL Abmeldung]** konfiguriert.
>
>Die Bestätigungsnachrichten werden in den in diesen Feldern angegebenen Versandvorlagen erstellt. Diese Zielgruppen-Mappings müssen **[!UICONTROL Abonnements]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Empfänger für Informations-Services anmelden {#subscribing-a-recipient-to-a-service}

Sie haben verschiedene Möglichkeiten, um einen Empfänger für einen Dienst anzumelden:

* Dienst manuell hinzufügen. Klicken Sie im Tab **[!UICONTROL Abonnements]** des Empfängerprofils auf **[!UICONTROL Hinzufügen]** und wählen Sie den gewünschten Dienst aus.

  Lesen Sie diesbezüglich auch über die Bearbeitung von Empfängerprofilen in [diesem Abschnitt](../../platform/using/editing-a-profile.md).

* automatisch eine Gruppe von Empfängern für diesen Dienst anmelden. Die Empfängerliste kann aus einem Filtervorgang, einer Gruppe, einem Ordner, einem Import oder einer direkten Auswahl mit der Maus stammen. Um diese Empfänger anzumelden, wählen Sie die Profile aus und klicken Sie mit der rechten Maustaste darauf. Auswählen **[!UICONTROL Aktionen > Auswahl für einen Dienst anmelden...]**, wählen Sie den betreffenden Dienst aus und starten Sie den Vorgang.
* Empfänger im Zuge eines Imports für einen Dienst anmelden. Geben Sie im letzten Schritt des Import-Assistenten den gewünschten Dienst an.

  Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/executing-import-jobs.md).

* Empfänger melden sich persönlich über ein Webformular an.

  Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../web/using/about-web-applications.md).

* Empfänger unter Verwendung eines Workflows mit der Aktivität **[!UICONTROL Abonnements]** anmelden.

  ![](assets/s_ncs_user_subscribe_from_wf.png)

  Workflows und ihre Verwendung in Formularen werden in [diesem Abschnitt](../../workflow/using/about-workflows.md) beschrieben.

### Empfänger von einem Service abmelden {#unsubscribing-a-recipient-from-a-service}

#### Manuelle Abmeldung {#manual-unsubscribing}

Für kommerzielle E-Mail-Sendungen ist das Einfügen eines Abmelde-Links gesetzlich vorgeschrieben. Empfänger, die nicht mehr kontaktiert werden möchten, können auf den entsprechenden Link klicken und werden so zukünftig aus den Versandzielgruppen ausgeschlossen.

Der standardmäßige Abmelde-Link wird über die letzte Schaltfläche in der Symbolleiste des Inhaltseditors eingefügt, der im Versand-Assistenten bereitgestellt wird (siehe [Über die Personalisierung](about-personalization.md)). Wenn der Empfänger auf diesen Link klickt, wird das Profil in die Blockierungsliste aufgenommen (Opt-out); der Empfänger wird also von keiner Versandaktion mehr als Ziel ausgewählt.

Die Empfänger können sich allerdings von einem Dienst abmelden, ohne sich von allen Diensten abmelden zu müssen. Dazu können Sie ein Webformular verwenden (siehe [diesen Abschnitt](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) oder einen personalisierten Abmelde-Link einfügen (siehe [Gestaltungsbausteine](personalization-blocks.md)).

Sie können sich auch manuell vom Empfängerprofil abmelden. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Abonnements]** den oder die betroffenen Informationsdienste aus und klicken Sie auf **[!UICONTROL Löschen]**.

Über den entsprechenden Informationsdienst können Sie sich abmelden. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Abonnements]** im Tab Dienst die betroffenen Empfänger auswählen und auf **[!UICONTROL Löschen]**.

#### Automatische Abmeldung {#automatic-unsubscription}

Ein Informationsdienst kann eine begrenzte Dauer haben. Die Abmeldung erfolgt automatisch, wenn die Gültigkeitsdauer abgelaufen ist. Dieser Zeitraum wird im Abschnitt **[!UICONTROL Bearbeiten]** Registerkarte der Diensteigenschaften. Sie wird in Tagen definiert.

![](assets/s_ncs_user_services_delay.png)

Sie können auch einen Abmelde-Workflow für eine Population einrichten. Gehen Sie dazu wie bei einem Abonnement-Workflow vor, wählen Sie jedoch die **[!UICONTROL Abmeldung]** -Option. Siehe [Empfänger für Informationsdienste anmelden](#subscribing-a-recipient-to-a-service).

### Abonnement-Verfolgung {#subscriber-tracking}

Auf der Registerkarte **[!UICONTROL Dashboard]** stehen Berichte zur Verfügung, die es ermöglichen, An- und Abmeldungen zu verfolgen.

![](assets/s_ncs_user_services_report.png)
