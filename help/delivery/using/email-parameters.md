---
solution: Campaign Classic
product: campaign
title: E-Mail-Parameter in Adobe Campaign Classic konfigurieren
description: Erfahren Sie mehr zu den Optionen und Einstellungen, die spezifisch für E-Mail-Versand sind.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: e84387c7c396c60c429c3f625870a97a7fdaef5a
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 87%

---


# E-Mail-Parameter {#email-parameters}

Dieser Abschnitt enthält die Optionen und Parameter, die spezifisch für E-Mail-Versand sind.

## E-Mail-BCC {#email-bcc}

In Adobe Campaign können Sie mit der BCC-Option E-Mails in einem externen System speichern, indem Sie einfach eine BCC-E-Mail-Adresse zu ihrer Versandzielgruppe hinzufügen.

Sobald die Option aktiviert ist, wird eine genaue Kopie aller gesendeten Nachrichten für diesen Versand aufbewahrt.

Weiterführende Informationen zur E-Mail-BCC-Konfiguration und zu Best Practices finden Sie in [diesem Abschnitt](../../installation/using/email-archiving.md).

>[!NOTE]
>
>E-Mail-BCC ist eine optionale Funktion. Bitte prüfen Sie Ihren Lizenzvertrag und kontaktieren Sie den Ansprechpartner für Ihr Konto, um diese Funktion zu aktivieren.

Beim Erstellen eines neuen Versands oder einer neuen Versandvorlage ist E-Mail-BCC nicht standardmäßig aktiviert. Sie müssen sie manuell auf der Ebene des E-Mail-Versands oder der Versandvorlage aktivieren.

Gehen Sie wie folgt vor, um E-Mail-BCC für eine E-Mail-Versandvorlage zu aktivieren:

1. Gehen Sie zu **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Sendungen]** oder **[!UICONTROL Ressourcen]** > **[!UICONTROL Vorlagen]** > **[!UICONTROL Versandvorlagen]**.
1. Wählen Sie den gewünschten Versand aus oder duplizieren Sie die Standardvorlage **E-Mail-Versand**, und wählen Sie dann die duplizierte Vorlage aus.
1. Wählen Sie die **Eigenschaften**-Schaltfläche aus.
1. Gehen Sie in den **[!UICONTROL Versand]**-Tab.
1. Aktivieren Sie die Option **E-Mail-BCC**. Eine Kopie aller gesendeten Nachrichten für jede Sendung, die auf dieser Vorlage basiert, wird an die dafür konfigurierte E-Mail-BCC-Adresse gesendet.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Wenn die an eine BCC-Adresse gesendeten E-Mails geöffnet und angeklickt werden, wird dies in **[!UICONTROL Gesamtöffnungen]** und **[!UICONTROL Klicks]** der Versandanalyse berücksichtigt, was zu falschen Berechnungen führen könnte.

## Wahl des Nachrichtenformats {#selecting-message-formats}

Sie können das Format der zu versendenden E-Mails konfigurieren. Klicken Sie hierzu auf die Schaltfläche **[!UICONTROL Eigenschaften]** und begeben Sie sich in den Tab .

![](assets/s_ncs_user_wizard_email_param.png)

Im unteren Bereich des Fensters haben Sie die Wahl zwischen:

* **[!UICONTROL Empfängerangaben berücksichtigen]** (Standardmodus)

   Das Nachrichtenformat wird anhand der im Empfängerprofil im Feld **[!UICONTROL E-Mail-Format]** gespeicherten Informationen bestimmt. Wenn ein Empfänger ein bestimmtes Format angegeben hat, wird ihm die Nachricht in diesem Format zugestellt. Wenn das Feld leer ist, wird die Nachricht im Multipart-Alternative-Format versandt (siehe unten).

* **[!UICONTROL E-Mail-Programm des Empfängers das beste Format wählen lassen]**

   Die Nachricht enthält beide Formate: Text und HTML. Das beim Empfänger angezeigte Format hängt von der Konfiguration des E-Mail-Programms ab (Multipart-Alternative).

   >[!IMPORTANT]
   >
   >Bei dieser Option werden beide Versionen des Dokuments gesendet. Der hierdurch erhöhte Kapazitätsverbrauch kann den Versanddurchsatz beeinträchtigen.

* **[!UICONTROL Alle Nachrichten im Textformat senden]**

   Die Nachricht wird im Textformat gesendet. Das HTML-Format wird nicht gesendet, sondern nur für die Mirrorseite verwendet, auf die ein Empfänger gelangt, wenn er auf den entsprechenden Link in der Nachricht klickt.

>[!NOTE]
>
>Weitere Informationen zum Definieren des E-Mail-Inhalts finden Sie in [diesem Abschnitt](../../delivery/using/defining-the-email-content.md).

## Mirrorseite erstellen {#generating-mirror-page}

Eine Mirrorseite ist eine HTML-Seite, die über einen Webbrowser online abgerufen werden kann und deren Inhalt mit dem der E-Mail identisch ist.

Standardmäßig wird die Mirror­Seite automatisch generiert, wenn der entsprechende Link in den Inhalt der E-Mail eingefügt wurde. Weitere Informationen zum Einfügen von Gestaltungsbausteinen finden Sie unter [Gestaltungsbausteine](../../delivery/using/personalization-blocks.md).

In den Versandeigenschaften kann die Erzeugung der Seite über das Feld **[!UICONTROL Modus]** im Tab **[!UICONTROL Gültigkeit]** konfiguriert werden.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>Zur Erzeugung einer Mirrorseite muss zuvor ein HTML-Versandinhalt erstellt worden sein.

Außerdem stehen die folgenden Modi zur Verfügung:

* **[!UICONTROL Mirrorseitenerzeugung forcieren]**: Erstellt eine Mirrorseite, selbst wenn im Versandinhalt kein entsprechender Link enthalten ist.
* **[!UICONTROL Keine Mirrorseite erzeugen]**: Erstellt keine Mirrorseite, selbst wenn im Versandinhalt der entsprechende Link enthalten ist.
* **[!UICONTROL Von der Nachrichtenkennung aus zugängliche Mirrorseite erzeugen]**: Diese Option ermöglicht den Zugriff auf den Inhalt der Mirrorseite einschließlich aller Personalisierungsinformationen von den Versandlogs aus. Klicken Sie hierfür nach Durchführung des Versands auf den Tab **[!UICONTROL Versand]** und wählen Sie die Zeile des Empfängers aus, dessen Mirrorseite Sie ansehen möchten. Klicken Sie dann auf den Link **[!UICONTROL Mirrorseite dieser Nachricht anzeigen...]**.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Zeichenkodierung {#character-encoding}

Auf dem Tab **[!UICONTROL SMTP]** der Versandparameter können Sie im Abschnitt **[!UICONTROL Zeichenkodierung]** eine bestimmte Kodierung festlegen.

Die Standardkodierung ist UTF-8. Wenn einige E-Mail-Anbieter Ihrer Empfänger keine UTF-8-Standardkodierung unterstützen, sollten Sie eine bestimmte Kodierung einrichten, sodass Sonderzeichen den Empfängern Ihrer E-Mails korrekt angezeigt werden.

Gehen wir davon aus, dass Sie eine E-Mail mit japanischen Zeichen versenden möchten. Um sicherzustellen, dass Ihren Empfängern in Japan alle Zeichen korrekt dargestellt werden, sollten Sie eine Kodierung verwenden, die anstelle der standardmäßigen UTF-8-Kodierung japanische Zeichen unterstützt.

Wählen Sie dazu die Option **[!UICONTROL Nachrichtenkodierung erzwingen (Codepage)]** im Abschnitt **[!UICONTROL Zeichenkodierung]** und wählen Sie eine Kodierung aus der angezeigten Dropdown-Liste.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Bounce Messages verwalten {#managing-bounce-emails}

Im Tab **[!UICONTROL SMTP]** der Versandeigenschaften lässt sich der Umgang mit Bounce Messages konfigurieren.

Standardmäßig werden Bounce Messages an die im Softwareverteilungs-Assitenten der Plattform angegebene Fehleradresse gesendet. Es besteht jedoch die Möglichkeit, für einen Versand durch Abwählen der Standardoption eine spezifische Fehleradresse anzugeben.

Sie können auch eine bestimmte Adresse in diesem Bildschirm definieren, um die Gründe für Absprungmeldungen zu untersuchen, wenn diese nicht automatisch durch die Anwendung qualifiziert werden konnten. Mit dem Symbol **Hinzufügen personalisierten Feldern** können Sie für jedes dieser Felder Personalisierungsparameter hinzufügen.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Weitere Informationen zur Absprung-Mail-Verwaltung finden Sie in [diesem Abschnitt](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

## SMTP-Header hinzufügen {#adding-smtp-headers}

Sie haben die Möglichkeit, Ihren Sendungen weitere SMTP-Header hinzuzufügen. Gehen Sie hierfür in den Tab **[!UICONTROL SMTP]** in den Versandeigenschaften.

Das in diesem Fenster erfasste Script muss pro Zeile einen Header im Format **Name: Wert** enthalten.

Werte werden bei Bedarf automatisch verschlüsselt.

>[!IMPORTANT]
>
>Das Hinzufügen zusätzlicher SMTP-Header ist eine Aufgabe für erfahrene Benutzer.
>
>Die Syntax des Skripts muss die Anforderungen für diesen Inhaltstyp (keine überflüssigen Leerzeichen, keine Leerzeilen usw.) erfüllen.
