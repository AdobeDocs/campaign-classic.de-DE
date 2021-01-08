---
solution: Campaign Classic
product: campaign
title: Fehlerbehebung
description: Erfahren Sie mehr über die Versandleistung und wie Sie Probleme beim Versand-Monitoring beheben können.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: ht
source-git-commit: f3ba836bbb5a5f82d6a7868dcb15edc8e61b9a5b
workflow-type: ht
source-wordcount: '797'
ht-degree: 100%

---


# Fehlerbehebung beim Versand {#delivery-troubleshooting}

In diesem Abschnitt werden häufig auftretende Probleme beim Versand sowie deren Fehlerbehebung aufgeführt.

Befolgen Sie außerdem die auf [dieser Seite beschriebenen](../../delivery/using/delivery-performances.md) Best Practices und die Checkliste, um sicherzustellen, dass Ihre Sendungen gut funktionieren.

**Verwandte Themen:**

* [Versandstatus](../../delivery/using/delivery-statuses.md)
* [Versand-Dashboard](../../delivery/using/delivery-dashboard.md)
* [Ursachen von fehlgeschlagenen Sendungen](../../delivery/using/understanding-delivery-failures.md)

## Langsame Sendungen {#slow-deliveries}

Nach dem Anklicken der **[!UICONTROL Senden]**-Schaltfläche dauert der Versand länger als üblich. Dies kann unterschiedliche Ursachen haben:

* Einige E-Mail-Anbieter haben Ihre IP-Adressen möglicherweise auf eine Blockierungsliste gesetzt. In diesem Fall überprüfen Sie Ihre Broadlogs und konsultieren Sie [diesen Abschnitt](../../delivery/using/about-deliverability.md).

* Ihr Versand könnte für eine rasche Verarbeitung zu groß sein. Dies kann passieren, wenn eine umfassende JavaScript-Personalisierung vorliegt oder die Versandgröße mehr als 60 KB beträgt. Nähere Informationen zu den Inhaltsrichtlinien finden Sie im Adobe Campaign-Handbuch [Best Practices beim Versand](../../delivery/using/delivery-best-practices.md).

* Der Versand könnte im MTA (Message Transfer Agent) von Adobe Campaign gedrosselt worden sein. Dies kann folgende Ursachen haben:

   * Nachricht in die Warteschlange gestellt (Fehlermeldung **[!UICONTROL Kontingent ausgeschöpft]**): Das in Campaign von den MX-Regeln definierte Kontingent ist ausgeschöpft. Weitere Informationen zu dieser Meldung finden Sie auf [dieser Seite](../../delivery/using/deliverability-faq.md). Weitere Informationen zu MX-Regeln finden Sie auf [dieser Seite](../../delivery/using/technical-recommendations.md#mx-rules).

   * Nachricht in die Warteschlange gestellt (Fehlermeldung **[!UICONTROL dynamische Durchsatzkontrolle]**): Vom Campaign MTA wurden beim Sendeversuch an einen ISP Fehler entdeckt, weshalb der Versand verlangsamt wurde, um die Fehlerdichte zu verringern und zu vermeiden, dass die IP-Adresse auf eine Blockierungsliste gesetzt wird.

* Durch einen Systemfehler wird möglicherweise verhindert, dass Server miteinander interagieren. Dadurch kann sich der gesamte Versandvorgang verlangsamen. Überprüfen Sie die Server, um sicherzustellen, dass keine Speicher- oder Ressourcenfehler vorliegen, die Campaign beispielsweise daran hindern können, Personalisierungsdaten abzurufen.

## Terminierte Sendungen {#scheduled-deliveries-}

Wenn Sendungen nicht zum terminierten Zeitpunkt durchgeführt werden, kann die Ursache daran liegen, dass die Server für die Mid-Sourcing-Instanz und die Produktionsinstanz in unterschiedlichen Zeitzonen liegen.

Wenn beispielsweise die Mid-Sourcing-Instanz in der Zeitzone von Brisbane liegt und die Produktionsinstanz in der Zeitzone von Darwin, liegen die beiden Zeitzonen eine halbe Stunde voneinander entfernt. Im Log würden Sie dann sehen, dass ein Versand, dessen Produktion um 11:56 Uhr festgelegt ist, am Mid-Sourcing-Server um 12:26 Uhr terminiert wäre, was einen Unterschied von einer halben Stunde ergibt.

## Status Fehlgeschlagen {#failed-status}

Wenn der Status eines E-Mail-Versands **[!UICONTROL Fehlgeschlagen]** lautet, kann die Ursache an Problemen mit Gestaltungsbausteinen liegen. Gestaltungsbausteine können bei einem Versand Fehler verursachen, wenn beispielsweise das Schema nicht mit dem Versand-Mapping übereinstimmt.

Versandlogs liefern wichtige Informationen über den Grund von fehlgeschlagenen Sendungen, wie z. B.:

* Bei Empfängernachrichten wird eine &quot;Unerreichbar&quot;-Fehlermeldung mit folgenden Informationen angezeigt:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   Die Ursache für dieses Problem ist fast immer eine Personalisierung innerhalb des HTML-Codes, die versucht, eine Tabelle oder ein Feld aufzurufen, die bzw. das bei der vorangegangenen Zielgruppenbestimmung oder beim Zielgruppen-Mapping des Versands nicht definiert oder zugeordnet wurde.

   Um dieses Problem zu beheben, müssen der Workflow und der Versandinhalt überprüft werden, um festzustellen, welcher Personalisierungsinhalt konkret die Tabelle aufrufen möchte und ob die Tabelle zugeordnet werden kann. Danach muss entweder der Aufruf dieser Tabelle in der HTML-Datei entfernt oder das Mapping mit dem Versand korrigiert werden.

* Beim Mid-Sourcing-Bereitstellungsmodell kann die folgende Meldung in den Versandlogs angezeigt werden:

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   Die Ursache hierfür sind Leistungsprobleme. Dieser Fehler tritt auf, wenn die Marketing-Instanz zu lange für die Datenerfassung benötigt, bevor diese an den Mid-Sourcing-Server gesendet werden.

   Um dieses Problem zu beheben, wird empfohlen, einen Vacuum-Befehl und eine Neuindizierung der Datenbank durchzuführen. Weiterführende Informationen zur Wartung der Datenbank finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

   Zusätzlich sollten Sie alle Workflows mit einer terminierten Aktivität und alle Workflows mit fehlgeschlagenem Status neu starten. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../workflow/using/scheduler.md).

* Wenn ein Versand fehlschlägt, kann der folgende Fehler in den Versandlogs angezeigt werden:

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   Normalerweise bedeutet dieser Fehler, dass es in der E-Mail ein Personalisierungsfeld oder einen Gestaltungsbaustein gibt, der für einen Empfänger mehr als einen Datensatz abruft.

   Um dieses Problem zu beheben, überprüfen Sie die verwendeten Personalisierungsdaten und danach den Zieldatensatz für die Empfänger, für deren Feld mehr als ein Eintrag vorhanden ist. Sie können vor der Versandaktivität auch die Aktivität **[!UICONTROL Deduplizierung]** im Zielgruppen-Workflow auswählen, damit immer nur ein einziges Personalisierungsfeld verwendet wird. Weitere Informationen zur Deduplizierung finden Sie auf [dieser Seite](../../workflow/using/deduplication.md).

* Manche Sendungen können fehlschlagen und eine &quot;Unerreichbar&quot;-Fehlermeldung mit folgenden Informationen anzeigen:

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   Das bedeutet, dass der Versand zwar erfolgreich war, Adobe Campaign aber eine automatische Antwort vom Empfänger erhalten hat (z. B. eine &quot;Abwesend&quot;-Antwort), die den Regeln für eingehende E-Mails &quot;Auto_replies&quot; entspricht.

   Die automatische Antwort-E-Mail wird von Adobe Campaign ignoriert und die Adresse des Empfängers wird nicht unter Quarantäne gestellt.
