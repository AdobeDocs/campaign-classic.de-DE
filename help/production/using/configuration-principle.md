---
product: campaign
title: Konfigurationsprinzip
description: Konfigurationsprinzip
feature: Monitoring, Configuration
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 8%

---

# Konfigurationsprinzip{#configuration-principle}



Die Adobe Campaign-Plattform basiert auf dem Konzept von Instanzen, ähnlich wie bei virtuellen Hosts, die von Apache verwendet werden. Diese Funktionsweise ermöglicht die gemeinsame Nutzung eines Servers durch Zuweisung mehrerer Instanzen. Instanzen sind völlig voneinander getrennt und arbeiten mit ihrer eigenen Datenbank und Konfigurationsdatei.

Für einen bestimmten Server gibt es zwei gemeinsame Elemente für alle Adobe Campaign-Instanzen:

* Das Kennwort **internal** : Dies ist das allgemeine Administratorkennwort. Dies ist für alle Instanzen eines bestimmten Anwendungsservers üblich.

  >[!IMPORTANT]
  >
  >Um sich mit der Kennung **Internal** anzumelden, müssen Sie zuvor ein Kennwort definiert haben. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Mehrere technische Serverkonfigurationen: Diese Konfigurationen können alle in der spezifischen Konfiguration einer Instanz überschrieben werden.

Die Konfigurationsdateien werden im Ordner &quot;**conf**&quot;des Installationsordners gespeichert. Die Konfiguration ist in drei Dateien unterteilt:

* **serverConf.xml**: Gesamtkonfiguration für alle Instanzen.
* **config-**`<instance>`**.xml** (wobei **`<instance>`** der Instanzname ist): spezifische Konfiguration einer Instanz.
* **serverConf.xml.diff**: Differenz zwischen der ersten Konfiguration und der aktuellen Konfiguration. Diese Datei wird automatisch von der Anwendung generiert und darf nicht manuell geändert werden. Sie wird verwendet, um beim Aktualisieren einer Build-Version automatisch Benutzeränderungen zu propagieren.

Eine Instanzkonfiguration wird wie folgt geladen:

* Das Modul lädt die Datei **serverConf.xml** , um die von allen Instanzen freigegebenen Parameter abzurufen.
* Anschließend wird die Datei **config-**`<instance>`**.xml** geladen. Die Werte in dieser Datei haben Vorrang vor den Werten in **serverConf.xml**.

  Diese beiden Dateien haben das gleiche Format. Jeder Wert in **serverConf.xml** kann für eine bestimmte Instanz in der Datei **config-`<instance>`.xml** überschrieben werden.

Dieser Betriebsmodus bietet große Flexibilität bei der Konfiguration.
