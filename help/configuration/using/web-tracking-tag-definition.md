---
product: campaign
title: Webtracking-Tag definieren
description: Webtracking-Tag definieren
feature: Application Settings
role: Data Engineer, Developer
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 4%

---

# Webtracking-Tag: Definition{#web-tracking-tag-definition}



Ein Webtracking-Tag ist lediglich eine URL, die mit den entsprechenden Parametern erstellt und über eine HTTP-Abfrage an den Weiterleitungs-Server gesendet wird.

## Format der zu sendenden Daten {#format-of-the-data-to-be-sent}

Eine Webtracking-URL hat folgendes Format: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Durch die zur URL hinzugefügte Zufallszahl werden Probleme vermieden, die durch Browser beim Zwischenspeichern von Web-Seiten verursacht werden.

In der folgenden Tabelle sind die vom Weiterleitungs-Server unterstützten Parameter aufgeführt.

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
                              <p>Versand-ID und Empfänger-ID.</p> 
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
                              <p>Empfängerkennung (nützlich, wenn Sitzungs-Cookie fehlt).</p> 
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
                              <p>Kennung der getrackten Web-Seite: Dies ist der einzige obligatorische Parameter.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>Arbeitshilfe</p> 
                           </td>
                           <td>
                              <p>URL-Parameter</p> 
                           </td>
                           <td>
                              <p>Versandkennung, die verwendet werden soll, wenn kein Sitzungs-Cookie vorhanden ist. Dieser Wert soll sein
                                 Wird im Hexadezimalsystem ausgedrückt.
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
                              <p>Parameter zur Identifizierung des Internetbenutzers. Das Format dieses Parameters ist „name=value“,
                                 wobei der Name ein Feld des Empfängerschemas ist. Dieser Parameter hat Vorrang vor
                                 Die im Sitzungs-Cookie enthaltene Kennung.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Einige Webtracking-URLs**

* Besuch einer „Homepage“-Kennungsseite

  **https://myserver.adobe.com/r/9862?tagid=home**

* Erfassen von Daten zum Geschäftsvolumen

  **https://myserver.adobe.com/r/4567?tagid=command&amount=100&article=2l**

* Feld angeben, um den Empfänger zu finden

  **https://myserver.adobe.com/r/2353?tagid=home&rcpid=saccount%3D10**

  Ein Empfänger mit der Kontonummer 10 wird auf die Startseite gesendet.

* Standardversand verwenden

  **https://myserver.adobe.com/r/2456?tagid=home&jobid=e6**

  Ein Empfänger wird zur Startseite weitergeleitet. Diese Informationen werden im Versand mit der Kennung 230 (e6 in der Datenbank 16) gespeichert, es sei denn, mit dieser Abfrage wird ein Sitzungs-Cookie mit einer Versandkennung gesendet.

>[!NOTE]
>
>Alle Werte, die über URL-Parameter an den Weiterleitungs-Server gesendet werden, müssen URL-kodiert sein. Beachten Sie in den angegebenen Beispielen, dass die Zeichen &#39;=&#39; und &#39;|&#39; als &#39;%3D&#39; bzw. &#39;%7C&#39; kodiert sind.

## Verfahren zur Datenübertragung {#data-transmission-methods}

Die folgenden Methoden sind möglich:

* Einfügen der URL in das **„src“**-Attribut eines HTML **`<img>`**-Tags, das in die zu verfolgende Webseite integriert ist.
* Direkter Aufruf an den Weiterleitungsserver, wenn die zu verfolgende Web-Seite generiert wird.
