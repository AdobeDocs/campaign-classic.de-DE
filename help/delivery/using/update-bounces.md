---
product: campaign
title: Aktualisieren der Bounce-Qualifizierung nach einem ISP-Ausfall
description: Erfahren Sie, wie Sie die Bounce-Qualifizierung nach einem ISP-Ausfall aktualisieren
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: 165797105affc9b5d4e4332f7f158031579bf91c
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 37%

---

# Aktualisieren falscher Hardbounces nach einem ISP-Ausfall {#update-bounces}

![](../../assets/common.svg)

## Kontext{#update-bounce-context}

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Globale Probleme bei Apple oder Gmail können beispielsweise dazu führen, dass einige E-Mail-Nachrichten, die an gültige Apple- oder Gmail-E-Mail-Adressen gesendet werden, fälschlicherweise als ungültige E-Mail-Adressen von ISP-Servern mit den folgenden Bounce-Antworten abgeschnitten werden:

* &quot;550 5.1.1 &quot;E-Mail-Adresse&quot;: Benutzer erfolgreich gefunden, aber kein Benutzerdatensatz gefunden.&quot;

* Empfänger &quot;550 &#39;E-Mail-Adresse&#39; abgelehnt

Beachten Sie Folgendes: Wenn die Verzögerung mit der Meldung &quot;452 angeforderte Aktion abgebrochen wurde: versuchen Sie es später erneut&quot;, werden beobachtet - diese werden automatisch wiederholt und es sind keine Aktionen erforderlich. Sie sollten sich verbessern, da der ISP seine volle Kapazität wiederherstellt.

>[!NOTE]
>
>Sie können das Systemstatus-Dashboard von Apple unter [diese Seite](https://www.apple.com/de/support/systemstatus/){_blank}.
>
>Sie können das Google Workspace-Status-Dashboard unter [diese Seite](https://www.google.com/appsstatus#hl=de&amp;v=status){_blank}.

## Auswirkung{#update-bounce-impact}

Bei Ausfall eines ISP können über Campaign versendete E-Mails nicht erfolgreich an ihren Empfänger zugestellt werden: Diese E-Mails werden fälschlicherweise als Bounces markiert.

Gemäß der Standardlogik für die Behandlung von Bounces hat Adobe Campaign diese Empfänger automatisch der Quarantäneliste mit dem **[!UICONTROL Status]** **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie Ihre Quarantänetabelle in Campaign aktualisieren, indem Sie diese Empfänger finden und entfernen oder ihren **[!UICONTROL Status]** auf **[!UICONTROL Gültig]** ändern, damit der nächtliche Bereinigungs-Workflow sie entfernt.

Die von diesem Problem betroffenen Empfänger finden Sie in den unten stehenden Anweisungen.

## Aktualisierungsprozess{#update-bounce-update}

Sie müssen eine Abfrage in Ihrer Quarantänetabelle ausführen, um alle betroffenen Empfänger herauszufiltern, z. B. Apple, die vom Ausfall potenziell betroffenen Adressen, @icloud.com, @me.com, @mac.com, , damit sie aus der Quarantäneliste entfernt und in künftige Campaign-E-Mail-Sendungen aufgenommen werden können.

Basierend auf dem Zeitrahmen des Vorfalls und dem ISP werden für diese Abfrage folgende Richtlinien empfohlen.

* Für Campaign-Umgebungen mit Regelinformationen für eingehende E-Mails im **[!UICONTROL Fehlertext]** Feld der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält „Momen_Code10_InvalidRecipient“
   * **E-Mail-Domain (@domain)** gleich domain1.com ODER **E-Mail-Domain (@domain)** gleich domain2.com ODER **E-Mail-Domain (@domain)** gleich domain3.com
   * **Status aktualisieren (@lastModified)** am oder nach MM/TT/JJJJ HH:MM:SS AM
   * **Status aktualisieren (@lastModified)** am oder vor MM/TT/JJJJ HH:MM:SS PM

* Für Campaign-Umgebungen mit SMTP-Bounce-Antwortinformationen im **[!UICONTROL Fehlertext]** Feld der Quarantäneliste:

   * **Fehlertext (Quarantänetext)** enthält &quot;550-5.1.1&quot;UND **Fehlertext (Quarantänetext)** enthält &quot;support.ISP.com&quot;

      wobei &quot;support.ISP.com&quot;sein kann: z. B. &quot;support.apple.com&quot;oder &quot;support.google.com&quot;

   * **Status aktualisieren (@lastModified)** am oder nach MM/TT/JJJJ HH:MM:SS AM
   * **Status aktualisieren (@lastModified)** am oder vor MM/TT/JJJJ HH:MM:SS PM


Sobald Sie die Liste der betroffenen Empfänger haben, können Sie diese entweder auf den Status **[!UICONTROL Gültig]** setzen, damit sie vom Workflow **[!UICONTROL Datenbankbereinigung]** aus der Quarantäneliste entfernt werden, oder sie einfach aus der Tabelle löschen.

**Verwandte Themen:**
* [Ursachen für das Fehlschlagen von Sendungen](understanding-delivery-failures.md)
* [Bounce-Message-Qualifizierung](understanding-delivery-failures.md#bounce-mail-qualification)
