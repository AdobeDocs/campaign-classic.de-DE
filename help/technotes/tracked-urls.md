---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 65ff09dd8ded029178c4c85489bf01ef80d16e8d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 15%

---

# Signaturproblem für verfolgte URLs {#tracked-urls}

Nach den letzten Änderungen können verfolgte URLs fehlschlagen, wenn die URL-Signatur in der Kampagne aktiv ist. Einige Postfächer können stärker betroffen sein als andere, da einige Firmen über spezielle Sicherheitstools verfügen, die sich auf Links auswirken und den URL-Signaturmechanismus ändern können.

Daher empfiehlt Adobe, den Signaturmechanismus für Verfolgungslinks zu deaktivieren. Mit diesem Verfahren werden alte Tracking-Links mit Ausnahme der Links behoben, die mit einem Escape der Dublette empfangen wurden.

Beachten Sie, dass Links zu Abmeldungen wie alle anderen Links fehlschlagen können. Die Häufigkeit ist von Host zu Host unterschiedlich, beträgt jedoch weniger als 1 %.

**Sind Sie betroffen?**

Zur Verbesserung der Sicherheit wurde der Signaturmechanismus für Links in E-Mails in [Kampagne Gold Standard 8](../rn/using/gold-standard.md#gs8) - April 2020 eingeführt - und ist standardmäßig für alle Kunden aktiviert, die Build 19.1.4 (9032@3a9dc9c) und Kampagne 20.2 starten.

Wenn Ihre Umgebung mit einer der folgenden Versionen ausgeführt wird, können Sie betroffen sein:

* Gold Standard 7 bis 11. [Mehr dazu](../rn/using/gold-standard.md)
* Kampagnen 21.1.1 bis 21.1.2. [Mehr dazu](../rn/using/latest-release.md)
* Kampagnen 20.3.1 bis 20.3.3. [Mehr dazu](../rn/using/release--20-3.md)
* Kampagnen 20.2.1 bis 20.2.3. [Mehr dazu](../rn/using/release--20-2.md)
* Kampagnen 20.1.1 bis 21.1.3. [Mehr dazu](../rn/using/release--20-1.md)
* Kampagnen 19.2.2 bis 19.2.3. [Mehr dazu](../rn/using/release--19-2.md)
* Kampagnen 19.1.5 bis 19.1.7. [Mehr dazu](../rn/using/release--19-1.md)

Erfahren Sie [in diesem Abschnitt](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version), wie Sie Ihre Version überprüfen.

**Wie wird die Aktualisierung durchgeführt?**

Als **gehosteter Kunde** arbeitet die Adobe mit Ihnen zusammen, um Ihre Konfiguration in Kürze zu aktualisieren.

Als **Vor-Ort-/Hybrid-Kunde** müssen Sie Ihre Konfiguration aktualisieren.

Gehen Sie wie folgt vor:

1. Ändern Sie in der Konfigurationsdatei [server](../installation/using/the-server-configuration-file.md) (serverConf.xml) **signEmailLinks** in **false**.
1. Starten Sie den **nlserver**-Dienst neu.
1. Starten Sie auf dem Tracking-Server den Webserver neu (Apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Die Datei **config-`<instance>`.xml** setzt die **serverConf.xml**-Einstellungen außer Kraft. Wenn **signEmailLinks** in **config-`<instance>`.xml** vorhanden ist (wobei **instance** der Name Ihrer Instanz ist), muss es auch in **false** umgewandelt werden.


**Wie wirkt sich das aus?**

Die Wartungsarbeiten erfordern eine Ausfallzeit von maximal 25 Minuten. Während dieses Zeitraums funktionieren nicht alle Versand, Verfolgungslinks und API-Aufrufe.

Nach Abschluss der Aktualisierung funktionieren alle Links erwartungsgemäß.

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

