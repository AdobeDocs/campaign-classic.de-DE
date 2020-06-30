---
title: Integration konfigurieren
seo-title: Integration konfigurieren
description: Integration konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 2%

---


# Pipeline-Überwachung {#pipeline-monitoring}

Der geplante Status-Webdienst informiert über den Status des Pipelineprozesses.

Sie können manuell über einen Browser oder automatisch mit einer Überwachungsanwendung aufgerufen werden.

Es ist im REST-Format, das unten beschrieben wird.

![](assets/triggers_8.png)

## Indicators {#indicators}

In diesem Abschnitt werden die Indikatoren im Status-Webdienst Liste.

Empfohlene Indikatoren zur Überwachung werden hervorgehoben.

* Verbraucher: Name des Clients, der die Auslöser zieht. In der Pipeline-Option konfiguriert.
* http-request
   * last-live-ms-ago: Zeit in ms seit der Verbindungsprüfung.
   * last-failed-cnx-ms-ago: Zeit in ms seit dem letzten Fehler der Verbindungsprüfung.
   * Pipeline-Host: Name des Hosts, von dem die Pipeline-Daten abgerufen werden.
* Zeiger
   * aktuelle Offsets: Wert des Zeigers in die Pipeline, pro untergeordneter Thread.
   * last-flush-ms-ago: Zeit in ms seit dem Abrufen eines Stapels von Auslösern.
   * next-offset-flush: Wartezeit bis zum nächsten Stapel, wenn dieser fertig ist.
   * processing-since-last-flush: Anzahl der im letzten Stapel verarbeiteten Auslöser.
* Routing
   * Auslöser: Liste der abgerufenen Auslöser. In der Pipeline-Option konfiguriert.
* stats
   * average-cursor-flush-time-ms: durchschnittliche Verarbeitungszeit für einen Stapel von Auslösern.
   * average-trigger-processing-time-ms: durchschnittliche Zeit, die mit der Analyse der Auslöserdaten verbracht wurde.
   * bytes-read: Anzahl der Bytes, die seit dem Start des Prozesses aus der Warteschlange gelesen wurden.
   * current-messages: aktuelle Anzahl ausstehender Meldungen, die aus der Warteschlange gezogen wurden und auf die Verarbeitung warten. **Dieser Indikator sollte nahe Null** liegen.
   * current-weiteren Zustellversuche: die aktuelle Anzahl der Meldungen, bei denen die Verarbeitung fehlgeschlagen ist und auf eine erneute Ausführung gewartet wird.
   * Spitzenmeldungen: maximale Anzahl ausstehender Meldungen, die der Prozess seit dem Start verarbeitet hat.
   * Zeiger-Flush: Anzahl der Meldungen, die seit dem Beginn verarbeitet wurden.
   * Routing-JS-custom: Anzahl der Nachrichten, die von der benutzerdefinierten JS verarbeitet wurden.
   * auslösend verworfen: Anzahl der Meldungen, die aufgrund von Verarbeitungsfehlern nach zu vielen weiteren Zustellversuchen verworfen wurden.
   * ausgelöst verarbeitet: Anzahl der Meldungen, die ohne Fehler verarbeitet wurden.
   * trigger-receive: Anzahl der Nachrichten, die von der Warteschlange empfangen wurden.

Diese Statistiken werden pro Verarbeitungs-Thread angezeigt.

* average-trigger-processing-time-ms: durchschnittliche Zeit, die mit der Analyse der Auslöserdaten verbracht wurde.
* is-JS-Prozessor: Wert &quot;1&quot;, wenn dieser Thread die benutzerdefinierte JS verwendet.
* auslösend verworfen: Anzahl der Meldungen, die aufgrund von Verarbeitungsfehlern nach zu vielen weiteren Zustellversuchen verworfen wurden. **Dieser Indikator sollte null** sein.
* Auslöserfehler: Anzahl der Verarbeitungsfehler im JS. **Dieser Indikator sollte null** sein.
* trigger-receive: Anzahl der Nachrichten, die von der Warteschlange empfangen wurden.

* Einstellungen: sie werden in den Konfigurationsdateien festgelegt.
   * flush-cursor-msg-count: Anzahl der Meldungen in einem Stapel.
   * flush-zeiger-period-ms: Zeit zwischen zwei Stapeln in Millisekunden.
   * processing-threads-JS: Anzahl der Verarbeitungsthreads, auf denen die benutzerdefinierte JS ausgeführt wird.
   * retry-period-ms: Zeit zwischen zwei weiteren Zustellversuchen, wenn ein Verarbeitungsfehler auftritt.
   * retry-validity-duration-ms: Dauer ab dem Zeitpunkt, zu dem die Verarbeitung wiederholt wird, bis die Nachricht verworfen wird.
   * Pipeline-Nachrichtenbericht

## Pipeline-Nachrichtenbericht {#pipeline-report}

Dieser Bericht zeigt die Anzahl der Nachrichten pro Stunde in den letzten fünf Tagen an.

![](assets/triggers_9.png)
