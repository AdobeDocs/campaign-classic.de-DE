---
solution: Campaign Classic
product: campaign
title: Konfiguration des Servers
description: Weitere Informationen zu Best Practices für die Serverkonfiguration.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '1159'
ht-degree: 62%

---


# Serverkonfiguration {#server-configuration}

## Konfigurieren von Sicherheitszonen

>[!IMPORTANT]
>
>Ab Build 8977 ist die Benutzeroberfläche der Sicherheitszonen nicht mehr verfügbar.
>
>* Wenn Sie auf AWS gehostet werden, muss das Hinzufügen von IP zur Zulassungsliste in der Systemsteuerung durchgeführt werden. Weitere Informationen finden Sie in der [entsprechenden Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html).
>* Wenn Sie nicht auf AWS gehostet werden, kontaktieren Sie das Adobe-Supportteam, um IPs auf die Zulassungsliste zu setzen.

>
>
Um zu überprüfen, ob Ihre Instanz auf AWS gehostet wird, folgen Sie den Schritten in [diesem Abschnitt](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

* Stellen Sie sicher, dass Ihr Reverse-Proxy in subNetwork nicht erlaubt ist. Ist dies der Fall, wird der **gesamte** Datenverkehr als von dieser lokalen IP-Adresse kommend und daher als vertrauenswürdig eingestuft.

* Minimieren Sie den Einsatz von sessionTokenOnly=&quot;true&quot;:

   * Achtung: Wenn dieses Attribut auf true gesetzt wird, ist der Benutzer durch **CRSF-Attacken** (Cross-Site Request Forgery) angreifbar.
   * Zusätzlich ist das sessionToken-Cookie nicht mit einem httpOnly-Flag versehen, weshalb es von einem Client-seitigen Javascript-Code gelesen werden kann.
   * Bei Verwendung von Message Center mit mehreren Ausführungsinstanzen ist jedoch der Einsatz von sessionTokenOnly unumgänglich: Erstellen Sie eine neue Sicherheitszone, setzen Sie sessionTokenOnly auf &quot;true&quot;, und fügen Sie dieser Zone **nur die benötigten IP-Adressen** hinzu.

* Setzen Sie möglichst alle allowHTTP, showErrors auf &quot;false&quot; (nicht für localhost), und prüfen Sie sie.

   * allowHTTP = &quot;false&quot;: zwingt Benutzer, HTTPS zu verwenden.
   * showErrors = &quot;false&quot;: verbirgt technische Fehler (einschließlich SQL-Fehler). Dies verhindert die Anzeige übermäßig vieler Informationen, schränkt aber auch die Fähigkeit des Benutzers ein, Probleme zu lösen (ohne vom Administrator zusätzliche Informationen einzuholen).

* Setzen Sie allowDebug nur für IP-Adressen auf true, die von Benutzern/Administratoren verwendet werden, die Fragebögen, WebApps und Berichte erstellen müssen (diese aber nicht in der Vorschau ansehen können). Durch dieses Flag werden in diesen IP-Adressen Relais-Regeln dargestellt, was eine Fehlerbehebung ermöglicht.

* Setzen Sie niemals allowEmptyPassword, allowUserPassword, allowSQLInjection auf true. Diese Attribute dienen nur der problemlosen Migration von v5 und v6.0:

   * **allowEmptyPassword** ermöglicht Benutzern, ein leeres Passwort zu haben. Ist dies bei Ihnen der Fall, weisen Sie alle Benutzer an, bis zu einer bestimmten Deadline ein Passwort zu erstellen. Sobald diese Frist abgelaufen ist, ändern Sie dieses Attribut auf &quot;false&quot;.

   * **allowUserPassword** ermöglicht es Benutzern, ihre Zugangsdaten als Parameter zu senden (sodass sie via Apache/IIS/Proxy gespeichert werden). Diese Funktion diente in der Vergangenheit zur Vereinfachung der API-Nutzung. In Ihrem Cookbook (oder in der Spezifikation) können Sie nachsehen, ob die Funktion von Drittanwendungen genutzt wird. Ist dies der Fall, weisen Sie den Administrator dieser Drittanwendungen an, die Verwendung unserer API zu ändern und die Funktion nicht mehr zu nutzen.

   * **** allowSQLInjectionermöglicht dem Benutzer die Durchführung von SQL-Injektionen mit einer alten Syntax. Führen Sie so bald wie möglich die unter [Diese Seite](../../migration/using/general-configurations.md) beschriebenen Korrekturen durch, um dieses Attribut auf &quot;false&quot;setzen zu können. Mit /nl/jsp/ping.jsp?zones=true können Sie die Konfiguration Ihrer Sicherheitszone überprüfen. Auf dieser Seite wird der aktive Status von Sicherheitsmaßnahmen (mit diesen Sicherheits-Flags berechnet) für die aktuelle IP-Adresse angezeigt.

* HttpOnly cookie/useSecurityToken: siehe Flag **sessionTokenOnly**.

* Minimieren Sie die Anzahl der IP-Adressen auf der Zulassungsliste: Standardmäßig wurden für Sicherheitszonen die drei Bereiche für private Netzwerke hinzugefügt. Es ist unwahrscheinlich, dass Sie alle diese IP-Adressen verwenden werden. Behalten Sie also nur die, die Sie brauchen.

* Aktualisieren Sie den WebApp-/internen Benutzer, damit er nur über localhost zugänglich sind.

## Schutz vor Datei-Upload

Erkundigen Sie sich bei den Benutzern, welche Arten von Dateien sie über die Schnittstelle nlclient/web zum Server hochladen. In Unternehmen sind die folgenden Dateien gebräuchlich:

* Bilder (jpg, gif, png, ...)
* Inhalte (zip, html, css, ...)
* Marketing-Assets (doc, xls, pdf, psd, tiff, ...)
* E-Mail-Anhänge (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* etc.

Fügen Sie alle zu serverConf/shared/datastore/@uploadAllowlist hinzu (gültiger regulärer Java-Ausdruck). Weiterführende Informationen finden Sie auf [dieser Seite](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

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
