---
title: Bereitstellen einer Instanz
seo-title: Bereitstellen einer Instanz
description: Bereitstellen einer Instanz
seo-description: null
page-status-flag: never-activated
uuid: 5694b07a-6c1c-45a3-8a22-fd9da163c28c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 71fc8bfc-40e0-4592-a540-bd6807ded3a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Bereitstellen einer Instanz{#deploying-an-instance}

>[!NOTE]
>
>Serverseitige Konfigurationen können nur von Adobe für Bereitstellungen ausgeführt werden, die von Adobe gehostet werden. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder in [diesem Artikel](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Bereitstellungsassistent {#deployment-wizard}

Ein grafischer Assistent, der in der Adobe Campaign-Client-Konsole verfügbar ist, ermöglicht es Ihnen, die Parameter der Instanz zu definieren, mit der Sie eine Verbindung herstellen möchten.

Um den Bereitstellungsassistenten zu starten, wählen Sie &quot; **Werkzeuge&quot;> &quot;Erweitert&quot;> &quot;Bereitstellungsassistent&quot;**.

![](assets/s_ncs_install_deployment_wiz_01.png)

Die Konfigurationsschritte lauten wie folgt:

1. [Allgemeine Parameter](#general-parameters)
1. [Parameter für den E-Mail-Kanal](#email-channel-parameters)
1. [Verwalten von gekürzten E-Mails](#managing-bounced-emails)
1. [Verfolgungskonfiguration](#tracking-configuration)
1. [Parameter für mobile Kanäle](#mobile-channel-parameters)
1. [Regionale Einstellungen](#regional-settings)
1. [Internetzugang](#access-from-the-internet)
1. [Verwaltung öffentlicher Ressourcen](#managing-public-resources)
1. [Daten bereinigen](#purging-data)

## Allgemeine Parameter {#general-parameters}

Im ersten Schritt des Bereitstellungsassistenten können Sie allgemeine Informationen zur Instanz eingeben.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Allgemeine Informationen {#general-information}

Im unteren Bereich des Fensters können Sie die zu aktivierenden Optionen auswählen.

* **[!UICONTROL Customer identifier used in billing]** : Dies kann der Name der Instanz und die Versionsnummer sein.
* **[!UICONTROL Common name of the customer]** : Geben Sie eine Zeichenfolge mit dem Namen Ihres Unternehmens ein. Diese Informationen können in den Links zum Rückgängigmachen des Abonnements verwendet werden.
* **[!UICONTROL Namespace]** : Geben Sie einen kurzen Bezeichner in Kleinbuchstaben ein. Ziel ist es, im Falle einer Aktualisierung zwischen Ihrer spezifischen Konfiguration und der werkseitigen Konfiguration zu unterscheiden. Der Standard-Namespace ist **cus** - für Kunden.

### Technische Optionen {#technical-options}

Im unteren Bereich des Fensters können Sie die zu aktivierenden Optionen auswählen.

Folgende Optionen stehen zur Verfügung:

* **[!UICONTROL Email channel]** : , um die E-Mail-Zustellung zu aktivieren. Siehe [E-Mail-Kanalparameter](#email-channel-parameters).
* **[!UICONTROL Tracking]** : Aktivieren der Verfolgung der Zielpopulation (öffnet sich und klickt). Siehe [Tracking-Konfiguration](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : Zum Definieren des POP-Kontos, das zum Abholen eingehender E-Mails verwendet wird. Weitere Informationen finden Sie unter Verwalten von [gekürzten E-Mails](#managing-bounced-emails).
* **[!UICONTROL LDAP integration]** : Zum Konfigurieren der Benutzerauthentifizierung über einen LDAP-Ordner. Siehe [Verbindung über LDAP](../../installation/using/connecting-through-ldap.md)herstellen.

## Parameter für den E-Mail-Kanal {#email-channel-parameters}

Im folgenden Schritt können Sie die Informationen definieren, die in den Nachrichtenkopfzeilen angezeigt werden sollen.

Diese Parameter können in Bereitstellungsvorlagen und für jede Bereitstellung einzeln überladen werden (sofern die Benutzer über die erforderlichen Rechte verfügen).

### Parameter für gelieferte E-Mails {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Geben Sie die folgenden Parameter an:

* **[!UICONTROL Sender name]** : Name des Absenders,
* **[!UICONTROL Sender address]** : Anschrift des Absenders,
* **[!UICONTROL Reply address text]** : Der Name, der angepasst werden kann und verwendet wird, wenn der Empfänger auf die **[!UICONTROL Reply]** Schaltfläche in seiner E-Mail-Client-Software klickt,
* **[!UICONTROL Reply address]** : Die E-Mail-Adresse, die verwendet wird, wenn der Empfänger auf die **[!UICONTROL Reply]** Schaltfläche in seiner E-Mail-Client-Software klickt,
* **[!UICONTROL Error address]** : E-Mail-Adresse von Fehlermeldungen. Dies ist die technische Adresse, die für die Verarbeitung von Absprungmeldungen verwendet wird, einschließlich E-Mails, die vom Adobe Campaign-Server aufgrund nicht vorhandener Zieladressen empfangen wurden.

In addition to this, you can specify the **masks** authorized for the sender address and the error address. Bei Angabe von mehr als einer Maske sind die Masken durch Kommata zu trennen. Hierbei handelt es sich um eine optionale Konfiguration. Wenn Felder eingegeben werden, prüft Adobe Campaign zum Zeitpunkt der Bereitstellung (während der Analyse, ob die Adresse keine Variablen enthält), dass die Adressen gültig sind. Dieser Betriebsmodus stellt sicher, dass keine Adressen verwendet werden, die Bereitstellungsprobleme auslösen könnten. Absenderadressen sind auf dem Versandserver zu konfigurieren.

### In Adressen zugelassene Zeichen {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

In der Adobe Campaign-Datenbank müssen alle E-Mail-Adressen wie folgt erstellt werden: `x@y.z`. Die Zeichen **x**, **y** und **z** dürfen nicht leer sein und dürfen keine nicht autorisierten Zeichen enthalten.

Hier können Sie die autorisierten Zeichen (&#39;Datenrichtlinie&#39;) im E-Mail-Feld der Datenbank definieren. Zeichen, die nicht in der Liste aufgeführt sind, sind verboten und werden daher verweigert, wenn Informationen in der Datenbank über die Schnittstelle, über ein Web-Formular und auch Importieren von Daten.

Es stehen zwei Listen zur Verfügung: Nur **europäisch** oder nur **USA**. Bei Bedarf können weitere Zeichen hinzugefügt werden.

### Versandparameter {#delivery-parameters}

**Die** erweiterten Parameter... über den Link können Sie auf Auslieferungsoptionen, Parameter, die mit einem erneuten Versuch verknüpft sind, und Quarantäne zugreifen.

![](assets/s_ncs_install_deployment_wiz_05.png)

In diesem Fenster können Sie für alle E-Mail-Kampagnen die Optionen für die Bereitstellung und die Adressenqualität definieren.

Folgende Optionen stehen zur Verfügung:

* **[!UICONTROL Delivery duration of messages]** : Nach dieser Zeit wird die Bereitstellung gestoppt (standardmäßig 5 Tage),
* **[!UICONTROL Online resources validity duration]** : Zeit, für die Informationen aus dem Empfängerprofil aufbewahrt werden, um Spiegelseiten zu generieren,
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Wenn diese Option aktiviert ist, werden Empfänger in der schwarzen Liste nicht kontaktiert.
* **[!UICONTROL Automatically ignore doubles]** : Wenn diese Option aktiviert ist, wird die Bereitstellung nicht an doppelte Adressen vorgenommen.

### Wiederholungsparameter {#retry-parameters}

Die Informationen zu den Wiedereinziehungen sind in den Feldern **Wiederherstellungszeiträume** und **Anzahl der Wiedereinziehungen** angegeben: Wenn ein Empfänger nicht erreichbar ist, z. B. wenn sein Posteingang voll ist, versucht das Programm standardmäßig, ihn 5-mal zu kontaktieren, wobei zwischen jedem Versuch (während der maximalen Auslieferungszeit) ein einstündiger Zeitraum liegt. Diese Werte können an Ihre Anforderungen angepasst werden.

### Quarantäne-Parameter {#quarantine-parameters}

In Bezug auf die Quarantäne stehen folgende Konfigurationsoptionen zur Verfügung:

* **[!UICONTROL Duration between two significant errors]** : Geben Sie einen Wert (&quot;1d&quot;) standardmäßig ein: 1 Tag), um die Zeit zu definieren, die die Anwendung wartet, bevor der Fehlerzähler im Falle eines Fehlers erhöht wird,
* **[!UICONTROL Maximum number of errors before quarantine]** : Sobald dieser Wert erreicht ist, wird die E-Mail-Adresse unter Quarantäne gestellt (standardmäßig &quot;5&quot;: die Adresse wird beim sechsten Fehler in Quarantäne gestellt). Dies bedeutet, dass der Kontakt automatisch von den nächsten Sendungen ausgeschlossen wird.

## Verwalten von gekürzten E-Mails {#managing-bounced-emails}

Absprungmail ist äußerst wichtig, um die Lieferfehler zu qualifizieren. Diese Fehler werden im Ordner &quot;NP@I&quot;kategorisiert, sobald die Regeln ihre Ursache ermittelt haben.

Dieser Schritt ist nur verfügbar, wenn im ersten Schritt des Bereitstellungsassistenten die Optionen für die Verwaltung des **E-Mail-Kanals** und des **Absprungmailings** ausgewählt wurden. Siehe [Allgemeine Parameter](#general-parameters).

In dieser Phase können Sie Einstellungen für die Verwaltung von Absprungmeldungen definieren.

![](assets/s_ncs_install_deployment_wiz_06.png)

### POP-Konto zum Abrufen eingehender E-Mails {#pop-account-used-to-retrieve-incoming-mails}

Geben Sie die Parameter an, mit denen eine Verbindung zum Konto zum Abrufen eingehender E-Mails hergestellt werden soll.

* **[!UICONTROL Label]** : Name, der alle unten angegebenen Parameter enthält,
* **[!UICONTROL Server]** : Server, der zum Abrufen der Absprungmail (eingehende E-Mail) verwendet wird,
* **[!UICONTROL Security]** : Wählen Sie ggf. **[!UICONTROL SSL]** aus der Dropdownliste aus,
* **[!UICONTROL Port]** : Serveranschluss (im Allgemeinen 110),
* **[!UICONTROL Account]** : Name des Kontos, das für die Absprungmail verwendet wird,
* **[!UICONTROL Password]** : Kennwort für das Konto.

Nachdem Sie die POP-Einstellungen angegeben haben, klicken Sie auf **Testen** , um sicherzustellen, dass sie korrekt sind.

### Nicht verarbeitete Absprungmeldungen {#unprocessed-bounce-mails}

Absprünge werden automatisch von Adobe Campaign verarbeitet, wobei die unter &quot; **Administration&quot;> &quot;Kampagnenverwaltung&quot;> &quot;Verwaltung für nicht bereitgestellte Produkte&quot;> &quot;Qualifizierung** des Bereitstellungsprotokolls&quot;aufgelisteten Regeln angewendet werden. Weitere Informationen hierzu finden Sie unter [Absprungmail-Verwaltung](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Nicht verarbeitete Absprünge werden nicht auf der Adobe Campaign-Oberfläche angezeigt. Sie werden automatisch gelöscht, es sei denn, sie werden mithilfe der folgenden Felder in ein Drittanbieter-Postfach übertragen:

* **[!UICONTROL Forwarding address]** : Füllen Sie dieses Feld aus, um alle Fehlermeldungen (verarbeitet oder unverarbeitet), die von der Adobe Campaign-Plattform erfasst wurden, an eine Adresse eines Drittanbieters zu übertragen.
* **[!UICONTROL Address for errors]** : Füllen Sie dieses Feld aus, um nur die Fehlermeldungen an eine Adresse eines Drittanbieters zu übertragen, für die der InMail-Prozess nicht qualifiziert war.
* **[!UICONTROL SMTP server]** : Server, der zum Senden der nicht verarbeiteten Absprungs-E-Mails verwendet wird.

>[!CAUTION]
>
>Um unverarbeitete Absprung-E-Mails weiterzuleiten, empfiehlt Adobe, nur das **[!UICONTROL Address for errors]** Feld auszufüllen. Stellen Sie jedoch sicher, dass die verwendete Adresse regelmäßig überprüft wird, da dies zu einer starken Belastung Ihres Mailservers führen könnte. Weitere Informationen erhalten Sie von Ihrem Kundenbetreuer.

## Verfolgungskonfiguration {#tracking-configuration}

Im nächsten Schritt können Sie die Verfolgung für die Instanz konfigurieren. Die Instanz muss bei den Tracking-Servern deklariert und registriert werden.

Dieser Schritt wird nur angeboten, wenn auf der ersten Seite des Bereitstellungsassistenten die Optionen **E-Mail-Kanal** und **Verfolgung** ausgewählt sind. Siehe [Allgemeine Parameter](#general-parameters).

Ausführlichere Informationen zur Web-Verfolgung (Tracking-Modus, Erstellen und Einfügen von Tags...) finden Sie in [diesem Dokument](../../configuration/using/about-web-tracking.md).

### Grundprinzip {#operating-principle}

Wenn Sie die Verfolgung für eine Instanz aktivieren, werden die URLs in den Auslieferungen während des Sendens geändert, um die Verfolgung zu aktivieren.

* Die auf dieser Seite des Bereitstellungsassistenten eingegebenen Informationen zu externen URLs (ob sicher oder nicht) werden zum Erstellen der neuen URL verwendet. Zusätzlich zu diesen Informationen enthält der geänderte Link Folgendes: die IDs der Lieferung, der Empfänger und die URL.

   Die Verfolgungsinformationen werden von Adobe Campaign auf den/den Tracking-Servern erfasst, um die Empfängerprofile und die mit der Bereitstellung verknüpften Daten zu bereichern ( **[!UICONTROL Tracking]** Registerkarten).

   Informationen zu internen URLs werden nur vom Adobe Campaign-Anwendungsserver verwendet, um den/die Tracking-Server/s zu kontaktieren.

   For more on this, refer to [Tracking server](#tracking-server).

* Nachdem die URLs konfiguriert wurden, müssen Sie die Verfolgung aktivieren. Dazu muss die Instanz auf den/den Tracking-Servern registriert sein.

   For more on this, refer to [Saving tracking](#saving-tracking).

### Tracking-Server {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Um die Effizienz der Verfolgung in diesem Fall zu gewährleisten, müssen die folgenden Informationen angezeigt werden:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** und/oder **[!UICONTROL Secure external URL]** : Geben Sie die Umleitungs-URL ein, die in der zu sendenden E-Mail verwendet werden soll.
* **[!UICONTROL Internal URL(s)]** : URLs, die nur vom Adobe Campaign-Server verwendet werden, um mit den Tracking-Servern Kontakt aufzunehmen, um Protokolle zu sammeln und die URLs hochzuladen. Es ist nicht erforderlich, sie mit der Instanz zu verknüpfen.

   Wenn Sie keine URL angeben, wird die Tracking-URL standardmäßig verwendet.

Mit der Mid-Sourcing-Architektur können Sie das Tracking-Management externalisieren. Gehen Sie dazu wie folgt vor:

1. Wählen Sie die Option **[!UICONTROL Externalize tracking management]** : Dadurch können Sie einen Server mit mittlerer Quelle als Tracking-Server verwenden.
1. Füllen Sie die Felder **[!UICONTROL External account]** und **[!UICONTROL Instance name]** Felder aus, um eine Verbindung mit dem mid-sourcing-Server herzustellen.

   Weitere Informationen finden Sie unter [Mid-Sourcing-Server](../../installation/using/mid-sourcing-server.md).

1. Klicken Sie auf die **[!UICONTROL Enable the tracking instance]** Schaltfläche, um die Verbindung zum Server zu genehmigen.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Speichern der Verfolgung {#saving-tracking}

Sobald die URLs gefüllt sind, müssen Sie den Tracking-Server registrieren.

Klicken Sie auf den Link **Registrierung auf dem/den Tracking-Server(n)** und wählen Sie dann eine der verfügbaren Optionen aus.

![](assets/s_ncs_install_deployment_wiz_09.png)

Es gibt drei mögliche Architekturtypen zur Implementierung der Verfolgung:

1. **Unterstützung für die Verfolgung in einer vorhandenen Instanz hinzufügen**

   Diese Auswahl gilt, wenn die Instanz bereits für andere Anforderungen erstellt wurde (MTA-Server usw.). auf Servern, die als Tracking-Server verwendet werden.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Geben Sie das Kennwort für das **interne** Konto auf den Umleitungsservern ein, um die Verfolgungsinstanz zu konfigurieren.

   >[!NOTE]
   >
   >Wenn mehrere Tracking-Server verwendet werden, müssen sie alle denselben Namen und dasselbe Kennwort verwenden.

   Geben Sie den Namen der Instanz und das Kennwort ein.

1. **Neue Instanz für die Verfolgung erstellen**

   Diese Option ist nützlich, wenn Verfolgungsinstanzen für die Verfolgung reserviert sind und keine anderen Anwendungsmodule haben.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Geben Sie das Kennwort für das **interne** Konto auf den Umleitungsservern ein, um die Verfolgungsinstanz zu konfigurieren.

   >[!NOTE]
   >
   >Wenn mehrere Tracking-Server konfiguriert sind, müssen sie alle dasselbe Kennwort verwenden.

   Geben Sie den Namen der Instanz, das Kennwort und alle damit verbundenen DNS-Masken, z. B. **[!UICONTROL Campaign*]** an.

1. **Validieren einer bereits vorkonfigurierten Verfolgungsinstanz**

   Diese Option wird verwendet, wenn Sie nicht über das Kennwort für das **interne** Konto verfügen. In diesem Fall ist ein Verfolgungskonto für Sie auf den/den Tracking-Servern vorkonfiguriert. Geben Sie das Kennwort des Verfolgungskontos der Umleitungsserver ein, um die Verfolgungsinstanz zu validieren.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Geben Sie den Namen der zu validierenden Instanz an.

Klicken Sie auf **Genehmigen** , um den Aufzeichnungsvorgang mit dem Tracking-Server zu starten.

Im vorherigen Fenster wird die Registrierung auf der Ebene des Tracking-Servers durch eine Meldung bestätigt:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Die mit URL-Suchen verknüpften Parameter **dürfen bei einer Standardinstallation nicht geändert** werden. Für alle anderen Parameter wenden Sie sich bitte an Adobe.

## Parameter für mobile Kanäle {#mobile-channel-parameters}

Im nächsten Schritt können Sie Standardeinstellungen für Auslieferungen an Mobiltelefone (SMS und WAP Push) definieren.

>[!NOTE]
>
>Der Mobilkanal ist optional: dieser Schritt wird nur angezeigt, wenn er gekauft wurde. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Standardkonto für die SMS-Zustellung {#default-account-for-sms-delivery}

Folgende Angaben sind erforderlich:

* **[!UICONTROL Label]** : Geben Sie einen Namen für dieses SMS/Wap Push-Konto ein. Sie können beispielsweise den Namen Ihres Routers verwenden.
* Für die **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]** Felder: Wenden Sie sich für die erforderlichen Einstellungen an Ihren Service Provider.

### Parameter der gesendeten SMS {#parameters-of-sms-sent}

In der Dropdownliste **Priorität** : Wählen Sie &quot;Normal&quot;, &quot;Hoch&quot;oder &quot;Dringend&quot;, um sie auf die zu sendenden Nachrichten anzuwenden.

### Erweiterte Parameter {#advanced-parameters}

**Die** erweiterten Parameter... über den Link können Sie auf die Optionen für Wiederholung und Quarantäne zugreifen.

![](assets/s_ncs_install_deployment_wiz_13.png)

Informationen zu Wiederholungen finden Sie in den Feldern **Zeitraum der Wiederholungen** und **Anzahl der Wiederholungen** : Wenn ein Mobilgerät nicht erreichbar ist, wird das Programm in Abständen von mindestens 15 Minuten (für die maximale Auslieferungszeit) standardmäßig 5-mal wiederholt. Diese Werte können an Ihre Bedürfnisse angepasst werden.

In Bezug auf die Quarantäne stehen folgende Konfigurationsoptionen zur Verfügung:

* **[!UICONTROL Time between two significant errors]** : Geben Sie einen Standardwert ein (standardmäßig &quot;1d&quot;): Tag), um die Zeit zu definieren, die die Anwendung wartet, bevor der Fehlerzähler auf einen Fehler erhöht wird.
* **[!UICONTROL Maximum number of errors before quarantine]** : Sobald dieser Wert erreicht ist, wird die Mobiltelefonnummer unter Quarantäne gestellt (standardmäßig &quot;5&quot;: die Nummer wird beim sechsten Fehler in Quarantäne gestellt). Das bedeutet, dass der Kontakt automatisch von zukünftigen Lieferungen ausgeschlossen wird.

## Regionale Einstellungen {#regional-settings}

In dieser Phase können Sie Voreinstellungen für Datenrichtlinien einbeziehen.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Wenn diese Option aktiviert ist, wendet die Anwendung das internationale Format auf Telefonnummern an (das Länderpräfix ist dann obligatorisch, da die Anzahl der Ziffern vor der Formatierung nicht überprüft wird). Wenn diese Option nicht ausgewählt ist, müssen Sie der internationalen Telefonnummer das Präfix &quot;+&quot;oder &quot;00&quot;selbst voranstellen.
* **[!UICONTROL Store all phone numbers using the international format]** : Diese Option betrifft nur **inländische** Telefonnummern, die importiert oder bearbeitet werden. Legen Sie fest, ob Sie ein internes Format (z. B. 425 555 0150) oder ein internationales Format (z. B. +1 425 555 0150)

## Access from the Internet {#access-from-the-internet}

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

In diesem Schritt können Sie Zugriffs-URLs für im Internet veröffentlichte Adobe Campaign-Seiten definieren.

Sie müssen hier auch die Veröffentlichungsoptionen angeben, die mit Webformularen verknüpft sind.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Im Web angezeigte Server {#servers-exposed-on-the-web}

Verwenden Sie diese Seite, um die Server-URLs für Folgendes zu füllen:

1. Greifen Sie auf den im Internet angezeigten Anwendungsserver zu: Abonnement-/Abonnementformulare, Extranet usw.
1. Greifen Sie auf den Anwendungsserver zu, wenn Ressourcen nicht im Web bereitgestellt werden: Formulare, Intranet, Bestätigungsseiten.
1. Greifen Sie auf die Spiegelseiten der Auslieferungen zu.

   Eine Spiegelseite ist eine dynamische Seite, die den Inhalt der E-Mail anzeigt. Der Zugriff erfolgt über einen Link, der in die an den Empfänger gesendete Nachricht eingefügt wird und personalisierte Elemente enthalten kann. Die Spiegelseite gibt dem Empfänger die Möglichkeit, die Nachricht in einem Internetbrowser anstatt der E-Mail-Software zu lesen, unabhängig vom Lieferformat (Text oder HTML). Spiegelseiten werden jedoch nur für eine bestimmte Bereitstellung generiert, wenn der erforderliche HTML-Inhalt definiert wurde.

Mit Adobe Campaign können Sie zwischen diesen drei URLs unterscheiden, um die Belastung über mehrere Plattformen zu verteilen.

## Verwaltung öffentlicher Ressourcen {#managing-public-resources}

>[!CAUTION]
>
>Aus Datenschutzgründen empfehlen wir die Verwendung von HTTPS für alle externen Ressourcen.

Damit die Bilder von Empfängern gesehen werden können, müssen die in E-Mails und öffentlichen Ressourcen verwendeten Bilder, die mit Kampagnen verknüpft sind, auf einem extern zugänglichen Server gespeichert sein. Sie können dann externen Empfängern oder Operatoren zur Verfügung stehen.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Für diesen Schritt müssen Sie Folgendes eingeben:

1. Die neue URL der öffentlichen Ressource. Weitere Informationen finden Sie im Abschnitt [URL](#public-resources-url) öffentlicher Ressourcen.
1. Der Bilderkennungsmodus bei einer Bereitstellung. Weitere Informationen finden Sie im Abschnitt [Auslieferungsbilderkennung](#delivery-image-detection) .
1. Veröffentlichungsoptionen. For more information, refer to the [Publication modes](#publication-modes) section.

Öffentliche Ressourcen können über den Knoten **Administration > Ressourcen > Online > Öffentliche Ressourcen** in der Adobe Campaign-Struktur aufgerufen werden. Sie werden in einer Bibliothek gesammelt und können in E-Mails eingeschlossen, aber auch in Kampagnen oder Aufgaben sowie im Inhaltsmanagement verwendet werden.

![](assets/install_pub_resources_view.png)

### URL öffentlicher Ressourcen {#public-resources-url}

Im ersten Feld können Sie den Start der URL angeben, die für die Ressourcen nach dem Hochladen verwendet wird. Nach dem Hochladen sind die Ressourcen über diese neue URL verfügbar.

Bei einer Bereitstellung können Sie Bilder verwenden, die in der Bibliothek öffentlicher Ressourcen oder in einem anderen lokalen Bild oder Bild gespeichert sind, das auf einem Server gespeichert ist.

* Bei E-Mail-Bildern verwenden Sie die URL **https://** server **/res/img** .

   Dieser Wert kann bei jeder Bereitstellung überschrieben werden.

* Bei öffentlichen Ressourcen die URL **https://** server **/res/** instance ****, wobei **instance**der Name der Verfolgungsinstanz ist.

### Bilderkennung bereitstellen {#delivery-image-detection}

Bei einer Bereitstellung können Sie Bilder verwenden, die in der Bibliothek öffentlicher Ressourcen oder in einem anderen lokalen Bild oder Bild gespeichert sind, das auf einem Server gespeichert ist.

Mithilfe der **URL-Masken** für Felder können Sie die Liste der URL-Masken angeben, die beim automatischen Hochladen von Bildern übersprungen werden sollen. Wenn Sie beispielsweise Bilder verwenden, die auf einer von außen zugänglichen Site gespeichert sind, insbesondere auf einer Internetseite, können Sie die Site-URL in dieses Feld eingeben.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Sie können mehrere URL-Masken durch ein Komma voneinander trennen.

* Informationen zur Verwendung und Verwaltung von Bildern in E-Mails finden Sie in [diesem Abschnitt](../../delivery/using/defining-the-email-content.md#adding-images).
* Im Auslieferungsassistenten haben die von diesen URLs aufgerufenen Bilder den Status &quot;Ignoriert&quot;.

### Veröffentlichungsmodus {#publication-modes}

Im unteren Bereich des Assistenten können Sie die Veröffentlichungsoptionen öffentlicher Ressourcen und Bilder auswählen. Diese Optionen stehen auch für Webformulare und Umfragen zur Verfügung.

Die folgenden Veröffentlichungsmodi stehen zur Verfügung:

* Tracking-Server

   Die Ressourcen werden automatisch auf die verschiedenen Tracking-Server kopiert. Sie werden in der Schritt- [Verfolgungskonfiguration](#tracking-configuration)konfiguriert.

* Andere Adobe Campaign-Server

   Sie können einen weiteren Adobe Campaign-Server verwenden, auf den die Ressourcen kopiert werden.

   Serverseitig müssen Sie eine neue Instanz mit folgendem Befehl erstellen, um einen dedizierten Adobe Campaign-Server zu verwenden:

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   Geben Sie dann das Kennwort ein.

   Die Parameter der dedizierten Server werden in den **[!UICONTROL Media URL(s)]**- **[!UICONTROL Password]** und **[!UICONTROL Instance name]** -Feldern angegeben.

   ![](assets/s_ncs_install_images_upload_b.png)

* Manuelles Veröffentlichungsskript (nur für öffentliche Ressourcen)

   ![](assets/s_ncs_install_images_upload_c.png)

   Sie können die Bilder mithilfe eines Skripts veröffentlichen:

   * Sie müssen dieses Skript erstellen: Der Inhalt hängt von Ihrer Konfiguration ab.
   * Das Skript wird durch den folgenden Befehl aufgerufen:

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      wobei `[INSTALL]` der Zugriffspfad zum Adobe Campaign-Installationsordner ist.

   * Stellen Sie unter Unix sicher, dass das Skript ausführbar ist.

Für Bilder müssen sie aus dem Ordner &quot;images&quot;kopiert werden, der über die Option **NmsDelivery_ImageSubDirectory** angegeben wurde, und auf einen oder mehrere Frontalserver. Diese Server speichern die Bilder, damit sie über die neue konfigurierte URL zugänglich sind.

Im Falle der Veröffentlichung auf einem Adobe Campaign-Server ohne manuelles Veröffentlichungsskript werden die Bilder einer Bereitstellung standardmäßig im `$(XTK_INSTALL_DIR)/var/res/img/ directory`. Die entsprechende URL lautet: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. Die entsprechende URL lautet wie folgt: **`https://server/res/instance`** wobei instance der Name der Verfolgungsinstanz ist.

>[!NOTE]
>
>Es ist möglich, den Ordner des öffentlichen Ressourcenspeichers zu ändern. Weitere Informationen finden Sie unter [Verwaltung öffentlicher Ressourcen](#managing-public-resources).

### Synchronisieren öffentlicher Ressourcen {#synchronizing-public-resources}

Mit dieser Funktion können Sie öffentliche Ressourcen **auf mehreren Reserveservern** synchronisieren.

Wenn auf dem Tracking-Server keine öffentliche Ressource vorhanden ist oder die Ressource einen 404-Fehler zurückgibt, versucht der Tracking-Server, die Ressource auf einem der Reserveserver zu finden.

Das Deklarieren und Konfigurieren von Reserveservern muss in der Datei &quot; **serverConf.xml** &quot;des Marketing-Servers erfolgen. Alle in der Datei **serverConf.xml** verfügbaren Parameter sind in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md)aufgeführt.

**Erklärung**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Konfiguration**

Für jede zu synchronisierende öffentliche Ressource müssen Sie dem `<url>` Element im `<relay>` Teil ein Statusattribut hinzufügen:

Das Statusattribut kann einen von drei Werten haben:

* reserve: Die öffentlichen Mittel werden synchronisiert

* normal: Vorhandenes Verhalten (ohne Synchronisierung)

* schwarze Liste: Die URL wird auf eine schwarze Liste gesetzt, wenn der Fehler &quot;404&quot;zurückgegeben wird. Die Dauer (in Sekunden) der schwarzen Liste wird durch ein **timeout** -Attribut definiert, dessen Standardwert 60 s ist.

Die vordefinierte Konfiguration der Synchronisierung lautet:

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## Daten bereinigen {#purging-data}

In der letzten Phase des Bereitstellungsassistenten können Sie das automatische Bereinigen veralteter Daten konfigurieren. Die Werte werden in Tagen angegeben.

![](assets/s_ncs_install_deployment_wiz_16.png)

Daten werden automatisch über den Arbeitsablauf zur Datenbankbereinigung gelöscht. Weitere Informationen zur Konfiguration und zum Betrieb dieses Workflows sowie zu den gelöschten Elementen finden Sie in diesem [Dokument](../../production/using/database-cleanup-workflow.md).
