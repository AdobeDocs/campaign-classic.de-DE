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
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 3%

---


# Über Adobe Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] ist eine Integration zwischen Adobe Campaign und Adobe Analytics mithilfe der Pipeline. Die Pipeline ruft die Aktionen oder Auslöser der Benutzer von Ihrer Website ab. Ein Warenkorbabbruch ist ein Beispiel für einen Auslöser. Auslöser werden in Adobe Campaign verarbeitet, um E-Mails in Echtzeit zu senden.

[!DNL Triggers] Marketingaktionen innerhalb eines kurzen Zeitraums nach der Aktion eines Benutzers ausführen. Die typische Reaktionszeit beträgt weniger als eine Stunde.

Es ermöglicht flexiblere Integrationen, da die Konfiguration minimal ist und kein Drittanbieter beteiligt ist.
Es unterstützt auch ein hohes Traffic-Aufkommen, ohne die Performance von Marketing-Aktivitäten zu beeinträchtigen. Beispielsweise kann die Integration eine Million Auslöser pro Stunde verarbeiten.

## [!DNL Triggers] Architektur {#triggers-architecture}

### Was ist Pipeline? {#pipeline-explanation}

>[!CAUTION]
>
>Nur Adobe Cloud-Lösungen können Ereignis aus den Pipeline-Diensten von Adobe erstellen und nutzen. Systeme, die nicht zu Adobe gehören, können das nicht.

Pipeline ist ein Messaging-System, das im Experience Cloud gehostet wird, das [Apache Kafka](http://kafka.apache.org/)verwendet. Es ist eine Möglichkeit, Daten einfach zwischen Lösungen zu übertragen. Außerdem ist Pipeline eine Meldungswarteschlange und keine Datenbank. Die Hersteller drängen Ereignis in die Pipeline, und die Verbraucher hören auf den Fluss und tun, was sie mit dem Ereignis wollen. Ereignis werden einige Tage aufbewahrt, aber nicht mehr. Das Ziel ist, rund um die Uhr zuzuhören und Ereignis sofort zu verarbeiten.

![](assets/triggers_1.png)

### Wie wirkt Pipeline? {#how-pipeline-work}

Der &quot;Pipeline&quot;-Prozess wird immer auf dem Adobe Campaign Marketing Server ausgeführt. Es verbindet sich mit der Pipeline, ruft die Ereignis ab und verarbeitet sie sofort.

![](assets/triggers_2.png)

Der geplante Prozess meldet sich mit einem Authentifizierungsdienst beim Experience Cloud an und sendet einen privaten Schlüssel. Der Authentifizierungsdienst gibt ein Token zurück. Das Token wird zum Authentifizieren beim Abrufen der Ereignis verwendet. [!DNL Triggers] werden von einem REST-Webdienst mit einer einfachen GET-Anforderung abgerufen. Die Antwort ist das JSON-Format. Zu den Parametern für die Anforderung gehören der Name des Auslösers und ein Zeiger, der die zuletzt abgerufene Meldung anzeigt. Der Pipeline-Prozess verarbeitet ihn automatisch.

## Verwenden der Integration von Adobe Experience Cloud-Auslösern mit Adobe Campaign Classic

Im Folgenden finden Sie einige [!DNL Triggers] Best Practices:

* Die [!DNL Trigger] Daten müssen während der Kampagne gespeichert werden. Es sollte nicht direkt verarbeitet werden, da es zu einer Latenz führen würde.
* Der Zeitstempel sollte aus der Meldung und nicht aus der Datenbank überprüft werden.
* Verwenden Sie TriggerTimestamp und Auslöser-ID, um Duplikat zu entfernen.

>[!CAUTION]
>
>Das unten stehende Beispiel wird nicht standardmäßig bereitgestellt. Dies ist ein spezifisches Beispiel aus verschiedenen möglichen Implementierungen.

Die Pipeline-Ereignis werden automatisch heruntergeladen. Diese Ereignis können mithilfe eines Formulars überwacht werden.

![](assets/triggers_3.png)

Der Knoten Pipeline-Ereignis ist nicht integriert und muss hinzugefügt werden. Das zugehörige Formular muss in Kampagne erstellt werden. Diese Vorgänge sind nur für Benutzer von Experten verfügbar. Weitere Informationen finden Sie in den folgenden Abschnitten: [Navigationshierarchie](../../configuration/using/about-navigation-hierarchy.md) und [Bearbeitung von Formularen](../../configuration/using/editing-forms.md).

Eine wiederkehrende Abfrage des Arbeitsablaufs für Kampagnen bei Auslösern und wenn sie die Marketingkriterien erfüllen, wird ein Versand Beginn.

![](assets/triggers_4.png)
