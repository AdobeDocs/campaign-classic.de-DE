---
product: campaign
title: Protokoll und Einstellungen des SMS-Connectors
description: Erfahren Sie mehr über den SMS-Connector und dessen Konfiguration
feature: SMS
role: Developer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
TQID: 'https://experienceleague.adobe.com/-e39I2kK3veYtZTufN0ZZrnZPAAco47dU8HFlCtlIxY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b1bd1421-1927-4c59-9bc6-ce292360e43b
    internal-label: SMS Messaging
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: ht
source-wordcount: '4785'
ht-degree: 100%
---
# Protokoll und Einstellungen des SMS-Connectors {#sms-connector-protocol}

>[!NOTE]
>
>In diesem Dokument beziehen sich alle Informationen zum Protokoll, zum Feldnamen und zu Feldwerten auf die [Spezifikation von SMPP Version 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

Im Zuge der Umstellung von Campaign v7 auf v8 wurde die Campaign Classic-Dokumentation optimiert und neu organisiert. Allgemeine Funktionen sind jetzt nur noch in der Dokumentation zu Campaign v8 verfügbar. Weitere Informationen zu den SMS-Connector-Einstellungen finden Sie in der [Dokumentation zu Campaign v8](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}

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

## SMPP-Protokoll {#smpp-protocol}

Adobe Campaign Classic unterstützt die Version 3.4 des SMPP-Protokolls. SMPP ist ein weit verbreitetes Protokoll, das den Versand von SMS an einen Anbieter (SMSC) sowie den Empfang von SMS und Empfangsbestätigungen ermöglicht. Weitere Informationen finden Sie in der [SMPP-Dokumentation](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

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

* **data_coding**: Gibt die im Textfeld verwendete Kodierung an. Weitere Informationen finden Sie im Abschnitt [SMS-Textkodierung](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/sms-channel#sms-text-encoding){target="_blank"} (Dokumentation zu Campaign v8).

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

* **short_message**: Der Text der Nachricht. Für den SR enthält dies Daten, die in Anhang B der SMPP-Protokollspezifikation beschrieben sind. Weitere Informationen finden Sie unter [Umgang mit SR-Fehlern](sms-protocol.md#sr-error-management).

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

>[!IMPORTANT]
>
> Adobe Campaign unterstützt beim Senden nur mehrteilige SMS oder lange SMS. UDH und `message_payload` werden für eingehende SMS (MO) nicht unterstützt, was bedeutet, dass MO auf 160 Zeichen begrenzt sind.

### Durchsatzbegrenzung und Fenster {#throughput-capping}

Die meisten Provider verlangen eine Durchsatzbegrenzung für jede SMPP-Verbindung. Dies kann durch die Festlegung einer Anzahl von SMS im externen Konto erreicht werden. Beachten Sie, dass die Durchsatzdrosselung pro Verbindung erfolgt. Der gesamte effektive Durchsatz ist die Grenze pro Verbindung multipliziert mit der Anzahl Verbindungen insgesamt. Dies wird im Abschnitt [Simultane Verbindungen](sms-protocol.md#connection-settings) beschrieben.

Um den maximal möglichen Durchsatz zu erreichen, müssen Sie eine Feinabstimmung des maximalen Übertragungsfensters vornehmen. Das Übertragungsfenster ist die Anzahl der `SUBMIT_SM PDU`s, die gesendet werden können, ohne auf eine `SUBMIT_SM_RESP` zu warten. Weitere Informationen finden Sie im Abschnitt zu den [Übertragungsfenster-Einstellungen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account#smpp-delays){target="_blank"} (Dokumentation zu Campaign v8).

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

## SMPP-Parameter für externe Konten {#SMPP-parameters-external}

Jede Implementierung des SMPP-Protokolls weist viele Variationen auf. Um die Kompatibilität und Anpassungsfähigkeit zu verbessern, stehen viele Einstellungen zur Verfügung, um das Verhalten des SMPP-Connectors zu ändern. In diesem Abschnitt werden alle Parameter und ihre Auswirkungen auf den Connector beschrieben.

### Allgemeine Parameter und Routing {#general-parameters-routing}

**MTA-Instanzen für dieses Konto beschränken**

Es ist möglich, die Anzahl der MTA-Instanzen festzulegen, die eine Verbindung zum SMPP-Provider herstellen dürfen. Wenn diese Option aktiviert ist, können Sie angeben, wie viele MTAs maximal verwendet werden können.

Diese Option ermöglicht eine genauere Kontrolle über die Anzahl der Verbindungen, siehe [Simultane Verbindungen](sms-protocol.md#connection-settings).

Wenn Sie einen höheren Wert als die Anzahl der ausgeführten MTAs festlegen, werden alle MTAs wie gewohnt ausgeführt: Diese Option ist nur eine Begrenzung und kann keine zusätzlichen MTAs erzeugen.

Wenn Sie die Anzahl der Verbindungen genau steuern müssen, z. B. aufgrund von Provider-Anforderungen, empfiehlt es sich, diese Option immer zu setzen, auch wenn in der aktuellen Bereitstellung die richtige Anzahl von MTAs ausgeführt wird. Wenn anschließend weitere MTAs hinzugefügt werden, wird die Verbindungsgrenze weiterhin eingehalten.

### Verbindungsparameter {#connection-settings}

#### Name der SMSC-Implementierung {#smsc-implementation-name}

Legt den Namen der SMSC-Implementierung fest. Sollte auf den Namen Ihres Providers eingestellt werden. Wenden Sie sich an den Administrator oder das Zustellbarkeitsteam, um zu erfahren, was in diesem Feld hinzugefügt werden muss. Die Rolle dieses Felds wird im Abschnitt [Umgang mit SR-Fehlern](sms-protocol.md#sr-error-management) beschrieben.

>[!NOTE]
>
>Die Beauftragung des Zustellbarkeits-Teams ist vertraglich geregelt. Kundinnen und Kunden sollten sich an den Adobe-Support wenden, um diesbezügliche Informationen zu erhalten.

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

#### Eingehende MO in Datenbank speichern {#incoming-mo-storing}

Bei Aktivierung wird der eingehende MO in der inSMS-Tabelle der Datenbank gespeichert. Diese Tabelle kann mithilfe der Abfrageaktivität eines beliebigen Workflows abgefragt werden.

In Adobe Campaign Classic werden die MOs allesamt in der inSMS-Datenbank gespeichert, daher ist diese Option nicht verfügbar.

#### Echtzeit-KPI-Aktualisierungen während SR-Verarbeitung aktivieren {#real-time-kpi}

Wenn diese Option aktiviert ist, werden die KPIs in Echtzeit auf der Hauptseite für den Versand aktualisiert, wenn ein Fehler-SR empfangen wird.

Der Nachteil kann eine niedrige Performance aufgrund der dadurch erzeugten Datenbankinhalte sein. Wenn diese Option deaktiviert ist, werden Statistiken vom **syncfromexec**-Workflow aktualisiert, der alle 20 Minuten ausgeführt wird.

Der KPI-Mechanismus von Adobe Campaign Classic unterscheidet sich davon grundlegend, daher ist diese Option nicht verfügbar.

#### Kurzwahlnummer {#short-code}

Gibt die Hauptkurzwahlnummer des Kontos an. Wenn für dieses Konto mehrere Kurzwahlnummern verwendet werden oder wenn die Kurzwahlnummer unbekannt ist, lassen Sie dieses Feld leer.

Die Angabe von Kurzwahlnummern ist für zwei Funktionen hilfreich:

* Die Vorschau zeigt die Kurzwahlnummer an, wenn keine Anrufernummer angegeben wurde. Es wird das tatsächliche Verhalten auf dem Mobiltelefon widergespiegelt.

* Die Blockierungslisten-Einstellung der automatischen Antwortfunktion stellt Benutzer nur für die jeweilige Kurzwahlnummer unter Quarantäne.

### SMSC-Besonderheiten {#SMSC-specifics}

Bei diesen Einstellungen handelt es sich um erweiterte Einstellungen, mit denen der Adobe Campaign-Connector an die meisten SMPP-Implementierungseigenschaften angepasst wird.

#### TLS-Zertifikatsprüfung überspringen {#skip-tls}

Wenn TLS aktiviert ist, werden alle Zertifikatsprüfungen übersprungen.

Wenn diese Option aktiviert ist, ist die Verbindung nicht mehr sicher. Sie sollte nicht in der Produktion aktiviert werden.

Dies kann für Debugging- oder Testzwecke nützlich sein.

Sie können zwischen drei verschiedenen Werten für die Zertifikatsprüfung wählen:

* Vollständige Zertifikatsprüfung (einschließlich Host-Name), Standard.
* Host-Namen-Prüfung überspringen.
* Zertifikatsprüfung überspringen.

#### Regex angewendet, um den Erfolgs-/Fehlerstatus zu ermitteln {#regex-applied}

Wenn Meldungen mit einer unbekannten stat/err-Feldkombination auftreten, werden diese Regex auf das stat-Feld angewendet, um zu bestimmen, ob der SR erfolgreich oder fehlerhaft war. SR mit stat-Werten, die mit keinem Regex übereinstimmen, werden ignoriert.

Standardmäßig werden stat-Werte, die mit `DELIV` beginnen, z. B. `DELIVRD` in [Anhang B](sms-protocol.md#sr-error-management), als erfolgreich betrachtet und stat-Werte, die Fehler aufweisen, z. B. `REJECTED`, `UNDELIV`, werden als Fehler betrachtet.

#### ID-Format in der MT-Quittierung (resp) {#id-format-mt}

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

**Dienst-ID-Tag**

Ermöglicht das Hinzufügen eines benutzerdefinierten TLV. Dieses Feld legt den Tag-Teil fest. Der Wert kann pro Versand im Wert **Dienst- oder Programm-ID** in den erweiterten Parametern des Versands angepasst werden.

Diese Einstellung erlaubt nur das Hinzufügen einer TLV-Option pro Nachricht.

### Automatische Antwort auf MO {#automatic-reply}

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

### Versandparameter {#delivery-parameters}

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
