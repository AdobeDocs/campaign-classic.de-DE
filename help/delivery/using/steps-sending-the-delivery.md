---
title: Versand konfigurieren und senden
seo-title: Versand konfigurieren und senden
description: Versand konfigurieren und senden
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 631e29bd6e59b8ae46084dee3a1d470916a2032b

---


# Versand konfigurieren und senden {#configuring-and-sending-the-delivery}

>[!NOTE]
>
>Nur der Versand-Inhaber kann einen Versand Beginn haben. Damit ein anderer Operator (oder eine andere Operatorgruppe) einen Versand Beginn ausführen kann, müssen Sie ihn als Überprüfer im **[!UICONTROL Delivery start:]** Feld hinzufügen.
>
>Weitere Informationen dazu finden Sie in [diesem Abschnitt](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Zusätzliche Versandparameter {#delivery-additiona-parameters}

Before sending the delivery, you can define the sending parameters in the delivery properties, via the **[!UICONTROL Delivery]** tab.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: Mit dieser Option haben Sie die Möglichkeit, die Reihenfolge Ihrer Sendungen zu beeinflussen, indem Sie eine Versandpriorität (normal, hoch oder niedrig) festlegen. Auf diese Weise werden dringende Sendungen vorrangig ausgeführt.

* **[!UICONTROL Message batch quantity]**: Mithilfe dieser Option können Sie die Anzahl der in einem XML-Sendekontingent enthaltenen Nachrichten festlegen. Wenn der Parameter auf „0“ gesetzt ist, werden die Nachrichten automatisch gruppiert. Die Package-Größe wird durch die `<delivery size>/1024`-Berechnung definiert, mit mindestens 8 und maximal 256 Nachrichten pro Package.

   >[!CAUTION]
   >
   >Bei Duplizierung eines Versands wird dieser Parameter automatisch auf 0 zurückgesetzt.

* **[!UICONTROL Send using multiple waves]**: Weitere Informationen finden Sie unter [Senden mit mehreren Schüben](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: Mithilfe dieser Option können Sie das Senden über SMTP testen. Der Versand wird bis zur Verbindung mit dem SMTP-Server vorbereitet aber nicht abgeschickt.

   >[!NOTE]
   >
   >Bei Mid-Sourcing-Installationen ist von der Verwendung dieser Option abzuraten, damit der MTA nicht aufgerufen wird.
   >
   >Weiterführende Informationen zur Konfiguration eines SMTP-Servers finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* **[!UICONTROL Archive emails]**: Mit dieser Option können Sie E-Mails auf einem externen System über BCC speichern, indem Sie einfach eine BCC-E-Mail-Adresse zu Ihrer Zielgruppe hinzufügen. Weitere Informationen hierzu finden Sie unter [E-Mails archivieren](../../delivery/using/sending-messages.md#archiving-emails).

Nachdem der Versand konfiguriert wurde und versandbereit ist, stellen Sie sicher, dass Sie die [Versandanalyse](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)ausgeführt haben. Once done, click **[!UICONTROL Confirm delivery]** to launch the delivery of messages.

![](assets/s_ncs_user_email_del_send.png)

You can then close the delivery wizard and track the execution of the delivery from the **[!UICONTROL Delivery]** tab, accessible via the detail of this delivery or via the list of deliveries.

Nach Absenden der Nachrichten können Sie den Versand beobachten und verfolgen, siehe diese Abschnitte:

* [Sendungen beobachten](../../delivery/using/monitoring-a-delivery.md)
* [Ursachen von fehlgeschlagenen Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Über das Nachrichten-Tracking](../../delivery/using/about-message-tracking.md)

## Versandzeitpunkt planen {#scheduling-the-delivery-sending}

Sie können das Senden der Nachrichten auf einen späteren Zeitpunkt verschieben, um z. B. den Werbedruck auf eine bestimmte Population zu kontrollieren.

1. Klicken Sie auf die **[!UICONTROL Send]** Schaltfläche und wählen Sie die **[!UICONTROL Postpone delivery]** Option aus.

1. Specify a start date in the **[!UICONTROL Contact date]** field.

![](assets/dlv_email_del_plan.png)

1. Sie können dann die Versandanalyse starten und den Versand bestätigen. However, the delivery sending will not start until the date given in the **[!UICONTROL Contact date]** field.

>[!CAUTION]
>
>Sobald Sie die Analyse gestartet haben, steht das von Ihnen definierte Kontaktdatum fest. Sollten Sie dieses Datum abändern, ist darauf zu achten, die Analyse erneut zu starten, damit Ihre Änderungen berücksichtigt werden.

![](assets/s_ncs_user_email_del_start_delayed.png)

In the delivery list, the delivery will appear with **[!UICONTROL Pending]** status.

![](assets/s_ncs_user_email_del_waiting.png)

Scheduling can also be configured upstream via the **[!UICONTROL Scheduling]** button of the delivery.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Dies bietet die Möglichkeit, den Versand auf einen späteren Zeitpunkt zu verschieben und ihn im Planungskalender zu verzeichnen.

* Mit dieser **[!UICONTROL Schedule delivery (no automatic execution)]** Option können Sie eine vorläufige Analyse des Versands planen.

   Wenn diese Konfiguration gespeichert wird, ändert sich der Versand in den **[!UICONTROL Targeting pending]** Status. Die Analyse wird am angegebenen Datum gestartet.

* Mit dieser **[!UICONTROL Schedule delivery (automatic execution on planned date)]** Option können Sie das Datum des Versands angeben.

   Klicken Sie auf **[!UICONTROL Send]** und wählen Sie **[!UICONTROL Postpone delivery]** dann die Analyse aus und bestätigen Sie den Versand. Wenn die Analyse abgeschlossen ist, ist die Zielgruppe des Versands fertig und die Meldungen werden automatisch am angegebenen Datum gesendet.

Datum und Uhrzeit werden in der Zeitzone des aktuellen Operators angegeben. Mit der **[!UICONTROL Time zone]** Dropdown-Liste unterhalb des Eingabefelds für das Kontaktdatum können Sie das eingegebene Datum und die eingegebene Uhrzeit automatisch in die ausgewählte Zeitzone konvertieren.

Wenn Sie also beispielsweise einen Versand für 8 Uhr Brüsseler Zeit terminieren, wird die Uhrzeit automatisch in die ausgewählte Zeitzone konvertiert:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## In mehreren Schüben versenden {#sending-using-multiple-waves}

Um eine gleichmäßige Auslastung der Kapazitäten zu gewährleisten, können Sie Sendungen in mehrere Schübe unterteilen. Konfigurieren Sie die Anzahl der Schübe und ihre Größe in Bezug auf den gesamten Versand.

>[!NOTE]
>
>Sie können nur die Größe und die Zeitverzögerung zwischen zwei aufeinanderfolgenden Schüben definieren. Die Empfängerauswahlkriterien für jeden Schub können nicht konfiguriert werden.

1. Open the delivery properties window and click the **[!UICONTROL Delivery]** tab.
1. Wählen Sie die **[!UICONTROL Send using multiple waves]** Option aus und klicken Sie auf den **[!UICONTROL Define waves...]** Link.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Zur Konfiguration von Schüben haben Sie die folgenden Möglichkeiten:

   * Definieren Sie die Größe für jede Welle. For example, if you enter **[!UICONTROL 30%]** in the corresponding field, each wave will represent 30% of the messages included in the delivery, except the last one, which will represent 10% of the messages.

      Geben Sie im **[!UICONTROL Period]** Feld die Verzögerung zwischen dem Beginn von zwei aufeinander folgenden Schüben an. Wenn Sie z. B. **[!UICONTROL 2d]** eintreten, wird die erste Welle sofort Beginn, die zweite in zwei Tagen, die dritte in vier Tagen usw.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definieren Sie einen Kalendereintrag für den Versand eines jeden Schubs.

      Geben Sie in der **[!UICONTROL Start]** Spalte die Verzögerung zwischen dem Beginn von zwei aufeinander folgenden Schüben an. Geben Sie in die **[!UICONTROL Size]** Spalte eine feste Zahl oder einen Prozentwert ein.

      Im unten stehenden Beispiel beinhaltet der erste Schub 25 % der Gesamtzahl der im Versand enthaltenen Nachrichten und beginnt unmittelbar. Die nächsten beiden Schübe vervollständigen den Versand und starten in Intervallen von je sechs Stunden.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   A specific typology rule, **[!UICONTROL Wave scheduling check]**, ensures that the last wave is planned before the delivery validity limit. Campaign typologies and their rules, configured in the **[!UICONTROL Typology]** tab of the delivery properties, are presented in [Validation process with typologies](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!CAUTION]
   >
   >Vergewissern Sie sich, dass die letzten Schübe den in der **[!UICONTROL Validity]** Registerkarte festgelegten Termin für den Versand nicht überschreiten. Andernfalls werden einige Nachrichten möglicherweise nicht gesendet.
   >
   >Planen Sie bei der Konfiguration der letzten Schübe auch genügend Zeit für zusätzliche Versuche ein. Siehe [diesen Abschnitt](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).

1. Gehen Sie zur Überwachung Ihrer Sendungen zu den Versandlogs. Näheres hierzu finden Sie auf [dieser Seite](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history).

   You can see the deliveries that were already sent in the processed waves (**[!UICONTROL Sent]** status) and the deliveries to be sent in the remaining waves (**[!UICONTROL Pending]** status).

Im Folgenden finden Sie die häufigsten Anwendungsbeispiele für Schübe.

* **In der Anfangsphase**

   Wenn E-Mails über eine neue Plattform versendet werden, sind ISPs normalerweise misstrauisch gegenüber den neuen IP-Adressen. Das plötzliche Versenden großer Mengen an E-Mails veranlasst ISPs oft dazu, sie als Spam zu qualifizieren.

   Um zu verhindern, dass Ihre Sendungen als Spam eingestuft werden, können Sie das gesendete Volumen schrittweise mithilfe von Schüben erhöhen. Damit gewährleisten Sie eine problemlose Entwicklung in der Anfangsphase und die Verringerung der Anzahl der ungültigen Adressen.

   Verwenden Sie dazu die **[!UICONTROL Schedule waves according to a calendar]** Option. Legen Sie beispielsweise die erste Welle auf 10 %, die zweite auf 15 % usw. fest.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Kampagnen, die ein Callcenter beinhalten**

   Bei telefonischen Treuekampagnen verfügen Unternehmen oft über begrenzte Kapazitäten für die Verarbeitung der Anrufe an Abonnenten.

   Mithilfe von Schüben kann die Anzahl der Nachrichten auf 20 pro Tag beschränkt werden, was der täglichen Verarbeitungskapazität eines Callcenters entspricht.

   To do this, select the **[!UICONTROL Schedule multiple waves of the same size]** option. Geben Sie **[!UICONTROL 20]** als Größe der Welle und **[!UICONTROL 1d]** in das **[!UICONTROL Period]** Feld ein.

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Konfiguration weiterer Zustellversuche {#configuring-retries}

Vorübergehend nicht zustellbare Nachrichten aufgrund eines **Softbounce** oder eines **ignorierten Fehlers** werden automatisch für einen erneuten Versuch vorgesehen. Die Typen und Ursachen für fehlgeschlagene Sendungen finden Sie in diesem [Abschnitt](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

The central section of the **[!UICONTROL Delivery]** tab for delivery parameters indicates how many retries should be performed the day after the delivery and the minimum delay between retries.

![](assets/s_ncs_user_wizard_retry_param.png)

Standardmäßig sind innerhalb der ersten 24 Stunden des Versands fünf erneute Versuche im Abstand von mindestens einer Stunde vorgesehen. One retry per day is programmed after that and until the delivery deadline, which is defined in the **[!UICONTROL Validity]** tab (see [Defining validity period](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)).

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen werden die Einstellungen für den erneuten Versuch im Versand nicht mehr von Campaign verwendet, wenn Sie auf den Enhanced MTA aktualisiert haben. Versuche aufgrund von Softbounces und die Zeitdauer zwischen ihnen werden durch den Enhanced MTA bestimmt, basierend auf Typ und Prioritätsstufe der Bounce-Antworten, die von der E-Mail-Domain der Nachricht zurückgegeben werden.
>
>Alle Auswirkungen sind im Dokument [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) ausführlich beschrieben.


## Gültigkeitszeitraum bestimmen {#defining-validity-period}

Nach dem Start des Versands können die Nachrichten (und alle weitere Zustellversuche) bis zum Ablauf der Frist für den Versand gesendet werden. Dies wird in den Eigenschaften des Versands über die **[!UICONTROL Validity]** Registerkarte angezeigt.

![](assets/s_ncs_user_email_del_valid_period.png)

* Im **[!UICONTROL Delivery duration]** Feld können Sie die Beschränkung für weitere Zustellversuche globaler Versand eingeben. Das bedeutet, dass Adobe Campaign die Meldungen, die am Tag des Beginns beginnen, sendet. Bei Meldungen, die nur einen Fehler zurückgeben, werden regelmäßige, konfigurierbare weitere Zustellversuche ausgeführt, bis die Gültigkeit erreicht ist.

   Sie können auch Datumsangaben angeben. Wählen Sie dazu **[!UICONTROL Explicitly set validity dates]**. In diesem Fall können Sie mit dem Versand- und dem Datumsbereich der Gültigkeit auch die Uhrzeit angeben. Die aktuelle Zeit wird standardmäßig verwendet, Sie können dies jedoch direkt im Eingabefeld ändern.

* **Gültigkeit der Mittel**: Das **[!UICONTROL Validity limit]** Feld wird für hochgeladene Ressourcen verwendet, hauptsächlich für die Mirrorseite und Bilder. Die Gültigkeitsdauer der Ressourcen auf dieser Seite ist begrenzt, um Speicherkapazität zu sparen.

   Die in diesem Feld möglichen Zeiteinheiten (Tage, Stunden etc.) können Sie in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#default-units) nachlesen.

>[!NOTE]
>
>For hosted or hybrid installations, if you have upgraded to the Enhanced MTA, the **[!UICONTROL Delivery duration]** setting in your Campaign deliveries will be used only if set to **3.5** days or less. Wenn Sie einen Wert von mehr als 3,5 Tagen definieren, wird dieser nicht berücksichtigt.
>
>Alle Auswirkungen sind im Dokument [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) ausführlich beschrieben.
