---
product: campaign
title: Einfügen von Webtracking-Tags in Ihre Site
description: Erfahren Sie, wie Sie Webtracking-Tags in Ihre Site einfügen
feature: Configuration
role: Developer
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Einfügen von Webtracking-Tags in Ihre Site{#inserting-tags-in-your-site}

## Einfache Methode {#simple-method}

Bei dieser Methode wird ein HTTP-Aufruf an den Weiterleitungsserver gesendet, indem ein **`<img>`** HTML-Tag in den HTML-Quell-Code der Web-Seite eingefügt wird, die verfolgt werden soll.

>[!IMPORTANT]
>
>Diese Methode verwendet die vom Webbrowser gesendeten Cookies, um den Empfänger zu identifizieren, und ist nicht 100 % zuverlässig.

**Beispiel**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

Das eingefügte Tag kontaktiert den Weiterleitungsserver.

![](assets/d_ncs_integration_webtracking_structure2.png)

Wenn Sie eine Seite definieren, die in der Konsole verfolgt werden soll, können Sie ein Beispiel-Webtracking-Tag generieren, das Sie kopieren und in den Quell-Code Ihrer Web-Seite einfügen können.

Wenn Sie jedoch Tags vom Typ TRANSAKTION verwenden, müssen Sie das Beispiel-Tag mit JavaScript ändern, um die Transaktionsinformationen (Betrag, Anzahl der Elemente) und alle Informationen einzufügen, die durch ein Erweiterungsschema definiert sind.

### Statisches Einfügen von Tags {#static-insertion-of-tags}

Kopieren Sie zum Einfügen statischer Tags einfach die von der Konsole generierten oder manuell erstellten Tags und fügen Sie sie in die Quelle Ihrer Web-Seite ein.

**Beispiel**: Einfügen eines Webtracking-Tags auf einer Seite, auf der ein Formular angezeigt wird.

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

Einfügen eines Web-Tracking-Tags vom Typ TRANSACTION auf der Bestätigungsseite („amount.md„).

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

### Dynamische Erstellung von Webtracking-Tags {#dynamic-generation-of-web-tracking-tags}

Wenn Ihre Web-Seiten dynamisch generiert werden, können Sie das Web-Tracking-Tag zum Zeitpunkt der Seitenerstellung hinzufügen.

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

## Optimale Methode {#optimum-method-}

Wenn Sie die an den Weiterleitungsserver gesendeten Informationen steuern möchten, ist es am zuverlässigsten, die HTTP-Abfrage mithilfe einer Seitengenerierungssprache selbst synchron durchzuführen.

Die von Ihnen erstellte URL muss den unter (Webtracking[Tag: Definition) definierten Syntaxregeln &#x200B;](../../configuration/using/web-tracking-tag-definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>Weiterleitung und Webtracking verwenden Cookies. Es ist wichtig, dass sich der Webserver, der den synchronen HTTP-Aufruf ausführt, in derselben Domain wie der Weiterleitungsserver befindet. Die verschiedenen HTTP-Austausche müssen die Cookies „id“, „uuid“ und „uuid230“ übermitteln.

**Beispiel**: Dynamische Generierung in Java, bei der die Empfängerauthentifizierung die Kontonummer verwendet.

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
