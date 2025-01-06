---
product: campaign
title: Zusätzliche Konfiguration
description: Konfiguration
feature: Monitoring, Configuration
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 27%

---

# Konfiguration{#configuration}



## Ändern des syslogd-Listening-Ports {#changing-the-syslogd-listening-port}

Standardmäßig ist der **syslogd** Listening-Port 666 (udp). Sie können sie bei Bedarf mit einer Umgebungsvariablen ändern.

Nach der Konfiguration wird diese Variable von allen Adobe Campaign-Modulen berücksichtigt.

### Unter Linux {#in-linux}

Bearbeiten Sie die Datei **customer.sh** und fügen Sie die folgende Zeile hinzu:

```sql
export TRACE_ADDR=localhost:<listening port>
```

### Unter Windows {#in-windows}

Sie müssen die Umgebungsvariable **TRACE_ADDR** mit dem Wert **localhost** erstellen: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Es wird empfohlen, einige Tests durchzuführen, um sicherzustellen, dass Ihre Plattform funktioniert, nachdem Sie diese Umgebungsvariable erstellt haben.

## Konfigurieren von Sicherheitszonen {#configuring-security-zones}

Jeder Operator muss mit einer Zone verknüpft sein, um sich bei einer Instanz anmelden zu können, und die IP des Operators muss in die Adressen oder Adresssätze aufgenommen werden, die in der Sicherheitszone definiert sind. Die Konfiguration des technischen Bereichs erfolgt in der Konfigurationsdatei des Adobe Campaign-Servers. Die Verknüpfung eines Benutzers mit einer Sicherheitszone muss in der Konsole definiert werden (Knoten **[!UICONTROL Administration > Zugriffsverwaltung > Benutzer]**).

>[!NOTE]
>
>Weiterführende Informationen zur Konfiguration von Sicherheitszonen finden Sie [diesem Abschnitt](../../installation/using/security-zones.md).
