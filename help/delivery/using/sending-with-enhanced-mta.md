---
solution: Campaign Classic
product: campaign
title: Entsendung mit der erweiterten MTA in Adobe Campaign Classic
description: Erfahren Sie mehr über den Umfang und die Besonderheiten des Versands von E-Mails mit dem Adobe Campaign Enhanced MTA.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 07ed17a093cb6fb2d7aae376325a127c61b1dcc2
workflow-type: tm+mt
source-wordcount: '1427'
ht-degree: 8%

---


# Senden mit dem erweiterten MTA {#sending-with-enhanced-mta}

Der **Adobe Campaign Enhanced MTA** (Mail Transfer Agent) bietet eine aktualisierte Sendepritsche, die eine verbesserte Bereitstellbarkeit, Reputation, Durchsatz, Berichte, Absprungbehandlung, IP-Rampeneinstieg und Verbindungseinstellungsverwaltung ermöglicht.

Es wurde implementiert, um die Skalierbarkeit zu verbessern, den Durchsatz von Versänden zu erhöhen und mehr E-Mails schneller zu versenden. Dies wird durch neue Techniken für den adaptiven Versand erreicht, die die Einstellungen für das Senden von E-Mails in Echtzeit ändern, basierend auf Feedback von Internet-Dienstleistern.

>[!IMPORTANT]
>
>Das Adobe Campaign Enhanced MTA ist nur für Campaign Classic- oder Hybridkunden verfügbar. Vor Ort installierte Campaign Classic können nicht für die Verwendung der erweiterten MTA aktualisiert werden.

Wenn Sie nach September 2018 eine Campaign Classic-Instanz bereitgestellt haben, verwenden Sie die erweiterte MTA. Für alle anderen Campaign Classic-Kunden finden Sie unter [Häufig gestellte Fragen](#enhanced-mta-faq) weitere Informationen.

Die erweiterte MTA-Implementierung kann sich auf einige der bestehenden Funktionen der Kampagne auswirken. Weitere Informationen finden Sie unter [Erweiterte MTA-Eigenschaften](#enhanced-mta-impacts).

## Häufig gestellte Fragen {#enhanced-mta-faq}

### Nutzung und Nutzen

**Was ist die erweiterte MTA?**

Adobe Campaign kann jetzt aktualisiert werden, um einen neuen MTA (Mail Transfer Agent) zu verwenden, der SparkPost&#39;s kommerzielle E-Mail-MTA mit dem Namen **Momentum** ausführt.

Momentum steht für innovative Hochleistungs-MTA-Technologie, die eine intelligentere Absprungbearbeitung und eine automatisierte Bereitstellungsoptimierung umfasst, die Absendern dabei hilft, optimale Inbox-Versand zu erzielen und zu erhalten. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Was sind die Vorteile?**

* Adobe Campaign-Clients, die die erweiterte MTA verwenden, verzeichnen einen massiven Anstieg der Gesamtdurchsatzgeschwindigkeit und eine erhebliche Verringerung der weichen Absprünge.<!--300%--><!--90%+-->
* Die erweiterte MTA verwendet die neueste MTA-Technologie, um Ihnen die optimale Durchsatzgeschwindigkeit für Ihren E-Mail-Versand zu bieten.
* Durch die sofortige und automatische Anpassung an das Feedback, das sie erhält, wird ein präziserer und intelligenter E-Mail-Versand mit Echtzeit-Versand-Daten sichergestellt.

**Kann ich die native Adobe Campaign-MTA und die erweiterte MTA gleichzeitig verwenden?**

Nein. Nur die erweiterte MTA kann für Ihre E-Mail-Versand verwendet werden, nachdem Ihre Instanz aktualisiert wurde.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Aktualisierung auf die erweiterte MTA

**Was ist erforderlich, um auf die erweiterte MTA zu aktualisieren?**

Wenn Sie nach September 2018 eine Campaign Classic-Instanz bereitgestellt haben, ist keine Aktion erforderlich, da Sie bereits die erweiterte MTA verwenden.

Bei allen anderen gehosteten oder teilweise gehosteten (Hybrid-) Kunden erreicht das Adobe Campaign-Team die Koordination eines Migrationsdatums und stellt die erforderlichen Schritte zur Migration zur Verfügung.

>[!IMPORTANT]
>
>Die erweiterte MTA steht nicht für lokale Installationen zur Verfügung.

**Wie wird die Aktualisierung meiner Instanz auf die erweiterte MTA durchgeführt?**

Der gesamte Prozess für Ihre gehosteten Instanzen erfordert einige Minuten Ausfallzeit. Adobe überwacht den E-Mail-Durchsatz und die Zustellbarkeit bis zu 24 Stunden nach der Aktualisierung, um etwaige Auswirkungen auf Ihre E-Mail-Versand zu bewerten.

Falls Probleme erkannt werden, kann die Adobe Ihre Instanz schnell und vorübergehend zurück auf das native Adobe Campaign-MTA setzen.

Derzeit betrifft die erweiterte MTA nur den E-Mail-Kanal. Ihre Push-Benachrichtigungen und SMS-Versand verwenden weiterhin die MTA der nativen Kampagne und sind von der Aktualisierung in keiner Weise betroffen.

**Muss ich die IP-Erwärmung nach einem Upgrade auf die erweiterte MTA erneut durchlaufen?**

Nein. Für die Aktualisierung ist kein Wechsel zu neuen IPs erforderlich, sodass Sie Ihre vorhandenen, gewärmten E-Mail-IPs weiterhin verwenden können.

**Wirkt sich die Aktualisierung auf die erweiterte MTA auf derzeit laufende Kampagnen oder Versand aus?**

Alle Versand, die vor der Aktualisierung Ihrer Instanz auf die Verwendung der erweiterten MTA vorbereitet wurden, müssen neu vorbereitet werden, damit die neue MTA ordnungsgemäß verwendet werden kann.

Für Kunden, die Adobe Campaign-Transaktionsnachrichten verwenden, werden alle API-Aufrufe an Trigger und E-Mails während der sehr kurzen Aktualisierungsausfälle in die Warteschlange gestellt und nach Abschluss der Aktualisierung versucht.

## Verbesserte MTA-Eigenschaften {#enhanced-mta-impacts}

### Verbesserte MTA-Kopfzeilen

Die neuesten Campaign Classic-Instanzen enthalten Code, der jeder Nachricht die erforderlichen erweiterten MTA-Kopfzeilen hinzufügt. Wenn Sie Adobe Campaign 19.1 (Build 9032) oder höher verwenden und dies nicht der Fall ist, müssen Sie den Parameter &quot;useMomentum=true&quot;zu Ihrer Marketinginstanzkonfiguration hinzufügen (in der Datei [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)).

Wenn Sie jedoch eine ältere Instanz verwenden, die diesen Code nicht enthält, muss eine neue Typologieregel mit dem Namen **[!UICONTROL Typologieregel für erweiterte MTAs]** zu allen vorhandenen Typologien in Ihrer Kampagne hinzugefügt werden.
Diese Regel wird von einem **[!UICONTROL Typology]**-Paket hinzugefügt, das im Rahmen der Aktualisierung auf die erweiterte MTA installiert wurde.

>[!IMPORTANT]
>
>Wenn Sie diese Typologieregel in Ihren Typologien sehen, löschen oder ändern Sie sie nicht in irgendeiner Weise. Andernfalls könnten Ihre E-Mail-Versand beeinträchtigt werden.

Dieses **[!UICONTROL Typology]**-Paket muss auf der Marketing-Instanz des Adobe Campaigns installiert sein.

Wenn Sie ein Hybrid-Client sind, gibt das Adobe Campaign-Team Ihnen Anweisungen, wie Sie das **[!UICONTROL Typology]**-Paket im Rahmen der Aktualisierung auf die erweiterte MTA auf Ihrer Marketing-Instanz installieren. Wenden Sie sich an Ihren Kundenbetreuer, um die vollständige Anleitung zu erhalten.

>[!IMPORTANT]
>
>Die Anweisungen des Adobe Campaign-Teams zur Installation des **[!UICONTROL Typology]**-Pakets sollten sorgfältig befolgt werden. Andernfalls treten möglicherweise große Probleme mit Ihren IPs auf, die zum Senden von E-Mails verwendet werden.

Weitere Informationen zu Typologien finden Sie in [diesem Abschnitt](../../campaign/using/about-campaign-typologies.md).

### Neue MX-Regeln

Die Durchsatzregeln für MX-Management-Versand werden nicht mehr verwendet. Die Enhanced MTA verfügt über eigene MX-Regeln, mit denen Sie Ihren Durchsatz nach Domäne auf Basis Ihres eigenen historischen E-Mail-Rufs und des Echtzeit-Feedbacks der Domänen, von denen Sie E-Mails senden, anpassen können.

Weiterführende Informationen zur MX-Konfiguration finden Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#mx-configuration).

### Absprungqualifikation

Die Absprungqualifikationen in der Kampagne **[!UICONTROL Versand-Protokollqualifizierung]** werden nicht mehr für **synchrone** Fehlermeldungen mit Versand-Fehlern verwendet. Der Enhanced MTA bestimmt den Bounce-Typ und die Qualifizierung und sendet diese Informationen an Campaign zurück.

>[!NOTE]
>
>Die erweiterte MTA qualifiziert den SMTP-Absprung und sendet diese Qualifikation in Form eines Absprungcodes, der einem Absprunggrund und einer Qualifikation für die Kampagne zugeordnet ist, an die Kampagne zurück.

Weitere Informationen zur Absprungqualifizierung finden Sie in [diesem Abschnitt](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Status mit verbesserter MTA gesendet

In der **[!UICONTROL Zusammenfassungs]**-Ansicht eines E-Mail-Versands [Dashboard](../../delivery/using/delivery-dashboard.md) gehen die **[!UICONTROL Beginn]** um 100% aus und gehen dann im gesamten Versand [Gültigkeitsdauer](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period) schrittweise zurück, da die weichen und festen Absprünge von der erweiterten MTA-Kampagne aus gemeldet werden.

Tatsächlich werden alle Meldungen in den [Versandprotokollen](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) als **[!UICONTROL Gesendet]** angezeigt, sobald sie erfolgreich von der Kampagne auf die erweiterte MTA übertragen wurden. Sie bleiben in diesem Status, es sei denn, ein [Bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) wird für diese Nachricht vom erweiterten MTA an Campaign zurückgemeldet.

Wenn Meldungen mit festem Absprung aus der erweiterten MTA zurückgesendet werden, ändert sich ihr Status von **[!UICONTROL Gesendet]** in **[!UICONTROL Fehlgeschlagen]** und der **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend verringert.

Wenn Meldungen mit weichem Zeilensprung aus der erweiterten MTA zurückgegeben werden, werden sie weiterhin als **[!UICONTROL Gesendet]** angezeigt und der **[!UICONTROL Erfolgsprozentsatz]** wird noch nicht aktualisiert. Nachrichten, bei denen ein Softbounce aufgetreten ist, erhalten dann während des Gültigkeitszeitraums des Versands [einen erneuten Zustellversuch](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure):

* Wenn ein erneuter Versuch vor Ende der Gültigkeitsdauer erfolgreich war, bleibt der Meldungsstatus weiterhin **[!UICONTROL Gesendet]** und der **[!UICONTROL Erfolg]**-Prozentsatz bleibt unverändert.

* Andernfalls ändert sich der Status in **[!UICONTROL Fehlgeschlagen]** und der **[!UICONTROL Erfolgsprozentsatz]** wird entsprechend verringert.

Daher sollten Sie bis zum Ende der Gültigkeitsdauer warten, um die finale **[!UICONTROL Erfolgsrate]** und die endgültige Anzahl der tatsächlich gesendeten **[!UICONTROL und]** Fehlgeschlagenen ]**Meldungen anzuzeigen.**[!UICONTROL 

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### Versanddurchsatz

Das Durchsatzdiagramm für Kampagnen-Versand zeigt den Durchsatz Ihrer E-Mail-Empfänger nicht mehr an. Dieses Diagramm zeigt nun die Durchsatzgeschwindigkeit für die Weiterleitung Ihrer Nachrichten von der Kampagne zur erweiterten MTA.

Weitere Informationen zum Durchsatz des Versands finden Sie in [diesem Abschnitt](../../reporting/using/global-reports.md#delivery-throughput).

### Gültigkeitszeitraum

Die Gültigkeitsdauer in Ihren Versänden für Kampagnen wird von der erweiterten MTA nur verwendet, wenn sie auf **3.5 Tage oder weniger** eingestellt ist. Wenn Sie einen Kampagne-Wert von mehr als 3,5 Tagen definieren, wird dieser nicht berücksichtigt.

Wenn die Gültigkeitsdauer beispielsweise auf den Standardwert von 5 Tagen in Kampagne gesetzt ist, werden Meldungen mit weichem Absprung in die Warteschlange für erweiterte MTA-Wiederholungen verschoben und erst 3,5 Tage nach Erreichen der erweiterten MTA erneut versucht. In diesem Fall wird der in der Kampagne eingestellte Wert nicht verwendet.

Sobald eine Nachricht 3,5 Tage lang in der Warteschlange des erweiterten MTA war und nicht gesendet werden konnte, wird sie mit einem Timeout beendet; ihr Status wird von **[!UICONTROL Gesendet]** in **[!UICONTROL Fehlgeschlagen]** geändert (in den Versandlogs).

Weitere Informationen zur Gültigkeitsdauer finden Sie in [diesem Abschnitt](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

### DKIM-Signatur

Die Signierung der DKIM-E-Mail-Authentifizierung (DomainKeys Identified Mail) erfolgt über die erweiterte MTA. Das DKIM-Signieren durch den nativen Campaign-MTA wird im Rahmen des Enhanced MTA-Upgrades in der Tabelle Domain-Verwaltung deaktiviert.
Weitere Informationen zu DKIM finden Sie in [diesem Abschnitt](../../delivery/using/technical-recommendations.md#dkim).