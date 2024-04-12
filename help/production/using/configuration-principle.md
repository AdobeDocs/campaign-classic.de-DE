---
product: campaign
title: Konfigurationsprinzip
description: Konfigurationsprinzip
feature: Monitoring, Configuration
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 8%

---

# Konfigurationsprinzip{#configuration-principle}



Die Adobe Campaign-Plattform basiert auf dem Konzept von Instanzen, ähnlich wie bei virtuellen Hosts, die von Apache verwendet werden. Diese Funktionsweise ermöglicht die gemeinsame Nutzung eines Servers durch Zuweisung mehrerer Instanzen. Instanzen sind völlig voneinander getrennt und arbeiten mit ihrer eigenen Datenbank und Konfigurationsdatei.

Für einen bestimmten Server gibt es zwei gemeinsame Elemente für alle Adobe Campaign-Instanzen:

* Die **intern** password: Dies ist das allgemeine Administratorkennwort. Dies ist für alle Instanzen eines bestimmten Anwendungsservers üblich.

  >[!IMPORTANT]
  >
  >So melden Sie sich mit dem **intern** Kennung, müssen Sie zuvor ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Mehrere technische Serverkonfigurationen: Diese Konfigurationen können alle in der spezifischen Konfiguration einer Instanz überschrieben werden.

Die Konfigurationsdateien werden im **conf** -Ordner des Installationsordners. Die Konfiguration ist in drei Dateien unterteilt:

* **serverConf.xml**: Gesamtkonfiguration für alle Instanzen.
* **config-**`<instance>`**.XML** , **`<instance>`** ist der Instanzname): spezifische Konfiguration einer Instanz.
* **serverConf.xml.diff**: Differenz zwischen der Erstkonfiguration und der aktuellen Konfiguration. Diese Datei wird automatisch von der Anwendung generiert und darf nicht manuell geändert werden. Sie wird verwendet, um beim Aktualisieren einer Build-Version automatisch Benutzeränderungen zu propagieren.

Eine Instanzkonfiguration wird wie folgt geladen:

* Das Modul lädt die **serverConf.xml** -Datei, um die von allen Instanzen gemeinsam genutzten Parameter abzurufen.
* Anschließend lädt er die **config-**`<instance>`**.XML** -Datei. Die in dieser Datei gefundenen Werte haben Vorrang vor den Werten in **serverConf.xml**.

  Diese beiden Dateien haben das gleiche Format. Jeder Wert in **serverConf.xml** kann für eine bestimmte Instanz im **config-`<instance>`.XML** -Datei.

Dieser Betriebsmodus bietet große Flexibilität bei der Konfiguration.
