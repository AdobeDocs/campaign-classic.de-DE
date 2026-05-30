---
product: campaign
title: Konfigurieren und Durchführen des Versands
description: Erfahren Sie, wie Sie den Versand konfigurieren und versenden
feature: Channel Configuration
role: User
hide: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
TQID: https://experienceleague.adobe.com/-Wh-pHFGE1kTId3t6g7wVJFfSvh2W5ERHi2K5-0Ohdw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 1649
ht-degree: 90%

---

# Konfigurieren und Durchführen des Versands {#configuring-and-sending-the-delivery}

## Berechtigungen{#delivery-permissions}

Nur die für einen Versand verantwortliche Person kann den Versand starten. Damit andere Benutzende (oder Benutzergruppen) einen Versand starten können, fügen Sie diese als Validierungsverantwortliche im Feld **[!UICONTROL Versandstart:]** hinzu. [Weitere Informationen](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Zusätzliche Versandparameter {#delivery-additiona-parameters}

Vor der Durchführung des Versands können Sie im Tab **[!UICONTROL Versand]** die Parameter der Versandeigenschaften definieren.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Versandpriorität]**: Diese Option ermöglicht es Ihnen, die Versandreihenfolge für Ihre Sendungen durch Angabe der Prioritätsstufe (normal, hoch oder niedrig) zu ändern.

* **[!UICONTROL Kontingentgröße]**: Mithilfe dieser Option können Sie die Anzahl der in einem XML-Versand-Package enthaltenen Nachrichten festlegen. Wenn der Parameter auf „0“ gesetzt ist, werden die Nachrichten automatisch gruppiert. Die Package-Größe wird durch die `<delivery size>/1024`-Berechnung definiert, mit mindestens 8 und maximal 256 Nachrichten pro Package.

  >[!IMPORTANT]
  >
  >Wenn der Versand durch Duplizieren eines existierenden Versands erstellt wird, wird dieser Parameter zurückgesetzt.

* **[!UICONTROL In mehreren Schüben versenden]**: Verwenden Sie diese Option, um Ihre Nachrichten in mehreren Schüben anstatt gleichzeitig zu versenden. [Weitere Informationen](#sending-using-multiple-waves).

* **[!UICONTROL SMTP-Versand testen]**: Verwenden Sie diese Option, um den Versand per SMTP zu testen. Der Versand wird bis zur Verbindung mit dem SMTP-Server verarbeitet, aber nicht gesendet: Für jeden Empfänger des Versands stellt Campaign eine Verbindung mit dem Server des SMTP-Anbieters her, führt den SMTP-Befehl RCPT TO aus und schließt die Verbindung vor dem SMTP-Befehl DATA.

  >[!NOTE]
  >
  >* Diese Option darf bei Mid-Sourcing nicht festgelegt werden.
  >
  >* Weitere Informationen zur SMTP-Server-Konfiguration finden Sie in [diesem Abschnitt](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL E-Mail-BCC]**: Mit dieser Option können Sie mit der BCC-Funktion E-Mails in einem externen System speichern, indem Sie einfach eine E-Mail-Adresse als BCC zu Ihrer Versandzielgruppe hinzufügen. [Weitere Informationen](sending-messages.md#archiving-emails).

## Bestätigen des Versands {#confirming-delivery}

Wenn der Versand konfiguriert und versandbereit ist, führen Sie die Versandanalyse aus.

Klicken Sie dazu auf **[!UICONTROL Senden]**, wählen Sie die gewünschte Aktion aus und klicken Sie auf **[!UICONTROL Analysieren]**. [Weitere Informationen](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Klicken Sie abschließend auf **[!UICONTROL Versand bestätigen]**, um den Versand der Nachrichten zu starten.

Nun können Sie den Versandassistenten schließen und die Durchführung auf der Registerkarte **[!UICONTROL Versand]** verfolgen (entweder in der Detailansicht des Versands oder in der Versandliste).

Nach dem Nachrichtenversand können Sie Ihre Sendungen überwachen und verfolgen. Lesen Sie diesbezüglich auch diese Abschnitte:

* [Überwachen von Sendungen](about-delivery-monitoring.md)
* [Ursachen für das Fehlschlagen von Sendungen](delivery-failures-quarantine.md)
* [Über das Nachrichten-Tracking](about-message-tracking.md)

## Planen des Versandzeitpunkts {#scheduling-the-delivery-sending}

Sie können den Nachrichtenversand verzögern, indem Sie für den Versand einen Zeitpunkt planen.

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Senden]** und wählen Sie die Option **[!UICONTROL Versand terminieren]** aus.

1. Geben Sie im Feld **[!UICONTROL Kontaktdatum]** das gewünschte Startdatum an.

![](assets/dlv_email_del_plan.png)

1. Sie können dann die Versandanalyse starten und den Versand bestätigen. Der Versand beginnt jedoch erst nach dem im Feld **[!UICONTROL Kontaktdatum]** angegebenen Datum.

>[!IMPORTANT]
>
>Sobald Sie die Analyse gestartet haben, wird das von Ihnen definierte Kontaktdatum fixiert. Wenn Sie dieses Datum ändern, müssen Sie die Analyse neu starten, damit Ihre Änderungen berücksichtigt werden.

![](assets/s_ncs_user_email_del_start_delayed.png)

In der Liste aller Sendungen erscheint der Versand mit dem Status **[!UICONTROL Ausstehend]**.

![](assets/s_ncs_user_email_del_waiting.png)

Die Terminierung kann auch vorab über die Schaltfläche **[!UICONTROL Planung]** erfolgen.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Dies bietet die Möglichkeit, den Versand auf einen späteren Zeitpunkt zu verschieben und ihn im Planungskalender zu verzeichnen.

* Bei Wahl der Option **[!UICONTROL Versand planen (keine automatische Ausführung)]** können Sie zudem die Analyse des Versands terminieren.

  Wenn diese Konfiguration gespeichert wird, ändert sich der Versand in den Status **[!UICONTROL Targeting ausstehend]**. Die Analyse wird am angegebenen Datum gestartet.

* Bei Wahl der Option **[!UICONTROL Versand planen (automatische Ausführung am geplanten Datum)]** wird nur das Kontaktdatum angegeben.

  Klicken Sie auf **[!UICONTROL Senden]** und wählen Sie **[!UICONTROL Versand]**, starten Sie dann die Analyse und bestätigen Sie den Versand. Wenn die Analyse abgeschlossen ist, ist die Versandzielgruppe bereit und die Nachrichten werden automatisch am angegebenen Datum gesendet.

Datum und Uhrzeit beziehen sich jeweils auf den aktuellen Benutzer. Die unter dem Eingabefeld des Kontaktdatums situierte Dropdown-Liste **[!UICONTROL Zeitzone]** ermöglicht es, die oberhalb eingegebene Uhrzeit der ausgewählten Zeitzone anzupassen.

Wenn Sie also beispielsweise einen Versand für 8 Uhr Brüsseler Zeit terminieren, wird die Uhrzeit automatisch in die ausgewählte Zeitzone konvertiert:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Versenden in mehreren Schüben {#sending-using-multiple-waves}

Um die Auslastung auszugleichen, können Sie Sendungen in mehrere Batches unterteilen. Konfigurieren Sie die Anzahl der Batches und ihre Größe in Bezug auf den gesamten Versand.

>[!NOTE]
>
>Sie können nur die Größe und die Verzögerung zwischen zwei aufeinander folgenden Schüben definieren. Die Empfängerauswahlkriterien für jede Welle können nicht konfiguriert werden.

1. Öffnen Sie das Versandeigenschaftenfenster und wählen Sie den **[!UICONTROL Versand]**-Tab aus.
1. Wählen Sie die Option **[!UICONTROL In mehreren Schüben versenden]** aus und danach den Link **[!UICONTROL Definition der Schübe...]**.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Zur Konfiguration von Schüben haben Sie die folgenden Möglichkeiten:

   * Definieren Sie die Größe eines jeden Schubs. Wenn Sie beispielsweise im entsprechenden Feld **[!UICONTROL 30 %]** eingeben, enthält jeder Schub 30 % der Versandnachrichten und der letzte Schub 10 % der Nachrichten.

     Geben Sie im Feld **[!UICONTROL Zeitraum]** die Verzögerung zwischen dem Start zweier aufeinanderfolgender Schübe an. Wenn Sie zum Beispiel **[!UICONTROL 2d]** eingeben, startet der erste Schub sofort, der zweite Schub startet in zwei Tagen, der dritte in vier Tagen usw.

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definieren Sie einen Kalendereintrag für den Versand eines jeden Schubs.

     Geben Sie in der Spalte **[!UICONTROL Start]** die Verzögerung zwischen dem Start zweier aufeinanderfolgender Schübe an. Geben Sie in der Spalte **[!UICONTROL Größe]** eine feste Zahl oder einen Prozentsatz ein.

     Im folgenden Beispiel stellt die erste Welle 25 % der Gesamtzahl der im Versand enthaltenen Nachrichten dar und beginnt sofort. Die beiden nächsten Schübe vervollständigen den Versand und starten in Sechs-Stunden-Intervallen.

     ![](assets/s_ncs_user_wizard_waves_create.png)

   Eine spezifische Typologieregel (**[!UICONTROL Prüfung der Schub-Planung]**) stellt sicher, dass der letzte Schub vor der Versand-Deadline eingeplant ist. Kampagnentypologien und die entsprechenden Regeln werden im Tab **[!UICONTROL Typologie]** der Versandeigenschaften konfiguriert und in [Validierung mit Typologien](steps-validating-the-delivery.md#validation-process-with-typologies) dargestellt.

   >[!IMPORTANT]
   >
   >Stellen Sie sicher, dass die letzten Schübe die Versandfrist nicht überschreiten, die auf der Registerkarte **[!UICONTROL Gültigkeit]** definiert ist. Andernfalls werden einige Nachrichten möglicherweise nicht gesendet.
   >
   >Planen Sie bei der Konfiguration der letzten Schübe auch genügend Zeit für zusätzliche Versuche ein. Siehe [diesen Abschnitt](steps-sending-the-delivery.md#configuring-retries).

1. Gehen Sie zur Überwachung Ihrer Sendungen zu den Versandlogs. Weitere Informationen finden Sie auf [dieser Seite](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"}.

   Die Versandlogs enthalten die bereits in den verarbeiteten Schüben durchgeführten Sendungen (Status **[!UICONTROL Gesendet]**) sowie die in den restlichen Schüben durchzuführenden Sendungen (Status **[!UICONTROL Ausstehend]**).

Im Folgenden finden Sie die häufigsten Anwendungsbeispiele für Schübe.

* **In der Anfangsphase**

  Wenn E-Mails über eine neue Plattform versendet werden, sind ISPs normalerweise misstrauisch gegenüber den neuen IP-Adressen. Das plötzliche Versenden großer Mengen an E-Mails veranlasst ISPs oft dazu, sie als Spam zu qualifizieren.

  Um zu vermeiden, dass Sie als Spam gekennzeichnet werden, können Sie die Anzahl der über Wellen gesendeten Nachrichten schrittweise erhöhen. Dies gewährleistet eine reibungslose Anlaufphase, da die Gesamtrate ungültiger Adressen verringert wird.

  Verwenden Sie dazu die Option **[!UICONTROL Schübe in einem Kalender definieren]**. Wählen Sie beispielsweise für den ersten Schub 10 %, für den zweiten 15 % usw. aus.

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Kampagnen, die ein Callcenter beinhalten**

  Bei telefonischen Treuekampagnen haben Unternehmen oft nur begrenzte Kapazitäten, um Abonnierende anzurufen.

  Mithilfe von Schüben kann die Anzahl der Nachrichten beispielsweise auf 20 pro Tag beschränkt werden, sofern dies der täglichen Verarbeitungskapazität eines Callcenters entspricht.

  Wählen Sie dazu die Option **[!UICONTROL Mehrere Schübe derselben Größe planen]**. Geben Sie **[!UICONTROL 20]** als Schubgröße und **[!UICONTROL 1d]** im Feld **[!UICONTROL Zeitraum]** ein.

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Konfigurieren der weiteren Zustellversuche {#configuring-retries}

Vorübergehend nicht zustellbare Nachrichten aufgrund eines **Softbounce** oder eines **ignorierten Fehlers** werden automatisch für einen erneuten Versuch vorgesehen. Die Typen und Ursachen für fehlgeschlagene Sendungen finden Sie in diesem [Abschnitt](delivery-failures-quarantine.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Bei gehosteten oder hybriden Installationen werden die Einstellungen für den erneuten Versuch im Versand nicht mehr von Campaign verwendet, wenn Sie auf den [Enhanced MTA](sending-with-enhanced-mta.md) aktualisiert haben. Weitere Zustellversuche aufgrund von Softbounces sowie die Zeitdauer zwischen ihnen werden durch den Enhanced MTA bestimmt, basierend auf Typ und Prioritätsstufe der Bounce-Antworten, die von der E-Mail-Domain der Nachricht zurückgegeben werden.

Bei On-Premise-Installationen und gehosteten/hybriden Installationen, die den bestehenden Campaign-MTA verwenden, gibt der zentrale Abschnitt der Registerkarte **[!UICONTROL Versand]** für die Versandparameter an, wie viele weitere Versuche am Tag nach dem Versand durchgeführt werden sollen, und den Mindestzeitabstand zwischen den Versuchen.

![](assets/s_ncs_user_wizard_retry_param.png)

Standardmäßig sind innerhalb der ersten 24 Stunden des Versands fünf erneute Versuche im Abstand von mindestens einer Stunde vorgesehen. An den folgenden Tagen wird bis zum Ablauf der Versandgültigkeit, die auf der Registerkarte **[!UICONTROL Gültigkeit]** festgelegt wird, jeweils ein Zustellversuch unternommen. Siehe [Definieren des Gültigkeitszeitraums](#defining-validity-period).

## Definieren des Gültigkeitszeitraums {#defining-validity-period}

Nach dem Start des Versands können die Nachrichten (und alle weiteren Zustellversuche) bis zum Ablauf der Versandgültigkeit gesendet werden. Dies wird auf der Registerkarte **[!UICONTROL Gültigkeit]** der Versandeigenschaften festgelegt.

![](assets/s_ncs_user_email_del_valid_period.png)

* Im Feld **[!UICONTROL Versandlaufzeit]** kann die Zeitspanne angegeben werden, in der weitere globale Zustellversuche unternommen werden. Dies bedeutet, dass Adobe Campaign die Nachrichten ab dem Startdatum versendet und dann nur für Nachrichten, die einen Fehler zurückgeben, regelmäßige, konfigurierbare weitere Zustellversuche durchführt, bis die Gültigkeitsgrenze erreicht ist.

  Sie können alternativ auch ein genaues Datum angeben. Markieren Sie dazu die Option **[!UICONTROL Gültigkeit explizit festlegen]**. In diesem Fall kann mit den Versand- und Gültigkeitsdaten auch eine bestimmte Uhrzeit konfiguriert werden. Standardmäßig wird die aktuelle Uhrzeit eingesetzt, sie kann jedoch direkt im Eingabefeld angepasst werden.

  >[!IMPORTANT]
  >
  >Wenn Sie auf den [Enhanced MTA](sending-with-enhanced-mta.md) aktualisiert haben, wird bei gehosteten oder hybriden Installationen die Einstellung **[!UICONTROL Versandlaufzeit]** in Ihren Campaign-E-Mail-Sendungen nur verwendet, wenn sie auf **3,5 Tage oder weniger** festgelegt ist. Wenn Sie einen Wert von mehr als 3,5 Tagen definieren, wird dieser nicht berücksichtigt.

* **Gültigkeit von Ressourcen**: Das Feld **[!UICONTROL Gültigkeit]** wird für hochgeladene Ressourcen verwendet, hauptsächlich für die Mirrorseite und Bilder. Die Gültigkeitsdauer der Ressourcen auf dieser Seite ist begrenzt, um Speicherkapazität zu sparen.

  Die Werte in diesem Feld können in den folgenden Einheiten ausgedrückt werden: **s** für Sekunden, **m** für Minuten, **h** für Stunden, **d** für Tage (Standard), **y** für Jahre.
