---
title: Über Adobe Experience Manager
seo-title: Über Adobe Experience Manager
description: Über Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: ht
source-wordcount: '479'
ht-degree: 100%

---


# Über Adobe Experience Cloud-Auslöser{#about-adobe-experience-triggers}

[!DNL Triggers] ist eine Integration zwischen Adobe Campaign und Adobe Analytics mithilfe der Pipeline. Die Pipeline ruft Aktionen oder Auslöser der Benutzer von Ihrer Website ab. Ein Beispiel für einen Auslöser ist ein Warenkorbabbruch. Auslöser werden in Adobe Campaign verarbeitet, um in nahezu Echtzeit E-Mails zu senden.

[!DNL Triggers] führen nach der Aktion eines Benutzers in einem kurzen Zeitraum Marketing-Aktionen aus. Die typische Reaktionszeit beträgt weniger als eine Stunde.

Dadurch werden flexiblere Integrationen möglich, da der Konfigurationsaufwand minimal ist und keine Drittanbieter beteiligt sind.
Unterstützt werden auch große Traffic-Volumen, ohne dass die Performance von Marketing-Aktivitäten leidet. Beispielsweise kann die Integration eine Million Auslöser pro Stunde verarbeiten.

## [!DNL Triggers]-Architektur {#triggers-architecture}

### Was ist die Pipeline? {#pipeline-explanation}

>[!CAUTION]
>
>Nur Adobe Cloud-Lösungen können Ereignisse aus Pipeline-Diensten von Adobe erstellen und nutzen. Systeme, die nicht von Adobe stammen, können das nicht.

Die Pipeline ist ein Messaging-System, das in Experience Cloud gehostet wird und [Apache Kafka](http://kafka.apache.org/) verwendet. Es stellt eine einfache Möglichkeit zur Übertragung von Daten zwischen Lösungen dar. Außerdem ist die Pipeline mehr Nachrichtenwarteschlange als Datenbank. Die Ersteller pushen Ereignisse in die Pipeline und die Verbraucher prüfen den Fluss und verwenden das jeweilige Ereignis nach Belieben. Ereignisse werden nur einige Tage gespeichert. Das Ziel besteht darin, den Datenfluss rund um die Uhr zu prüfen und Ereignisse sofort zu verarbeiten.

![](assets/triggers_1.png)

### Wie funktioniert die Pipeline? {#how-pipeline-work}

Der [!DNL pipelined]-Prozess wird auf dem Adobe Campaign-Marketing-Server kontinuierlich ausgeführt. Er stellt eine Verbindung zur Pipeline her, ruft die Ereignisse ab und verarbeitet sie sofort.

![](assets/triggers_2.png)

Der [!DNL pipelined]-Prozess meldet sich mit einem Authentifizierungsdienst bei Experience Cloud an und sendet einen privaten Schlüssel. Der Authentifizierungsdienst gibt ein Token zurück. Das Token dient beim Abrufen der Ereignisse zum Authentifizieren. [!DNL Triggers] werden von einem REST-Web-Dienst mit einer einfachen GET-Anfrage abgerufen. Die Antwort weist das JSON-Format auf. Zu den Parametern für die Anfrage gehören der Name des Auslösers und ein Zeiger, der die zuletzt abgerufene Nachricht angibt. Der [!DNL pipelined]-Prozess wird automatisch verarbeitet.

## Verwenden der Integration von Adobe Experience Cloud-Auslösern mit Adobe Campaign Classic

Im Folgenden finden Sie einige Best Practices für [!DNL Triggers]:

* Die [!DNL Trigger]-Daten müssen beim Eintritt in Campaign gespeichert werden. Sie sollten nicht direkt verarbeitet werden, da dies Latenz verursachen würde.
* Der Zeitstempel aus der Nachricht (und nicht aus der Datenbank) sollte überprüft werden.
* Verwenden Sie &quot;TriggerTimestamp&quot; und die Auslöser-ID, um Duplikate zu entfernen.

>[!CAUTION]
>
>Das unten stehende Beispiel wird nicht nativ bereitgestellt. Dies ist ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

Die Pipeline-Ereignisse werden automatisch heruntergeladen. Diese Ereignisse können mithilfe eines Formulars überwacht werden.

![](assets/triggers_3.png)

Der Knoten &quot;Pipeline Event&quot; ist nicht nativ und muss hinzugefügt werden. Außerdem muss in Campaign das zugehörige Formular erstellt werden. Diese Aufgaben müssen von erfahrenen Benutzern ausgeführt werden. Weitere Informationen finden Sie in den folgenden Abschnitten: [Navigationshierarchie](../../configuration/using/about-navigation-hierarchy.md) und [Bearbeiten von Formularen](../../configuration/using/editing-forms.md).

Ein wiederkehrender Kampagnen-Workflow fragt Auslöser ab. Wenn diese den Marketing-Kriterien entsprechen, wird ein Versand gestartet.

![](assets/triggers_4.png)
