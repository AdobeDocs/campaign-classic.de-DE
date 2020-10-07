---
title: Einfügen von Tags in Ihre Site
seo-title: Einfügen von Tags in Ihre Site
description: Einfügen von Tags in Ihre Site
seo-description: null
page-status-flag: never-activated
uuid: e5e4a431-2093-4d5a-acd2-0040b6ce3519
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 57988b00-62cc-43d3-a2eb-bfed5bff7dc1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 6%

---


# Einfügen von Tags in Ihre Site{#inserting-tags-in-your-site}

## Einfache Methode {#simple-method}

Diese Methode besteht darin, einen HTTP-Aufruf an den Umleitungsserver zu senden, indem ein **`<img>`** HTML-Tag in den HTML-Quellcode der Webseite eingefügt wird, die Sie verfolgen möchten.

>[!IMPORTANT]
>
>Diese Methode verwendet die vom Webbrowser gesendeten Cookies zur Identifizierung des Empfängers und ist nicht hundertprozentig zuverlässig.

**Beispiel**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

Das eingefügte Tag kontaktiert den Weiterleitungsserver.

![](assets/d_ncs_integration_webtracking_structure2.png)

Wenn Sie eine Seite definieren, die in der Konsole verfolgt werden soll, können Sie einen Beispiel-Web-Trackingtag generieren, der kopiert und in den Quellcode Ihrer Webseite eingefügt wird.

Wenn Sie TRANSACTION-Tags verwenden, müssen Sie das Beispiel-Tag jedoch mit JavaScript ändern, um die Transaktionsinformationen (Anzahl, Anzahl der Elemente) und alle von einem Erweiterungsschema definierten Informationen einzufügen.

### Statische Einfügung von Tags {#static-insertion-of-tags}

Um statische Tags einzufügen, kopieren Sie einfach die von der Konsole erzeugten oder manuell erstellten Tags in die Quelle Ihrer Webseite.

**Beispiel**: Einfügen eines Web-Trackingtags auf einer Seite, auf der ein Formular angezeigt wird.

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

Einfügen eines TRANSACTION-Trackingtags in die Bestätigungsseite (&quot;amount.md&quot;).

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### Dynamische Erstellung von Web-Trackingtagen {#dynamic-generation-of-web-tracking-tags}

Wenn Ihre Webseiten dynamisch generiert werden, können Sie den Web-Trackingtag zur Seitengenerierung hinzufügen.

**Beispiel**: Webtracking zu JSPs hinzugefügt.

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## Optimum-Methode {#optimum-method-}

Wenn Sie die an den Umleitungsserver gesendeten Informationen steuern möchten, ist die zuverlässigste Möglichkeit, die HTTP-Abfrage selbst synchron mit einer Seitenerstellungssprache durchzuführen.

Die URL, die Sie erstellen, muss den in [Webtrackingtag definierten Syntaxregeln entsprechen: Definition](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>Für Umleitung und Webverfolgung werden Cookies verwendet. Es ist wichtig, dass sich der Webserver, der den synchronen HTTP-Aufruf durchführt, in derselben Domäne befindet wie der Umleitungsserver. Die verschiedenen HTTP-Austausche müssen die Cookies &quot;id&quot;, &quot;uuid&quot;und &quot;uuid230&quot;enthalten.

**Beispiel**: Dynamische Generierung in Java mit Empfänger-Authentifizierung unter Verwendung ihrer Kontonummer.

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```

