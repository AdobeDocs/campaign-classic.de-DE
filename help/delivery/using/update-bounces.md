---
product: campaign
title: Aktualisieren der Bounce-Qualifizierung nach einem ISP-Ausfall
description: Erfahren Sie, wie Sie die Bounce-Qualifizierung nach einem ISP-Ausfall aktualisieren
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Deliverability
hide: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
TQID: https://experienceleague.adobe.com/91YUAuxL17kfBm6-hryEpf-A8SPJzA-z-ss9f2maszY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 100%

---

# Aktualisieren falscher Hardbounces nach einem ISP-Ausfall {#update-bounces}



## Kontext{#update-bounce-context}

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Globale Probleme bei Apple oder Gmail können beispielsweise dazu führen, dass einige E-Mail-Nachrichten, die an gültige Apple- oder Gmail-E-Mail-Adressen gesendet werden, von den ISP-Servern fälschlicherweise als ungültige E-Mail-Adressen einen Hardbounce mit den folgenden Antworten erfahren:

* „550 5.1.1 &#39;E-Mail-Adresse&#39;: Benutzer oder Benutzerin erfolgreich gefunden, aber kein Benutzerdatensatz gefunden.“

* „550 &#39;E-Mail-Adresse&#39; Empfänger oder Empfängerin abgelehnt“

Bitte beachten: Wenn Aufschub-Bounces mit der Nachricht „452 angeforderte Aktion abgebrochen: Versuchen Sie es später erneut“ auftreten, werden diese automatisch wiederholt und es sind keine Aktionen erforderlich. Die Situation sollte sich verbessern, sobald der ISP seine volle Kapazität wieder erreicht.

>[!NOTE]
>
>Sie können das Apple-Systemstatus-Dashboard auf [dieser Seite](https://www.apple.com/de/support/systemstatus/){_blank} überprüfen.
>
>Sie können das Google Workspace-Status-Dashboard auf [dieser Seite](https://www.google.com/appsstatus#hl=de&v=status){_blank} überprüfen.
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
   * **Statusaktualisierung (@lastModified)** `MM/DD/YYYY HH:MM:SS AM` oder später
   * **Statusaktualisierung (@lastModified)** `MM/DD/YYYY HH:MM:SS PM` oder früher

* Für Campaign-Umgebungen mit SMTP-Bounce-Antwortinformationen im Feld **[!UICONTROL Fehlertext]** der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält „550-5.1.1“ UND **Fehlertext (Quarantänetext)** enthält „support.ISP.com“,

     wobei „support.ISP.com“ zum Beispiel: „support.apple.com“ oder „support.google.com“ sein kann

   * **Statusaktualisierung (@lastModified)** am oder später als `MM/DD/YYYY HH:MM:SS AM`
   * **Statusaktualisierung (@lastModified)** am oder früher als `MM/DD/YYYY HH:MM:SS PM`


Sobald Sie die Liste der betroffenen Empfänger haben, können Sie diese entweder auf den Status **[!UICONTROL Gültig]** setzen, damit sie vom Workflow **[!UICONTROL Datenbankbereinigung]** aus der Quarantäneliste entfernt werden, oder sie einfach aus der Tabelle löschen.

**Verwandte Themen:**
* [Ursachen für das Fehlschlagen von Sendungen](delivery-failures-quarantine.md)
* [Bounce-Message-Qualifizierung](delivery-failures-quarantine.md#bounce-mail-qualification)
