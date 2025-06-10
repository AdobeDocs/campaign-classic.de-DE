---
product: campaign
title: Neue GCM-basierte Funktionen
description: Neue GCM-basierte Funktionen
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: ht
source-wordcount: '578'
ht-degree: 100%

---

# GCM-basierte Funktionen {#new-functions}

Um die Sicherheit zu erhöhen, haben wir die Verwendung des AES-Algorithmus (Advanced Encryption Standard) mit dem CBC-Modus (Cipher Block Chaining) für kryptografische Vorgänge eingestellt. Dafür wurden neue Verschlüsselungsfunktionen eingeführt. Diese Funktionen verwenden AES mit dem Galois/Counter Mode (AES-GCM) und bieten so eine sicherere Alternative. Sie sind in JavaScript, JSP, SOAP-APIs und XML-Schemata verfügbar, sodass Kundinnen und Kunden zur Verschlüsselung und Entschlüsselung von CBC zu GCM wechseln können.

Diese Dokumentation listet die neu eingeführten AES-GCM-Funktionen und die eingestellten CBC-basierten Funktionen auf.

Neue Funktionen

* [EncryptString-API-Funktion](#encryptString-api-xtk)
* [EncryptStringWithServerPassword-API-Funktion](#EncryptStringWithServerPassword-api-xtk)
* [encryptString-JavaScript-Funktion](#encryptString-javascript)

Legacy-Funktionen, die für GCM verwendet werden können:

* [DecryptString-JavaScript-Funktion ](#decryptString-javascript)
* [DecryptPassword-JavaScript-Funktion](#decryptPassword-javascript)

[Eingestellte Funktionen](#depracated-functions)

## API-Funktionen

### EncryptString {#encryptString-api-xtk}

Verschlüsselt den String mit dem Instanzschlüssel unter Verwendung des AES-Algorithmus mit GCM-Modus.

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**Parameter**: decrypted

**Rückgabewert(e)**: encrypted

**Schema**: xtk:session

**Statisch**: Ja

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Verschlüsselt den String mit dem Server-Schlüssel unter Verwendung des AES-Algorithmus mit GCM-Modus.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Parameter**: decrypted

**Rückgabewert(e)**: encrypted

**Schema**: xtk:session

**Statisch**: Ja

## JavaScript-Funktionen

### encryptString() {#encryptString-javascript}

Verschlüsselt einen String mit dem Schlüssel der Instanz oder einem anderen Schlüssel.

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**Parameter**:

* str: Der zu verschlüsselnde String.
* key: Der AES-Verschlüsselungsschlüssel wird mit Base 64 verschlüsselt: 256 Bit bei einer Schlüssellänge von 32, 192 Bit bei einer Schlüssellänge von 24, 128 Bit bei einer Schlüssellänge von 16 oder fehlender Schlüsselangabe.
* useSalt: Verwenden Sie Salt der zu verschlüsselnden Daten. Standardmäßig „true“.

**Rückgabewert**: Gibt den verschlüsselten String zurück.

**Bemerkungen**

Die Verschlüsselung erfolgt nach folgender Methode:

* Der Unicode-String wird in einen UTF-8-String umgewandelt.
* Am Ende wird im Chiffretext ein Prüfzeichen hinzugefügt.
* Dieser String wird mit dem AES-Algorithmus im Galois/Counter Mode (GCM) unter Verwendung von Salt mit einem 12-Byte-Initialisierungsvektor und einem 16-Byte-Tag verschlüsselt. Wenn kein Schlüssel als Parameter angegeben wird, wird der Instanzschlüssel verwendet.
* Der Chiffretext enthält das Tag und den Initialisierungsvektor.
* Der verschlüsselte Block wird dann in Base 64 konvertiert.

Die Entschlüsselung erfolgt mit der Funktion „decryptString“.

**Funktionen**

Verfügbar in:

* Content-Management
* Versandeigenschaften
* Versandnachricht
* Typologieregel
* Import
* JSSP
* SOAP-Methoden
* WebApp
* Workflow

### decryptString() {#decryptString-javascript}

Entschlüsselt einen String mit dem Schlüssel der Instanz oder einem anderen Schlüssel. Diese Legacy-Funktion kann mit GCM verwendet werden. Sie steht für die Entschlüsselung von mit dem AES-CBC-Modus verschlüsselten Chiffretext nicht mehr zur Verfügung.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parameter**:

* str: Der zu entschlüsselnde String.
* key: Der AES-Verschlüsselungsschlüssel wird mit Base 64 verschlüsselt: 256 Bit bei einer Schlüssellänge von 32, 192 Bit bei einer Schlüssellänge von 24, 128 Bit bei einer Schlüssellänge von 16 oder fehlender Schlüsselangabe.
* useSalt: Verwenden Sie Salt der zu entschlüsselnden Daten. Standardmäßig „true“.

**Rückgabewert**: Gibt den entschlüsselten String zurück.

**Warnung**: In der Datenbank gespeicherte Passwörter (Optionen/externe Konten) können mit dieser Methode nicht mehr entschlüsselt werden. Verwenden Sie dazu [decryptPassword](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Entschlüsselt ein in einem externen Konto gespeichertes Passwort. Diese Legacy-Funktion kann mit GCM verwendet werden. Sie steht für die Entschlüsselung von mit dem AES-CBC-Modus verschlüsselten Chiffretext nicht mehr zur Verfügung.

```
            decryptPassword (str)
         
```

**Parameter**:

* str: Der zu entschlüsselnde String.

**Rückgabewert**: Gibt das Passwort in reiner Textform zurück.

**Bemerkungen**

Diese Funktion kann nicht in Workflows, Web-Anwendungen, Berichten oder Sendungen aufgerufen werden, aber in JSSP- oder SOAP-Aufrufimplementierungen. Beispiel:

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

## Eingestellte Funktionen {#depracated-functions}

Folgende Funktionen stehen nicht mehr zur Verfügung:

* cryptString
* Verschlüsseln
* EncryptServerPassword
