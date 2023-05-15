---
product: campaign
title: Konfigurationsprinzip
description: Konfigurationsprinzip
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

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
* **config-**`<instance>`**.xml** , **`<instance>`** ist der Instanzname): spezifische Konfiguration einer Instanz.
* **serverConf.xml.diff**: Differenz zwischen der Erstkonfiguration und der aktuellen Konfiguration. Diese Datei wird automatisch von der Anwendung generiert und darf nicht manuell geändert werden. Sie wird verwendet, um beim Aktualisieren einer Build-Version automatisch Benutzeränderungen zu propagieren.

Eine Instanzkonfiguration wird wie folgt geladen:

* Das Modul lädt die **serverConf.xml** -Datei, um die von allen Instanzen gemeinsam genutzten Parameter abzurufen.
* Anschließend lädt er die **config-**`<instance>`**.xml** -Datei. Die in dieser Datei enthaltenen Werte haben Vorrang vor den Werten in **serverConf.xml**.

   Diese beiden Dateien haben das gleiche Format. Jeder Wert in **serverConf.xml** kann für eine bestimmte Instanz im **config-`<instance>`.xml** -Datei.

Dieser Betriebsmodus bietet große Flexibilität bei der Konfiguration.
