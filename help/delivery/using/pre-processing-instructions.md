---
solution: Campaign Classic
product: campaign
title: Anweisungen zur Vorab-Bearbeitung von getrackten URLs
description: Erfahren Sie mehr über Anweisungen zur Vorab-Bearbeitung, mit denen Sie die URL einer E-Mail skripten und dennoch tracken können.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 7a58da8fd20abbff9dcf8361536310de49a7905f
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 80%

---


# Anweisungen zur Vorab-Bearbeitung {#pre-processing-instructions}

Sie können eine bestimmte Syntax im Inhalt des Versands verwenden, um Anweisungen hinzuzufügen und die URL der verfolgten E-Mail zu skripten. Die &lt;%@-Anweisungen sind nicht JavaScript: Diese Syntax ist spezifisch für Adobe Campaign.

Sie gelten nur im Zusammenhang mit dem Versandinhalt. Dies ist die einzige Möglichkeit, die URL einer E-Mail zu skripten und dennoch zu tracken (neben URL-Parametern). Sie können als ein automatisches Kopieren/Einfügen betrachtet werden, das während der Versandanalyse angewendet wird, bevor die zu trackenden Links erkannt werden.

Es gibt drei Arten von Anweisungen:

* **[!DNL include]**: hauptsächlich um Code in Optionen, Gestaltungsbausteinen, externen Dateien oder Seiten hervorzuheben. [Mehr dazu](#include)
* &quot;**[!DNL value]**&quot;: , um Zugriff auf die Felder des Versands, Versand- und benutzerdefinierte Objekte zu gewähren, die im Versand geladen werden. [Mehr dazu](#value)
* &quot;**[!DNL foreach]**&quot;: um ein Array zu wiederholen, das als benutzerdefiniertes Objekt geladen wird. [Mehr dazu](#foreach)

Sie können direkt vom Versand-Assistenten aus getestet werden. Sie gelten in der Inhaltsvorschau und wenn Sie auf die Tracking-Schaltfläche klicken, um die Liste der URLs anzuzeigen.

## [!DNL include] {#include}

Die folgenden Beispiele gehören zu den am häufigsten verwendeten:

* Link zur Mirror-Seite einschließen:

   ```
   <%@ include view="MirrorPage" %>  
   ```

* URL der Mirrorseite:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* Vordefinierte Abmelde-URL:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* Weitere Beispiele:

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   Verwenden Sie die Personalisierungsschaltfläche im Versand-Assistenten, um die richtige Syntax zu erhalten.

## [!DNL value] {#value}

Diese Anweisung ermöglicht den Zugriff auf die Parameter des Versands, die für alle Empfänger gleich sind.

Syntax:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

Wobei:

* **[!DNL object]**: Name des Objekts (Beispiel: Versand, Anbieter usw.).
Objekt kann sein:
   * &quot;delivery&quot;: für den aktuellen Versand (siehe Details und Einschränkungen im Unterabschnitt unten).
   * &quot;provider&quot;: für den aktuellen Versand-Provider/Routing (nms:externalAccount).
   * Ein zusätzliches Skriptobjekt: wenn ein Objekt im Kontext geladen wird: **Eigenschaften** > **Personalisierung** > **Objekte im Ausführungskontext hinzufügen**.
   * Element der foreach-Schleife: siehe Abschnitt [Foreach](#foreach) weiter unten.
* **[!DNL xpath]**: xpath des Felds.
* **[!DNL index]** (optional): Wenn  **[!DNL object]** es sich um ein Array handelt (für zusätzliche Skriptobjekte), Elementindex im Array (Beginn bei 0).

### [!DNL delivery] object {#delivery-object}

Für die E-Mail-Personalisierung kann auf zwei Arten auf das &quot;delivery&quot;-Objekt zugegriffen werden:

* JavaScript verwenden:

   ```
   <%= delivery.myField %>`.
   ```

   Im Objektversand in JavaScript werden benutzerdefinierte Felder nicht unterstützt. Sie funktionieren in der Vorschau, jedoch nicht im MTA, da der MTA nur auf das vorkonfigurierte Versandschema zugreifen kann.

* Vorverarbeitung:

   ```
   <%@ value object="delivery"
   ```


>[!NOTE]
>
>* Bei der Anweisung `<%@ value object="delivery" xpath="@myCustomField" %>` gibt es eine weitere Einschränkung für Sendungen, die über Mid-Sourcing gesendet werden. Das benutzerdefinierte Feld &quot;@myCustomField&quot; muss dem Schema &quot;nms:delivery&quot; auf Marketing- und Mid-Sourcing-Plattformen hinzugefügt werden.
   >
   >
* Verwenden Sie für Versandparameter/-variablen die folgende Syntax (unter Verwendung des &quot;delivery&quot;-Objekts):
>
>
`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### [!DNL value] in einem Javascript-Abschnitt  {#value-in-javascript}

Damit der Wert &lt;%@ in Javascript-Abschnitten verwendet werden kann, werden zwei Sonderobjekte durch &lt;% und %> ersetzt:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Beispiel:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Diese Anweisung ermöglicht die Iteration eines Arrays von Objekten, die im Versand geladen werden, um einzelne Links zu den Objekten zu verfolgen.

Syntax:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

Wobei:

* **[!DNL object]**: Name des Objekts, von dem aus gestartet werden soll, normalerweise ein zusätzliches Skriptobjekt, es kann sich jedoch auch um einen Versand handeln.
* **[!DNL xpath]** (optional): xpath der Sammlung, die als Schleife verwendet werden soll. Der Standardwert ist &quot;.&quot;, d. h., das Objekt ist das Array, über das eine Schleife ausgeführt werden soll.
* **[!DNL index]** (optional): wenn &quot;xpath&quot; nicht &quot;.&quot; und &quot;object&quot; selbst ein Array ist, Elementindex des Objekts (beginnt bei 0).
* **[!DNL item]** (optional): Name eines neuen Objekts, auf das mit dem Wert &quot;&lt;%@&quot; innerhalb der foreach-Schleife zugegriffen werden kann. Standardeinstellung mit dem Link-Namen im Schema.

Beispiel:

Laden Sie in den Versandeigenschaften/der Versandpersonalisierung ein Array von Artikeln und eine Beziehungstabelle zwischen Empfänger und Artikeln.

Die Anzeige von Links zu diesen Artikeln kann mit einem JavaScript wie folgt erfolgen:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Bei dieser Lösung werden die Links zu allen Artikeln ohne Differenzierung verfolgt. Sie können zwar wissen, dass ein Empfänger auf einen Artikel-Link geklickt hat, aber Sie können nicht wissen, auf welchen Artikel.

Die Lösung ist:

1. Laden Sie alle möglichen Artikel in einem zusätzlichen Skript-Array des Versands – articleList[] – vorab, was bedeutet, dass eine endliche Anzahl möglicher Artikel vorhanden sein muss.
1. Schreiben Sie eine JavaScript-Funktion am Anfang des Inhalts.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```
1. Zeigen Sie den Artikel durch Aufruf der Funktion an.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

