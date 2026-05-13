---
product: campaign
title: Veröffentlichen des Kampagnenkits
description: Veröffentlichen des Kampagnenkits
feature: Distributed Marketing
hide: true
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
TQID: https://experienceleague.adobe.com/5M0QtWtNs4Llfmaw8cbvYLD2YM7ET-QcKf-GjQP0ZRg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 483
ht-degree: 63%

---

# Veröffentlichen des Kampagnenkits{#publishing-the-campaign-package}



Die Benutzenden der Zentralstelle veröffentlichen in der **[!UICONTROL Liste der Kampagnenkits]** die Kits, die den Lokalstellen zur Verfügung gestellt werden sollen.

Bevor sie in der Liste der Kampagnenkits veröffentlicht werden können, müssen die Kampagnenkits von der Zentralstelle genehmigt werden. Zu diesem Zweck können Sie Validierungsverantwortliche oder Gruppen von Validierungsverantwortlichen über den Link **[!UICONTROL Validierungsparameter]** im Kampagnenkit festlegen.

## Validierenden Benutzer bestimmen {#assigning-a-reviewer}

Um den Validierer anzugeben, klicken Sie auf den Link **[!UICONTROL Validierungsparameter...]** des Kampagnenkits und wählen Sie den jeweiligen Benutzer in der Dropdown-Liste aus.

![](assets/s_advuser_mkg_dist_define_valid.png)

Um den Validierungsprozess zu starten, klicken Sie auf die Schaltfläche **[!UICONTROL Zur Validierung unterbreiten]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Der Validierungsverantwortliche erhält dann eine Benachrichtigung, mit der er die Verfügbarkeit dieses Kampagnenkits bestätigt. Die Nachricht enthält einen Link zum Akzeptieren oder Ablehnen der Validierung über den Web-Zugriff.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>Auf Organisationseinheitsebene können Sie auch validierende Benutzer angeben, um Bestellungen zu validieren. Weitere Informationen hierzu finden Sie unter [Organisationseinheiten](about-distributed-marketing.md#organizational-entities).

## Weitere validierende Benutzer hinzufügen {#adding-other-reviewers}

Über den Link **[!UICONTROL Bearbeiten...]** im Tab **[!UICONTROL Validierungsparameter...]** des Kampagnenkits können weitere validierungsverantwortliche Benutzer hinzugefügt werden.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Validierungszeitraum {#approval-periods}

Wenn nicht anders angegeben, muss die Validierung innerhalb von drei Tagen ab dem Unterbreitungsdatum erfolgen.

Im Fenster „Validierungsverantwortliche bearbeiten“ können Sie auch Erinnerungen einstellen, um eine oder mehrere Nachrichten zu senden, wenn ein Kampagnenkit nicht genehmigt wurde. Klicken Sie dazu zunächst auf den Link **[!UICONTROL Erinnerung hinzufügen]** und dann auf die Schaltfläche **[!UICONTROL Hinzufügen]**.

Erinnerungen können entweder an einem bestimmten Datum und/oder **x** Tage nach dem Übermittlungsdatum gesendet werden. Die Art der Erinnerung kann in der ersten Spalte der Erinnerungstabelle konfiguriert werden. Im unten stehenden Beispiel erhalten die Validierungsverantwortlichen eine Erinnerungsnachricht einen Tag vor Ablauf der Validierungsfrist, also zwei Tage nach dem Unterbreitungsdatum, und eine zweite Erinnerung am 29.1.2014, also zwei Tage vor dem in der Spalte **[!UICONTROL Datum]** ausgewählten Datum.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Sobald er definiert ist und das Paket zur Genehmigung eingereicht wurde, wird der Ausführungsplan auf der Registerkarte **[!UICONTROL Audit]** angezeigt. Darin werden die auf der Grundlage der vorherigen Konfiguration berechnete Verarbeitungsfrist sowie die Daten aller konfigurierten Mahnungen angezeigt.

## Validierung über die Adobe Campaign-Konsole {#approving-via-the-adobe-campaign-console}

Wenn kein Validierungsverantwortlicher bestimmt wurde oder keiner der benachrichtigten Benutzer das Kit validiert hat, kann die Validierung direkt über die Schaltfläche **[!UICONTROL Kampagnenkit validieren]** des **[!UICONTROL Dashboards]** des Kampagnenkits oder über die Übersicht der Kits erfolgen.

![](assets/s_advuser_mkg_dist_valid_button.png)

Nach der Validierung wird die Kampagne veröffentlicht und der Liste hinzugefügt. Sobald das Verfügbarkeitsdatum erreicht ist, können Lokalstellen sie verwenden. Wenn die Lokalstellen bei der Erstellung der Kampagne angegeben wurden, wird eine Nachricht an die Benutzenden in der Benachrichtigungsgruppe gesendet, um sie darüber zu informieren, dass die Kampagne verfügbar ist. Wenn zuvor keine Entität angegeben wurde, ist die Kampagne standardmäßig für alle Lokalstellen verfügbar. Weitere Informationen hierzu finden Sie unter [Organisationseinheiten](about-distributed-marketing.md#organizational-entities).
