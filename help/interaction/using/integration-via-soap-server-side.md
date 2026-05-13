---
product: campaign
title: Integration mittels SOAP (Server-seitig)
description: Integration mittels SOAP (Server-seitig)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
TQID: https://experienceleague.adobe.com/-f0NEfvLKh0PfgkB-c4SiPUyQrGuKx55yXOBfmYMmHs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 326
ht-degree: 65%

---

# Integration mittels SOAP (Server-seitig){#integration-via-soap-server-side}



Die für die Angebotsverwaltung bereitgestellten SOAP-Web-Services unterscheiden sich von den in Adobe Campaign üblicherweise verwendeten. Sie können über die im vorherigen Abschnitt beschriebene Interaktions-URL aufgerufen werden, über die Sie Angebote für einen bestimmten Kontakt unterbreiten oder aktualisieren können.

## Angebotsvorschläge {#offer-proposition}

Fügen Sie für einen Angebotsvorschlag über SOAP den Befehl **nms:proposition#Propose** hinzu, gefolgt von den folgenden Parametern:

* **targetId** – Primärschlüssel des Kontakts (es kann sich um einen zusammengesetzten Schlüssel handeln).
* **maxCount** - gibt die Anzahl an Angebotsvorschlägen für den Kontakt an.
* **context** - erlaubt das Einfügen von Kontextdaten in das Platzierungsschema. Wenn das verwendete Schema &quot;**&quot;:interaction**, sollte **`<empty>`** hinzugefügt werden.
* **categories** - bezeichnet die Kategorie, der die vorgeschlagenen Angebote angehören müssen.
* **themes** - bezeichnet die Themen, denen die vorgeschlagenen Angebote entsprechen müssen.
* **uuid** - Wert des permanenten Adobe Campaign-Cookies (&quot;uuid230&quot;).
* **nlid** - Wert des Adobe Campaign-Sitzungs-Cookies (&quot;nlid&quot;).
* **noProp** - Angabe des Werts &quot;true&quot;, wenn keine Vorschläge eingefügt werden sollen.

>[!NOTE]
>
>Die Einstellungen **targetId** und **maxCount** sind obligatorisch. Die anderen sind optional.

Als Antwort auf die Abfrage gibt der SOAP-Dienst folgende Parameter zurück:

* **interactionId** - Kennung der Interaktion.
* **propositions** - das die Liste der Vorschläge enthaltene XML-Element. Jeder Vorschlag verfügt über eine Kennung und eine spezifische HTML-Darstellung.

## Angebotsaktualisierung {#offer-update}

Fügen Sie den **nms:interaction#UpdateStatus**-Befehl zur URL hinzu, gefolgt von diesen Parametern:

* **proposition** - die die vom Angebotsmodul ausgegebene Vorschlagskennung enthaltende Zeichenfolge. Siehe [Angebotsvorschläge](#offer-proposition).
* **status** - Zeichenfolge, die den neuen Status des Angebots angibt. Die möglichen Werte werden in der Auflistung **propositionStatus** im Schema **nms:common** aufgeführt. Beispielsweise entspricht die Zahl 3 werksmäßig dem Status **Akzeptiert**.
* **context** - XML-Element, mit dem Sie Kontextdaten zum Platzierungsschema hinzufügen können. Wenn das verwendete Schema &quot;**&quot;:interaction**, sollte **`<empty>`** hinzugefügt werden.

## Anwendungsbeispiel eines SOAP-Aufrufs {#example-using-a-soap-call}

Nachfolgend finden Sie Beispiel-Code für einen SOAP-Aufruf.

Hier ein URL-Beispiel:

```
http://<urlOfYourJSSP>?env=liveRcp&sp=<nameSpaceOfferSpace>&t=<targetID>
```

```
<%
  var env = request.getUTF8Parameter("env");
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.htmlSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
