---
product: campaign
title: Transaktionsnachrichten-Architektur
description: In diesem Abschnitt werden die Transaktionsnachrichten-Architektur von Adobe Campaign Classic und die verfügbaren Kanäle für den Versand von Transaktionsnachrichten erläutert
feature: Transactional Messaging, Message Center, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
exl-id: 0a059397-b037-405b-b9c1-94a4a072674d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '1232'
ht-degree: 100%

---

# Transaktionsnachrichten-Architektur {#transactional-messaging-architecture}



Transaktionsnachrichten basieren auf einer Architektur, die sich aus mehreren Instanzen zusammensetzt:

* Eine **Kontrollinstanz**, auf der die Nachrichtenvorlagen erstellt werden.

* Eine oder mehrere **Ausführungsinstanzen**, auf denen die Ereignisse empfangen und von denen aus die Transaktionsnachrichten versendet werden.

![](assets/messagecenter_diagram.png)

| Kontrollinstanz | Ausführungsinstanz |
|--- |--- |
| Adobe Campaign-Benutzer melden sich bei der Kontrollinstanz an, um folgende Aktionen auszuführen: <ul><li>Erstellen der Transaktionsnachrichtenvorlagen</li><li>Erstellen der Nachrichtenvorschau mithilfe einer Liste von Testadressen</li><li>Anzeigen von Berichten</li><li>Überwachen der Ausführungsinstanzen</li></ul> | Ausführungsinstanzen dienen zur Ausführung folgender Aktionen: <ul><li>Empfangen von Ereignissen</li><li>Verknüpfen der Ereignisse mit Transaktionsnachrichtenvorlagen</li><li>Versenden einer personalisierten Nachricht an die einzelnen Empfänger</li></ul> |

## Installieren von Instanzen {#installing-instances}

Bei der Installation der Transaktionsnachrichten-Packages sind mehrere Vorsichtsmaßnahmen erforderlich. Es wird empfohlen, in einer Testumgebung zu arbeiten, bevor Sie in Produktion gehen. Des Weiteren ist der Besitz einer entsprechenden Adobe-Campaign-Lizenz erforderlich. Nehmen Sie für weiterführende Informationen mit Ihrem Adobe-Kundenbetreuer Kontakt auf.

>[!IMPORTANT]
>
>Die Kontroll- und die Ausführungsinstanz(en) müssen auf unterschiedlichen Computern installiert werden. Sie können aber nicht auf derselben Campaign-Instanz ausgeführt werden.

Wenn Sie mehrere Kanäle benötigen, müssen Sie die entsprechenden Packages installieren und konfigurieren, bevor Sie die Transaktionsnachrichten-Packages installieren. Weiterführende Informationen hierzu finden Sie unter [Hinzufügen von Versandkanälen](#adding-a-delivery-channel).

## Kontrollinstanz {#control-instance}

Um die Kontrollinstanz auf Ihrem System zu installieren, wählen Sie das Package **[!UICONTROL Transaktionsnachrichten-Kontrolle]** über das Menü **[!UICONTROL Werkzeuge]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package importieren]** aus. Weitere Informationen hierzu finden Sie unter [Installieren von nativen Campaign Classic-Packages](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_controlinstance_001.png)

Die detaillierten Schritte zur Konfiguration der Kontrollinstanz werden in [diesem Abschnitt](../../message-center/using/configuring-instances.md#control-instance) beschrieben.

### Unterstützung mehrerer Kontrollinstanzen {#supporting-several-control-instances}

>[!IMPORTANT]
>
>Die Freigabe eines Ausführungs-Clusters mit mehreren Kontrollinstanzen wird nur bei On-Premise-Umgebungen unterstützt.

Mehrere Kontrollinstanzen können einen Ausführungscluster gemeinsam nutzen. Wenn Sie beispielsweise unterschiedliche spezialisierte Marken führen, haben Sie die Möglichkeit, für jede Marke eine Kontrollinstanz zu konfigurieren und alle Kontrollinstanzen mit dem gleichen Ausführungscluster zu verbinden.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Weiterführende Informationen zur hierfür erforderlichen Konfiguration finden Sie unter [Mehrere Kontrollinstanzen verwenden](../../message-center/using/configuring-instances.md#using-several-control-instances).

## Ausführungsinstanz {#execution-instance}

Um eine Ausführungsinstanz auf Ihrem System zu installieren, wählen Sie das Package **[!UICONTROL Transaktionsnachrichten-Ausführung]** über das Menü **[!UICONTROL Werkzeuge]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Package importieren]** aus. Weitere Informationen hierzu finden Sie unter [Installieren von nativen Campaign Classic-Packages](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_executioninstance_001.png)

Die detaillierten Schritte zur Konfiguration einer Ausführungsinstanz finden Sie in [diesem Abschnitt](../../message-center/using/configuring-instances.md#execution-instance).

## Verfügbare Versandkanäle

Der E-Mail-Kanal ist standardmäßig verfügbar. Sie können Ihre Transaktionsnachrichten auf mehreren unterschiedlichen Kanälen versenden, indem Sie weitere Kanäle hinzufügen (z. B. Mobile-Kanal, Mobile-App-Kanal usw.).

>[!IMPORTANT]
>
>Das Hinzufügen eines Versandkanals (Mobile-Kanal, Mobile-App-Kanal usw.) muss vor der Installation des Transaktionsnachrichten-Packages durchgeführt werden.

### Hinzufügen von Versandkanälen {#adding-a-delivery-channel}

Es wird empfohlen, **das Versandkanal-Package grundsätzlich vor der Installation des Transaktionsnachrichten-Packages hinzuzufügen**.

Wenn Sie jedoch ein Transaktionsnachrichtenprojekt auf dem E-Mail-Kanal gestartet haben und dann während des Projekts entscheiden, einen neuen Kanal hinzuzufügen, können Sie die folgenden Schritte ausführen.

>[!NOTE]
>
>Dieses Verfahren gilt nur für Kunden, die einen Windows NLServer verwenden, der auf demselben Computer installiert ist, auf dem sie arbeiten.

1. Installieren Sie den benötigten Kanal, zum Beispiel den **mobilen Kanal**, mithilfe des Package-Import-Assistenten (**[!UICONTROL Tools > Erweitert > Package importieren... > Adobe Campaign-Package]**).
1. Führen Sie einen Dateiimport durch (**[!UICONTROL Tools > Erweitert > Package-Import... > Datei]**) und wählen Sie die Datei **datakitnms **`[Your language]`**packagemessageCenter.xml** aus.
1. Behalten Sie im Bereich **[!UICONTROL XML-Inhalt der zu importierenden Daten]** nur die Versandvorlage bei, die dem hinzugefügten Kanal entspricht. Wenn Sie beispielsweise den **mobilen Kanal** gewählt haben, behalten Sie nur das Element **Entitäten** bei, das der Vorlage **[!UICONTROL Mobil-Transaktionsnachricht]** (smsTriggerMessage) entspricht. Wenn Sie den **Mobile App-Kanal** hinzugefügt haben, behalten Sie nur die **iOS-Transaktionsnachricht** (iosTriggerMessage) und die **Android-Transaktionsnachricht** (androidTriggerMessage) bei.

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!IMPORTANT]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).-->

### Transaktions-Push-Benachrichtigung {#transactional-messaging-and-push-notifications}

In Kombination mit dem Mobile-App-Kanal-Modul können Sie über Benachrichtigungen Transaktionsnachrichten an Mobilgeräte senden.

>[!NOTE]
>
>Der Mobile-App-Kanal wird in [diesem Abschnitt](../../delivery/using/about-mobile-app-channel.md) im Detail beschrieben.

Um Transaktionsnachrichten-Module in Verbindung mit dem Mobile-App-Kanal zu nutzen, sind folgende Konfigurationen notwendig:

1. Installieren Sie das Package **Mobile App Channel** in den Kontroll- und Ausführungsinstanzen.
1. Replizieren Sie den Dienst sowie die Applikationen, die dieser in den Ausführungsinstanzen enthält.****

Das betreffende Ereignis muss folgende Elemente enthalten:

* Die Kennung des Mobilgeräts (**registrationId** für Android und **deviceToken** für iOS). Diese Kennung repräsentiert die &quot;Adresse&quot;, an die die Benachrichtigung gesendet wird.
* Die Definition der Relation zu der Mobile App oder dem Integrationsschlüssel (**uuid**), die den Abruf der App-spezifischen Verbindungsinformationen erlaubt.
* Den Kanal über den die Benachrichtigung gesendet wird (**wishedChannel**): 41 für iOS und 42 für Android.
* Alle für die Personalisierung nützlichen Daten.

Beispiel der Verarbeitung eines diese Informationen enthaltenden Ereignisses:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>Die Erstellung der Nachrichtenvorlagen folgt der üblichen Vorgehensweise.

### Transaktionsnachricht und LINE {#transactional-messaging-and-line}

In Kombination mit dem LINE-Kanal ermöglichen Ihnen Transaktionsnachrichten, Echtzeit-Nachrichten über die im Mobilgerät installierte LINE-App zu senden. Dies dient zum Senden der Willkommensnachricht, wenn ein LINE-Benutzer die Seite Ihrer Marke hinzufügt.

Um das Transaktionsnachrichtenmodul mit LINE zu verwenden, sind die folgenden Elemente zur Konfiguration Ihrer **Marketing-Instanz** und Ihrer Ausführungsinstanz **erforderlich**:

* Installieren Sie das Package **[!UICONTROL LINE Connect]** auf beiden Instanzen.
* Installieren Sie das Package **[!UICONTROL Transaktionsnachrichten-Kontrolle]** auf Ihrer Marketing-Instanz und das Package **[!UICONTROL Transaktionsnachrichten-Ausführung]** auf der Ausführungsinstanz.
* Erstellen Sie auf beiden Instanzen ein **externes LINE-Konto** und einen **LINE-Service** mit identischen Namen, damit sie synchronisiert werden können. Weiterführende Informationen dazu, wie Sie ein externes LINE-Konto und einen LINE-Service erstellen, finden Sie in [diesem Abschnitt](../../delivery/using/line-channel.md#setting-up-line-channel).

Konfigurieren Sie dann im **[!UICONTROL Explorer]** unter **[!UICONTROL Plattform]** > **[!UICONTROL Externes Konto]** unterschiedliche externe Konten auf beiden Instanzen:

1. Erstellen Sie in der **Ausführungsinstanz** das externe Konto **[!UICONTROL Externe Datenbank]** mit der folgenden Konfiguration:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Titel]** und **[!UICONTROL Interner Name]**: Benennen Sie Ihr externes Konto beliebig.
   * **[!UICONTROL Typ]**: Wählen Sie **[!UICONTROL Externe Datenbank]** .
   * Die Option **[!UICONTROL Aktiviert]** muss aktiviert sein.

   In der Kategorie **[!UICONTROL Verbindung]**:

   * **[!UICONTROL Typ]**: Wählen Sie Ihren Datenbankserver aus, z. B. PostgresSQL.
   * **[!UICONTROL Server]**: Geben Sie Ihre Datenbankserver-URL ein.
   * **[!UICONTROL Konto]**: Geben Sie Ihr Datenbankkonto ein.

     >[!NOTE]
     >
     >Ein Datenbankbenutzer benötigt für die FDA-Verbindung Lesezugriff auf die folgenden Tabellen: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRtEvent, NmsBatchEvent, NmsBroadLogMsg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Passwort]**: Geben Sie das Passwort für Ihr Datenbankkonto ein.
   * **[!UICONTROL Datenbank]**: Geben Sie den Datenbanknamen der Ausführungsinstanz ein.
   * Die Option **[!UICONTROL Ziel des &#39;HTTP-Weiterleitung auf Remote-Datenbank&#39; Kontos]** muss aktiviert sein.

1. Erstellen Sie in der **Marketing-Instanz** das Konto **[!UICONTROL Externe Datenbank]** mit der folgenden Konfiguration:

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Titel]** und **[!UICONTROL Interner Name]**: Benennen Sie Ihr externes Konto beliebig.
   * **[!UICONTROL Typ]**: Wählen Sie **[!UICONTROL Externe Datenbank]** .
   * Die Option &quot;Aktiviert&quot; muss aktiviert sein.

   In der Kategorie **[!UICONTROL Verbindung]**:

   * **[!UICONTROL Typ]**: Wählen Sie **[!UICONTROL HTTP-Weiterleitung auf Remote-Datenbank]** aus .
   * **[!UICONTROL Server]**: Geben Sie die Kampagnenserver-URL der Ausführungsinstanz ein.
   * **[!UICONTROL Konto]**: Geben Sie das Konto ein, über das auf Ihre Ausführungsinstanz zugegriffen wird.
   * **[!UICONTROL Passwort]**: Geben Sie das Passwort für das Konto ein, über das auf Ihre Ausführungsinstanz zugegriffen wird.
   * **[!UICONTROL Datenquelle]**: Geben Sie die Syntax **[!UICONTROL nms:extAccount:ID Ihres externen Datenbankkontos in die ausführende Instanz]** ein.

1. Erstellen Sie in der **Marketing-Instanz** das externe Konto **[!UICONTROL Ausführungsinstanz]** mit der folgenden Konfiguration, um den Datensynchronisations-Workflow zu erstellen:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Titel]** und **[!UICONTROL Interner Name]**: Benennen Sie Ihr externes Konto beliebig.
   * **[!UICONTROL Typ]**: Wählen Sie **[!UICONTROL Ausführungsinstanz]** aus .
   * Die Option &quot;Aktiviert&quot; muss aktiviert sein.

   In der Kategorie **[!UICONTROL Verbindung]**:

   * **[!UICONTROL URL]**: Geben Sie die URL der Ausführungsinstanz ein.
   * **[!UICONTROL Konto]**: Geben Sie das Konto ein, über das auf Ihre Ausführungsinstanz zugegriffen wird.
   * **[!UICONTROL Passwort]**: Geben Sie das Passwort für das Konto ein, über das auf Ihre Ausführungsinstanz zugegriffen wird.

   In der Kategorie **[!UICONTROL Konto-Verbindungsmethode]**:

   * **[!UICONTROL Methode]**: Wählen Sie **[!UICONTROL Federated Data Access (FDA)]** aus.
   * **[!UICONTROL FDA-Konto]**: Wählen Sie Ihr FDA-Konto aus der Dropdown-Liste aus.
   * Wählen Sie die Schaltfläche **[!UICONTROL Archivierungs-Workflow erstellen]** aus.
   * Wählen Sie die Schaltfläche **[!UICONTROL Datensynchronisations-Workflow erstellen]** aus, um den LINE-Datensynchronisations-Workflow zu erstellen.

1. Sie können jetzt mit dem [Erstellen von Transaktionsnachrichten](../../message-center/using/creating-the-message-template.md) beginnen.
