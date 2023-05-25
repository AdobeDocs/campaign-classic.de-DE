---
product: campaign
title: Erste Schritte mit dem Tracking personalisierter Links
description: Erfahren Sie, wie Sie in Campaign Links in E-Mails schreiben, die personalisiert werden können und das Tracking unterstützen.
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: ht
source-wordcount: '218'
ht-degree: 100%

---

# Erste Schritte mit dem Tracking personalisierter Links {#tracking-personalized-links}



Die Links in E-Mail-Inhalten, die eine Personalisierung enthalten, benötigen eine bestimmte Syntax, um nachverfolgt zu werden.

Durch die Verwendung von JavaScript in E-Mail-Inhalten (HTML oder Text) können Sie dynamische Inhalte mit zwei Einschränkungen generieren und an die Empfänger senden:

* Das Script kann nicht direkt auf die Datenbank zugreifen (SQL-Funktion und API-Funktionen sind nicht verfügbar),
* Adobe Campaign muss zum Tracken von Links URLs erkennen können. [Mehr dazu](detecting-tracking-urls.md)

Sie können spezifische Anweisungen zur Vorab-Bearbeitung hinzufügen, um die URL zu skripten und zu tracken. [Mehr dazu](pre-processing-instructions.md)

Zur Tracking-Erkennung bettet Adobe Campaign [Tidy](https://www.html-tidy.org/) ein, um die HTML-Quelle zu analysieren und das Muster zu erkennen. Es werden alle URLs des Inhalts aufgelistet, damit sie einzeln verfolgt werden können. Adobe Campaign verwendet wiederum Tidy, um die URL (`http://myurl.com`) durch eine URL zu ersetzen, die auf den Weiterleitungs-Server von Adobe Campaign verweist.

Zum Beispiel wird im ursprünglichen Inhalt `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` für einen bestimmten Empfänger durch `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName` ersetzt. 

Wobei:

* &quot;h&quot; bedeutet HTML-Inhalt (oder &quot;t&quot; für Textinhalte).
* 617791 ist die Nachrichtenkennung/BroadLog-Kennung (hexadezimal).
* 71ffa3 ist die NmsDelivery-Kennung (hexadezimal).
* 71ffa8 ist die NmsTrackingUrl-Kennung (hexadezimal).
* p1, p2 usw. sind alle Parameter, die in der URL ersetzt werden sollen.
