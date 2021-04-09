---
solution: Campaign Classic
product: campaign
title: Konfigurationsprinzip
description: Konfigurationsprinzip
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# Konfigurationsprinzip{#configuration-principle}

Die Adobe Campaign-Plattform basiert auf dem Konzept der Instanzen, ähnlich wie die von Apache verwendeten virtuellen Hosts. In diesem Modus können Sie einen Server freigeben, indem Sie ihm mehrere Instanzen zuweisen. Instanzen sind komplett voneinander getrennt und arbeiten mit ihrer eigenen Datenbank- und Konfigurationsdatei.

Für einen bestimmten Server gibt es zwei Elemente, die allen Adobe Campaign-Instanzen gemein sind:

* Das **interne**-Kennwort: dies ist das allgemeine Administratorkennwort. Sie ist für alle Instanzen eines bestimmten Anwendungsservers gültig.

   >[!IMPORTANT]
   >
   >Um sich mit dem Bezeichner **Internal** anzumelden, müssen Sie vorher ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Mehrere technische Serverkonfigurationen: Diese Konfigurationen können alle in der spezifischen Konfiguration einer Instanz überladen werden.

Die Konfigurationsdateien werden im Ordner **conf** des Installationsordners gespeichert. Die Konfiguration ist in drei Dateien unterteilt:

* **serverConf.xml**: Gesamtkonfiguration für alle Instanzen.
* **config-**`<instance>`**.xml** (wobei  **`<instance>`** der Instanzname lautet): spezifische Konfiguration einer Instanz.
* **serverConf.xml.diff**: Delta zwischen der ursprünglichen Konfiguration und der aktuellen Konfiguration. Diese Datei wird automatisch von der Anwendung generiert und darf nicht manuell geändert werden. Es wird verwendet, um Benutzeränderungen beim Aktualisieren einer Buildversion automatisch zu propagieren.

Eine Instanzkonfiguration wird wie folgt geladen:

* Das Modul lädt die Datei **serverConf.xml**, um die von allen Instanzen freigegebenen Parameter abzurufen.
* Anschließend wird die Datei **config-**`<instance>`**.xml** geladen. Die in dieser Datei gefundenen Werte haben Priorität vor den Werten in **serverConf.xml**.

   Diese beiden Dateien haben das gleiche Format. Jeder Wert in **serverConf.xml** kann für eine bestimmte Instanz in der Datei **config-`<instance>`.xml** überladen werden.

Dieser Betriebsmodus bietet große Flexibilität bei Konfigurationen.
