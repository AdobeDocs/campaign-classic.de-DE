---
solution: Campaign Classic
product: campaign
title: Aktualisierung der Absprungqualifikation nach einem ISP-Ausfall
description: Erfahren Sie, wie Sie die Absprungqualifikation nach einem ISP-Ausfall aktualisieren.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 0c93193ff30737870803f9fb25019f3162dcc96d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 1%

---


# Aktualisierung der Absprungqualifikation nach einem ISP-Ausfall {#update-bounce-qualification.md}

## Kontext

Bei Ausfall eines ISP können per Kampagne gesendete E-Mails nicht erfolgreich an ihren Empfänger gesendet werden: Diese E-Mails werden fälschlicherweise als Absprünge gekennzeichnet.

Im Dezember 2020 führte ein globales Problem bei Gmail dazu, dass einige E-Mail-Nachrichten, die an gültige Gmail-E-Mail-Adressen gesendet wurden, fälschlicherweise als ungültige E-Mail-Adressen von Gmail-Servern abgeschnitten wurden, wobei die folgende Antwort darauf lautet: *&quot;550-5.1.1 Das E-Mail-Konto, auf das Sie versucht haben zu erreichen, ist nicht vorhanden.&quot;*

Google hat erklärt, dass die Gmail-Ausfälle und Störungen, die dieses Problem verursacht haben, am 14. Dezember um 6:55 Uhr begonnen und am 15. Dezember um 18:09 Uhr EST beendet haben. Unsere Analyse der Daten zeigte am 16. Dezember um 2:06 Uhr EST eine sehr kurze Spitze in den Gmail-Absprüngen, die meisten am 15. Dezember zwischen 14:00 Uhr EST und 18:30 Uhr EST.

>[!NOTE]
>
>Sie können das Google Workspace-Status-Dashboard auf [dieser Seite](https://www.google.com/appsstatus#hl=en&amp;v=status) überprüfen.


Gemäß der standardmäßigen Absprungbearbeitungslogik hat Adobe Campaign diese Empfänger automatisch der Quarantäne-Liste mit der Einstellung **[!UICONTROL Status]** von **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie die Tabelle Ihrer Quarantäne in der Kampagne aktualisieren, indem Sie diese Empfänger suchen und entfernen oder deren **[!UICONTROL Status]** in **[!UICONTROL Gültig]** ändern, damit sie vom nächtlichen Bereinigungsarbeitsablauf entfernt werden.

Um die Empfänger zu finden, die von dieser Gmail-Ausgabe betroffen waren, oder falls dies bei einem anderen ISP erneut passiert, lesen Sie bitte die unten stehenden Anweisungen.

## Aktualisierungsprozess

Sie müssen eine Abfrage auf Ihrer Quarantänen-Tabelle ausführen, um alle Gmail- (oder andere ISP-) Empfänger auszufiltern, die möglicherweise von einem Ausfall betroffen waren, damit sie aus der Liste der Quarantäne entfernt und in zukünftige E-Mail-Versand der Kampagne aufgenommen werden können.

Auf der Grundlage des Zeitrahmens des Vorfalls werden im Folgenden die Richtlinien für diese Abfrage empfohlen.

>[!IMPORTANT]
>
>Diese Daten/Zeiten basieren auf der Eastern Standard Zeitzone (EST). Passen Sie die Zeitzone Ihrer Instanz an.

* Für Instanzen von Kampagnen mit SMTP-Absprungantwortinformationen im Feld **[!UICONTROL Fehlertext]** der Liste Quarantäne:

   * **Fehlertext (Quarantäne)** enthält &quot;550-5.1.1 Das E-Mail-Konto, das Sie erreichen wollten, ist nicht vorhanden&quot; UND  **Fehlertext (Quarantäne)** enthält &quot;support.google.com&quot; **
   * **Status aktualisieren (@lastModified)** am oder nach dem 14.12.2020 6:55:00 Uhr
   * **Status aktualisieren (@lastModified)** am oder vor dem 16.12.2020 6.00:00 Uhr

* Für Instanzen von Kampagnen mit Inbound-E-Mail-Regelinformationen im Feld **[!UICONTROL Fehlertext]** der Liste Quarantäne:

   * **Fehlertext (Quarantäne)** enthält &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-Mail-Domäne (@Domäne)**  gleich &quot;gmail.com&quot; ODER E-Mail-Domäne (@Domäne) gleich &quot;googlemail.com&quot;
   * **Status aktualisieren (@lastModified)** am oder nach dem 14.12.2020 6:55:00 Uhr
   * **Status aktualisieren (@lastModified)** am oder vor dem 16.12.2020 6.00:00 Uhr

Sobald Sie die Liste der betroffenen Empfänger haben, können Sie diese entweder auf den Status **[!UICONTROL Gültig]** setzen, damit sie vom **[!UICONTROL Datenbankbereinigung]**-Arbeitsablauf aus der Liste der Quarantäne entfernt werden, oder sie einfach aus der Tabelle löschen.

**Verwandte Themen:**
* [Verstehen Sie Versand-Fehler.](../../delivery/using/understanding-delivery-failures.md)
* [Bounce-Message-Qualifizierung          ](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)

