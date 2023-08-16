---
product: campaign
title: Aktualisieren der Bounce-Qualifizierung nach einem ISP-Ausfall
description: Erfahren Sie, wie Sie die Bounce-Qualifizierung nach einem ISP-Ausfall aktualisieren
badge-v7: label="v7" type="Informative" tooltip="Gilt für Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 100%

---

# Aktualisieren falscher Hardbounces nach einem ISP-Ausfall {#update-bounces}



## Kontext{#update-bounce-context}

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Globale Probleme bei Apple oder Gmail können beispielsweise dazu führen, dass einige E-Mail-Nachrichten, die an gültige Apple- oder Gmail-E-Mail-Adressen gesendet werden, von den ISP-Servern fälschlicherweise als ungültige E-Mail-Adressen einen Hardbounce mit den folgenden Antworten erfahren:

* „550 5.1.1 &#39;E-Mail-Adresse&#39;: Benutzer oder Benutzerin erfolgreich gefunden, aber kein Benutzerdatensatz gefunden.“

* „550 &#39;E-Mail-Adresse&#39; Empfänger oder Empfängerin abgelehnt“

Bitte beachten: Wenn Abweisungs-Bounces mit der Nachricht „452 angeforderte Aktion abgebrochen: Versuchen Sie es später erneut“ auftreten, werden diese automatisch wiederholt und es sind keine Aktionen erforderlich. Die Situation sollte sich verbessern, sobald der ISP seine volle Kapazität wieder erreicht.

>[!NOTE]
>
>Das Apple-Systemstatus-Dashboard lässt sich auf [dieser Seite](https://www.apple.com/de/support/systemstatus/){_blank} überprüfen.
>
>Das Status-Dashboard von Google Workspace lässt sich auf [dieser Seite](https://www.google.com/appsstatus#hl=de&amp;v=status){_blank} überprüfen.
>

## Auswirkung{#update-bounce-impact}

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Gemäß der Standardlogik für die Behandlung von Bounces hat Adobe Campaign diese Empfänger automatisch der Quarantäneliste mit dem **[!UICONTROL Status]** **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie Ihre Quarantänetabelle in Campaign aktualisieren, indem Sie diese Empfänger finden und entfernen oder ihren **[!UICONTROL Status]** auf **[!UICONTROL Gültig]** ändern, damit der nächtliche Bereinigungs-Workflow sie entfernt.

Um die Empfängerinnen und Empfänger zu finden, die von diesem Problem betroffen sind, lesen Sie die folgenden Anweisungen.

## Aktualisierungsprozess{#update-bounce-update}

Es muss eine Abfrage in Ihrer Quarantänetabelle erfolgen, um alle betroffenen Empfänger und Empfängerinnen zu filtern – zum Beispiel bei Apple die Adressen mit @icloud.com, @me.com, @mac.com –, die möglicherweise von dem Ausfall betroffen waren, damit sie aus der Quarantäneliste entfernt und in zukünftige E-Mail-Sendungen von Campaign aufgenommen werden können.

Auf der Grundlage des Zeitrahmens des Vorfalls und des ISP befinden sich unten die empfohlenen Richtlinien für diese Abfrage.

* Für Campaign-Umgebungen mit Regelinformationen für eingehende E-Mails im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält „Momen_Code10_InvalidRecipient“
   * **E-Mail-Domain (@domain)** gleich domain1.com ODER **E-Mail-Domain (@domain)** gleich domain2.com ODER **E-Mail-Domain (@domain)** gleich domain3.com
   * **Aktualisierungsstatus (@lastModified)** am oder nach MM/TT/JJJJ HH:MM:SS AM
   * **Aktualisierungsstatus (@lastModified)** am oder vor MM/TT/JJJJ HH:MM:SS PM

* Für Campaign-Umgebungen mit SMTP-Bounce-Antwortinformationen im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält „550-5.1.1“ UND **Fehlertext (Quarantänetext)** enthält „support.ISP.com“,

     wobei „support.ISP.com“ Folgendes sein kann: „support.apple.com“ oder „support.google.com“ zum Beispiel

   * **Aktualisierungsstatus (@lastModified)** am oder nach MM/TT/JJJJ HH:MM:SS AM
   * **Aktualisierungsstatus (@lastModified)** am oder vor MM/TT/JJJJ HH:MM:SS PM


Sobald Sie die Liste der betroffenen Empfänger haben, können Sie diese entweder auf den Status **[!UICONTROL Gültig]** setzen, damit sie vom Workflow **[!UICONTROL Datenbankbereinigung]** aus der Quarantäneliste entfernt werden, oder sie einfach aus der Tabelle löschen.

**Verwandte Themen:**
* [Ursachen für das Fehlschlagen von Sendungen](understanding-delivery-failures.md)
* [Bounce-Message-Qualifizierung](understanding-delivery-failures.md#bounce-mail-qualification)
