---
title: Versand validieren
seo-title: Versand validieren
description: Versand validieren
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8c1f284be77447a88748ce97a3524b7035bb5bc0
workflow-type: tm+mt
source-wordcount: '1817'
ht-degree: 64%

---


# Versand validieren {#validating-the-delivery}

Der erstellte und konfigurierte Versand muss vor dem Senden an die Hauptzielgruppe validiert werden.

Gehen Sie dazu wie folgt vor:

1. **Versand analysieren** – hier erfolgt die Vorbereitung der zu sendenden Nachrichten. Siehe [Versand analysieren ](#analyzing-the-delivery).

   Die während der Analyse angewendeten Regeln werden im Abschnitt [Validierung mit Typologien](#validation-process-with-typologies) dargestellt. The available validation modes are detailed in the [Changing the approval mode](#changing-the-approval-mode) section.

1. **Testsendungen durchführen** – hier erfolgt die Validierung von Inhalt, URLs, Personalisierungsfeldern usw. Siehe [Testversand durchführen](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) und [Spezifische Testversand-Zielgruppe definieren](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>Beide Schritte sind erforderlich und müssen nach jeder Änderung des Nachrichteninhalts wiederholt werden.

## Versand analysieren {#analyzing-the-delivery}

Die Analyse ist die Phase, in der die Zielpopulation berechnet und der Versandinhalt vorbereitet wird. Sobald sie abgeschlossen ist, ist der Versand startbereit.

### Starten der Analyse {#launching-the-analysis}

1. Um die Versand-Analyse zu starten, klicken Sie auf **[!UICONTROL Senden]**.
1. Wählen Sie **[!UICONTROL schnellstmöglich]** Liefern.

   ![](assets/s_ncs_user_email_del_send.png)

1. Klicken Sie auf **[!UICONTROL Analysieren]** , um die Analyse manuell zu starten.

   Die Fortschrittsleiste zeigt den Fortschritt der Analyse an.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >Die während der Analyse verwendeten Validierungsregeln werden im Abschnitt [Validierung mit Typologien](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) beschrieben.

1. You can stop the analysis at any time by clicking **[!UICONTROL Stop]**.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   Während der Vorbereitungsphase werden keine Nachrichten gesendet. Sie können die Analyse daher ohne Risiko Beginn oder Stornierung vornehmen.

   >[!IMPORTANT]
   >
   >Beim Ausführen friert die Analyse den Versand (oder Testversand) ein. Jede Änderung des Versands (oder Testversands) muss von einer anderen Analyse gefolgt werden, bevor sie anwendbar wird.

1. Warten Sie, bis die Analyse abgeschlossen ist.

   Nach Abschluss der Analyse wird im oberen Bereich des Versands angezeigt, ob die Vorbereitung abgeschlossen ist oder ob Fehler aufgetreten sind. Alle Validierungsschritte, Warnungen und Fehler werden aufgelistet. Farbige Symbole zeigen den Nachrichtentyp an:
   * Das blaue Symbol zeigt eine informative Meldung an.
   * Das gelbe Symbol zeigt einen nicht kritischen Verarbeitungsfehler an.
   * Das rote Symbol zeigt einen kritischen Fehler an, der das Senden des Versands verhindert.

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. Klicken Sie auf **[!UICONTROL Schließen]** , um die Fehler zu berichtigen, falls vorhanden.

1. Nachdem Sie die Änderungen vorgenommen haben, starten Sie die Analyse neu und klicken Sie auf **[!UICONTROL Analysieren]**.

Nachdem Sie das Ergebnis der Analyse überprüft haben, können Sie auf &quot;Versand **[!UICONTROL bestätigen&quot;klicken, um die Nachricht an die angegebene Zielgruppe zu senden]** . Mit einer Bestätigungsmeldung können Sie den Versand starten.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Klicken Sie auf den Link **[!UICONTROL Hauptzielgruppe des Versands ändern]**, wenn die Anzahl der zu sendenden Nachrichten nicht Ihrer Konfiguration entspricht. Passen Sie die Zielpopulation entsprechend an und analysieren Sie erneut den Versand.

### Analyse {#analysis-parameters}

The **[!UICONTROL Analysis]** tab of the delivery properties lets you define a set of information concerning the preparation of messages during the analysis phase.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Folgende Optionen stehen zur Verfügung:

* **[!UICONTROL Bezeichnung und Code des Versands]** : Die Optionen in diesem Abschnitt werden zur Berechnung der Feldwerte während der Analyse des Versands verwendet. Der **[!UICONTROL Ausführungsordner während der Analyse]** des Versands wird mit dem Namen des Ordners berechnet, der während der Analyse diesen Versand enthält.
* **[!UICONTROL Genehmigungsmodus]** : In diesem Feld können Sie nach Abschluss der Analyse einen manuellen oder automatischen Versand definieren. Die Validierungsmodi werden im Abschnitt [Ändern des Genehmigungsmodus](#changing-the-approval-mode) angezeigt.
* **[!UICONTROL Bereiten Sie die Versand in der Datenbank]** vor: Mit dieser Option können Sie die Analyse der Versand verbessern. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#improving-delivery-analysis).
* **[!UICONTROL Bereiten Sie die Personalisierungsdaten mit einem Workflow]** vor: Mit dieser Option können Sie die Personalisierungsdaten Ihres Versands in einem automatischen Arbeitsablauf vorbereiten, wodurch Sie eine erhebliche Leistungssteigerung bei der Ausführung der Personalisierung erzielen können. For more on this, see [Optimizing personalization](../../delivery/using/personalization-fields.md#optimizing-personalization).
* **[!UICONTROL Auftrag eines Beginns in einem separate Prozess]** : Mit dieser Option können Sie die Versand-Analyse in einem separaten Prozess Beginn. Die Analyse-Funktion verwendet standardmäßig den Adobe Campaign Application Server-Prozess (Web-Nlserver). Durch Auswahl dieser Option stellen Sie sicher, dass die Analyse auch im Ereignis eines Anwendungsserverfehlers abgeschlossen wird.
* **[!UICONTROL Zielbestimmungs- und Personalisierungsabfragen im Protokoll speichern]** - schreibt in der Analysephase die SQL-Abfrage-Logs in das Versandprotokoll.
* **[!UICONTROL Personalisierungsscripts beim Versand ignorieren]** - im HTML-Inhalt enthaltene JavaScript-Anweisungen werden nicht interpretiert, sondern 1:1 in den gesendeten Inhalten abgebildet. Die Anweisungen beginnen mit dem Tag **&lt;%=**.

### Verbessern der Analyse von Versänden {#improving-delivery-analysis}

Um die Vorbereitung des Versands zu beschleunigen, können Sie vor dem Starten der Analyse die Option Versand **[!UICONTROL vorbereiten]** aktivieren.

Wenn diese Option aktiviert ist, erfolgt die Vorbereitung des Versands direkt in der Datenbank, wodurch die Analyse erheblich beschleunigt werden kann.

Diese Option steht derzeit nur zur Verfügung, wenn die folgenden Bedingungen erfüllt sind:
* Der Versand muss eine E-Mail sein. Die anderen Kanal werden derzeit nicht unterstützt.
* Sie dürfen kein Mid-Sourcing oder externes Routing, sondern nur Versand-Routing-Typ verwenden. Sie können das Routing überprüfen, das auf der Registerkarte &quot; **[!UICONTROL Allgemein]** &quot;der Eigenschaften des **[!UICONTROL Versands]** verwendet wird.
* Eine Population, die aus einer externen Datei stammt, kann nicht Zielgruppe werden. Klicken Sie für einen Versand in den **[!UICONTROL E-Mail-Parametern]** auf den Link &quot; **[!UICONTROL An]** &quot;und überprüfen Sie, ob die Option &quot; **[!UICONTROL Definiert in der Datenbank]** &quot;aktiviert ist. Überprüfen Sie bei einem Versand, der in einem Workflow verwendet wird, ob die Empfänger von den eingehenden Ereignissen **[!UICONTROL angegeben werden]** , die auf der Registerkarte &quot; **[!UICONTROL Versand]** &quot;aufgeführt sind.
* Sie müssen eine PostgreSQL-Datenbank verwenden.

### Analysepriorität konfigurieren {#analysis-priority-}

Wenn Ihr Versand Teil einer Kampagne ist, bietet der **[!UICONTROL Erweitert]**-Tab eine zusätzliche Option, die die Hierarchisierung der Sendungen innerhalb der Kampagne ermöglicht.

Jeder Versand wird analysiert, bevor die Nachrichten abgeschickt werden. Die Analysedauer hängt von der Größe der Extraktionsdatei des Versands ab. Je größer die Datei, desto länger die Analyse. Nachfolgende Sendungen werden verzögert.

Die Optionen im Bereich **[!UICONTROL Nachrichtenvorbereitung durch die Steuerung]** erlauben die Priorisierung der Versandanalysen eines Kampagnen-Workflows.

![](assets/delivery_analysis_priority.png)

Einem großen Versand sollte also vorzugsweise eine niedrige Priorität zugewiesen werden, um die Analyse der anderen Sendungen des Workflows nicht zu verlangsamen.

>[!NOTE]
>
>Um sicherzustellen, dass die Analyse umfangreicher Sendungen die Durchführung Ihrer Workflows nicht bremst, haben Sie die Möglichkeit, die Option **[!UICONTROL Ausführung auf einen Zeitpunkt mit geringer Auslastung verschieben]** anzukreuzen.

## Testversand durchführen {#sending-a-proof}

Um eventuelle Konfigurationsfehler zu erkennen, ist es empfehlenswert, Ihre Sendungen einem Validierungszyklus zu unterziehen. Auf diese Weise können Sie den Inhalt wiederholt von Testempfängern prüfen lassen. Schalten Sie nach jeder Änderung einen neuen Testversand, um den Inhalt abschließend validieren zu lassen.

>[!NOTE]
>
>* Die verfügbaren Validierungsmodi werden unter [Validierungsmodus ändern](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode) detailliert beschrieben.
>* Die Konfiguration der Testversand-Zielgruppe wird unter [Spezifische Testversand-Zielgruppe definieren](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target) beschrieben.

>



Gehen Sie wie folgt vor, um einen Testversand durchzuführen:

1. Stellen Sie sicher, dass die Testversand-Zielgruppe wie unter [Spezifische Testversand-Zielgruppe definieren](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target) beschrieben konfiguriert wurde.
1. Wählen Sie **[!UICONTROL Testversand auslösen]** in der Symbolleiste am oberen Rand des Versand-Assistenten aus.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Starten Sie die Nachrichtenanalyse. Siehe [Versand analysieren](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
1. Sie können den Versand jetzt starten (siehe [Versand senden](../../delivery/using/steps-sending-the-delivery.md)).

   Nach dem Versand gestartet wurde, wird der Testversand in der Versandliste angezeigt und automatisch erstellt und nummeriert. Er kann bearbeitet werden, wenn Sie auf den Inhalt und die Eigenschaften zugreifen möchten. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Wenn ein Versand mit Inhalten in verschiedenen Formaten (HTML und Text) erstellt wurde, können Sie entscheiden, welches Format den Testversand-Empfängern zugestellt werden soll. Wählen Sie im unteren Bereich des Fensters zur Testversand-Zielgruppenauswahl die entsprechende Option aus.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

Zur Einarbeitung der Hinweise der Testversand-Empfänger werden verschiedene Änderungen im Versandinhalt vorzunehmen sein. Im Anschluss an diese Änderungen müssen Analyse und Testversand erneut durchgeführt werden. Die fortlaufend nummerierten Testsendungen werden im Versandprotokoll verzeichnet.

Klicken Sie auf den Tab **[!UICONTROL Testsendungen]** des Protokolls (Rubrik **[!UICONTROL Verfolgung]**), um einen Überblick über die gesamte Testversandliste zu erhalten.

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

Nach Abschluss des Validierungszyklus kann der Versand der Hauptzielgruppe zugestellt werden.

Im Tab **[!UICONTROL Erweitert]** der Versandeigenschaften kann der Testversand konfiguriert werden. Bei Bedarf können Sie die Ausschlussregeln überschreiben.

![](assets/s_ncs_user_wizard_email01_145.png)

Folgende Optionen stehen zur Verfügung:

* Beibehaltung von doppelten Adressen und Empfängern;
* Mit beiden der folgenden Optionen können Sie Empfänger auf der blockierungsliste und Adressen in der Quarantäne behalten. Eine Beschreibung dieser Optionen für die Hauptzielgruppe finden Sie unter [Ausschlussparameter anpassen](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings). Im Gegensatz zur Zielgruppe eines Versands, bei dem diese Adressen standardmäßig ausgeschlossen sind, werden sie standardmäßig für die Zielgruppe eines Testversands beibehalten.
* Wenn Sie die Option **[!UICONTROL Versandcode für den Testversand beibehalten]** auswählen, werden Haupt- und Testversand unter dem gleichen Code geführt, welcher im ersten Schritt des Versandassistenten vergeben wird.
* Standardmäßig enthält der Betreff des Testversands &#39;Proof #‘, wobei # der Nummer des Testversands entspricht. Sie können dieses Präfix im Feld **[!UICONTROL Titelpräfix]** ändern.

## Validierung mit Typologien {#validation-process-with-typologies}

Während der Versandanalyse werden Inhalt und Konfiguration anhand gewisser Regeln geprüft. Standardmäßig beziehen sich die **Typologieregeln** für E-Mails auf folgende Punkte:

* Validierung des Betreffs,
* Validierung von URLs und Bildern,
* Validierung der URL-Titel,
* Validierung des Abmelde-Links,
* Prüfung der Testversandgröße,
* Prüfung der Gültigkeitsdauer,
* Prüfung der Schub-Planung.

Die jeweils anzuwendenden Regeln werden im **[!UICONTROL Typologie]**-Tab der Versandeigenschaften ausgewählt.

Sie können auf die Typologieregeln im Knoten **[!UICONTROL Administration > Kampagnenverwaltung > Typologieverwaltung > Typologieregeln]** zugreifen, um z. B. eine ausführliche Beschreibung zu erhalten oder die Reihenfolge der Anwendung festzulegen.

An dieser Stelle können auch neue Regeln und Typologien erstellt werden. Dies sollte jedoch erfahrenen Anwendern mit JavaScript-Kenntnissen vorbehalten bleiben.

Weitere Informationen zu Typologieregeln finden Sie unter [Grundlagen zu Kampagnentypologien](../../campaign/using/about-campaign-typologies.md).

Klicken Sie zur Bearbeitung der aktuellen Typologie auf das Symbol **[!UICONTROL Verknüpftes Element öffnen]** (rechts vom Feld **[!UICONTROL Typologie]**).

![](assets/s_ncs_user_email_del_typo_tab.png)

Im Tab **[!UICONTROL Regeln]** finden Sie die Liste der anzuwendenden Typologieregeln. Ihre genaue Konfiguration können Sie durch Klick auf das Symbol **[!UICONTROL Details...]** einsehen:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>Typologien vom Typ **[!UICONTROL Schlichtung]** kommen im Bereich des Werbedruck-Managements zum Einsatz. Lesen Sie diesbezüglich [diesen Abschnitt](../../campaign/using/about-marketing-resource-management.md).

## Validierungsmodus ändern {#changing-the-approval-mode}

Der **[!UICONTROL Analyse]**-Tab in den Versandeigenschaften bietet die Möglichkeit, einen Validierungsmodus zu wählen. So können Sie angeben, ob ein Versand trotz Erzeugung von Warnhinweisen bei der Analyse (z. B. weil im Versandbetreff bestimmte Sonderzeichen wie § oder $ verwendet wurden) gestartet werden soll oder nicht. Standardmäßig muss der Benutzer den Versand der Nachrichten nach Abschluss der Analyse bestätigen. Es handelt sich in diesem Fall um eine **manuelle** Validierung.

In der Dropdown-Liste des entsprechenden Felds

![](assets/s_ncs_user_email_del_validation_mode.png)

stehen folgende Validierungsmodi zur Verfügung:

* **[!UICONTROL Manuell]**: Am Ende der Analysephase muss der Benutzer die Absendung bestätigen, um die Nachrichten abzuschicken. Klicken Sie dazu auf die Schaltfläche **[!UICONTROL Start]**, um den Versand zu starten.
* **[!UICONTROL Halbautomatisch]**: Die Nachrichten werden automatisch abgeschickt, wenn die Analysephase ohne Warnhinweise abschließt.
* **[!UICONTROL Automatisch]**: Die Nachrichten werden unabhängig vom Ergebnis der Analysephase automatisch abgeschickt.
