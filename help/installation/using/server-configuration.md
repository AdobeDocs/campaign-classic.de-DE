---
solution: Campaign Classic
product: campaign
title: Serversicherheitskonfiguration
description: Weitere Informationen zu Best Practices bei der Serverkonfiguration
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 42%

---

# Sicherheitseinstellungen des Servers {#server-configuration}

## Schutz vor Datei-Upload

Überprüfen Sie mithilfe der Kampagne Client Console oder der Weboberfläche, welche Dateien auf den Server hochgeladen werden. Zur Erinnerung:

* Bilder (jpg, gif, png, ...)
* Inhalte (zip, html, css, ...)
* Marketing-Assets (doc, xls, pdf, psd, tiff, ...)
* E-Mail-Anhänge (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* etc.

Fügen Sie alle zu serverConf/shared/datastore/@uploadAllowlist hinzu (gültiger regulärer Java-Ausdruck). Weiterführende Informationen finden Sie auf [dieser Seite](../../installation/using/file-res-management.md).

Adobe Campaign schränkt die Dateigröße nicht ein. Sie können dies jedoch tun, indem Sie IIS/Apache konfigurieren. Weiterführende Informationen finden Sie in diesem [Abschnitt](../../installation/using/web-server-configuration.md).

## Relais

Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays).

Standardmäßig werden alle dynamischen Seiten automatisch an den lokalen Tomcat-Server des Geräts weitergeleitet, dessen Web-Modul gestartet wird. Sie können aber auch nicht verwendete Adobe-Campaign-Module ausschließen (z. B. WebApp, Interaction, manche JSPs), indem Sie sie aus den Relais-Regeln entfernen.

Standardmäßig haben wir die Fähigkeit zur Anzeige von Endbenutzerressourcen mithilfe von http (httpAllowed=&quot;true&quot;) gezwungen. Da diese Seiten personenbezogene Daten (E-Mail-Inhalt/Adresse, Gutscheine, Angebote etc.) enthalten können, sollten Sie für diese Pfade wieder HTTPS zwingend festlegen.

Wenn Sie unterschiedliche Host-Namen verwenden (einen öffentlichen und einen für Benutzer), können Sie die Verknüpfung gewisser Ressourcen, die von den Benutzern benötigt werden, auch über den öffentlichen DNS-Namen verhindern.

## Schutz der ausgehenden Verbindung

Die Liste der URLs, die standardmäßig von JavaScript-Codes (Workflows usw.) über Ihre Campaign Classic-Instanzen aufgerufen werden können, begrenzt ist. Um eine neue URL zuzulassen, muss der Administrator darauf in der Datei [serverConf.xml](../../installation/using/the-server-configuration-file.md) verweisen.

Es gibt drei Modi für den Verbindungsschutz:

* **Blockierung** : alle URLs, die nicht zur Zulassungsliste gehören, mit einer Fehlermeldung blockiert werden. Dies ist der Standardmodus nach einem Postupgrade.
* **Zulässig** : alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig.
* **Warnung** : alle URLs, die sich nicht auf der Zulassungsliste befinden, sind zulässig, der JS-Interpreter gibt jedoch eine Warnung aus, sodass der Administrator sie erfassen kann. In diesem Modus werden Warnmeldungen für JST-310027 hinzugefügt.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Neue Clients verwenden den Blockiermodus. Wenn sie eine neue URL zulassen möchten, müssen sie den Administrator ersuchen, die URL auf die Zulassungsliste zu setzen.

Bestehende, aus einer Migration stammende Kunden können einige Zeit den Warnmodus verwenden. In dieser Zeit müssen sie den ausgehenden Verkehr analysieren, bevor sie die URLs genehmigen.

## Einschränkung der Befehle (serverseitig)

Mehrere Befehle sind auf der Blacklist und können nicht mit der Funktion execCommand ausgeführt werden. Eine zusätzliche Sicherheit wird von einem dedizierten Unix-Benutzer bereitgestellt, um externe Befehle auszuführen. Bei gehosteten Installationen wird diese Einschränkung automatisch angewendet. Bei lokalen Installationen können Sie diese Einschränkung manuell einrichten, indem Sie die Anweisungen von [dieser Seite](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands) befolgen. Darüber hinaus sind die Workflow-Aktivitäten **[!UICONTROL Script]** und **[!UICONTROL Externe Aufgabe]** nicht verfügbar (neu installierte Instanzen).

## Sonstige Konfigurationen

Sie können zusätzliche HTTP-Header für alle Seiten hinzufügen (weitere Informationen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Sie können zusätzliche Header wie HSTS, X-FRAME-OPTIONS, CSP etc. hinzufügen.
* Sie müssen sie in einer Umgebung testen, bevor Sie sie in der Produktion anwenden.

   >[!IMPORTANT]
   >
   >Adobe Campaign kann durch Hinzufügen bestimmter Kopfzeilen beschädigt werden.

Mit Adobe Campaign können Sie ein einfaches Kennwort im Element `<dbcnx .../>` festlegen. Verwenden Sie diese Funktion nicht.

Standardmäßig bindet Adobe Campaign eine Sitzung nicht an eine bestimmte IP, aber Sie können sie aktivieren, um zu verhindern, dass die Sitzung gestohlen wird. Legen Sie dazu in der Datei [serverConf.xml](../../installation/using/the-server-configuration-file.md) das Attribut checkIPConsistent auf **true** im Knoten `<authentication>` fest.

Standardmäßig verwendet das MTA des Adobe Campaigns keine gesicherte Verbindung, um Inhalte an den SMTP-Server zu senden. Sie müssen diese Funktion aktivieren (kann die Geschwindigkeit des Versands verringern). Setzen Sie dazu **enableTLS** auf **true** im Knoten `<smtp ...>`.

Sie können die Dauer einer Sitzung im Authentifizierungsknoten beschränken (Attribut sessionTimeOutSec).
