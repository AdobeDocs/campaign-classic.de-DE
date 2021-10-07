---
product: campaign
title: Integration mittels SOAP (Server-seitig)
description: Integration mittels SOAP (Server-seitig)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 100%

---

# Integration mittels SOAP (Server-seitig){#integration-via-soap-server-side}

![](../../assets/v7-only.svg)

Die für die Angebotsverwaltung verfügbaren SOAP-Webservices unterscheiden sich von den in Adobe Campaign gewöhnlich verwendeten. Sie sind über die im vorangehenden Kapitel beschriebene Interaction-URL zugänglich und ermöglichen es, ein Angebot für einen spezifischen Kontakt vorzuschlagen oder zu aktualisieren.

## Angebotsvorschläge {#offer-proposition}

Für Angebotsvorschläge über SOAP muss der Befehl **nms:proposition#Propose** hinzugefügt werden, gefolgt von im Anschluss erläuterten Parametern:

* **targetId** - Primärschlüssel des Kontakts (es kann sich um einen zusammengesetzten Schlüssel handeln).
* **maxCount** - gibt die Anzahl an Angebotsvorschlägen für den Kontakt an.
* **context** - erlaubt das Einfügen von Kontextdaten in das Platzierungsschema. Wenn das verwendete Schema **nms:interaction** lautet, sollte **`<empty>`** hinzugefügt werden.
* **categories** - bezeichnet die Kategorie, der die vorgeschlagenen Angebote angehören müssen.
* **themes** - bezeichnet die Themen, denen die vorgeschlagenen Angebote entsprechen müssen.
* **uuid** - Wert des permanenten Adobe-Campaign-Cookies (&quot;uuid230&quot;).
* **nlid** - Wert des Adobe-Campaign-Sitzungs-Cookies (&quot;nlid&quot;).
* **noProp** - Angabe des Werts &quot;true&quot;, wenn keine Vorschläge eingefügt werden sollen.

>[!NOTE]
>
>**targetId** und **maxCount** sind Pflichtparameter, die Angabe der anderen ist optional.

Als Antwort auf die Abfrage gibt der SOAP-Dienst folgende Parameter zurück:

* **interactionId** - Kennung der Interaktion.
* **propositions** - das die Liste der Vorschläge enthaltene XML-Element. Jeder Vorschlag verfügt über eine Kennung und eine spezifische HTML-Darstellung.

## Angebotsaktualisierung {#offer-update}

Ergänzen Sie die URL mit dem Befehl **nms:interaction#UpdateStatus** und folgenden Parametern:

* **proposition** - die die vom Angebotsmodul ausgegebene Vorschlagskennung enthaltende Zeichenkette. Siehe [Angebotsvorschläge](#offer-proposition).
* **status** - Zahl, die den neuen Status des Angebots angibt. Die möglichen Werte sind in der Auflistung **propositionStatus**, im Schema **nms:common** aufgeführt. Beispielsweise entspricht die Zahl 3 werksmäßig dem Status **Akzeptiert**.
* **context** - XML-Element, mit dem Sie Kontextdaten zum Platzierungsschema hinzufügen können. Wenn das verwendete Schema **nms:interaction** lautet, sollte **`<empty>`** hinzugefügt werden.

## Anwendungsbeispiel eines SOAP-Aufrufs {#example-using-a-soap-call}

Unten stehend ein Beispiel-Code eines SOAP-Aufrufs:

```
<%
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
      for each( var propHtml in props.proposition.*.mdSource )
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
