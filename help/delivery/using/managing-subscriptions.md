---
title: Abonnements verwalten
seo-title: Abonnements verwalten
description: Abonnements verwalten
seo-description: null
page-status-flag: never-activated
uuid: a2c526fa-3080-4dd5-9628-f0e7040f93cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 9a61fe74-f779-4f23-be25-3d9a8e95704a
translation-type: ht
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: ht
source-wordcount: '1158'
ht-degree: 100%

---


# Abonnements verwalten{#managing-subscriptions}

## Über Informationsdienste {#about-information-services}

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
>Ein Muster zum Erstellen eines Anmeldeformulars mit zweifacher Bestätigung finden Sie in [diesem Abschnitt](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## Informationsdienste erstellen {#creating-an-information-service}

Sie haben die Möglichkeit, Abonnements für Informationsdienste zu erstellen und zu verwalten und ihnen Bestätigungsnachrichten oder andere automatische Mitteilungen zuzuordnen.

Die Rubrik **[!UICONTROL Profile und Zielgruppen]** bietet unter dem Stichwort **[!UICONTROL Dienste und Abonnements]** eine Übersicht über alle existierenden Informationsdienste.

![](assets/s_ncs_user_services_new.png)

Klicken Sie auf den Namen eines Dienstes, um ihn zu öffnen und zu bearbeiten, oder auf die Schaltfläche **[!UICONTROL Erstellen]**, um einen neuen Dienst anzulegen.

![](assets/s_ncs_user_services_add.png)

* Geben Sie im Feld **[!UICONTROL Titel]** einen Namen für den neuen Dienst ein und wählen Sie den Versandkanal aus: E-Mail, Mobile, Facebook, Twitter oder Mobile App.

   >[!NOTE]
   >
   >Facebook- und Twitter-Abonnements werden in [diesem Abschnitt](../../social/using/about-social-marketing.md) ausführlich beschrieben. Mobile App-Abonnements werden im Abschnitt [Über den Mobile-App-Kanal](../../delivery/using/about-mobile-app-channel.md) beschrieben.

* Bei Diensten vom Typ **E-Mail** haben Sie die Wahl zwischen zwei Modi: **[!UICONTROL Newsletter]** oder **[!UICONTROL Viral]**.
* Sie haben die Möglichkeit, bei An- und Abmeldungen **Bestätigungsnachrichten** zu versenden. Wählen Sie in diesem Fall neben den Feldern **[!UICONTROL Anmeldung]** und **[!UICONTROL Abmeldung]** die jeweils zu verwendenden Versandvorlagen aus. Die Vorlagen müssen mit einem Zielgruppen-Mapping des Typs **[!UICONTROL Abonnements]** und ohne Angabe einer Zielgruppe konfiguriert werden. Siehe Abschnitt [Über den E-Mail-Kanal](../../delivery/using/about-email-channel.md).
* Standardmäßig sind Abonnements zeitlich nicht begrenzt. Sie können jedoch die Option **[!UICONTROL Unbegrenzt]** abwählen und eine Gültigkeitsdauer in Tagen (**[!UICONTROL T]**) oder Monaten (**[!UICONTROL M]**) festlegen.

Speichern Sie den Dienst und klicken Sie in der Liste auf seinen Namen, um mit der Bearbeitung fortzufahren. Im Tab **[!UICONTROL Abonnements]** wird die Liste aller angemeldeten User (Unter-Tab **[!UICONTROL Aktive Abonnements]**) bzw. aller An- und Abmeldungen (Unter-Tab **[!UICONTROL Verlauf]**) angezeigt. Sie haben an dieser Stelle auch die Möglichkeit, Abonnenten hinzuzufügen oder zu entfernen. Siehe [Abonnenten hinzufügen und löschen](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Die Schaltfläche **[!UICONTROL Details...]** bietet die Möglichkeit, die Eigenschaften des Abonnements für den markierten Empfänger anzuzeigen und zu ändern.

Sie können die Eigenschaften des Abonnements für einen Empfänger ändern.

![](assets/s_ncs_user_services_modify.png)

Klicken Sie zur Verfolgung der Abonnements (Anmeldungen, Abonnentenanzahl usw.) im Dashboard auf den Tab **[!UICONTROL Berichte]**. Hier können Sie außerdem Berichte archivieren und auf Verläufe zugreifen.

## Abonnenten hinzufügen und löschen {#adding-and-deleting-subscribers}

Klicken Sie im **[!UICONTROL Abonnements]**-Tab eines Dienstes auf die Schaltfläche **[!UICONTROL Hinzufügen]**. (Eine weitere Möglichkeit ist, in der Abonnentenliste einen Rechtsklick zu machen und die Option **[!UICONTROL Hinzufügen]** zu wählen.) Geben Sie den die anzumeldenden Empfänger enthaltenden Ordner an, markieren Sie die neuen Abonnenten und klicken Sie zur Bestätigung auf **[!UICONTROL OK]**.

Um Abonnenten zu entfernen, markieren Sie sie und klicken Sie auf **[!UICONTROL Löschen]**. (Sie haben auch die Möglichkeit, auf der Abonnentenliste einen Rechtsklick zu machen und die Option **[!UICONTROL Löschen]** zu wählen.)

In beiden Fällen können Sie eine Bestätigungsnachricht an die betreffenden Benutzer senden, wenn eine Versandvorlage für Abmeldungen mit dem Dienst verknüpft wurde (siehe [Informationsdienste erstellen](#creating-an-information-service)). Mit einem Warnhinweis können Sie diesen Versand validieren oder nicht validieren:

![](assets/s_ncs_user_services_update.png)

Siehe [An- und Abmeldungen](#subscription-and-unsubscription-mechanisms).

## An Abonnenten eines Dienstes versenden {#delivering-to-the-subscribers-of-a-service}

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
>Die Bestätigungsnachrichten werden ausgehend von den Vorlagen erstellt, die hier angegeben werden. Das Zielgruppen-Mapping der Vorlagen muss vom Typ **[!UICONTROL Abonnements]** sein.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Empfänger für Informationsdienste anmelden {#subscribing-a-recipient-to-a-service}

Sie haben verschiedene Möglichkeiten, um einen Empfänger für einen Dienst anzumelden:

* Dienst manuell hinzufügen. Klicken Sie im Tab **[!UICONTROL Abonnements]** des Empfängerprofils auf **[!UICONTROL Hinzufügen]** und wählen Sie den gewünschten Dienst aus.

   Lesen Sie diesbezüglich auch über die Bearbeitung von Empfängerprofilen in [diesem Abschnitt](../../platform/using/editing-a-profile.md).

* Gruppe von Empfängern gebündelt für einen Dienst anmelden. Bei den Empfängern kann es sich beispielsweise um eine bestehende Gruppe, das Ergebnis einer Filterung bzw. eines Imports oder um in einem bestimmten Ordner enthaltene Profile handeln. Markieren Sie die Empfänger, klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Aktionen > Auswahl für einen Dienst anmelden...]**. Markieren Sie den gewünschten Dienst und starten Sie den Vorgang.
* Empfänger im Zuge eines Imports für einen Dienst anmelden. Geben Sie im letzten Schritt des Import-Assistenten den gewünschten Dienst an.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/importing-data.md#import-wizard).

* Empfänger melden sich persönlich über ein Webformular an.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../web/using/about-web-applications.md).

* Empfänger unter Verwendung eines Workflows mit der Aktivität **[!UICONTROL Abonnements]** anmelden.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   Workflows und ihre Verwendung in Formularen werden in [diesem Abschnitt](../../workflow/using/about-workflows.md) beschrieben.

### Empfänger von einem Dienst abmelden {#unsubscribing-a-recipient-from-a-service}

#### Manuelle Abmeldung {#manual-unsubscribing}

Für kommerzielle E-Mail-Sendungen ist das Einfügen eines Abmelde-Links gesetzlich vorgeschrieben. Empfänger, die nicht mehr kontaktiert werden möchten, können auf den entsprechenden Link klicken und werden so zukünftig aus den Versandzielgruppen ausgeschlossen.

Der standardmäßige Abmelde-Link wird über die letzte Schaltfläche in der Symbolleiste des Inhaltseditors eingefügt, der im Versand-Assistenten bereitgestellt wird (siehe [Über die Personalisierung](../../delivery/using/about-personalization.md)). Wenn der Empfänger auf diesen Link klickt, wird das Profil in die Blockierungsliste aufgenommen (Opt-out); der Empfänger wird also von keiner Versandaktion mehr als Ziel ausgewählt.

Die Empfänger können sich allerdings von einem Dienst abmelden, ohne sich von allen Diensten abmelden zu müssen. Dazu können Sie ein Webformular verwenden (siehe [diesen Abschnitt](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) oder einen personalisierten Abmelde-Link einfügen (siehe [Gestaltungsbausteine](../../delivery/using/personalization-blocks.md)).

Des Weiteren können Sie einen Empfänger manuell über sein Profil abmelden. Klicken Sie hierfür auf den **[!UICONTROL Abonnements]**-Tab, markieren Sie die entsprechenden Informationsdienste und klicken Sie auf **[!UICONTROL Löschen]**.

Eine andere Möglichkeit ist die Abmeldung eines oder mehrerer Empfänger direkt im betroffenen Informationsdienst. Klicken Sie hierfür auf den **[!UICONTROL Abonnements]**-Tab des Dienstes, markieren Sie die Empfänger und klicken Sie auf **[!UICONTROL Löschen]**.

#### Automatische Abmeldung {#automatic-unsubscription}

Ein Informationsdienst kann eine begrenzte Gültigkeit haben. Nach deren Ablauf werden die Abonnenten automatisch abgemeldet. Die Dauer der Gültigkeit wird im **[!UICONTROL Bearbeiten]**-Tab der Diensteigenschaften konfiguriert (in Tagen).

![](assets/s_ncs_user_services_delay.png)

Sie haben außerdem die Möglichkeit, einen Abmelde-Workflow für eine bestimmte Population zu erstellen. Gehen Sie wie oben für einen Anmelde-Workflow beschrieben vor und kreuzen Sie in der Abonnements-Aktivität die Option **[!UICONTROL Abmeldung]** an. Siehe [Empfänger für Informationsdienste anmelden](#subscribing-a-recipient-to-a-service).

### Abonnement-Verfolgung {#subscriber-tracking}

Im Tab **[!UICONTROL Dashboard]** stehen Berichte zur Verfügung, die es ermöglichen, An- und Abmeldungen zu verfolgen.

![](assets/s_ncs_user_services_report.png)
