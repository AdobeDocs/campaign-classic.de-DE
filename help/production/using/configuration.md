---
product: campaign
title: Zusätzliche Konfiguration
description: Konfiguration
feature: Monitoring, Configuration
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
TQID: https://experienceleague.adobe.com/gzcQquM9q71NIOt8mScgRpLtwffxvopslrrpLxxIang
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 35%

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
