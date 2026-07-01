---
product: campaign
title: Wichtige Aspekte bei der Verwaltung der Zustellbarkeit in Adobe Campaign Classic
description: Die wichtigsten zu überprüfenden Punkte beim Verwalten der Zustellbarkeit in Adobe Campaign
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
TQID: https://experienceleague.adobe.com/ZRai7Bd-IRaWUQQmkuUYwXhNXp2BI-B4k-4cGq1k6uk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 674
ht-degree: 100%

---

# Behebung von Problemen bei der Zustellbarkeit{#deliverability-faq}

Haben Sie ein Problem mit der Zustellbarkeit? Vielleicht finden Sie hier die Lösung.

## MX-Regelfehler {#mx-rule-error}

**Was bedeutet die Fehlermeldung &quot;Kontingent ausgeschöpft&quot;?**

Diese Meldung bedeutet, dass Sie das Limit für einen gewissen MX (Mail eXchanger) erreicht haben und warten müssen, bis Sie wieder eine E-Mail an diesen Anbieter senden können.

In Adobe Campaign gibt es eine Konfiguration für die Anzahl der E-Mails pro Stunde, die gesendet werden können. Bei dieser Konfiguration ist Vorsicht geboten, weil sich die in der Instanz definierte Anzahl nicht auf die Anzahl tatsächlich gesendeter E-Mails, sondern auf die mit den ISP erfolgten Verbindungen bezieht.

Das bedeutet, dass eine Verbindung eine MX-Regel verwenden kann, ohne erfolgreich eine E-Mail zu senden. In diesem Fall muss eine Konfiguration mit IP oder einer Domain von schwacher Reputation mehrere Verbindungen ausprobieren, bevor die E-Mail erfolgreich versendet wird. Für jeden Versuch wird eine Nachricht auf das stundenbasierte Kontingent angerechnet. Dadurch wird die Leistung der Marketing-Kampagne erheblich beeinträchtigt.

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

  Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](delivery-failures-quarantine.md#quarantine-vs-denylist).

* **Was bedeuten die unterschiedlichen Gründe für Quarantäne-Fehler?**

  Es gibt zehn mögliche Gründe: Unbestimmt, Unbekannter Nutzer, Ungültige Domain, Auf Blockierungsliste, Zurückgewiesen, Fehler ignoriert, Unerreichbar, Konto deaktiviert, Postfach voll, Nicht angemeldet.

  Weitere Informationen hierzu finden Sie unter [Funktionsweise der Quarantäneverwaltung](delivery-failures-quarantine.md).

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

  Durch Auswahl des entsprechenden Links können Sie die Details der Website aufrufen. Dann können Sie diese Website ersuchen, Ihre Website von der Blockierungsliste zu löschen.

  >[!NOTE]
  >
  >Das Verfahren zum Entfernen aus der Liste kann je nach Website variieren. Auf manchen Websites müssen Sie ein Konto erstellen, während andere nur die Angabe der IP-Adresse verlangen.
