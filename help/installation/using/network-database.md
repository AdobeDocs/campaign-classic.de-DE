---
product: campaign
title: Netzwerk, Datenbank und SSL/TLS
description: Erfahren Sie mehr über Best Practices für Netzwerk-, Datenbank- und SSL-/TLS-Konfiguration
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
TQID: https://experienceleague.adobe.com/PLGVcm4QYeU0A1uEhlDEfweZ275xpxtxo91r4aidr1I
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 138
ht-degree: 45%

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

Um das Zertifikat zu überprüfen, können Sie openssl verwenden. Um aktive Chiffren zu überprüfen, können Sie nmap verwenden:

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
