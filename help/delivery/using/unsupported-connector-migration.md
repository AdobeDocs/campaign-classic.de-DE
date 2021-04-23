---
solution: Campaign Classic
product: campaign
title: Migration nicht unterstützter SMS-Connectoren
description: Migration eines nicht unterstützten SMS-Connectors zum erweiterten allgemeinen SMPP-Connector
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '636'
ht-degree: 100%

---

# Migration eines nicht unterstützten SMS-Connectors zum erweiterten allgemeinen SMPP-Connector{#unsupported-connector-migration}

Ab Version 20.2 werden alte Connectoren nicht mehr unterstützt. Mithilfe dieses Dokuments können Sie noch auf dem alten System laufende Connectoren zum empfohlenen SMPP-Connector migrieren.

>[!CAUTION]
>
>Diese Migration ist nicht obligatorisch, wird aber von Adobe empfohlen und stellt sicher, dass Sie mit der neuesten unterstützten Software-Version arbeiten.

## Über SMS-Connectoren {#about-sms-connectors}

Die folgenden Connectoren werden ab Version 20.2 nicht mehr unterstützt:

* **[!UICONTROL Allgemeines SMPP]** (SMPP-Version 3.4 mit Unterstützung für Binärmodus)
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

Veraltete Funktionen sind weiterhin verfügbar und werden unterstützt, sie werden jedoch nicht weiterentwickelt. Es wird empfohlen, den Connector **[!UICONTROL Erweitertes allgemeines SMPP]** zu verwenden.

Weiterführende Informationen zu veralteten und entfernten Funktionen finden Sie auf dieser [Seite](../../rn/using/deprecated-features.md).

Alte SMS-Connectoren verwenden den Java-SMS-Connector und überlasten damit den Web-Prozess. Durch die Migration auf den neuen Connector **[!UICONTROL Erweitertes allgemeines SMPP]** wird diese Last auf den MTA verschoben, der dafür ausgelegt ist.

## Migration zum erweiterten allgemeinen SMPP-Connector {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>Sie können zwar möglicherweise Parameter übertragen, benötigen aber zur Konfiguration des Connectors **[!UICONTROL Erweitertes allgemeines SMPP]** weitere Informationen von Ihrem Provider zum Einrichten der übrigen Parameter. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../delivery/using/sms-protocol.md).

Zunächst müssen Sie das neue externe Konto **[!UICONTROL Erweitertes allgemeines SMPP]** erstellen. Anschließend können Sie möglicherweise einige der Parameter übertragen. Eine Anleitung mit detaillierten Schritten finden Sie auf dieser [Seite](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

Sie müssen nun die Parameter im Tab **[!UICONTROL Mobile]** Ihres neu erstellten externen Kontos **[!UICONTROL Erweitertes allgemeines SMPP]** entsprechend Ihrem vorherigen Connector einrichten.

### Vom allgemeinen Connector {#from-generic-connector}

Bei Auswahl des **[!UICONTROL allgemeinen]** Connectors sollten Sie über einen benutzerdefinierten JavaScript-Connector verfügen, der sich an die jeweilige Situation anpasst.

Wenn Sie wissen, dass dieser Connector bereits das SMPP-Protokoll verwendet, können Sie zum **[!UICONTROL erweiterten allgemeinen SMPP]**-Connector migrieren. Falls nicht, erkundigen Sie sich bei Ihrem Provider, ob er das SMPP-Protokoll unterstützt, und richten Sie mithilfe eines Beraters einen neuen Connector ein.

Von Ihrem **[!UICONTROL allgemeinen]** Connector können Sie Folgendes auf Ihr neu erstelltes **[!UICONTROL erweitertes SMPP]**-Konto übertragen:

![](assets/smpp_generic.png)

Im Tab **[!UICONTROL Verbindungsparameter]**:

* **[!UICONTROL Konto]**
* **[!UICONTROL Passwort]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### Vom allgemeinen SMPP-Connector {#from-generic-smpp-connector}

Von Ihrem **[!UICONTROL allgemeinen SMPP]**-Connector können Sie Folgendes auf Ihr neu erstelltes **[!UICONTROL erweitertes SMPP]**-Konto übertragen:

![](assets/smpp_generic_2.png)

Im Tab **[!UICONTROL Verbindungsparameter]**:

* **[!UICONTROL Konto]**
* **[!UICONTROL Passwort]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL Systemtyp]**

Im Tab **[!UICONTROL SMPP-Kanaleinstellungen]**:

* **[!UICONTROL Anrufernummer]**
* **[!UICONTROL Anrufer-NPI]**
* **[!UICONTROL Empfänger-NPI]**
* **[!UICONTROL Anrufer-TON]**
* **[!UICONTROL Empfänger-TON]**

Im Tab **[!UICONTROL Kodierungs-Mapping]**:

* **[!UICONTROL Kodierung ausgehender SMS]**

Im Tab **[!UICONTROL SMSC-Besonderheiten]**:

* **[!UICONTROL Kodierung bei Versand]** entspricht dem **[!UICONTROL ID-Format in der MT-Quittierung (resp)]**
* **[!UICONTROL Kodierung bei Versand]** entspricht dem **[!UICONTROL ID-Format im SR]**

### Vom Sybase365-Connector {#from-sybase}

Von Ihrem **[!UICONTROL Sybase365]**-Connector können Sie Folgendes auf Ihr neu erstelltes **[!UICONTROL erweitertes SMPP]**-Konto übertragen:

![](assets/smpp_3.png)

Im Tab **[!UICONTROL Verbindungsparameter]**:

* **[!UICONTROL Konto]**
* **[!UICONTROL Passwort]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL Systemtyp]**

### Vom CLX-Connector {#from-clx}

Von Ihrem **[!UICONTROL CLX]**-Connector können Sie Folgendes auf Ihr neu erstelltes **[!UICONTROL erweitertes SMPP]**-Konto übertragen:

![](assets/smpp_4.png)

Im Tab **[!UICONTROL Verbindungsparameter]**:

* **[!UICONTROL Konto]**
* **[!UICONTROL Passwort]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL Systemtyp]**

Im Tab **[!UICONTROL SMPP-Kanaleinstellungen]**:

* **[!UICONTROL Anrufernummer]**

Im Tab **[!UICONTROL SMSC-Besonderheiten]**:

* **[!UICONTROL Kodierung bei Versand]** entspricht dem **[!UICONTROL ID-Format in der MT-Quittierung (resp)]**
* **[!UICONTROL Kodierung bei Versand]** entspricht dem **[!UICONTROL ID-Format im SR]**

### Vom Tele2-Connector {#from-tele2}

Von Ihrem **[!UICONTROL Tele2]**-Connector können Sie Folgendes auf Ihr neu erstelltes **[!UICONTROL erweitertes SMPP]**-Konto übertragen:

![](assets/smpp_6.png)

Im Tab **[!UICONTROL Verbindungsparameter]**:

* **[!UICONTROL Konto]**
* **[!UICONTROL Passwort]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL Systemtyp]**

Im Tab **[!UICONTROL SMPP-Kanaleinstellungen]**:

* **[!UICONTROL Anrufernummer]**
* **[!UICONTROL Anrufer-NPI]**
* **[!UICONTROL Empfänger-NPI]**
* **[!UICONTROL Anrufer-TON]**

Im Tab **[!UICONTROL Kodierungs-Mapping]**:

* **[!UICONTROL Kodierung ausgehender SMS]**

### Vom O2-Connector {#from-O2}

Von Ihrem **[!UICONTROL O2]**-Connector können Sie Folgendes auf Ihr neu erstelltes **[!UICONTROL erweitertes SMPP]**-Konto übertragen:

![](assets/smpp_5.png)

Im Tab **[!UICONTROL Verbindungsparameter]**:

* **[!UICONTROL Konto]**
* **[!UICONTROL Passwort]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL Systemtyp]**

Im Tab **[!UICONTROL SMPP-Kanaleinstellungen]**:

* **[!UICONTROL Anrufernummer]**
* **[!UICONTROL Anrufer-NPI]**
* **[!UICONTROL Empfänger-NPI]**
* **[!UICONTROL Anrufer-TON]**
* **[!UICONTROL Empfänger-TON]**
