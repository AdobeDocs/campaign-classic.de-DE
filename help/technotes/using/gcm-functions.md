---
product: campaign
title: Neue GCM-basierte Funktionen
description: Neue GCM-basierte Funktionen
feature: Technote
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 2%

---

# GCM-basierte Funktionen {#new-functions}

Um die Sicherheit zu verbessern, haben wir die Verwendung des AES-Algorithmus (Advanced Encryption Standard) mit CBC-Modus (Cipher Block Chaining) für kryptografische Vorgänge verworfen. Neue Verschlüsselungsfunktionen wurden eingeführt. Diese Funktionen verwenden AES mit dem Galois/Counter-Modus (AES-GCM) und bieten so eine sicherere Alternative. Diese Funktionen sind in JavaScript, JSP, SOAP-APIs und XML-Schemata verfügbar, sodass Kunden zur Verschlüsselung und Entschlüsselung von CBC zu GCM wechseln können.

Diese Dokumentation listet die neu eingeführten AES-GCM-Funktionen und die CBC-basierten Funktionen auf, die veraltet sind.

Neue Funktionen:

* [EncryptString-API-Funktion](#encryptString-api-xtk)
* [EncryptStringWithServerPassword-API-Funktion](#EncryptStringWithServerPassword-api-xtk)
* [encryptString-JavaScript-Funktion](#encryptString-javascript)

Legacy-Funktionen, die für GCM verwendet werden können:

* [JavaScript-Funktion DecryptString](#decryptString-javascript)
* [JavaScript-Funktion „DecryptPassword“](#decryptPassword-javascript)

[Veraltete Funktionen](#depracated-functions)

## API-Funktionen

### EncryptString {#encryptString-api-xtk}

Verschlüsselt den String mit dem Instanzschlüssel unter Verwendung des AES-Algorithmus im GCM-Modus.

```
            String 
            encrypted = Encrypt (
            String       
            decrypted
            

      )
         
```

**Parameter**: Entschlüsselter Text

**Rückgabewert(e)**: verschlüsselt

**Schema**: xtk:session

**static**: Ja

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Verschlüsselt den String mit dem Serverschlüssel unter Verwendung des AES-Algorithmus im GCM-Modus.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**parameter**: entschlüsselt

**Rückgabewert(e)**: verschlüsselt

**Schema**: xtk:session

**static**: Ja

## JavaScript-Funktionen

### encryptString() {#encryptString-javascript}

Verschlüsselt eine Zeichenfolge mit dem Schlüssel der Instanz oder einem anderen Schlüssel.

```
            cryptString (str [, key
      ] [, useSalt ])
         
```

**Parameter**:

* str: Die zu verschlüsselnde Zeichenfolge.
* Schlüssel: Der AES-Verschlüsselungsschlüssel wird in Basis 64: 256 Bit kodiert, wenn die Schlüssellänge 32 beträgt; 192 Bit, wenn die Schlüssellänge 24 beträgt; 128 Bit, wenn die Schlüssellänge 16 beträgt oder kein Schlüssel angegeben ist.
* useSalt: Verwendet ein Salz der zu verschlüsselnden Daten. Standardmäßig „true“.

**Rückgabewert**: Gibt die verschlüsselte Zeichenfolge zurück.

**Bemerkungen**

Die Verschlüsselung erfolgt nach folgender Methode:

* Die Unicode-Zeichenfolge wird in eine UTF-8-Zeichenfolge umgewandelt.
* Am Ende wird im Chiffretext ein Prüfzeichen hinzugefügt.
* Diese Zeichenfolge wird mit dem AES-Algorithmus im Galois/Counter Mode (GCM)-Modus mit Salt mit einem 12 Byte Initialisierungsvektor und einem 16 Byte-Tag verschlüsselt. Wenn kein Schlüssel als Parameter angegeben wird, wird der Instanzschlüssel verwendet.
* Der Chiffretext enthält das Tag und den Initialisierungsvektor.
* Der verschlüsselte Block wird dann in die Basis 64 umgewandelt.

Die Entschlüsselung erfolgt mit der Funktion decryptString.

**Funktionen**

Verfügbar in:

* Content-Management
* Versandeigenschaften
* Versandnachricht
* Typologieregel
* Import
* JSSP
* SOAP-Methode
* WebApp
* Workflow

### decryptString() {#decryptString-javascript}

Verschlüsselt eine Zeichenfolge mit dem Schlüssel der Instanz oder einem anderen Schlüssel. Diese alte Funktion kann mit GCM verwendet werden. Sie ist für die Entschlüsselung von Chiffretext, der mit dem AES-CBC-Modus verschlüsselt wird, veraltet.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parameter**:

* str: Die zu entschlüsselnde Zeichenfolge.
* Schlüssel: Der AES-Verschlüsselungsschlüssel wird in Basis 64: 256 Bit kodiert, wenn die Schlüssellänge 32 beträgt; 192 Bit, wenn die Schlüssellänge 24 beträgt; 128 Bit, wenn die Schlüssellänge 16 beträgt oder kein Schlüssel angegeben ist.
* useSalt: Verwendet ein Salz der zu entschlüsselnden Daten. Standardmäßig „true“.

**Rückgabewert**: Gibt die entschlüsselte Zeichenfolge zurück.

**Warnung**: In der Datenbank gespeicherte Kennwörter (Optionen/externe Konten) können mit dieser Methode nicht mehr entschlüsselt werden. Verwenden Sie dazu [decryptPassword](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Entschlüsselt ein in einem externen Konto gespeichertes Kennwort. Diese alte Funktion kann mit GCM verwendet werden. Sie ist für die Entschlüsselung von Chiffretext, der mit dem AES-CBC-Modus verschlüsselt wird, veraltet.

```
            decryptPassword (str)
         
```

**Parameter**:

* str: Die zu entschlüsselnde Zeichenfolge.

**Rückgabewert**: Gibt das Kennwort in Textform zurück.

**Bemerkungen**

Diese Funktion kann nicht in Workflows, Web-Anwendungen, Berichten oder Sendungen aufgerufen werden. Sie kann in JSSP- oder SOAP-Aufrufimplementierungen aufgerufen werden. Beispiel:

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Veraltete Funktionen {#depracated-functions}

Die folgenden Funktionen sind vollständig veraltet:

* cryptString
* Verschlüsseln
* EncryptServerPassword
