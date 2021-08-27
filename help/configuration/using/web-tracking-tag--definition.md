---
product: campaign
title: '"Webtracking-Tag: Definition"'
description: '"Webtracking-Tag: Definition"'
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 6%

---

# Webtracking-Tag: Definition{#web-tracking-tag-definition}

![](../../assets/v7-only.svg)

Ein Webtrackingtag ist einfach eine URL, die mit den entsprechenden Parametern erstellt und über eine HTTP-Abfrage an den Weiterleitungsserver gesendet wird.

## Format der zu sendenden Daten {#format-of-the-data-to-be-sent}

Das Format einer Web-Tracking-URL lautet wie folgt: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Die der URL hinzugefügte Zufallszahl vermeidet Probleme, die durch das Zwischenspeichern von Webseiten in Browsern verursacht werden.

Die folgende Tabelle enthält eine Liste von speziellen Parametern, die vom Weiterleitungsserver unterstützt werden.

<table>
                     <thead>
                        <tr>
                           <th>Name</th>
                           <th>Typ</th>
                           <th>Beschreibung</th> 
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
                              <p>Versandkennung und Empfänger-ID.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>Permanentes Cookie</p> 
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
                              <p>Kennung der verfolgten Webseite: Dies ist der einzige obligatorische Parameter.</p> 
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
                              <p>Die Versandkennung, die verwendet wird, wenn kein Sitzungs-Cookie vorhanden ist. Dieser Wert muss
                                 in Hexadezimalzahl ausgedrückt.
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
                              <p>Parameter zur Identifizierung des Internetbenutzers. Das Format dieses Parameters ist "name=value",
                                 wobei der Name ein Feld des Empfängerschemas ist. Dieser Parameter hat Vorrang vor
                                 die im Sitzungs-Cookie enthaltene Kennung.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Einige Web-Tracking-URLs**

* Besuch einer Homepage-Identifizierungsseite

   **https://myserver.adobe.com/r/9862?tagid=home**

* Erfassen von Daten zum Geschäftsvolumen

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Auswahl eines Empfängerfelds

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   Ein Empfänger mit einer Kontonummer von 10 wird an die Startseite gesendet.

* Standardversand verwenden

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   Ein Empfänger wird an die Startseite gesendet. Diese Informationen werden im Versand mit der Kennung 230 (e6 in Datenbank 16) gespeichert, es sei denn, mit dieser Abfrage wird ein Sitzungs-Cookie mit einer Versandkennung gesendet.

>[!NOTE]
>
>Alle Werte, die über URL-Parameter an den Weiterleitungsserver gesendet werden, müssen URL-codiert sein. Beachten Sie in den Beispielen, dass die Zeichen &#39;=&#39; und &#39;|&#39; als &#39;%3D&#39; bzw. &#39;%7C&#39; kodiert sind.

## Datenübertragungsmethoden {#data-transmission-methods}

Die folgenden Methoden sind möglich:

* Einfügen der URL in das Attribut **&quot;src&quot;** eines HTML **`<img>`**-Tags, das in die Webseite eingefügt wurde, die Sie verfolgen möchten.
* Direkter Aufruf an den Weiterleitungsserver, wenn die Webseite, die Sie verfolgen möchten, generiert wird.
