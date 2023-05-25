---
product: campaign
title: Erstellen einer Versandvorlage
description: Erstellen einer Versandvorlage
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '392'
ht-degree: 100%

---

# Erstellen einer Versandvorlage{#creating-a-delivery-template}



![](assets/do-not-localize/how-to-video.png) [Entdecken Sie diese Funktion im Video](#delivery-template-video).

## Einen bestehenden Versand in eine Vorlage konvertieren {#converting-an-existing-delivery-to-a-template}

Sie haben die Möglichkeit, einen existierenden Versand als Basis für wiederkehrende Versandaktionen zu verwenden. Markieren Sie hierfür in der über den Knoten **[!UICONTROL Kampagnenverwaltung > Sendungen]** zugänglichen Versandliste den gewünschten Versand.

Klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Aktionen > Als Vorlage speichern...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Geben Sie im Feld **[!UICONTROL Ordner]** an, wo die Vorlage gespeichert werden soll, und im Feld **[!UICONTROL Ausführungsordner]**, wo die auf dieser Vorlage beruhenden Sendungen zu speichern sind.

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Weitere Informationen zum Konfigurationsmodus finden Sie unter [Vorlage einem Versand zuordnen](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Neue Vorlage erstellen {#creating-a-new-template}

>[!NOTE]
>
>Zur Vermeidung von Konfigurationsfehlern empfiehlt Adobe, keine neuen Vorlagen zu erstellen, sondern eine native Vorlage zu duplizieren und die Eigenschaften je nach Bedarf anzupassen.

Führen Sie zur Konfiguration einer Versandvorlage die folgenden Schritte aus:

1. Öffnen Sie den Campaign-Explorer.
1. Wählen Sie im Ordner **Ressourcen** die Option **Vorlagen** und dann **Versandvorlagen** aus.

   ![](assets/delivery_template_1.png)

1. Durch Klicken auf **Neu** in der Symbolleiste wird eine neue Versandvorlage erstellt oder über **Duplizieren** eine vorhandene Vorlage dupliziert.

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


## Anleitungsvideos {#delivery-template-video}

### Konfigurieren einer Versandvorlage

Das folgende Video zeigt, wie man eine Vorlage für einen Ad-hoc-Versand konfiguriert.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### Einrichten der Eigenschaften von Versandvorlagen

Das folgende Video zeigt, wie die Eigenschaften der Versandvorlage festgelegt werden, und erklärt die einzelnen Eigenschaften im Detail.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### Bereitstellen einer Ad-hoc-Versandvorlage

In diesem Video wird erläutert, wie man eine Ad-hoc-E-Mail-Versandvorlage bereitstellt. Außerdem wird der Unterschied zwischen einem E-Mail-Versand- und einem Versand-Workflow erläutert.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
