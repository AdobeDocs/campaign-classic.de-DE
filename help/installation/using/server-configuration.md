---
product: campaign
title: Server-Sicherheitskonfiguration
description: Weitere Informationen zu Best Practices für die Server-Konfiguration
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 24%

---

# Sicherheitseinstellungen des Servers {#server-configuration}

## Schutz vor Datei-Upload

Erkundigen Sie sich bei den aktiven Benutzern, welche Dateien sie über die Campaign-Client-Konsole oder die Web-Schnittstelle auf den Server hochladen. Zur Erinnerung: geschäftliche Anforderungen können wie folgt sein:

* Bilder (jpg, gif, png, ...)
* Inhalte (zip, html, css, ...)
* Marketing-Assets (doc, xls, pdf, psd, tiff, ...)
* E-Mail-Anhänge (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* etc.

Fügen Sie alle zu serverConf/shared/datastore/@uploadAllowlist hinzu (gültiger regulärer Java-Ausdruck). Weitere Informationen finden Sie auf [dieser Seite](../../installation/using/file-res-management.md).

Adobe Campaign schränkt die Dateigröße nicht ein. Sie können dies jedoch tun, indem Sie IIS/Apache konfigurieren. Weiterführende Informationen finden Sie in [diesem Abschnitt](../../installation/using/web-server-configuration.md).

## Relais

Weitere Informationen finden [ auf ](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) Seite.

Standardmäßig werden alle dynamischen Seiten automatisch an den lokalen Tomcat-Server des Computers weitergeleitet, dessen Web-Modul gestartet wird. Sie können sich dafür entscheiden, einige nicht weiterzuleiten. Wenn Sie einige Adobe Campaign-Module (z. B. WebApp, Interaction, einige JSP) nicht verwenden, können Sie diese aus den Relay-Regeln entfernen.

Standardmäßig haben wir die Funktion gezwungen, Endbenutzerressourcen mithilfe von http (httpAllowed=„true„) anzuzeigen. Da diese Seiten personenbezogene Daten (E-Mail-Inhalt/Adresse, Gutscheine, Angebote etc.) enthalten können, sollten Sie für diese Pfade wieder HTTPS zwingend festlegen.

Wenn Sie unterschiedliche Host-Namen verwenden (einen öffentlichen und einen für Benutzer), können Sie die Verknüpfung gewisser Ressourcen, die von den Benutzern benötigt werden, auch über den öffentlichen DNS-Namen verhindern.

## Schutz vor ausgehenden Verbindungen

Die Standardliste der URLs, die von JavaScript-Codes (Workflows usw.) aufgerufen werden können, ist begrenzt. Um eine neue URL zuzulassen, muss der Administrator in der Datei „serverConf[xml“ darauf ](../../installation/using/the-server-configuration-file.md).

Es gibt drei Modi für den Verbindungsschutz:

* auf die Zulassungsliste setzen **Sperren** : Alle URLs, die nicht zur gehören, werden mit einer Fehlermeldung blockiert. Dies ist der Standardmodus nach einem Postupgrade.
* auf die Zulassungsliste setzen **Permissive** : Alle URLs, die nicht zur gehören, sind zulässig.
* **Warnung** : Alle URLs, die sich nicht auf der Zulassungsliste befinden, sind zulässig, aber der JS-Interpreter gibt eine Warnung aus, damit der Administrator sie erfassen kann. Dieser Modus fügt JST-310027 Warnmeldungen hinzu.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Neue Clients verwenden den Blockierungsmodus. Wenn sie eine neue URL zulassen möchten, müssen sie sich an ihren Administrator wenden, um sie der Zulassungsliste hinzuzufügen.

Bestehende Kunden, die von einer Migration kommen, können den Warnmodus eine Weile lang verwenden. In der Zwischenzeit muss der ausgehende Traffic analysiert werden, bevor die URLs autorisiert werden.

## Einschränkung der Befehle (serverseitig)

Mehrere Befehle sind in der -Blockierungsliste enthalten und können nicht mit der execCommand-Funktion ausgeführt werden. Ein spezieller Unix-Benutzer bietet zusätzliche Sicherheit, um externe Befehle auszuführen. Bei gehosteten Installationen wird diese Einschränkung automatisch angewendet. Bei On-Premise-Installationen können Sie diese Einschränkung manuell einrichten, indem Sie den Anweisungen auf [ Seite ](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Darüber hinaus sind **[!UICONTROL Script]**- und **[!UICONTROL Externe Aufgabe]**-Workflow-Aktivitäten nicht verfügbar (neu installierte Instanzen).

## Sonstige Konfigurationen

Sie können für alle Seiten zusätzliche HTTP-Kopfzeilen hinzufügen (weitere Informationen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Sie können zusätzliche Header wie HSTS, X-FRAME-OPTIONS, CSP etc. hinzufügen.
* Sie müssen sie in einer Testumgebung testen, bevor Sie sie in der Produktion anwenden.

  >[!IMPORTANT]
  >
  >Adobe Campaign kann durch Hinzufügen bestimmter Kopfzeilen beschädigt werden.

Mit Adobe Campaign können Sie im `<dbcnx .../>` ein einfaches Kennwort festlegen. Verwenden Sie diese Funktion nicht.

Adobe Campaign hängt eine Sitzung standardmäßig nicht an eine bestimmte IP-Adresse an. Sie können sie jedoch aktivieren, um den Diebstahl der Sitzung zu verhindern. Legen Sie dazu in der Datei [serverConf.xml](../../installation/using/the-server-configuration-file.md) im `<authentication>`-Knoten das Attribut checkIPConsistent **true** fest.

Standardmäßig verwendet der MTA von Adobe Campaign keine gesicherte Verbindung, um Inhalte an den SMTP-Server zu senden. Diese Funktion muss aktiviert werden (kann die Versandgeschwindigkeit verringern). Legen Sie dazu **enableTLS** im `<smtp ...>` auf **true** fest.

Sie können die Dauer einer Sitzung im Authentifizierungsknoten beschränken (Attribut sessionTimeOutSec).
