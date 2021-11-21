---
product: campaign
title: Konfiguration der Versandeinstellungen für Campaign
description: Erfahren Sie, wie Sie die Versandeinstellungen für Campaign konfigurieren
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# Versandeinstellungen konfigurieren {#delivery-settings}

![](../../assets/v7-only.svg)

Die Versandparameter müssen im Abschnitt **serverConf.xml** Ordner.

* **DNS-Konfiguration**: Geben Sie die Bereitstellungsdomäne und die IP-Adressen (oder den Host) der DNS-Server an, die verwendet werden, um auf DNS-Abfragen des MX-Typs zu reagieren, die vom MTA-Modul vom **`<dnsconfig>`** ab.

   >[!NOTE]
   >
   >Die **nameServers** -Parameter ist für eine Installation unter Windows unerlässlich. Für eine Installation unter Linux muss sie leer gelassen werden.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Je nach Ihren Anforderungen und Einstellungen können Sie außerdem die folgenden Konfigurationen vornehmen: konfigurieren Sie eine [SMTP-Relais](#smtp-relay), passen Sie die Anzahl der [Untergeordnete MTA-Prozesse](#mta-child-processes), [Ausgehenden SMTP-Traffic verwalten](#managing-outbound-smtp-traffic-with-affinities).

## SMTP-Relais {#smtp-relay}

Das MTA-Modul fungiert als nativer E-Mail-Übertragungsagent für SMTP-Broadcast (Port 25).

Es ist jedoch möglich, ihn durch einen Relais-Server zu ersetzen, wenn Ihre Sicherheitsrichtlinien dies erfordern. In diesem Fall ist der globale Durchsatz der &quot;Relais&quot;-Durchsatz (vorausgesetzt, der Durchsatz des Relais-Servers ist niedriger als der Durchsatz des Adobe Campaign-Servers).

In diesem Fall werden diese Parameter durch die Konfiguration des SMTP-Servers im **`<relay>`** Abschnitt. Sie müssen die IP-Adresse (oder den Host) des SMTP-Servers angeben, der zum Übertragen von E-Mails verwendet wird, sowie den zugehörigen Port (standardmäßig 25).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Dieser Betriebsmodus beinhaltet schwerwiegende Einschränkungen bei Sendungen, da er den Durchsatz aufgrund der inhärenten Leistung des Relais-Servers (Latenz, Bandbreite usw.) stark reduzieren kann. Darüber hinaus wird die Fähigkeit zur Qualifizierung von Fehlern bei synchronen Sendungen (erkannt durch Analyse des SMTP-Traffics) begrenzt, und der Versand ist nicht möglich, wenn der Server nicht verfügbar ist.

## Untergeordnete MTA-Prozesse {#mta-child-processes}

Es ist möglich, die Anzahl der untergeordneten Prozesse (standardmäßig maxSpareServers 2) zu steuern, um die Übertragungsleistung entsprechend der CPU-Leistung der Server und den verfügbaren Netzwerkressourcen zu optimieren. Diese Konfiguration wird im **`<master>`** -Abschnitt der MTA-Konfiguration auf jedem einzelnen Computer.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Siehe auch [Optimierung des E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

## Ausgehenden SMTP-Traffic mit Affinitäten verwalten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>Die Affinitätskonfiguration muss von einem Server zum anderen konsistent sein. Es wird empfohlen, sich bezüglich der Affinitätskonfiguration an die Adobe zu wenden, da Konfigurationsänderungen auf allen Anwendungsservern repliziert werden sollten, auf denen der MTA ausgeführt wird.

Sie können den ausgehenden SMTP-Traffic durch Affinitäten mit IP-Adressen verbessern.

Gehen Sie hierzu wie folgt vor:

1. Geben Sie die Affinitäten im **`<ipaffinity>`** Abschnitt **serverConf.xml** -Datei.

   Eine Affinität kann mehrere verschiedene Namen haben: , um sie zu trennen, verwenden Sie die **;** Zeichen.

   Beispiel:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Die relevanten Parameter werden im Abschnitt **serverConf.xml** -Datei.

1. Um die Affinitätsauswahl in den Dropdown-Listen zu aktivieren, müssen Sie die Affinitätsnamen in der **IPAffinity** Auflistung.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Auflistungen werden im Abschnitt [dieses Dokuments](../../platform/using/managing-enumerations.md).

   Anschließend können Sie die zu verwendende Affinität auswählen, wie unten für Typologien dargestellt:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Konfiguration des Versandservers](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Verwandte Themen** 
* [Technische E-Mail-Konfigurationen](email-deliverability.md)
* [MX-Server mit Campaign verwenden](using-mx-servers.md)
* [E-Mail-BCC konfigurieren](email-archiving.md)
