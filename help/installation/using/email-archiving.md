---
title: E-Mail-Archivierung
seo-title: E-Mail-Archivierung
description: E-Mail-Archivierung
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: e7de74feb61cc8f4b386a6ff86fc58b9c9e9ca1d
workflow-type: ht
source-wordcount: '1312'
ht-degree: 100%

---


# E-Mail-Archivierung{#email-archiving}

Sie können Adobe Campaign so konfigurieren, dass von den von der Plattform gesendeten E-Mails eine Kopie beibehalten wird.

Adobe Campaign selbst ermöglicht zwar nicht die Verwaltung von archivierten Dateien, Sie können aber die gewünschten Nachrichten an eine bestimmte Adresse senden, wo sie mithilfe eines externen Systems verarbeitet und archiviert werden.

Dazu werden E-Mail-Dateien, die den gesendeten E-Mails entsprechen, auf einen Remote-Server, z. B. einen SMTP-E-Mail-Server, übertragen. Das Archivierungsziel ist eine BCC-E-Mail-Adresse (für die Versand-Empfänger unsichtbar), die Sie angeben müssen.

## Empfehlungen und Einschränkungen      {#recommendations-and-limitations}

* Die Funktion zum Archivieren von E-Mails ist optional. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.
* Wenden Sie sich bei **gehosteten und hybriden Architekturen** an Ihren Kundenbetreuer, um sie zu aktivieren. Die gewünschte BCC-Adresse muss dem Adobe-Team übermittelt werden, das die Adresse für Sie konfigurieren wird.
* Für **lokale Installationen** folgen Sie den unten stehenden Richtlinien, um sie zu aktivieren - siehe [Aktivieren der E-Mail-Archivierung (vor Ort)](#activating-email-archiving--on-premise-) und [Konfigurieren der BCC-E-Mail-Adresse (vor Ort)](#configuring-the-bcc-email-address--on-premise-) .
* Sie können nur eine einzige BCC-E-Mail-Adresse verwenden.
* Nachdem E-Mail-BCC konfiguriert wurde, stellen Sie sicher, dass die Funktion in der Versandvorlage oder im Versand über die Option E-Mails **[!UICONTROL archivieren]** aktiviert ist. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/sending-messages.md#archiving-emails).
* Nur erfolgreich gesendete E-Mails werden berücksichtigt, Absprünge nicht.
* Das E-Mail-Archivierungssystem wurde mit Adobe Campaign 17.2 (Build 8795) geändert. Wenn Sie bereits mit der E-Mail-Archivierung arbeiten, müssen Sie manuell auf das neue E-Mail-Archivierungssystem (BCC) aktualisieren. Weitere Informationen finden Sie im Abschnitt [Aktualisiertes E-Mail-Archivierungssystem (BCC)](#updated-email-archiving-system--bcc-) .

## Aktivieren der E-Mail-Archivierung (vor Ort) {#activating-email-archiving--on-premise-}

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
>In einer Mid-Sourcing-Instanz befindet sich der Ordner für die archivierten E-Mails auf dem Mid-Sourcing-Server.
>
>Die deliveryID und die BroadlogID stammen vom Mid-Sourcing-Server, wenn der Status der E-Mails nicht gesendet wird. Sobald der Status auf **[!UICONTROL Gesendet]** geändert wurde, stammen diese IDs vom Marketing-Server.

### Parameter {#parameters}

Nachdem der lokale Ordnerpfad definiert wurde, fügen Sie die folgenden Elemente wie gewünscht in der **config-`<instance name>.xml`** Datei hinzu und bearbeiten Sie sie. Nachfolgend sind die Standardwerte aufgeführt:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: Format, das beim Komprimieren der .eml-Dateien verwendet wird. Die möglichen Werte sind:

   **0**: keine Komprimierung (Standardwert)

   **1**: Komprimierung (.zip-Format)

* **compressBatchSize**: Anzahl der eml-Dateien, die einem Archiv hinzugefügt wurden (.zip-Datei).
* **archivingType**: zu verwendende Archivierungsstrategie. Die möglichen Werte sind:

   **0**: Rohkopien gesendeter E-Mails werden im .eml-Format im **Ordner &quot;dataLogPath** &quot;gespeichert (Standardwert). Eine Archivierungskopie der **`<deliveryid>-<broadlogid>-sent.eml`** Datei wird im Ordner **dataLogPath/archives** gespeichert. Der Pfad der gesendeten E-Mail-Datei wird **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`** geändert.

   **1**: Rohkopien gesendeter E-Mails werden im .eml-Format im **Ordner &quot;dataLogPath** &quot;gespeichert und über SMTP an die BCC-E-Mail-Adresse gesendet. Sobald die E-Mail-Kopien an die BCC-Adresse gesendet werden, wird der Name der Archivdatei **`<deliveryid>-<broadlogid>-sent-archived.eml`** und die Datei wird in den Ordner **dataLogPath/archives** verschoben. Der Pfad der gesendeten und archivierten E-Mail-Datei wird dann **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`** angezeigt.

* **expirationDelay**: Anzahl der Tage .eml-Dateien werden zur Archivierung aufbewahrt. Nach dieser Verzögerung werden sie zur Komprimierung automatisch in den Ordner **dataLogPath/archives** verschoben. Standardmäßig laufen .eml-Dateien nach zwei Tagen ab.
* **purgeArchivesDelay**: Die Anzahl der Tage, die Archive im **Ordner &quot;dataLogPath/`<archives>`** &quot;gespeichert werden. Nach diesem Zeitraum werden sie endgültig gelöscht. Die Bereinigung beginnt mit dem Start der MTA. Standardmäßig wird sie alle sieben Tage durchgeführt.
* **pollDelay**: Überprüfungsfrequenz (in Sekunden) für neue eingehende gesendete E-Mails im **Ordner &quot;dataLogPath** &quot;. Wenn dieser Parameter beispielsweise auf 60 gesetzt ist, bedeutet dies, dass der Archivierungsprozess jede Minute die .eml-Dateien in den **`<date and time>`** dataLogPath/-Ordnern durchläuft, bei Bedarf eine Bereinigung durchführt und E-Mail-Kopien an die BCC-Adresse sendet und/oder die archivierten Dateien komprimiert, wann immer dies erforderlich ist.
* **acquisitionLimit**: Anzahl der .eml-Dateien, die gleichzeitig verarbeitet werden, bevor der Archivierungsprozess gemäß dem Parameter **pollDelay** erneut angewendet wird. Wenn Sie beispielsweise den Parameter **acquisitionLimit** auf 100 setzen, während der Parameter **pollDelay** auf 60 eingestellt ist, werden 100 .eml-Dateien pro Minute verarbeitet.
* **smtpNbConnection**: Anzahl der SMTP-Verbindungen zur BCC-E-Mail-Adresse.

Stellen Sie sicher, dass Sie diese Parameter an den E-Mail-Versand-Durchsatz anpassen. In einer Konfiguration, in der die MTA 30.000 E-Mails pro Stunde sendet, können Sie den Parameter **pollDelay** auf 600, den Parameter **acquisitionLimit** auf 5000 und den Parameter **smtpNbConnection** auf 2 setzen. Das bedeutet, dass bei Verwendung von 2 SMTP-Verbindungen alle 10 Minuten 5.000 E-Mails an die BCC-Adresse gesendet werden.

## BCC-E-Mail-Adresse konfigurieren (vor Ort) {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
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

## Aktualisiertes E-Mail-Archivierungssystem (BCC) {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>Das E-Mail-Archivierungssystem (BCC) wurde mit Adobe Campaign 17.2 (Build 8795) geändert. Wenn Sie von einem älteren Build aktualisieren und bereits E-Mail-Archivierungsfunktionen verwenden, müssen Sie manuell auf das neue E-Mail-Archivierungssystem (BCC) aktualisieren.

Nehmen Sie dazu die folgenden Änderungen an der **`config-<instance>.xml`** Datei vor:

1. Entfernen Sie den **Parameter zipPath** vom **`<archiving>`** Knoten.
1. Legen Sie den Parameter **compressionFormat** bei Bedarf auf **1** fest.
1. Legen Sie den Parameter **archivingType** auf **1** fest.

Nachdem E-Mail-BCC konfiguriert wurde, stellen Sie sicher, dass Sie die Option E-Mails **[!UICONTROL archivieren]** in der Versandvorlage oder im Versand auswählen. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/sending-messages.md#archiving-emails).

## Best Practices {#best-practices}

* **BCC-Adresszeile**: Stellen Sie sicher, dass es über genügend Aufnahmekapazität verfügt, um alle E-Mails zu archivieren, die von der MTA gesendet werden.
* **MTA-Mutualisierung**: Die BCC-Archivierungsfunktion funktioniert auf MTA-Ebene. Damit können Sie alle E-Mails, die von der MTA gesendet werden, Duplikat werden. Da die MTA über mehrere Instanzen hinweg (z. B. dev, test oder prod) oder sogar über mehrere Clients (in einer Mid-Sourcing-Umgebung) hinweg mutualisiert werden kann, wirkt sich das Einrichten dieser Funktion auf die Sicherheit aus:

   * Wenn Sie eine MTA für mehrere Clients freigeben und bei einem dieser Clients diese Option aktiviert ist, greift dieser Client auf alle E-Mails der anderen Clients zu, die dieselbe MTA verwenden. Um eine solche Situation zu vermeiden, verwenden Sie für jeden Client eine andere MTA.
   * Wenn Sie dieselbe MTA für mehrere Instanzen verwenden (Entwicklung, Test, Test), werden die Nachrichten, die von allen drei Instanzen gesendet werden, von der Option dataLogPath dupliziert.

* **E-Mails pro Verbindung**: Die BCC E-Mail-Archivierung funktioniert durch Öffnen einer Verbindung und Versenden aller E-Mails über diese Verbindung. Adobe empfiehlt, mit Ihrem internen technischen Ansprechpartner die Anzahl der E-Mails zu überprüfen, die in einer bestimmten Verbindung akzeptiert werden. Eine Erhöhung dieser Zahl kann einen großen Einfluss auf den BCC-Durchsatz haben.
* **BCC sendet IPs**: Derzeit werden BCC-E-Mails nicht über die normalen MTA-Proxys gesendet. Stattdessen wird eine direkte Verbindung vom MTA-Server zum Ziel-E-Mail-Server geöffnet. Dies bedeutet, dass Sie je nach Konfiguration des E-Mail-Servers zusätzliche IPs zur Zulassungsliste im Netzwerk hinzufügen müssen.

