---
solution: Campaign Classic
product: campaign
title: Aktualisieren der Bounce-Qualifizierung nach einem ISP-Ausfall
description: Erfahren Sie, wie Sie die Bounce-Qualifizierung nach einem ISP-Ausfall aktualisieren.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
translation-type: ht
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: ht
source-wordcount: '486'
ht-degree: 100%

---

# Aktualisieren der Bounce-Qualifizierung nach einem ISP-Ausfall {#update-bounce-qualification.md}

## Kontext

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Im Dezember 2020 führte ein globales Problem bei Gmail dazu, dass einige E-Mail-Nachrichten, die an gültige Gmail-Adressen gesendet wurden, von Gmail-Servern fälschlicherweise als ungültige E-Mail-Adressen mit der folgenden Bounce-Antwort zurückgewiesen wurden: *&quot;550-5.1.1 Das E-Mail-Konto, das Sie zu erreichen versucht haben, existiert nicht.&quot;*

Google hat angegeben, dass die Gmail-Ausfälle und -Störungen, die dieses Problem verursachten, am 14. Dezember um 6:55 Uhr begannen und am 15. Dezember um 18:09 Uhr EST endeten. Unsere Datenanalyse zeigte außerdem eine sehr kurze Spitze an Gmail-Bounces um 2:06 Uhr EST am 16. Dezember, wobei der Großteil am 15. Dezember zwischen 14:00 Uhr und 18:30 Uhr EST auftrat.

>[!NOTE]
>
>Sie können das Google Workspace-Status-Dashboard auf [dieser Seite](https://www.google.com/appsstatus#hl=de&amp;v=status) überprüfen.


Gemäß der Standardlogik für die Behandlung von Bounces hat Adobe Campaign diese Empfänger automatisch der Quarantäneliste mit dem **[!UICONTROL Status]** **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie Ihre Quarantänetabelle in Campaign aktualisieren, indem Sie diese Empfänger finden und entfernen oder ihren **[!UICONTROL Status]** auf **[!UICONTROL Gültig]** ändern, damit der nächtliche Bereinigungs-Workflow sie entfernt.

Um die Empfänger zu finden, die von diesem Gmail-Problem betroffen waren, oder für den Fall, dass dies bei einem anderen ISP erneut auftritt, lesen Sie bitte die folgenden Anweisungen.

## Aktualisierungsprozess

Sie müssen eine Abfrage in Ihrer Quarantäne-Tabelle ausführen, um alle Gmail-Empfänger (oder Empfänger anderer ISPs) herauszufiltern, die möglicherweise von dem Ausfall betroffen waren, damit sie aus der Quarantäneliste entfernt und in zukünftige E-Mail-Sendungen von Campaign aufgenommen werden können.

Auf der Grundlage des Zeitrahmens des Vorfalls werden im Folgenden die Richtlinien für diese Abfrage empfohlen.

>[!IMPORTANT]
>
>Diese Daten/Zeiten basieren auf der Eastern Standard Zeitzone (EST). Passen Sie die Zeitzone Ihrer Instanz an.

* Für Campaign-Instanzen mit SMTP-Bounce-Antwortinformationen im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält &quot;550-5.1.1 Das E-Mail-Konto, das Sie erreichen wollten, existiert nicht&quot; UND **Fehlertext (Quarantänetext)** enthält &quot;support.google.com&quot; **
   * **Statusaktualisierung (@lastModified)** später als 14.12.2020 6:55:00 Uhr
   * **Statusaktualisierung (@lastModified)** früher als 16.12.2020 6.00:00 Uhr

* Für Campaign-Instanzen mit Regelinformationen für eingehende E-Mails im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-Mail-Domain (@domain)** gleich &quot;gmail.com&quot; ODER E-Mail-Domain (@domain) gleich &quot;googlemail.com&quot;
   * **Status aktualisieren (@lastModified)** später als 14.12.2020 6:55:00 Uhr
   * **Status aktualisieren (@lastModified)** früher als 16.12.2020 6.00:00 Uhr

Sobald Sie die Liste der betroffenen Empfänger haben, können Sie diese entweder auf den Status **[!UICONTROL Gültig]** setzen, damit sie vom Workflow **[!UICONTROL Datenbankbereinigung]** aus der Quarantäneliste entfernt werden, oder sie einfach aus der Tabelle löschen.

**Verwandte Themen:**
* [Ursachen für das Fehlschlagen von Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Bounce-Message-Qualifizierung](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
