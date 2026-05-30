---
product: campaign
title: Synchronisieren von Profilen
description: Erfahren Sie, wie Sie Profile mit dem ACS-Connector synchronisieren
feature: ACS Connector
hide: true
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
TQID: https://experienceleague.adobe.com/AmLdA4Rvz3MNJ1U5aqC4ITjfa66N86htyRMJWJKkMb8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1255
ht-degree: 66%

---

# Synchronisieren von Profilen{#synchronizing-profiles}



ACS Connector repliziert Daten von Campaign v7 nach Campaign Standard. Die von Campaign v7 empfangenen Daten können in Campaign Standard verwendet werden, um Sendungen zu erstellen. Sie können sehen, wie Profile synchronisiert werden, indem Sie die unten aufgeführten Vorgänge ausführen.

* **Neue Empfänger hinzufügen**: Erstellen Sie in Campaign v7 einen neuen Empfänger und vergewissern Sie sich, dass ein entsprechendes Profil nach Campaign Standard repliziert wurde. Siehe [Erstellen eines neuen Empfängers](#creating-a-new-recipient).
* **Empfänger aktualisieren**: Bearbeiten Sie einen neuen Empfänger in Campaign v7 und vergewissern Sie sich in Campaign Standard, dass die Änderung repliziert wurde. Siehe [Bearbeiten eines Empfängers](#editing-a-recipient).
* **Workflow in Campaign Standard erstellen**: Erstellen eines Workflows in Campaign Standard, der eine Abfrage mit einer Zielgruppe oder mit Profilen enthält, die aus Campaign v7 repliziert wurden. Siehe [Erstellen eines Workflows](#creating-a-workflow).
* **Versand in Campaign Standard erstellen**: Befolgen Sie den Workflow bis zum Ende, um eine Lieferung zu versenden. Siehe [Erstellen eines Versands](#creating-a-delivery).
* **Abmelde-Link überprüfen**: Verwenden Sie ein Web-Programm von Campaign v7, um sicherzustellen, dass die Entscheidung des Empfängers, sich von einem Service abzumelden, an die Datenbank von Campaign v7 gesendet wird. Die Option, den Service nicht mehr zu erhalten, wird nach Campaign Standard repliziert. Siehe [Ändern des Abmelde-Links](#changing-the-unsubscription-link).

## Voraussetzungen {#prerequisites}

In den folgenden Abschnitten wird beschrieben, wie Sie mit dem ACS-Connector Empfänger in Campaign v7 hinzufügen und bearbeiten und dann in einem Campaign Standard-Versand verwenden können. ACS Connector erfordert Folgendes:

* Empfänger in Campaign v7, die nach Campaign Standard repliziert wurden
* Benutzerrechte zur Durchführung von Workflows in sowohl Campaign v7 als auch Campaign Standard
* Benutzerrechte zur Erstellung und Durchführung eines Versands in Campaign Standard

## Ändern des Abmelde-Links {#changing-the-unsubscription-link}

Wenn ein Empfänger in einer von Campaign Standard gesendeten E-Mail auf den Abmelde-Link klickt, wird das entsprechende Profil in Campaign Standard aktualisiert. Um sicherzustellen, dass ein repliziertes Profil die Entscheidung eines Benutzers enthält, sich von einem Service abzumelden, müssen die Informationen an Campaign v7 und nicht an Campaign Standard gesendet werden. Um die Änderung auszuführen, ist der Abmelde-Service mit einer Web-Anwendung von Campaign v7 und nicht mit Campaign Standard verknüpft.

>[!NOTE]
>
>Ersuchen Sie bitte Ihren Berater, die Webanwendung für den Abmeldedienst zu konfigurieren, bevor Sie die folgenden Schritte ausführen.

## Erstellen eines neuen Empfängers {#creating-a-new-recipient}

1. Erstellen Sie in Campaign v7 einen neuen Empfänger für die Replikation nach Campaign Standard. Geben Sie so viele Informationen wie möglich ein, einschließlich Nachname, Vorname, E-Mail-Adresse und Postanschrift des Empfängers. Wählen Sie jedoch keine **[!UICONTROL Anrede]**, da diese im nächsten Abschnitt [Bearbeiten einer Empfängerin bzw. eines Empfängers](#editing-a-recipient) hinzugefügt wird.

   ![](assets/acs_connect_profile_sync_01.png)

1. Bestätigen Sie, dass der neue Empfänger zu Campaign Standard hinzugefügt wurde. Überprüfen Sie bei der Profilüberprüfung, ob die in Campaign v7 eingegebenen Daten auch in Campaign Standard verfügbar sind. Informationen darüber, wo Sie Profile in Campaign Standard ansehen können, finden Sie im Abschnitt [Navigationsprinzipien](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=de).

   ![](assets/acs_connect_profile_sync_02.png)

   Standardmäßig wird für den ACS-Connector alle 15 Minuten eine Replikation durchgeführt. Weiterführende Informationen finden Sie unter [Datenreplikation](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Bearbeiten eines Empfängers {#editing-a-recipient}

Die folgenden Schritte zum Ändern eines einzelnen Datenpunkts veranschaulichen auf einfache Weise, wie Campaign v7 bei Verwendung von Datenreplikation zur primären Datenbank für Campaign Standard wird. Das Ändern oder Löschen replizierter Daten in Campaign v7 hat dieselbe Wirkung auf die entsprechenden Daten in Campaign Standard.

1. Wählen Sie die Empfängerin bzw. den Empfänger, die/den Sie unter [Erstellen einer neuen Empfängerin bzw. eines neuen Empfängers](#creating-a-new-recipient) erstellt haben, und bearbeiten Sie den Empfängernamen. Wählen Sie beispielsweise eine **[!UICONTROL Anrede]** für die Empfängerin bzw. den Empfänger (Herr oder Frau).

   ![](assets/acs_connect_profile_sync_03.png)

1. Vergewissern Sie sich, dass der Empfängername in Campaign Standard aktualisiert wurde. Informationen darüber, wo Sie Profile in Campaign Standard ansehen können, finden Sie im Abschnitt [Navigationsprinzipien](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=de).

   ![](assets/acs_connect_profile_sync_04.png)

   Standardmäßig wird für den ACS-Connector alle 15 Minuten eine Replikation durchgeführt. Weiterführende Informationen finden Sie unter [Datenreplikation](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Erstellen eines Workflows {#creating-a-workflow}

Von Campaign v7 replizierte Profile und Services stehen Digital-Marketing-Experten zur Verfügung, um die umfangreichen Daten in Campaign Standard zu nutzen. Die folgenden Anweisungen zeigen, wie Sie eine Abfrage zu einem Campaign Standard-Workflow hinzufügen und dann mit der replizierten Datenbank verwenden.

Weiterführende Informationen und die vollständige Anleitung zu Campaign Standard-Workflows finden Sie im Abschnitt [Workflows](../../workflow/using/about-workflows.md).

1. Gehen Sie zu Campaign Standard und wählen Sie **[!UICONTROL Marketing-Aktivitäten]** aus.
1. Wählen Sie rechts oben **[!UICONTROL Erstellen]** aus.
1. Wählen Sie **[!UICONTROL Workflow]** aus.
1. Wählen Sie **[!UICONTROL Neuer Workflow]** und **[!UICONTROL Weiter]** aus.
1. Geben Sie im Feld **[!UICONTROL Titel]** einen Namen für den Workflow sowie nach Bedarf zusätzliche Informationen ein. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Ziehen Sie aus dem Bereich **[!UICONTROL Zielgruppenbestimmung]** auf der linken Seite ein **[!UICONTROL Abfrage]**-Ziel in den Arbeitsbereich.

   ![](assets/acs_connect_profile_sync_05.png)

1. Doppelklicken Sie auf die Aktivität **[!UICONTROL Abfrage]** und wählen Sie einen Parameter aus, der mit der replizierten Datenbank verwendet werden kann. Sie können beispielsweise:

   * Ziehen Sie **[!UICONTROL Profile]** in den Arbeitsbereich. Wählen Sie über das Pulldown-Menü die Option **[!UICONTROL Ist erweiterungsfähige externe Ressource]** aus, um Profile zu finden, die von Campaign v7 repliziert wurden.
   * Schränken Sie die Zielgruppe weiter ein, indem Sie weitere Abfrageparameter in den Arbeitsbereich ziehen.

## Erstellen eines Versands {#creating-a-delivery}

>[!NOTE]
>
>In der Anleitung zur Erstellung des Versands wird der Vorgang fortgesetzt, der mit dem [Erstellen eines Workflows](#creating-a-workflow) begonnen wurde.

Digitale Marketer können eine Web-Anwendung von Campaign v7 nutzen, um sicherzustellen, dass die Entscheidung eines Empfängers, sich von einem Service abzumelden, an die Datenbank von Campaign v7 gesendet wird. Nachdem der Empfänger auf den Abmelde-Link geklickt hat, wird die Option, den Service nicht mehr zu erhalten, von Campaign v7 nach Campaign Standard repliziert. Weitere Informationen finden Sie unter [Ändern des Abmelde-Links](#changing-the-unsubscription-link).

Folgen Sie den unten beschriebenen Schritten, um einem bestehenden Workflow einen E-Mail-Versand hinzuzufügen, wobei der Abmeldedienst in Campaign v7 erstellt wird. Weiterführende Informationen und eine vollständige Anleitung zu Campaign-Standard-Workflows finden Sie in diesem [Dokument](../../workflow/using/about-workflows.md).

>[!NOTE]
>
>Ersuchen Sie bitte Ihren Berater, die Webanwendung für den Abmeldedienst zu konfigurieren, bevor Sie die folgenden Schritte ausführen.

1. Wählen Sie links **[!UICONTROL Kanäle]** aus.
1. Ziehen Sie **[!UICONTROL E-Mail-Versand]** zum vorhandenen Workflow im Arbeitsbereich.

   ![](assets/acs_connect_profile_sync_07.png)

1. Wählen Sie mit einem Doppelklick die Aktivität **[!UICONTROL E-Mail-Versand]** aus und danach **[!UICONTROL Einmalige E-Mail]** oder **[!UICONTROL Wiederkehrende E-Mail]**. Wählen Sie die gewünschten Optionen aus und danach **[!UICONTROL Weiter]**.
1. Wählen Sie **[!UICONTROL Per E-Mail versenden]** und danach **[!UICONTROL Weiter]** aus.

   ![](assets/acs_connect_profile_sync_08.png)

1. Geben Sie im Feld **[!UICONTROL Titel]** einen Namen für den Versand und nach Bedarf weitere Informationen ein. Klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. Geben Sie im Feld **[!UICONTROL Betreff]** den Betreff ein, der im Posteingang des Empfängers angezeigt werden soll.
1. Wählen Sie **[!UICONTROL Inhalt wechseln]** aus, um eine HTML-Vorlage hinzuzufügen.

   ![](assets/acs_connect_profile_sync_10.png)

1. Wählen Sie einen Inhalt aus, der einen Abmelde-Link enthält. Klicken Sie auf **[!UICONTROL Bestätigen]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. Der aktuelle Abmelde-Link muss durch einen neuen ersetzt werden, der die von Ihrem Berater erstellte Web-Anwendung verwendet. Suchen Sie den Abmelde-Link am unteren Rand des E-Mail-Inhalts und klicken Sie darauf. Klicken Sie auf das Papierkorbsymbol, um den Link zu löschen.

   ![](assets/acs_connect_profile_sync_12.png)

1. Klicken Sie in denselben Inhaltsbereich und geben Sie **Abmelde-Link** ein.

   ![](assets/acs_connect_profile_sync_13.png)

1. Heben Sie den Text mit dem Cursor hervor und wählen Sie dann das Kettensymbol aus.
1. Wählen Sie **[!UICONTROL Link zu einer Landingpage]** aus.

   ![](assets/acs_connect_profile_sync_14.png)

1. Klicken Sie auf das Ordnersymbol, um die Landingpage auszuwählen.

   ![](assets/acs_connect_profile_sync_15.png)

1. Wählen Sie die vom Consultant erstellte Webanwendung und danach **[!UICONTROL Bestätigen]** aus.

   ![](assets/acs_connect_profile_sync_16.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Kehren Sie durch die Auswahl des Versandnamens zum Workflow zurück.

   ![](assets/acs_connect_profile_sync_17.png)

1. Klicken Sie **[!UICONTROL Start]**, um den Versand durchzuführen. Das Symbol für den E-Mail-Versand blinkt, um anzuzeigen, dass er für den Versand vorbereitet wird.

   ![](assets/acs_connect_profile_sync_18.png)

1. Wählen Sie mit einem Doppelklick den Kanal **[!UICONTROL E-Mail-Versand]** aus. **** Klicken Sie auf **[!UICONTROL OK]**, um die Nachrichten zu senden.

   ![](assets/acs_connect_profile_sync_19.png)

## Verifizieren des Abmelde-Services {#verifying-the-unsubscription-service}

Befolgen Sie die Anweisungen in [Erstellen eines Workflows](#creating-a-workflow) und [Erstellen eines Versands](#creating-a-delivery), bevor Sie mit den folgenden Schritten fortfahren.

1. Der Empfänger klickt auf den Abmelde-Link in der E-Mail.

   ![](assets/acs_connect_profile_sync_20.png)

1. Der Empfänger bestätigt die Abmeldung.

   ![](assets/acs_connect_profile_sync_21.png)

1. Die Empfängerdaten in Campaign v7 werden entsprechend aktualisiert. Bestätigen Sie, dass die Option **[!UICONTROL Nicht mehr kontaktieren (alle Kanäle)]** für die Empfängerin bzw. den Empfänger aktiviert ist.

   ![](assets/acs_connect_profile_sync_22.png)

1. Gehen Sie zu Campaign Standard und öffnen Sie die Profildetails des Empfängers. Vergewissern Sie sich, dass **[!UICONTROL Nicht mehr kontaktieren (alle Kanäle)]** ein Häkchen aufweist. Informationen darüber, wo Sie Profile in Campaign Standard ansehen können, finden Sie im Abschnitt [Navigationsprinzipien](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=de).

   ![](assets/acs_connect_profile_sync_23.png)
