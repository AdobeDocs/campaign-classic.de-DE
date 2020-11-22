---
solution: Campaign Classic
product: campaign
title: Konfigurationsprinzip
description: Konfigurationsprinzip
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---


# Konfigurationsprinzip{#configuration-principle}

Die Adobe Campaign-Plattform basiert auf dem Konzept der Instanzen, ähnlich wie die von Apache verwendeten virtuellen Hosts. In diesem Modus können Sie einen Server freigeben, indem Sie ihm mehrere Instanzen zuweisen. Instanzen sind komplett voneinander getrennt und arbeiten mit ihrer eigenen Datenbank- und Konfigurationsdatei.

Für einen bestimmten Server gibt es zwei Elemente, die allen Adobe Campaign-Instanzen gemein sind:

* Das **interne** Kennwort: dies ist das allgemeine Administratorkennwort. Sie ist für alle Instanzen eines bestimmten Anwendungsservers gültig.

   >[!IMPORTANT]
   >
   >Um sich mit der **internen** Kennung anzumelden, müssen Sie vorher ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/campaign-server-configuration.md#internal-identifier).

* Mehrere technische Serverkonfigurationen: Diese Konfigurationen können alle in der spezifischen Konfiguration einer Instanz überladen werden.

Die Konfigurationsdateien werden im **conf** -Ordner des Installationsordners gespeichert. Die Konfiguration ist in drei Dateien unterteilt:

* **serverConf.xml**: Gesamtkonfiguration für alle Instanzen.
* **config-**`<instance>`**.xml** (wobei **`<instance>`** der Instanzname lautet): spezifische Konfiguration einer Instanz.
* **serverConf.xml.diff**: Delta zwischen der ursprünglichen Konfiguration und der aktuellen Konfiguration. Diese Datei wird automatisch von der Anwendung generiert und darf nicht manuell geändert werden. Es wird verwendet, um Benutzeränderungen beim Aktualisieren einer Buildversion automatisch zu propagieren.

Eine Instanzkonfiguration wird wie folgt geladen:

* Das Modul lädt die Datei &quot; **serverConf.xml** &quot;, um die von allen Instanzen freigegebenen Parameter abzurufen.
* Anschließend wird die Datei &quot; **config-**`<instance>`**.xml** &quot;geladen. Die in dieser Datei gefundenen Werte haben Vorrang vor den Werten in **serverConf.xml**.

   Diese beiden Dateien haben das gleiche Format. Jeder Wert in **serverConf.xml** kann für eine bestimmte Instanz in der Datei **config-`<instance>`.xml** überladen werden.

Dieser Betriebsmodus bietet große Flexibilität bei Konfigurationen.
