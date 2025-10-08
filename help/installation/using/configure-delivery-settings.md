---
product: campaign
title: Konfiguration der Kampagnenversandeinstellungen
description: Erfahren Sie, wie Sie die Versandeinstellungen einer Kampagne konfigurieren
feature: Installation, Channel Configuration
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 28279c6ec0eab7f914cf6107cd1ec1cebd05113d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 10%

---

# Konfigurieren der Versandeinstellungen {#delivery-settings}



Die Versandparameter müssen im Ordner **serverConf.xml** konfiguriert werden.

* **DNS-Konfiguration**: Geben Sie die Bereitstellungs-Domain und die IP-Adressen (oder den Host) der DNS-Server an, die verwendet werden, um auf DNS-Abfragen vom MX-Typ zu reagieren, die vom MTA-Modul ab **`<dnsconfig>`** durchgeführt werden.

  >[!NOTE]
  >
  >Der **nameServers** ist für eine Installation unter Windows unverzichtbar. Für eine Installation unter Linux muss es leer bleiben.

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

Je nach Bedarf und Einstellungen können Sie auch die folgenden Konfigurationen durchführen: Konfigurieren eines [SMTP-Relais](#smtp-relay), Anpassen der Anzahl [untergeordneten MTA-Prozesse](#mta-child-processes), [Verwalten des ausgehenden SMTP-Traffics](#managing-outbound-smtp-traffic-with-affinities).

## SMTP-Relais {#smtp-relay}

Das MTA-Modul fungiert als nativer Mail-Transfer-Agent für die SMTP-Übertragung (Port 25).

Es ist jedoch möglich, sie durch einen Relais-Server zu ersetzen, wenn dies aufgrund der Sicherheitsrichtlinien erforderlich ist. In diesem Fall ist der globale Durchsatz der Relais-Durchsatz (vorausgesetzt, der Durchsatz des Relais-Servers ist niedriger als der von Adobe Campaign).

In diesem Fall werden diese Parameter durch Konfigurieren des SMTP-Servers im Abschnitt **`<relay>`** festgelegt. Sie müssen die IP-Adresse (oder den Host) des SMTP-Servers, der zum Übertragen von E-Mails verwendet wird, und den zugehörigen Port (standardmäßig 25) angeben.

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Dieser Betriebsmodus bedeutet schwerwiegende Einschränkungen für die Sendungen, da er den Durchsatz aufgrund der intrinsischen Leistung des Relay-Servers (Latenz, Bandbreite usw.) erheblich reduzieren kann. Außerdem ist die Kapazität zur Qualifizierung von synchronen Versandfehlern (die durch die Analyse des SMTP-Traffics erkannt werden) begrenzt, und das Senden ist nicht möglich, wenn der Relais-Server nicht verfügbar ist.

## Untergeordnete MTA-Prozesse {#mta-child-processes}

Es ist möglich, die Anzahl der untergeordneten Prozesse (standardmäßig maxSpareServers 2) zu steuern, um die Übertragungsleistung entsprechend der CPU-Leistung der Server und der verfügbaren Netzwerkressourcen zu optimieren. Diese Konfiguration muss im **`<master>`** Abschnitt der MTA-Konfiguration auf jedem einzelnen Computer vorgenommen werden.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Siehe auch [Optimierung des E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

## Ausgehenden SMTP-Traffic mit Affinitäten verwalten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>Die Affinitätskonfiguration muss von einem Server zum anderen konsistent sein. Es wird empfohlen, sich zur Affinitätskonfiguration an Adobe zu wenden, da Konfigurationsänderungen auf allen Anwendungsservern repliziert werden sollten, auf denen der MTA ausgeführt wird.

Sie können den ausgehenden SMTP-Traffic durch die Affinität zu IP-Adressen verbessern.

Gehen Sie hierzu wie folgt vor:

1. Geben Sie die Affinitäten im Abschnitt **`<ipaffinity>`** der Datei **serverConf.xml** ein.

   Eine Affinität kann mehrere verschiedene Namen haben: Um sie zu trennen, verwenden Sie das Zeichen **;**.

   Beispiel:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Die relevanten Parameter finden Sie in der Datei **serverConf.xml**.

1. Um die Affinitätsauswahl in den Dropdown-Listen zu aktivieren, müssen Sie den/die Affinitätsnamen in der Auflistung **IPAffinity** hinzufügen.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Weitere Informationen zum **Arbeiten mit Aufzählungen** finden Sie in der [Dokumentation zu Adobe Campaign v8 (Konsole)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.


   Anschließend können Sie die zu verwendende Affinität auswählen, wie unten für Typologien dargestellt:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Konfiguration des Versand-Servers](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Verwandte Themen** 
* [Technische E-Mail-Konfigurationen](email-deliverability.md)
* [MX-Server mit Campaign verwenden](using-mx-servers.md)
* [E-Mail-BCC konfigurieren](email-archiving.md)
