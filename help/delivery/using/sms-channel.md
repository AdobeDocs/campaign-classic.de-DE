---
title: SMS-Kanal
seo-title: SMS-Kanal
description: SMS-Kanal
seo-description: null
page-status-flag: never-activated
uuid: be6a2abc-ba5c-4363-bf38-cc309ee3a8d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 8b101c0b-3611-4f15-813b-7c0bf54fc48a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '3272'
ht-degree: 100%

---


# SMS-Kanal{#sms-channel}

Adobe Campaign ermöglicht die Zustellung großer Mengen personalisierter SMS-Nachrichten. Die Empfängerprofile müssen mindestens eine Mobiltelefonnummer enthalten.

>[!NOTE]
>
>Die Option **Mobile App Channel (NMAC)** ermöglicht darüber hinaus den Empfang von Benachrichtigungen auf mobilen Terminals.
> 
>Weiterführende Informationen finden Sie im Abschnitt [Über den Mobile-App-Kanal](../../delivery/using/about-mobile-app-channel.md).

Die folgenden Abschnitte enthalten Informationen, die speziell für den SMS-Kanal gelten. Allgemeine Informationen zum Erstellen einer Sendung finden Sie in [diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

## SMS-Kanal einrichten {#setting-up-sms-channel}

Folgende Voraussetzungen müssen gegeben sein, um Sendungen an Mobiltelefone richten zu können:

1. ein externes Konto mit Angabe des Connectors und des Nachrichtentyps;

   Beachten Sie, dass folgende Connectoren ab Version 20.2 nicht mehr unterstützt werden: NetSize, Generic SMPP (SMPP Version 3.4 mit Unterstützung für Binärmodus), Sybase365 (SAP SMS 365), CLX Communications, Tele2, O2 und iOS. Eingestellte Funktionen sind weiterhin verfügbar, werden jedoch weder weiter verbessert noch unterstützt. Weiterführende Informationen hierzu finden Sie auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/deprecated-and-removed-features.html).

1. Eine Versandvorlage, die auf das externe Konto Bezug nimmt.

### Erstellen eines externen SMPP-Kontos {#creating-an-smpp-external-account}

Um eine SMS an ein Mobiltelefon zu senden, müssen Sie zunächst Ihr externes SMPP-Konto erstellen.
Weitere Informationen zum SMS-Protokoll und zu den Einstellungen finden Sie in dieser [Technote](https://helpx.adobe.com/de/campaign/kb/sms-connector-protocol-and-settings.html).

Gehen Sie dazu wie folgt vor:

1. Wählen Sie dazu im Navigationsbaum im Knoten **[!UICONTROL Plattform]** > **[!UICONTROL Externe Konten]** das Symbol **[!UICONTROL Neu]** aus.
1. Definieren Sie den Kontotyp mit **Routing**, den Kanal mit **Mobiltelefon (SMS)** und den Versandmodus mit **Gebündelter Versand**.

   ![](assets/extended_smpp_create_account.png)

1. Kreuzen Sie die Option **[!UICONTROL Aktiviert]** an.
1. Wählen Sie im Tab **[!UICONTROL Mobiltelefon]** aus der **[!UICONTROL Connector]**-Dropdown-Liste die Option **[!UICONTROL Erweitertes allgemeines SMPP]**.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > Ab Version 20.2 werden ältere Connectoren eingestellt und nicht mehr unterstützt. Es wird empfohlen, den Connector **[!UICONTROL Erweitertes allgemeines SMPP]** zu verwenden. Weiterführende Informationen über das Migrieren zum empfohlenen Connector finden Sie auf dieser [Seite](https://helpx.adobe.com/de/campaign/kb/sms-connector.html).

1. Mit der Option **[!UICONTROL Ausführliche SMPP-Protokolle in der Protokolldatei aktivieren]** können Sie den gesamten SMPP-Traffic in Logdateien speichern. Diese Option muss aktiviert sein, um eine Fehlerbehebung beim Connector durchzuführen und einen Vergleich mit dem vom Provider aufgezeichneten Traffic anzustellen.

1. Wenden Sie sich an Ihren SMS-Dienstleister. Dieser kann Ihnen die für das externe Konto erforderlichen Angaben auf dem Tab **[!UICONTROL Verbindungsparameter]** bereitstellen.

   Der von Ihnen ausgewählte Provider nennt Ihnen danach den Wert für das Feld **[!UICONTROL Name der SMSC-Implementierung]**.

   Sie können die Anzahl der Verbindungen mit dem Dienstleister per untergeordnetem MTA definieren. Standardmäßig ist 1 eingestellt.

1. Standardmäßig kommt in Bezug auf die maximal zulässige Zeichenanzahl einer SMS der Mobilfunkstandard GSM zur Anwendung.

   SMS, die das GSM-Alphabet verwenden, sind auf 160 Zeichen begrenzt oder auf 153 Zeichen pro SMS bei Nachrichten, die in mehreren Teilen gesendet werden.

   >[!NOTE]
   >
   >Gewisse Zeichen zählen doppelt (Akkoladen, eckige Klammern, Eurozeichen etc.).
   >
   >Eine Liste der von GSM unterstützten Zeichen finden Sie unten.

   Bei Bedarf können Sie die Transliteration von Zeichen zulassen, indem Sie die entsprechende Option aktivieren.

   ![](assets/extended_smpp_transliteration.png)

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#about-character-transliteration).

1. Im Tab **[!UICONTROL Durchsatz und Dauer]** können Sie den maximalen Durchsatz für ausgehende Nachrichten (&quot;MT&quot;, Mobile Terminated) festlegen. Bei Angabe von &quot;0&quot; im entsprechenden Feld ist der Durchsatz unbegrenzt.

   Werte, die eine Dauer angeben, sind in Sekunden auszudrücken.

1. Im Tab **[!UICONTROL Kodierungs-Mapping]** können Sie Kodierungen definieren.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#about-text-encodings).

1. Im Tab **[!UICONTROL SMSC-Besonderheiten]** ist die Option **[!UICONTROL Vollständige Telefonnummer senden]** standardmäßig deaktiviert. Aktivieren Sie sie nicht, wenn Sie die Konformität mit dem SMPP-Protokoll wahren und nur Zahlen an den Server des SMS-Anbieters (SMSC) übertragen möchten.

   Bei gewissen Anbietern ist die Verwendung des Vorzeichens &#39;+&#39; jedoch erforderlich, sodass es ratsam ist, mit Ihrem Anbieter Kontakt aufzunehmen, der Sie bei Bedarf dazu auffordern wird, diese Option zu aktivieren.

   Das Kontrollkästchen **[!UICONTROL TLS über SMPP aktivieren]** ermöglicht die Verschlüsselung von SMPP-Traffic. Weitere Informationen hierzu finden Sie in dieser [Technote](https://helpx.adobe.com/de/campaign/kb/sms-connector-protocol-and-settings.html).

1. Wenn Sie einen Connector vom Typ **[!UICONTROL Erweitertes allgemeines SMPP]** konfigurieren, können Sie automatische Antworten einrichten.

   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#automatic-reply).

### Über die Transliteration von Zeichen {#about-character-transliteration}

Die Transliteration von Zeichen kann in einem externen Konto für den SMPP-Mobiltelefon-Versand im Tab **[!UICONTROL Mobile]** eingerichtet werden.

Transliteration bezeichnet in einer SMS die Ersetzung eines Zeichens durch ein anderes, wenn das erste Zeichen nicht von GSM unterstützt wird.

* Wenn die Transliteration **[!UICONTROL zugelassen]** wurde, wird jedes nicht unterstützte Zeichen beim Nachrichtenversand durch ein Zeichen des GSM-Alphabets ersetzt. So wird beispielsweise der Buchstabe &quot;ë&quot; durch &quot;e&quot; ersetzt. Der Nachrichteninhalt wird in diesem Fall leicht verändert übermittelt, aber die Zeichenanzahl bleibt identisch.
* Wenn die Transliteration **[!UICONTROL nicht zugelassen]** wurde, werden alle Nachrichten mit nicht unterstützten Zeichen im Binärformat (Unicode) gesendet: Alle Zeichen werden unverändert übermittelt. In Unicode kodierte SMS sind auf 70 Zeichen (oder 67 Zeichen bei Nachrichten, die in mehreren Teilen gesendet werden) begrenzt. Bei Überschreitung der maximalen Zeichenanzahl werden mehrere Teilnachrichten gesendet, wodurch zusätzliche Kosten entstehen können.

>[!IMPORTANT]
>
>Die Verwendung von Personalisierungsfeldern im SMS-Inhalt führt u. U. dazu, dass nicht von GSM unterstützte Zeichen eingefügt werden.

Die Transliteration von Zeichen ist standardmäßig deaktiviert. Es wird empfohlen, diese Option nicht zu aktivieren, wenn Sie alle Zeichen Ihrer SMS beibehalten möchten, um beispielsweise Eigennamen unverändert zu übermitteln.

Sollte Ihre SMS jedoch eine hohe Anzahl an Zeichen enthalten, die dem Unicode-Zeichensatz entstammen, können Sie diese Option wählen, um Ihre Versandkosten zu begrenzen.

Die folgende Tabelle zeigt den vom GSM-Standard unterstützten Zeichensatz. Jedes im Nachrichteninhalt enthaltene Zeichen, das nicht in der unten stehenden Tabelle aufgeführt ist, führt zur Konvertierung der gesamten Nachricht in das Binärformat (Unicode), sobald sie 70 Zeichen überschreitet.

**Einfache Zeichen**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> ¡ </td> 
   <td> P </td> 
   <td> ¿ </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> " </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> ¤ </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: Leerzeichen

ESC: Escape

LF: Zeilenvorschub

CR: Wagenrücklauf

**Doppelt zählende Zeichen**

^ { } `[ ~ ]` | €

### Über Textkodierungen {#about-text-encodings}

Beim SMS-Versand kann Adobe Campaign eine oder mehrere Textkodierungen verwenden. Je nach Kodierung kommen unterschiedliche Zeichensätze zur Anwendung und variiert die Anzahl an zulässigen Zeichen pro SMS.

Beim Konfigurieren eines neuen externen Kontos für einen SMPP-Mobiltelefon-Versand können Sie das **[!UICONTROL Kodierungs-Mapping]** im Tab **[!UICONTROL Mobiltelefon]** definieren: Über das Feld **[!UICONTROL data_coding]** kann Adobe Campaign dem SMSC (Short Message Service Center) kommunizieren, welche Kodierung verwendet wird.

>[!NOTE]
>
>Das Mapping zwischen dem Wert des **data_coding**-Felds und der tatsächlich verwendeten Kodierung ist standardisiert. Gewisse SMSC besitzen jedoch ihr eigenes Mapping. In diesem Fall muss Ihr **Adobe-Campaign**-Administrator das Mapping deklarieren. Kontaktieren Sie für weiterführende Informationen Ihren Anbieter.

Sie können **data_codings** deklarieren. Durch Angabe von nur einer Kodierung in der Tabelle wird die Anwendung dieser Kodierung erzwungen.

* Wenn kein Kodierungs-Mapping definiert wurde, verhält sich der Connector standardmäßig:

   * Er versucht, das GSM-Alphabet zu verwenden und ordnet diesem den Wert **DATA_CODING = 0** zu.
   * Falls die Verwendung des GSM-Alphabets nicht möglich ist, verwendet er **UCS2** und ordnet den Wert **DATA_CODING = 8** zu.

* Wenn Sie die zu verwendenden Kodierungen sowie die damit verbundenen **[!UICONTROL data_coding]**-Feldwerte definieren, verwendet Adobe Campaign die Kodierungen in der Reihenfolge ihres Erscheinens in der Liste. Wenn die Verwendung der ersten Kodierung nicht möglich ist, wird die zweite verwendet, usw.

>[!IMPORTANT]
>
>Die Reihenfolge der Deklarierung ist entscheidend. Wir empfehlen Ihnen, die Liste aufsteigend nach den entstehenden **Kosten** zu ordnen, um die Kodierungen zu favorisieren, die eine größere Anzahl von Zeichen pro SMS erlauben.
>
>Deklarieren Sie nur die Kodierungen, die Sie tatsächlich verwenden möchten. Deklarieren Sie hingegen keine vom SMSC angebotenen Kodierungen in der Liste, die nicht Ihrer Verwendung entsprechen.

### Automatische Antwort {#automatic-reply}

Wenn Sie einen Connector vom Typ Erweitertes allgemeines SMPP konfigurieren, können Sie automatische Antworten einrichten.

Im Bereich **[!UICONTROL Automatische Antwort auf MO]** können Sie Benachrichtigungen konfigurieren, die automatisch gesendet werden, wenn ein Abonnent auf eine durch Adobe Campaign versendete SMS mit einer ein Schlüsselwort wie beispielsweise &quot;STOP&quot; enthaltenden Nachricht antwortet.

>[!NOTE]
>
>Bei den Schlüsselwörtern kann die Groß-/Kleinschreibung ignoriert werden.

Geben Sie für jedes Schlüsselwort eine Kurzwahlnummer (short code) an, d. h. eine als Absendername fungierende Nummer, die gewöhnlich für den Nachrichtenversand verwendet wird, sowie die an den Abonnenten zu sendende Nachricht.

Es besteht die Möglichkeit, jeder automatischen Antwort eine Aktion zuzuordnen: **[!UICONTROL Unter Quarantäne stellen]** oder **[!UICONTROL Aus der Quarantäne entfernen]**. Wenn beispielsweise das Wort &quot;STOP&quot; gesendet wird, erhält der Abonnent automatisch eine Abmeldebestätigung und sein Profil wird unter Quarantäne gestellt.

![](assets/extended_smpp_reply.png)

Wird die Aktion **[!UICONTROL Aus der Quarantäne entfernen]** mit einer automatischen Antwort verknüpft, werden die Empfänger, die das entsprechende Schlüsselwort senden, automatisch aus der Quarantäne entlassen.

Die Empfänger sind in der Tabelle **[!UICONTROL Adressen unzustellbarer Sendungen]** aufgeführt, die über das Menü **[!UICONTROL Administration]** > **[!UICONTROL Kampagnenverwaltung]** > **[!UICONTROL Unzustellbarkeitsverwaltung]** abrufbar ist.

* Lassen Sie die Spalte **[!UICONTROL Kurzwahlnummer]** leer, wenn unabhängig von der Kurzwahlnummer dieselbe Nachricht gesendet werden soll.
* Lassen Sie die Spalte **[!UICONTROL Schlüsselwort]** leer, wenn unabhängig vom Schlüsselwort dieselbe Nachricht gesendet werden soll.
* Lassen Sie die Spalte **[!UICONTROL Antwort]** leer, wenn nur eine Aktion ausgeführt, aber keine Antwort gesendet werden soll. Dies ermöglicht beispielsweise die Entlassung eines Abonnenten aus der Quarantäne, wenn er ein anderes Schlüsselwort als &quot;STOP&quot; sendet.

Wenn Sie mehrere externe Konten mit dem Connector „Erweitertes allgemeines SMPP“ mit demselben Provider-Konto haben, kann das folgende Problem auftreten: Wenn Sie eine Antwort an eine Kurzwahlnummer senden, kann sie auf einer Ihrer externen Kontoverbindungen empfangen werden. Folglich ist die automatische Antwort, die gesendet wird, möglicherweise nicht die erwartete Nachricht.
Um dies zu vermeiden, wenden Sie je nach verwendetem Provider eine der folgenden Lösungen an:

* Erstellen Sie für jedes externe Konto ein Provider-Konto.
* Verwenden Sie das Feld **[!UICONTROL Systemtyp]** im Tab **[!UICONTROL Mobiltelefon]** > **[!UICONTROL Verbindungsparameter]**, um jede Kurzwahlnummer zu unterscheiden. Bitten Sie Ihren Provider um einen anderen Wert für jedes Konto.

   ![](assets/extended_smpp_system-type.png)

Die Schritte zum Einrichten eines externen Kontos mithilfe des Connectors „Erweitertes allgemeines SMPP“ sind im Abschnitt [Erstellen eines externen SMPP-Kontos](../../delivery/using/sms-channel.md#creating-an-smpp-external-account) beschrieben.

### Versandvorlagen ändern {#changing-the-delivery-template}

Adobe Campaign enthält eine vorkonfigurierte Vorlage für Sendungen auf Mobiltelefone. Auf diese Vorlage können Sie im Knoten **[!UICONTROL Ressourcen > Vorlagen > Versandvorlagen]** zugreifen. Weiterführende Informationen finden Sie im Abschnitt [Über Vorlagen](../../delivery/using/about-templates.md).

Um den SMS-Kanal zu nutzen, muss in der Versandvorlage der entsprechende Connector angegeben werden.

Wir empfehlen Ihnen, nicht die native Versandvorlage zu ändern, sondern diese zu duplizieren und die Kopie nach Bedarf zu konfigurieren.

Im folgenden Beispiel wird eine Vorlage erstellt, die dem Versand von Nachrichten mithilfe des zuvor aktivierten SMPP-Kontos dient. Gehen Sie dazu wie folgt vor:

1. Markieren Sie den **[!UICONTROL Versandvorlagen]**-Knoten.
1. Klicken Sie mit der rechten Maustaste auf die Vorlage **[!UICONTROL Versand auf Mobiltelefone]** und wählen Sie die Option **[!UICONTROL Duplizieren]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Ändern Sie die Beschriftung der Vorlage, z. B. **Mobiltelefon-Versand (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie auf dem Tab **[!UICONTROL Allgemein]** einen Routing-Modus, der dem externen Konto entspricht, das Sie in den vorherigen Schritten erstellt haben.

   ![](assets/s_user_mobile_template_change_03.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Erstellung abzuschließen.

   ![](assets/s_user_mobile_template_list.png)

Sie verfügen nun über ein externes Konto und eine Versandvorlage, die es Ihnen erlauben, per SMS zu versenden.

## SMS-Versand erstellen {#creating-a-sms-delivery}

### Versandkanal auswählen {#selecting-the-delivery-channel}

Gehen Sie wie folgt vor, um einen neuen SMS-Versand zu erstellen:

>[!NOTE]
>
>Allgemeine Methoden zur Versanderstellung finden Sie in [diesem Abschnitt](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Erstellen Sie einen neuen Versand beispielsweise im Versand-Dashboard.
1. Wählen Sie die zuvor erstellte Versandvorlage **Mobiltelefon-Versand (SMPP)** aus. Lesen Sie diesbezüglich auch den Abschnitt [Versandvorlagen ändern](#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Geben Sie für Ihren Versand einen Titel, einen Code und eine Beschreibung ein. Weiterführende Informationen dazu finden Sie in [diesem Abschnitt](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Klicken Sie auf **[!UICONTROL Fortfahren]**, um die Eingaben zu bestätigen und in das Fenster der Nachrichtenkonfiguration zu gelangen.

## SMS-Inhalt erstellen {#defining-the-sms-content}

Um den Inhalt der SMS zu erstellen, gehen Sie wie folgt vor:

1. Geben Sie den Nachrichteninhalt im Bereich **[!UICONTROL Textinhalt]** des Assistenten ein. Die Schaltflächen der Symbolleiste bieten die Möglichkeit, Inhalte zu importieren und zu speichern oder in ihnen zu suchen. Die letzte Schaltfläche in der Symbolleiste dient der Einfügung von Personalisierungsfeldern.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   Die Verwendung von Personalisierungsfeldern wird im Abschnitt [Über die Personalisierung](../../delivery/using/about-personalization.md) beschrieben.

1. Durch Auswahl des **[!UICONTROL Vorschau]**-Tabs unten auf der Seite können Sie das Rendering der personalisierten Nachricht prüfen. Klicken Sie in der Symbolleiste auf die Schaltfläche **[!UICONTROL Personalisierung testen]** und wählen Sie einen Empfänger aus der Zielgruppe oder ein anderes Profil aus.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Sie können nun den personalisierten Nachrichteninhalt sowie die Anzeige der SMS auf dem rechts im Bild angezeigten Mobiltelefondisplay prüfen. Klicken Sie auf das Display, um die Nachricht mit der Maus zu scrollen.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Der Link **[!UICONTROL Geladene Daten]** ermöglicht die auszugsweise Anzeige des Empfängerprofils.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >Bei Verwendung der Codepage „Latin-1 (ISO-8859-1)“ ist die Länge von SMS auf 160, bei Unicode auf 70 Zeichen begrenzt. Gewisse Sonderzeichen können die Länge der Nachricht beeinflussen. Weitere Informationen zur Nachrichtenlänge finden Sie im Abschnitt [Über die Transliteration von Zeichen](#about-character-transliteration).
   >
   >Wenn die Nachricht Personalisierungsfelder oder bedingte Inhalte enthält, kann die Länge von Empfänger zu Empfänger variieren. Daher sollte die Länge jeweils nach erfolgter Personalisierung geprüft werden.
   >
   >Während der Analysephase wird die Nachrichtenlänge geprüft und im Falle eines Überschreitens ein Warnhinweis erzeugt.

1. Wenn Sie den NetSize-Connector oder einen SMPP-Connector verwenden, besteht die Möglichkeit, den Absendernamen des Versands zu personalisieren. Weitere Informationen hierzu finden Sie im Abschnitt [Erweiterte Parameter](#advanced-parameters).

## Zielgruppe bestimmen {#selecting-the-target-population}

Die detaillierten Schritte zur Auswahl der Zielpopulation eines Versands finden Sie in [diesem Abschnitt](../../delivery/using/steps-defining-the-target-population.md).

Weitere Informationen zur Verwendung von Personalisierungsfeldern finden Sie unter [Über die Personalisierung](../../delivery/using/about-personalization.md).

Weitere Informationen zur Verwendung von Testadressen finden Sie unter [Über Testadressen](../../delivery/using/about-seed-addresses.md).

## SMS-Nachrichten senden {#sending-sms-messages}

Klicken Sie auf **[!UICONTROL Senden]**, um die Nachrichtenerstellung abzuschließen und den Versand zu starten.

Die detaillierten Schritte zur Validierung und zum Versand von Nachrichten finden Sie in den folgenden Abschnitten:

* [Versand validieren](../../delivery/using/steps-validating-the-delivery.md)
* [Versenden der Nachrichten](../../delivery/using/steps-sending-the-delivery.md)

### Erweiterte Parameter {#advanced-parameters}

Die Schaltfläche **[!UICONTROL Eigenschaften]** gibt Zugriff auf erweiterte Versandparameter. Der Abschnitt **[!UICONTROL SMS-Parameter]** im **[!UICONTROL Senden]**-Tab ermöglicht spezifische Konfigurationen.

Folgende Optionen stehen zur Verfügung:

* **Absenderadresse**: ermöglicht die Personalisierung des Versandabsenders mit einer Zeichenfolge aus alphanumerischen Zeichen, die auf elf Zeichen begrenzt ist. Das Feld darf nicht ausschließlich aus Zahlen bestehen. Sie können eine Bedingung definieren, um beispielsweise je nach Bereichs-Code des Empfängers unterschiedliche Namen anzuzeigen:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Überprüfen Sie die gültige Rechtslage Ihres Landes bezüglich der Änderung des Absendernamens. Stellen Sie außerdem sicher, dass Ihr Provider diese Funktionalität anbietet.

* **Übermittlungsmodus**: Art der SMS-Übermittlung.
* **Priorität**: Einer Nachricht zugeordnete Wichtigkeit. Standardmäßig wird die Priorität **[!UICONTROL Normal]** vorgeschlagen. Je nach Provider können Zuschläge für mit der Priorität **[!UICONTROL Hoch]** versendete SMS anfallen.
* **Anwendungstyp**: Verschiedene Optionen stehen zur Auswahl. Standardmäßig wird **[!UICONTROL Direktmarketing]** vorgeschlagen, da es sich um den am häufigsten verwendeten Typ handelt.

**Den NetSize-Connector betreffende Parameter**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Nachricht in mehreren SMS versenden**: ermöglicht den Versand von Nachrichten mit mehr als 160 Zeichen in mehreren SMS.

**SMPP-Connectoren betreffende Parameter**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Maximale Anzahl an SMS pro Nachricht**: ermöglicht die Angabe der maximalen SMS-Anzahl pro Nachricht, wobei 0 für eine SMS steht. Wenn die Nachricht mehr als die angegebene Anzahl an SMS benötigt, wird sie nicht gesendet.

## SMS-Sendungen beobachten und verfolgen {#monitoring-and-tracking-sms-deliveries}

Nach Absenden der Nachrichten können Sie den Versand beobachten und verfolgen, siehe diese Abschnitte:

* [Sendungen beobachten](../../delivery/using/monitoring-a-delivery.md)
* [Ursachen von fehlgeschlagenen Sendungen](../../delivery/using/understanding-delivery-failures.md)
* [Über das Nachrichten-Tracking](../../delivery/using/about-message-tracking.md)

## Verarbeitung eingehender Nachrichten {#processing-inbound-messages}

Das Modul **nlserver sms** ruft in regelmäßigen Abständen den Verarbeitungsfortschritt der Sendungen, Empfangsbestätigungen und Empfängerabmeldungen ab.

* **Empfangsbestätigungen**: Der Status Ihrer Sendungen kann in den Versandlogs eingesehen werden.

   >[!NOTE]
   >
   >Jede gesendete SMS ist mit einem externen Konto über den Primärschlüssel des letzteren verbunden. Dies bedeutet, dass
   >
   > * Empfangsbestätigungen eines externen Kontos für gelöschte SMS nicht korrekt verarbeitet werden können.
   > * ein SMS-Konto nur mit einem externen Konto verknüpft sein darf, damit die Empfangsbestätigungen korrekt zugeordnet werden können


* **Abmeldungen**: Empfänger, die keine SMS-Sendungen mehr erhalten möchten, können sich durch das Senden einer Nachricht mit Inhalt STOP abmelden. Wenn es Ihr Providervertrag vorsieht, können Sie diese Nachrichten mithilfe der Workflow-Aktivität **SMS-Empfang** abrufen. Dies ermöglicht die Erstellung einer Abfrage, die die Option **Diese Person nicht mehr kontaktieren** für die entsprechenden Empfänger aktiviert.

   Nähere Informationen hierzu finden Sie im [Workflows](../../workflow/using/architecture.md)-Handbuch.

## InSMS-Schema {#insms-schema}

Das InSMS-Schema enthält Informationen zu eingehenden SMS. Die Beschreibung dieser Felder findet sich in ihren jeweiligen desc-Attributen.

* **message**: Inhalt der erhaltenen SMS.
* **origin**: Mobiltelefonnummer des Nachrichtenabsenders.
* **providerId**: Kennung der vom SMS-SC (Short Message Service Centre) zurückgegebenen Nachricht.
* **created**: Eingangsdatum der Nachricht in Adobe Campaign.
* **extAccount**: externes Adobe-Campaign-Konto.

   >[!IMPORTANT]
   >
   >Die folgenden Felder sind NetSize-spezifisch.
   >
   >Wenn der Betreiber nicht NetSize verwendet, bleiben diese Felder leer.

* **alias**: Alias der eingehenden Nachricht.
* **separator**: Trennzeichen zwischen Alias und Nachrichten-Textkörper.
* **messageDate**: Nachrichtendatum gemäß Betreiber.
* **receivalDate**: Datum des Empfangs der vom Betreiber gesendeten Nachricht im SMS-SC (Short Message Service Centre).
* **deliveryDate**: Datum des Versands der Nachricht durch das SMS-SC (Short Message Service Centre).
* **largeAccount**: Code des der eingehenden SMS zugeordneten Kundenkontos.
* **countryCode**: Ländercode des Betreibers.
* **operatorCode**: Netzwerkcode des Betreiber.
* **linkedSmsId**: Adobe-Campaign-Kennung (broadlogId) der ausgehenden SMS, auf die diese SMS antwortet.

## Automatische Antworten (US-amerikanische Gesetzgebung) {#managing-automatic-replies--american-regulation-}

Wenn ein Abonnent auf eine durch Adobe Campaign versendete SMS mit einer die Schlüsselwörter STOP, HELP oder YES enthaltenden Nachricht antwortet, ist für den US-amerikanischen Markt eine Konfiguration der automatischen Benachrichtigungen an den Absender gesetzlich vorgeschrieben.

Wenn beispielsweise das Wort STOP gesendet wird, erhält der Abonnent automatisch eine Abmelde-Bestätigung.

Der Absendername für diese Art von Nachrichten besteht aus einer kurzen Nummer (short code), welche auch für die üblichen Sendungen genutzt wird.

>[!IMPORTANT]
>
>Das folgende detaillierte Verfahren gilt nur für SMPP-Connectoren, mit Ausnahme des Connectors „Erweitertes allgemeines SMPP“. Weitere Informationen hierzu finden Sie im Abschnitt [Erstellen eines externen SMPP-Kontos](#creating-an-smpp-external-account).
>
>Sie betrifft die Zertifizierung durch amerikanische Provider bezüglich in den USA zu versendender Marketingkampagnen. Insbesondere müssen diese SMS dem Abonnenten, der ein entsprechendes Schlüsselwort gesendet hat, unverzüglich zugestellt werden.

1. Erstellen Sie eine XML-Datei nach folgendem Muster:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Geben Sie für das Attribut **name** des **`<shortcode>`**-Tags die Kurzwahlnummer an, die anstelle des Absendernamens angezeigt werden soll.

   Geben Sie in jedem **`<reply>`**-Tag im Attribut **keyword** ein Schlüsselwort und im Attribut **text** die dem Schlüsselwort entsprechende Nachricht an.

   >[!NOTE]
   >
   >Schlüsselwörter sind in Großbuchstaben zu schreiben.

   Wenn Sie für verschiedene Schlüsselwörter dieselbe Nachricht versenden möchten, können Sie die entsprechende Zeile duplizieren.

   Beispiel:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Speichern Sie dann die Datei unter dem Namen **smsAutoReply.xml**.

   Bitte berücksichtigen Sie, dass beim Dateinamen unter Linux die Groß- und Kleinschreibung zu beachten ist.

1. Kopieren Sie die Datei in das **conf**-Verzeichnis in Adobe Campaign (am gleichen Ort wie der Web-Server).

>[!IMPORTANT]
>
>Für diese Arten von Benachrichtigungen wird kein Verlauf erstellt. Sie sind also nicht im [Versand-Dashboard](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) enthalten.
>
>Sie werden des Weiteren nicht bei der Berechnung des [Werbedrucks](../../campaign/using/pressure-rules.md) berücksichtigt.
