---
solution: Campaign Classic
product: campaign
title: Netzwerk, Datenbank und SSL/TLS
description: Weitere Informationen zu Best Practices für die Konfiguration von Netzwerk, Datenbank und SSL/TLS.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 63b2e6b95812f1649e636580984a1f0dcc9c5c53
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 65%

---


# Netzwerk, Datenbank und SSL/TLS {#network-database}

## Netzwerkkonfiguration

Bei der Bereitstellung eines lokalen Architekturtyps ist unbedingt die [Netzwerkkonfiguration](../../installation/using/network-configuration.md) zu überprüfen. Stellen Sie sicher, dass der Tomcat-Server NICHT direkt von außerhalb des Servers zugänglich ist:

* Schließen Sie den Tomcat-Port (8080) auf externen IP-Adressen (muss auf localhost ausgeführt werden).
* Ordnen Sie den Standard-HTTP-Port (80) nicht dem Tomcat-Port (8080) zu.

Verwenden Sie möglichst eine sichere Verbindung: POP3S statt POP3 (oder POP3 über TLS).

## Datenbank

Sie müssen die Best Practices für die Sicherheit Ihrer Datenbank-Engine anwenden.

## SSL/TLS-Konfiguration

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
