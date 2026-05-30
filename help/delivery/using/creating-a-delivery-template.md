---
product: campaign
title: Erstellen einer Versandvorlage
description: Erstellen einer Versandvorlage
feature: Delivery Templates
hide: true
role: User
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
TQID: https://experienceleague.adobe.com/5rlrthjXAnU8yfU1z67u-7uD0Z-pRfm0-Or5q7PBs-Q
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 400
ht-degree: 100%

---

# Erstellen einer Versandvorlage{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Entdecken Sie diese Funktion im Video](#delivery-template-video).

## Einen bestehenden Versand in eine Vorlage konvertieren {#converting-an-existing-delivery-to-a-template}

Sie haben die Möglichkeit, einen existierenden Versand als Basis für wiederkehrende Versandaktionen zu verwenden. Markieren Sie hierfür in der über den Knoten **[!UICONTROL Kampagnenverwaltung > Sendungen]** zugänglichen Versandliste den gewünschten Versand.

Klicken Sie mit der rechten Maustaste und wählen Sie **[!UICONTROL Aktionen > Als Vorlage speichern...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Dadurch wird eine Versandvorlage aus dem ausgewählten Versand erstellt. Geben Sie im Feld **[!UICONTROL Ordner]** an, wo die Vorlage gespeichert werden soll, und im Feld **[!UICONTROL Ausführungsordner]**, wo die auf dieser Vorlage beruhenden Sendungen zu speichern sind.

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

1. Tragen Sie der Kategorie **E-Mail-Parameter** den E-Mail-Betreff und die Zielpopulation ein.
1. Fügen Sie Ihren **HTML-Inhalt** ein, um Ihre Vorlage zu personalisieren. Sie können auch einen Mirrorseite-Link und einen Abmelde-Link angeben.
1. Wählen Sie die Registerkarte **Vorschau**. Wählen Sie im Dropdown-Menü **Personalisierung testen** die Option **Empfänger** aus, um sich Ihre Vorlage in der Vorschau anzusehen.

   ![](assets/delivery_template_5.png)

1. Klicken Sie auf **Speichern**. Ihre Vorlage kann jetzt in einem Versand verwendet werden.


## Anleitungsvideos {#delivery-template-video}

### Konfigurieren einer Versandvorlage

Das folgende Video zeigt, wie man eine Vorlage für einen Ad-hoc-Versand konfiguriert.

>[!VIDEO](https://video.tv.adobe.com/v/27531?captions=ger&quality=12)

### Einrichten der Eigenschaften von Versandvorlagen

Das folgende Video zeigt, wie die Eigenschaften der Versandvorlage festgelegt werden, und erklärt die einzelnen Eigenschaften im Detail.

>[!VIDEO](https://video.tv.adobe.com/v/39113?captions=ger&quality=12)

### Bereitstellen einer Ad-hoc-Versandvorlage

In diesem Video wird erläutert, wie man eine Ad-hoc-E-Mail-Versandvorlage bereitstellt. Außerdem wird der Unterschied zwischen einem E-Mail-Versand- und einem Versand-Workflow erläutert.

>[!VIDEO](https://video.tv.adobe.com/v/27449?captions=ger&quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
