---
product: campaign
title: Konfigurieren von URL-Genehmigungen
description: Erfahren Sie, wie Sie URL-Genehmigungen konfigurieren
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 31%

---

# Konfigurieren von URL-Berechtigungen (On-Premise){#url-permissions}



Die Liste der URLs, die standardmäßig von JavaScript-Codes (Workflows usw.) über Ihre Campaign Classic-Instanzen aufgerufen werden können, ist begrenzt. Diese URLs ermöglichen das ordnungsgemäße Funktionieren der Instanzen.

Standardmäßig sind Instanzen nicht berechtigt, eine Verbindung zu externen URLs herzustellen. Es ist jedoch möglich, externe URLs zur Liste der berechtigten URLs hinzuzufügen, sodass Ihre Instanz eine Verbindung mit ihnen herstellen kann. Dadurch können Sie zwischen Ihren Campaign-Instanzen und externen Systemen, wie z. B. SFTP-Servern oder Websites, eine Verbindung herstellen, um den Datei- und/oder Datentransfer zu ermöglichen.

>[!NOTE]
>
>Dieses Verfahren ist auf **On-Premise** -Implementierungen beschränkt.
>
>Als **gehosteter** -Kunde können Sie, wenn Sie auf das [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) zugreifen können, die Benutzeroberfläche für die URL-Berechtigungen selbst verwenden. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=de)
>
>Andere **hybride/gehostete** -Kunden müssen sich an das Adobe-Supportteam wenden, um IP zur Zulassungsliste hinzuzufügen.
>

Bei Bereitstellungen vom Typ **Hybrid** und **On-Premise** muss der Administrator in der Datei **serverConf.xml** auf eine neue **urlPermission** verweisen.


Drei Verbindungsschutzmodi sind verfügbar:

* **Blocking**: Alle URLs, die nicht zur Zulassungsliste gehören, werden mit einer Fehlermeldung blockiert. Dies ist der Standardmodus nach einem Postupgrade.
* **Permissive**: Alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig.
* **Warnung**: Alle URLs, die nicht zur Zulassungsliste gehören, sind erlaubt, doch der JS-Interpreter gibt eine Warnung aus, damit der Administrator sie erfassen kann. In diesem Modus werden Warnmeldungen vom Typ JST-310027 hinzugefügt.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Standardmäßig verwenden neue Implementierungen den Modus **Blocking** .
>
>Als bestehender Kunde, der aus einer Migration stammt, können Sie den Modus **Warnung** vorübergehend verwenden. Analysieren Sie den ausgehenden Traffic, bevor Sie die URLs zulassen. Sobald die Liste der zulässigen URLs definiert ist, können Sie die URLs zur Zulassungsliste hinzufügen und den Modus **Blocking** aktivieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de)
* [Hosting-Modelle](hosting-models.md)
* [Campaign-Server konfigurieren](configuring-campaign-server.md)
* [Parameter der Konfigurationsdatei des Campaign-Servers](the-server-configuration-file.md)
* [Checkliste für Sicherheit und Datenschutz](get-started-security-privacy.md)
