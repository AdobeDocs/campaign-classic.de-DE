---
product: campaign
title: Netzwerk, Datenbank und SSL/TLS
description: Erfahren Sie mehr über Best Practices für Netzwerk-, Datenbank- und SSL-/TLS-Konfiguration
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 59%

---

# Netzwerk, Datenbank und SSL/TLS {#network-database}

## Netzwerkkonfiguration

Eine sehr wichtige Sache, die bei der Bereitstellung einer On-Premise-Architektur zu überprüfen ist, ist die [Netzwerkkonfiguration](../../installation/using/network-configuration.md). Stellen Sie sicher, dass der Tomcat-Server NICHT direkt außerhalb des Servers zugänglich ist:

* Schließen Sie den Tomcat-Port (8080) auf externen IP-Adressen (muss auf localhost ausgeführt werden).
* Ordnen Sie den Standard-HTTP-Port (80) nicht dem Tomcat-Port (8080) zu.

Verwenden Sie möglichst eine sichere Verbindung: POP3S statt POP3 (oder POP3 über TLS).

## Datenbank

Sie müssen die Best Practices für die Datenbankmodul-Sicherheit anwenden.

## SSL-/TLS-Konfiguration

Das Zertifikat können Sie mit openssl überprüfen. Die aktive Cipher Suite können Sie mit nmap überprüfen:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

Sie können auch ein Phython-Script [sslyze](https://github.com/nabla-c0d3/sslyze/releases) verwenden, das beide Aufgaben übernimmt.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
