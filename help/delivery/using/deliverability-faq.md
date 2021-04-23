---
solution: Campaign Classic
product: campaign
title: Wichtige Aspekte bei der Verwaltung der Zustellbarkeit in Adobe Campaign Classic
description: Welche Hauptaspekte sind bei der Verwaltung der Zustellbarkeit in Adobe Campaign Classic zu beachten?
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '671'
ht-degree: 100%

---

# Behebung von Problemen bei der Zustellbarkeit{#deliverability-faq}

Haben Sie ein Problem mit der Zustellbarkeit? Möglicherweise finden Sie hier eine Lösung.

## MX-Regelfehler {#mx-rule-error}

**Was bedeutet die Fehlermeldung &quot;Kontingent ausgeschöpft&quot;?**

Diese Meldung bedeutet, dass Sie das Limit für einen gewissen MX (Mail eXchanger) erreicht haben und warten müssen, bis Sie wieder eine E-Mail an diesen Anbieter senden können.

In Adobe Campaign gibt es eine Konfiguration bezüglich der Anzahl an E-Mails, die pro Stunde gesendet werden können. Bei dieser Konfiguration ist Vorsicht geboten, weil sich die in der Instanz definierte Anzahl nicht auf die Anzahl tatsächlich gesendeter E-Mails, sondern auf die mit den ISP erfolgten Verbindungen bezieht.

Das heißt, eine Verbindung kann sich einer MX-Regel bedienen, ohne dass der erfolgreiche Versand einer E-Mail erfolgt. In diesem Fall muss eine Konfiguration mit IP oder einer Domain von schwacher Reputation mehrere Verbindungen ausprobieren, bevor die E-Mail erfolgreich versendet wird. Bei jedem Versuch wird ein Guthaben vom Typ &quot;Nachrichten pro Stunde&quot; verbraucht. Dadurch wird die Leistung von Marketingkampagnen stark beeinflusst.

Somit ist &quot;Kontingente ausgeschöpft&quot; nicht nur eine Frage der Konfiguration, sondern kann auch mit der Reputation zusammenhängen. Fehlermeldungen im [SMTP-Protokoll](../../production/using/monitoring-processes.md#smtp-errors-per-domain) sollten unbedingt analysiert werden.

Weiterführende Informationen zur MX-Konfiguration finden Sie in [diesem Abschnitt](../../installation/using/email-deliverability.md#mx-configuration).

## Gleiche Fehlermeldung bei einem ISP {#same-error-for-an-isp}

**Warum erhalte ich bei einem bestimmten ISP immer dieselbe Fehlermeldung?**

Wenn Sie bei einem ISP immer dieselbe Fehlermeldung erhalten, hat der ISP möglicherweise festgestellt, dass Ihre E-Mail- oder IP-Adresse fehlerhaft ist. Wir empfehlen in diesem Fall folgende Schritte:
* Prüfen Sie, ob Sie eine große Menge an Fehlschlägen in Verbindung mit nicht bestehenden E-Mail-Adressen erhalten (**Unbekannter Nutzer**).
* Aktualisieren Sie Ihre Anmeldeformulare und achten Sie auf etwaige Fehler im Domain-Namen (z. B. gmaul.com oder yaho.com).
* Wenn Fehlermeldungen auftreten, die Ihre E-Mails als Spam einstufen, oder wenn Ihre E-Mails blockiert werden, versuchen Sie, alle Empfänger auszuschließen, die innerhalb von 12 Monaten ab dem Versand ihre E-Mail nicht geöffnet oder darauf geklickt haben.

Wenn das Problem fortbesteht, kontaktieren Sie die entsprechenden kommerziellen Dienstleister, Zustellbarkeitsdienste oder die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Blockierungsliste versus Quarantäne {#denylist-versus-quarantine}

* **Was ist der Unterschied zwischen einer E-Mail-Adresse auf einer Blockierungsliste und einer E-Mail-Adresse in Quarantäne?**

   * Der Status **[!UICONTROL Auf Blockierungsliste]** ist das Ergebnis einer Feedback-Schleife (wenn ein Empfänger eine E-Mail als Spam meldet).

   * Der Status **[!UICONTROL In Quarantäne]** ist das Ergebnis eines Soft- oder Hardbounce.
   Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist).

* **Was bedeuten die unterschiedlichen Gründe für Quarantäne-Fehler?**

   Es gibt zehn mögliche Gründe: Unbestimmt, Unbekannter Nutzer, Ungültige Domain, Auf Blockierungsliste, Zurückgewiesen, Fehler ignoriert, Unerreichbar, Konto deaktiviert, Postfach voll, Nicht angemeldet.

   Weitere Informationen hierzu finden Sie unter [Funktionsweise der Quarantäneverwaltung](../../delivery/using/understanding-quarantine-management.md).

## Aus Blockierungsliste entfernen {#remove-from-denylist}

* **Einer meiner Empfänger wurde versehentlich der Blockierungsliste hinzugefügt. Wie kann ich ihn aus der Blockierungsliste entfernen, damit ich ihm wieder Nachrichten senden kann?**

   * Gehen Sie zu **[!UICONTROL Administration > Kampagnenverwaltung > Unzustellbarkeitsverwaltung > Adressen unzustellbarer Sendungen]**.
   * Setzen Sie in den Details des entsprechenden Datensatzes den Wert des **[!UICONTROL Status]**-Feldes auf **[!UICONTROL Gültig]**.
   * Speichern Sie die Daten.

* **Wie kann ich feststellen, ob eine meiner IP-Adressen auf einer Blockierungsliste steht? Wie kann ich meine IP-Adresse(n) wieder aus der Blockierungsliste entfernen?**

   Um festzustellen, ob Ihre IP-Adresse auf einer Blockierungsliste steht, können Sie verschiedene Websites verwenden, um sie zu überprüfen, z. B.:
   * [MX Toolbox](https://mxtoolbox.com/)
   * [Wie lautet meine IP-Adresse?](https://whatismyipaddress.com)

   Nach der IP-Adressen-Prüfung erhalten Sie eine Liste mit Details zur Blockierungsliste und auch den Namen der Website, von der die IP-Adresse auf die Blockierungsliste gesetzt wurde.

   Durch Anklicken des entsprechenden Links können Sie die Details der Website aufrufen. Dann können Sie diese Website ersuchen, Ihre Website von der Blockierungsliste zu löschen.

   >[!NOTE]
   >
   >Dieser Prozess ist je nach Website unterschiedlich. Auf manchen Websites müssen Sie ein Konto erstellen, während andere nur die Angabe der IP-Adresse verlangen.
