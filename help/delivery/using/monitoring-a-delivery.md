---
title: Sendungen beobachten
seo-title: Sendungen beobachten
description: Sendungen beobachten
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4c4e2cfaa9603c42e5e97de1e13318f8541921ca

---


# Sendungen beobachten{#monitoring-a-delivery}

Im **Versand-Dashboard** können Sie Sendungen beobachten und etwaige Probleme beim Nachrichtenversand erkennen.

**Verwandte Themen**

* [Ursachen von fehlgeschlagenen Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Funktionsweise der Quarantäneverwaltung](../../delivery/using/understanding-quarantine-management.md)
* [Best Practices beim Versand](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)
* [Erste-Schritte-Handbuch: Verwalten der Zustellbarkeit](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)

## Versand-Dashboard {#delivery-dashboard}

Sie können Versandinformationen aufrufen, indem Sie das Dashboard öffnen und auf die verschiedenen Tabs klicken.

Nach Abschluss des Versands kann der Inhalt der einzelnen Tabs nicht mehr verändert werden und steht nur zur Ansicht zur Verfügung.

![](assets/s_ncs_user_del_details.png)

### Versandzusammenfassung {#delivery-summary}

Die **[!UICONTROL Summary]** Registerkarte enthält die Merkmale der Bereitstellung: Lieferstatus, verwendeter Kanal, Angaben zum Absender, Betreff, Angaben zur Ausführung. Weitere Informationen finden Sie unter [Anzahl der gesendeten](#number-of-messages-sent)Nachrichten.

Über den **[!UICONTROL reports]** Link können Sie eine Reihe von Berichten zur Auslieferungsaktion anzeigen: allgemeiner Lieferbericht, detaillierter Bericht, Lieferbericht, Verteilung fehlgeschlagener Nachrichten, Öffnungsrate, Klicks und Transaktionen usw. Der Inhalt dieser Registerkarte kann entsprechend Ihren Anforderungen konfiguriert werden. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../reporting/using/delivery-reports.md).

### Protokolle und Versandverlauf {#delivery-logs-and-history}

Auf der **[!UICONTROL Delivery]** Registerkarte wird ein Verlauf der Vorfälle in dieser Bereitstellung angezeigt. Es enthält die Lieferprotokolle, d.h. die Liste der gesendeten Nachrichten und deren Status sowie die zugehörigen Meldungen.

Bei einer Lieferung können Sie (z. B.) nur Empfänger mit einer fehlgeschlagenen Lieferung oder einer Adresse in der Quarantäne anzeigen. Klicken Sie dazu auf die **[!UICONTROL Filters]** Schaltfläche und wählen Sie **[!UICONTROL By state]**. Wählen Sie dann den Status in der Dropdownliste aus.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Unterschiedliche Status werden auf [dieser Seite](#delivery-statuses) beschrieben.

>[!NOTE]
>
>Über den **[!UICONTROL Display the mirror page for this message...]** Link können Sie die Spiegelseite für den Inhalt der Auslieferung anzeigen, die in der Liste in einem neuen Fenster ausgewählt wurde. Die Spiegelseite steht nur für Auslieferungen zur Verfügung, für die HTML-Inhalte definiert wurden. Weitere Informationen finden Sie unter [Generieren der Spiegelseite](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### Trackinglogs {#tracking-logs}

The **[!UICONTROL Tracking]** tab lists the tracking history for this delivery. Auf dieser Registerkarte werden Verfolgungsdaten für die gesendeten Nachrichten angezeigt, d. h. alle URLs, die von Adobe Campaign verfolgt werden. Die Verfolgungsdaten werden stündlich aktualisiert.

>[!NOTE]
>
>Sollte das Tracking für einen Versand nicht aktiviert worden sein, wird dieser Tab nicht angezeigt.

Die Verfolgungskonfiguration wird im entsprechenden Stadium des Auslieferungsassistenten ausgeführt. See [How to configure tracked links](../../delivery/using/how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** Daten werden in den Bereitstellungsberichten interpretiert. Siehe [diesen Abschnitt](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Versandverfolgung {#delivery-audit-}

Die **[!UICONTROL Audit]** Registerkarte enthält das Lieferprotokoll und alle Meldungen zu den Proofs. Über die **[!UICONTROL Refresh]** Schaltfläche können Sie die Daten aktualisieren. Verwenden Sie die **[!UICONTROL Filters]** Schaltfläche, um einen Filter für die Daten zu definieren.

Mit Sondersymbolen können Sie Fehler oder Warnungen identifizieren. Siehe [Analysieren der Bereitstellung](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

The **[!UICONTROL Proofs]** sub-tab lets you view the list of proofs that have been sent.

![](assets/s_ncs_user_delivery_log_tab.png)

Sie können die in diesem Fenster angezeigten Informationen (und die Informationen der Registerkarten **[!UICONTROL Delivery]** und **[!UICONTROL Tracking]** Registerkarten) ändern, indem Sie die anzuzeigenden Spalten auswählen. Klicken Sie dazu auf das **[!UICONTROL Configure list]** Symbol unten rechts. Weitere Informationen zum Konfigurieren der Listenanzeige finden Sie in [diesem Abschnitt](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Synchronisation des Versand-Dashboards {#delivery-dashboard-synchronization}

Im Versand-Dashboard können Sie anhand der verarbeiteten Nachrichten und der Versandlogs überprüfen, ob Ihr Versand erfolgreich durchgeführt wurde.

Manche Indikatoren oder Status können falsch oder nicht aktuell sein. Gehen Sie zur Behebung dieses Problems wie folgt vor:

* Wenn Ihr Lieferstatus nicht korrekt ist, überprüfen Sie, ob alle erforderlichen Genehmigungen für diese Bereitstellung durchgeführt wurden oder ob die **[!UICONTROL operationMgt]** und die **[!UICONTROL deliveryMgt]** Workflows fehlerfrei ausgeführt werden. Dies kann auch auf die Bereitstellung mit einer Affinität zurückzuführen sein, die in der sendenden Instanz nicht konfiguriert wurde.
* Wenn Ihre Auslieferungsindikatoren immer noch bei null liegen und Sie eine Konfiguration mit mittlerer Auslieferung vornehmen, überprüfen Sie den **[!UICONTROL Mid-sourcing (delivery counters)]** technischen Arbeitsablauf. Starten Sie es, wenn sein Status nicht **[!UICONTROL Started]** ist. Sie können dann versuchen, die Indikatoren neu zu berechnen, indem Sie mit der rechten Maustaste auf die entsprechende Bereitstellung im Adobe Campaign-Explorer klicken und dann **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* If your delivery counter does not match your delivery, try to recompute the indicators by right-clicking the relevant delivery in the Adobe Campaign explorer and selecting **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** to resynchronize. For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* Wenn Ihr Bereitstellungszähler für Bereitstellungen mit mittlerer Quelle nicht aktuell ist, überprüfen Sie, ob der **[!UICONTROL Mid-Sourcing (Delivery counters)]** technische Arbeitsablauf ausgeführt wird. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../installation/using/mid-sourcing-deployment.md).

Sie können Ihre Sendungen auch mithilfe unterschiedlicher Berichte über das Versand-Dashboard nachverfolgen. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../reporting/using/delivery-reports.md).

## Leistungsprobleme {#performance-issues}

### Checkliste {#checklist-}

Bei mangelhafter Zustellbarkeit überprüfen Sie Folgendes:

* **Die Versandgröße**: Größere Sendungen benötigen zur Ausführung länger. MTA-Kindprozesse werden für Standard-Bündelgrößen konfiguriert. Diese sind für die meisten Instanzen ausreichend, müssen jedoch überprüft werden, wenn Sendungen immer zu langsam durchgeführt werden.
* **Die Zielgruppe des Versands**: Die Versandleistung kann durch Softbounce-Fehler beeinträchtigt werden, die entsprechend der Konfiguration der Neuversuche gehandhabt werden. Je größer die Anzahl der Fehler ist, desto mehr Neuversuche sind nötig.
* **Die Gesamtauslastung der Plattform**: Wenn mehrere große Sendungen durchgeführt werden, kann die gesamte Plattform davon beeinträchtigt sein. In diesem Zusammenhang sollten Sie auch die IP-Reputation und Probleme bei der Zustellbarkeit überprüfen. Weiterführende Informationen dazu finden Sie im Adobe Campaign-Handbuch zu [Best Practices für die Optimierung der Zustellbarkeit](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) und auf [dieser Seite](../../delivery/using/about-deliverability.md).

Auch die Wartung der Plattform und der Datenbank kann die Leistung beim Versand beeinträchtigen. Weiterführende Informationen dazu finden Sie auf [dieser Seite](../../production/using/database-performances.md).

### Langsame Sendungen {#slow-deliveries}

Nachdem Sie auf die **[!UICONTROL Send]** Schaltfläche geklickt haben, dauert Ihre Lieferung länger als sonst. Dies kann von verschiedenen Elementen verursacht werden:

* Manche Internet Service Provider haben Ihre IP-Adressen möglicherweise auf eine Schwarze Liste gesetzt. Prüfen Sie in diesem Fall Ihre Broadlogs und lesen Sie in [diesem Erste-Schritte-Handbuch](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html).
* Ihr Versand könnte für eine rasche Verarbeitung zu groß sein. Dies kann passieren, wenn eine umfassende JavaScript-Personalisierung vorliegt oder die Versandgröße mehr als 60 KB beträgt. Nähere Informationen zu den Inhaltsrichtlinien finden Sie im Adobe Campaign-Handbuch [Best Practices beim Versand](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html).
* Der Versand könnte im MTA (Message Transfer Agent) von Adobe Campaign gedrosselt worden sein. Dies kann folgende Ursachen haben:

   * Ausgegebene Nachrichten (**[!UICONTROL quotas met]** Meldung): die in den deklarativen MX-Regeln in Campaign angegebenen Quoten eingehalten wurden. For more information about this message, refer to [this page](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ). Weitere Informationen zu MX-Regeln finden Sie auf [dieser Seite](../../delivery/using/technical-recommendations.md#mx-rules).
   * Messages pended (**[!UICONTROL dynamic flow control]** message): Campaign MTA has encountered errors when trying to deliver messages for a given ISP which causes a slowdown to avoid too big of an error density and thus facing potential blacklisting.

* Durch einen Systemfehler wird möglicherweise verhindert, dass Server miteinander interagieren. Dadurch kann sich der gesamte Versandvorgang verlangsamen. Überprüfen Sie die Server, um sicherzustellen, dass keine Speicher- oder Ressourcenfehler vorliegen, die Campaign beispielsweise daran hindern können, Personalisierungsdaten abzurufen.

### Best Practices für die Leistung {#best-practices-performance}

* Bewahren Sie auf der Instanz keine fehlgeschlagenen Sendungen auf, da dadurch temporäre Tabellen gespeichert werden, was wiederum die Leistung beeinträchtigt.

* Entfernen Sie nicht mehr benötigte Lieferungen.

* Inaktive Empfänger in den letzten 12 Monaten werden aus der Datenbank entfernt, um die Adressenqualität zu erhalten.

* Planen Sie nicht die gleichzeitige Durchführung umfangreicher Sendungen. In einem Zeitraum von 5 bis 10 Minuten wird die Last gleichmäßig über das System verteilt. Koordinieren Sie die Planung der Auslieferungen mit den anderen Mitgliedern Ihres Teams, um die beste Leistung sicherzustellen. Wenn der Marketing-Server viele verschiedene Aufgaben gleichzeitig ausführt, kann die Leistung verlangsamt werden.

* Halten Sie die Größe Ihrer E-Mails so gering wie möglich. Die empfohlene maximale Größe einer E-Mail beträgt ca. 35 KB. Die Größe einer E-Mail-Zustellung generiert eine bestimmte Menge an Volumen auf den sendenden Servern.

* Große Auslieferungen wie Lieferungen an über eine Million Empfänger benötigen Platz in den Versandwarteschlangen. Dies allein ist kein Problem für den Server, aber in Kombination mit Dutzenden von anderen großen Auslieferungen, die alle gleichzeitig ausgehen, kann es zu einer Versandverzögerung führen.

* Durch Personalisierung in E-Mails werden Daten für jeden Empfänger aus der Datenbank abgerufen. Bei vielen Personalisierungselementen erhöht sich dadurch die Datenmenge, die zur Vorbereitung der Bereitstellung benötigt wird.

* Indexieren von Adressen. Um die Performance der in der Anwendung verwendeten SQL-Abfragen zu optimieren, kann ein Index vom Hauptelement des Datenschemas deklariert werden.

>[!NOTE]
>
>ISPs würden Adressen nach einer Inaktivität deaktivieren. An Absender werden abgespeckte Nachrichten gesendet, um sie über diesen neuen Status zu informieren.

## Versandstatus {#delivery-statuses}

Beim Versand können folgende Status auf dem Versand-Dashboard angezeigt werden:

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definitionen und Lösungen<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nicht anwendbar<br /> </td> 
   <td> Der Versandserver (MTA) hat den Versand zwar berücksichtigt, aber nicht verarbeitet.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignoriert<br /> </td> 
   <td> Die Nachricht wurde wegen eines Adressfehlers nicht an den Empfänger gesendet. Die Adresse stand entweder auf der Blacklist, war in Quarantäne, nicht verfügbar oder ein Duplikat. <br /> </td> 
  </tr> 
  <tr> 
   <td> Gesendet<br /> </td> 
   <td> Gesendet: Der Versand wurde korrekt an den E-Mail-Provider durchgeführt (aber der Empfänger hat sie nicht unbedingt erhalten).<br /> </td> 
  </tr> 
  <tr> 
   <td> Fehlgeschlagen<br /> </td> 
   <td> Der Versand hat den Empfänger nicht erreicht, weil die Adresse ungültig oder der Posteingang voll war. Die Ursache kann auch ein Problem mit Gestaltungsbausteinen sein, da diese Fehler hervorrufen können, wenn die Schemata nicht mit dem Versand-Mapping übereinstimmen. Siehe Status <a href="#failed-status" target="_blank">"Fehlgeschlagen"</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Vom Dienstleister berücksichtigt<br /> </td> 
   <td> Der SMS-Dienstleister hat den Versand erhalten.<br /> </td> 
  </tr> 
  <tr> 
   <td> Auf Mobiltelefon erhalten<br /> </td> 
   <td> Der Empfänger hat die SMS auf seinem Mobilgerät erhalten.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ausstehend<br /> </td> 
   <td> Die Nachrichten sind versandbereit und werden vom Versand-Server (MTA) verarbeitet. Siehe <a href="#pending-status" target="_blank">Ausstehender Status</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Versand abgebrochen<br /> </td> 
   <td> Ein Benutzer hat den Vorgang abgebrochen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Vorbereitet<br /> </td> 
   <td> Hierbei handelt es sich um einen Zwischenstatus, der ausschließlich für externe Connectoren (z. B. Mobile-Kanal) verwendet wird. Er folgt auf den 'Ausstehend'-Status, wobei der Folgestatus vom externen Connector bestimmt wird.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dem Dienstleister übermittelt<br /> </td> 
   <td> Der Versand wurde dem SMS-Dienstleister übermittelt, aber noch nicht von ihm empfangen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Weiterführende Informationen zur Optimierung der Zustellbarkeit von mit Adobe Campaign gesendeten E-Mails finden Sie im Adobe Campaign-Handbuch zu [Best Practices für die Optimierung der Zustellbarkeit](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) und auf [dieser Seite](../../delivery/using/about-deliverability.md).

### Status Ausstehend {#pending-status}

After confirming your delivery, you can see that the status of your delivery is **[!UICONTROL Pending]**. This status means that the execution process is waiting on the availability of some resources.

Der **[!UICONTROL Pending]** Status kann zunächst bedeuten, dass Ihre Auslieferung geplant wurde und bis zum angegebenen Datum aussteht. For more on this, refer to the [Delivery scheduling](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) section.

If your delivery is not being sent and its status remains **[!UICONTROL Pending]**, it can be the result of:

* Der MTA (Message Transfer Agent), der für die Durchführung von Modulen und Prozessen am Versandserver und die Verwaltung des E-Mail-Versands verantwortlich ist, wurde möglicherweise noch nicht gestartet oder muss neu gestartet werden. Um dies zu überprüfen und bei Bedarf das Modul zu starten, gehen Sie wie folgt vor:

   * Check that your `mta@<instance>` modules are launched on your MTA servers.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * Wenn der MTA nicht aufgelistet ist, starten Sie ihn mit folgendem Befehl:

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersetzen Sie `<INSTANCENAME>` dies durch den Namen Ihrer Instanz (Produktion, Entwicklung usw.). Der Instanzname wird über die Konfigurationsdateien identifiziert: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* Die Bereitstellung kann eine Affinität verwenden, die auf dem sendenden Server nicht konfiguriert ist. Überprüfen Sie in diesem Fall die Konfiguration des Traffic-Managements (IP-Affinität) und verwenden Sie das **[!UICONTROL Managing affinities with IP addresses]** Feld, um die Bereitstellung mit dem MTA zu verknüpfen, das die Affinität verwaltet. For more information on affinities, refer to [this section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* Wenn die Bereitstellungsvorbereitung aussteht, können zu viele Kampagnen ausgeführt werden, die die Statusaktualisierung der Bereitstellung blockieren. Um dies zu lösen, gehen Sie zu **[!UICONTROL Options]** und erhöhen Sie den Wert von **[!UICONTROL NmsOperation_LimitConcurrency]** (Standard ist 10). Führen Sie nicht mehr Kampagnen aus als der Wert, der dieser spezifischen Option zugewiesen ist.

### Status Fehlgeschlagen {#failed-status}

Wenn der Status einer E-Mail-Zustellung **[!UICONTROL Failed]** lautet, kann sie mit einem Problem mit Personalisierungsblöcken verknüpft werden. Personalisierungsblöcke in einer Bereitstellung können Fehler hervorrufen, wenn die Schemata beispielsweise nicht mit der Zuordnungszuordnung übereinstimmen.

Versandlogs liefern wichtige Informationen über den Grund von fehlgeschlagenen Sendungen, wie z. B.:

* Wenn Empfängermeldungen mit einem Fehler &quot;Nicht erreichbar&quot;fehlschlagen, der Folgendes angibt: **Fehler beim Kompilieren des Skripts &quot;content htmlContent&quot;Zeile X: nicht definiert`[table]`ist. JavaScript: Fehler bei der Auswertung von Skript &#39;content htmlContent**, die Ursache dieses Problems ist fast immer eine Personalisierung im HTML-Versuch, auf eine Tabelle oder ein Feld aufzurufen, die nicht im Upstream Targeting oder in der Targeting-Zuordnung der Bereitstellung definiert oder zugeordnet wurde.

   Um dieses Problem zu beheben, müssen der Workflow und der Versandinhalt überprüft werden, um festzustellen, welcher Personalisierungsinhalt konkret die Tabelle aufrufen möchte und ob die Tabelle zugeordnet werden kann. Danach muss entweder der Aufruf dieser Tabelle in der HTML-Datei entfernt oder das Mapping mit dem Versand korrigiert werden.

* Beim Mid-Sourcing-Bereitstellungsmodell können Versandlogs folgende Mitteilung aufweisen: **Error during the call of method &#39;AppendDeliveryPart&#39; on the mid sourcing server: &#39;Communication error with the server: please check this one is correctly configured. Code HTTP 408 &#39;Service temporarily unavailable&#39;**.

   Die Ursache hierfür sind Leistungsprobleme. Dieser Fehler tritt auf, wenn die Marketing-Instanz zu lange für die Datenerfassung benötigt, bevor diese an den Mid-Sourcing-Server gesendet werden.

   Um dieses Problem zu beheben, wird empfohlen, einen Vacuum-Befehl und eine Neuindizierung der Datenbank durchzuführen. Weiterführende Informationen zur Wartung der Datenbank finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

   Zusätzlich sollten Sie alle Workflows mit einer terminierten Aktivität und alle Workflows mit fehlgeschlagenem Status neu starten. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

* Wenn ein Versand fehlschlägt, erscheint folgende Fehlermeldung in den Versandlogs: **DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.**

   Normalerweise bedeutet dieser Fehler, dass es in der E-Mail ein Personalisierungsfeld oder einen Gestaltungsbaustein gibt, der für einen Empfänger mehr als einen Datensatz abruft.

   Um dies zu lösen, überprüfen Sie die verwendeten Personalisierungsdaten und überprüfen Sie dann das Ziel auf Empfänger, die mehr als einen Eintrag für eines dieser Felder haben. Sie können auch eine **[!UICONTROL Deduplication]** Aktivität im Targeting-Arbeitsablauf vor der Bereitstellungsaktivität verwenden, um zu überprüfen, ob immer nur ein Personalisierungsfeld vorhanden ist. For more information on deduplication, refer to [this page](../../workflow/using/deduplication.md).

* Wenn ein Versand fehlschlägt und der Fehler &quot;Unerreichbar&quot; mit der Mitteilung &quot;Empfang einer Bounce Message (Regel &#39;Auto_replies&#39; wurde auf diesen Bounce angewandt)&quot; angezeigt wird, bedeutet dies, dass der Versand erfolgreich war, aber Adobe Campaign eine automatische Antwort vom Empfänger erhalten hat (z. B. eine Abwesenheitsantwort), die den E-Mail-Empfangsregeln &#39;Auto_replies&#39; entsprochen hat. Die automatische Antwort wird von Adobe Campaign ignoriert, und die Empfängeradresse kommt nicht in Quarantäne.

**Verwandte Themen:**

* [Protokolle und Versandverlauf](#delivery-logs-and-history)
* [Ursachen von fehlgeschlagenen Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Typen und Ursachen für fehlgeschlagene Sendungen](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Anzahl gesendeter Nachrichten {#number-of-messages-sent}

You can access deliveries from the delivery list, via the **[!UICONTROL Campaign Management > Deliveries]** node of the tree.

Standardmäßig zeigt die Versandliste die Titel und Status aller im ausgewählten Knoten erstellten Sendungen sowie die Anzahl der zu versendenden, der verarbeiteten und der erfolgreich zugestellten Nachrichten an.

* The number of **[!UICONTROL Messages to send]** corresponds to the number of recipients targeted after analysis and prior to delivery.
* The number of messages in the **[!UICONTROL success]** column corresponds to the number of messages sent by the server and received by the recipients.
* The number of **[!UICONTROL processed]** messages corresponds to the number of messages received plus the number of messages with errors.

Dieselben Informationen werden auch im Versand-Dashboard angezeigt.

>[!NOTE]
>
>Bei großen Auslieferungen sollten Sie diese Werte eventuell aktualisieren. Wählen Sie dazu die betreffende Lieferung aus und klicken Sie mit der rechten Maustaste darauf. Wählen Sie diese Informationen aus **[!UICONTROL Action > Recompute delivery and tracking indicators...]** und verwenden Sie dann den Assistenten.

## Terminierte Sendungen {#scheduled-deliveries-}

Wenn Sendungen nicht zum terminierten Zeitpunkt durchgeführt werden, kann die Ursache daran liegen, dass die Server für die Mid-Sourcing-Instanz und die Produktionsinstanz in unterschiedlichen Zeitzonen liegen.

Wenn beispielsweise die Mid-Sourcing-Instanz in der Zeitzone von Brisbane liegt und die Produktionsinstanz in der Zeitzone von Darwin, liegen die beiden Zeitzonen eine halbe Stunde voneinander entfernt. Im Log würden Sie dann sehen, dass ein Versand, dessen Produktion um 11:56 Uhr festgelegt ist, am Mid-Sourcing-Server um 12:26 Uhr terminiert wäre, was einen Unterschied von einer halben Stunde ergibt.
