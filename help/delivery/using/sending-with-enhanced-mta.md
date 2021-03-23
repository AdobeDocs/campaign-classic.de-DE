---
solution: Campaign Classic
product: campaign
title: Mit dem Enhanced MTA in Adobe Campaign Classic senden
description: Erfahren Sie mehr über den Umfang und die Besonderheiten des E-Mail-Versands mit dem Enhanced MTA in Adobe Campaign.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '1962'
ht-degree: 99%

---


# Mit dem Enhanced MTA senden {#sending-with-enhanced-mta}

Der **Adobe Campaign Enhanced MTA** (Mail Transfer Agent) bietet eine erweiterte Versandinfrastruktur, die Verbesserungen bei Zustellbarkeit, Reputation, Durchsatz, Reporting, Bounce-Behandlung, IP-Anfangsphase und Verwaltung der Verbindungsparameter ermöglicht.

Er wurde implementiert, um die Skalierbarkeit zu verbessern, den Versanddurchsatz zu erhöhen und mehr E-Mails schneller zu senden. Erreicht wird dies durch neue adaptive Versandtechniken, die die Einstellungen für den E-Mail-Versand in Echtzeit auf der Grundlage von Rückmeldungen von ISPs (Internetanbietern) ändern.

>[!IMPORTANT]
>
>Der Adobe Campaign Enhanced MTA ist nur für Kunden von gehosteten oder hybriden Campaign Classic-Bereitstellungen verfügbar. On-Premise-Installationen von Campaign Classic können nicht für die Verwendung des Enhanced MTA aktualisiert werden.

Wenn Ihnen eine Campaign Classic-Instanz nach September 2018 bereitgestellt wurde, verwenden Sie den Enhanced MTA. Alle anderen Campaign Classic-Kunden finden weitere Information in den [häufig gestellten Fragen](#enhanced-mta-faq) weiter unten.

Die Implementierung des Enhanced MTA kann sich auf einige der bestehenden Campaign-Funktionen auswirken. Weitere Informationen finden Sie unter den [Besonderheiten des Enhanced MTA](#enhanced-mta-impacts).

>[!NOTE]
>
>Wenn Sie ein Endbenutzer von Adobe Campaign sind und wissen möchten, ob Ihre Instanz auf den Enhanced MTA aktualisiert wurde, wenden Sie sich an Ihren internen Campaign-Administrator.

## Häufig gestellte Fragen {#enhanced-mta-faq}

### Nutzung und Vorteile

**Was ist der Enhanced MTA?**

Adobe Campaign kann jetzt auf einen neuen MTA (Mail Transfer Agent) aktualisiert werden, der den kommerziellen E-Mail-MTA von SparkPost namens **Momentum** verwendet.

Momentum steht für eine innovative, hochleistungsfähige MTA-Technologie, die eine intelligentere Behandlung von Bounce-E-Mails und eine automatische Zustellbarkeitsoptimierung beinhaltet, die den Absendern hilft, optimale Zustellraten im Posteingang zu erreichen und zu erhalten. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Was sind die Vorteile?**

* Adobe Campaign-Kunden, die den Enhanced MTA einsetzen, haben eine <!--300%-->massive Steigerung der Gesamtdurchsatzgeschwindigkeit und eine <!--90%+-->deutliche Reduzierung der Softbounces festgestellt.
* Der Enhanced MTA nutzt die neueste MTA-Technologie, um Ihnen optimale Durchsatzgeschwindigkeiten für Ihren E-Mail-Versand zu bieten.
* Durch die sofortige und automatische Anpassung an die Rückmeldungen, die er erhält, sorgt er außerdem für einen genaueren und intelligenteren E-Mail-Versand mit Versanddaten in Echtzeit.

**Kann ich den nativen Adobe Campaign-MTA und den Enhanced MTA gleichzeitig verwenden?**

Nein. Nach der Aktualisierung Ihrer Instanz kann nur der Enhanced MTA kann für Ihren E-Mail-Versand verwendet werden.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Aktualisierung auf den Enhanced MTA

**Was ist für eine Aktualisierung auf den Enhanced MTA erforderlich?**

Wenn Ihnen eine Campaign Classic-Instanz nach September 2018 bereitgestellt wurde, ist keine Aktion erforderlich, da Sie bereits den Enhanced MTA nutzen.

Bei allen anderen gehosteten oder teilweise gehosteten (hybriden) Kunden wird sich das Adobe Campaign-Team melden, um einen Termin für die Migration zu koordinieren und Details zu den entsprechenden Schritten bereitzustellen, die für die Migration erforderlich sind.

>[!IMPORTANT]
>
>Der Enhanced MTA ist nicht für On-Premise-Installationen verfügbar.

**Wie wird meine Instanz auf den Enhanced MTA aktualisiert?**

Der gesamte Prozess für Ihre gehosteten Instanzen erfordert einige Minuten Ausfallzeit. Adobe überwacht den E-Mail-Durchsatz und die Zustellbarkeit bis zu 24 Stunden nach der Aktualisierung, um etwaige Auswirkungen auf Ihre E-Mail-Sendungen zu beurteilen.

Sollten Probleme festgestellt werden, kann Adobe Ihre Instanz schnell und vorübergehend wieder auf den nativen Adobe Campaign-MTA zurücksetzen.

Derzeit wirkt sich der Enhanced MTA nur auf den E-Mail-Kanal aus. Ihre Push-Benachrichtigungen und SMS-Sendungen verwenden weiterhin den nativen Campaign-MTA und sind in keiner Weise von der Aktualisierung betroffen.

**Muss ich nach der Aktualisierung auf den Enhanced MTA das IP-Warmup erneut durchführen?**

Nein. Die Aktualisierung erfordert keinen Wechsel zu neuen IPs, sodass Sie Ihre bestehenden E-Mail-IPs nach IP-Warmup weiter verwenden können.

**Wirkt sich die Aktualisierung auf den Enhanced MTA auf laufende Kampagnen oder Sendungen aus?**

Alle Sendungen, die vor der Aktualisierung Ihrer Instanz auf den Enhanced MTA vorbereitet wurden, müssen erneut vorbereitet werden, damit Sie den neuen MTA ordnungsgemäß nutzen können.

Für Kunden, die die Transaktionsnachrichtenfunktionen von Adobe Campaign nutzen, werden alle API-Aufrufe zum Auslösen einer E-Mail während der sehr kurzen Ausfallzeit der Aktualisierung in eine Warteschlange gestellt und nach Abschluss der Aktualisierung versucht.

## Besonderheiten des Enhanced MTA {#enhanced-mta-impacts}

### Header des Enhanced MTA

Die neuesten Campaign Classic-Instanzen enthalten Code, der jeder Nachricht die erforderlichen Enhanced MTA-Header hinzufügt. Wenn Sie Adobe Campaign 19.1 (Build 9032) oder höher verwenden und dies nicht der Fall ist, müssen Sie den Parameter &quot;useMomentum=true&quot; der Konfiguration Ihrer Marketing-Instanz (in der Datei [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)) den Parameter &quot;useMomentum=true&quot; hinzufügen.

Wenn Sie jedoch eine ältere Instanz verwenden, die diesen Code nicht enthält, muss eine neue Typologieregel mit dem Namen **[!UICONTROL Typology Rule for Enhanced MTAs]** zu allen vorhandenen Typologien in Ihrer Campaign-Instanz hinzugefügt werden.
Diese Regel wird von einem **[!UICONTROL Typologiepaket]** hinzugefügt, das im Rahmen der Aktualisierung auf den Enhanced MTA installiert wurde.

>[!IMPORTANT]
>
>Wenn Sie diese Typologieregel in Ihren Typologien sehen, dürfen Sie sie nicht löschen oder in irgendeiner Weise ändern. Andernfalls könnten Ihre E-Mail-Sendungen beeinträchtigt werden.

Dieses **[!UICONTROL Typologiepaket]** muss in der Marketing-Instanz von Adobe Campaign installiert sein.

Wenn Sie ein Kunde mit einer hybriden Bereitstellung sind, erhalten Sie vom Adobe Campaign-Team Anweisungen zur Installation des **[!UICONTROL Typologiepakets]** in Ihrer Marketing-Instanz im Rahmen der Aktualisierung auf den Enhanced MTA. Wenden Sie sich an Ihren Kundenbetreuer, um die vollständigen Anweisungen zu erhalten.

>[!IMPORTANT]
>
>Die Anweisungen des Adobe Campaign-Teams zur Installation des **[!UICONTROL Typologiepakets]** sollten sorgfältig befolgt werden. Andernfalls kann es zu größeren Problemen mit Ihren IPs kommen, die zum Senden von E-Mails verwendet werden.

Weitere Informationen zu Typologien finden Sie in [diesem Abschnitt](../../campaign/using/about-campaign-typologies.md).

### Neue MX-Regeln

Die Regeln der MX-Verwaltung für den Versanddurchsatz sind nicht mehr in Gebrauch. Der Enhanced MTA hat seine eigenen MX-Regeln. Mit diesen kann Ihr Durchsatz anhand Ihrer historischen E-Mail-Reputation und dem Echtzeit-Feedback, das von den Domains stammt, von denen Sie E-Mails senden, angepasst werden.

Weiterführende Informationen zur MX-Konfiguration finden Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#mx-configuration).

### Bounce-Qualifizierung

Die Bounce-Qualifizierungen in der Tabelle **[!UICONTROL Versandlogqualifizierung]** in Campaign werden nicht mehr für Fehlermeldungen bei **synchronen** Zustellungsfehlern verwendet. Der Enhanced MTA bestimmt den Bounce-Typ und die Qualifizierung und sendet diese Informationen an Campaign zurück.

>[!NOTE]
>
>Der Enhanced MTA qualifiziert den SMTP-Bounce und sendet diese Qualifizierung zurück an Campaign in Form eines Bouncecodes, der in Campaign einem Bounce-Grund und einer Bounce-Qualifikation zugeordnet ist.

Weitere Informationen zur Bounce-Qualifizierung finden Sie in [diesem Abschnitt](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Versanddurchsatz

Das Diagramm für den Campaign-Versanddurchsatz zeigt nicht mehr den Durchsatz an Ihre E-Mail-Empfänger an. Dieses Diagramm zeigt jetzt die Durchsatzgeschwindigkeit für die Weiterleitung Ihrer Nachrichten von Campaign an den Enhanced MTA an.

Weitere Informationen zum Versanddurchsatz finden Sie in [diesem Abschnitt](../../reporting/using/global-reports.md#delivery-throughput).

### Gültigkeitszeitraum

Die Einstellung für den Gültigkeitszeitraum in Ihren Campaign-Sendungen wird vom Enhanced MTA nur verwendet, wenn sie auf **3,5 Tage oder weniger** eingestellt ist. Wenn Sie in Campaign einen Wert von mehr als 3,5 Tagen definieren, wird dieser nicht berücksichtigt.

Wenn der Gültigkeitszeitraum in Campaign beispielsweise auf den Standardwert von 5 Tagen eingestellt ist, werden Softbounce-Nachrichten in die Warteschlange für Wiederholungsversuche des Enhanced MTA aufgenommen und nur bis zu 3,5 Tage ab dem Zeitpunkt, an dem die Nachricht den Enhanced MTA erreicht hat, erneut versucht. In diesem Fall wird der in Campaign eingestellte Wert nicht verwendet.

Sobald eine Nachricht 3,5 Tage lang in der Warteschlange des Enhanced MTA war und nicht gesendet werden konnte, wird sie mit einem Timeout beendet; ihr Status wird von **[!UICONTROL Gesendet]** in **[!UICONTROL Fehlgeschlagen]** geändert (in den Versandlogs).

Weitere Informationen zum Gültigkeitszeitraum finden Sie in [diesem Abschnitt](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### DKIM-Signierung

Die Signierung der DKIM-E-Mail-Authentifizierung (DomainKeys Identified Mail) erfolgt durch den Enhanced MTA. Das DKIM-Signieren durch den nativen Campaign-MTA wird im Rahmen des Enhanced MTA-Upgrades in der Tabelle &quot;Domain-Verwaltung&quot; deaktiviert.
Weitere Informationen zu DKIM finden Sie im Best Practice Guide [Adobe Deliverability Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Berichte zum Versanderfolg

In der Ansicht **[!UICONTROL Zusammenfassung]** des [Dashboards](../../delivery/using/delivery-dashboard.md) eines E-Mail-Versands beginnt der **[!UICONTROL Erfolgsprozentsatz]** bei 100 % und sinkt dann allmählich während des [Gültigkeitszeitraums](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period) des Versands, da die Soft- und Hardbounces vom Enhanced MTA an Campaign zurückgemeldet werden.

Alle Nachrichten werden in den [Versandlogs](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) als **[!UICONTROL Gesendet]** angezeigt, sobald sie erfolgreich von Campaign an den Enhanced MTA weitergeleitet wurden. Sie bleiben in diesem Status, es sei denn, ein [Bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) wird für diese Nachricht vom Enhanced MTA an Campaign zurückgemeldet.

Wenn vom Enhanced MTA Hardbounces zurückgemeldet werden, ändert sich der Status dieser Nachrichten von **[!UICONTROL Gesendet]** in **[!UICONTROL Fehlgeschlagen]** und der **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend verringert.

Wenn vom Enhanced MTA Softbounces zurückgemeldet werden, werden diese Nachrichten weiterhin als **[!UICONTROL Gesendet]** angezeigt und der **[!UICONTROL Erfolgsprozentsatz]** wird noch nicht aktualisiert. Nachrichten, bei denen ein Softbounce aufgetreten ist, erhalten dann während des Gültigkeitszeitraums des Versands [einen erneuten Zustellversuch](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure):

* Wenn ein erneuter Versuch vor Ende der Gültigkeitszeitraums erfolgreich ist, bleibt der Nachrichtenstatus weiterhin **[!UICONTROL Gesendet]** und der **[!UICONTROL Erfolgsprozentsatz]** unverändert.

* Andernfalls ändert sich der Status in **[!UICONTROL Fehlgeschlagen]** und der **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend verringert.

Daher sollten Sie bis zum Ende des Gültigkeitszeitraums warten, um den endgültigen **[!UICONTROL Erfolgsprozentsatz]** und die endgültige Anzahl der tatsächlich **[!UICONTROL gesendeten]** und **[!UICONTROL fehlgeschlagenen]** Nachrichten anzuzeigen.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Email Feedback Service (Beta) {#email-feedback-service}

Mit der EFS-Funktion (Email Feedback Service) wird der Status jeder E-Mail genau gemeldet, da Feedback direkt vom erweiterten MTA (Message Transfer Agent) erfasst wird.

>[!IMPORTANT]
>
>Der Email Feedback Service ist derzeit als Betafunktion verfügbar.
>
>Wenn Sie an diesem Beta-Programm teilnehmen möchten, füllen Sie [dieses Formular](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) aus, und wir werden uns bei Ihnen melden.

Nachdem der Versand gestartet wurde, ändert sich der **[!UICONTROL Erfolgsprozentsatz]** nicht, wenn die Nachricht erfolgreich von Campaign an den Enhanced MTA weitergeleitet wurde.

<!--![](assets/efs-sending.png)-->

Die Versandlogs zeigen den Status **[!UICONTROL Vom Dienstleister berücksichtigt]** für jede Zieladresse an.

<!--![](assets/efs-pending.png)-->

Wenn die Nachricht tatsächlich den Zielgruppenprofilen zugestellt wird und diese Informationen in Echtzeit vom Enhanced MTA gemeldet werden, zeigen die Versandlogs für jede Adresse, die die Nachricht erfolgreich erhalten hat, den Status **[!UICONTROL Gesendet]** an. Der **[!UICONTROL Erfolgsprozentsatz]** wird mit jedem erfolgreichen Versand entsprechend erhöht.

Wenn Hardbounces vom Enhanced MTA zurückgemeldet werden, ändert sich ihr Log-Status von **[!UICONTROL Vom Dienstleister berücksichtigt]** in **[!UICONTROL Fehlgeschlagen]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Wenn Softbounces vom Enhanced MTA zurückgemeldet werden, bleibt ihr Log-Status unverändert (**[!UICONTROL Vom Dienstleister berücksichtigt]**): Nur der [Fehlergrund](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) wird aktualisiert<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. Der **[!UICONTROL Erfolgsprozentsatz]** bleibt unverändert. Nachrichten, bei denen ein Softbounce aufgetreten ist, erhalten dann während des [Gültigkeitszeitraums](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period) des Versands einen erneuten Zustellversuch:

* Wenn ein erneuter Versuch vor Ende der Gültigkeitszeitraums erfolgreich ist, ändert sich der Nachrichtenstatus in **[!UICONTROL Gesendet]** und der **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend erhöht.

* Andernfalls ändert sich der Status in **[!UICONTROL Fehlgeschlagen]**. Der **[!UICONTROL Erfolgsprozentsatz]** <!--and **[!UICONTROL Bounces + errors]** -->bleibt unverändert.

>[!NOTE]
>
>Weitere Informationen zu Hard- und Softbounces finden Sie in [diesem Abschnitt](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Weitere Informationen zu zusätzlichen Zustellversuchen nach einem vorübergehend fehlgeschlagenen Versand finden Sie in [diesem Abschnitt](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


Die folgenden Tabellen zeigen die Änderungen der KPIs und Versandlogstatus, die durch die EFS-Funktion eingeführt wurden.

**Mit Email Feedback Service**

| Schritt im Versandprozess | KPI-Zusammenfassung | Versandlogstatus |
|--- |--- |--- |
| Nachricht wird erfolgreich von Campaign an den Enhanced MTA weitergeleitet | **[!UICONTROL Erfolgsprozentsatz]** wird nicht angezeigt (beginnt bei 0 %) | Vom Dienstleister berücksichtigt |
| Hardbounces werden vom Enhanced MTA zurückgemeldet. | Keine Änderung des **[!UICONTROL Erfolgsprozentsatzes]** | Fehlgeschlagen |
| Softbounces werden vom erweiterten MTA zurückgemeldet. | Keine Änderung des **[!UICONTROL Erfolgsprozentsatzes]** | Vom Dienstleister berücksichtigt |
| Weitere Zustellversuche von Nachrichten, bei denen ein Softbounce aufgetreten ist, sind erfolgreich | **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend erhöht | Gesendet |
| Weitere Zustellversuche von Nachrichten, bei denen ein Softbounce aufgetreten ist, schlagen fehl | Keine Änderung des **[!UICONTROL Erfolgsprozentsatzes]** | Fehlgeschlagen |

**Ohne Email Feedback Service**

| Schritt im Versandprozess | KPI-Zusammenfassung | Versandlogstatus |
|--- |--- |--- |
| Nachricht wird erfolgreich von Campaign an den Enhanced MTA weitergeleitet | **[!UICONTROL Erfolgsprozentsatz]** beginnt bei 100 % | Gesendet |
| Hardbounces werden vom Enhanced MTA zurückgemeldet. | **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend verringert | Fehlgeschlagen |
| Softbounces werden vom erweiterten MTA zurückgemeldet. | Keine Änderung des **[!UICONTROL Erfolgsprozentsatzes]** | Gesendet |
| Weitere Zustellversuche von Nachrichten, bei denen ein Softbounce aufgetreten ist, sind erfolgreich | Keine Änderung des **[!UICONTROL Erfolgsprozentsatzes]** | Gesendet | **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend erhöht | Gesendet |
| Weitere Zustellversuche von Nachrichten, bei denen ein Softbounce aufgetreten ist, schlagen fehl | **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend verringert | Fehlgeschlagen |
