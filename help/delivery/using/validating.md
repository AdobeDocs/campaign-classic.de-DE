---
product: campaign
title: Validierung
description: Validierung
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Direct Mail
hide: true
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
TQID: https://experienceleague.adobe.com/I31u-kAqMRpzti-bOtfYjrGbwvmsfeEPwWU7kCFLzcQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 277
ht-degree: 100%

---

# Validierung{#validating}



In [diesem Abschnitt](steps-validating-the-delivery.md) werden globale Konzepte zur Validierung eines Versands vorgestellt.

Die Ausgabedatei eines Briefpost-Versands wird während der Versandanalyse generiert. Der Inhalt der Datei hängt von den ausgewählten Ausgabespalten ab (siehe [Extraktionsdatei](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>Die Analysephase ist im Abschnitt [Versand analysieren](steps-validating-the-delivery.md#analyzing-the-delivery) ausführlich beschrieben.

Während der Analysephase wird die Datei generiert, es werden aber keine Empfängerinformationen (z. B. Versandlogs) aktualisiert. Sie können diesen Auftrag daher ohne Risiko abbrechen.

Prüfen Sie jetzt das Ergebnis der Analyse und den Inhalt der Ausgabedatei und klicken Sie dann auf **[!UICONTROL Absendung bestätigen]**. Über eine Bestätigungsnachricht kann der Versand gestartet werden.

Mit der Absendebestätigung wird die Extraktion der Daten in die angegebene Datei gestartet.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Nun können Sie den Assistenten schließen und die Versand-Logs auf der Registerkarte **[!UICONTROL Versand]** ansehen, auf die Sie über die Detailansicht des Versands zugreifen können.

Sie können den Abrufmodus der Versandlogs auf der Registerkarte **[!UICONTROL Analyse]** der Versandeigenschaften konfigurieren.

Dabei stehen zwei Modi zur Verfügung:

* **[!UICONTROL Nachrichten werden nach Validierung als gesendet betrachtet]** (Standardmodus): In diesem Funktionsmodus werden alle Versandlogs aktualisiert, sobald der Benutzer den Versand bestätigt (ihr Status wechselt von &#39;Versand ausstehend&#39; zu &#39;Gesendet&#39;). Der Versand wechselt dann automatisch in den Status **[!UICONTROL Abgeschlossen]**.
* **[!UICONTROL Eine Ergebnisdatei listet gesendete und fehlgeschlagene Nachrichten auf]**: Dieser Modus ermöglicht eine Aktualisierung der Broadlogs mittels einer externen Datei vom Dienstleister. In diesem Fall muss ein Workflow zur Verarbeitung dieser Informationen verwendet werden, um den Broadlog-Status zu aktualisieren.

  >[!NOTE]
  >
  >Nach der Aktualisierung der Versandlogs muss der Versandstatus vom Benutzer in **[!UICONTROL Abgeschlossen]** geändert werden.
