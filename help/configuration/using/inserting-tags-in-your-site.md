---
product: campaign
title: Einfügen von Tags in Ihre Site
description: Einfügen von Tags in Ihre Site
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 5%

---

# Einfügen von Tags in Ihre Site{#inserting-tags-in-your-site}

![](../../assets/v7-only.svg)

## Einfache Methode {#simple-method}

Diese Methode besteht darin, einen HTTP-Aufruf an den Weiterleitungsserver zu senden, indem eine **`<img>`** HTML-Tag im HTML-Quellcode der Webseite, die Sie verfolgen möchten.

>[!IMPORTANT]
>
>Diese Methode verwendet die vom Webbrowser gesendeten Cookies, um den Empfänger zu identifizieren. Sie ist nicht zu 100 % zuverlässig.

**Beispiel**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

Das eingefügte Tag kontaktiert den Weiterleitungsserver.

![](assets/d_ncs_integration_webtracking_structure2.png)

Wenn Sie eine Seite definieren, die in der Konsole verfolgt werden soll, können Sie ein Beispiel-Webtrackingtag generieren, das kopiert und in den Quellcode Ihrer Webseite eingefügt wird.

Wenn Sie jedoch Tags vom Typ TRANSACTION verwenden, müssen Sie das Beispiel-Tag mit JavaScript ändern, um die Transaktionsinformationen (Menge, Anzahl der Elemente) und alle von einem Erweiterungsschema definierten Informationen einzufügen.

### Statisches Einfügen von Tags {#static-insertion-of-tags}

Um statische Tags einzufügen, kopieren Sie einfach die von der Konsole generierten oder manuell erstellten Tags und fügen Sie sie in die Quelle Ihrer Webseite ein.

**Beispiel**: Einfügen eines Webtrackingtags auf einer Seite, auf der ein Formular angezeigt wird.

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

Einfügen eines Webtrackingtags vom Typ TRANSACTION in die Bestätigungsseite (&quot;amount.md&quot;).

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

### Dynamische Generierung von Web-Tracking-Tags {#dynamic-generation-of-web-tracking-tags}

Wenn Ihre Webseiten dynamisch generiert werden, können Sie das Webtrackingtag zum Zeitpunkt der Seitenerstellung hinzufügen.

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

Wenn Sie die an den Weiterleitungsserver gesendeten Informationen steuern möchten, ist die zuverlässigste Möglichkeit, die HTTP-Abfrage synchron selbst mithilfe einer Sprache zur Seitenerstellung durchzuführen.

Die URL, die Sie erstellen, muss den in [Webtrackingtag: Definition](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>Umleitung und Webtracking verwenden Cookies. Es ist wichtig, dass sich der Webserver, der den synchronen HTTP-Aufruf durchführt, in derselben Domäne befindet wie der Umleitungsserver. Die verschiedenen HTTP-Austausche müssen die Cookies &quot;id&quot;, &quot;uuid&quot;und &quot;uuid230&quot;vermitteln.

**Beispiel**: Dynamische Generierung in Java, bei der die Empfängerauthentifizierung anhand der Kundennummer erfolgt.

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
