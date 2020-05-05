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
translation-type: ht
source-git-commit: 7bcf222f41c0e40368644b76197b07f2ded699f0

---


# Versand validieren {#validating-the-delivery}

Der erstellte und konfigurierte Versand muss vor dem Senden an die Hauptzielgruppe validiert werden.

Gehen Sie dazu wie folgt vor:

1. **Versand analysieren** – hier erfolgt die Vorbereitung der zu sendenden Nachrichten. Siehe [Versand analysieren ](#analyzing-the-delivery).

   Die verfügbaren Validierungsmodi werden unter [Validierungsmodus ändern](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode) detailliert beschrieben.

1. **Testsendungen durchführen** – hier erfolgt die Validierung von Inhalt, URLs, Personalisierungsfeldern usw. Siehe [Testversand durchführen](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) und [Spezifische Testversand-Zielgruppe definieren](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!CAUTION]
>
>Beide Schritte sind erforderlich und müssen nach jeder Änderung des Nachrichteninhalts wiederholt werden.

## Versand analysieren {#analyzing-the-delivery}

Die Analyse ist die Phase, in der die Zielpopulation berechnet und der Versandinhalt vorbereitet wird. Sobald sie abgeschlossen ist, ist der Versand startbereit. Um die Versandanalyse zu starten, klicken Sie auf **[!UICONTROL Senden]** und wählen Sie **[!UICONTROL Sendungen schnellstmöglich abschicken]** aus.

![](assets/s_ncs_user_email_del_send.png)

Über die Schaltfläche **[!UICONTROL Analysieren]** können Sie die Analyse manuell starten. Die Statusbar zeigt den Bearbeitungsfortschritt an. Im unteren Bereich des Bildschirms wird das Ergebnis der Analyse angezeigt, wobei Warnhinweise durch spezifische Symbole gekennzeichnet werden.

![](assets/s_ncs_user_interface_delivery04b.png)

>[!NOTE]
>
>Die Validierungsregeln werden unter [Validierung mit Typologien](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) beschrieben.

Es ist jederzeit möglich, den Vorgang durch Klick auf die Schaltfläche **[!UICONTROL Abbrechen]** zu unterbrechen.

![](assets/s_ncs_user_wizard_email01_16.png)

Während der Analysephase werden noch keine Nachrichten versandt. Sie können diesen Vorgang daher so oft wie nötig starten und unterbrechen.

>[!CAUTION]
>
>Der Zustand des Versands (oder Testversands) wird zum Zeitpunkt der Analyse festgeschrieben. Jede Änderung des Versands (oder Testversands) muss durch eine erneute Analysephase bestätigt werden.

Der letzte Logeintrag zeigt eventuelle Fehler und deren Anzahl an. Ein spezifisches Symbol verdeutlicht den Fehlertypen. Ein gelbes Symbol kennzeichnet beispielsweise einen nicht blockierenden Verarbeitungsfehler, während ein rotes Symbol einen Fehler bezeichnet, der den Start des Versands verhindert.

![](assets/s_ncs_user_email_del_analyze_error.png)

Klicken Sie auf **[!UICONTROL Schließen]**, um die Fehler zu korrigieren. Führen Sie dann eine neue Analyse durch.

Prüfen Sie zunächst das Ergebnis der Analyse und klicken Sie dann auf **[!UICONTROL Absendung bestätigen]**, um die Nachrichten an die gewählte Zielgruppe zu senden. Durch Bestätigung des Pop-ups wird der Versand gestartet.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Klicken Sie auf den Link **[!UICONTROL Hauptzielgruppe des Versands ändern]**, wenn die Anzahl der zu sendenden Nachrichten nicht Ihrer Konfiguration entspricht. Passen Sie die Zielpopulation entsprechend an und analysieren Sie erneut den Versand.

Der **[!UICONTROL Analyse]**-Tab in den Versandeigenschaften ermöglicht die Konfiguration verschiedener Parameter in Bezug auf die Nachrichtenvorbereitung im Zuge der Analyse.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

Folgende Optionen stehen zur Verfügung:

* **[!UICONTROL Titel und Versandcode]** - die Optionen in diesem Bildschirmbereich ermöglichen die Berechnung der entsprechenden Felder im Zuge der Versandanalyse. Das Feld **[!UICONTROL Ausführungsordner bei der Versandanalyse berechnen]** ermöglicht die Berechnung des Namens der Datei, die diese Versandaktion im Zuge der Analysephase enthalten wird.
* **[!UICONTROL Validierungsmodus]**: In diesem Feld können Sie den Typ der Versandvalidierung auswählen. Die Validierungsmodi werden unter [Validierung mit Typologien](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) beschrieben.
* **[!UICONTROL Personalisierungsdaten mit einem Workflow vorbereiten]**: Mit dieser Option können Sie die im Versand enthaltenen Personalisierungsdaten in einem automatischen Workflow vorbereiten. Dies verbessert erheblich die Leistung der Versandanalyse, wenn eine große Datenmenge verarbeitet wird, insbesondere wenn die Personalisierungsdaten von einer externen Tabelle per FDA kommen. Lesen Sie hierzu auch den Abschnitt [Zugriff auf externe Datenbanken (FDA)](../../platform/using/additional-options.md#optimizing-email-personalization-with-external-data).
* **[!UICONTROL Vorgang in einem separaten Prozess starten]** - die Versandanalyse wird in einem separaten Prozess durchgeführt. Standardmäßig verwendet die Analysefunktion den Prozess des Adobe-Campaign-Anwendungsserver (nlserver web). Durch Ankreuzen dieser Option stellen Sie sicher, dass die Analyse selbst im Falle eines Problems mit dem Anwendungsserver vollständig durchgeführt wird.
* **[!UICONTROL Zielbestimmungs- und Personalisierungsabfragen im Protokoll speichern]** - schreibt in der Analysephase die SQL-Abfrage-Logs in das Versandprotokoll.
* **[!UICONTROL Personalisierungsscripts beim Versand ignorieren]** - im HTML-Inhalt enthaltene JavaScript-Anweisungen werden nicht interpretiert, sondern 1:1 in den gesendeten Inhalten abgebildet. Die Anweisungen beginnen mit dem Tag **&lt;%=**.

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
* Mit beiden der folgenden Optionen können Sie Blacklist-Empfänger und -Adressen in Quarantäne halten. Eine Beschreibung dieser Optionen für die Hauptzielgruppe finden Sie unter [Ausschlussparameter anpassen](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings). Im Gegensatz zur Zielgruppe eines Versands, bei dem diese Adressen standardmäßig ausgeschlossen sind, werden sie standardmäßig für die Zielgruppe eines Testversands beibehalten.
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
