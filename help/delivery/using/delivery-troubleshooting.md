---
product: campaign
title: Fehlerbehebung beim Versand
description: Erfahren Sie mehr über die Versand-Performance und wie Sie Probleme beim Versand-Monitoring beheben können
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 87%

---

# Fehlerbehebung beim Versand {#delivery-troubleshooting}

In diesem Abschnitt werden häufig auftretende Probleme beim Versand sowie deren Fehlerbehebung aufgeführt.

Befolgen Sie außerdem die auf [dieser Seite beschriebenen](delivery-performances.md) Best Practices und die Checkliste, um sicherzustellen, dass Ihre Sendungen gut funktionieren.

**Verwandte Themen:**

* [Versandstatus](delivery-statuses.md)
* [Versand-Dashboard](delivery-dashboard.md)
* [Ursachen von fehlgeschlagenen Sendungen](understanding-delivery-failures.md)

## Langsame Sendungen {#slow-deliveries}

Nach dem Klicken auf die Schaltfläche **[!UICONTROL Senden]** dauert der Versand länger als üblich. Dies kann unterschiedliche Ursachen haben:

* Einige E-Mail-Anbieter haben Ihre IP-Adressen möglicherweise auf eine Blockierungsliste gesetzt. In diesem Fall überprüfen Sie Ihre Broadlogs und konsultieren Sie [diesen Abschnitt](about-deliverability.md).

* Ihr Versand könnte für eine rasche Verarbeitung zu groß sein. Dies kann passieren, wenn eine umfassende JavaScript-Personalisierung vorliegt oder die Versandgröße mehr als 60 KB beträgt. Siehe Adobe Campaign v8 [Best Practices beim Versand](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/delivery-best-practices){target="_blank"}.  Informationen zu Inhaltsrichtlinien.

* Der Versand könnte im MTA (Message Transfer Agent) von Adobe Campaign gedrosselt worden sein. Dies kann folgende Ursachen haben:

   * Nachricht in die Warteschlange gestellt (Meldung **[!UICONTROL Kontingente ausgeschöpft]**): Kontingente, die durch die in Campaign festgelegten deklarativen MX-Regeln angegebenen wurden, wurden ausgeschöpft. Weitere Informationen zu dieser Meldung finden Sie auf [dieser Seite](deliverability-faq.md). Weitere Informationen zu MX-Regeln finden Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#about-mx-rules).

   * Nachricht in die Warteschlange gestellt (Fehlermeldung **[!UICONTROL dynamische Durchsatzkontrolle]**): Vom Campaign MTA wurden beim Sendeversuch an einen ISP Fehler entdeckt, weshalb der Versand verlangsamt wurde, um die Fehlerdichte zu verringern und zu vermeiden, dass die IP-Adresse auf eine Blockierungsliste gesetzt wird.

* Durch einen Systemfehler wird möglicherweise verhindert, dass Server miteinander interagieren. Dadurch kann sich der gesamte Versandvorgang verlangsamen. Überprüfen Sie die Server, um sicherzustellen, dass keine Speicher- oder Ressourcenfehler vorliegen, die Campaign beispielsweise daran hindern können, Personalisierungsdaten abzurufen.

## Terminierte Sendungen {#scheduled-deliveries-}

Wenn Sendungen nicht zum terminierten Zeitpunkt durchgeführt werden, kann die Ursache daran liegen, dass die Server für die Mid-Sourcing-Instanz und die Produktionsinstanz in unterschiedlichen Zeitzonen liegen.

Wenn sich beispielsweise die Mid-Sourcing-Instanz in der Zeitzone von Brisbane und die Produktionsinstanz in der Zeitzone von Darwin befindet, sind beide Zeitzonen eine halbe Stunde voneinander entfernt. Dann ist im Administratorprotokoll klar ersichtlich, dass, wenn der Versand für die Produktion um 11::56 geplant ist, derselbe für die Mid-Sourcing-Instanz geplante Versand bei 12::26 liegen würde, was einen Unterschied von einer halben Stunde aufweist.

## Status &quot;Fehlgeschlagen&quot; {#failed-status}

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

  Die Ursache hierfür sind Performance-Probleme. Dieser Fehler tritt auf, wenn die Marketing-Instanz zu lange für die Datenerfassung benötigt, bevor diese an den Mid-Sourcing-Server gesendet werden.

  Um dieses Problem zu beheben, wird empfohlen, einen Vacuum-Befehl und eine Neuindizierung der Datenbank durchzuführen. Weiterführende Informationen zur Wartung der Datenbank finden Sie in [diesem Abschnitt](../../production/using/recommendations.md).

  Zusätzlich sollten Sie alle Workflows mit einer terminierten Aktivität und alle Workflows mit fehlgeschlagenem Status neu starten. Weitere Informationen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/flow-control-activities/scheduler.html?lang=de){target="_blank"}.

* Wenn ein Versand fehlschlägt, kann der folgende Fehler in den Versandlogs angezeigt werden:

  ```
  DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
  ```

  Normalerweise bedeutet dieser Fehler, dass es in der E-Mail ein Personalisierungsfeld oder einen Gestaltungsbaustein gibt, der für einen Empfänger mehr als einen Datensatz abruft.

  Um dieses Problem zu beheben, überprüfen Sie die verwendeten Personalisierungsdaten und danach den Zieldatensatz für die Empfänger, für deren Feld mehr als ein Eintrag vorhanden ist. Sie können vor der Versandaktivität auch die Aktivität **[!UICONTROL Deduplizierung]** im Zielgruppen-Workflow auswählen, damit immer nur ein einziges Personalisierungsfeld verwendet wird. Weitere Informationen zur Deduplizierung finden Sie in der [ zu Campaign v8 ](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/deduplication.html){target="_blank"}.

* Manche Sendungen können fehlschlagen und eine &quot;Unerreichbar&quot;-Fehlermeldung mit folgenden Informationen anzeigen:

  ```
  Inbound email bounce (rule 'Auto_replies' has matched this bounce).
  ```

  Das bedeutet, dass der Versand zwar erfolgreich war, Adobe Campaign aber eine automatische Antwort vom Empfänger erhalten hat (z. B. eine &quot;Abwesend&quot;-Antwort), die den Regeln für eingehende E-Mails &quot;Auto_replies&quot; entspricht.

  Die automatische Antwort-E-Mail wird von Adobe Campaign ignoriert und die Adresse des Empfängers wird nicht unter Quarantäne gestellt.
