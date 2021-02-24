---
solution: Campaign Classic
product: campaign
title: Vorverarbeitung von Anweisungen für verfolgte URLs
description: Erfahren Sie mehr über die Anweisungen zur Vorverarbeitung, mit denen Sie die URL einer E-Mail als Skript festlegen und diese trotzdem nachverfolgen können.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Anweisungen zur Vorverarbeitung {#pre-processing-instructions}

Die &lt;%@-Anweisungen sind nicht JavaScript, diese Syntax ist spezifisch für Adobe Campaign.

Sie gelten nur im Zusammenhang mit Versänden. Es ist die einzige Möglichkeit, die URL einer E-Mail zu skripten und sie trotzdem nachverfolgen zu lassen (außer URL-Parametern). Sie können als automatische Kopieren/Einfügen während der Analyse des Versands betrachtet werden, bevor die zu verfolgenden Links erkannt werden.

Es gibt drei Arten von Anweisungen:

* &quot;**include**&quot;: hauptsächlich zum Factorisieren von Optionen, Gestaltungsbausteinen, externen Dateien oder Seiten.
* &quot;**value**&quot;: , um Zugriff auf die Felder des Versands, Versand- und benutzerdefinierte Objekte zu gewähren, die im Versand geladen werden
* &quot;**foreach**&quot;: zum Schleifen eines Arrays, das als benutzerdefiniertes Objekt geladen wird.

Sie können direkt vom Versand-Assistent getestet werden. Sie gelten für die Content-Vorschau und wenn Sie auf die Tracking-Schaltfläche klicken, um die Liste der URLs anzuzeigen.

## &lt;>{#<%@-include}

Die folgenden Beispiele gehören zu den am häufigsten verwendeten:

* Link Mirrorseite einschließen: `<%@ include view="MirrorPage" %>`
* Mirrorseiten-URL: &quot;Ansicht als `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* Vordefinierte Abmeldung-URL: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Weitere Beispiele:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Verwenden Sie die Personalisierungsschaltfläche im Versand-Assistent, um die richtige Syntax zu erhalten.

## &lt;%@ value {#<%@-value}

Diese Anweisung ermöglicht den Zugriff auf die Parameter der Lieferung, die für alle Empfänger konstant sind.

Syntax:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Dabei gilt:

* &quot;object&quot;: Name des Objekts (Beispiel: Lieferung, Anbieter usw.).
* &quot;xpath&quot;: xpath des Felds.
* &quot;index&quot; (optional): Wenn &quot;object&quot;ein Array ist (für zusätzliche Skriptobjekte), wird der Elementindex im Array (beginnt bei 0).

Objekt kann:

* *&quot;Lieferung&quot;: für die aktuelle Lieferung (siehe Details und Einschränkungen im Unterabschnitt unten).
* &quot;Anbieter&quot;: für den aktuellen Zustellanbieter/Routing (nms:externalAccount).
* Ein zusätzliches Skriptobjekt: wenn ein Objekt im Kontext über Folgendes geladen wird: **Properties** > **Personalisierung** > **Objekte im Ausführungskontext hinzufügen**.
* Element der foreach-Schleife: Siehe Abschnitt [Foreach](#<%@-foreach) unten.

### &quot;delivery&quot;-Objekt {#delivery-object}

Für die E-Mail-Personalisierung ist das Bereitstellungsobjekt auf zwei Arten verfügbar:

* In JavaScript. Beispiel: `<%= delivery.myField %>`.

   Im JavaScript-Objekt werden benutzerdefinierte Felder nicht unterstützt. Sie funktionieren in der Vorschau, aber nicht in der MTA, da die MTA nur auf das vordefinierte Bereitstellungsschema zugreifen kann.

* Durch die Vorverarbeitung `<%@ value object="delivery"`.

Für die `<%@ value object="delivery" xpath="@myCustomField" %>`-Anweisung gibt es eine weitere Einschränkung für Lieferungen, die über die Mitte-Sourcing gesendet werden. Das benutzerdefinierte Feld &quot;@myCustomField&quot;muss dem Schema &quot;nms:delivery&quot;auf Marketing- und Midsourcing-Plattformen hinzugefügt werden.

>[!NOTE]
>
>Verwenden Sie für Bereitstellungsparameter/Variablen die folgende Syntax (mithilfe des Bereitstellungsobjekts):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#<%@-value-in-javascript}

Damit &lt;%@-Wert in Skriptabschnitten verwendet werden kann, werden zwei spezielle Objekte durch &lt;% und %> ersetzt:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Beispiel:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#<%@-foreach}

Diese Anweisung ermöglicht die Iteration für ein Array von Objekten, die in die Bereitstellung geladen wurden, um einzelne Verknüpfungen zu den Objekten zu verfolgen.

Syntax:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Dabei gilt:

* &quot;object&quot;: Name des Objekts, von dem aus gestartet werden soll, normalerweise ein zusätzliches Skriptobjekt, kann aber eine Bereitstellung sein.
* &quot;xpath&quot;(optional): xpath der Sammlung, um sie zu wiederholen. Der Standardwert ist &quot;.&quot;, d. h., das Objekt ist das Array, das wiederholt werden soll.
* &quot;index&quot; (optional): wenn xpath nicht &quot;.&quot;ist. und object ist ein Array selbst, item index of object (beginnt bei 0).
* &quot;item&quot; (optional): Name eines neuen Objekts, auf das innerhalb der foreach-Schleife mit dem &lt;%@-Wert zugegriffen werden kann. Standard mit dem Verknüpfungsnamen im Schema.

Beispiel:

Laden Sie in den Bereitstellungseigenschaften/Personalisierung ein Array von Artikeln und eine Beziehungstabelle zwischen Empfänger und Artikeln.

Die Anzeige von Links zu diesen Artikeln kann einfach mit einem Javascript wie folgt erfolgen:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Mit dieser Lösung werden die Links zu allen Artikeln ohne Unterschied verfolgt. Sie können wissen, dass ein Empfänger auf einen Artikel-Link geklickt hat, aber Sie können nicht wissen, zu welchem Artikel.

Die Lösung lautet:

1. Laden Sie alle möglichen Artikel in ein zusätzliches Skript-Array der Lieferung - articleList[] -, was bedeutet, dass es eine begrenzte Anzahl von möglichen Artikeln geben muss.
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
1. Zeigen Sie den Artikel an, indem Sie die Funktion aufrufen.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

