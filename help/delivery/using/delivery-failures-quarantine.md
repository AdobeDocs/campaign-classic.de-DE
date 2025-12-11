---
product: campaign
title: Versandfehler und Quarantäneverwaltung
description: Erfahren Sie, wie Sie in Campaign Classic v7 Versandfehler verstehen und Quarantänen verwalten können.
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: ht
source-wordcount: '1635'
ht-degree: 100%

---

# Versandfehler und Quarantäneverwaltung {#delivery-failures-quarantine}

>[!NOTE]
>
>Eine umfassende Anleitung zu fehlgeschlagenen Sendungen und zur Quarantäneverwaltung finden Sie in der Dokumentation zu Campaign v8. Dieser Inhalt gilt für Benutzende von Campaign Classic v7 und Campaign v8:
>
>* [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}: Behandelt Fehlertypen, Fehlerursachen, synchrone/asynchrone Fehler, Verwaltung von Neuversuchen und Fehlerbehebung
>* [Quarantäneverwaltung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}: Behandelt die Unterschiede zwischen Quarantäne und Blockierungsliste, Softbounce-Fehlerschwellen, Quarantäneberichte und Adressenentfernung
>
>Auf dieser Seite wird die **Campaign Classic v7-spezifische Konfiguration** für die Bounce-E-Mail- und Quarantäneverwaltung in Hybrid- und On-Premise-Bereitstellungen dokumentiert.

## Ursachen von fehlgeschlagenen Sendungen

Informationen zu häufigen Konzepten bei fehlgeschlagenen Sendungen, Fehlertypen und Anleitungen zur Fehlerbehebung finden Sie in der [Dokumentation zu Versandfehlern in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Bounce-E-Mail-Konfiguration {#bounce-mail-config}

Die folgenden Konfigurationsoptionen sind für **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** verfügbar, um die Bounce-E-Mail-Verarbeitung zu verwalten.

### Konfiguration des Bounce-Postfachs {#bounce-mailbox-configuration}

Die Konfiguration des Bounce-Postfachs für On-Premise-Installationen wird [in diesem Abschnitt](../../installation/using/deploying-an-instance.md#managing-bounced-emails) beschrieben.

Asynchrone Fehlermeldungen werden von der Adobe Campaign-Plattform über das Bounce-Postfach erfasst und vom inMail-Prozess qualifiziert, um die Liste der E-Mail-Verwaltungsregeln anzureichern.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services wird die Konfiguration der Bounce-Postfächer von Adobe durchgeführt und verwaltet. Keine Konfiguration ist erforderlich. 

### Verwalten der Bounce-E-Mail-Qualifizierung             {#bounce-mail-qualification-management}

Bei On-Premise-Installationen und gehosteten/hybriden Installationen, die den bestehenden Campaign-MTA verwenden, erhält der Adobe Campaign-Versand-Server eine Fehlermeldung vom Messaging-Server oder dem Remote-DNS-Server, wenn der Versand einer E-Mail fehlschlägt. Die Liste der Fehler besteht aus Zeichenfolgen, die in der vom Remote-Server zurückgegebenen Nachricht enthalten sind. Jeder Fehlermeldung sind Fehlertypen und Gründe zugeordnet.

Auf die entsprechende Liste kann im Knoten **[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Versandlogqualifizierung]** zugegriffen werden. Sie enthält alle von Adobe Campaign für die Qualifizierung von fehlgeschlagenen Sendungen verwendeten Regeln. Die Liste erhebt keinen Anspruch auf Vollständigkeit. Sie wird jedoch regelmäßig von Adobe Campaign angereichert und kann auch vom Benutzer ergänzt werden.

![](assets/tech_quarant_rules_qualif.png)

Die vom Remote-Server beim ersten Auftreten dieses Fehlertyps zurückgegebene Nachricht wird in der Spalte **[!UICONTROL Erster Text]** der Tabelle **[!UICONTROL Versandlogqualifizierung]** angezeigt. Wird diese Spalte nicht angezeigt, wählen Sie in der Liste rechts unten die Schaltfläche **[!UICONTROL Liste konfigurieren]**, um die Spalte auszuwählen.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtert diese Nachricht, um den variablen Inhalt (wie IDs, Daten, E-Mail-Adressen, Telefonnummern usw.) zu löschen, und zeigt das gefilterte Ergebnis in der Spalte **[!UICONTROL Text]** an. Die Variablen werden durch **`#xxx#`** ersetzt, mit Ausnahme der Adressen, die durch ersetzt **`*`** werden.

Dadurch können alle Fehlschläge desselben Typs zusammengefasst werden und mehrfache Einträge für ähnliche Fehler in die Versandlogqualifizierungs-Tabelle werden vermieden.

>[!NOTE]
>
>Im Feld **[!UICONTROL Trefferanzahl]** wird die Anzahl der Vorkommnisse der Nachricht in der Liste angezeigt. Die maximale Anzahl ist 100 000. Sie können das Feld bearbeiten, wenn Sie es beispielsweise zurücksetzen möchten.

Folgende Qualifizierungsstatus von Bounce Messages treten auf:

* **[!UICONTROL Zu qualifizieren]**: Die Bounce-E-Mail konnte nicht automatisch qualifiziert werden und muss dem Zustellbarkeits-Team vorgelegt werden, um die korrekte Steuerung der Zustellbarkeit der Plattform zu gewährleisten. Nicht qualifizierte Bounce-E-Mails werden nicht zur Anreicherung der E-Mail-Regeln herangezogen.
* **[!UICONTROL Beibehalten]**: Die Bounce-E-Mail wurde qualifiziert und wird vom Workflow **Zustellbarkeit** verwendet, um mit den existierenden E-Mail-Regeln verglichen zu werden und eventuell die Liste zu ergänzen.
* **[!UICONTROL Ignorieren]**: Die Bounce-E-Mail wird vom Campaign MTA ignoriert, was bedeutet, dass diese Bounce-E-Mail nie dazu führt, dass die Adresse der Empfängerin bzw. des Empfängers unter Quarantäne gestellt wird. Sie wird vom Workflow **Zustellbarkeit** nicht verwendet und auch nicht an Client-Instanzen gesendet.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>Bei Ausfall eines ISP werden über Campaign gesendete E-Mails fälschlicherweise als Bounces gekennzeichnet. Um dies zu korrigieren, müssen Sie die Bounce-Qualifizierung aktualisieren. Weitere Informationen hierzu finden Sie auf [dieser Seite](update-bounce-qualification.md).

### Konfiguration von E-Mail-Verwaltungsregeln {#email-management-rules}

Auf E-Mail-Regeln kann im Knoten **[!UICONTROL Administration > Kampagnen > Unzustellbarkeitsverwaltung]** zugegriffen werden. Im unteren Teil des Fensters können Sie die Details der Regeln sehen.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Die Standardparameter der Plattform werden im Bereitstellungsassistenten konfiguriert. Weiterführende Informationen erhalten Sie in [diesem Abschnitt](../../installation/using/deploying-an-instance.md).

Folgende Regeln sind in der Standardkonfiguration vorgesehen:

>[!IMPORTANT]
>
>* Nach Änderungen der Parameter muss der Versand-Server (MTA) neu gestartet werden.
>* Neuerstellung und Änderungen von Verwaltungsregeln sollten erfahrenen Benutzenden vorbehalten bleiben.

#### Eingehende E-Mails {#inbound-email}

In diesen Regeln sind die Strings enthalten, die von Remote-Servern zurückgegeben werden können und die die Qualifizierung der Fehler erlauben **Hard**, **Soft** oder **Ignoriert**.

Wenn die Zustellung einer E-Mail fehlschlägt, gibt der Remote-Server eine Bounce-Nachricht an die in der Plattformkonfiguration angegebene Adresse zurück. Adobe Campaign vergleicht den Inhalt jeder Bounce-E-Mail mit den in der Regelliste verzeichneten Strings und ordnet ihnen einen der drei Fehlertypen zu.

>[!NOTE]
>
>Der Benutzer kann eigene Regeln erstellen. Beim Import eines Pakets und bei der Aktualisierung von Daten durch den Workflow **Zustellbarkeit** werden benutzerdefinierte E-Mail-Regeln überschrieben.

Weiterführende Informationen zur Bounce-E-Mail-Qualifizierung finden Sie [in diesem Abschnitt](#bounce-mail-qualification-management).

#### Domain-Verwaltung {#domain-management}

Bei On-Premise-Installationen wendet der MTA eine einzige **Domain-Verwaltungsregel** auf alle Domains an.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Sie haben die Möglichkeit, gewisse Authentifizierungsnormen und Verschlüsselungsschlüssel zu aktivieren, um den Domain-Namen zu prüfen: **Sender ID**, **DomainKeys**, **DKIM**, **S/MIME**.
* Mit den **SMTP-Relais**-Parametern können Sie die IP-Adresse und den Port eines Relais-Servers für eine bestimmte Domain konfigurieren. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#smtp-relay).

Wenn Ihre Nachrichten mit **[!UICONTROL im Namen von]** in der Absenderadresse angezeigt werden, vergewissern Sie sich, dass Sie Ihre E-Mails nicht mit der **Sender ID** signieren, dem veralteten proprietären Authentifizierungsstandard für E-Mails von Microsoft. Wenn die Option **[!UICONTROL Sender ID]** aktiviert ist, deaktivieren Sie das entsprechende Feld und wenden Sie sich an die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Ihre Zustellbarkeit wird nicht beeinträchtigt.

#### MX-Verwaltung {#mx-management}

Bei On-Premise-Installationen ermöglichen MX-Verwaltungsregeln die Regulierung des Flusses ausgehender E-Mails für eine bestimmte Domain.

<!--![](assets/tech_quarant_domain_rules_01.png)-->

Diese Regeln stehen im Bereitstellungsassistenten zur Verfügung und können angepasst werden:

* **[!UICONTROL MX-Verwaltung]**: Diese Regel wird verwendet, um den Fluss ausgehender E-Mails für eine Domain zu steuern. Sie analysiert die Bounce-E-Mails und blockiert bei Bedarf den Versand. 

* **[!UICONTROL Zeitraum]**: Der Zeitrahmen, in dem Nachrichten gedrosselt oder blockiert werden.

* **[!UICONTROL Limit]**: Die maximal zulässige Anzahl von Nachrichten pro Zeitraum.

* **[!UICONTROL Typ]**: Der Fehlertyp (Hard, Soft oder Ignoriert), der zum Bestimmen des Versandverhaltens verwendet wird. Definitionen zu Fehlertypen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

Weiterführende Informationen zur MX-Verwaltung erhalten Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#about-mx-rules).

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden MX-Regeln und die E-Mail-Flussverwaltung von Adobe als Teil der verwalteten Infrastruktur verwaltet. Wenden Sie sich an die Adobe-Kundenunterstützung, wenn Sie MX-Einstellungen für bestimmte Anwendungsfälle anpassen müssen.

## Quarantäneverwaltung {#quarantine-management}

Eine umfassende Anleitung zur Quarantäneverwaltung finden Sie in der [Dokumentation zur Quarantäneverwaltung in Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Quarantänekonfiguration {#quarantine-config}

Die folgenden Konfigurationsoptionen sind für **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7** verfügbar, um das Quarantäneverhalten anzupassen.

### Konfiguration der Softbounce-Fehlerschwellen {#soft-error-threshold}

Bei On-Premise-Installationen mit dem alten Campaign-MTA können Sie die Anzahl der Fehler und den Zeitraum zwischen zwei Fehlern ändern, bevor eine Adresse unter Quarantäne gestellt wird.

So konfigurieren Sie diese Einstellungen:

1. Öffnen Sie den Bereitstellungsassistenten über **[!UICONTROL Werkzeuge]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Bereitstellungsassistent]**
2. Navigieren Sie zu **[!UICONTROL E-Mail-Kanal]** > **[!UICONTROL Erweiterte Parameter]**
3. Konfigurieren:
   * **Fehleranzahl**: Die maximale Anzahl von Softbounce-Fehlern, bevor eine Adresse unter Quarantäne gestellt wird (Standard: 5)
   * **Zeitraum zwischen zwei signifikanten Fehlern**: Das Zeitfenster (in Sekunden) für die Fehlerzählung (Standard: 86.400 Sekunden = 1 Tag)

Wenn der Zähler die Schwelle erreicht, wird die Adresse unter Quarantäne gestellt. Wenn der letzte schwerwiegende Fehler vor mehr als 10 Tagen aufgetreten ist, wird der Fehlerzähler neu initialisiert.

Weitere Informationen finden Sie [auf dieser Seite](communication-channels.md) unter **Versand** > **Konfigurieren weiterer Zustellversuche**.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden Einstellungen für weitere Zustellversuche und Fehlerschwellenwerte von Adobe basierend auf der IP-Leistung und der Domain-Reputation verwaltet. Keine Konfiguration ist erforderlich. 

### Datenbankbereinigungs-Workflow {#database-cleanup-workflow}

Bei On-Premise-Installationen entfernt der technische Workflow **[!UICONTROL Datenbankbereinigung]** automatisch die Quarantäneadressen, die bestimmte Voraussetzungen erfüllen.

Greifen Sie auf diesen Workflow über **[!UICONTROL Administration]** > **[!UICONTROL Produktion]** > **[!UICONTROL Technische Workflows]** > **[!UICONTROL Datenbankbereinigung]** zu.

Der Workflow entfernt Adressen in den folgenden Fällen aus der Quarantäne:

* Adressen mit Status **[!UICONTROL Mit Fehlern]** nach einem erfolgreichen Versand
* Adressen mit Status **[!UICONTROL Mit Fehlern]**, wenn der letzte Softbounce mehr als 10 Tage zurückliegt
* Adressen mit Status **[!UICONTROL Mit Fehlern]** und dem Fehler **[!UICONTROL Postfach voll]** nach 30 Tagen

Stellen Sie sicher, dass dieser Workflow regelmäßig ausgeführt wird (empfohlen: täglich), um die Hygiene der Quarantäneliste aufrechtzuerhalten.

Weitere Informationen zur Datenbankbereinigung finden Sie [in diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Bei Benutzenden von Campaign v8 Managed Cloud Services wird der Datenbankbereinigungs-Workflow von Adobe überwacht und verwaltet.

### Besonderheiten der Quarantäne bei Push-Benachrichtigungen {#push-quarantine-specifics}

Bei Campaign Classic v7 erfolgt die Quarantäne für Push-Benachrichtigungen entsprechend dem allgemeinen Quarantänemechanismus, allerdings mit einigen kanalspezifischen Verhaltensweisen.

Für **iOS**- und **Android**-Push-Benachrichtigungen verwendet der Quarantänemechanismus Geräte-Token anstelle von E-Mail-Adressen. Wenn eine App deinstalliert oder neu installiert wird, wird das zugehörige Token unter Quarantäne gestellt.

Detaillierte Informationen zu Quarantäneszenarien für Push-Benachrichtigungen (Fehlertypen in iOS und Android, Verhalten bei erneuten Zustellversuchen usw.) finden Sie in der Dokumentation [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}, die umfassende Fehlertyptabellen für Push-Benachrichtigungen.

### Besonderheiten der SMS-Quarantäne {#sms-quarantine-specifics}

Bei Campaign Classic v7 erfolgt die Quarantäne von SMS entsprechend dem allgemeinen Quarantänemechanismus, allerdings mit einigen kanalspezifischen Verhaltensweisen bezüglich Telefonnummern statt E-Mail-Adressen.

Der SMS-Quarantänemechanismus hängt vom verwendeten Connector ab:

* **Standard-SMPP-Connectoren**: Die in **[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Versandlogqualifizierung]** definierten Regeln für die Fehlerqualifizierung gelten für SMS-Sendungen.

* **Erweiterter allgemeiner SMPP-Connector**: Das Fehler-Management wird mithilfe regulärer Ausdrücke (Regex) anders gehandhabt, um Statusbericht-Nachrichten (SR) zu analysieren, die vom SMSC-Provider zurückgegeben werden.

Ausführliche Informationen zu SMS-Quarantäneszenarien und Fehlertypen finden Sie in der Dokumentation unter [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} mit umfassenden Tabellen zu SMS-Fehlertypen.

## Verwandte Themen

* [Informationen zu Versandfehlern](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Dokumentation zu Campaign v8)
* [Quarantäneverwaltung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Dokumentation zu Campaign v8)
* [Best Practices für den Versand](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8)
* [Versandstatus](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (Dokumentation zu Campaign v8)
* [Datenbankbereinigungs-Workflow](../../production/using/database-cleanup-workflow.md) (v7 Hybrid/On-Premise)
* [Konfigurieren von weiteren Versandversuchen](communication-channels.md) (v7 Hybrid/On-Premise)
* [Aktualisieren der Bounce-Qualifizierung](update-bounce-qualification.md) (v7 Hybrid/On-Premise)
* [Konfiguration der E-Mail-Zustellbarkeit](../../installation/using/email-deliverability.md) (v7 Hybrid/On-Premise)
* [Bereitstellen einer Instanz](../../installation/using/deploying-an-instance.md#managing-bounced-emails) (v7 Hybrid/On-Premise)

