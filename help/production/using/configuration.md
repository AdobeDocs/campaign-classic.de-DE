---
product: campaign
title: Zusätzliche Konfiguration
description: Konfiguration
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 23%

---

# Konfiguration {#configuration}



## syslogd-Listening-Port ändern {#changing-the-syslogd-listening-port}

Standardmäßig wird die **syslogd** Listening-Anschluss ist 666 (udp). Sie können sie bei Bedarf mithilfe einer Umgebungsvariablen ändern.

Nach der Konfiguration wird diese Variable von allen Adobe Campaign-Modulen berücksichtigt.

### Unter Linux {#in-linux}

Bearbeiten Sie die **customer.sh** und fügen Sie die folgende Zeile hinzu:

```
export TRACE_ADDR=localhost:<listening port>
```

### Windows {#in-windows}

Sie müssen die **TRACE_ADDR** Umgebungsvariable mit **localhost** Wert: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Es wird empfohlen, einige Tests durchzuführen, um sicherzustellen, dass Ihre Plattform funktioniert, nachdem Sie diese Umgebungsvariable erstellt haben.

## Konfigurieren von Sicherheitszonen {#configuring-security-zones}

Jeder Operator muss mit einer Zone verknüpft sein, um sich bei einer Instanz anmelden zu können, und die IP des Operators muss in die Adressen oder Adresssätze aufgenommen werden, die in der Sicherheitszone definiert sind. Die Konfiguration der technischen Zone erfolgt in der Konfigurationsdatei des Adobe Campaign-Servers. Die Verknüpfung eines Benutzers mit einer Sicherheitszone muss in der Konsole definiert werden ( **[!UICONTROL Administration > Zugriffe > Benutzer]** Knoten).

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie unter [diesem Abschnitt](../../installation/using/security-zones.md).
