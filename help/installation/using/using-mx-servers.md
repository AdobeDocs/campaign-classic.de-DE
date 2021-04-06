---
solution: Campaign Classic
product: campaign
title: Verwenden von MX-Servern mit Kampagne
description: Erfahren Sie, wie MX-Server mit Adobe Campaign Classic funktionieren.
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
translation-type: tm+mt
source-git-commit: 3b5a6e6f03d9cb26ed372c3df069cbada36756a2
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---

# Verwenden von MX-Servern mit Kampagne {#using-mx-servers}

Erfahren Sie, wie MX-Server mit Adobe Campaign Classic funktionieren.

## MX-Server {#mx-servers}

### Was ist ein MX-Server?

Ein Mailaustauscher-Datensatz (MX-Datensatz) ist eine Art Ressourcendatensatz im DNS (Domain Name System), der einen E-Mail-Server angibt, der für die Annahme von E-Mail-Nachrichten im Namen einer Domäne verantwortlich ist.

### Wie funktioniert ein MX-Server?

Wenn Sie eine E-Mail senden, stellt der Software-Server eine Verbindung zum Empfänger-Domänenserver her. Die Kommunikation zwischen den beiden Servern verwendet SMTP-Sprache und eine Domäne kann mehr als einen MX-Server haben. Die Verbindung zu dieser Domäne erfolgt mit der höchsten Priorität (kleinste Zahl) und andere Beginn werden als &quot;Backup-Server&quot;bezeichnet. Das Verbindungsprotokoll muss eingehalten werden.

### Wie funktioniert ein MX-Server mit Adobe Campaign?

Im Verbindungsprotokoll müssen Regeln eingehalten werden, um Spamming und Monopolisierung von Servern zu verhindern. Die wichtigsten sind:

* **Maximale Anzahl zulässiger** Verbindungen: Wenn diese Nummer eingehalten wird, befinden sich IPs nicht auf der Blockierungsliste und E-Mails werden aufgrund zusätzlicher Verbindungen nicht verweigert.
* **Maximale Anzahl der Nachrichten**: Während der Verbindung muss die Anzahl der gesendeten Nachrichten definiert werden. Wenn diese Zahl nicht definiert ist, sendet der Server so viele wie möglich. Dadurch wird der ISP als Spammer identifiziert und der Blockierungsliste hinzugefügt.
* **Nachrichten pro Stunde**: Um Ihrem e-Ruf gerecht zu werden, steuert Adobe Campaign die Anzahl der E-Mails, die Ihre IPs pro Stunde senden können. Dieses System schützt Sie vor einer E-Mail-Verweigerung oder Blockierungsliste.

## Inbounce-E-Mails

### Was ist eine Inbounce-E-Mail?

Dies ist der von Adobe Campaign verwendete Prozess zur Verarbeitung von Fehlern während der Serverkommunikation.

### Wie funktioniert eine Inbounce-E-Mail?

Die Fehleradresse verarbeitet Absprünge, die von ISPs zurückgesendet werden. Der Prozess analysiert verschiedene SMTP-Fehlercodes und wendet die richtige Aktion gemäß dem RegEx-Standard an.

Beispielsweise enthält eine E-Mail-Adresse ein Feedback &quot;550 Benutzer unbekannt&quot;, das von einem ISP gesendet wurde. Dieser Fehlercode wird von der Fehleradresse des Adobe Campaigns (returnPath-Adresse) verarbeitet. Dieser Fehler wird dann mit dem RegEx-Standard verglichen und die richtige Regel wird angewendet. Die E-Mail wird als *Hardbounce* (passend zum Typ) und dann *Unbekannter Benutzer* (entsprechend dem Grund) betrachtet und nach der ersten Schleife in die Quarantäne gesendet.

### Wie verwaltet Adobe Campaign es?

Adobe Campaign verwaltet diesen Vorgang mit einer Übereinstimmung zwischen einem Fehlertyp und einem Grund:

* **[!UICONTROL Benutzer unbekannt]**: Adresse, die syntaktisch korrekt ist, aber nicht existiert. Dieser Fehler wird als ein harter Absprung kategorisiert und innerhalb des ersten Fehlers in die Quarantäne verschoben.
* **[!UICONTROL Postfach vollständig]**: Mailbox, die die maximale Kapazität erreicht hat. Dieser Fehler kann auch darauf hindeuten, dass der Benutzer diese Mailbox nicht mehr verwendet. Dieser Fehler wird als Soft Bounce kategorisiert und innerhalb des dritten Fehlers in die Quarantäne verschoben und nach 30 Tagen aus der Quarantäne entfernt.
* **[!UICONTROL Inaktiver Benutzer]**: Der Posteingang wurde vom ISP in den letzten 6 Monaten aufgrund eines inaktiven Benutzers deaktiviert. Dieser Fehler wird als Soft Bounce kategorisiert und innerhalb des dritten Fehlers in die Quarantäne verschoben.
* **[!UICONTROL Ungültige Domain]**: Die Domäne in der E-Mail-Adresse ist nicht vorhanden. Dieser Fehler wird als Soft Bounce kategorisiert und innerhalb des dritten Fehlers in die Quarantäne verschoben.
* **[!UICONTROL Verweigert]**: Der ISP weigerte sich, die E-Mail an seine Benutzer zu senden. Dieser Fehler wird als Soft Bounce kategorisiert und nicht in die Quarantäne gedrängt, da der Fehler nicht mit der E-Mail-Adresse, sondern mit IP oder einem Domain-Ruf verknüpft ist.

>[!NOTE]
>
>Weitere Informationen zu Fehlertypen und -gründen finden Sie in diesem [Versand](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Instanz der Auslieferbarkeit

Eine tägliche Aktualisierung der MX-Regeln und -Inbounces-Regeln wird von einem bestimmten Workflow in der Client-Instanz verwaltet, der mit dem Eigentümer der Instanz im Bereich &quot;Auslieferung&quot;dieser Regeln verbunden ist.

Dieses tägliche Update wird für alle Clients ausgeführt, die ihre Instanz durch einen Transparenzvorgang auf dem neuesten Stand halten möchten.

Die MX-Regeln weisen sechs verschiedene Durchsatzstufen auf, die hauptsächlich während des Vorbeschleunigungsprozesses verwendet werden:

![](assets/mx-rules-throughput.png)

Der benutzerdefinierte Modus ist für fortgeschrittene Clients gedacht, die ihre eigenen MX-Regeln festlegen möchten. Wenn der benutzerdefinierte Modus aktiviert ist, wird der Client nicht von der Instanz im Bereich &quot;Auslieferbarkeit&quot;aktualisiert, da die Synchronisierung deaktiviert wird.

## Absprungbeispiele

* **Benutzer unbekannt**  (harter Absprung): 550 5.1.1 ... Benutzer ist unbekannt {mx003}
* **Postfach gefüllt**  (Soft-Absprung): 550 5.2.2 Benutzerquote überschritten
* **Inaktives Postfach**  (Soft Bounce): 550 5.7.1 : Anschrift des Empfängers abgelehnt: Inaktive MailBox, nicht länger als 6 Monate gefüllt
* **Domäne ungültig**  (Soft-Absprung): DNS-Abfrage für &#39;ourdan.com&#39; fehlgeschlagen
* **Refused** (soft bounce): Inbound-E-Mail-Absprung (Regel &#39;Feedback_loop_Hotmail&#39; entspricht diesem Absprung)
* **Unerreichbar**  (weicher Absprung): 421 4.16.55  [TS01] Meldungen von x.x.x.x wurden aufgrund übermäßiger Benutzerbeschwerden vorübergehend zurückgestellt

**Verwandte Themen:**
* [MX-Konfiguration](../../installation/using/email-deliverability.md#mx-configuration)
* [Technische E-Mail-Konfiguration](../../installation/using/email-deliverability.md)
* [Verstehen Sie Versand-Fehler.](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Technisches Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/product-specific-resources/campaign/acc-technical-recommendations.html)
