---
product: campaign
title: E-Mail-Parameter
description: Erfahren Sie mehr zu den Optionen und Einstellungen, die spezifisch für den E-Mail-Versand sind
feature: Email
role: User, Developer
hide: true
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
TQID: https://experienceleague.adobe.com/MmKuHkMyqQizW9agSWTlcNOzrzG12TkBXcHVHjGvhxA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 998
ht-degree: 89%

---

# E-Mail-Parameter {#email-parameters}

In diesem Abschnitt finden Sie die Optionen und Parameter, die spezifisch für den E-Mail-Versand sind.

## E-Mail-BCC {#email-bcc}

In Adobe Campaign können Sie mit der BCC-Option E-Mails in einem externen System speichern, indem Sie einfach eine BCC-E-Mail-Adresse zu Ihrer Versandzielgruppe hinzufügen.

Sobald die Option aktiviert ist, wird eine exakte Kopie aller gesendeten Nachrichten für diesen Versand aufbewahrt.

Weiterführende Informationen zur E-Mail-BCC-Konfiguration und zu Best Practices finden Sie in [diesem Abschnitt](../../installation/using/email-archiving.md).

>[!NOTE]
>
>E-Mail-BCC ist eine optionale Funktion. Bitte prüfen Sie Ihren Lizenzvertrag und kontaktieren Sie den Ansprechpartner für Ihr Konto, um diese Funktion zu aktivieren.

Beim Erstellen eines neuen Versands oder einer neuen Versandvorlage ist E-Mail-BCC nicht standardmäßig aktiviert. Sie müssen die Funktion auf der E-Mail-Versand- oder Versandvorlagenebene manuell aktivieren.

>[!NOTE]
>
>Wenn Sie E-Mail-BCC mit [Enhanced MTA](sending-with-enhanced-mta.md) verwenden, ist diese Option automatisch für alle Sendungen aktiviert.

Gehen Sie wie folgt vor, um E-Mail-BCC für eine E-Mail-Versandvorlage zu aktivieren:

1. Gehen Sie zu **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]** oder **[!UICONTROL Ressourcen]** > **[!UICONTROL Vorlagen]** > **[!UICONTROL Versandvorlagen]**.
1. Wählen Sie den gewünschten Versand aus oder duplizieren Sie die Standardvorlage **E-Mail-Versand**, und wählen Sie dann die duplizierte Vorlage aus.
1. Wählen Sie die **Eigenschaften**-Schaltfläche aus.
1. Gehen Sie in den **[!UICONTROL Versand]**-Tab.
1. Aktivieren Sie die Option **E-Mail-BCC**. Eine Kopie aller gesendeten Nachrichten für jede Sendung, die auf dieser Vorlage basiert, wird an die dafür konfigurierte E-Mail-BCC-Adresse gesendet.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Wenn die an eine BCC-Adresse gesendeten E-Mails geöffnet und angeklickt werden, wird dies in der Versandanalyse in **[!UICONTROL Gesamtöffnungen]** und **[!UICONTROL Klicks]** berücksichtigt, was zu falschen Berechnungen führen könnte.

## Wahl des Nachrichtenformats {#selecting-message-formats}

Sie können das Format der gesendeten E-Mail-Nachrichten ändern. Bearbeiten Sie hierzu die Versandeigenschaften und klicken Sie auf die Registerkarte **[!UICONTROL Versand]**.

![](assets/s_ncs_user_wizard_email_param.png)

Im unteren Bereich des Fensters haben Sie die Wahl zwischen:

* **[!UICONTROL Empfängerangaben berücksichtigen]** (Standardmodus)

  Das Nachrichtenformat wird anhand der im Empfängerprofil gespeicherten Daten definiert und standardmäßig im Feld **[!UICONTROL E-Mail-Format]** gespeichert (@emailFormat). Falls ein Empfänger Nachrichten in einem bestimmten Format erhalten möchte, werden sie in diesem Format gesendet. Wenn das Feld nicht ausgefüllt ist, wird eine Multipart-Alternative-Nachricht gesendet (siehe unten).

* **[!UICONTROL E-Mail-Programm des Empfängers das beste Format wählen lassen]**

  Die Nachricht enthält beide Formate: Text und HTML. Welches Format beim Empfang angezeigt wird, hängt von der Konfiguration des E-Mail-Programms der Empfängerin bzw. des Empfängers ab (Multipart-Alternative).

  >[!IMPORTANT]
  >
  >Diese Option umfasst beide Versionen der Nachricht. Dies wirkt sich daher auf die Versandrate aus, da die Nachricht größer ist.

* **[!UICONTROL Alle Nachrichten im Textformat senden]**

  Die Nachricht wird im Textformat gesendet. Das HTML-Format wird nicht gesendet, sondern nur für die Mirrorseite verwendet, wenn der Empfänger auf die Nachricht klickt.

>[!NOTE]
>
>Weitere Informationen zum Definieren des E-Mail-Inhalts finden Sie in [diesem Abschnitt](defining-the-email-content.md).

## Erzeugen der Mirrorseite {#generating-mirror-page}

Die Mirrorseite ist eine HTML-Seite, auf die online über einen Webbrowser zugegriffen werden kann. Ihr Inhalt ist identisch mit dem der E-Mail.

Standardmäßig wird die Mirrorseite automatisch generiert, wenn der entsprechende Link in den Inhalt der E-Mail eingefügt wurde. Weitere Informationen zu Gestaltungsbausteinen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html?lang=de){target="_blank"}.

In den Versandeigenschaften kann die Erzeugung der Seite über das Feld **[!UICONTROL Modus]** im Tab **[!UICONTROL Gültigkeit]** konfiguriert werden.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>Zur Erzeugung einer Mirrorseite muss zuvor ein HTML-Versandinhalt erstellt worden sein.

Zusätzlich zum Standardmodus stehen die folgenden Optionen zur Verfügung:

* **[!UICONTROL Mirrorseitenerzeugung forcieren]**: Erstellt eine Mirror-Seite, selbst wenn im Versandinhalt kein entsprechender Link enthalten ist.
* **[!UICONTROL Keine Mirrorseite erzeugen]**: Erstellt keine Mirror-Seite, selbst wenn im Versandinhalt der entsprechende Link enthalten ist.
* **[!UICONTROL Von der Nachrichtenkennung aus zugängliche Mirrorseite erzeugen]**: Diese Option ermöglicht den Zugriff auf den Inhalt der Mirror-Seite einschließlich aller Personalisierungsinformationen von den Versandlogs aus. Klicken Sie hierfür nach Durchführung des Versands auf die Registerkarte **[!UICONTROL Versand]** und wählen Sie die Zeile des Empfängers aus, dessen Mirrorseite Sie ansehen möchten. Klicken Sie dann auf den Link **[!UICONTROL Mirrorseite dieser Nachricht anzeigen...]**.

  ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Zeichenkodierung {#character-encoding}

Auf dem Tab **[!UICONTROL SMTP]** der Versandparameter können Sie im Abschnitt **[!UICONTROL Zeichenkodierung]** eine bestimmte Kodierung festlegen.

Die Standardkodierung ist UTF-8. Wenn einige E-Mail-Anbieter Ihrer Empfänger keine UTF-8-Standardkodierung unterstützen, sollten Sie eine bestimmte Kodierung einrichten, sodass Sonderzeichen den Empfängern Ihrer E-Mails korrekt angezeigt werden.

Gehen wir davon aus, dass Sie eine E-Mail mit japanischen Zeichen versenden möchten. Um sicherzustellen, dass Ihren Empfängern in Japan alle Zeichen korrekt dargestellt werden, sollten Sie eine Kodierung verwenden, die anstelle der standardmäßigen UTF-8-Kodierung japanische Zeichen unterstützt.

Wählen Sie dazu die Option **[!UICONTROL Nachrichtenkodierung erzwingen (Codepage)]** im Abschnitt **[!UICONTROL Zeichenkodierung]** und wählen Sie eine Kodierung aus der angezeigten Dropdown-Liste.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Bounce Messages verwalten {#managing-bounce-emails}

Auf der Registerkarte **[!UICONTROL SMTP]** der Versandeigenschaften lässt sich der Umgang mit Bounce Messages konfigurieren.

Standardmäßig gehen Bounce Messages im [Standard-Fehlerpostfach der Plattform](../../installation/using/deploying-an-instance.md#parameters-for-delivered-emails-parameters-for-delivered-emails) ein. Es besteht jedoch die Möglichkeit, für einen Versand durch Abwählen der Standardoption eine spezifische Fehleradresse anzugeben.

Sie können eine weitere Adresse angeben, die es ermöglicht, die Unzustellbarkeitsursache derjenigen E-Mails zu untersuchen, bei denen das Programm sie nicht automatisch erkannt hat. Bei beiden Feldern können Sie durch Klick auf das entsprechende Symbol **Personalisierungsfelder hinzufügen**.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Weitere Informationen zur Bounce-Message-Verwaltung finden Sie in [diesem Abschnitt](delivery-failures-quarantine.md#bounce-mail-management).

## SMTP-Header hinzufügen {#adding-smtp-headers}

Sie können Ihren Sendungen auch SMTP-Header hinzufügen. Verwenden Sie dazu den entsprechenden Abschnitt der Registerkarte **[!UICONTROL SMTP]** im Versand.

Das in diesem Fenster eingegebene Skript muss pro Zeile einen Header im Format **Name:value** enthalten.

Werte werden bei Bedarf automatisch verschlüsselt.

>[!IMPORTANT]
>
>Das Hinzufügen eines Skripts zum Einfügen zusätzlicher SMTP-Header ist fortgeschrittenen Benutzern vorbehalten.
>
>Die Syntax des Scripts muss die Anforderungen für diesen Inhaltstyp (keine überflüssigen Leerzeichen, keine Leerzeilen usw.) erfüllen.
