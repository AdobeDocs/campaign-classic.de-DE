---
product: campaign
title: MX-Server mit Campaign verwenden
description: Erfahren Sie, wie MX-Server mit Adobe Campaign Classic funktionieren.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

---

# MX-Server mit Campaign verwenden {#using-mx-servers}



Erfahren Sie, wie MX-Server mit Adobe Campaign Classic funktionieren.

## MX-Server {#mx-servers}

### Was ist ein MX-Server?

Ein E-Mail-Austauschdatensatz (MX-Eintrag) ist ein Ressourcentyp im Domain Name System (DNS), der einen E-Mail-Server angibt, der für die Annahme von E-Mail-Nachrichten im Namen einer Domain zuständig ist.

### Wie funktioniert ein MX-Server?

Wenn Sie eine E-Mail senden, stellt der Software-Server eine Verbindung zum Empfänger-Domain-Server her. Die Kommunikation zwischen den beiden Servern nutzt die SMTP-Sprache und eine Domain kann über mehr als einen MX-Server verfügen. Die Verbindung zu dieser Domäne beginnt mit der höchsten Priorität (kleinste Zahl) und andere Server werden als &quot;Backup&quot;-Server bezeichnet. Das Verbindungsprotokoll muss eingehalten werden.

### Wie funktioniert ein MX-Server mit Adobe Campaign?

Im Verbindungsprotokoll müssen Regeln eingehalten werden, um das Spamming und Monopolisieren von Servern zu verhindern. Die wichtigsten sind:

* **Maximale Anzahl erlaubter Verbindungen**: Wenn diese Zahl eingehalten wird, befinden sich IPs nicht auf der Blockierungsliste und E-Mails werden aufgrund zusätzlicher Verbindungen nicht verweigert.
* **Maximale Nachrichtenanzahl**: Während der Verbindung muss die Anzahl der zu sendenden Nachrichten definiert werden. Wenn diese Zahl nicht definiert ist, sendet der Server so viele wie möglich. Dies führt dazu, dass der ISP als Spammer identifiziert und der Blockierungsliste hinzugefügt wird.
* **Nachrichten pro Stunde**: Um Ihre E-Reputation zu wahren, steuert Adobe Campaign die Anzahl der E-Mails, die Ihre IPs pro Stunde senden können. Dieses System schützt Sie vor E-Mail-Verweigerung oder Blockierungsliste.

## E-Mails in Bounce Messages

### Was ist eine Inbounce-E-Mail?

Dies ist der Prozess, der von Adobe Campaign zur Verarbeitung von Fehlern während der Serverkommunikation verwendet wird.

### Wie funktioniert eine Inbounce-E-Mail?

Die Fehleradresse verarbeitet Bounces, die von ISPs zurückgesendet werden. Der Prozess analysiert verschiedene SMTP-Fehlercodes und wendet die richtige Aktion gemäß dem RegEx-Standard an.

Beispielsweise hat eine E-Mail-Adresse ein Feedback &quot;550 Benutzer unbekannt&quot;, das von einem ISP gesendet wurde. Dieser Fehlercode wird von der Adobe Campaign-Fehleradresse verarbeitet (Rückgabepfad-Adresse). Dieser Fehler wird dann mit dem RegEx-Standard verglichen und die richtige Regel wird angewendet. Die E-Mail gilt als *Hardbounce* (entspricht dem Typ) und dann *Benutzer unbekannt* (entsprechend dem Grund) und nach der ersten Schleife in das System unter Quarantäne gestellt werden.

### Wie wird sie von Adobe Campaign verwaltet?

Adobe Campaign verwaltet diesen Prozess mit einer Übereinstimmung zwischen einem Fehlertyp und einem Grund:

* **[!UICONTROL Benutzer unbekannt]**: Adresse, die syntaktisch korrekt ist, aber nicht vorhanden ist. Dieser Fehler wird als Hardbounce kategorisiert und innerhalb des ersten Fehlers unter Quarantäne gestellt.
* **[!UICONTROL Postfach voll]**: Postfach, das die maximale Kapazität erreicht hat. Dieser Fehler kann auch darauf hinweisen, dass der Benutzer dieses Postfach nicht mehr verwendet. Dieser Fehler wird als Softbounce kategorisiert und innerhalb des dritten Fehlers unter Quarantäne gestellt und nach 30 Tagen aus der Quarantäne entfernt.
* **[!UICONTROL Inaktiver Benutzer]**: Das Postfach wurde vom ISP aufgrund eines inaktiven Benutzers in den letzten 6 Monaten deaktiviert. Dieser Fehler wird als Softbounce kategorisiert und innerhalb des dritten Fehlers unter Quarantäne gestellt.
* **[!UICONTROL Ungültige Domain]**: Die Domain in der E-Mail-Adresse existiert nicht. Dieser Fehler wird als Softbounce kategorisiert und innerhalb des dritten Fehlers unter Quarantäne gestellt.
* **[!UICONTROL Abgelehnt]**: Der ISP weigerte sich, die E-Mail an seine Benutzer zu senden. Dieser Fehler wird als Softbounce kategorisiert und nicht unter Quarantäne gestellt, da der Fehler nicht mit der E-Mail-Adresse, sondern mit der IP-Adresse oder der Reputation einer Domain verknüpft ist.

>[!NOTE]
>
>Weiterführende Informationen zu Typen und Ursachen für fehlgeschlagene Sendungen finden Sie in diesem Abschnitt [Abschnitt](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Zustellbarkeitsinstanz {#deliveratbility-env}

Eine tägliche Aktualisierung der MX-Regeln und -Inbounces-Regeln wird von einem bestimmten Workflow in der Client-Instanz verwaltet, der mit dem Eigentümer der Zustellbarkeitsinstanz dieser Regeln verbunden ist.

Diese tägliche Aktualisierung wird für alle Kunden durchgeführt, die ihre Instanz mithilfe eines Transparenzprozesses auf dem neuesten Stand halten möchten.

Die MX-Regeln weisen 6 verschiedene Durchsatzstufen auf, die hauptsächlich während der Anlaufphase verwendet werden:

![](assets/mx-rules-throughput.png)

Der benutzerdefinierte Modus richtet sich an fortgeschrittene Clients, die eigene MX-Regeln festlegen möchten. Wenn der benutzerdefinierte Modus aktiviert ist, wird der Client von der Zustellbarkeitsinstanz nicht aktualisiert, da die Synchronisierung deaktiviert wird.

## Bounce-Beispiele

* **Unbekannter Nutzer** (Hardbounce): 550 5.1.1 ... Benutzer ist unbekannt {mx003}
* **Postfach voll** (Softbounce): 550 5.2.2 Benutzerquote überschritten
* **Inaktives Postfach** (Softbounce): 550 5.7.1 : Empfängeradresse abgelehnt: Inaktive MailBox, nicht länger als 6 Monate geöffnet
* **Domäne ungültig** (Softbounce): DNS-Abfrage für &#39;ourdan.com&#39; fehlgeschlagen
* **Abgelehnt** (Softbounce): Eingehender E-Mail-Bounce (Regel &#39;Feedback_loop_Hotmail&#39; entspricht diesem Bounce)
* **Unerreichbar** (Softbounce): 421 4,16,55 [TS01] Nachrichten von x.x.x.x werden aufgrund übermäßiger Benutzerbeschwerden vorübergehend verschoben

**Verwandte Themen:**
* [MX-Konfiguration](../../installation/using/email-deliverability.md#mx-configuration)
* [Technische E-Mail-Konfiguration](../../installation/using/email-deliverability.md)
* [Ursachen für das Fehlschlagen von Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Technische Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
