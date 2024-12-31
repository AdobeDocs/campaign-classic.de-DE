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



Die Adobe Campaign-Plattform basiert auf dem Konzept der Instanzen, ähnlich dem von virtuellen Hosts, die von Apache verwendet werden. In diesem Betriebsmodus können Sie einen Server freigeben, indem Sie ihm mehrere Instanzen zuweisen. Instanzen sind vollständig voneinander getrennt und arbeiten mit ihrer eigenen Datenbank und Konfigurationsdatei.

Für einen bestimmten Server gibt es zwei Elemente, die für alle Adobe Campaign-Instanzen gelten:

* Das **interne** Kennwort: Dies ist das allgemeine Administratorkennwort. Sie ist in allen Instanzen eines bestimmten Anwendungs-Servers gleich.

  >[!IMPORTANT]
  >
  >Für die Anmeldung mit der **internen** Kennung muss zuvor ein Kennwort definiert worden sein. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Mehrere technische Server-Konfigurationen: Diese Konfigurationen können alle in der spezifischen Konfiguration einer -Instanz überladen werden.

Die Konfigurationsdateien werden im Verzeichnis **conf** des Installationsverzeichnisses gespeichert. Die Konfiguration ist in drei Dateien unterteilt:

* **serverConf.**: Gesamtkonfiguration für alle Instanzen.
* **config-**`<instance>`**.xml** (wobei **`<instance>`** der Instanzname ist): spezifische Konfiguration einer Instanz.
* **serverConf.xml.diff**: Delta zwischen der anfänglichen Konfiguration und der aktuellen Konfiguration. Diese Datei wird automatisch von der Anwendung generiert und darf nicht manuell geändert werden. Er wird verwendet, um Benutzeränderungen beim Aktualisieren einer Build-Version automatisch zu propagieren.

Eine Instanzkonfiguration wird wie folgt geladen:

* Das Modul lädt die **serverConf.xml**, um die von allen Instanzen gemeinsam genutzten Parameter abzurufen.
* Anschließend wird die Datei **config-**`<instance>`**.xml** geladen. Die in dieser Datei gefundenen Werte haben Vorrang vor den in „serverConf **xml“ enthaltenen**.

  Diese beiden Dateien haben dasselbe Format. Jeder Wert in **serverConf.xml** kann für eine bestimmte Instanz in der Datei **config-`<instance>`.xml** überladen werden.

Dieser Betriebsmodus bietet eine große Flexibilität bei der Konfiguration.
