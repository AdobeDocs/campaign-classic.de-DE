---
product: campaign
title: Über die Erstkonfiguration
description: Über die Erstkonfiguration
feature: Installation, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 13%

---

# Wichtige Schritte zum Konfigurieren und Bereitstellen der Instanz{#about-initial-configuration}



Nachdem die Installation von Adobe Campaign abgeschlossen ist, müssen Sie sie konfigurieren, um sicherzustellen, dass sie effizient mit Ihren Einschränkungen und Ihrer technischen Architektur funktioniert. Die Schritte zum Konfigurieren einer Adobe Campaign-Instanz werden in diesem Kapitel in der folgenden Reihenfolge beschrieben:

1. Erstellen Sie die Instanz und die zugehörige Verbindung, siehe [Erstellen einer Instanz und Anmelden](../../installation/using/creating-an-instance-and-logging-on.md).
1. Erstellen und konfigurieren Sie die Datenbank, siehe [Datenbank erstellen und konfigurieren](../../installation/using/creating-and-configuring-the-database.md).
1. Konfigurieren Sie den Adobe Campaign-Server, siehe [Campaign-Serverkonfiguration](../../installation/using/configuring-campaign-server.md).
1. Bereitstellen der Instanz, siehe [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md).

Die Konfiguration der Instanz erfordert die Aktivierung von Prozessen (Web, MTA, wfserver usw.) auf dem Server gestartet und Module zum Senden von E-Mails, zum Tracking usw. konfiguriert werden. Für jede Instanz werden Adobe Campaign-Prozesse auf dem Server aktiviert. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

Für jede Instanz können zusätzliche Konfigurationen erforderlich sein (je nach verwendetem Modul, Ihrer Architektur und Ihren Anforderungen), um den Betrieb von Adobe Campaign zu optimieren.
