---
solution: Campaign Classic
product: campaign
title: '"Webtrackingtag: Definition"'
description: '"Webtrackingtag: Definition"'
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 6%

---


# Webtrackingtag: Definition{#web-tracking-tag-definition}

Ein Web-Trackingtag ist einfach eine URL, die mit den entsprechenden Parametern erstellt und über eine HTTP-Abfrage an den Umleitungsserver gesendet wird.

## Format der zu sendenden Daten {#format-of-the-data-to-be-sent}

Das Format einer Web-Tracking-URL lautet wie folgt: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Die der URL hinzugefügte Zufallszahl vermeidet Probleme, die durch das Zwischenspeichern von Webseiten in Browsern verursacht werden.

Die folgende Tabelle enthält eine Liste von speziellen Parametern, die vom Umleitungsserver unterstützt werden.

<table>
                     <thead>
                        <tr>
                           <th>Name</th>
                           <th>Typ</th>
                           <th>Beschreibung </th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>Sitzungs-Cookie</p> 
                           </td>
                           <td>
                              <p>Versand-ID und Empfänger-ID.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>Ständiges Cookie</p> 
                           </td>
                           <td>
                              <p>Empfänger-ID (nützlich, wenn Sitzungs-Cookie fehlt).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>URL-Parameter</p> 
                           </td>
                           <td>
                              <p>Bezeichner der verfolgten Webseite: dies ist der einzige obligatorische Parameter.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>URL-Parameter</p> 
                           </td>
                           <td>
                              <p>Versand-ID, die verwendet wird, wenn kein Sitzungs-Cookie vorhanden ist. Dieser Wert ist als Hexadezimalwert anzugeben.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL-Parameter</p> 
                           </td>
                           <td>
                              <p>Parameter zur Identifizierung des Internetbenutzers. Das Format dieses Parameters ist "name=value", wobei der Name ein Schema des Empfängers ist. Dieser Parameter hat Vorrang vor der Kennung im Sitzungs-Cookie.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Einige Web-Tracking-URLs**

* Besuch einer Homepage mit Identifikatoren

   **https://myserver.adobe.com/r/9862?tagid=home**

* Erfassen von Daten zum Geschäftsvolumen

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Festlegen eines Felds zum Suchen des Empfängers

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Ein Empfänger mit einer Kontonummer von 10 wird an die Startseite gesendet.

* Verwenden eines Standard-Versands

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Ein Empfänger wird an die Startseite gesendet. Diese Informationen werden im Versand mit dem Bezeichner 230 (e6 in Datenbank 16) gespeichert, es sei denn, mit dieser Abfrage wird ein Sitzungscookie mit einem Versand-Bezeichner gesendet.

>[!NOTE]
>
>Alle Werte, die über URL-Parameter an den Umleitungsserver gesendet werden, müssen URL-kodiert sein. Beachten Sie in den angegebenen Beispielen, dass die Zeichen &#39;=&#39; und &#39;|&#39; als &#39;%3D&#39; bzw. &#39;%7C&#39; kodiert sind.

## Datenübertragungsmethoden {#data-transmission-methods}

Folgende Methoden sind möglich:

* Einfügen der URL in das **&quot;src&quot;** -Attribut eines HTML- **`<img>`** Tags, das in die Webseite eingefügt wurde, die Sie verfolgen möchten.
* Direktaufruf an den Umleitungsserver, wenn die Webseite, die Sie verfolgen möchten, generiert wird.

