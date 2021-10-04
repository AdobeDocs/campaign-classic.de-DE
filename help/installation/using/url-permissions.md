---
product: campaign
title: Konfigurieren von URL-Genehmigungen
description: Erfahren Sie, wie Sie URL-Genehmigungen konfigurieren
audience: installation
content-type: reference
topic-tags: additional-configurations
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 34%

---

# Konfigurieren von URL-Berechtigungen (On-Premise){#url-permissions}

![](../../assets/v7-only.svg)

Die Liste der URLs, die standardmäßig von JavaScript-Codes (Workflows usw.) über Ihre Campaign Classic-Instanzen aufgerufen werden können, ist begrenzt. Diese URLs ermöglichen das ordnungsgemäße Funktionieren der Instanzen.

Standardmäßig sind Instanzen nicht berechtigt, eine Verbindung zu externen URLs herzustellen. Es ist jedoch möglich, externe URLs zur Liste der berechtigten URLs hinzuzufügen, sodass Ihre Instanz eine Verbindung mit ihnen herstellen kann. Dadurch können Sie zwischen Ihren Campaign-Instanzen und externen Systemen, wie z. B. SFTP-Servern oder Websites, eine Verbindung herstellen, um den Datei- und/oder Datentransfer zu ermöglichen.

>[!NOTE]
>
>Dieses Verfahren ist auf **On-Premise** -Implementierungen beschränkt.
>
>Als Kunde von **gehostet** können Sie, wenn Sie auf [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) zugreifen können, die Benutzeroberfläche für URL-Genehmigungen zur Selbstbedienung verwenden. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=de)   
>
>Andere **hybride/gehostete** -Kunden müssen sich an das Adobe Support-Team wenden, um IP zur Zulassungsliste hinzuzufügen.

Bei **Hybrid**- und **On-Premise**-Bereitstellungen muss der Administrator in der Datei **serverConf.xml** auf eine neue **urlPermission** verweisen.


Drei Verbindungsschutzmodi sind verfügbar:

* **Blockieren**: alle URLs, die nicht zur Zulassungsliste gehören, werden mit einer Fehlermeldung blockiert. Dies ist der Standardmodus nach einem Postupgrade.
* **Permissive**: alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig.
* **Warnung**: alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig, doch der JS-Interpreter gibt eine Warnung aus, damit der Administrator sie erfassen kann. In diesem Modus werden Warnmeldungen vom Typ JST-310027 hinzugefügt.

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

* [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Hosting-Modelle](hosting-models.md)
* [Campaign-Server konfigurieren](configuring-campaign-server.md)
* [Parameter der Konfigurationsdatei des Campaign-Servers](the-server-configuration-file.md)
* [Checkliste für Sicherheit und Datenschutz](get-started-security-privacy.md)
