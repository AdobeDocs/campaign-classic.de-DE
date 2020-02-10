---
title: Senden einer E-Mail mit Adobe Campaign Classic
description: Erfahren Sie mehr über die Parameter, die für die Bereitstellung von E-Mails in Adobe Campaign Classic spezifisch sind.
page-status-flag: never-activated
uuid: 791f7a54-3225-46ca-ad6f-6c32e9c62d75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: e2dd8161-fe38-48bf-a288-8ec328b2660e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c800c20fff89b97f6fa38b3c659ca765765e157

---


# Sending an email{#sending-an-email}

To approve your email and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

Die detaillierten Schritte zur Validierung und zum Versand von Nachrichten finden Sie in den folgenden Abschnitten:

* [Versand validieren](../../delivery/using/steps-validating-the-delivery.md)
* [Versenden der Nachrichten](../../delivery/using/steps-sending-the-delivery.md)

In den folgenden Abschnitten werden die Parameter beschrieben, die für die Bereitstellung von E-Mails spezifisch sind.

## E-Mails archivieren {#archiving-emails}

In Adobe Campaign können Sie mit der BCC-Option E-Mails in einem externen System speichern, indem Sie einfach eine BCC-E-Mail-Adresse zu ihrer Versandzielgruppe hinzufügen. Durch Aktivierung dieser Option wird eine exakte Kopie aller versandten Nachrichten aufbewahrt.

Weiterführende Informationen zur Konfiguration von E-Mail-BCC finden Sie in [diesem Abschnitt](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Hierbei handelt es sich um eine optionale Funktion. Bitte prüfen Sie Ihren Lizenzvertrag und kontaktieren Sie den Ansprechpartner für Ihr Konto, um diese Funktion zu aktivieren.

Bei der Erstellung eines neuen Versands oder einer Versandvorlage ist die E-Mail-BCC-Option nicht standardmäßig aktiviert, selbst wenn die Option erworben wurde. Sie muss für jeden Versand bzw. jede Vorlage manuell aktiviert werden.

Gehen Sie dazu wie folgt vor:

1. Gehen Sie zu **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** oder **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Wählen Sie den gewünschten Versand aus oder duplizieren Sie die Standardvorlage **E-Mail-Versand**, und wählen Sie dann die duplizierte Vorlage aus.
1. Wählen Sie die **Eigenschaften**-Schaltfläche aus.
1. Wählen Sie die **[!UICONTROL Delivery]** Registerkarte.
1. Aktivieren Sie die Option **E-Mails archivieren**, um eine Kopie aller gesendeten Nachrichten dieses Versands oder aller auf dieser Vorlage basierenden Sendungen aufzubewahren.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >If the emails sent to the BCC address are opened and clicked through, this will be taken into account in the **[!UICONTROL Total opens]** and **[!UICONTROL Clicks]** from the send analysis, which could cause some miscalculations.

## Mirrorseite erstellen {#generating-the-mirror-page}

Eine Mirrorseite ist eine HTML-Seite, die über einen Webbrowser online abgerufen werden kann und deren Inhalt mit dem der E-Mail identisch ist.

Standardmäßig wird die Spiegelseite generiert, wenn der Link in den Inhalt der E-Mail eingefügt wird. Weitere Informationen zum Einfügen von Personalisierungsblöcken finden Sie unter [Personalisierungsblöcke](../../delivery/using/personalization-blocks.md).

In the delivery properties, the **[!UICONTROL Mode]** field of the **[!UICONTROL Validity]** tab lets you modify the generation mode for this page.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>Zur Erzeugung einer Mirrorseite muss zuvor ein HTML-Versandinhalt erstellt worden sein.

Außerdem stehen die folgenden Modi zur Verfügung:

* **[!UICONTROL Force the generation of the mirror page]** : Auch wenn kein Link zur Spiegelseite in die Bereitstellung eingefügt wird, wird die Spiegelseite erstellt.
* **[!UICONTROL Do not generate the mirror page]** : Es wird keine Spiegelseite erzeugt, auch wenn der Link in der Bereitstellung vorhanden ist.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** : Mit dieser Option können Sie im Lieferprotokoll-Fenster auf den Inhalt der Spiegelseite mit Personalisierungsinformationen zugreifen. Klicken Sie dazu nach dem Ende der Bereitstellung auf die **[!UICONTROL Delivery]** Registerkarte und wählen Sie die Zeile des Empfängers aus, dessen Spiegelseite Sie anzeigen möchten. Klicken Sie auf den **[!UICONTROL Display the mirror page for this message...]** Link.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Bounce Messages verwalten {#managing-bounce-emails}

Im Tab **[!UICONTROL SMTP]** der Versandeigenschaften lässt sich der Umgang mit Bounce Messages konfigurieren.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Standardmäßig werden Bounce Messages an die im Softwareverteilungs-Assitenten der Plattform angegebene Fehleradresse gesendet. Es besteht jedoch die Möglichkeit, für einen Versand durch Abwählen der Standardoption eine spezifische Fehleradresse anzugeben.

Sie können eine weitere Adresse angeben, die es ermöglicht, die Unzustellbarkeitsursache derjenigen E-Mails zu untersuchen, bei denen die Anwendung sie nicht automatisch erkannt hat. Bei beiden Feldern können Sie durch Klick auf das entsprechende Symbol Personalisierungsfelder hinzufügen.

## Zeichenkodierung {#character-encoding}

Auf der **[!UICONTROL SMTP]** Registerkarte der Bereitstellungsparameter können Sie mit dem **[!UICONTROL Character encoding]** Abschnitt eine bestimmte Kodierung festlegen.

Die Standardkodierung ist UTF-8. Wenn einige E-Mail-Anbieter Ihrer Empfänger die UTF-8-Standardkodierung nicht unterstützen, sollten Sie eine bestimmte Kodierung so einrichten, dass die Sonderzeichen den Empfängern Ihrer E-Mails korrekt angezeigt werden.

Sie möchten beispielsweise eine E-Mail mit japanischen Zeichen senden. Um sicherzustellen, dass alle Zeichen Ihren Empfängern in Japan korrekt angezeigt werden, sollten Sie eine Kodierung verwenden, die anstelle des Standard-UTF-8 die japanischen Zeichen unterstützt.

Wählen Sie dazu die **[!UICONTROL Force the encoding used for messages]** Option im **[!UICONTROL Character encoding]** Abschnitt aus und wählen Sie eine Kodierung aus der angezeigten Dropdownliste aus.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## SMTP-Header hinzufügen {#adding-smtp-headers}

Es ist möglich, SMTP-Header zu Ihren Auslieferungen hinzuzufügen. Verwenden Sie dazu den entsprechenden Abschnitt der **[!UICONTROL SMTP]** Registerkarte in der Bereitstellung.

Das in diesem Fenster erfasste Script muss pro Zeile einen Header im Format **Name: Wert** enthalten.

Werte werden bei Bedarf automatisch verschlüsselt.

>[!CAUTION]
>
>Das Hinzufügen zusätzlicher SMTP-Header ist eine Aufgabe für erfahrene Benutzer.
>
>Die Syntax des Skripts muss die Anforderungen für diesen Inhaltstyp (keine überflüssigen Leerzeichen, keine Leerzeilen usw.) erfüllen.
