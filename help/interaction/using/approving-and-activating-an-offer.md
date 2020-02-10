---
title: Angebotsvalidierung
seo-title: Angebotsvalidierung
description: Angebotsvalidierung
seo-description: null
page-status-flag: never-activated
uuid: 1be96bb4-ef17-4b4d-b872-05e1c6b1412d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 7b1c58a0-6fd6-4c9d-b1c4-f3dffda42523
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Angebotsvalidierung{#approving-and-activating-an-offer}

Nach Erstellung seines Inhalts muss ein Angebot validiert werden, um in die Live-Umgebung dupliziert zu werden und somit zur Unterbreitung zur Verfügung zu stehen. Die Validierung bezieht sich sowohl auf den Inhalt als auch auf die Eignung des Angebots.

Ein Banner im Dashboard zeigt den Validierungsstatus an.

![](assets/offer_validate_001.png)

## Angebotsinhalte validieren {#approving-offer-content}

Die Validierung des Angebotsinhalts besteht darin, die Darstellung(en) des Angebots auszuwählen, die in der Live-Umgebung zur Verfügung gestellt werden sollen.

Ein Angebotsinhalt hat pro Platzierung eine Darstellung. Da jede Platzierung ihre eigene Struktur und eigene Rendering-Funktionen aufweist, kann die Darstellung eines Angebots je nach Platzierung variieren.

Sie haben daher die Möglichkeit, den Inhalt eines Angebots für gewisse Platzierungen zu validieren, ihn für andere jedoch abzulehnen.

>[!CAUTION]
>
>Sobald Inhalt und Eignung eines Angebots validiert wurden, startet automatisch der Publikations-Workflow (Angebotsbenachrichtigung), welcher das Angebot in die Live-Umgebung dupliziert und für die aktivierten Platzierungen verfügbar macht.

Gehen Sie wie folgt vor, um den Inhalt eines Angebots zu validieren:

1. Klicken Sie auf die **[!UICONTROL Approval]** Schaltfläche und wählen Sie **[!UICONTROL Approve content]** im Popup aus.

   ![](assets/offer_validate_002.png)

1. Using the drop-down list, select the representations you want to keep editing or those you want to publish to the live environment, then click **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   Nach erfolgter Validierung werden die Informationen im Angebots-Dashboard aktualisiert.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >Die **[!UICONTROL Content approved]** Erwähnung bedeutet nicht, dass alle Angebotsdarstellungen aktiviert und genehmigt wurden. Es zeigt an, dass der Prozess zur Inhaltsgenehmigung erreicht wurde, unabhängig davon, ob alle Angebote aktiviert/genehmigt wurden oder nicht.

## Angebotseignungen validieren {#approving-offer-eligibility}

Die Eignungsvalidierung umfasst die Prüfung der Gewichtung sowie der im Angebot konfigurierten oder aus der übergeordneten Kategorie resultierenden Eignungsregeln.

>[!CAUTION]
>
>Sobald Inhalt und Eignung eines Angebots validiert wurden, startet automatisch der Publikations-Workflow (Angebotsbenachrichtigung), welcher das Angebot in die Live-Umgebung dupliziert und für die aktivierten Platzierungen verfügbar macht.

* Die vollständige Liste der Regeln können Sie durch Klicken auf **[!UICONTROL Schedule and eligibility rules]**.

   ![](assets/offer_validate_005.png)

* Um die Berechtigungsregeln zu ändern, klicken Sie auf **[!UICONTROL Reject]** und dann auf **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_007.png)

   Die diversen Status werden im Angebots-Dashboard aktualisiert.

   ![](assets/offer_validate_006.png)

* To accept the offer eligibility, click **[!UICONTROL Approve eligibility]**.

   ![](assets/offer_validate_008.png)

   Approve eligibility, add a comment if necessary, then click **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_009.png)

   Die diversen Status werden im Angebots-Dashboard aktualisiert.

   ![](assets/offer_validate_010.png)

## Validierungsverfolgung {#approval-tracking}

Die Genehmigungsverfolgung ist im Angebots-Dashboard verfügbar. Klicken Sie auf **[!UICONTROL Hide/display logs]** , um darauf zuzugreifen.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>Tracking is also available in the **[!UICONTROL Audit]** tab of the offer, with details of reviewers&#39; comments.

## Validierungen zurücksetzen {#restart-the-approval}

Sie haben die Möglichkeit, eine bereits erfolgte Validierung zurückzusetzen. Gehen Sie wie folgt vor:

1. Klicken Sie **[!UICONTROL Content approved]** auf das Angebotsdashboard.
1. Wählen Sie im daraufhin angezeigten **[!UICONTROL Edit]** Fenster die zu startende Genehmigung aus und klicken Sie dann auf **[!UICONTROL Re-initialize approval to submit it again]**.
1. Confirm by clicking **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## Angebote freigeben {#publishing-the-offer}

Sobald der Inhalt und die Berechtigung eines Angebots genehmigt wurden, wird das Angebot durch einen Workflow veröffentlicht, der automatisch für jedes Angebot ausgeführt wird, dessen Genehmigungszyklus abgeschlossen ist. Der **[!UICONTROL Offer notification]** Workflow wird außerdem stündlich ausgeführt, um die im Angebotskatalog enthaltenen Bereiche und Kategorien (falls erforderlich) von der Designumgebung zur Live-Umgebung zu synchronisieren.

Das Angebots-Dashboard in der Design-Umgebung enthält alle Informationen bezüglich seiner Freigabe für die Live-Umgebung, insbesondere den dortigen Angebotstitel.

![](assets/offer_golive_001.png)

Bei freigegebenen Angeboten werden Sie durch Klick auf den Angebotstitel in die Live-Umgebung weitergeleitet. Das dort angezeigte Dashboard enthält alle relevanten Informationen.

![](assets/offer_golive_002.png)

## Angebote deaktivieren {#disabling-an-offer}

Es besteht die Möglichkeit, bereits validierte Angebote zu deaktivieren.

To do this, go to the dashboard for an online offer or an offer waiting to go online, then click **[!UICONTROL Disable offer]**.

You can also directly disable a category by going to the **[!UICONTROL Eligibility]** tab and checking the **[!UICONTROL Enabled]** box.

>[!NOTE]
>
>Wenn Sie ein freigegebenes Angebot löschen, wird es automatisch in der Live-Umgebung deaktiviert. Nach Ablauf der Beibehaltungsdauer der Vorschläge werden die deaktivierten Angebote aus der Live-Umgebung gelöscht.

![](assets/offer_preview_deactivate.png)

