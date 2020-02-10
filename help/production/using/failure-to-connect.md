---
title: Verbindung fehlgeschlagen
seo-title: Verbindung fehlgeschlagen
description: Verbindung fehlgeschlagen
seo-description: null
page-status-flag: never-activated
uuid: 5e4cf47d-9699-4b4c-9c45-064fdc17110a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 493067fb-68f1-48b9-afaa-3127a847db83
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 90813bc2913d56136067b9f64c0e934df3f17473

---


# Verbindung fehlgeschlagen{#failure-to-connect}

Die Gründe dafür können vielfältig sein und von verschiedenen Kontexten abhängen.

Überprüfen Sie die allgemeine Konfiguration der Sicherheitszonen.

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Sicherheitszonen finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Überprüfen Sie die folgenden Informationen:

1. **Netzwerkprüfungen**

   * Haben Sie Internetzugang von Ihrem Computer?

      Vergewissern Sie sich, dass Sie eine Verbindung zu Websites im Internet herstellen können (z. B.). Wenn Sie keine Verbindung herstellen können, liegt das Problem auf Ihrem Computer. Wenden Sie sich an Ihren Systemadministrator.

   * Können Sie über einen anderen Dienst eine Verbindung zum Server herstellen, auf dem Adobe Campaign gehostet wird?

      Stellen Sie eine Verbindung mit dem Server über SSH oder auf andere Weise her. Ist dies nicht möglich, hat Ihr Hostunternehmen ein Problem. Wenden Sie sich an den Systemadministrator.

1. **Überprüfungen auf Webserverseite** (IIS/Apache/etc.)

   * Reagiert der Webserver?

      Stellen Sie mithilfe eines Webbrowsers eine Verbindung zur Adobe Campaign-Server-Zugriffs-URL her: **http(s)://`<urlserver>`**. Wenn er nicht reagiert, wird der Webserver auf dem Computer angehalten. Wenden Sie sich an den Systemadministrator Ihres Hostunternehmens, um den Dienst neu zu starten.

   * Wurde Adobe Campaign korrekt integriert?

      Melden Sie sich bei: URL **http(s)://`<urlserver>`/r/test** . Der Server sollte die folgende Art von Meldung zurückgeben

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      Wenn Sie dieses Ergebnis nicht erhalten, überprüfen Sie Ihre Webserverkonfiguration, ob diese Integration berücksichtigt wird.

1. **Überprüfungen auf der Seite &quot;Adobe Campaign&quot;**

   * Wurde das Adobe Campaign-Webmodul gestartet?

      Stellen Sie eine Verbindung mit der folgenden URL her: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Wenn Sie einen Tomcat Java-Fehler erhalten:

         Wird die JAVA-Integration korrekt ausgeführt? Adobe Campaign erfordert ein SUN-JDK.

         Es ist in die Datei **`[path of application]`/nl6/customer.sh integriert.**

      * Wenn Sie eine leere Seite erhalten:

         Hat das Adobe Campaign-Webmodul gestartet? Sie sollten Folgendes erhalten:

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * Andernfalls starten Sie es mit dem folgenden Befehl neu:

         ```
         nlserver start web
         ```
>[!NOTE]
>
>Wenn Sie eine Antwort vom folgenden Typ erhalten, wenn Sie die Adobe Campaign-Module auflisten: nlserver **pdump**
>HH:MM:SS > Anwendungsserver für Adobe Campaign Classic (7.X YY.R Build XXX@SHA1) von TT/MM/JJJJ Keine Aufgaben Sie müssen die gesamte Adobe Campaign-Anwendung neu starten. Verwenden Sie dazu den folgenden Befehl: **nlserver watchdog -svc -noconsole **
