---
product: campaign
title: Senden von Transaktions-E-Mails mit Anhängen
description: Erfahren Sie, wie Sie mit Adobe Campaign Transaktions-E-Mails mit individuellen und/oder personalisierten Anhängen versenden können.
feature: Transactional Messaging, Message Center
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 99%

---

# Anwendungsbeispiel: Senden von Transaktions-E-Mails mit Anhängen {#transactional-email-with-attachments}



In diesem Anwendungsbeispiel sollen E-Mail-Anhänge dynamisch zu ausgehenden Sendungen hinzugefügt werden.

## Die wichtigsten Schritte {#key-steps}

In diesem Szenario erfahren Sie, wie Sie Transaktions-E-Mails mit individuellen und/oder personalisierten Anhängen versenden können. Die Anhänge werden nicht vorab auf den Transaktionsnachrichtenversand-Server hochgeladen, sondern dynamisch generiert.

Wenn Sie Kundeninteraktionen oder Daten erfassen, müssen Sie diese Informationen unter Umständen am Ende dieses Vorgangs beispielsweise in Form einer an eine E-Mail angehängten PDF-Datei an den Kunden zurücksenden.

Hier werden die allgemeinen Schritte für diesen Vorgang beschrieben.

1. Der Kunde öffnet die Webseite und findet ein Produkt, das er kaufen möchte.
1. Der Kunde wählt das Produkt aus und passt einige Optionen an.
1. Der Kunde schließt die Transaktion ab.
1. Dem Kunden wird eine E-Mail zur Bestätigung der Transaktion gesendet. Da davon abzuraten ist, in der E-Mail personenbezogene Daten (Personally Identifiable Information, PII) zu senden, wird eine sichere PDF-Datei erzeugt und an die E-Mail angehängt.
1. Der Kunde erhält die E-Mail und den Anhang mit den relevanten Daten.

In diesem Szenario werden die Anhänge nicht vorab erstellt, sondern den ausgehenden E-Mails dynamisch hinzugefügt, was folgende Vorteile bietet:

* Sie können den Inhalt des Anhangs personalisieren.
* Wenn der Anhang mit einer Transaktion verknüpft ist (wie im oben beschriebenen Beispiel), kann er dynamische Daten enthalten, die im Laufe des Kundenprozesses generiert werden.
* Das Anhängen von PDF-Dateien erhöht die Sicherheit, da Sie diese verschlüsseln und über HTTPS senden können.

## Recommendations und Limits {#important-notes}

Um Performance-Probleme zu vermeiden, dürfen die in den E-Mails enthaltenen Bilder nicht größer als 100 KB sein. Diese standardmäßig festgelegte Beschränkung kann in der Option `NmsDelivery_MaxDownloadedImageSize` geändert werden. Adobe empfiehlt jedoch dringend, große Bilder in E-Mail-Sendungen zu vermeiden.

Adobe empfiehlt außerdem, die Größe und Anzahl der angehängten Dateien zu begrenzen. Standardmäßig kann nur eine Datei als Anhang zu einer E-Mail hinzugefügt werden. Dieser Schwellenwert kann in der Option `NmsDelivery_MaxRecommendedAttachments` konfiguriert werden.

Weitere Informationen finden Sie in der [Liste der Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md#delivery).

Bevor Sie dieses Szenario implementieren, lesen Sie die folgenden Leitlinien sorgfältig durch:

* Die Instanzen für Transaktionsnachrichten sollten nicht zum Speichern, Exportieren oder Hochladen von Dateien oder Daten verwendet werden. Sie dürfen nur für Ereignisdaten und zugehörige Informationen verwendet werden. Sie dürfen nicht als Dateispeichersystem betrachtet werden.
* Da außerhalb von Adobe kein direkter Zugriff auf die Instanzen oder Server für Transaktionsnachrichten besteht, ist keine Standardmethode zum Übertragen solcher Dateien auf diese Server verfügbar (kein FTP-Zugriff).
* Gemäß dem Vertrag ist es untersagt, den Speicherplatz der Instanzen für Transaktionsnachrichten zum Speichern jeglicher Typen von Dateien zu verwenden. Dies gilt auch für Anhänge.
* Sie müssen zum Hosten dieser Dateien ein anderes Online-Speichersystem verwenden. Sie benötigen FTP-Zugriff auf das System und müssen Dateien schreiben und löschen können.

>[!NOTE]
>
>Zur Vermeidung von Performance-Problemen wird empfohlen, nicht mehr als einen Anhang pro E-Mail hinzuzufügen. Der empfohlene Schwellenwert kann über [die Liste der Campaign Classic-Optionen](../../installation/using/configuring-campaign-options.md#delivery) konfiguriert werden.

## Implementierung {#implementation}

Das folgende Diagramm zeigt die verschiedenen Schritte bei der Implementierung dieses Szenarios:

![](assets/message-center-uc1.png)

Gehen Sie wie folgt vor, um einer Transaktionsnachricht dynamisch einen E-Mail-Anhang hinzuzufügen:

1. Gestalten Sie zunächst Ihren Anhang. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   So können Sie die Dateien an eine E-Mail anhängen, selbst wenn sie nicht in der Ausführungsinstanz gehostet werden.

1. Sie können E-Mails über einen SOAP-Nachrichtenauslöser senden. Im SOAP-Aufruf gibt es einen URL-Parameter (attachmentURL).

   Weitere Informationen zu SOAP-Anfragen finden Sie unter [Ereignisbeschreibung](../../message-center/using/event-description.md).

1. Klicken Sie beim Erstellen Ihrer E-Mail auf **[!UICONTROL Anhang]**.

1. Geben Sie im Bildschirm **[!UICONTROL Definition eines Anhangs]** den SOAP-Anhangsparameter ein:

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. Bei der Verarbeitung der Nachricht ruft das System die Datei vom Remote-Speicherort (Drittpartei-Server) ab und hängt sie an die jeweilige Nachricht an.

   Da es sich bei diesem Parameter um eine Variable handeln kann, sollte die Nachricht die über den SOAP-Aufruf gesendete vollständige Remote-URL-Variable Ihrer Datei akzeptieren.

   ![](assets/message-center-uc2.png)
