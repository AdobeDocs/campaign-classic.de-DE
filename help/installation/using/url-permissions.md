---
solution: Campaign Classic
product: campaign
title: URL-Berechtigungen konfigurieren
description: Informationen zum Konfigurieren von URL-Berechtigungen
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: 8ab0aab42accbd1253d53e8133f5af0a38c724ea
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 32%

---


# URL-Berechtigungen konfigurieren (lokal){#url-permissions}

Die Liste der URLs, die standardmäßig von JavaScript-Codes (Workflows usw.) über Ihre Campaign Classic-Instanzen aufgerufen werden können, ist begrenzt. Diese URLs ermöglichen das ordnungsgemäße Funktionieren der Instanzen.

Standardmäßig sind Instanzen nicht berechtigt, eine Verbindung zu externen URLs herzustellen. Es ist jedoch möglich, einige externe URLs zur Liste autorisierter URLs hinzuzufügen, damit Ihre Instanz eine Verbindung zu ihnen herstellen kann. Dadurch können Sie zwischen Ihren Campaign-Instanzen und externen Systemen, wie z. B. SFTP-Servern oder Websites, eine Verbindung herstellen, um den Datei- und/oder Datentransfer zu ermöglichen.

>[!NOTE]
>
>Dieses Verfahren ist auf **lokale** Bereitstellungen beschränkt.
>
>Wenn Sie als Kunde **gehostet** auf [Kampagne Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) zugreifen können, können Sie die Benutzeroberfläche für die Selbstbedienung der URL-Zugriffsberechtigungen verwenden. [Mehr dazu](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html)
>
>Andere **hybride/gehostete**-Kunden müssen sich an das Supportteam der Adobe wenden, um der Zulassungsliste IP hinzuzufügen.


Bei Implementierungen von **Hybrid** und **On-Premise** muss der Administrator auf eine neue **urlPermission** in der Datei **serverConf.xml** verweisen.


Es stehen drei Verbindungsschutzmodi zur Verfügung:

* **Blockierung**: alle URLs, die nicht zur Zulassungsliste gehören, werden mit einer Fehlermeldung blockiert. Dies ist der Standardmodus nach einem Postupgrade.
* **Zulässig**: alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig.
* **Warnung**: alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig, der JS-Interpreter gibt jedoch eine Warnung aus, sodass der Administrator sie erfassen kann. In diesem Modus werden Warnmeldungen für JST-310027 hinzugefügt.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Standardmäßig verwenden neue Implementierungen den Modus **Blocking**.
>
>Als bestehender Kunde, der aus einer Migration stammt, können Sie vorübergehend den Modus **Warnung** verwenden. Analysieren Sie den ausgehenden Traffic, bevor Sie die URLs zulassen. Sobald die Liste der zulässigen URLs definiert ist, können Sie die URLs der Zulassungsliste hinzufügen und den Modus **Blockieren** aktivieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Hosting-Modelle](hosting-models.md)
* [Campaign-Server konfigurieren](configuring-campaign-server.md)
* [Parameter der Konfigurationsdatei des Kampagne-Servers](the-server-configuration-file.md)
* [Checkliste für Sicherheit und Datenschutz](get-started-security-privacy.md)