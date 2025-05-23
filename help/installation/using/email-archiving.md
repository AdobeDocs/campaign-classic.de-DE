---
product: campaign
title: E-Mail-Archivierung
description: E-Mail-Archivierung
feature: Installation, Instance Settings, Email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 82%

---

# E-Mail-BCC konfigurieren {#email-archiving}



Sie können Adobe Campaign so konfigurieren, dass von den von der Plattform gesendeten E-Mails eine Kopie beibehalten wird.

Adobe Campaign selbst ermöglicht zwar nicht die Verwaltung von archivierten Dateien, Sie können aber die gewünschten Nachrichten an eine bestimmte Adresse senden, wo sie mithilfe eines externen Systems verarbeitet und archiviert werden.

Dazu werden E-Mail-Dateien, die den gesendeten E-Mails entsprechen, auf einen Remote-Server, z. B. einen SMTP-E-Mail-Server, übertragen. Das Archivierungsziel ist eine BCC-E-Mail-Adresse (für die Versand-Empfänger unsichtbar), die Sie angeben müssen.

## Empfehlungen und Einschränkungen            {#recommendations-and-limitations}

* Die Funktion &quot;E-Mail-BCC&quot; ist optional. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.
* Wenden Sie sich bei **gehosteten und hybriden Architekturen** an Ihren Kundenbetreuer, um sie zu aktivieren. Die gewünschte BCC-E-Mail-Adresse muss dem Adobe-Team, das die Adresse für Sie konfigurieren wird, mitgeteilt werden.
* Befolgen **bei On-Premise** Installationen die folgenden Richtlinien zur Aktivierung. Weitere Informationen finden Sie in den Abschnitten [Aktivieren von E-Mail-BCC (On-Premise)](#activating-email-archiving--on-premise-) und [Konfigurieren der BCC-E-Mail-Adresse (On-Premise)](#configuring-the-bcc-email-address--on-premise-).
* Sie können nur eine einzige BCC-E-Mail-Adresse verwenden.
* Nachdem E-Mail-BCC konfiguriert wurde, stellen Sie sicher, dass die Funktion in der Versandvorlage oder im Versand über die Option **[!UICONTROL E-Mail-BCC]** aktiviert ist. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/sending-messages.md#archiving-emails).
* Nur erfolgreich gesendete E-Mails werden berücksichtigt, Absprünge nicht.
* Das E-Mail-Archivierungssystem wurde mit Adobe Campaign 17.2 (Build 8795) geändert. Wenn Sie bereits die E-Mail-Archivierung verwendet haben, müssen Sie das Upgrade auf das neue E-Mail-BCC-System manuell durchführen. Weiterführende Informationen hierzu finden Sie im Abschnitt [Wechseln zum neuen E-Mail-BCC](#updated-email-archiving-system--bcc-).

## Aktivieren von E-Mail-BCC (On-Premise) {#activating-email-archiving--on-premise-}

[!BADGE Hybrid und On-Premise]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"}


Gehen Sie wie unten beschrieben vor, um die BCC-E-Mail-Archivierung zu aktivieren, wenn Adobe Campaign vor Ort installiert ist.

### Lokaler Ordner {#local-folder}

Um die Übertragung von gesendeten E-Mails an eine BCC-E-Mail-Adresse zu ermöglichen, müssen zunächst genaue Kopien der gesendeten E-Mails als .eml-Dateien in einem lokalen Ordner gespeichert werden.

Der Pfad für den lokalen Ordner muss in der **Datei &quot;config-`<instance>`.xml** &quot;aus der Konfiguration angegeben werden. Beispiel:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Es liegt in der Verantwortung des Teams, das das Projekt implementiert, sicherzustellen, dass die Sicherheitseinstellungen den Zugriff auf den Ordner erlauben, der über die Parameter **dataLogPath** definiert wurde.

Der vollständige Pfad lautet wie folgt: **`<datalogpath>  YYYY-MM-DDHHh`**. Datum und Uhrzeit werden gemäß der Uhr des MTA-Servers (UTC) festgelegt. Beispiel:

```
C:\emails\2018-12-02\13h
```

Der Name der Archivdatei ist **`<deliveryid>-<broadlogid>.eml`** der Status der E-Mails nicht **[!UICONTROL gesendet]**. Sobald der Status auf **[!UICONTROL Gesendet]** geändert wurde, wird der Dateiname **`<deliveryid>-<broadlogid>-sent.eml`** angezeigt. Beispiel:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In einer Mid-Sourcing-Instanz befindet sich das Verzeichnis für die BCC-E-Mails auf dem Mid-Sourcing-Server.
>
>Die deliveryID und die BroadlogID stammen vom Mid-Sourcing-Server, wenn der Status der E-Mails nicht gesendet wird. Sobald der Status auf **[!UICONTROL Gesendet]** geändert wurde, stammen diese IDs vom Marketing-Server.

### Parameter {#parameters}

Nachdem der lokale Ordnerpfad definiert wurde, fügen Sie die folgenden Elemente wie gewünscht in der **config-`<instance name>.xml`** Datei hinzu und bearbeiten Sie sie. Nachfolgend sind die Standardwerte aufgeführt:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: Format, das beim Komprimieren der .eml-Dateien verwendet wird. Die möglichen Werte sind:

  **0**: keine Komprimierung (Standardwert)

  **1**: Komprimierung (.zip-Format)

* **compressBatchSize**: Anzahl der eml-Dateien, die einem Archiv hinzugefügt wurden (.zip-Datei).


* **archivingType**: zu verwendende Archivierungsstrategie. Der einzige mögliche Wert ist **1**. Rohkopien der gesendeten E-Mails werden im .eml-Format im Ordner **dataLogPath** gespeichert und über SMTP an die BCC-E-Mail-Adresse gesendet. Sobald die E-Mail-Kopien an die BCC-Adresse gesendet werden, wird der Name der Archivdatei **`<deliveryid>-<broadlogid>-sent-archived.eml`** und die Datei wird in den Ordner **dataLogPath/archives** verschoben. Der Pfad der gesendeten und archivierten E-Mail-Datei wird dann **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`** angezeigt.

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**: Anzahl der Tage .eml-Dateien werden zur Archivierung aufbewahrt. Nach dieser Verzögerung werden sie zur Komprimierung automatisch in den Ordner **dataLogPath/archives** verschoben. Standardmäßig laufen .eml-Dateien nach zwei Tagen ab.
* **purgeArchivesDelay**: Die Anzahl der Tage, die Archive im **Ordner &quot;dataLogPath/`<archives>`** &quot;gespeichert werden. Nach diesem Zeitraum werden sie endgültig gelöscht. Die Bereinigung beginnt mit dem Start der MTA. Standardmäßig wird sie alle sieben Tage durchgeführt.
* **pollDelay**: Überprüfungsfrequenz (in Sekunden) für neue eingehende gesendete E-Mails im **Ordner &quot;dataLogPath** &quot;. Wenn dieser Parameter beispielsweise auf 60 gesetzt ist, bedeutet dies, dass der Archivierungsprozess jede Minute die .eml-Dateien in den **`<date and time>`** dataLogPath/-Ordnern durchläuft, bei Bedarf eine Bereinigung durchführt und E-Mail-Kopien an die BCC-Adresse sendet und/oder die archivierten Dateien komprimiert, wann immer dies erforderlich ist.
* **acquisitionLimit**: Anzahl der .eml-Dateien, die gleichzeitig verarbeitet werden, bevor der Archivierungsprozess gemäß dem Parameter **pollDelay** erneut angewendet wird. Wenn Sie beispielsweise den Parameter **acquisitionLimit** auf 100 setzen, während der Parameter **pollDelay** auf 60 eingestellt ist, werden 100 .eml-Dateien pro Minute verarbeitet.
* **smtpNbConnection**: Anzahl der SMTP-Verbindungen zur BCC-E-Mail-Adresse.

Stellen Sie sicher, dass Sie diese Parameter an den E-Mail-Versand-Durchsatz anpassen. In einer Konfiguration, in der die MTA 30.000 E-Mails pro Stunde sendet, können Sie den Parameter **pollDelay** auf 600, den Parameter **acquisitionLimit** auf 5000 und den Parameter **smtpNbConnection** auf 2 setzen. Das bedeutet, dass bei Verwendung von 2 SMTP-Verbindungen alle 10 Minuten 5.000 E-Mails an die BCC-Adresse gesendet werden.

## Konfigurieren der BCC-E-Mail-Adresse (On-Premise) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE Hybrid und On-Premise]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"}


>[!IMPORTANT]
>
>Aus Datenschutzgründen müssen BCC-E-Mails von einem Archivierungssystem bearbeitet werden, in dem personenbezogene Daten (PII, Personally Identifiable Information) sicher aufbewahrt werden.

Verwenden Sie in der **config-`<instance name>.xml`** -Datei die folgenden Parameter, um den SMTP-E-Mail-Server zu definieren, auf den die gespeicherten Dateien übertragen werden:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: Archivierungsziel der Zielgruppe
* **smtpEnableTLS**: mit einer gesicherten SMTP-Verbindung (TLS/SSL-Protokoll)
* **smtpRelayAddress**: zur Verwendung
* **smtpRelayPort**: Relaisanschluss

>[!NOTE]
>
>Wenn Sie einen SMTP-Relais verwenden, werden die Änderungen an den E-Mails, die vom Relais vorgenommen werden, im Archivierungsprozess nicht berücksichtigt.
>
>Darüber hinaus weist der Relais allen E-Mails, einschließlich der nicht gesendeten E-Mails, den Status **[!UICONTROL Gesendet]** zu. Daher werden alle Nachrichten archiviert.

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## Best Practices für E-Mail-BCC {#best-practices}

* **BCC-Adresszeile**: Stellen Sie sicher, dass es über genügend Aufnahmekapazität verfügt, um alle E-Mails zu archivieren, die von der MTA gesendet werden.
* **MTA-Pooling**: Die BCC-Archivierungsfunktion funktioniert auf MTA-Ebene. Damit können Sie alle E-Mails, die von der MTA gesendet werden, Duplikat werden. Da der MTA über mehrere Instanzen hinweg (z. B. Entwicklung, Test oder Produktion) oder sogar über mehrere Clients hinweg (in einer Mid-Sourcing-Umgebung) gepoolt werden kann, wirkt sich das Einrichten dieser Funktion negativ auf die Sicherheit aus:

   * Wenn Sie eine MTA für mehrere Clients freigeben und bei einem dieser Clients diese Option aktiviert ist, greift dieser Client auf alle E-Mails der anderen Clients zu, die dieselbe MTA verwenden. Um eine solche Situation zu vermeiden, verwenden Sie für jeden Client eine andere MTA.
   * Wenn Sie dieselbe MTA für mehrere Instanzen verwenden (Entwicklung, Test, Test), werden die Nachrichten, die von allen drei Instanzen gesendet werden, von der Option dataLogPath dupliziert.

* **E-Mails pro Verbindung**: Die BCC E-Mail-Archivierung funktioniert durch Öffnen einer Verbindung und Versenden aller E-Mails über diese Verbindung. Adobe empfiehlt, mit Ihrem internen technischen Ansprechpartner die Anzahl der E-Mails zu überprüfen, die in einer bestimmten Verbindung akzeptiert werden. Eine Erhöhung dieser Zahl kann einen großen Einfluss auf den BCC-Durchsatz haben.
* **BCC sendet IPs**: Derzeit werden BCC-E-Mails nicht über die normalen MTA-Proxys gesendet. Stattdessen wird eine direkte Verbindung vom MTA-Server zum Ziel-E-Mail-Server geöffnet. Dies bedeutet, dass Sie je nach E-Mail-Server-Konfiguration möglicherweise zusätzliche IPs zu der -Zulassungsliste in Ihrem Netzwerk hinzufügen müssen.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->