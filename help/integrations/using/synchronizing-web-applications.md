---
title: Webanwendungen synchronisieren
seo-title: Webanwendungen synchronisieren
description: Webanwendungen synchronisieren
seo-description: null
page-status-flag: never-activated
uuid: da74e4d3-e439-454a-8a43-6784e4789d1b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: df68ab11-7a8b-4e89-8cc4-8764e8a859b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Webanwendungen synchronisieren{#synchronizing-web-applications}

In diesem Anwendungsbeispiel versenden wir eine Nachricht mit Campaign Standard, die einen Link zu einer Webanwendung von Campaign v7 enthält. Wenn der Empfänger den Link in der E-Mail anklickt, öffnet sich die Webanwendung mit einem Formular mit mehreren mit Empfängerdaten vorausgefüllten Feldern sowie einem Anmelde-Link zu einem Newsletter. Der Empfänger kann seine Daten aktualisieren und sich für den Dienst anmelden. Sein Profil wir in Campaign v7 aktualisiert und die Informationen werden nach Campaign Standard repliziert.

Wenn Sie über zahlreiche Dienste und Webanwendungen in Campaign v7 verfügen, ist es empfehlenswert, nicht alle nach Campaign Standard zu übertragen. ACS Connector ermöglicht Ihnen, alle bestehenden Campaign v7-Webanwendungen und -Dienste mit einem in Campaign Standard erstellten Versand zu verknüpfen.

## Voraussetzungen {#prerequisites}

Dazu ist Folgendes erforderlich:

* Empfänger, die in der Campaign v7-Datenbank gespeichert und mit Campaign Standard synchronisiert werden. Siehe Abschnitt [Synchronisierungsprofile](../../integrations/using/synchronizing-profiles.md) .
* Ein Dienst und eine Webanwendung, die in Campaign v7 erstellt und publiziert wurden.
* die Webanwendung muss eine **[!UICONTROL Pre-loading]** Aktivität mit der **[!UICONTROL Adobe Campaign encryption]** Identifizierungsmethode enthalten.

## Webanwendung und Dienst erstellen {#creating-the-web-application-and-service}

Sie können in Campaign v7 Webanwendungen erstellen, mit denen sich Empfänger für einen Dienst anmelden können. Die Webanwendung und der Dienst werden in Campaign v7 konzipiert und gespeichert und Sie können diesen Dienst über eine Campaign Standard-Kommunikation aktualisieren. Weiterführende Informationen zu Webanwendungen in Campaign v7 finden Sie in [diesem Abschnitt](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

In Campaign v7 wurden die folgenden Objekte erstellt:

* ein Newsletter-Dienst
* eine Webanwendung mit einer **[!UICONTROL Pre-loading]**, einer **[!UICONTROL Page]** und einer **[!UICONTROL Storage]** Aktivität.

1. Wählen Sie eine vorhandene Webanwendung **[!UICONTROL Resources > Online > Web applications]** aus.

   ![](assets/acs_connect_lp_2.png)

1. Bearbeiten Sie die **[!UICONTROL Preloading]** Aktivität. Das **[!UICONTROL Auto-load data referenced in the form]** Kästchen wird markiert und das **[!UICONTROL Adobe Campaign encryption]** Identifizierungsverfahren ausgewählt. Auf diese Weise kann die Webanwendung die Felder des Formulars im Voraus mit den in der Adobe Campaign-Datenbank gespeicherten Daten laden. Siehe [dieses Dokument](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Edit the **[!UICONTROL Page]**. Three fields (Name, Email and Phone) have been included, as well as a check box to invite the recipient to subscribe to a newsletter (**[!UICONTROL Newsletter]** service).

   ![](assets/acs_connect_lp_3.png)

1. Gehen Sie zu **[!UICONTROL Profiles and Target > Services and subscriptions]** und öffnen Sie den **[!UICONTROL Newsletter]** Dienst. Dies ist der Dienst, der von der Kommunikation mit Campaign Standard aktualisiert wird. Sie können sehen, dass noch kein Empfänger diesen Dienst abonniert hat.

   ![](assets/acs_connect_lp_5.png)

1. Wählen Sie einen Empfänger **[!UICONTROL Profiles and Targets > Recipient]** aus. Sie können sehen, dass er den Dienst noch nicht abonniert hat.

   ![](assets/acs_connect_lp_6.png)

## Daten replizieren {#replicating-the-data}

Um die erforderlichen Daten zwischen Campaign v7 und Campaign Standard zu replizieren, stehen verschiedene Vorlagen für den Replikationsarbeitsablauf zur Verfügung. Der **[!UICONTROL Profiles replication]** Arbeitsablauf repliziert automatisch alle Empfänger der Kampagne v7 in Campaign Standard. See [Technical and replication workflows](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). Der **[!UICONTROL Landing pages replication]** Arbeitsablauf ermöglicht die Replizierung der Webanwendungen, die wir in Campaign Standard verwenden möchten.

![](assets/acs_connect_lp_1.png)

Um zu überprüfen, ob die Daten korrekt repliziert wurden, gehen Sie in Campaign Standard folgendermaßen vor:

1. From the home screen, click on **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Suchen Sie nach Ihrem Campaign v7-Empfänger und vergewissern Sie sich, dass er in Campaign Standard angezeigt wird.

   ![](assets/acs_connect_lp_8.png)

1. Klicken Sie in der oberen Leiste auf **[!UICONTROL Marketing activities]** und suchen Sie die Webanwendung Campaign v7. Es wird als Landingpage in Campaign Standard angezeigt.

   ![](assets/acs_connect_lp_9.png)

1. Klicken Sie links oben auf das **[!UICONTROL Adobe Campaign]**-Logo, wählen Sie dann **Profiles &amp; Audiences > Dienste** aus und vergewissern Sie sich, dass auch der Newsletter-Dienst angezeigt wird.

   ![](assets/acs_connect_lp_10.png)

## E-Mail konzipieren und senden {#designing-and-sending-the-email}

In diesem Abschnitt erfahren Sie, wie in eine E-Mail in Campaign Standard ein Link eingefügt wird, der zu einer Landingpage weist, die von einer Campaign v7-Webanwendung repliziert wurde.

Die Schritte für die Erstellung, die Konzeption und den Versand der E-Mail erfolgen wie üblich. Siehe das [Adobe Campaign Standard](https://helpx.adobe.com/support/campaign/standard.html)-Handbuch.

1. Erstellen Sie eine neue E-Mail und wählen Sie mindestens ein repliziertes Profil als Zielgruppe.
1. Bearbeiten Sie den Inhalt und fügen Sie eine **[!UICONTROL Link to a landing page]** ein.

   ![](assets/acs_connect_lp_12.png)

1. Wählen Sie die von der Campaign v7-Webanwendung replizierte Landingpage aus.

   ![](assets/acs_connect_lp_13.png)

1. Stellen Sie Ihre E-Mail zusammen, führen Sie Testsendungen durch und senden Sie die endgültige E-Mail.
1. Einer der Empfänger öffnet die E-Mail und klickt auf den Link zur Newsletter-Anmeldung.

   ![](assets/acs_connect_lp_14.png)

1. Er gibt eine Telefonnummer ein und fügt dem Kästchen zur Newsletter-Anmeldung ein Häkchen hinzu.

   ![](assets/acs_connect_lp_15.png)

## Aktualisierte Daten abrufen {#retrieving-the-updated-information}

Wenn der Empfänger seine Daten über die Webanwendung aktualisiert, ruft Adobe Campaign v7 synchron die aktualisierten Daten ab. Diese werden anschließend von Campaign v7 nach Campaign Standard repliziert.

1. Wechseln Sie in Campaign v7 zu **[!UICONTROL Profiles and Target > Services and subscriptions]** und öffnen Sie den **[!UICONTROL Newsletter]** Dienst. Sie können sehen, dass der Empfänger jetzt in der Abonnentenliste angezeigt wird.

   ![](assets/acs_connect_lp_16.png)

1. Wählen Sie den Empfänger **[!UICONTROL Profiles and Targets > Recipient]** aus. Sie können sehen, dass die Telefonnummer jetzt gespeichert ist.

   ![](assets/acs_connect_lp_17.png)

1. In the **[!UICONTROL Subscriptions]** tab, we can also see that he has subscribed to the newsletter service.

   ![](assets/acs_connect_lp_18.png)

1. Warten Sie ein paar Minuten, bis der Profilreplikations-Workflow durchgeführt wurde.
1. Öffnen Sie in Campaign Standard das Empfängerprofil und überprüfen Sie, ob die aktualisierten Daten korrekt von Campaign v7 repliziert wurden.

   ![](assets/acs_connect_lp_19.png)

1. Bearbeiten Sie das Profil. Sie sehen, dass die Telefonnummer aktualisiert wurde.

   ![](assets/acs_connect_lp_20.png)

1. Klicken Sie auf die **[!UICONTROL Subscriptions]** Registerkarte. Der Newsletter-Dienst wird jetzt angezeigt.

   ![](assets/acs_connect_lp_21.png)

