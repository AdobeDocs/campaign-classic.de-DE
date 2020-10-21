---
title: Konfigurieren des Campaign-Servers
seo-title: Konfigurieren des Campaign-Servers
description: Konfigurieren des Campaign-Servers
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 3%

---


# Konfigurieren des Campaign-Servers{#campaign-server-configuration}

In den folgenden Abschnitten werden obligatorische Serverkonfigurationen beschrieben, die den effizienten Betrieb von Adobe Campaign für die meisten Setups gewährleisten.

Weitere Konfigurationen finden Sie unter [Konfigurieren des Kampagne-Servers](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Serverseitige Konfigurationen können nur von der Adobe für Bereitstellungen ausgeführt werden, die von der Adobe gehostet werden. Weitere Informationen zu den verschiedenen Bereitstellungen finden Sie im Abschnitt [Hosting-Modelle](../../installation/using/hosting-models.md) oder in [der Funktionsmatrix](../../installation/using/capability-matrix.md).

## Interne Kennung {#internal-identifier}

Die **interne** Kennung ist eine technische Anmeldung, die zu Installations-, Verwaltungs- und Wartungszwecken verwendet wird. Diese Anmeldung ist keiner Instanz zugeordnet.

Operatoren, die mit dieser Anmeldung verbunden sind, haben alle Rechte auf allen Instanzen. Bei einer Neuinstallation hat diese Anmeldung kein Kennwort. Sie müssen dieses Kennwort manuell definieren.

Verwenden Sie den folgenden Befehl:

```
nlserver config -internalpassword
```

Anschließend werden die folgenden Informationen angezeigt. Geben Sie das Kennwort ein und bestätigen Sie es:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Konfigurationsdateien {#configuration-files}

Die Konfigurationsdateien werden im Installationsordner des Adobe Campaigns im **conf** -Ordner gespeichert. Die Konfiguration erstreckt sich über zwei Dateien:

* **`config-<instance>.xml`** (wobei **instance** der Name der Instanz ist): spezifische Konfiguration der Instanz. Wenn Sie Ihren Server für mehrere Instanzen freigeben, geben Sie bitte die für jede Instanz spezifischen Parameter in die entsprechende Datei ein.
* **serverConf.xml**: allgemeine Konfiguration für alle Instanzen. Diese Datei enthält die technischen Parameter des Adobe Campaign-Servers: diese werden von allen Instanzen freigegeben. Die Beschreibung einiger dieser Parameter ist nachfolgend beschrieben. Die Ansicht aller verfügbaren Parameter finden Sie in der Datei selbst. Die verschiedenen Knoten und Parameter, die in diesem [Abschnitt](../../installation/using/the-server-configuration-file.md)aufgeführt sind.

Sie können den Ordner &quot;Datenspeicherung&quot;(**var** -Verzeichnis) der Adobe Campaign-Daten (Protokolle, Downloads, Umleitungen usw.) konfigurieren. Verwenden Sie dazu die Systemvariable **XTK_VAR_DIR** :

* Geben Sie unter Windows den folgenden Wert in der Systemvariable **XTK_VAR_DIR** an

   ```
   D:\log\AdobeCampaign
   ```

* Wechseln Sie unter Linux zur Datei **customer.sh** und geben Sie Folgendes an: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

   For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Aktivieren von Prozessen {#enabling-processes}

Serverprozesse werden über die **Datei &quot;config-default.xml&quot;aktiviert (und deaktiviert) und** aktiviert ( **`config-<instance>.xml`** config-default.xml).

Wenn Sie die Änderungen auf diese Adobe Campaigne anwenden möchten, müssen Sie beim Starten des Dateidiensts den Befehl **nlserver config -reload** ausführen.

Es gibt zwei Arten von Prozessen: mehrere Instanzen und eine einzelne Instanz.

* **mehrere Instanzen**: für alle Instanzen wird ein einzelner Prozess gestartet. Dies gilt für **Web**-, **syslogd** - und **trackinglogd** -Prozesse.

   Die Aktivierung kann über die Datei **config-default.xml** konfiguriert werden.

   Deklarieren eines Adobe Campaign-Servers für den Zugriff auf Client-Konsolen und für die Weiterleitung (Verfolgung):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In diesem Beispiel wird die Datei unter Linux mit einem **vi** -Befehl bearbeitet. Sie kann mit einem beliebigen **.txt** - oder **.xml** -Editor bearbeitet werden.

* **Monoinstanz**: Ein Prozess wird für jede Instanz gestartet (Module: **mta**, **wfserver**, **inMail**, **sms** und **stat**).

   Die Aktivierung kann mithilfe der Konfigurationsdatei der Instanz konfiguriert werden:

   ```
   config-<instance>.xml
   ```

   Deklarieren eines Servers für Versand, Ausführen von Workflow-Instanzen und Wiederherstellen der Absprung-Mail:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Versandeinstellungen {#delivery-settings}

Die Versand-Parameter müssen im Ordner &quot; **serverConf.xml** &quot;konfiguriert werden.

* **DNS-Konfiguration**: Geben Sie die Domäne des Versands und die IP-Adressen (oder den Host) der DNS-Server an, die verwendet werden, um auf MX-Typ-DNS-Abfragen zu reagieren, die vom MTA-Modul ab **`<dnsconfig>`** dem Zeitpunkt des Antrages vorgenommen werden.

   >[!NOTE]
   >
   >Der Parameter **nameServers** ist für eine Installation unter Windows unerlässlich. Bei einer Installation unter Linux muss sie leer bleiben.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Die anderen Versand-Parameter, die in dieser Datei verfügbar sind, finden Sie unter [Personalisieren von Versand-Parametern](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Siehe auch [E-Mail-Zustellbarkeit](../../installation/using/email-deliverability.md).
