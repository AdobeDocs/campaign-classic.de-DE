---
product: campaign
title: MX-Server mit Campaign verwenden
description: Erfahren Sie, wie MX-Server mit Adobe Campaign Classic funktionieren
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 3%

---

# MX-Server mit Campaign verwenden {#using-mx-servers}



Erfahren Sie, wie MX-Server mit Adobe Campaign Classic funktionieren.

## MX-Server {#mx-servers}

### Was ist ein MX-Server?

Ein Mail-Exchange-Eintrag (MX-Eintrag) ist ein Ressourceneintrag im Domain Name System (DNS), der einen E-Mail-Server angibt, der für die Annahme von E-Mail-Nachrichten im Namen einer Domain verantwortlich ist.

### Wie funktioniert ein MX-Server?

Wenn Sie eine E-Mail senden, stellt der Software-Server eine Verbindung mit dem Empfänger-Domain-Server her. Die Kommunikation zwischen den beiden Servern erfolgt über SMTP, und eine Domain kann über mehr als einen MX-Server verfügen. Die Verbindung zu dieser Domain beginnt mit der höchsten Priorität (kleinste Zahl) und andere Server werden als „Backup“-Server bezeichnet. Das Verbindungsprotokoll muss eingehalten werden.

### Wie funktioniert ein MX-Server mit Adobe Campaign?

Im Verbindungsprotokoll müssen Regeln eingehalten werden, um Spamming und Monopolisierung von Servern zu verhindern. Die wichtigsten sind die folgenden:

* auf die Blockierungsliste setzen **Maximal zulässige Anzahl von Verbindungen**: Wenn diese Anzahl eingehalten wird, werden IPs nicht auf der-Seite angezeigt und E-Mails werden nicht aufgrund von zusätzlichen Verbindungen abgelehnt.
* **Maximale Nachrichtenanzahl**: Während der Verbindung muss die Anzahl der zu sendenden Nachrichten definiert werden. Wenn diese Zahl nicht definiert ist, sendet der Server so viele E-Mails wie möglich. Dies führt dazu, dass der ISP als Spam identifiziert und der Blockierungsliste hinzugefügt wird.
* **Nachrichten pro Stunde**: Um eine Übereinstimmung mit Ihrer E-Reputation zu erzielen, steuert Adobe Campaign die Anzahl der E-Mails, die Ihre IPs pro Stunde senden können. Dieses System schützt Sie vor E-Mail-Ablehnung und/oder Blockierungsliste.

## E-Mail-Empfang

### Was ist eine Inbounce-E-Mail?

Dies ist der Prozess, der von Adobe Campaign zur Verarbeitung von Fehlern während der Serverkommunikation verwendet wird.

### Wie funktioniert eine Inbounce-E-Mail?

Die Fehleradresse verarbeitet Bounces, die von ISPs zurückgesendet werden. Der Prozess analysiert verschiedene SMTP-Fehler-Codes und wendet die richtige Aktion gemäß dem RegEx-Standard an.

Eine E-Mail-Adresse enthält beispielsweise das Feedback „550 Benutzer unbekannt“, das von einem ISP gesendet wird. Dieser Fehlercode wird von der Adobe Campaign-Fehleradresse (Rückgabepfad-Adresse) verarbeitet. Dieser Fehler wird dann mit dem RegEx-Standard verglichen und die richtige Regel wird angewendet. Die E-Mail wird als *Hardbounce* (entspricht dem Typ) und dann *Unbekannter Benutzer* (entspricht dem Grund) betrachtet und nach der ersten Schleife in das System unter Quarantäne gestellt.

### Wie verwaltet Adobe Campaign die IT?

Adobe Campaign verwaltet diesen Prozess mit einer Übereinstimmung zwischen einem Fehlertyp und einem Grund:

* **[!UICONTROL Benutzer unbekannt]**: Adresse, die syntaktisch korrekt ist, aber nicht existiert. Dieser Fehler wird als Hardbounce kategorisiert und innerhalb des ersten Fehlers in Quarantäne verschoben.
* **[!UICONTROL Postfach voll]**: Postfach mit maximaler Kapazität. Dieser Fehler kann auch darauf hinweisen, dass der Benutzer dieses Postfach nicht mehr verwendet. Dieser Fehler wird als Softbounce kategorisiert, innerhalb des dritten Fehlers in die Quarantäne verschoben und nach einem Zeitraum von 30 Tagen aus der Quarantäne genommen.
* **[!UICONTROL Inaktiver Benutzer]**: Das Postfach wurde vom ISP aufgrund eines inaktiven Benutzers in den letzten 6 Monaten deaktiviert. Dieser Fehler wird als Softbounce kategorisiert und innerhalb des dritten Fehlers in Quarantäne verschoben.
* **[!UICONTROL Ungültige Domain]**: Die Domain in der E-Mail-Adresse existiert nicht. Dieser Fehler wird als Softbounce kategorisiert und innerhalb des dritten Fehlers in Quarantäne verschoben.
* **[!UICONTROL Verweigert]**: Der ISP weigerte sich, die E-Mail an seine Benutzer zu senden. Dieser Fehler wird als Softbounce kategorisiert und nicht in Quarantäne gepusht, da der Fehler nicht mit der E-Mail-Adresse, sondern mit der IP- oder Domain-Reputation verknüpft ist.

>[!NOTE]
>
>Weitere Informationen zu Typen und Ursachen für fehlgeschlagene Sendungen finden Sie in [Abschnitt](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Zustellbarkeitsinstanz {#deliveratbility-env}

Eine tägliche Aktualisierung der MX-Regeln und Bounces-Regeln wird von einem bestimmten Workflow in der Client-Instanz verwaltet, der mit dem Eigentümer der Zustellbarkeitsinstanz dieser Regeln verbunden ist.

Diese tägliche Aktualisierung wird für alle Kunden ausgeführt, die ihre Instanz durch einen Transparenzprozess auf dem neuesten Stand halten möchten.

Die MX-Regeln verfügen über 6 verschiedene Durchsatzstufen, die hauptsächlich während des Anlaufprozesses verwendet werden:

![](assets/mx-rules-throughput.png)

Der Modus Benutzerdefiniert ist für fortgeschrittene Clients gedacht, die ihre eigenen MX-Regeln festlegen möchten. Wenn der benutzerdefinierte Modus aktiviert ist, wird der Client von der Zustellbarkeitsinstanz nicht aktualisiert, da die Synchronisierung deaktiviert wird.

## Bounce-Beispiele

* **Benutzer unbekannt** (Hardbounce): 550 5.1.1 … Benutzer ist unbekannt {mx003}
* **Postfach voll** (Softbounce): 550 5.2.2 Benutzerkontingent überschritten
* **Inaktives Postfach** (Softbounce): 550 5.7.1 : Empfängeradresse abgelehnt: Inaktives Postfach, seit mehr als 6 Monaten nicht angezeigt
* **Domain ungültig** (Softbounce): DNS-Abfrage für „ourdan.com“ fehlgeschlagen
* **Verweigert** (Softbounce): Bounce für eingehende E-Mails (Regel &#39;Feedback_Loop_Hotmail&#39; wurde auf diesen Bounce angewandt)
* **Unerreichbar** (Softbounce): 421 4.16.55 [TS01] Nachrichten von x.x.x.x aufgrund übermäßiger Benutzerbeschwerden vorübergehend zurückgestellt

**Verwandte Themen:**
* [MX-Konfiguration](../../installation/using/email-deliverability.md#mx-configuration)
* [Technische E-Mail-Konfiguration](../../installation/using/email-deliverability.md)
* [Ursachen für das Fehlschlagen von Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic. - Technische Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
