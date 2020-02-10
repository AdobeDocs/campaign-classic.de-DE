---
title: Versandvorlage erstellen
seo-title: Versandvorlage erstellen
description: Versandvorlage erstellen
seo-description: null
page-status-flag: never-activated
uuid: 8ceae1ec-9e02-4809-aa8b-1e6bd7790950
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 0e67d9dd-3ee8-4c06-98a4-3a2c644b6c0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Versandvorlage erstellen{#creating-a-delivery-template}

## Einen bestehenden Versand in eine Vorlage konvertieren {#converting-an-existing-delivery-to-a-template}

Eine Bereitstellung kann für neue wiederholte Übermittlungsaktionen in eine Vorlage konvertiert werden. Um eine Bereitstellung in eine Vorlage zu konvertieren, wählen Sie sie in der Bereitstellungsliste aus, auf die über den **[!UICONTROL Campaign management]** Knoten der Struktur zugegriffen werden kann.

Right-click and select **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Diese Aktion erstellt eine Bereitstellungsvorlage aus der ausgewählten Bereitstellung. Sie müssen den Ordner eingeben, in dem die Bereitstellung gespeichert wird (im **[!UICONTROL Folder]** Feld), sowie den Ordner, in dem die auf der Grundlage dieser Vorlage erstellten Auslieferungen erstellt werden (im **[!UICONTROL Execution folder]** Feld).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Weitere Informationen zum Konfigurationsmodus finden Sie unter [Verknüpfen der Vorlage mit einer Bereitstellung](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Neue Vorlage erstellen {#creating-a-new-template}

Führen Sie zur Konfiguration einer Versandvorlage die folgenden Schritte aus:

1. Öffnen Sie den Campaign-Explorer.
1. Wählen Sie im Ordner **Ressourcen** die Option **Vorlagen** und dann **Versandvorlagen** aus.

   ![](assets/delivery_template_1.png)

1. Klicken Sie in der Symbolleiste auf **Neu**, um eine neue Versandvorlage zu erstellen.

   ![](assets/delivery_template_2.png)

1. Ändern Sie den **Titel** und den Ordnernamen **Interner Name**.
1. Speichern Sie Ihre Vorlage und öffnen Sie sie erneut.
1. Klicken Sie auf die Schaltfläche **Eigenschaften** und ändern Sie dann die Werte entsprechend Ihren Anforderungen.

   ![](assets/delivery_template_3.png)

1. Bestätigen Sie im Tab **Allgemein** die in den Dropdown-Menüs **Ausführungsordner**, **Ordner** und **Routing** ausgewählten Speicherorte oder ändern Sie sie.

   ![](assets/delivery_template_4.png)

1. Tragen Sie der Kategorie **E-Mail-Parameter** den E-Mail-Betreff und die Zielgruppe ein.
1. Fügen Sie Ihren **HTML-Inhalt** ein, um Ihre Vorlage zu personalisieren. Sie können auch einen Mirrorseite-Link und einen Abmelde-Link angeben.
1. Wählen Sie den Tab **Vorschau**. Wählen Sie im Dropdown-Menü **Personalisierung testen** die Option **Empfänger** aus, um sich Ihre Vorlage in der Vorschau anzusehen.

   ![](assets/delivery_template_5.png)

1. Klicken Sie auf **Speicher**. Ihre Vorlage kann jetzt in einem Versand verwendet werden.

>[!NOTE]
>
>Zur Vermeidung von Konfigurationsfehlern wird empfohlen, keine neuen Vorlagen zu erstellen, sondern native Vorlagen zu duplizieren und die Eigenschaften je nach Bedarf anzupassen.
