---
title: Adobe Campaign Classic-Architektur für Transaktionsnachrichten
description: In diesem Abschnitt wird die transaktionale Messaging-Architektur von Adobe Campaign Classic beschrieben.
page-status-flag: never-activated
uuid: a8fe7a37-6df7-49f4-838f-97a72e4a38f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: a910d5fe-cef4-47d8-b3bc-0055ef0d1afd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Transaktionsnachrichten-Architektur{#transactional-messaging-architecture}

## Über Ausführungs- und Kontrollinstanzen {#about-execution-and-control-instances}

Die Transaktionsnachrichtenfunktion in Adobe Campaign (auch Message Center genannt) gewährleistet optimale Skalierbarkeit und Rund-um-die-Uhr-Betrieb. Hierfür besteht die Anwendung aus mehreren Instanzen:

* mindestens einer Kontrollinstanz, in der die Nachrichtenvorlagen erstellt werden;
* einer oder mehrerer Ausführungsinstanzen, in denen die Ereignisse empfangen und Transaktionsnachrichten versandt werden.

Um diese Funktionen zu nutzen, können Benutzer von Adobe Campaign in der Kontrollinstanz Vorlagen für Transaktionsnachrichten erstellen, eine Nachrichtenvorschau mithilfe einer Testadresse erzeugen, Berichte anzeigen und Ausführungsinstanzen überwachen.

Ausführungsinstanzen empfangen die Ereignisse des Informationssystems, ordnen diese den verfügbaren Transaktionsnachrichten-Vorlagen zu und senden schließlich jedem Kontakt auf den Vorlagen basierende personalisierte Nachrichten.

![](assets/messagecenter_diagram.png)

## Mehrere Kontrollinstanzen {#supporting-several-control-instances}

>[!CAUTION]
>
>Die Freigabe eines Ausführungsclusters mit mehreren Steuerungsinstanzen wird nur für lokale Umgebungen unterstützt.

Mehrere Kontrollinstanzen können einen Ausführungscluster gemeinsam nutzen. Wenn Sie beispielsweise unterschiedliche spezialisierte Marken führen, haben Sie die Möglichkeit, für jede Marke eine Kontrollinstanz zu konfigurieren und alle Kontrollinstanzen mit dem gleichen Ausführungscluster zu verbinden.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Weitere Informationen zur erforderlichen Konfiguration finden Sie unter [Verwenden mehrerer Steuerinstanzen](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances).

## Instanzeninstallation {#installing-instances}

Bei der Installation der Transaktionsnachrichten-Packages sind mehrere Vorsichtsmaßnahmen erforderlich. Es wird empfohlen, in einer Testumgebung zu arbeiten, bevor Sie in Produktion gehen. Des Weiteren ist der Besitz einer entsprechenden Adobe-Campaign-Lizenz erforderlich. Nehmen Sie für weiterführende Informationen mit Ihrem Adobe-Kundenbetreuer Kontakt auf.

>[!CAUTION]
>
>Die Kontroll- und die Ausführungsinstanz(en) müssen auf unterschiedlichen Computern installiert werden. Sie können aber nicht auf derselben Campaign-Instanz ausgeführt werden.

Wenn Sie mehrere Kanäle verwenden müssen, müssen Sie zugehörige Pakete installieren und konfigurieren, bevor Sie Transaktionsnachrichten installieren. Siehe [Hinzufügen eines Bereitstellungskanals](#adding-a-delivery-channel).

* To install the control instance on your machine, select the **[!UICONTROL Transactional message control]** module.

   ![](assets/messagecenter_install_controlinstance_001.png)

* To install the execution instance on your machine, select the **[!UICONTROL Transactional message execution]** module.

   ![](assets/messagecenter_install_executioninstance_001.png)

## Hinzufügen von Versandkanälen {#adding-a-delivery-channel}

Versandkanäle (Mobile (SMS), Mobile App etc.) müssen unbedingt vor der Installation der Transaktionsnachrichten-Packages hinzugefügt werden. Falls Sie bereits ein Transaktionsnachrichten-Projekt über den E-Mail-Kanal begonnen haben und im Laufe des Projekts einen weiteren Kanal hinzufügen möchten, gehen Sie wie folgt vor:

1. Installieren Sie den Kanal, den Sie benötigen, z. B. den **Mobilkanal**, mithilfe des Paketimportassistenten ( **[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** ).
1. Führen Sie einen Dateiimport ( **[!UICONTROL Tools > Advanced > Import package... > File]** ) durch und wählen Sie die Datei ****`[Your language]`**datakitnmspackagedageCenter.xml** .
1. Behalten Sie in **[!UICONTROL XML content of the data to import]** nur die Bereitstellungsvorlage bei, die dem hinzugefügten Kanal entspricht. Wenn Sie beispielsweise den **Mobilkanal** hinzugefügt haben, sollten Sie nur das **Entitätselement** beibehalten, das dem Element entspricht **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Wenn Sie den **Mobilanwendungskanal** hinzugefügt haben, behalten Sie nur die **iOS-Transaktionsmeldung** (iosTriggerMessage) und die **Android-Transaktionsmeldung** (androidTriggerMessage) bei.

   ![](assets/messagecenter_install_channel.png)

## Transaktionsnachrichten und eingehende Interaktion {#transactional-messages-and-inbound-interaction}

In Kombination mit dem Interaktionsmodul können den Transaktionsnachrichten personalisierte Angebote hinzugefügt werden.

>[!NOTE]
>
>Weiterführende Informationen zum Interaktionsmodul finden Sie im Abschnitt [Interaction](../../interaction/using/interaction-and-offer-management.md).

Um Transaktionsnachrichten in Verbindung mit Interaction zu nutzen, sind folgende Konfigurationen notwendig:

* Installieren Sie das Package **Interaction** in den Kontrollinstanzen und erstellen Sie einen Angebotskatalog.

   >[!CAUTION]
   >
   >Replizieren Sie die erstellten Angebote nicht in den Ausführungsinstanzen.

* Um die Angebote zu personalisieren, muss das betreffende Ereignis eine mit dem Empfänger verknüpfte Kennung enthalten. Der Wert dieser Kennung wird im Attribut **@externalID** festgeschrieben. **Interaction** ist standardmäßig so konfiguriert, dass der Empfänger über den Primärschlüssel identifiziert wird:

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
   ```

   Sie können **Interaction** auch dahingehend konfigurieren, dass die Identifizierung über ein Feld Ihrer Wahl erfolgt, beispielsweise die E-Mail-Adresse:

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
   ```

Erstellen Sie Ihre Versandvorlagen auf die gleiche Weise wie für E-Mail-Kampagnen:

* Fügen Sie das Angebot in die betreffende Transaktionsnachrichten-Vorlage ein.
* Überprüfen Sie die Vorschau, führen Sie einen Testversand durch und veröffentlichen Sie die Vorlage.

Der Einzelmodus muss auch bei den Angebotsplatzierungen aktiviert werden, siehe [diesen Abschnitt](../../interaction/using/creating-offer-spaces.md).

## Transaktionsnachrichten und Push-Benachrichtigungen {#transactional-messaging-and-push-notifications}

In Kombination mit dem Mobile-App-Kanal-Modul können Sie über Benachrichtigungen Transaktionsnachrichten an Mobilgeräte senden.

>[!NOTE]
>
>Der Mobile-App-Kanal wird in [diesem Abschnitt](../../delivery/using/about-mobile-app-channel.md) im Detail beschrieben.

Um Transaktionsnachrichten-Module in Verbindung mit dem Mobile-App-Kanal zu nutzen, sind folgende Konfigurationen notwendig:

1. Installieren Sie das Package **Mobile App Channel** in den Kontroll- und Ausführungsinstanzen.
1. Replizieren Sie den Dienst sowie die Applikationen, die dieser in den Ausführungsinstanzen enthält.****

Das betreffende Ereignis muss folgende Elemente enthalten:

* Die Kennung des Mobilgeräts (**registrationID** für Android und **deviceToken** für iOS). Diese Kennung repräsentiert die &quot;Adresse&quot;, an die die Benachrichtigung gesendet wird.
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

## Transaktionsnachricht und LINE {#transactional-messaging-and-line}

In Kombination mit dem LINE-Kanal ermöglichen Ihnen Transaktionsnachrichten, Echtzeit-Nachrichten über die im Mobilgerät installierte LINE-App zu senden. Dies dient zum Senden der Willkommensnachricht, wenn ein LINE-Benutzer die Seite Ihrer Marke hinzufügt.

Um das Transaktionsnachrichtenmodul mit LINE zu verwenden, sind die folgenden Elemente zur Konfiguration Ihrer **Marketinginstanz** und Ihrer Ausführungsinstanz **erforderlich**:

* Install the **[!UICONTROL LINE Connect]** package on both instances.
* Installieren Sie das **[!UICONTROL Transactional message control]** Paket auf Ihrer Marketing-Instanz und das **[!UICONTROL Transactional message execution]** -Paket auf der Ausführungsinstanz.
* Erstellen Sie ein **externes LINE-Konto** und den entsprechenden **Service** auf beiden Instanzen mit identischen Namen, damit sie synchronisiert werden können. Weiterführende Informationen zum Erstellen eines externen LINE-Kontos und Services finden Sie auf dieser [Seite](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-).

Then, from the **[!UICONTROL Explorer]** , in **[!UICONTROL Platform]** > **[!UICONTROL External account]** , you need to configure different external accounts on both instances:

1. Create an **[!UICONTROL External database]** external account in your **execution** instance with the following configuration:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** und **[!UICONTROL Internal name]** : Benennen Sie Ihr externes Konto nach Bedarf.
   * **[!UICONTROL Type]** : auswählen **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]** muss markiert werden.
   Aus der **[!UICONTROL Connection]** Kategorie:

   * **[!UICONTROL Type]** : Wählen Sie Ihren Datenbankserver, z.B. PostgresSQL.
   * **[!UICONTROL Server]** : Geben Sie Ihre Datenbankserver-URL ein.
   * **[!UICONTROL Account]** : Geben Sie Ihr Datenbankkonto ein.

      >[!NOTE]
      >
      >Ein Datenbankbenutzer benötigt für die FDA-Verbindung Lesezugriff auf die folgenden Tabellen: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRtEvent, NmsBatchEvent, NmsBroadLogMsg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Password]** : Geben Sie das Kennwort für Ihr Datenbankkonto ein.
   * **[!UICONTROL Database]** : Geben Sie den Datenbanknamen der Ausführungsinstanz ein.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** muss markiert werden.


1. Create an **[!UICONTROL External Database]** account in your **marketing** instance with the following configuration.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** und **[!UICONTROL Internal name]** : Benennen Sie Ihr externes Konto nach Bedarf.
   * **[!UICONTROL Type]** : auswählen **[!UICONTROL External database]** .
   * Die Option &quot;Aktiviert&quot; muss aktiviert sein.
   Aus der **[!UICONTROL Connection]** Kategorie:

   * **[!UICONTROL Type]** : auswählen **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : Geben Sie die Kampagnenserver-URL der Ausführungsinstanz ein.
   * **[!UICONTROL Account]** : Geben Sie das Konto ein, das für den Zugriff auf Ihre Ausführungsinstanz verwendet wird.
   * **[!UICONTROL Password]** : Geben Sie das Kennwort für das Konto ein, das für den Zugriff auf Ihre Ausführungsinstanz verwendet wird.
   * **[!UICONTROL Data Source]** : Geben Sie die folgende Syntax ein **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** .


1. Create an **[!UICONTROL Execution instance]** external account in your **marketing** instance using the following configuration to create the data synchronization workflow:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** und **[!UICONTROL Internal name]** : Benennen Sie Ihr externes Konto nach Bedarf.
   * **[!UICONTROL Type]** : auswählen **[!UICONTROL Execution instance]** .
   * Die Option &quot;Aktiviert&quot; muss aktiviert sein.
   Aus der **[!UICONTROL Connection]** Kategorie:

   * **[!UICONTROL URL]** : Geben Sie die URL der Ausführungsinstanz ein.
   * **[!UICONTROL Account]** : Geben Sie Ihr Konto ein, das für den Zugriff auf Ihre Ausführungsinstanz verwendet wird.
   * **[!UICONTROL Password]** : Geben Sie das Kennwort für das Konto ein, das für den Zugriff auf Ihre Ausführungsinstanz verwendet wird.
   Aus der **[!UICONTROL Account connection method]** Kategorie:

   * **[!UICONTROL Method]** : auswählen **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : Wählen Sie Ihr FDA-Konto aus der Dropdownliste.
   * Click the **[!UICONTROL Create the archiving workflow]** button.
   * Klicken Sie auf die **[!UICONTROL Create data synchronization workflow]** Schaltfläche, um den LINE-Arbeitsablauf für die Datensynchronisierung zu erstellen.



1. Jetzt können Sie Transaktionsnachrichten erstellen. Weiterführende Informationen dazu finden Sie auf dieser [Seite](../../message-center/using/introduction.md).
