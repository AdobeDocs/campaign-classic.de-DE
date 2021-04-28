---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: e1b09767a8eed3a7dc90e4db0429238d86d39570
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 14%

---

# Signaturproblem für verfolgte URLs {#tracked-urls}

Nach den letzten Änderungen können verfolgte URLs fehlschlagen, wenn die URL-Signatur in der Kampagne aktiv ist. Einige Postfächer können stärker betroffen sein als andere, da einige Firmen über spezielle Sicherheitstools verfügen, die sich auf Links auswirken und den URL-Signaturmechanismus ändern können.

Daher empfiehlt Adobe, den Signaturmechanismus für Verfolgungslinks zu deaktivieren. Mit diesem Verfahren werden alte Tracking-Links mit Ausnahme der Links behoben, die mit einem Escape der Dublette empfangen wurden.

Beachten Sie, dass Links zu Abmeldungen wie alle anderen Links fehlschlagen können. Die Häufigkeit ist von Host zu Host unterschiedlich, beträgt jedoch weniger als 1 %.

**Sind Sie betroffen?**

Zur Verbesserung der Sicherheit wurde der Signaturmechanismus für Links in E-Mails in [Kampagne Gold Standard 8](../rn/using/gold-standard.md#gs8) - April 2020 eingeführt - und ist standardmäßig für alle Kunden aktiviert, die Build 19.1.4 (9032@3a9dc9c) und Kampagne 20.2 starten.

Wenn Ihre Umgebung mit einer der folgenden Versionen ausgeführt wird, können Sie betroffen sein:

* Gold Standard 8 bis 11. [Mehr dazu](../rn/using/gold-standard.md#gs-8)
* Kampagne 21.1.1 (Build 9277) bis Version 21.1.2 (Build 9282). [Mehr dazu](../rn/using/latest-release.md)
* Kampagne 20.3.1 (Build 9228) bis Version 20.3.3 (Build 9234). [Mehr dazu](../rn/using/release--20-3.md)
* Kampagne 20.2.1 (Build 9178) bis Version 20.2.3 (Build 9182). [Mehr dazu](../rn/using/release--20-2.md)
* Kampagne 20.1.1 (Build 9122) bis Version 21.1.3 (Build 9124). [Mehr dazu](../rn/using/release--20-1.md)
* Kampagne 19.2.2 (Build 9080) bis Version 19.2.3 (Build 9081). [Mehr dazu](../rn/using/release--19-2.md)
* Kampagne 19.1.5 (Build 9033) bis Version 19.1.7 (Build 9036). [Mehr dazu](../rn/using/release--19-1.md)

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

