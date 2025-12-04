---
product: campaign
title: Funktionsweise der Quarantäneverwaltung
description: Funktionsweise der Quarantäneverwaltung
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 2%

---

# Funktionsweise der Quarantäneverwaltung{#understanding-quarantine-management}

>[!NOTE]
>
>Eine umfassende Anleitung zur Quarantäneverwaltung finden Sie auf der Seite [Quarantäneverwaltung für Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines) . Diese Inhalte gelten für Benutzende von Campaign Classic v7 und Campaign v8 und umfassen:
>
>* Quarantänekonzepte im Vergleich zu Blockierungslisten
>* Gründe für die Quarantäne von Adressen (Hard-/Soft-Fehler)
>* Soft-Fehlermanagement und Schwellenwerte für Fehlerzähler
>* Zugreifen auf und Identifizieren von in Quarantäne befindlichen Adressen
>* Entfernen von Adressen aus der Quarantäne (automatisch, manuell, stapelweise)
>* Quarantäneverwaltungsberichte
>
>Auf dieser Seite wird die **Campaign Classic v7-spezifische Konfiguration** Quarantäneverwaltung in Hybrid- und On-Premise-Bereitstellungen dokumentiert.

Eine umfassende Anleitung zur Quarantäneverwaltung finden Sie in der [Dokumentation zur Quarantäneverwaltung in Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Quarantäne-Konfiguration {#v7-quarantine-config}

Die folgenden Konfigurationsoptionen sind für **Hybrid-/On-Premise-Bereitstellungen von Campaign Classic v7 verfügbar** um das Quarantäneverhalten anzupassen.

### Konfiguration der Fehlerschwellenwerte {#soft-error-threshold}

Bei On-Premise-Installationen mit dem alten Campaign MTA können Sie die Anzahl der Fehler und den Zeitraum zwischen zwei Fehlern ändern, bevor eine Adresse unter Quarantäne gestellt wird.

So konfigurieren Sie diese Einstellungen:

1. Greifen Sie über **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Bereitstellungsassistent auf den Bereitstellungsassistenten zu]**
2. Navigieren Sie zu **[!UICONTROL E-Mail]** > **[!UICONTROL Erweiterte Parameter]**
3. Konfigurieren:
   * **Fehleranzahl**: Die maximale Anzahl von Softbounces, bevor eine Adresse unter Quarantäne gestellt wird (Standard: 5)
   * **Zeitraum zwischen zwei signifikanten**: Das Zeitfenster (in Sekunden) für die Fehlerzählung (Standard: 86.400 Sekunden = 1 Tag)

Wenn der Fehlerzähler den Schwellenwert erreicht, wird die Adresse unter Quarantäne gestellt. Wenn der letzte schwerwiegende Fehler vor mehr als 10 Tagen aufgetreten ist, wird der Fehlerzähler neu initialisiert.

Weitere Informationen finden Sie auf [ Seite ](communication-channels.md) unter **Versand** > **Weitere Zustellversuche konfigurieren**.

>[!NOTE]
>
>Für Benutzende von Campaign v8 Managed Cloud Services werden Wiederholungseinstellungen und Fehlerschwellenwerte von Adobe basierend auf der IP-Leistung und der Domain-Reputation verwaltet. Es ist keine Konfiguration erforderlich.

### Datenbankbereinigungs-Workflow {#database-cleanup-workflow}

Bei On-Premise-Installationen entfernt der technische Workflow **[!UICONTROL Datenbankbereinigung]** automatisch die Quarantäneadressen, die bestimmten Bedingungen entsprechen.

Greifen Sie auf diesen Workflow über **[!UICONTROL Administration]** > **** > **[!UICONTROL Technische Workflows]** > **[!UICONTROL Datenbankbereinigung]** zu.

Der Workflow entfernt Adressen in den folgenden Fällen aus der Quarantäne:

* Adressen im Status **[!UICONTROL Mit Fehlern]** nach einem erfolgreichen Versand
* Adressen im Status **[!UICONTROL Mit Fehlern]** , wenn der letzte Softbounce mehr als 10 Tage zurückliegt
* Adressen im Status **[!UICONTROL Mit Fehlern]** mit dem Fehler **[!UICONTROL Postfach voll]** nach 30 Tagen

Stellen Sie sicher, dass dieser Workflow regelmäßig ausgeführt wird (empfohlen: täglich), um die Hygiene der Quarantäneliste aufrechtzuerhalten.

Weiterführende Informationen zur Datenbankbereinigung finden Sie in [diesem Abschnitt](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>Benutzende von Campaign v8 Managed Cloud Services überwachen und verwalten den Datenbankbereinigungs-Workflow von Adobe.

### Besonderheiten der Quarantäne bei Push-Benachrichtigungen {#push-quarantine-specifics}

Für Campaign Classic v7 folgen Quarantänen für Push-Benachrichtigungen dem allgemeinen Quarantänemechanismus mit einigen kanalspezifischen Verhaltensweisen.

Für **iOS**- und **Android**-Push-Benachrichtigungen verwendet der Quarantänemechanismus Geräte-Token anstelle von E-Mail-Adressen. Wenn eine Mobile App deinstalliert oder neu installiert wird, wird das zugehörige Token unter Quarantäne gestellt.

Detaillierte Informationen zu Quarantäneszenarien für Push-Benachrichtigungen (Fehlertypen in iOS und Android, Verhalten bei erneuten Zustellversuchen usw.) finden Sie in der [Übersicht zu Versandfehlern](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} die umfassende Fehlertyptabellen für Push-Benachrichtigungen enthält.

### Besonderheiten der SMS-Quarantäne {#sms-quarantine-specifics}

Für Campaign Classic v7 erfolgt die Quarantäne von SMS nach dem allgemeinen Quarantänemechanismus, wobei sich einige kanalspezifische Verhaltensweisen auf Telefonnummern statt auf E-Mail-Adressen beziehen.

Der SMS-Quarantänemechanismus hängt vom verwendeten Connector ab:

* **Standard-SMPP-Connectoren**: Die in **[!UICONTROL Administration > Kampagnen-Management > Unzustellbarkeitsverwaltung > Versandlogqualifizierung“ definierten Regeln für die Fehlerqualifizierung]** SMS-Sendungen.

* **Erweiterter allgemeiner SMPP-Connector**: Das Fehlermanagement wird mithilfe regulärer Ausdrücke (Regexe) anders gehandhabt, um Statusbericht(SR)-Nachrichten zu analysieren, die vom SMSC-Provider zurückgegeben werden.

Ausführliche Informationen zu SMS-Quarantäneszenarien und Fehlertypen finden Sie in der [Informationen zu Versandfehlern](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} , die umfassende Tabellen zu SMS-Fehlertypen enthält.

## Verwandte Themen

* [Quarantäneverwaltung](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Dokumentation zu Campaign v8)
* [Fehlgeschlagene Sendungen analysieren](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (Dokumentation zu Campaign v8)
* [Best Practices für den Versand](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (Dokumentation zu Campaign v8)
* [Datenbankbereinigungs-Workflow](../../production/using/database-cleanup-workflow.md) (v7 Hybrid/On-Premise)
* [Konfigurieren von weiteren Versandversuchen](communication-channels.md) (v7 Hybrid/On-Premise)
