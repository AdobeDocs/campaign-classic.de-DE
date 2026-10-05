---
product: campaign
title: Konfigurieren von URL-Berechtigungen
description: Erfahren Sie, wie Sie URL-Berechtigungen konfigurieren
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
TQID: 'https://experienceleague.adobe.com/5F4SRt978KzXMI06t3rNt3YRnYI-EWwSkQIrAd0oDq8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
  - id: fb2a841f-c522-491f-9901-a1b939d252df
    internal-label: Security
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
    internal-label: Permissions
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 35%
---
# Konfigurieren von URL-Berechtigungen (On-Premise){#url-permissions}



Die Standardliste der URLs, die von JavaScript-Codes (Workflows usw.) durch Ihre Campaign Classic-Instanzen ist eingeschränkt. Diese URLs ermöglichen das ordnungsgemäße Funktionieren der Instanzen.

Standardmäßig sind Instanzen nicht berechtigt, eine Verbindung zu externen URLs herzustellen. Es ist jedoch möglich, der Liste der autorisierten URLs einige externe URLs hinzuzufügen, damit Ihre Instanz eine Verbindung zu ihnen herstellen kann. Dadurch können Sie zwischen Ihren Campaign-Instanzen und externen Systemen, wie z. B. SFTP-Servern oder Websites, eine Verbindung herstellen, um den Datei- und/oder Datentransfer zu ermöglichen.

>[!NOTE]
>
>Dieses Verfahren ist auf On **Premise-Bereitstellungen**.
>
>Wenn Sie als **gehosteter** Kunde auf das [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) zugreifen können, können Sie die Benutzeroberfläche zum Self-Service für URL-Berechtigungen verwenden. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=de)
>
>Andere **hybride/gehostete** Kunden müssen sich an das Adobe-Supportteam wenden, um IP zur hinzuzufügen.
>

Bei **Hybrid**- und **On-Premise**-Bereitstellungen muss der Administrator auf eine neue **urlPermission** in der Datei **serverConf.xml** verweisen.


Es stehen drei Verbindungsschutzmodi zur Verfügung:

* **Sperren**: Alle URLs, die nicht zur gehören, werden mit einer Fehlermeldung blockiert. Dies ist der Standardmodus nach einem Postupgrade.
* **Permissive**: Alle URLs, die nicht zur gehören, sind zulässig.
* **Warnung**: Alle URLs, die nicht zur Zulassungsliste gehören, sind zulässig, aber der JS-Interpreter gibt eine Warnung aus, damit der Administrator sie erfassen kann. Dieser Modus fügt JST-310027 Warnmeldungen hinzu.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Standardmäßig verwenden neue Implementierungen den **Sperrmodus**.
>
>Als bestehender Kunde, der von einer Migration stammt, können Sie den **Warnungsmodus** temporär verwenden. Analysieren Sie den ausgehenden Traffic, bevor Sie die URLs zulassen. Sobald die Liste der zulässigen URLs definiert ist, können Sie die URLs zur Zulassungsliste hinzufügen und den **Sperrmodus** aktivieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Control Panel-Dokumentation](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de)
* [Hosting-Modelle](hosting-models.md)
* [Campaign-Server konfigurieren](configuring-campaign-server.md)
* [Konfigurationsdateiparameter des Campaign-Servers](the-server-configuration-file.md)
* [Checkliste für Sicherheit und Datenschutz](get-started-security-privacy.md)
