---
title: Hinzufügen von Anlagen zu Transaktionsnachrichten mit Adobe Campaign Classic
description: Erfahren Sie, wie Sie mit Adobe Campaign Classic transaktionale E-Mails mit einzelnen und/oder personalisierten Anhängen versenden.
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 24a50fcaad4d9081e5504652eb5b73aa7db1e65f
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 24%

---


# Verwendungsfall: Senden von transaktionalen E-Mails mit Anlagen{#transactional-email-with-attachments}

In diesem Anwendungsbeispiel sollen E-Mail-Anhänge dynamisch zu ausgehenden Sendungen hinzugefügt werden.

## Die wichtigsten Schritte {#key-steps}

In diesem Szenario erfahren Sie, wie Sie transaktionale E-Mails mit einzelnen und/oder personalisierten Anhängen versenden. Die Anlagen werden nicht vorab auf den Transaktionsnachrichtenserver hochgeladen: stattdessen werden sie spontan generiert.

Wenn Sie Kundeninteraktionen oder -details erfassen, müssen Sie diese Informationen möglicherweise am Ende des Prozesses an den Kunden zurücksenden, z. B. in einer PDF-Datei, die an eine E-Mail angehängt ist.

Nachfolgend sind die wichtigsten Schritte dieses Szenarios aufgeführt:

1. Der Kunde öffnet die Webseite und findet ein Produkt, das er kaufen möchte.
1. Der Kunde wählt das Produkt aus und passt einige Optionen an.
1. Der Kunde schließt die Transaktion ab.
1. Dem Kunden wird eine E-Mail zur Bestätigung der Transaktion gesendet. Da es nicht empfohlen wird, in der E-Mail PII (Personally Identizable Information) zu senden, wird eine sichere PDF-Datei generiert und an die E-Mail angehängt.
1. Der Kunde erhält die E-Mail und den Anhang mit den entsprechenden Daten.

In diesem Szenario werden die Anlagen nicht vorab erstellt, sondern den ausgehenden E-Mails direkt hinzugefügt, wovon die folgenden Angebote profitieren:

* Auf diese Weise können Sie den Inhalt der Anlage personalisieren.
* Wenn die Anlage mit einer Transaktion verknüpft ist (wie im Beispiel oben beschrieben), kann sie dynamische Daten enthalten, die während des Kundenprozesses generiert werden.
* Durch das Anhängen von PDF-Dateien wird die Sicherheit optimiert, da sie verschlüsselt und über HTTPS gesendet werden können.

## Empfehlungen  {#important-notes}

Bevor Sie dieses Szenario implementieren, lesen Sie die folgenden Leitlinien sorgfältig durch:

* Die Transaktionsnachrichteninstanzen sollten nicht zum Speichern, Exportieren oder Hochladen von Dateien oder Daten verwendet werden. Sie können nur für Ereignis-Daten und zugehörige Informationen verwendet werden. Sie sollten nicht als Dateisystem für die Datenspeicherung betrachtet werden.
* Da es außerhalb von Adobe keinen direkten Zugriff auf die Transaktionsnachricht-Instanzen oder Server gibt, ist keine Standardmethode zum Übertragen solcher Dateien auf diese Server verfügbar (kein FTP-Zugriff).
* Es ist vertraglich nicht korrekt, den Speicherplatz auf den Transaktionsnachrichteninstanzen zu verwenden, um Dateien jeglicher Art zu speichern, nicht einmal für Anlagen.
* Sie müssen ein anderes Online-Festplattensystem verwenden, um diese Dateien zu hosten. Sie benötigen einen FTP-Zugriff auf dieses System und müssen Dateien schreiben und löschen können.

## Umsetzung {#implementation}

Das folgende Diagramm zeigt die verschiedenen Schritte bei der Implementierung dieses Szenarios:

![](assets/message-center-uc1.png)

Gehen Sie wie folgt vor, um einer Transaktionsnachricht eine E-Mail-Anlage direkt hinzuzufügen:

1. Beginn durch Entwerfen Ihrer Anlage. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Dadurch können Sie die Dateien an eine E-Mail anhängen, auch wenn sie nicht auf der Ausführungsinstanz gehostet werden.

1. Sie können E-Mails über einen SOAP-Nachrichtenauslöser senden. Im SOAP-Aufruf gibt es einen URL-Parameter (attachmentURL).

   Weitere Informationen zu SOAP-Anfragen finden Sie unter [Ereignisbeschreibung](../../message-center/using/event-description.md).

1. Klicken Sie beim Entwerfen Ihrer E-Mail auf **[!UICONTROL Anlage]**.

1. Geben Sie im Bildschirm &quot; **[!UICONTROL Anlagendefinition]** &quot;den Parameter SOAP-Anlage ein:

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. Wenn die Nachricht verarbeitet wird, ruft das System die Datei vom Remote-Speicherort (Drittanbieter-Server) ab und hängt sie an die einzelne Nachricht an.

   Da es sich bei diesem Parameter um eine Variable handeln kann, sollte sie die über den SOAP-Aufruf gesendete vollständige Remote-URL-Variable Ihrer Datei akzeptieren.

   ![](assets/message-center-uc2.png)
