---
solution: Campaign Classic
product: campaign
title: 'Konfiguration '
description: 'Konfiguration '
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 4%

---


# Konfiguration{#configuration}

## Ändern des syslogd-Listening-Anschlusses {#changing-the-syslogd-listening-port}

Der **syslogd** -Listening-Anschluss ist standardmäßig auf 666 (udp) eingestellt. Sie können die Variable bei Bedarf mit einer Umgebung ändern.

Nach der Konfiguration wird diese Variable von allen Adobe Campaign-Modulen berücksichtigt.

### Unter Linux {#in-linux}

Bearbeiten Sie die Datei &quot; **customer.sh** &quot;und fügen Sie die folgende Zeile hinzu:

```
export TRACE_ADDR=localhost:<listening port>
```

### Windows {#in-windows}

Sie müssen die Variable **TRACE_ADDR.** Umgebung mit dem **Wert localhost** erstellen: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Es wird empfohlen, einige Tests durchzuführen, um sicherzustellen, dass Ihre Umgebung funktioniert, nachdem Sie diese Variable erstellt haben.

## Konfigurieren von Sicherheitszonen {#configuring-security-zones}

Jeder Operator muss mit einer Zone verknüpft sein, um sich bei einer Instanz anzumelden, und die IP-Adresse des Betreibers muss in die Adressen oder Adresssätze aufgenommen werden, die in der Sicherheitszone definiert sind. Die Konfiguration der technischen Zone erfolgt in der Konfigurationsdatei des Adobe Campaign-Servers. Die Verknüpfung eines Operators mit einer Sicherheitszone muss in der Konsole definiert werden ( **[!UICONTROL Administration > Zugriffsverwaltung > Operatoren]** -Knoten).

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#defining-security-zones).
