---
solution: Campaign Classic
product: campaign
title: Protokoll und Einstellungen des SMS-Connectors
description: Erfahren Sie mehr über den SMS-Connector und dessen Konfiguration.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '8433'
ht-degree: 99%

---

# Protokoll und Einstellungen des SMS-Connectors {#sms-connector-protocol}

>[!NOTE]
>
>Informationen zu **Protokoll und Einstellungen des SMS-Connectors** für Adobe Campaign Standard finden Sie auf dieser [Seite](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/configuring-sms/sms-protocol.html?lang=de#administrating).
>
>In diesem Dokument beziehen sich alle Informationen zum Protokoll, zum Feldnamen und zu Feldwerten auf die [Spezifikation von SMPP Version 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

## Übersicht {#overview}

SMS ist zwar auf das Senden kurzer Textnachrichten ohne Formatierung beschränkt, aber ihre Einfachheit macht sie zu einem wertvollen Kommunikationskanal.

Es gibt zwei Möglichkeiten, eine SMS zu senden:

* Manuell von einem Telefon aus (die übliche Art und Weise, wie Personen direkt kommunizieren),
* Über das Internet (die Art und Weise, wie Adobe Campaign Nachrichten sendet). Dazu benötigen Sie einen SMS-Dienstleister, der das Internet mit dem Mobilfunknetz verbindet.
Adobe Campaign verwendet das SMPP-Protokoll, um SMS an einen Dienstleister zu senden.

In diesem Dokument wird die Einrichtung einer Verbindung zwischen Adobe Campaign und einem SMPP-Provider erläutert.

SMPP-Provider können manchmal von der offiziellen Spezifikation abweichen. Der SMS-Connector in Adobe Campaign bietet aber viele Optionen zum Anpassen seines Verhaltens, um die Kompatibilität mit den meisten Providern sicherzustellen.

>[!IMPORTANT]
>
>Das Einrichten einer Verbindung zu einem neuen Provider erfordert möglicherweise einige technische Fähigkeiten, Kenntnisse über TCP, die binäre, hexadezimale Darstellung und Textkodierungen. Es erfordert auch eine aktive Zusammenarbeit mit dem Provider.

### SMS-Typen {#sms-types}

Beim Senden von Massen-SMS über einen SMS-Provider kommen drei verschiedene Arten von SMS-Nachrichten vor:

* **SMS MT (Mobile Terminated)**: Eine SMS, die von Adobe Campaign über den SMPP-Provider an Smartphones und Tablets versendet wird.

* **SMS MO (Mobile Originated)**: Eine SMS, die von einem Smartphone oder Tablet über den SMPP-Provider an Adobe Campaign gesendet wird.

* **SMS SR (Status Report = Statusbericht) oder DR oder DLR (Delivery Receipt = Empfangsbestätigung)**: Eine vom Smartphone oder Tablet über den SMPP-Provider an Adobe Campaign gesendete Rückbestätigung, die angibt, dass die SMS erfolgreich empfangen wurde. Adobe Campaign erhält möglicherweise auch einen SR, der angibt, dass die Nachricht nicht zugestellt werden konnte, oft mit einer Fehlerbeschreibung.

Sie müssen zwischen Quittungen (RESP PDU, Teil des SMPP-Protokolls) und SR unterscheiden: SR ist eine Art SMS, die über das Netzwerk gesendet wird, während eine Quittung nur bestätigt, dass eine Übertragung erfolgreich war.

Sowohl Quittungen als auch SR können Fehler auslösen, wobei die Unterscheidung zwischen den beiden bei der Fehlerbehebung hilft.

### Von einer SMS übertragene Informationen {#information-sms}

Eine SMS enthält mehr Informationen als Text. Hier ist eine Liste der Informationen, die Sie in einer SMS erwarten können:

* Der Text, der auf 140 Byte begrenzt ist, was je nach Kodierung zwischen 70 und 160 Zeichen bedeutet. Details und Einschränkungen finden Sie unter [SMS-Textkodierung](../../delivery/using/sms-protocol.md#sms-text-encoding) weiter unten.

* Eine Empfängeradresse, manchmal auch `ADC` oder `MSISDN` genannt. Das ist die Nummer des Mobiltelefons, das die SMS erhält.

* Eine Absenderadresse, die manchmal als `oADC` oder `sender id` bezeichnet wird. Dabei kann es sich um eine herkömmliche Telefonnummer handeln, um eine Kurzwahlnummer, wenn diese über einen Provider gesendet wird, oder um einen Namen. Der Name ist eine optionale Funktion. In diesem Fall können Sie nicht auf die SMS antworten.

* Eine Markierung, die angibt, ob es sich bei der Nachricht um eine Flash-Nachricht handelt. Eine Flash-Nachricht ist ein Popup, das nicht im Speicher abgelegt wird.

* Eine Markierung, die angibt, ob ein SR erwartet wird oder nicht.

* Ein Gültigkeitsdatum, nach dem von den Netzwerkgeräten keine neuen Versuche mehr angestellt werden dürfen.

* Ein `data_coding`-Feld, das die Kodierung des Textes angibt.

## SMPP-Protokoll {#smpp-protocol}

Adobe Campaign Classic unterstützt Version 3.4 des SMPP-Protokolls. SMPP ist ein weit verbreitetes Protokoll, das den Versand von SMS an einen Provider (SMSC) sowie den Empfang von SMS und Empfangsbestätigungen ermöglicht. Weitere Informationen finden Sie in der [SMPP-Dokumentation](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Die Netzwerkgeräte auf der Seite des SMS-Dienstleisters werden oft als SMSC bezeichnet.

### SMPP-Verbindungen {#smpp-connections}

Adobe Campaign verbindet sich über TCP mit den Netzwerkgeräten des SMS-Dienstleisters. Das SMPP-Protokoll stellt permanente TCP-Verbindungen von Adobe Campaign zum Provider her. Die TCP-Verbindungen werden immer von Adobe Campaign initiiert, auch wenn es um den Empfang von Nachrichten geht.
SMPP öffnet je nach Modus 1 oder 2 TCP-Verbindungen. Alle Verbindungen werden immer von Adobe Campaign initiiert.

Das SMPP-Protokoll kann in zwei Modi verwendet werden:

* **Transmitter+Receiver (oder TX+RX)**: Es werden zwei separate TCP-Verbindungen zum Senden und Empfangen von Nachrichten verwendet.
* **Transceiver (oder TRX)**: Es wird eine einzelne TCP-Verbindung zum Senden und Empfangen von Nachrichten verwendet.

>[!NOTE]
>
> Adobe Campaign Classic unterstützt nur den TX+RX-Modus. Dies hängt mit seiner technischen Architektur zusammen.

### SMPP-PDU {#smpp-pdu}

SMPP-Übertragungseinheiten (&quot;Pakete&quot;) werden PDUs genannt. Eine **PDU** enthält einen Befehl, einen Status, eine Sequenznummer und Daten.

Jede PDU muss durch eine `SMPP RESP PDU` (synchrone Antwort) quittiert werden. Anfragen können in einer Pipeline zusammengefasst werden: Der Absender kann viele Befehle senden, ohne auf `RESP` zu warten. Die Anzahl der Anfragen, die zu einem beliebigen Zeitpunkt in einer Pipeline zusammengefasst werden können, wird als Fenster bezeichnet. `RESP PDU` können in jeder beliebigen Reihenfolge eintreffen und sind unabhängig von der Reihenfolge ihrer Initiator-PDU.

Im getrennten **Transmitter + Receiver**-Modus hängt die verwendete Verbindung von der Art der gesendeten Nachricht ab. Die Senderverbindung wird für MT verwendet, und die Empfängerverbindung wird für MO und SR verwendet. Anfragen und Antworten für jede Art von Nachricht werden über dieselbe TCP-Verbindung gesendet.

Wenn beispielsweise ein MT gesendet wird, wird die Senderverbindung verwendet und die `RESP`, die den MT quittiert, wird auch über den Senderkanal gesendet. Wenn Sie einen MO (oder einen SR) erhalten, wird die Empfängerverbindung verwendet, um den MO zu empfangen und die `RESP` zu senden, die den MO quittiert.

![](assets/do-not-localize/sms_protocol_1.png)

In Adobe Campaign Classic wird für die Zuordnung von SR zu ihren entsprechenden MT bei den Schritten `SUBMIT_SM_RESP` und `DELIVER_SM` eine ID vom SMSC zurückgegeben. Die Kennung wird im Feld `providerId` der Tabelle `nms::providerMsgId` gespeichert und `broadLogId` und `deliveryId` zugeordnet. Diese Zuordnung erfolgt im Rahmen des SMS-Prozesses beim Schreiben in die Datenbank.

Eine erfolgreiche `SUBMIT_SM_RESP PDU` löst im Versandprotokoll den Nachrichtenstatus &quot;gesendet&quot; aus, während eine erfolgreiche `DELIVER_SM (SR) PDU` den Nachrichtenstatus &quot;empfangen&quot; auslöst.

### Sicherheitsaspekte {#security-aspects}

Das Protokoll selbst ist nicht verschlüsselt. Die meisten Provider implementieren eine Variante von &quot;IP auf Zulassungsliste&quot;, sodass die IP-Adressen der Adobe Campaign-Server dem Provider mitgeteilt werden müssen.

Adobe Campaign unterstützt die Übergabe von Anmelde- und Kennwortdaten während der Bindungsphase. SMPP über TLS wird ebenfalls unterstützt. Es ist zu beachten, dass für die Gewährleistung eines ordnungsgemäßen Schutzes Zertifikate erforderlich sind. Obwohl der SMPP-Connector das Umgehen von Zertifikatprüfungen erlaubt, sollte dies nur zum Testen verwendet werden, da TLS ohne Zertifikate einen wesentlich geringeren Schutz bietet.

Der Connector verwendet die Standardzertifikate, die von der Systembibliothek `openssl` bereitgestellt werden. Normalerweise wird diese vom `/etc/ssl/certs`-Verzeichnis auf Debian bereitgestellt. Dieses Verzeichnis wird standardmäßig durch das Package &quot;ca-certificates&quot; bereitgestellt, kann aber angepasst werden.

### Informationen in den verschiedenen PDU-Arten {#information-pdu}

Jede Art von PDU verfügt über verschiedene Felder, die unterschiedliche Informationen enthalten. Diese PDUs sind in der [Spezifikation von SMPP Version 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) aufgeführt.

In jedem der folgenden Abschnitte werden die PDU und ihre synchrone Antwort (`*_RESP PDU`) beschrieben. Alle PDUs müssen mit einer entsprechenden `RESP` quittiert werden. Dies ist ein obligatorischer Teil der Spezifikation.

PDUs können optionale Felder haben. Hier werden nur die gebräuchlichsten Felder beschrieben. Weitere Informationen finden Sie in der [Spezifikation von SMPP Version 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Mit dieser PDU wird eine Verbindung zum SMSC initiiert. Die Modi **Transmitter**, **Receiver** und **Transceiver** ändern nur die Art der SMS, die über diese Verbindung übertragen werden darf:

| Modus | Zulässige Arten von SMS |
|:-:|:-:|
| Transmitter | MT |
| Receiver | MO + SR |
| Transceiver | MT + MO + SR |

Wichtige Felder in einer `BIND_* PDU`:

* **system_id**: Für die Authentifizierung verwendete Anmeldedaten. Im externen Konto eingestellt.

* **password**: Für die Authentifizierung verwendetes Passwort. Im externen Konto eingestellt.

* **system_type**: Muss bei einigen Providern auf einen bestimmten Wert eingestellt werden Im externen Konto eingestellt und in allen Versionen verfügbar. Unterscheidet häufig zwischen verschiedenen Arten von Verträgen, Kanälen, Ländern usw.

* **addr_ton** und **addr_npi**: Bei einigen Providern erforderlich. Werden durch die Einstellungen `Bind TON` und `Bind NPI` im externen Konto eingestellt.

* **address_range**: Bei einigen Providern erforderlich. Meistens ist dies eine Liste der für diese Verbindung zulässigen Kurzwahlnummern. Im externen Konto eingestellt.

`BIND_*_RESP` hat kein bestimmtes Feld; bestätigt, ob die Verbindung erfolgreich war oder nicht.

#### UNBIND {#unbind}

Diese PDU muss vom System gesendet werden, bevor die Verbindung getrennt wird. Es muss auf die übereinstimmende `UNBIND_RESP`-PDU warten, bevor die Verbindung geschlossen wird.

Das konforme SMSC darf die Verbindung nicht schließen, die TCP-Verbindung wird über den Adobe Campaign-Connector gesteuert.

#### SUBMIT_SM {#submit-sm}

Diese PDU sendet einen MT an das SMSC. Seine Antwort-PDU gibt die ID des MT an.

Wichtige Felder in einer `SUBMIT_SM`-PDU:

* **service_type**: Bei einigen Providern erforderlich. Wird in den Versandeigenschaften eingestellt.

* **source_addr_ton** und **source_addr_npi**: Geben an, welche Art von Quelladresse übertragen wird. Die Bedeutung dieser Felder ist standardisiert, da sie jedoch von einigen Providern unterschiedlich verwendet werden, sollten Sie den Provider nach seinem korrekten Wert fragen. Im externen Konto eingestellt.

* **source_addr**: Quelladresse/oADC des MT. Auf dem Mobiltelefon angezeigt. Im externen Konto und im Versand eingestellt, der Wert im Versand hat Vorrang vor dem Wert des externen Kontos.

* **dest_addr_ton** und **dest_addr_npi**: Geben an, welche Art von Zieladresse übertragen wird (z. B. lokales oder internationales Format). Die Bedeutung dieser Felder ist standardisiert, da sie jedoch von einigen Providern unterschiedlich verwendet werden, sollten Sie den Provider nach seinem korrekten Wert fragen. Im externen Konto eingestellt.

* **destination_addr**: Empfängeradresse, Telefonnummer oder MSISDN.

* **esm_class**: Wird verwendet, um anzugeben, ob UDH im Textfeld verwendet wird oder nicht. Wird vom Connector automatisch für geteilte SMS aktiviert, wenn der `message_payload`-Modus nicht verwendet wird.

* **priority_flag**: Priorität dieser Nachricht gegenüber anderen. Dies ist an die Priorität des Versands gebunden.

* **validity_period**: Zeitstempel, nach dem kein erneuter Versuch unternommen werden sollte. Wird im Versand eingestellt.

* **registered_delivery**: Gibt an, ob ein SR angefordert wird oder nicht. Adobe Campaign setzt diese Markierung immer, außer bei automatischen Antworten. Bei mehrteiligen Nachrichten wird die Markierung nur für den ersten Teil festgelegt. Alle Versionen weisen dasselbe Verhalten auf.

* **data_coding**: Gibt die im Textfeld verwendete Kodierung an. Weitere Informationen finden Sie im Abschnitt [SMS-Textkodierung](../../delivery/using/sms-protocol.md#sms-text-encoding).

* **short_message**: Der Text der Nachricht. Wenn UDH verwendet wird, enthält dies auch die UHD-Kopfzeile.

Adobe Campaign unterstützt die folgenden optionalen Felder:

* **dest_addr_subunit**: Wird verwendet, um das Ziel der SMS anzugeben: Flash, Mobiltelefon oder SIM-Karte. Wird in den Versandeigenschaften eingestellt.

* **message_payload**: Wenn diese Option im externen Konto aktiviert ist, werden lange Nachrichten in einer einzelnen PDU gesendet und der Text wird in diesem Feld und nicht im `short_message`-Feld übertragen.

#### SUBMIT_SM_RESP {#submit-sm-resp}

Diese PDU enthält die ID des MT. Dies ist nützlich, um sie mit dem eingehenden SR abzugleichen.

>[!IMPORTANT]
>
>Viele Provider übermitteln die MT-ID hexadezimal. Achten Sie darauf, dass Sie die Einstellung **ID-Format in der MT-Quittierung (resp)** im externen Konto korrekt festlegen.

Einige Provider senden `SUBMIT_SM_RESP` nach dem Versand des SR. Um dieses Verhalten zu berücksichtigen, wartet Adobe Campaign 30 Sekunden, bevor mit **Ungültige Nachrichten-ID** auf einen SR mit einer unbekannten ID geantwortet wird.

#### DELIVER_SM {#delivery-sm}

Diese PDU wird vom SMSC an Adobe Campaign gesendet. Sie enthält entweder einen MO oder einen SR.

Die meisten Felder haben dieselbe Bedeutung wie ihr `SUBMIT_SM`-Gegenstück. Hier ist die Liste nützlicher Felder:

* **source_addr**: Quelladresse von MO/SR. Normalerweise ist dies eine Telefonnummer.

* **destination_addr**: Kurzwahlnummer, die den MO oder den SR empfangen hat.

* **esm_class**: Wird verwendet, um anzugeben, ob die PDU ein MO oder ein SR ist.

* **short_message**: Der Text der Nachricht. Für den SR enthält dies Daten, die in Anhang B der SMPP-Protokollspezifikation beschrieben sind. Weitere Informationen finden Sie unter [Umgang mit SR-Fehlern](../../delivery/using/sms-protocol.md#sr-error-management).

Adobe Campaign kann die Nachrichtenkennung im optionalen Feld `receipted_message_id` mit entsprechender Konfiguration lesen.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Diese PDU wird von Adobe Campaign gesendet, um SR und MO zu quittieren.

Adobe Campaign Classic quittiert SR und MO, sobald sie in die Datenbank eingefügt wurden. Dennoch können auch dann noch Verarbeitungsfehler auftreten, wenn eine erfolgreiche `DELIVER_SM_RESP`-PDU gesendet wurde. Dies hängt mit der Software-Architektur von Adobe Campaign Classic zusammen.

#### ENQUIRE_LINK {#enquire-links}

Diese PDU wird nur verwendet, um zu überprüfen, ob die Verbindung live ist. Ihre Häufigkeit sollte entsprechend den Bedürfnissen des Providers festgelegt werden.

Die Standardeinstellung von 60 Sekunden entspricht den meisten im externen Konto festgelegten Konfigurationen.

#### ENQUIRE_LINK_RESP {#enquire-links-resp}

Diese PDU quittiert, dass die Verbindung aktiv ist.

### Mehrteilige SMS (lange SMS) {#multipart}

Mehrteilige SMS oder lange SMS sind SMS, die in mehreren Teilen gesendet werden. Aufgrund technischer Einschränkungen im Mobilfunknetzprotokoll kann eine SMS nicht größer als 140 Byte sein. Andernfalls muss sie aufgeteilt werden. Weitere Informationen zur Anzahl der Zeichen, die in eine SMS passen, finden Sie im Abschnitt [SMS-Textkodierung](../../delivery/using/sms-protocol.md#sms-text-encoding).

Jeder Teil einer langen Nachricht ist eine individuelle SMS. Diese Teile bewegen sich unabhängig voneinander durch das Netzwerk und werden vom empfangenden Mobiltelefon zusammengesetzt. Um zusätzliche Zustellversuche und Verbindungsprobleme zu verarbeiten, sendet Adobe Campaign diese Teile in umgekehrter Reihenfolge und fordert nur einen SR für den ersten Teil der Nachricht an, der zuletzt gesendet wurde. Da das Mobiltelefon eine Nachricht nur anzeigt, wenn der erste Teil empfangen wurde, führen zusätzliche Zustellversuche für weitere Teile nicht zu Duplikaten auf dem Mobiltelefon.

Die maximale Anzahl an SMS pro Nachricht kann pro Versand mithilfe der Einstellung **Maximale Anzahl an SMS pro Nachricht** in der **Versandvorlage** eingestellt werden. Nachrichten, die diesen Grenzwert überschreiten, schlagen beim Versand mit der Fehlermeldung &quot;SMS zu lang&quot; fehl.

Es gibt zwei Möglichkeiten, lange SMS zu senden:

* **UDH**: die standardmäßige und empfohlene Methode zum Senden langer Nachrichten. In diesem Modus teilt der Connector die Nachricht in mehrere `SUBMIT_SM PDU`s mit UDH-Informationen auf. Dieses Protokoll wird von Mobiltelefonen selbst verwendet. Das bedeutet, dass Adobe Campaign die meiste Kontrolle über die Nachrichtengenerierung hat und somit genau berechnen kann, wie viele Teile gesendet und wie sie aufgeteilt wurden.

* **message_payload**: Möglichkeit, die gesamte lange Nachricht in einer einzigen `SUBMIT_SM PDU` zu senden. Der Provider muss sie aufteilen, was bedeutet, dass Adobe Campaign nicht genau wissen kann, wie viele Teile gesendet wurden. Einige Provider erfordern diesen Modus. Wir empfehlen Ihnen jedoch, ihn nur zu verwenden, wenn sie UDH nicht unterstützen.

Weitere Informationen zum Protokoll und den Formaten finden Sie in der Beschreibung der Felder `esm_class`, `short_message` und `message_payload` der [SUBMIT_SM PDU](../../delivery/using/sms-protocol.md#information-pdu).

### Durchsatzbegrenzung und Fenster{#throughput-capping}

Die meisten Provider verlangen eine Durchsatzbegrenzung für jede SMPP-Verbindung. Dies kann durch die Festlegung einer Anzahl von SMS im externen Konto erreicht werden. Beachten Sie, dass die Durchsatzdrosselung pro Verbindung erfolgt. Der gesamte effektive Durchsatz ist die Grenze pro Verbindung multipliziert mit der Anzahl Verbindungen insgesamt. Dies wird im Abschnitt [Simultane Verbindungen](../../delivery/using/sms-protocol.md#connection-settings) beschrieben.

Um den maximal möglichen Durchsatz zu erreichen, müssen Sie eine Feinabstimmung des maximalen Übertragungsfensters vornehmen. Das Übertragungsfenster ist die Anzahl der `SUBMIT_SM PDU`s, die gesendet werden können, ohne auf eine `SUBMIT_SM_RESP` zu warten. Weitere Informationen finden Sie im Abschnitt zum [Übertragungsfenster](../../delivery/using/sms-protocol.md#throughput-timeouts).

### SR und Umgang mit Fehlern (&quot;Anhang B&quot;) {#sr-error-management}

Das SMPP-Protokoll definiert standardmäßige synchrone Fehler in `RESP PDU`s, definiert jedoch keine Fehler-Codes für SRs. Jeder Provider verwendet eigene Fehler-Codes mit der entsprechenden Bedeutung.

Die [SMPP-Protokollspezifikation](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) enthält eine Empfehlung in Anhang B (Seite 167). Die eigentlichen Fehler-Codes und deren Bedeutung sind dort jedoch nicht aufgeführt.

Zur Anpassung an den Umgang mit Fehlern wurde das Broadlog-Meldungssystem von Adobe Campaign genutzt, um Fehler und deren Schweregrad (hart, weich usw.) ordnungsgemäß bereitzustellen.

Wie bereits erwähnt, gibt es zwei Arten von Fehlern:

* synchrone Antworten in den `SUBMIT_SM_RESP`, die unmittelbar nach dem Senden der Nachricht an die SMSC auftreten,
* Empfangsbestätigungen, die erst viel später eingehen, nachdem das Mobilgerät die Nachricht erhalten hat oder die Nachricht abgelaufen ist. In diesem Fall findet man den Fehler in einem SR.

Wenn ein SR empfangen wird, befinden sich Status und Fehler in seinem `short_message`-Feld (Beispiel für Implementierungen, die mit Anhang B übereinstimmen). Das Feld `short_message` der PDU wird häufig als **Textfeld** bezeichnet, da es den Text im MT enthält. Bei einem SR enthält es technische Informationen sowie ein Unterfeld mit dem Namen **Text**. Diese beiden Felder unterscheiden sich, wobei `short_message` das Feld **Text** und andere Informationen enthält.

Das Verhalten der Connectoren von Adobe Campaign Classic ist (mit Ausnahme des erweiterten SMPP) code-seitig festgelegt und hängt vom ausgewählten Provider ab. Bei allgemeinem SMPP wird nur zwischen Erfolg und Fehler unterschieden, jedoch keine Details angegeben. Unter Umständen enthält das Versand-Log einige Informationen, doch ist dies nicht gesichert.

#### SR-Textfeldformat {#sr-text-field-format}

Die Spezifikation empfiehlt die Verwendung dieses Formats für das SR-Textfeld. Es handelt sich dabei um eine Liste von Unterfeldern, die durch Leerzeichen voneinander getrennt sind, um den Feldnamen und den zugehörigen Wert zu trennen. Bei Feldnamen wird nicht zwischen Groß- und Kleinschreibung unterschieden.

Beispiel eines SR-Textfelds, das der Empfehlung in Anhang B entspricht:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Das ID-Feld ist die im `SUBMIT_SM_RESP PDU` empfangene ID, die Bestätigung des MT.

`sub` und `dlvrd` sollen die Anzahl der gelieferten Teile und zugestellten Nachrichten zählen. Dies wird jedoch von Adobe Campaign nicht verwendet, da das Broadlog-System bessere und stärker integrierte Informationen liefert.

Die Felder `submit date` und `done date` enthalten Zeitstempel, die angeben, wann der MT gesendet wurde und wann der SR vom Mobiltelefon gesendet wurde. Hierbei sind einige Probleme mit Zeitzonen oder sogar falschen Zeitstempeln zu erwarten, die von Mobiltelefonen mit falschen Datumsangaben ausgegeben werden.

Das Feld &quot;stat&quot; ist wichtig, da es den Status der Nachricht angibt. Die einzigen wichtigen Status sind `DELIVRD`, `UNDELIV` und `REJECTD`. Der Status `DELIVRD` zeigt einen Erfolg an, die beiden anderen einen Fehler. Andere Werte sind möglich, aber es handelt sich in der Regel um Zwischenbenachrichtigungen, z. B. wenn der MT den Mobilnetzbetreiber erreicht, aber nicht das Mobiltelefon. Diese Zwischenbenachrichtigungen werden von Adobe Campaign ignoriert.

Das Feld &quot;err&quot; enthält den Provider-spezifischen Fehler-Code. Um die Interpretation der Werte zu ermöglichen, muss der Provider eine Tabelle möglicher Fehler-Codes und deren Bedeutung bereitstellen.

Schließlich enthält das Textfeld normalerweise den Anfang des Textes des MT. Dies wird von Adobe Campaign ignoriert und von einigen Providern nicht übertragen, um Lecks personenbezogener Daten und den Verbrauch von Netzwerkbandbreite zu vermeiden. Bei der Fehlersuche kann man durch das Auslesen dieses Felds den zu einem Test-MT passenden SR leichter erkennen.

### Beispiel für die SR-Verarbeitung in Adobe Campaign Classic – erweitertes allgemeines SMPP {#sr-processing}

In diesem Beispiel werden eine Implementierung nach der Empfehlung in Anhang B, die Standardwerte im externen Konto und ein erfolgreicher SMS MT gezeigt.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Zunächst wird Regex `id extraction` angewendet, um die ID zu extrahieren und mit dem entsprechenden MT abzustimmen.

Dann werden Regex `status extraction` und Regex `error code extraction` angewendet, um diese Felder zu extrahieren und an die Zeichenfolge anzuhängen.

Die Broadlog-Meldung wird mit folgenden Informationen erstellt und die ursprüngliche unveränderte Zeichenfolge wird als Referenz angehängt:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Die Nachricht wird dann normalisiert, wobei der MESSAGE-Teil entfernt wird, um mehrere Nachrichten mit demselben Status- und Fehler-Code abgleichen zu können.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Wenn die Nachricht nicht bereits in der Tabelle mit den Broadlog-Meldungen bereitgestellt wurde, wird ein neuer Eintrag erstellt, der die gesamte Nachricht als **firstText** und die normalisierte Nachricht verwendet. Dann verwendet der Connector den Regex &quot;success&quot; und `error`, um festzustellen, ob es sich um einen Erfolg oder einen Fehler handelt:

* Eine Übereinstimmung mit Regex `success` wird als Erfolg betrachtet.

* Wenn die Nachricht mit Regex `error` übereinstimmt, wird sie als Fehler qualifiziert.

* Wenn keine dieser beiden Regex übereinstimmt, wird der SR ignoriert. Möglicherweise handelt es sich um eine Zwischenbenachrichtigung, die von Adobe Campaign nicht verarbeitet wird.

Standardmäßig werden alle Fehler als weiche Fehler bereitgestellt. Das bedeutet, dass harte Fehler von Hand bereitgestellt werden müssen.

### SMS-Textkodierung {#sms-text-encoding}

**Bei Kodierungsproblemen sollten Sie sich immer an den SMSC-Provider wenden**. Nur die SMSC-Provider verfügen über Kenntnisse der von ihnen unterstützten Kodierung und über spezielle Regeln, die aufgrund von Einschränkungen in ihrer technischen Plattform gelten können.

SMS-Nachrichten verwenden eine spezielle 7-Bit-Kodierung, die oft GSM7-Kodierung genannt wird.

Im SMPP-Protokoll wird der GSM7-Text auf 8 Bit pro Zeichen erweitert, um die Fehlerbehebung zu erleichtern. Das SMSC packt ihn in 7 Bit pro Zeichen, bevor er an das Mobilgerät gesendet wird. Das bedeutet, dass das Feld `short_message` der SMS im SMPP-Frame bis zu 160 Byte lang sein kann, während es beim Senden im Mobilfunknetz auf 140 Byte begrenzt ist.

Bei Kodierungsproblemen sollten Sie Folgendes überprüfen:

* Sie sollten wissen, welche Zeichen zu welcher Kodierung gehören. GSM7 unterstützt diakritische Zeichen oder Akzente nicht in vollem Umfang. Besonders im Französischen, wo é und è zu GSM7 gehören, ê, â oder ï aber nicht. Dasselbe gilt für Spanisch.

* Das C mit Unterhäkchen (ç) ist im GSM7-Alphabet nur in Großbuchstaben vorhanden, einige Telefone geben es jedoch in Kleinbuchstaben oder intelligenter Gross-/Kleinschreibung wieder. Die allgemeine Empfehlung lautet, dies vollständig zu vermeiden und das Unterhäkchen zu entfernen oder auf UCS-2 umzusteigen.

* **Verwenden Sie kein ASCII in SMS**, es sei denn, dies wird vom SMSC-Provider ausdrücklich verlangt. Diese Kodierung verschwendet Speicherplatz, da sie 8-Bit-Zeichen und eine geringere Abdeckung als GSM7 aufweist. Diese Kodierung kann für CDMA-Netzwerke erforderlich sein, die in Nordamerika verwendet werden.

* Latein-1 wird nicht immer unterstützt. Überprüfen Sie die Kompatibilität mit Ihrem SMSC-Provider, bevor Sie versuchen, Latin-1 zu verwenden.

* Nationale Sprachverschiebungstabellen werden vom Adobe Campaign-Connector nicht unterstützt. Sie müssen stattdessen UCS-2 oder eine andere `data_coding` verwenden.

* UCS-2 und UTF-16 werden oft per Telefon gemischt. Dies ist ein Problem bei der Verwendung von Emojis und anderen Zeichen, die nicht in UCS-2 vorhanden sind.

* Die meisten Telefone haben nicht für alle UCS-2-Zeichen Schriftzeichen. Smartphones können seltene Zeichen in der Regel recht einfach anzeigen, aber Funktionstelefone haben in der Regel nur eine begrenzte Unterstützung für die Zeichen, die in der Muttersprache des Landes nützlich sind, in dem sie gekauft wurden. Wenn Sie Emoji- oder ASCII-Grafiken verwenden möchten, testen Sie sie vor dem Versand auf einer Vielzahl von Telefonen. Die Adobe Campaign-Vorschau simuliert keine fehlenden Glyphen und zeigt die im Webbrowser verfügbaren Symbole an.

Das Feld `data_coding` gibt an, welche Kodierung verwendet wird. Ein Hauptproblem besteht darin, dass der Wert 0 die standardmäßige SMSC-Kodierung in der Spezifikation bedeutet, die sich normalerweise auf GSM7 bezieht. Erkundigen Sie sich beim SMSC-Partner, welche Kodierung mit `data_coding` = 0 verknüpft ist, die nur von Adobe Campaign unterstützt wird. Andere `data_coding`-Werte folgen in der Regel der Spezifikation. Sie müssen dies aber vom SMSC-Provider bestätigen lassen.

Die maximale Größe einer Nachricht hängt von ihrer Kodierung ab. In dieser Tabelle sind alle relevanten Informationen zusammengefasst:

| Kodierung | Übliche Datenkodierung (data_coding) | Nachrichtengröße (Zeichen) | Größe der Teile für mehrteilige SMS | Verfügbare Zeichen |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | GSM7-Standardzeichensatz + Erweiterung (erweiterte Zeichen benötigen 2 Zeichen) |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (variiert von Telefon zu Telefon) |

## SMPP-Parameter für externe Konten {#SMPP-parameters-external}

Jede Implementierung des SMPP-Protokolls weist viele Variationen auf. Um die Kompatibilität und Anpassungsfähigkeit zu verbessern, stehen viele Einstellungen zur Verfügung, um das Verhalten des SMPP-Connectors zu ändern. In diesem Abschnitt werden alle Parameter und ihre Auswirkungen auf den Connector beschrieben.

### Allgemeine Parameter und Routing {#general-parameters-routing}

**MTA-Instanzen für dieses Konto beschränken**

Es ist möglich, die Anzahl der MTA-Instanzen festzulegen, die eine Verbindung zum SMPP-Provider herstellen dürfen. Wenn diese Option aktiviert ist, können Sie angeben, wie viele MTAs maximal verwendet werden können.

Diese Option ermöglicht eine genauere Kontrolle über die Anzahl der Verbindungen, siehe [Simultane Verbindungen](../../delivery/using/sms-protocol.md#connection-settings).

Wenn Sie einen höheren Wert als die Anzahl der ausgeführten MTAs festlegen, werden alle MTAs wie gewohnt ausgeführt: Diese Option ist nur eine Begrenzung und kann keine zusätzlichen MTAs erzeugen.

Wenn Sie die Anzahl der Verbindungen genau steuern müssen, z. B. aufgrund von Provider-Anforderungen, empfiehlt es sich, diese Option immer zu setzen, auch wenn in der aktuellen Bereitstellung die richtige Anzahl von MTAs ausgeführt wird. Wenn anschließend weitere MTAs hinzugefügt werden, wird die Verbindungsgrenze weiterhin eingehalten.

### Verbindungsparameter {#connection-settings}

#### Name der SMSC-Implementierung {#smsc-implementation-name}

Legt den Namen der SMSC-Implementierung fest. Sollte auf den Namen Ihres Providers eingestellt werden. Wenden Sie sich an den Administrator oder das Zustellbarkeitsteam, um zu erfahren, was in diesem Feld hinzugefügt werden muss. Die Rolle dieses Felds wird im Abschnitt [Umgang mit SR-Fehlern](../../delivery/using/sms-protocol.md#sr-error-management) beschrieben.

#### Server {#server}

Der DNS-Name oder die IP-Adresse des Servers, mit dem eine Verbindung hergestellt werden soll.

#### Port {#port}

Der TCP-Port, zu dem eine Verbindung hergestellt werden soll.

#### Konto {#account}

Die Anmeldedaten der Verbindung. Im Feld `system_id` der BIND PDU übergeben.

#### Passwort {#password}

Passwort der SMPP-Verbindung. Im Passwortfeld der BIND PDU übergeben.

#### Systemtyp {#system-type}

Wert, der im Feld `system_id` der BIND PDU übergeben wird. Einige Provider benötigen hier einen bestimmten Wert.

#### Anzahl untergeordneter MTA-Verbindungen {#number-mta-child}

In Adobe Campaign Classic gibt diese die Anzahl der Verbindungen pro untergeordnetem MTA-Element an.

Die Anzahl der Verbindungen pro untergeordnetem MTA-Element ist über den SMPP-Connector von Adobe Campaign Classic regulierbar. Die allgemeine Höchstzahl von Verbindungen lässt sich durch Begrenzen der Anzahl untergeordneter MTA-Prozesse regulieren, wofür häufig eine dedizierte Mid-Sourcing-Plattform für SMS erforderlich ist.

In Adobe Campaign Classic kann die Zahl der Receiver-Verbindungen von der Zahl der Transmitter-Verbindungen abweichen:

* **Transmitter-Verbindungen = Anzahl untergeordneter MTA-Verbindungen x Anzahl untergeordneter MTA-Prozesse x Anzahl der MTAs (wenn automatische Antwort eingestellt ist) + Anzahl untergeordneter MTA-Verbindungen**

Wie oben dargelegt, öffnet der SMS-Prozess von Adobe Campaign Classic mehr Transmitter-Verbindungen, wenn die automatische Antwort aktiviert ist. Diese zusätzlichen Verbindungen dienen zum Senden der automatischen Antworten.

* **Receiver-Verbindungen = Anzahl untergeordneter MTA-Verbindungen**

Wenn automatische Antworten eingerichtet sind, öffnet der SMS-Prozess Transmitter-Receiver-Paare, wodurch sich die Anzahl der Transmitter-Verbindungen erhöht. Wenn keine automatischen Antworten eingerichtet sind, werden nur die Receiver-Verbindungen geöffnet.

#### TLS über SMPP aktivieren {#enable-TLS}

Verwenden Sie TLS, um eine Verbindung zum Provider herzustellen. Die Verbindung wird verschlüsselt. Die TLS-Verbindung wird von der OpenSSL-Bibliothek verwaltet. Alles, was für OpenSSL gilt, gilt auch für diese Verbindung.

#### Ausführliche SMPP-Verfolgung in Logdatei aktivieren {#enable-verbose-log-file}

Mit dieser Einstellung wird der gesamte SMPP-Traffic in Logdateien abgelegt. Parameter müssen häufig während der ersten Einrichtung angepasst werden. Dies muss aktiviert werden, um Fehler beim Connector zu beheben und mit dem Traffic auf der Provider-Seite zu vergleichen.

In Adobe Campaign Classic wird MT-bezogener Traffic im MTA-Log und MO- und SR-bezogener Traffic im SMS-Log protokolliert.

### Verbindungsparameter des Receivers {#receiver-connection}

Dieser Abschnitt ist nur im getrennten Modus **Transmitter + Receiver** sichtbar.

#### Andere Parameter für den Receiver verwenden {#receiver-parameters}

Wenn das Kontrollkästchen deaktiviert ist, werden für Sender und Empfänger dieselben Einstellungen verwendet.

Wenn das Kontrollkästchen aktiviert ist, gelten die Einstellungen im Abschnitt **Verbindungsparameter** für den Sender und die **Verbindungsparameter des Receivers** gelten für den Empfänger.

**Receiver-Server, Port, Konto, Passwort, Systemtyp**

Diese Einstellungen gelten für den Empfänger im Modus Transmitter + Receiver. Sie funktionieren wie im Transmitter-Modus. Weitere Informationen finden Sie weiter oben.

### Parameter des SMPP-Kanals {#smpp-channel-settings}

#### Transliteration der Zeichen zulassen {#allow-character-transliteration}

Bei der Transliteration werden äquivalente Zeichen zu fehlenden Zeichen gefunden. Beispielsweise fehlt das französische Zeichen &quot;ê&quot; (e mit Zirkumflex-Akzent) in der GSM-Kodierung, es kann jedoch durch &quot;e&quot; ersetzt werden, ohne die Lesbarkeit zu beeinträchtigen.

Wenn dieses Kontrollkästchen deaktiviert ist, schlägt die Textkodierung fehl, wenn die Zeichenfolge nicht exakt kodiert werden kann.

Wenn dieses Kontrollkästchen aktiviert ist, versucht die Textkodierung, die Zeichenfolge in eine ungefähre Version zu konvertieren, anstatt fehlzuschlagen. Wenn einige Zeichen in der Zielkodierung keine Entsprechung haben, schlägt die Textkodierung fehl.

Eine allgemeinere Erläuterung des Kodierungsprozesses finden Sie unter dem Parameter [Definieren eines bestimmten Kodierungs-Mapping](../../delivery/using/sms-protocol.md#SMSC-specifics).

#### Eingehende MO in Datenbank speichern {#incoming-mo-storing}

Bei Aktivierung wird der eingehende MO in der inSMS-Tabelle der Datenbank gespeichert. Diese Tabelle kann mithilfe der Abfrageaktivität eines beliebigen Workflows abgefragt werden.

In Adobe Campaign Classic werden die MOs allesamt in der inSMS-Datenbank gespeichert, daher ist diese Option nicht verfügbar.

#### Echtzeit-KPI-Aktualisierungen während SR-Verarbeitung aktivieren {#real-time-kpi}

Wenn diese Option aktiviert ist, werden die KPIs in Echtzeit auf der Hauptseite für den Versand aktualisiert, wenn ein Fehler-SR empfangen wird.

Der Nachteil kann eine niedrige Leistung aufgrund der dadurch erzeugten Datenbankinhalte sein. Wenn diese Option deaktiviert ist, werden Statistiken vom **syncfromexec**-Workflow aktualisiert, der alle 20 Minuten ausgeführt wird.

Der KPI-Mechanismus von Adobe Campaign Classic unterscheidet sich davon grundlegend, daher ist diese Option nicht verfügbar.

#### Anrufernummer {#source-number}

Definiert die Standardquelladresse für Nachrichten. Diese Einstellung gilt nur, wenn die Anrufernummer im Versand leer gelassen wurde.

Standardmäßig wird das Feld für die Anrufernummer nicht übergeben, sodass der Provider es durch die Kurzwahlnummer ersetzt.

Damit wird die Funktion zum Überschreiben der Absenderadresse/oADC aktiviert.

#### Kurzwahlnummer {#short-code}

Gibt die Hauptkurzwahlnummer des Kontos an. Wenn für dieses Konto mehrere Kurzwahlnummern verwendet werden oder wenn die Kurzwahlnummer unbekannt ist, lassen Sie dieses Feld leer.

Die Angabe von Kurzwahlnummern ist für zwei Funktionen hilfreich:

* Die Vorschau zeigt die Kurzwahlnummer an, wenn keine Anrufernummer angegeben wurde. Es wird das tatsächliche Verhalten auf dem Mobiltelefon widergespiegelt.

* Die Blockierungslisten-Einstellung der automatischen Antwortfunktion stellt Benutzer nur für die jeweilige Kurzwahlnummer unter Quarantäne.

#### Anrufer-TON/NPI, Empfänger-TON/NPI {#ton-npi}

TON (Type of Number = Nummerntyp) und NPI (Numbering Plan Indicator = Nummerierungsplanindikator) werden in Abschnitt 5.2.5 der [Spezifikation von SMPP Version 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (Seite 117) beschrieben. Diese Werte sollten entsprechend den Anforderungen des Providers eingestellt werden.

Sie werden unverändert in den Feldern `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` und `dest_addr_npi` der `SUBMIT_SM PDU` übertragen.

#### Diensttyp {#service-type}

Dieses Feld wird unverändert im Feld `service_type` der `SUBMIT_SM PDU` übertragen. Stellen Sie den Wert entsprechend den Anforderungen des Providers ein.

### Durchsatz und Zeitüberschreitung {#throughput-timeouts}

Diese Einstellungen steuern alle Zeitaspekte des SMPP-Kanals. Einige Provider erfordern eine sehr genaue Steuerung der Nachrichtenrate sowie der Fenster- und Wiederholungszeiten. Diese Einstellungen sollten auf Werte gesetzt werden, die der Kapazität des Providers und den in seinem Vertrag angegebenen Bedingungen entsprechen.

#### Übertragungsfenster {#sending-window}

Das Fenster entspricht der Anzahl der `SUBMIT_SM PDU`s, die gesendet werden können, ohne auf eine passende `SUBMIT_SM_RESP` zu warten.

Beispiel einer Übertragung mit einem maximalen Fenster von 4:

![](assets/do-not-localize/sms_protocol_2.png)

Das Fenster hilft, den Durchsatz zu erhöhen, wenn die Netzwerkverbindung eine hohe Latenz aufweist.  Der Wert des Fensters muss mindestens der Anzahl der SMS entsprechen, multipliziert mit der Latenz der Verbindung in Sekunden, damit der Connector nie auf ein `SUBMIT_SM_RESP` wartet, bevor die nächste Nachricht gesendet wird.
Wenn das Fenster zu groß ist, kann es passieren, dass Sie bei Verbindungsproblemen mehr doppelte Nachrichten senden. Außerdem haben die meisten Provider ein sehr strenges Limit für das Fenster und lehnen Nachrichten ab, die das Limit überschreiten.

Berechnung der optimalen Formel für das Übertragungsfenster:

* Messen Sie die maximale Latenz zwischen `SUBMIT_SM` und `SUBMIT_SM_RESP`.

* Multiplizieren Sie diesen in Sekunden angegebenen Wert mit dem maximalen MT-Durchsatz. Daraus ergibt sich der Wert für das optimale Übertragungsfenster.

Beispiel: Wenn Sie für den maximalen Durchsatz an MT 300 SMS/s eingestellt haben und die Latenz zwischen `SUBMIT_SM` und `SUBMIT_SM_RESP` im Durchschnitt 100 ms beträgt, wäre der optimale Wert `300×0.1 = 30`.

#### Maximaler Durchsatz an MT {#max-mt-throughput}

Maximale Anzahl an MT pro Sekunde und pro Verbindung. Diese Einstellung wird genau eingehalten. Der MTA wird beim Nachrichtenversand diese Grenze nie überschreiten. Diese Einstellung ist nützlich für Provider, die eine genaue Drosselung benötigen.

Um die Gesamtdurchsatzgrenze zu ermitteln, multiplizieren Sie diese Gesamtanzahl von Verbindungen, wie in der obigen Formel angegeben.

0 bedeutet keine Begrenzung, der MTA sendet MT so schnell wie möglich.

Im Allgemeinen wird empfohlen, diese Einstellung unter 1.000 zu halten, da es unmöglich ist, einen genauen Durchsatz oberhalb dieser Zahl zu garantieren, es sei denn, es wurde mit der endgültigen Architektur ordnungsgemäß ein Benchmark durchgeführt. Wenn Sie einen Durchsatz von über 1.000 benötigen, kontaktieren Sie bitte Ihren Provider. Möglicherweise ist es besser, die Anzahl der Verbindungen auf über 1.000 MT/s zu erhöhen.

#### Dauer bis zu einer erneuten Verbindung {#time-reconnection}

Wenn die TCP-Verbindung verloren geht, wartet der Connector diese Anzahl von Sekunden, bevor er versucht, eine Verbindung herzustellen.

#### Gültigkeitsdauer der MT {#expiration-period}

Zeitüberschreitung zwischen `SUBMIT_SM` und der zugehörigen `SUBMIT_SM_RESP`. Wenn die `RESP` nicht rechtzeitig empfangen wird, gilt die Nachricht als fehlgeschlagen und die globale Wiederholungsrichtlinie des MTA wird angewendet.

#### Bind-Timeout {#bind-timeout}

Zeitüberschreitung zwischen dem TCP-Verbindungsversuch und der `BIND_*_RESP`-Antwort. Nach Ablauf des Zeitlimits wird die Verbindung durch den Adobe Campaign-Connector geschlossen. Erst nach Ablauf der Dauer bis zu einer erneuten Verbindung wird versucht, die Verbindung wiederherzustellen.

#### enquire_link-Zeitraum {#enquire-link-period}

`enquire_link` ist eine spezielle Art von PDU, die gesendet wird, um die Verbindung aktiv zu halten. Dieser Zeitraum wird in Sekunden angegeben. Der Connector sendet nur `enquire_link`, wenn die Verbindung inaktiv ist, um Bandbreite zu sparen. Wenn nach der doppelten Zeitdauer keine RESP empfangen wird, wird die Verbindung als unterbrochen betrachtet und ein Wiederverbindungsprozess ausgelöst.

### SMSC-Besonderheiten {#SMSC-specifics}

Bei diesen Einstellungen handelt es sich um erweiterte Einstellungen, mit denen der Adobe Campaign-Connector an die meisten SMPP-Implementierungseigenschaften angepasst wird.

**Definieren eines bestimmten Kodierungs-Mappings**

Einzelheiten zur Textkodierung finden Sie im Abschnitt [SMS-Textkodierung](../../delivery/using/sms-protocol.md#sms-text-encoding).

Mit dieser Einstellung können Sie ein benutzerdefiniertes Kodierungs-Mapping definieren, das von der Spezifikation abweicht. Sie können eine Liste von Kodierungen zusammen mit ihrem `data_coding`-Wert deklarieren.

Der MTA versucht, die Kodierung mit der ersten Kodierung in der Liste durchzuführen. Schlägt dies fehl, wird versucht, die nächste Kodierung in der Liste zu verwenden, usw. Wenn keine Kodierung zum Verschlüsseln der Nachricht verwendet werden kann, tritt ein Fehler auf. Sobald die Kodierung gefunden wurde, erstellt der MTA die `SUBMIT_SM PDU` mit dem kodierten Text und dem `data_coding`-Feld mit dem in der Tabelle angegebenen Wert.

Die Reihenfolge der Elemente in der Tabelle ist wichtig: Kodierungen werden von oben nach unten ausprobiert. Sie sollten die günstigste oder am meisten empfohlene Kodierung ganz oben auf die Liste setzen, gefolgt von immer teureren Kodierungen.

Bitte beachten Sie, dass UCS-2 niemals fehlschlagen wird, da es alle in Adobe Campaign unterstützten Zeichen kodieren kann und die maximale Länge einer UCS-2-SMS viel kleiner ist: nur 70 Zeichen.

Sie können diese Einstellung auch verwenden, um zu erzwingen, dass eine bestimmte Kodierung immer verwendet wird, indem Sie in der Mapping-Tabelle nur eine Zeile deklarieren.

Das standardmäßige Mapping, das verwendet wird, wenn das Kontrollkästchen nicht aktiviert ist, entspricht der folgenden Tabelle:

| data_coding | Kodierung |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

Dies bedeutet, dass der MTA versucht, die Nachricht in GSM zu kodieren. Wenn dies gelingt, wird die Nachricht mit `data_coding` = 0 gesendet.

Wenn die Nachricht nicht in GSM kodiert werden kann, wird sie in UCS-2 kodiert und `data_coding` auf 8 gesetzt.

#### message_payload aktivieren {#enable-message-payload}

Wenn diese Option deaktiviert ist, werden lange SMS vom MTA aufgeteilt und in mehreren `SUBMIT_SM PDU`s mit UDH gesendet. Die Nachricht wird vom Mobiltelefon entsprechend den UDH-Daten neu zusammengesetzt.

Wenn diese Option aktiviert ist, werden lange SMS in einer einzigen SUBMIT_SM PDU gesendet, wobei der Text in das optionale Feld message_payload eingefügt wird. Weitere Informationen dazu finden Sie in der [SMPP-Spezifikation](../../delivery/using/sms-protocol.md#ACS-SMPP-connector).

Wenn diese Funktion aktiviert ist, kann Adobe Campaign die SMS-Teile nicht einzeln zählen: alle Nachrichten werden als in einem Teil gesendet gezählt.

#### Vollständige Telefonnummer senden {#send-full-phone-number}

Wenn dieses Kontrollkästchen nicht aktiviert ist, werden nur Ziffern der Telefonnummer an den Provider gesendet (`destination_addr`-Feld des `SUBMIT_SM`-Felds). Dies ist das Standardverhalten, da das internationale Rufnummernkennzeichen, normalerweise ein &quot;+&quot;-Präfix, in SMPP durch TON- und NPI-Felder ersetzt wird.

Wenn das Kontrollkästchen aktiviert ist, wird die Telefonnummer unverändert gesendet, also ohne Vorverarbeitung und potenzielle Leerzeichen, &quot;+&quot;-Präfix oder Pfund-/Hash-/Sternzeichen.

Diese Funktion wirkt sich auch auf das Verhalten der Blockierungslistenfunktion für automatische Antworten aus: Wenn das Kontrollkästchen nicht aktiviert ist, wird den in die Quarantänetabelle eingefügten Telefonnummern ein &quot;+&quot;-Präfix hinzugefügt, um das &quot;+&quot;-Präfix zu kompensieren, das vom SMPP-Protokoll selbst aus der Telefonnummer entfernt wird.

#### TLS-Zertifikatsprüfung überspringen {#skip-tls}

Wenn TLS aktiviert ist, werden alle Zertifikatsprüfungen übersprungen.

Wenn diese Option aktiviert ist, ist die Verbindung nicht mehr sicher. Sie sollte nicht in der Produktion aktiviert werden.

Dies kann für Debugging- oder Testzwecke nützlich sein.

#### Bind TON/NPI {#bind-ton-npi}

TON (Type of Number = Nummerntyp) und NPI (Numbering Plan Indicator = Nummerierungsplanindikator) werden in Abschnitt 5.2.5 der [Spezifikation von SMPP Version 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (Seite 117) beschrieben. Diese Werte sollten entsprechend den Anforderungen des Providers eingestellt werden.

Sie werden unverändert in den Feldern `addr_ton` und `addr_npi` der BIND PDU übertragen.

#### Adressenbereich {#address-range}

Wird im Feld address_range der BIND PDU unverändert gesendet. Dieser Wert sollte entsprechend den Anforderungen des Providers eingestellt werden.

#### Anzahl ungültiger ID-Quittierungen {#invalid-id}

Begrenzt die Anzahl der **ungültigen Nachrichten-IDs** `DELIVER_SM_RESP`, die für einen einzelnen SR gesendet werden können.

**Dies sollte nur zur Fehlerbehebung als Problemumgehung verwendet** und unter normalen Bedingungen auf 0 gesetzt werden.

Beispiel: die Einstellung lautet 2:

* Der Provider sendet einen SR (`DELIVER_SM`) mit der ID &quot;1234&quot;.

* Die ID &quot;1234&quot; konnte nicht in der Datenbank gefunden werden.

* Der Connector zählt für diese ID einen Fehler vom Typ **Ungültige ID**, daher wird `DELIVER_SM_RESP` mit dem Fehler-Code &quot;Nachrichten-ID ungültig&quot; (normales Verhalten) gesendet.

* Der Provider versucht denselben SR mit der ID &quot;1234&quot; erneut.

* Die ID &quot;1234&quot; konnte immer noch nicht in der Datenbank gefunden werden.

* Der Connector zählt für diese ID zwei Fehler vom Typ **Ungültige ID**. Daher wird `DELIVER_SM_RESP` &quot;OK&quot; gesendet, auch wenn sie nicht korrekt verarbeitet wurde.

* Diese Funktion dient zum Leeren von SR-Puffern auf der Provider-Seite, wenn aufgrund eines ungültigen SR-Blocks Nachrichten nicht verarbeitet werden können.

Wenn dieses Feld auf 0 gesetzt wird, wird der Mechanismus deaktiviert, bei dem **Nachrichten-ID ungültig** immer zurückgegeben wird. Dies ist das normale Verhalten.

Wenn Sie dieses Feld auf 1 setzen, antwortet der Connector immer mit &quot;OK&quot;, auch wenn die ID ungültig ist. Es sollte nur unter Aufsicht, zur Fehlerbehebung und für eine minimale Zeitdauer, z. B. zur Behebung eines Problems auf Provider-Seite, auf 1 gesetzt werden.

#### Regex zur ID-Extraktion im SR {#regex-extraction}

Das SR-Format wird von der SMPP-Protokollspezifikation nicht strikt durchgesetzt. Es handelt sich lediglich um eine Empfehlung, die in [Anhang B](../../delivery/using/sms-protocol.md#sr-error-management) (Seite 167) der Spezifikation beschrieben ist. Einige SMPP-Implementierer formatieren dieses Feld unterschiedlich, sodass Adobe Campaign eine Möglichkeit benötigt, das richtige Feld zu extrahieren.

Standardmäßig werden bis zu 10 alphanumerische Zeichen nach `id:` erfasst.

Der Regex muss über genau eine Erfassungsgruppe mit einem Teil in Klammern verfügen. Der ID-Teil muss in Klammern eingeschlossen sein. Das Regex-Format ist PCRE.

Achten Sie beim Anpassen dieser Einstellung darauf, so viel Kontext wie möglich einzubeziehen, um Fehlauslösungen zu vermeiden. Wenn bestimmte Präfixe vorhanden sind, z. B. `id:` im standardisierten Präfix, müssen Sie sie in den Regex aufnehmen. Verwenden Sie außerdem so weit wie möglich Worttrennzeichen (\b), um zu vermeiden, dass Text in der Mitte eines Wortes erfasst wird.

Wenn nicht genügend Kontext in den Regex aufgenommen wird, kann dies zu einer kleinen Sicherheitslücke führen: Der tatsächliche Inhalt der Nachricht kann in den SR aufgenommen werden. Wenn Sie nur ein bestimmtes ID-Format ohne Kontext verwenden, z. B. eine UUID, wird möglicherweise der eigentliche Textinhalt analysiert, z. B. eine UUID, die in das Textfeld eingebettet ist, anstatt der ID.

#### Regex angewendet, um den Erfolgs-/Fehlerstatus zu ermitteln {#regex-applied}

Wenn Meldungen mit einer unbekannten stat/err-Feldkombination auftreten, werden diese Regex auf das stat-Feld angewendet, um zu bestimmen, ob der SR erfolgreich oder fehlerhaft war. SR mit stat-Werten, die mit keinem Regex übereinstimmen, werden ignoriert.

Standardmäßig werden stat-Werte, die mit `DELIV` beginnen, z. B. `DELIVRD` in [Anhang B](../../delivery/using/sms-protocol.md#sr-error-management), als erfolgreich betrachtet und stat-Werte, die Fehler aufweisen, z. B. `REJECTED`, `UNDELIV`, werden als Fehler betrachtet.

#### ID-Format in der MT-Quittierung (resp){#id-format-mt}

Dies zeigt das Format der ID an, die im Feld `message_id` der `SUBMIT_SM_RESP PDU` zurückgegeben wird.

* **Nicht ändern**: Die ID wird unverändert als ASCII-kodierter Text wie in der Datenbank gespeichert. Es findet keine Vorverarbeitung oder Filterung statt.

* **Dezimalzahl**: Die ID wird als Dezimalzahl in ASCII-Form erwartet. Führende und nachfolgende Leerzeichen und führende Nullen werden bei dieser Einstellung entfernt.

* **Hexadezimalzahl**: Die ID wird als Hexadezimalzahl in ASCII-Form erwartet, ohne führendes 0x und nachgestelltes h. Die ID wird dann in eine Dezimalzahl umgewandelt, bevor sie in der Datenbank gespeichert wird.

* **Hexadezimaler String**: Die ID muss ein ASCII-kodierter Text sein, der selbst eine Zeichenfolge ist, die als Hexadezimalwert kodiert wurde. In der PDU finden Sie beispielsweise `0x34 0x31 0x34 0x32 0x34 0x33`, was in ASCII &quot;414243&quot; bedeutet. Diese Zeichenfolge wird dann als hexadezimaler String von Bytes dekodiert und Sie erhalten &quot;ABC&quot;: Die ID &quot;ABC&quot; wird in der Datenbank gespeichert.

#### ID-Format im SR {#id-format-sr}

Dies gibt das Format der ID an, die vom `Extraction`-Regex der ID im SR erfasst wird. Die Werte haben die gleiche Bedeutung und das gleiche Verhalten wie das Format im MT oben.

**SR-Kennung oder Fehler-Code in einem optionalen Feld speichern**

>[!NOTE]
>
>Nur im erweiterten SMPP-Connector von Adobe Campaign Classic verfügbar.

Wenn diese Option aktiviert ist, wird der Inhalt der optionalen Felder an den Text angehängt, der durch die oben genannten Regex verarbeitet wird. Der Text hat das Format `0xTAG:VALUE`, wobei `0xTAG` der 4-stellige Hexadezimalwert des Tags in Großbuchstaben ist, z. B. `0x002E`.

Sie können beispielsweise die ID im Feld `receipted_message_id` erfassen. Aktivieren Sie dazu dieses Kontrollkästchen, und dem Status wird folgender Text hinzugefügt:

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

In diesem Beispiel ist 0x001E das Tag des optionalen Felds und die UUID der Wert des Felds.

Um diesen Wert zu erfassen, können Sie jetzt den folgenden Regex im Feld &quot;Regex zur ID-Extraktion im SR&quot; festlegen:

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>Sie können nur optionale Felder mit Textwerten (ASCII/UTF-8) erfassen. Insbesondere können Binärfelder mit dem aktuellen Regex-System nicht zuverlässig erfasst werden.

**SR-Kennung oder Fehler-Code in einem Textfeld speichern**

Wenn diese Option aktiviert ist, wird das Feld **Text** während der Verarbeitung des Statustextes des SR beibehalten.

Dies ist nützlich, wenn der Provider wichtige Daten wie die ID oder den Status in dieses Feld eingibt. Normalerweise kann dieses Feld sicher verworfen werden, da es Text mit einer Nicht-ASCII-Kodierung enthalten und die Regex-Verarbeitung stören kann.

Das Aktivieren dieser Option kann zu einer sehr kleinen Sicherheitslücke führen, wenn der `Extraction`-Regex der ID im SR-Feld nicht spezifisch genug ist. Der Inhalt des Felds **Text** kann als ID geparst werden, und ein Angreifer kann es verwenden, um gefälschte IDs einzuschleusen, was zu einer teilweisen Dienstverweigerung führen kann.

**Dienst-ID-Tag**

Ermöglicht das Hinzufügen eines benutzerdefinierten TLV. Dieses Feld legt den Tag-Teil fest. Der Wert kann pro Versand im Wert **Dienst- oder Programm-ID** in den erweiterten Parametern des Versands angepasst werden.

Diese Einstellung erlaubt nur das Hinzufügen einer TLV-Option pro Nachricht.

### Automatische Antwort auf MO        {#automatic-reply}

>[!IMPORTANT]
>
>In Adobe Campaign Classic sowie in Hybrid-Architekturen benötigt der Mid-Operator Schreibrechte für den Ordner **Externes Konto**, wenn für den SMPP-Connector automatische Antworten eingerichtet werden sollen.

Mit dieser Funktion können Sie schnell einen Antworttext an ein MO senden und das Senden pro Kurzwahlnummer an die Blockierungsliste handhaben.

Die Spalten **Schlüsselwort** und **Kurzwahlnummer** definieren Bedingungen, um die automatische Antwort auszulösen. Wenn beide Felder übereinstimmen, wird der MO gesendet und die zusätzliche Aktion ausgelöst. Um einen Platzhalter festzulegen, sollten Sie das Feld leer lassen. Das Schlüsselwort wird mit dem ersten alphanumerischen Wort im MO-Text abgeglichen, wobei Interpunktion und führende Leerzeichen ignoriert werden. Das bedeutet, dass das Feld **Schlüsselwort** keine Leerzeichen enthalten darf und ein einzelnes Wort sein muss.

Die Einstellung **Schlüsselwort** ist ein Präfix. Wenn Sie beispielsweise &quot;AD&quot; angeben, entspricht dies &quot;AD&quot;, &quot;ADAPT&quot; und &quot;ADOBE&quot;. Wenn Sie mehrere Schlüsselwörter mit einem gemeinsamen Präfix haben, müssen Sie auf die Reihenfolge achten, da Schlüsselwörter von oben nach unten verarbeitet werden.

Die Spalte **Antwort** enthält den Antworttext. In diesem Bereich ist keine Personalisierung möglich. Wenn Sie dieses Feld leer lassen, wird keine Nachricht als Antwort gesendet, aber die zusätzliche Aktion wird trotzdem ausgelöst.

Die Spalte **Zusätzliche Aktion** enthält eine zusätzliche Aktion, wenn sowohl **Schlüsselwort** als auch **Kurzwahlnummer** übereinstimmen. Eine leere Kurzwahlnummer stimmt mit allen Kurzwahlnummern überein. Sie können unter Quarantäne stellen oder aus der Quarantäne holen. Mit dem Wert &quot;Keine&quot; wird auf den Text geantwortet. Wenn Sie eine **Zusätzliche Aktion** angeben, aber das Feld **Antwort** leer lassen, wird die Aktion ausgeführt, aber es wird keine Antwort gesendet. Quarantäne wird nur für die angegebene Kurzwahlnummer oder alle Kurzwahlnummern angewendet, wenn das Feld leer gelassen wird.

>[!IMPORTANT]
>
>Die Einstellung &quot;Vollständige Telefonnummer senden&quot; wirkt sich auf das Verhalten des Quarantänemechanismus für automatische Antworten aus: Wenn &quot;Vollständige Telefonnummer senden&quot; nicht aktiviert ist, wird der unter Quarantäne gestellten Telefonnummer ein Pluszeichen (&quot;+&quot;) vorangestellt, damit sie mit dem internationalen Telefonnummernformat kompatibel ist.

Alle Einträge in der Tabelle werden in der angegebenen Reihenfolge verarbeitet, bis eine Regel übereinstimmt. Wenn mehrere Regeln mit einem MO übereinstimmen, wird nur die oberste Regel angewendet.

## SMS-Versandvorlagenparameter {#sms-delivery-template-parameters}

Einige Parameter können pro Versandvorlage festlegt werden.

### Feld &quot;Von&quot;{#from-field}

Dieses Feld ist optional. Es ermöglicht das Überschreiben der Absenderadresse (oADC). Der Inhalt dieses Felds wird im Feld `source_addr` der `SUBMIT_SM PDU` eingefügt.

Das Feld ist durch die SMPP-Spezifikation auf 21 Zeichen begrenzt, einige Provider können jedoch längere Werte zulassen. Beachten Sie auch, dass in einigen Ländern sehr strenge Einschränkungen gelten können, z. B. für Länge, Inhalt, zulässige Zeichen.

### Versandparameter {#delivery-parameters}

#### Maximale Anzahl an SMS pro Nachricht {#maximum-sms}

Diese Einstellung funktioniert nur, wenn die Einstellung **Nachrichten-Payload** deaktiviert ist. Wenn die Nachricht mehr SMS als diesen Wert erfordert, wird ein Fehler ausgelöst.

Das SMS-Protokoll begrenzt SMS auf 255 Teile. Allerdings haben einige Mobiltelefone Probleme, lange Nachrichten mit mehr als zehn Teilen zusammenzustellen. Die Begrenzung hängt vom genauen Modell ab. Wir empfehlen Ihnen, nicht mehr als fünf Teile pro Nachricht zu verwenden.

Aufgrund der Funktionsweise personalisierter Nachrichten in Adobe Campaign kann die Größe der Nachrichten variieren. Eine große Anzahl langer Nachrichten könnte die Versandkosten erhöhen.

#### Übermittlungsmodus {#transmission-mode}

Dieses Feld gibt die Art der SMS an, die Sie übertragen möchten: Normale oder Flash-Nachrichten, die auf dem Mobilgerät oder der SIM-Karte gespeichert werden.

Diese Einstellung wird im optionalen Feld `dest_addr_subunit` in der `SUBMIT_SM PDU` übertragen.

* **Keine Angabe** sendet kein optionales Feld in der PDU.

* **Flash** setzt den Wert auf 1. Es wird eine Flash-Nachricht gesendet, die auf dem Mobiltelefon angezeigt und nicht im Speicher abgelegt wird.

* **Normal** setzt den Wert auf 0. Es wird eine normale Nachricht gesendet.

* **Auf Mobilgerät speichern** setzt den Wert auf 2. Das Telefon wird angewiesen, die SMS im internen Speicher abzulegen.

* **Auf Gerät speichern** setzt den Wert auf 3. Das Telefon wird angewiesen, die SMS auf der SIM-Karte zu speichern.

#### Gültigkeitszeitraum {#validity-period}

Der Gültigkeitszeitraum wird im Feld `validity_period` der `SUBMIT_SM PDU` übertragen. Das Datum wird immer im absoluten UTC-Zeitformat formatiert, das Datumsfeld endet mit &quot;00+&quot;.

## Erweiterter allgemeiner SMPP-Connector {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

Die Pfeile stellen Datenflüsse dar.

Beim Senden von Versandkontingenten erzeugt der MTA untergeordnete MTA-Elemente. Die Anzahl dieser untergeordneten MTA-Prozesse ist dynamisch und von der Konfiguration in serverConf.xml abhängig. Jedes untergeordnete MTA-Element instanziiert den Connector `CSmppConnectorWorker`, der eine Verbindung zum SMPP-Provider herstellt. Verbindungen werden so lange aufrechterhalten wie das untergeordnete MTA-Element existiert. Dies ist ebenfalls in serverConf.xml konfigurierbar.

Der SMS-Prozess verarbeitet nur SR; er verbindet sich mit dem Provider und lässt die Verbindung offen. Der Prozess verbindet sich zudem alle zehn Minuten erneut, um neue Einstellungen zu laden. Dies ist ein ordnungsgemäßer Vorgang.

### Abgleichen von MT-, SR- und broadLog-Einträgen {#matching-mt}

Die MT- und SR-Daten werden in einer als Zwischenspeicher fungierenden `nmsProviderMsgId`-Tabelle temporär abgelegt, bevor sie asynchron in das broadLog übertragen werden.

Die Tabelle `nmsProviderMsgId` ist in drei Spalten gruppiert:

* Spalten, die aktualisiert werden, wenn ein MT gesendet und quittiert wird: `iBroadLogId`, `iDeliveryId`

* Spalten, die aktualisiert werden, wenn ein SR empfangen wird: `iMsgId`, `iStatus`

* Spalten, die immer aktualisiert werden: `tsCreated`, `sProviderId`

Nach abgeschlossener Verarbeitung von MT und SR sollten die Zeilen vollständig ausgefüllt sein, also sowohl mit broadLog- als auch mit Statusinformationen.

`iMsgId` ist darin der Tabelle `nmsBroadLogMsg` zugeordnet, die die vollständige Status-/Fehlermeldung angibt.

Der SMS-Prozess sucht minütlich nach vollständigen Zeilen und verarbeitet diese dann asynchron:

* Die vollständige Zeile wird gelesen.
* Der SMS-Prozess berechnet den Namen der broadLog-Tabelle auf Basis des Versand-Mappings.
* Der SMS-Prozess aktualisiert die broadLog-Tabelle mit der Nachrichtenkennung und dem Status.

**Durchsatz und parallele Verbindungen**

Jedes untergeordnete MTA-Element erstellt eine konfigurierbare Anzahl von Verbindungen. Mit einer Begrenzung der Zahl der untergeordneten MTA-Elemente wird somit auch die Zahl der Verbindungen begrenzt. Da untergeordnete MTA-Prozesse und Traffic miteinander korrelieren, lässt sich dies zu einem gewissen Grad regulieren. Eine gewisse Unvorhersehbarkeit verbleibt aber dennoch.

## Vor der Live-Schaltung {#checklist}

Diese Checkliste enthält eine Liste der Dinge, die Sie vor der Live-Schaltung überprüfen sollten. Eine unvollständige Einrichtung kann zu vielen Problemen führen.

### Prüfen auf Konflikte mit externen Konten {#external-account-conflict}

Vergewissern Sie sich, dass Sie keine alten externen SMS-Konten haben. Wenn Sie das Testkonto deaktiviert lassen, besteht das Risiko, dass es auf dem Produktionssystem wieder aktiviert wird und potenzielle Konflikte entstehen.

Wenn Sie mehrere Konten in derselben Adobe Campaign-Instanz haben, die eine Verbindung zu demselben Provider herstellen, wenden Sie sich an den Provider, um sicherzustellen, dass tatsächlich zwischen den Verbindungen dieser Konten unterschieden wird. Für mehrere Konten mit denselben Anmeldedaten ist eine zusätzliche Konfiguration erforderlich.

### Aktivieren der ausführlichen SMPP-Verfolgung während der Prüfungen {#enable-verbose}

Sie sollten während der Prüfungen immer die ausführliche SMPP-Verfolgung aktivieren.
Auch wenn Sie die Protokolle nicht selbst überprüfen können, ist es für [Adobe Kundendienst](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) einfacher, Ihnen zu helfen.

### Testen Ihrer SMS {#test}

* **SMS mit allen möglichen Zeichen senden**
Wenn Sie SMS mit Nicht-GSM- oder Nicht-ASCII-Zeichen senden müssen, versuchen Sie, einige Nachrichten mit möglichst vielen verschiedenen Zeichen zu senden. Wenn Sie eine benutzerdefinierte Zeichen-Mapping-Tabelle einrichten, senden Sie mindestens eine SMS für alle möglichen 
`data_coding`-Werte.

* **Überprüfen, ob SR ordnungsgemäß verarbeitet wurden**
Die SMS sollte im Versandlog als empfangen markiert sein. Das Versandlog sollte erfolgreich sein und wie folgt aussehen:

Vergewissern Sie sich, dass Sie den Namen des Versand-Providers geändert haben. Das Versandlog sollte niemals Folgendes enthalten:    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Vergewissern Sie sich, dass Sie den Namen des Versand-Providers geändert haben. Das Versandlog sollte in Produktionsumgebungen niemals **SR Generic** enthalten.

* **Überprüfen, ob MO verarbeitet werden**
Wenn Sie MO verarbeiten müssen (automatische Antworten, MO-Speicherung in der Datenbank usw.), versuchen Sie, einige Tests durchzuführen. Senden Sie ein paar SMS für alle automatischen Antwortschlüsselwörter und prüfen Sie, ob die Antwort schnell genug ist, also nicht länger als ein paar Sekunden dauert.
Prüfen Sie im Log, ob Adobe Campaign mit einer erfolgreichen 
`DELIVER_SM_RESP` (command_status=0) antwortet

### Überprüfen der PDUs {#check-pdus}

Auch wenn die Nachrichten erfolgreich aussehen, ist es wichtig, zu prüfen, ob die PDUs richtig formatiert sind.

Dieser Schritt ist erforderlich, wenn eine Verbindung zu einem Provider hergestellt wird, der zuvor nicht mit Adobe Campaign verbunden war.

#### BIND {#bind}

Vergewissern Sie sich, dass die `BIND_* PDUs` korrekt gesendet wurden. Am wichtigsten ist es zu prüfen, dass der Provider immer erfolgreiche `BIND_*_RESP PDUs` zurückgibt (command_status = 0).

Vergewissern Sie sich, dass nicht zu viele `BIND_* PDU`s vorhanden sind. Wenn es zu viele sind, kann das darauf hinweisen, dass die Verbindung instabil ist. Weitere Informationen finden Sie im Abschnitt [Probleme mit instabilen Verbindungen](../../delivery/using/sms-protocol.md#issues-unstable-connection).

#### INQUIRE_LINK {#enquire-link-pdus}

Vergewissern Sie sich, dass `ENQUIRE_LINK PDU`s regelmäßig ausgetauscht werden, wenn die Verbindung inaktiv ist.

**SUBMIT_SM / DELIVER_SM**

Senden Sie eine Nachricht und suchen Sie dann in den Logs nach den zugehörigen `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` und `DELIVER_SM_RESP PDU`s.

Mit der `SUBMIT_SM PDU`:

* Prüfen Sie, ob `data_coding` korrekt ist, standardmäßig 0.
* Prüfen Sie, ob `short_message` korrekt kodiert ist. Versuchen Sie, mit einem Hexadezimal-Konverter zu dekodieren, der mehrere Kodierungen unterstützt.

Mit der `SUBMIT_SM_RESP PDU`:

* Vergewissern Sie sich, dass sie erfolgreich war, command_status = 0.
* Vergewissern Sie sich, dass der Hauptteil eine ordnungsgemäß formatierte ID und anschließend ein 0-Byte enthält.

Mit der `DELIVER_SM PDU`:

* Dekodieren Sie das hexadezimale `short_message`-Feld.
* Überprüfen Sie mit einem Regex-Überprüfungstool, ob der im `Extraction`-Regex der ID im SR definierte Regex genau eine Erfassungsgruppe zurückgibt und die gesamte ID in der Nachricht erfasst.
* Überprüfen Sie, ob die extrahierte ID mit der in `SUBMIT_SM_RESP` übereinstimmt.
* Vergewissern Sie sich, dass der im `Extraction`-Regex des Status im SR definierte Regex den Inhalt des stat-Felds zurückgibt.
* Vergewissern Sie sich, dass der im `Extraction`-Regex des Fehlers im SR definierte Regex den Inhalt des err-Felds zurückgibt.

Mit der `DELIVER_SM_RESP PDU`:

* Vergewissern Sie sich, dass sie nach Empfang der `DELIVER_SM PDU` schnell gesendet wurde, in der Regel in weniger als 1 Sekunde.
* Vergewissern Sie sich, dass sie erfolgreich war, command_status = 0.

### Kontaktieren des Providers {#provider}

Auch wenn Ihre SMS erfolgreich ist, sollten Sie beim Provider nachfragen, ob alles in Ordnung ist.

### Deaktivieren der ausführlichen SMPP-Verfolgung {#disable-verbose}

Sobald alle Überprüfungen abgeschlossen sind, müssen Sie **die ausführliche SMPP-Verfolgung deaktivieren**, um nicht zu viele Logs zu generieren. Sie können sie auch in Produktionssystemen zur Fehlerbehebung erneut aktivieren.
