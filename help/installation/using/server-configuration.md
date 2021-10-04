---
product: campaign
title: Sicherheitskonfiguration des Servers
description: Weitere Informationen zu Best Practices bei der Serverkonfiguration
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 39%

---

# Sicherheitseinstellungen des Servers {#server-configuration}

![](../../assets/v7-only.svg)

## Schutz vor Datei-Upload

Erkundigen Sie sich bei den Benutzern, welche Art von Dateien sie über die Campaign Client-Konsole oder die Web-Oberfläche auf den Server hochladen. Zur Erinnerung:

* Bilder (jpg, gif, png, ...)
* Inhalte (zip, html, css, ...)
* Marketing-Assets (doc, xls, pdf, psd, tiff, ...)
* E-Mail-Anhänge (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* etc.

Fügen Sie alle zu serverConf/shared/datastore/@uploadAllowlist hinzu (gültiger regulärer Java-Ausdruck). Weiterführende Informationen finden Sie auf [dieser Seite](../../installation/using/file-res-management.md).

Adobe Campaign schränkt die Dateigröße nicht ein. Sie können dies jedoch tun, indem Sie IIS/Apache konfigurieren. Weiterführende Informationen finden Sie in [diesem Abschnitt](../../installation/using/web-server-configuration.md).

## Relais

Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) .

Standardmäßig werden alle dynamischen Seiten automatisch an den lokalen Tomcat-Server des Geräts weitergeleitet, dessen Web-Modul gestartet wird. Sie können aber auch nicht verwendete Adobe-Campaign-Module ausschließen (z. B. WebApp, Interaction, manche JSPs), indem Sie sie aus den Relais-Regeln entfernen.

Standardmäßig haben wir die Möglichkeit erzwungen, Endbenutzerressourcen mithilfe von http (httpAllowed=&quot;true&quot;) anzuzeigen. Da diese Seiten personenbezogene Daten (E-Mail-Inhalt/Adresse, Gutscheine, Angebote etc.) enthalten können, sollten Sie für diese Pfade wieder HTTPS zwingend festlegen.

Wenn Sie unterschiedliche Host-Namen verwenden (einen öffentlichen und einen für Benutzer), können Sie die Verknüpfung gewisser Ressourcen, die von den Benutzern benötigt werden, auch über den öffentlichen DNS-Namen verhindern.

## Schutz der ausgehenden Verbindung

Die Liste der URLs, die standardmäßig von JavaScript-Codes (Workflows usw.) über Ihre Campaign Classic-Instanzen aufgerufen werden können, ist begrenzt. Um eine neue URL zuzulassen, muss der Administrator sie in der Datei [serverConf.xml](../../installation/using/the-server-configuration-file.md) referenzieren.

Es gibt drei Modi für den Verbindungsschutz:

* **Blockieren** : alle URLs, die nicht zur Zulassungsliste gehören, werden mit einer Fehlermeldung blockiert. Dies ist der Standardmodus nach einem Postupgrade.
* **Permissive** : alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig.
* **Warnung** : alle URLs, die sich nicht auf der Zulassungsliste befinden, sind erlaubt, doch der JS-Interpreter gibt eine Warnung aus, damit sie vom Administrator erfasst werden können. In diesem Modus werden Warnmeldungen vom Typ JST-310027 hinzugefügt.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Neue Clients verwenden den Blockierungsmodus. Wenn sie eine neue URL zulassen möchten, müssen sie sich an ihren Administrator wenden, um sie der Zulassungsliste hinzuzufügen.

Bestehende, aus einer Migration stammende Kunden können einige Zeit den Warnmodus verwenden. In dieser Zeit müssen sie den ausgehenden Verkehr analysieren, bevor sie die URLs genehmigen.

## Einschränkung der Befehle (serverseitig)

Mehrere Befehle sind auf der Blacklist und können nicht mit der Funktion execCommand ausgeführt werden. Ein spezieller Unix-Benutzer stellt zusätzliche Sicherheit bereit, um externe Befehle auszuführen. Bei gehosteten Installationen wird diese Einschränkung automatisch angewendet. Bei lokalen Installationen können Sie diese Einschränkung manuell einrichten, indem Sie den Anweisungen von [dieser Seite](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands) folgen. Darüber hinaus sind die Workflow-Aktivitäten **[!UICONTROL Script]** und **[!UICONTROL Externe Aufgabe]** nicht verfügbar (neu installierte Instanzen).

## Sonstige Konfigurationen

Sie können für alle Seiten zusätzliche HTTP-Header hinzufügen (weitere Informationen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Sie können zusätzliche Header wie HSTS, X-FRAME-OPTIONS, CSP etc. hinzufügen.
* Sie müssen sie in einer Testumgebung testen, bevor Sie sie in der Produktion anwenden.

   >[!IMPORTANT]
   >
   >Adobe Campaign kann durch Hinzufügen bestimmter Kopfzeilen beschädigt werden.

Mit Adobe Campaign können Sie ein einfaches Kennwort im Element `<dbcnx .../>` festlegen. Verwenden Sie diese Funktion nicht.

Standardmäßig ist eine Sitzung in Adobe Campaign nicht an eine bestimmte IP-Adresse gebunden, Sie können sie jedoch aktivieren, um zu verhindern, dass die Sitzung gestohlen wird. Setzen Sie dazu in der Datei [serverConf.xml](../../installation/using/the-server-configuration-file.md) das Attribut checkIPConsistent im Knoten **true** auf `<authentication>`.

Standardmäßig verwendet der MTA von Adobe Campaign keine gesicherte Verbindung, um Inhalte an den SMTP-Server zu senden. Sie müssen diese Funktion aktivieren (dies kann die Versandgeschwindigkeit verringern). Setzen Sie dazu **enableTLS** im Knoten `<smtp ...>` auf **true** .

Sie können die Dauer einer Sitzung im Authentifizierungsknoten beschränken (Attribut sessionTimeOutSec).
