---
product: campaign
title: Problem mit Signaturen getrackter URLs
description: Problem mit Signaturen getrackter URLs
feature: Technote
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 100%

---

# Problem mit Signaturen getrackter URLs {#tracked-urls}



Im Zuge der jüngsten Änderungen kann bei getrackten URLs ein Fehler auftreten, wenn die Signatur für diese URLs in Campaign aktiv ist. Postfächer, bei denen spezielle Sicherheits-Tools verwendet werden, die sich auf Links auswirken und den Mechanismus für URL-Signaturen verändern, können hiervon stärker betroffen sein.

Es wird daher empfohlen, den Signaturmechanismus für Tracking-Links zu deaktivieren. Auf diese Weise wird das Problem bei alten Tracking-Links behoben (mit Ausnahme von empfangenden Links, die ein doppeltes Escape-Zeichen enthalten).

Es gilt zu beachten, dass der Fehler bei Abmelde-Links ebenso auftreten kann wie bei allen anderen Links. Die Auftrittshäufigkeit ist dabei von Host zu Host unterschiedlich, beträgt jedoch weniger als 1 %.

**Sind Sie betroffen?**

Im April 2020 wurde [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) zur Verbesserung der Sicherheit um den Signaturmechanismus für Tracking-Links in E-Mails erweitert. Für Kunden, die Build 19.1.4 (9032@3a9dc9c) oder höher bzw. Campaign 20.2 verwenden, ist der Mechanismus standardmäßig aktiviert.

Kunden, deren Umgebung auf einer der folgenden Versionen basiert, sind möglicherweise betroffen:

* Gold Standard 8 bis 11. [Mehr dazu](../../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1 (Build 9277) bis Version 21.1.2 (Build 9282). [Mehr dazu](../../rn/using/latest-release.md)
* Campaign 20.3.1 (Build 9228) bis Version 20.3.3 (Build 9234).
* Campaign 20.2.1 (Build 9178) bis Version 20.2.4 (Build 9187).
* Campaign 20.1.1 (Build 9122) bis Version 21.1.3 (Build 9124). 
* Campaign 19.2.2 (Build 9080) bis Version 19.2.3 (Build 9081).
* Campaign 19.1.5 (Build 9033) bis Version 19.1.7 (Build 9036).


[In diesem Abschnitt](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) erfahren Sie, wie Sie Ihre Version überprüfen.

**Wie wird die Aktualisierung durchgeführt?**

Mit **gehosteten Kunden** arbeitet Adobe direkt zusammen, um die Aktualisierung ihrer Konfiguration zeitnah abzuschließen.

Als **On-Premise-/Hybrid-Kunde** müssen Sie Ihre Konfiguration eigenständig aktualisieren.

Gehen Sie dazu wie folgt vor:

1. Ändern Sie in der [Server-Konfigurationsdatei](../../installation/using/the-server-configuration-file.md) (serverConf.xml) den Eintrag für **signEmailLinks** in **false**.
1. Starten Sie den **nlserver**-Service neu.
1. Starten Sie den Webserver (apache2 unter Debian, httpd unter CentOS/RedHat, IIS unter Windows) auf dem Trackingserver neu.

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Mit der Datei **config-`<instance>`.xml** werden die in **serverConf.xml** enthaltenen Einstellungen überschrieben. Sofern der Eintrag **signEmailLinks** in **config-`<instance>`.xml** vorhanden ist (wobei **instance** den Namen Ihrer Instanz angibt), muss dieser ebenfalls in **false** geändert werden.
>

**Wie wirkt sich das aus?**

Für den Wartungsvorgang ist eine Stillstandszeit von maximal 25 Minuten einzuplanen. Während dieser funktionieren Versand, Tracking-Links und API-Aufrufe nicht.

Nach Abschluss der Aktualisierung funktionieren alle Links wieder ordnungsgemäß.

>[!NOTE]
>
>Wenden Sie sich bei Fragen zu diesen Änderungen an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>
