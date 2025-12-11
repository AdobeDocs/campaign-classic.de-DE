---
product: campaign
title: Aktualisierung der Bounce-Qualifizierung nach dem Apple-Ausfall 2021
description: Hier wird erklärt, wie die Bounce-Qualifizierung nach dem Apple-Ausfall von 2021 aktualisiert werden kann
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: ht
source-wordcount: '461'
ht-degree: 100%

---

# Aktualisieren fehlerhafter Hardbounces nach Apple-Ausfall {#update-bounce-qualification.md}

## Kontext

Am 26. April 2021 führte ein globales Problem bei Apple dazu, dass einige E-Mail-Nachrichten, die an gültige Apple-E-Mail-Adressen gesendet wurden, von Apple-Servern fälschlicherweise als ungültige E-Mail-Adressen mit der folgenden Bounce-Antwort zurückgewiesen wurden: „550 5.1.1 &#39;email address&#39;: user lookup success but no user record found (&#39;E-Mail-Adresse&#39;: Benutzersuche erfolgreich, aber kein Benutzereintrag gefunden).“

Dieses Problem trat am 26.04. auf und dauerte von 7:00 bis 13:00 Uhr EST.

>[!NOTE]
>
>Sie können das Apple-Systemstatus-Dashboard auf [dieser Seite](https://www.apple.com/de/support/systemstatus/) überprüfen.

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Gemäß der Standardlogik für die Behandlung von Bounces hat Adobe Campaign diese Empfänger automatisch der Quarantäneliste mit dem **[!UICONTROL Status]** **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie Ihre Quarantänetabelle in Campaign aktualisieren, indem Sie diese Empfänger finden und entfernen oder ihren **[!UICONTROL Status]** auf **[!UICONTROL Gültig]** ändern, damit der nächtliche Bereinigungs-Workflow sie entfernt.

Um die Empfänger zu finden, die von diesem Problem betroffen waren, oder für den Fall, dass dies bei einem anderen ISP erneut auftritt, lesen Sie bitte die folgenden Anweisungen.

## Aktualisierungsprozess

Sie müssen eine Abfrage in Ihrer Quarantänetabelle ausführen, um alle Apple-Empfänger (einschließlich @icloud.com, @me.com, @mac.com) herauszufiltern, die möglicherweise von dem Ausfall betroffen waren, damit sie aus der Quarantäneliste entfernt und in zukünftige E-Mail-Sendungen von Campaign aufgenommen werden können.

Auf der Grundlage des Zeitrahmens des Vorfalls werden im Folgenden die Richtlinien für diese Abfrage empfohlen.

>[!IMPORTANT]
>
>Diese Daten/Zeiten basieren auf der Eastern Standard Zeitzone (EST). Bitte passen Sie die Zeitzone Ihrer Instanz an.

* Für Campaign-Instanzen mit SMTP-Bounce-Antwortinformationen im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält „Benutzerin oder Benutzer erfolgreich gefunden, aber kein Benutzereintrag gefunden“ UND **Fehlertext (Quarantänetext)** enthält „support.apple.com“
   * **Statusaktualisierung (@lastModified)** später als 26.04.2021 07:00:00 Uhr
   * **Statusaktualisierung (@lastModified)** früher als 26.04.2021 13:00:00 Uhr

* Für Campaign-Instanzen mit Regelinformationen für eingehende E-Mails im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält „Momen_Code10_InvalidRecipient“
   * **E-Mail-Domain (@domain)** ist gleich icloud.com ODER **E-Mail-Domain (@domain)** ist gleich me.com ODER **E-Mail-Domain (@domain)** ist gleich mac.com
   * **Statusaktualisierung (@lastModified)** später als 26.04.2021 07:00:00 Uhr
   * **Statusaktualisierung (@lastModified)** früher als 26.04.2021 13:00:00 Uhr

Sobald Sie die Liste der betroffenen Empfänger haben, können Sie diese entweder auf den Status **[!UICONTROL Gültig]** setzen, damit sie vom Workflow **[!UICONTROL Datenbankbereinigung]** aus der Quarantäneliste entfernt werden, oder sie einfach aus der Tabelle löschen.

**Verwandte Themen:**
* [Ursachen für das Fehlschlagen von Sendungen](delivery-failures-quarantine.md)
* [Bounce-Message-Qualifizierung](delivery-failures-quarantine.md#bounce-mail-qualification)
