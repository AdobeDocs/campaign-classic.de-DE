---
solution: Campaign Classic
product: campaign
title: Konfiguration der Kampagne Versand-Einstellungen
description: Erfahren Sie, wie Sie die Einstellungen für Kampagne Versand konfigurieren
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
translation-type: tm+mt
source-git-commit: 401e1be234d52f04cbdf8dfa97f51ac227836cd5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 3%

---

# Versand-Einstellungen {#delivery-settings} konfigurieren

Die Versand-Parameter müssen im Ordner **serverConf.xml** konfiguriert werden.

* **DNS-Konfiguration**: Geben Sie die Domäne des Versands und die IP-Adressen (oder den Host) der DNS-Server an, die verwendet werden, um auf MX-Typ-DNS-Abfragen zu reagieren, die vom MTA-Modul ab  **`<dnsconfig>`** dem Zeitpunkt des Abschlusses vorgenommen werden.

   >[!NOTE]
   >
   >Der Parameter **nameServers** ist für eine Installation unter Windows unerlässlich. Bei einer Installation unter Linux muss sie leer bleiben.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Je nach Bedarf und Einstellungen können Sie außerdem die folgenden Konfigurationen durchführen: konfigurieren Sie einen [SMTP-Relais](#smtp-relay), passen Sie die Anzahl der [untergeordneten MTA-Prozesse](#mta-child-processes), [Verwalten des ausgehenden SMTP-Traffics](#managing-outbound-smtp-traffic-with-affinities) an.

## SMTP-Relais {#smtp-relay}

Das MTA-Modul fungiert als systemeigener E-Mail-Transfer-Agent für SMTP-Übertragungen (Port 25).

Es ist jedoch möglich, ihn durch einen Server zu ersetzen, wenn Ihre Sicherheitsrichtlinien dies erfordern. In diesem Fall ist der globale Durchsatz der Relaisdurchsatz (vorausgesetzt, dass der Relaisserver-Durchsatz niedriger ist als der Durchsatz des Adobe Campaigns).

In diesem Fall werden diese Parameter durch Konfiguration des SMTP-Servers im Abschnitt **`<relay>`** festgelegt. Sie müssen die IP-Adresse (oder den Host) des SMTP-Servers angeben, der zum Übertragen von E-Mails verwendet wird, und den zugehörigen Anschluss (standardmäßig 25).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Dieser Betriebsmodus setzt erhebliche Einschränkungen für Versand voraus, da er den Durchsatz aufgrund der intrinsischen Performance des Relaisservers (Latenz, Bandwith...) stark reduzieren kann. Darüber hinaus wird die Fähigkeit, synchrone Versand-Fehler zu qualifizieren (durch Analyse des SMTP-Traffics erkannt), begrenzt sein, und das Senden ist nicht möglich, wenn der Server nicht verfügbar ist.

## MTA-untergeordnete Prozesse {#mta-child-processes}

Es ist möglich, die Anzahl der untergeordneten Prozesse (maxSpareServers standardmäßig 2) zu steuern, um die Übertragungsleistung entsprechend der CPU-Leistung der Server und der verfügbaren Netzwerkressourcen zu optimieren. Diese Konfiguration ist auf jedem einzelnen Computer im Abschnitt **`<master>`** der MTA-Konfiguration vorzunehmen.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Siehe auch [Optimierung des E-Mail-Versands](../../installation/using/email-deliverability.md#email-sending-optimization).

## Verwalten des ausgehenden SMTP-Traffics mit Affinitäten {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>Die Konfiguration der Affinität muss von einem Server zum anderen konsistent sein. Es wird empfohlen, sich für die Konfiguration der Affinität an die Adobe zu wenden, da Konfigurationsänderungen auf allen Anwendungsservern, auf denen die MTA ausgeführt wird, repliziert werden sollten.

Sie können den ausgehenden SMTP-Traffic durch Affinitäten mit IP-Adressen verbessern.

Gehen Sie hierzu wie folgt vor:

1. Geben Sie die Affinitäten im Abschnitt **`<ipaffinity>`** der Datei **serverConf.xml** ein.

   Eine Affinität kann mehrere verschiedene Namen haben: zum Trennen verwenden Sie das Zeichen **;**.

   Beispiel:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Informationen zur Ansicht der entsprechenden Parameter finden Sie in der Datei **serverConf.xml**.

1. Um die Auswahl der Affinitäten in den Dropdown-Listen zu aktivieren, müssen Sie die Affinitäten in der Auflistung **IPAffinity** hinzufügen.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Die Auflistungen sind in [diesem Dokument](../../platform/using/managing-enumerations.md) detailliert.

   Anschließend können Sie die zu verwendende Affinität auswählen, wie unten für Typologien dargestellt:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Sie können auch auf [Serverkonfiguration des Versands](../../installation/using/email-deliverability.md#delivery-server-configuration) verweisen.

**Verwandte Themen**
* [Technische E-Mail-Konfigurationen](email-deliverability.md)
* [Verwenden von MX-Servern mit Kampagne](using-mx-servers.md)
* [E-Mail-BCC konfigurieren](email-archiving.md)
