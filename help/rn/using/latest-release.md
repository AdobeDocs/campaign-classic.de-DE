---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# Aktuelle Version{#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.3.5 – Build 9368 {#release-7-3-5}

[!BADGE Allgemeine Verfügbarkeit]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Allgemeine Verfügbarkeit"}


_5. Dezember 2023_


### Verbesserungen bei der Sicherheit  {#release-7-3-5-security}


* Mit Campaign Classic v7.3.5 wurde der Authentifizierungsprozess verbessert und sicherer gemacht. Technische Benutzende sollten sich jetzt über das Adobe Identity Management System (IMS) mit Campaign verbinden. Erfahren Sie in [dieser Technote](../../technotes/using/ims-migration.md), wie Sie Ihre vorhandenen technischen Konten migrieren können.

* Darüber hinaus empfiehlt Adobe Campaign im Rahmen der Bemühungen, die Sicherheit und den Authentifizierungsprozess zu verbessern, dringend, den Authentifizierungsmodus für Endbenutzende von der nativen Authentifizierung mit Login/Passwort auf das Adobe Identity Management System (IMS) zu migrieren. Erfahren Sie in [diesem technischen Hinweis](../../technotes/using/migrate-users-to-ims.md), wie Sie Ihre Benutzenden migrieren können.

* Wenn jetzt ein Web-Formular den Status **Veröffentlichung ausstehend** hat, wird es nicht automatisch live geschaltet. Um Sicherheitsprobleme zu vermeiden, muss es veröffentlicht werden, bevor es **online** und über die Web-Formular-URL in einem Webbrowser abrufbar ist. [Weitere Informationen](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Patches  {#release-7-3-5-patches}

* Fehlerkorrektur – Bei der Verwendung von Daten aus einer Google Big Query-Datenbank und der Aktualisierung von Daten in einer Oracle-Datenbank werden jetzt nicht mehr alle Schlüssel in der temporären Workflow-Tabelle auf `0` gesetzt. (NEO-65091)
* Fehlerkorrektur – Die Ausführung eines Workflows funktioniert jetzt auch dann, wenn zwei Abfragen einer Google Big Query-Datenbank in einer **Vereinigungs**-Workflow-Aktivität kombiniert werden. (NEO-63705)
* Fehlerkorrektur – Benutzende müssen sich jetzt nicht mehr neu authentifizieren, wenn sie in einem Kampagnenbericht auf `Back` klicken. (NEO-65087)
* Fehlerkorrektur – Im Workflow „Datenbankbereinigung“ tritt jetzt kein Fehler mehr auf, wenn ein Versand vor seinen Testsendungen gelöscht wird. (NEO-48114)
* Fehlerkorrektur – Beim Herstellen einer Verbindung zur Client Console tritt jetzt auch bei den neuesten Updates der TLS-Überprüfung kein Verbindungsfehler mehr auf. (NEO-50488)
* Fehlerkorrektur – Bei der HTTP-Proxy-Authentifizierung nach dem Campaign-Postupgrade auf 7.3.1 schlagen jetzt HTTP-Anforderungen in Campaign-Workflows nicht mehr mit `error 407 – proxy auth required is returned` fehl. (NEO-49624)
* Behebung eines zeitweiligen Fehlers bei der GPG-Entschlüsselung in **Skript** Workflow-Aktivitäten. Die entsprechende Fehlermeldung lautete: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

