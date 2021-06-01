---
product: campaign
title: 'Konfiguration '
description: 'Konfiguration '
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 4%

---

# Konfiguration {#configuration}

## Ändern des syslogd-Listening-Ports {#changing-the-syslogd-listening-port}

Standardmäßig ist der Listening-Port **syslogd** 666 (udp). Sie können sie bei Bedarf mithilfe einer Umgebungsvariablen ändern.

Nach der Konfiguration wird diese Variable von allen Adobe Campaign-Modulen berücksichtigt.

### Unter Linux {#in-linux}

Bearbeiten Sie die Datei **customer.sh** und fügen Sie die folgende Zeile hinzu:

```
export TRACE_ADDR=localhost:<listening port>
```

### Windows {#in-windows}

Sie müssen die Umgebungsvariable **TRACE_ADDR** mit dem Wert **localhost** erstellen: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Es wird empfohlen, einige Tests durchzuführen, um sicherzustellen, dass Ihre Plattform funktioniert, nachdem Sie diese Umgebungsvariable erstellt haben.

## Konfigurieren von Sicherheitszonen {#configuring-security-zones}

Jeder Benutzer muss mit einer Zone verknüpft sein, um sich bei einer Instanz anmelden zu können, und die Benutzer-IP muss in die Adressen oder Adresssätze aufgenommen werden, die in der Sicherheitszone definiert sind. Die Konfiguration der technischen Zone erfolgt in der Konfigurationsdatei des Adobe Campaign-Servers. Die Verknüpfung eines Benutzers mit einer Sicherheitszone muss in der Konsole definiert werden ( Knoten **[!UICONTROL Administration > Zugriffe > Benutzer]** ).

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie in [diesem Abschnitt](../../installation/using/security-zones.md).
