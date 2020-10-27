---
title: Multibranding konfigurieren
seo-title: Multibranding konfigurieren
description: Multibranding konfigurieren
seo-description: null
page-status-flag: never-activated
uuid: 61b4235c-da03-4da8-b14b-7ffb12c8d4c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 907d82c8-9262-4952-b8df-21144dd55824
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 100%

---


# Multibranding konfigurieren{#configuring-multibranding}

In diesem Abschnitt wird eine Lösung beschrieben, mit der Tracking- und Mirrorseiten-URLs für jede Marke für Transaktionsnachrichten in Adobe Campaign konfiguriert werden können.

## Voraussetzungen {#prerequisites}

* Alle Hosts müssen der Konfigurationsdatei der Instanz (`config-<instance>.xml`) hinzugefügt werden.
* Jeder Marke muss eine Sub-Domain zugewiesen werden.
* Wenn das Webtracking auf HTTPS-Seiten erfolgt, müssen Sie für alle Marken über ein HTTPS-Zertifikat verfügen.

## Typische Vorgehensweise {#typical-process}

Um Multibranding zu konfigurieren, ist es nötig, sowohl Ausführungsinstanzen als auch Kontrollinstanzen zu konfigurieren. Gehen Sie bei Ausführungsinstanzen folgendermaßen vor:

1. Erstellen Sie für jede Marke ein externes Konto.

   >[!NOTE]
   >
   >Die Erstellung eines externen Kontos vom Ausführungsinstanz-Typ wird in Abschnitt [Kontrollinstanz](../../message-center/using/creating-a-shared-connection.md#control-instance) beschrieben.

1. Erweitern Sie das Schema nms:extAccount, um die Tracking-URL hinzuzufügen:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Die Erweiterung eines vorhandenen Schemas wird im Abschnitt [Schema erweitern](../../configuration/using/extending-a-schema.md) beschrieben.

1. Passen Sie das Formular nms:extAccount an:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Passen Sie die Optionen NmsTracking_OpenFormula und NmsTracking_ClickFormula so an, dass das externe Konto anstelle einer globalen Option verwendet wird.

   Ersetzen Sie zu diesem Zweck:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   durch:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Diese Änderungen könnten beim Upgrade Konflikte verursachen. Möglicherweise müssen Sie diese Formeln manuell in ihre neue Version einbinden.

In der Kontrollinstanz müssen Versandvorlagen und externe Konten verknüpft werden. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie für jede Marke ein externes Konto mit demselben internen Namen wie in Schritt 1 definiert.
1. Erstellen Sie für jede Marke eine Standard-Versandvorlage.
1. Konfigurieren Sie in den **[!UICONTROL Eigenschaften]** der Versandvorlage das Routing zum externen Konto der Marke.

