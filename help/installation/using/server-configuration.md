---
product: campaign
title: Sicherheitskonfiguration des Servers
description: Weitere Informationen zu Best Practices bei der Serverkonfiguration
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 35%

---

# Sicherheitseinstellungen des Servers {#server-configuration}

## Schutz vor Datei-Upload

Erkundigen Sie sich bei den Benutzern, welche Art von Dateien sie über die Campaign Client-Konsole oder die Web-Oberfläche auf den Server hochladen. Zur Erinnerung:

* Bilder (jpg, gif, png, ...)
* Inhalte (zip, html, css, ...)
* Marketing-Assets (doc, xls, pdf, psd, tiff, ...)
* E-Mail-Anhänge (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* etc.

Fügen Sie alle zu serverConf/shared/datastore/@uploadAllowlist hinzu (gültiger regulärer Java-Ausdruck). Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/file-res-management.md).

Adobe Campaign schränkt die Dateigröße nicht ein. Sie können dies jedoch tun, indem Sie IIS/Apache konfigurieren. Weiterführende Informationen finden Sie in [diesem Abschnitt](../../installation/using/web-server-configuration.md).

## Relais

Siehe [diese Seite](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) für weitere Informationen.

Standardmäßig werden alle dynamischen Seiten automatisch an den lokalen Tomcat-Server des Geräts weitergeleitet, dessen Web-Modul gestartet wird. Sie können aber auch nicht verwendete Adobe-Campaign-Module ausschließen (z. B. WebApp, Interaction, manche JSPs), indem Sie sie aus den Relais-Regeln entfernen.

Standardmäßig haben wir die Möglichkeit erzwungen, Endbenutzerressourcen mithilfe von http (httpAllowed=&quot;true&quot;) anzuzeigen. Da diese Seiten personenbezogene Daten (E-Mail-Inhalt/Adresse, Gutscheine, Angebote etc.) enthalten können, sollten Sie für diese Pfade wieder HTTPS zwingend festlegen.

Wenn Sie unterschiedliche Host-Namen verwenden (einen öffentlichen und einen für Benutzer), können Sie die Verknüpfung gewisser Ressourcen, die von den Benutzern benötigt werden, auch über den öffentlichen DNS-Namen verhindern.

## Schutz der ausgehenden Verbindung

Die Liste der URLs, die standardmäßig von JavaScript-Codes (Workflows usw.) über Ihre Campaign Classic-Instanzen aufgerufen werden können, ist begrenzt. Um eine neue URL zuzulassen, muss der Administrator sie im [Datei &quot;serverConf.xml&quot;](../../installation/using/the-server-configuration-file.md).

Es gibt drei Modi für den Verbindungsschutz:

* **Blockieren** : Alle URLs, die nicht zur Zulassungsliste gehören, werden blockiert und erhalten eine Fehlermeldung. Dies ist der Standardmodus nach einem Postupgrade.
* **Permissive** : Alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig.
* **Warnung** : Alle URLs, die sich nicht auf der Zulassungsliste befinden, sind zulässig, der JS-Interpreter gibt jedoch eine Warnung aus, damit der Administrator sie erfassen kann. In diesem Modus werden Warnmeldungen vom Typ JST-310027 hinzugefügt.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Neue Clients verwenden den Blockierungsmodus. Wenn sie eine neue URL zulassen möchten, müssen sie sich an ihren Administrator wenden, um sie der Zulassungsliste hinzuzufügen.

Vorhandene Kunden, die aus einer Migration stammen, können den Warnmodus für eine Weile verwenden. In der Zwischenzeit müssen sie den ausgehenden Traffic analysieren, bevor sie die URLS autorisieren.

## Einschränkung der Befehle (serverseitig)

Mehrere Befehle sind in der Blockierungsliste enthalten und können nicht mit der Funktion execCommand ausgeführt werden. Ein spezieller Unix-Benutzer stellt zusätzliche Sicherheit bereit, um externe Befehle auszuführen. Bei gehosteten Installationen wird diese Einschränkung automatisch angewendet. Bei On-Premise-Installationen können Sie diese Einschränkung manuell einrichten, indem Sie den Anweisungen unter [diese Seite](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Darüber hinaus **[!UICONTROL Skript]** und **[!UICONTROL Externe Aufgabe]** Workflow-Aktivitäten sind nicht verfügbar (neu installierte Instanzen).

## Sonstige Konfigurationen

Sie können für alle Seiten zusätzliche HTTP-Header hinzufügen (weitere Informationen finden Sie unter [diese Seite](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Sie können zusätzliche Header wie HSTS, X-FRAME-OPTIONS, CSP etc. hinzufügen.
* Sie müssen sie in einer Testumgebung testen, bevor Sie sie in der Produktion anwenden.

  >[!IMPORTANT]
  >
  >Adobe Campaign kann durch Hinzufügen bestimmter Kopfzeilen beschädigt werden.

Adobe Campaign ermöglicht die Festlegung eines einfachen Kennworts im `<dbcnx .../>` -Element. Verwenden Sie diese Funktion nicht.

Standardmäßig ist eine Sitzung in Adobe Campaign nicht an eine bestimmte IP-Adresse gebunden, Sie können sie jedoch aktivieren, um zu verhindern, dass die Sitzung gestohlen wird. Gehen Sie dazu im [Datei &quot;serverConf.xml&quot;](../../installation/using/the-server-configuration-file.md)setzen Sie das Attribut checkIPConsistent auf **true** im `<authentication>` Knoten.

Standardmäßig verwendet der MTA von Adobe Campaign keine gesicherte Verbindung, um Inhalte an den SMTP-Server zu senden. Sie müssen diese Funktion aktivieren (dies kann die Versandgeschwindigkeit verringern). Legen Sie dazu **enableTLS** nach **true** im `<smtp ...>` Knoten.

Sie können die Dauer einer Sitzung im Authentifizierungsknoten beschränken (Attribut sessionTimeOutSec).
