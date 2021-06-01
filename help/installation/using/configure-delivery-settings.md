---
product: campaign
title: Konfiguration der Versandeinstellungen für Campaign
description: Erfahren Sie, wie Sie die Versandeinstellungen für Campaign konfigurieren
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# Versandeinstellungen konfigurieren {#delivery-settings}

Die Versandparameter müssen im Ordner **serverConf.xml** konfiguriert werden.

* **DNS-Konfiguration**: Geben Sie die Bereitstellungsdomäne und die IP-Adressen (oder den Host) der DNS-Server an, die verwendet werden, um auf DNS-Abfragen vom MX-Typ zu reagieren, die vom MTA-Modul ab  **`<dnsconfig>`** jetzt durchgeführt werden.

   >[!NOTE]
   >
   >Der Parameter **nameServers** ist für eine Installation unter Windows unerlässlich. Für eine Installation unter Linux muss sie leer gelassen werden.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Je nach Ihren Anforderungen und Einstellungen können Sie außerdem die folgenden Konfigurationen vornehmen: einen [SMTP-Relais](#smtp-relay) konfigurieren, die Anzahl der [untergeordneten MTA-Prozesse](#mta-child-processes) anpassen, [Ausgehenden SMTP-Traffic verwalten](#managing-outbound-smtp-traffic-with-affinities).

## SMTP-Relais {#smtp-relay}

Das MTA-Modul fungiert als nativer E-Mail-Übertragungsagent für SMTP-Broadcast (Port 25).

Es ist jedoch möglich, ihn durch einen Relais-Server zu ersetzen, wenn Ihre Sicherheitsrichtlinien dies erfordern. In diesem Fall ist der globale Durchsatz der &quot;Relais&quot;-Durchsatz (vorausgesetzt, der Durchsatz des Relais-Servers ist niedriger als der Durchsatz des Adobe Campaign-Servers).

In diesem Fall werden diese Parameter durch Konfiguration des SMTP-Servers im Abschnitt **`<relay>`** festgelegt. Sie müssen die IP-Adresse (oder den Host) des SMTP-Servers angeben, der zum Übertragen von E-Mails verwendet wird, sowie den zugehörigen Port (standardmäßig 25).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Dieser Betriebsmodus beinhaltet schwerwiegende Einschränkungen bei Sendungen, da er den Durchsatz aufgrund der inhärenten Leistung des Relais-Servers (Latenz, Bandwith..) stark reduzieren kann. Darüber hinaus wird die Fähigkeit zur Qualifizierung von Fehlern bei synchronen Sendungen (erkannt durch Analyse des SMTP-Traffics) begrenzt, und der Versand ist nicht möglich, wenn der Server nicht verfügbar ist.

## MTA-Kindprozesse {#mta-child-processes}

Es ist möglich, die Anzahl der untergeordneten Prozesse (standardmäßig maxSpareServers 2) zu steuern, um die Übertragungsleistung entsprechend der CPU-Leistung der Server und den verfügbaren Netzwerkressourcen zu optimieren. Diese Konfiguration wird im Abschnitt **`<master>`** der MTA-Konfiguration auf jedem einzelnen Computer vorgenommen.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Weitere Informationen finden Sie unter [Optimierung des E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

## Ausgehenden SMTP-Traffic mit Präferenzen verwalten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>Die Affinitätskonfiguration muss von einem Server zum anderen konsistent sein. Es wird empfohlen, sich bezüglich der Affinitätskonfiguration an die Adobe zu wenden, da Konfigurationsänderungen auf allen Anwendungsservern repliziert werden sollten, auf denen der MTA ausgeführt wird.

Sie können den ausgehenden SMTP-Traffic durch Affinitäten mit IP-Adressen verbessern.

Gehen Sie hierzu wie folgt vor:

1. Geben Sie die Affinitäten im Abschnitt **`<ipaffinity>`** der Datei **serverConf.xml** ein.

   Eine Affinität kann mehrere verschiedene Namen haben: um sie zu trennen, verwenden Sie das Zeichen **;**.

   Beispiel:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Informationen zum Anzeigen der relevanten Parameter finden Sie in der Datei **serverConf.xml** .

1. Um die Affinitätsauswahl in den Dropdown-Listen zu aktivieren, müssen Sie die Affinitätsnamen in der Auflistung **IPAffinity** hinzufügen.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Auflistungen werden in [diesem Dokument](../../platform/using/managing-enumerations.md) beschrieben.

   Anschließend können Sie die zu verwendende Affinität auswählen, wie unten für Typologien dargestellt:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Konfiguration des Versandservers](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Verwandte Themen**
* [Technische E-Mail-Konfigurationen](email-deliverability.md)
* [MX-Server mit Campaign verwenden](using-mx-servers.md)
* [E-Mail-BCC konfigurieren](email-archiving.md)
