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
translation-type: tm+mt
source-git-commit: 718b490d48c6cfabdb24ab18dffb6db664f2a46c
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 51%

---

# Aktualisieren Sie falsche Festplatten nach Apple-Ausfall {#update-bounce-qualification.md}

## Kontext

Am 26. April 2021 führte ein weltweites Problem bei Apple dazu, dass einige E-Mail-Nachrichten, die an gültige Apple-E-Mail-Adressen gesendet wurden, fälschlicherweise als ungültige E-Mail-Adressen von Apple-Servern abgeschnitten wurden, wobei die folgende Antwort lautet:  &quot;550 5.1.1 &quot;E-Mail-Adresse&quot;: Sucherfolg des Benutzers, aber kein Benutzerdatensatz gefunden.&quot;

Dieses Problem trat am 26.04.2010 auf und dauerte von 7.00 - 13.00 Uhr EST.

>[!NOTE]
>
>Sie können das Apple-Systemstatus-Dashboard auf [dieser Seite](https://www.apple.com/support/systemstatus/) überprüfen.

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Gemäß der Standardlogik für die Behandlung von Bounces hat Adobe Campaign diese Empfänger automatisch der Quarantäneliste mit dem **[!UICONTROL Status]** **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie Ihre Quarantänetabelle in Campaign aktualisieren, indem Sie diese Empfänger finden und entfernen oder ihren **[!UICONTROL Status]** auf **[!UICONTROL Gültig]** ändern, damit der nächtliche Bereinigungs-Workflow sie entfernt.

Um die Empfänger zu finden, die von diesem Problem betroffen waren, oder falls dies bei einem anderen ISP erneut auftritt, lesen Sie bitte die unten stehenden Anweisungen.

## Aktualisierungsprozess

Sie müssen eine Abfrage auf Ihrer Quarantänen-Tabelle ausführen, um alle Apple-Empfänger auszufiltern - einschließlich @icloud.com, @me.com, @mac.com -, die möglicherweise von dem Ausfall betroffen waren, damit sie aus der Liste der Quarantäne entfernt und in zukünftige E-Mail-Versand der Kampagne aufgenommen werden können.

Auf der Grundlage des Zeitrahmens des Vorfalls werden im Folgenden die Richtlinien für diese Abfrage empfohlen.

>[!IMPORTANT]
>
>Diese Daten/Zeiten basieren auf der Eastern Standard Zeitzone (EST). Passen Sie die Zeitzone Ihrer Instanz an.

* Für Campaign-Instanzen mit SMTP-Bounce-Antwortinformationen im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantäne)** enthält &quot;Benutzersuche erfolgreich, aber kein Benutzerdatensatz gefunden&quot; UND  **Fehlertext (Quarantäne)** enthält &quot;support.apple.com&quot;
   * **Status aktualisieren (@lastModified)** am oder nach dem 26.04.2021 07:00:00 AM
   * **Status aktualisieren (@lastModified)** am oder vor dem 26.04.2021 01:00:00 PM

* Für Campaign-Instanzen mit Regelinformationen für eingehende E-Mails im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-Mail-Domäne (@Domäne)** gleich icloud.com ODER  **E-Mail-Domäne (@Domäne)** gleich me.com ODER  **E-Mail-Domäne (@Domäne)** gleich mac.com
   * **Status aktualisieren (@lastModified)** am oder nach dem 26.04.2021 07:00:00 AM
   * **Status aktualisieren (@lastModified)** am oder vor dem 26.04.2021 01:00:00 PM

Sobald Sie die Liste der betroffenen Empfänger haben, können Sie diese entweder auf den Status **[!UICONTROL Gültig]** setzen, damit sie vom Workflow **[!UICONTROL Datenbankbereinigung]** aus der Quarantäneliste entfernt werden, oder sie einfach aus der Tabelle löschen.

**Verwandte Themen:**
* [Ursachen für das Fehlschlagen von Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Bounce-Message-Qualifizierung](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)
