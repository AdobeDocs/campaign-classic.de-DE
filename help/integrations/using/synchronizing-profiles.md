---
title: Profile synchronisieren
seo-title: Profile synchronisieren
description: Profile synchronisieren
seo-description: null
page-status-flag: never-activated
uuid: 3d5f0fd4-dfe7-4b34-a75f-8cf36fb7c91d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 91115d4f-0cb6-4bce-b28d-17f15e9f9a0a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 56212b320d5077f9b66952e7c11eb8bdcea9e3b4
workflow-type: ht
source-wordcount: '1266'
ht-degree: 100%

---


# Profile synchronisieren{#synchronizing-profiles}

ACS Connector repliziert Daten von Campaign v7 nach Campaign Standard. Die von Campaign v7 übertragenen Daten können in Campaign Standard zur Versanderstellung verwendet werden. Führen Sie die folgenden Schritte aus, um Profile zu synchronisieren.

* **Neue Empfänger hinzufügen**: Erstellen Sie in Campaign v7 einen neuen Empfänger und vergewissern Sie sich, dass ein entsprechendes Profil nach Campaign Standard repliziert wurde. Siehe [Neuen Empfänger erstellen](#creating-a-new-recipient).
* **Empfänger aktualisieren**: Bearbeiten Sie einen neuen Empfänger in Campaign v7 und vergewissern Sie sich in Campaign Standard, dass die Änderung repliziert wurde. Siehe [Empfänger bearbeiten](#editing-a-recipient).
* **Workflow in Campaign Standard erstellen**: Erstellen Sie einen Workflow in Campaign Standard, der eine Abfrage mit einer Zielgruppe oder mit Profilen enthält, die aus Campaign v7 repliziert wurden. Lesen Sie diesbezüglich auch den Abschnitt [Workflows erstellen](#creating-a-workflow).
* **Versand in Campaign Standard erstellen**: Führen Sie den Workflow aus und schließen Sie ihn mit einem Versand ab. Siehe [Versand erstellen](#creating-a-delivery).
* **Abmelde-Link verifizieren**: Verifizieren Sie mit einer Campaign v7-Webanwendung, dass die Entscheidung des Empfängers, sich von einem Dienst abzumelden, an die Datenbank von Campaign v7 gesendet wurde. Die Entscheidung, diesen Dienst nicht mehr in Anspruch zu nehmen, wird nach Campaign Standard repliziert. Siehe [Abmelde-Link ändern](#changing-the-unsubscription-link).

## Voraussetzungen {#prerequisites}

Im folgenden Abschnitt wird beschrieben, wie Sie mithilfe von ACS Connector Empfänger in Campaign v7 hinzufügen und bearbeiten und dann in einem Campaign Standard-Versand verwenden können. ACS Connector benötigt dazu Folgendes:

* Empfänger in Campaign v7, die nach Campaign Standard repliziert wurden
* Benutzerrechte zur Durchführung von Workflows in sowohl Campaign v7 als auch Campaign Standard
* Benutzerrechte zur Erstellung und Durchführung eines Versands in Campaign Standard

## Abmelde-Link ändern {#changing-the-unsubscription-link}

Wenn ein Empfänger in einer von Campaign Standard gesendeten E-Mail einen Abmelde-Link anklickt, wird das entsprechende Profil in Campaign Standard aktualisiert. Um sicherzustellen, dass ein repliziertes Profil die Benutzerentscheidung enthält, sich von einem Dienst abzumelden, muss diese Information an Campaign v7 und nicht an Campaign Standard gesendet werden. Deshalb ist der Abmeldedienst zur Ausführung dieser Änderung mit einer Webanwendung von Campaign v7 verbunden, und nicht mit Campaign Standard.

>[!NOTE]
>
>Ersuchen Sie bitte Ihren Berater, die Webanwendung für den Abmeldedienst zu konfigurieren, bevor Sie die folgenden Schritte ausführen.

## Neuen Empfänger erstellen {#creating-a-new-recipient}

1. Erstellen Sie in Campaign v7 einen neuen Empfänger für die Replikation nach Campaign Standard. Geben Sie so viele Informationen wie möglich ein, einschließlich Nachname, Vorname, E-Mail-Adresse und Postanschrift des Empfängers. Wählen Sie jedoch keine **[!UICONTROL Anrede]** aus, da diese im nächsten Abschnitt [Empfänger bearbeiten](#editing-a-recipient) hinzugefügt wird. Weitere Informationen hierzu finden Sie unter [Empfänger hinzufügen](../../platform/using/adding-profiles.md).

   ![](assets/acs_connect_profile_sync_01.png)

1. Vergewissern Sie sich, dass der neue Empfänger in Campaign Standard hinzugefügt wurde. Achten Sie bei der Überprüfung des Profils darauf, dass die in Campaign v7 eingegebenen Daten auch in Campaign Standard verfügbar sind. Informationen darüber, wo Sie Profile in Campaign Standard ansehen können, finden Sie im Abschnitt [Navigationsprinzipien](https://docs.adobe.com/content/help/de-DE/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_02.png)

   Standardmäßig wird für den ACS Connector alle 15 Minuten eine Replikation durchgeführt. Weiterführende Informationen finden Sie unter [Datenreplikation](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Empfänger bearbeiten {#editing-a-recipient}

Die folgenden Schritte zum Ändern eines einzelnen Datenpunkts veranschaulichen auf einfache Weise, wie Campaign v7 bei Verwendung von Datenreplikation zur primären Datenbank für Campaign Standard wird. Das Ändern oder Löschen replizierter Daten in Campaign v7 hat dieselbe Wirkung auf die entsprechenden Daten in Campaign Standard.

1. Wählen Sie unter [Neuen Empfänger erstellen](#creating-a-new-recipient) den neu erstellten Empfänger aus und bearbeiten Sie seinen Namen. Wählen Sie beispielsweise eine **[!UICONTROL Anrede]** für den Empfänger (z. B. Herr oder Frau). Weitere Informationen finden Sie unter [Profile bearbeiten](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_03.png)

1. Vergewissern Sie sich, dass der Name des Empfängers in Campaign Standard aktualisiert wurde. Um zu erfahren, wo Sie die Profile in Campaign Standard finden, lesen Sie den Abschnitt [Navigationsprinzipien](https://docs.adobe.com/content/help/de-DE/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_04.png)

   Standardmäßig wird für den ACS Connector alle 15 Minuten eine Replikation durchgeführt. Weitere Informationen finden Sie unter [Datenreplikation](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Workflow erstellen    {#creating-a-workflow}

Marketer können die umfassenden von Campaign v7 replizierten Profile und Dienste in Campaign Standard nutzen. Die folgende Anleitung zeigt, wie eine Abfrage zu einem Campaign-Standard-Workflow hinzugefügt wird und mit der replizierten Datenbank genutzt wird.

Weiterführende Informationen und die vollständige Anleitung zu Campaign Standard-Workflows finden Sie im Abschnitt [Workflows](../../workflow/using/about-workflows.md).

1. Gehen Sie zu Campaign Standard und wählen Sie **[!UICONTROL Marketingaktivitäten]** aus.
1. Wählen Sie rechts oben **[!UICONTROL Erstellen]** aus.
1. Wählen Sie **[!UICONTROL Workflow]** aus.
1. Wählen Sie **[!UICONTROL Neuer Workflow]** und **[!UICONTROL Weiter]** aus.
1. Geben Sie im Feld **[!UICONTROL Titel]** einen Namen für den Workflow sowie nach Bedarf zusätzliche Informationen ein. Wählen Sie **[!UICONTROL Weiter]** aus.
1. Ziehen Sie aus dem Bereich **[!UICONTROL Zielgruppenbestimmung]** auf der linken Seite ein **[!UICONTROL Abfrage]**-Ziel in den Arbeitsbereich.

   ![](assets/acs_connect_profile_sync_05.png)

1. Wählen Sie mit einem Doppelklick die Aktivität **[!UICONTROL Abfrage]** aus und wählen Sie danach einen Parameter aus, der mit der replizierten Datenbank verwendet werden kann. Beispielsweise können Sie:

   * Ziehen Sie **[!UICONTROL Profile]** in den Arbeitsbereich. Wählen Sie über das Pulldown-Menü die Option **[!UICONTROL Ist erweiterungsfähige externe Ressource]** aus, um Profile zu finden, die von Campaign v7 repliziert wurden.
   * Schränken Sie die Zielgruppe weiter ein, indem Sie weitere Abfrageparameter in den Arbeitsbereich ziehen.

## Versanderstellung {#creating-a-delivery}

>[!NOTE]
>
>In der Anleitung zur Erstellung des Versands wird der Workflow fortgesetzt, der im Abschnitt ](#creating-a-workflow)Workflow erstellen[ begonnen wurde.

Marketer können mit einer Campaign v7-Webanwendung verifizieren, dass die Entscheidung eines Empfängers, sich von einem Dienst abzumelden, an die Datenbank von Campaign v7 gesendet wurde. Nachdem der Empfänger auf den Abmelde-Link geklickt hat, wird die Entscheidung, diesen Dienst nicht mehr in Anspruch zu nehmen, von Campaign v7 nach Campaign Standard repliziert. Weitere Informationen finden Sie unter [Abmelde-Link ändern](#changing-the-unsubscription-link).

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

1. Geben Sie im Feld **[!UICONTROL Titel]** einen Namen für den Versand und nach Bedarf weitere Informationen ein. Wählen Sie **[!UICONTROL Weiter]** aus.

   ![](assets/acs_connect_profile_sync_09.png)

1. Geben Sie im Feld **[!UICONTROL Betreff]** den Betreff ein, der im Posteingang des Empfängers angezeigt werden soll.
1. Wählen Sie **[!UICONTROL Inhalt wechseln]** aus, um eine HTML-Vorlage hinzuzufügen.

   ![](assets/acs_connect_profile_sync_10.png)

1. Wählen Sie einen Inhalt aus, der einen Abmelde-Link enthält. Wählen Sie **[!UICONTROL Bestätigen]** aus.

   ![](assets/acs_connect_profile_sync_11.png)

1. Der aktuelle Abmelde-Link muss durch einen neuen ersetzt werden, der auf die von Ihrem Consultant erstellte Webanwendung verweist. Gehen Sie zum Abmelde-Link am unteren Ende der E-Mail und wählen Sie ihn durch einen Einfachklick aus. Wählen Sie dann das Papierkorbsymbol aus, um den Link zu entfernen.

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

1. Wählen Sie **[!UICONTROL Starten]** aus, um den Versand durchzuführen. Das blinkende E-Mail-Versand-Symbol zeigt an, dass der Versand vorbereitet wird.

   ![](assets/acs_connect_profile_sync_18.png)

1. Wählen Sie mit einem Doppelklick den Kanal **[!UICONTROL E-Mail-Versand]** aus. Wählen Sie danach **[!UICONTROL Bestätigen]** und **[!UICONTROL OK]** aus, um die Nachrichten zu senden.

   ![](assets/acs_connect_profile_sync_19.png)

## Abmeldedienst verifizieren {#verifying-the-unsubscription-service}

Befolgen Sie die Anweisungen unter [Workflow erstellen](#creating-a-workflow) und [Versand erstellen](#creating-a-delivery), bevor Sie mit den unten stehenden Schritten fortfahren.

1. Der Empfänger klickt auf den Abmelde-Link in der E-Mail.

   ![](assets/acs_connect_profile_sync_20.png)

1. Der Empfänger bestätigt die Abmeldung.

   ![](assets/acs_connect_profile_sync_21.png)

1. Die Empfängerdaten in Campaign v7 werden entsprechend aktualisiert. Bestätigen Sie, dass das Feld **[!UICONTROL Nicht mehr kontaktieren (alle Kanäle)]** für den Empfänger aktiviert ist. Wie Sie einen Empfänger in Campaign v7 aufrufen können, finden Sie unter [Profile bearbeiten](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_22.png)

1. Gehen Sie zu Campaign Standard und öffnen Sie die Profildetails des Empfängers. Vergewissern Sie sich, dass **[!UICONTROL Nicht mehr kontaktieren (alle Kanäle)]** ein Häkchen aufweist. Informationen darüber, wo Sie sich in Campaign Standard Profile ansehen können, finden Sie in [Navigationsprinzipien](https://docs.adobe.com/content/help/de-DE/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_23.png)

