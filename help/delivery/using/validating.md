---
product: campaign
title: Validierung
description: Validierung
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '277'
ht-degree: 100%

---

# Validierung{#validating}



In [diesem Abschnitt](steps-validating-the-delivery.md) werden globale Konzepte zur Validierung eines Versands vorgestellt.

Die Ausgabedatei eines Briefpost-Versands wird während der Versandanalyse generiert. Der Inhalt der Datei hängt von den ausgewählten Ausgabespalten ab (siehe [Extraktionsdatei](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>Die Analysephase ist im Abschnitt [Versand analysieren](steps-validating-the-delivery.md#analyzing-the-delivery) ausführlich beschrieben.

Bei der Erzeugung der Datei werden keine Empfängerinformationen (z. B. Versandlogs) aktualisiert. Der Vorgang kann daher problemlos unterbrochen werden.

Prüfen Sie jetzt das Ergebnis der Analyse und klicken Sie dann auf **[!UICONTROL Absendung bestätigen]**, um die Nachrichten an die gewählte Zielgruppe zu senden. Durch Bestätigung des Pop-ups wird der Versand gestartet.

Mit der Absendebestätigung wird die Extraktion der Daten in die angegebene Datei gestartet.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Nun können Sie den Assistenten schließen und die Logs im **[!UICONTROL Versand]**-Tab ansehen, auf den Sie über die Detailansicht des Versands zugreifen können.

Sie können den Abrufmodus der Versandlogs auf der Registerkarte **[!UICONTROL Analyse]** der Versandeigenschaften konfigurieren.

Dabei stehen zwei Modi zur Verfügung:

* **[!UICONTROL Nachrichten werden nach Validierung als gesendet betrachtet]** (Standardmodus): In diesem Funktionsmodus werden alle Versandlogs aktualisiert, sobald der Benutzer den Versand bestätigt (ihr Status wechselt von &#39;Versand ausstehend&#39; zu &#39;Gesendet&#39;). Der Versand wechselt dann automatisch in den Status **[!UICONTROL Abgeschlossen]**.
* **[!UICONTROL Ergebnisdatei listet gesendete und fehlgeschlagene Nachrichten]**: Dieser Modus ermöglicht eine Aktualisierung der Versandlogs mittels einer externen Datei vom Dienstleister. In diesem Fall ist die Erstellung eines Workflows zur Verarbeitung dieser Informationen notwendig, um den Status der Versandlogs zu aktualisieren.

  >[!NOTE]
  >
  >Nach der Aktualisierung der Versandlogs muss der Versandstatus vom Benutzer in **[!UICONTROL Abgeschlossen]** geändert werden.
