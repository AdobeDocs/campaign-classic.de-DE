---
product: campaign
title: Mid-Sourcing-Server in Campaign installieren
description: In diesem Abschnitt werden die Installation und Konfiguration eines Mid-Sourcing-Servers in Campaign beschrieben
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: b500b2cbf68fd46bd84ddbfa71cf9431c6b60060
workflow-type: tm+mt
source-wordcount: '1061'
ht-degree: 3%

---

# Mid-Sourcing-Server{#mid-sourcing-server}



In diesem Abschnitt werden die Installation und Konfiguration eines Mid-Sourcing-Servers sowie die Bereitstellung einer -Instanz beschrieben, die es Dritten ermöglicht, Nachrichten im **Mid-Sourcing**-Modus zu senden.

Die „Mid-Sourcing“-Architektur wird in [Mid-Sourcing-Bereitstellung“ ](../../installation/using/mid-sourcing-deployment.md).

Die Installation eines Mid-Sourcing-Servers erfolgt auf die gleiche Weise wie die normale Installation eines Servers (siehe Standardkonfiguration). Es handelt sich um eine unabhängige Instanz mit einer eigenen Datenbank, die für die Ausführung von Sendungen verwendet werden kann. Einfach ausgedrückt: Es enthält eine zusätzliche Konfiguration, die es Remote-Instanzen ermöglicht, über sie Sendungen im Mid-Sourcing-Modus auszuführen.

>[!CAUTION]
>
>Nachdem der Mid-Sourcing-Server eingerichtet und die [Synchronisierungs-Workflows](../../workflow/using/about-technical-workflows.md) zum ersten Mal ausgeführt wurden, stellen Sie sicher, dass Sie den internen Namen der externen Mid-Sourcing-Konten nicht aktualisieren.

## Schritte zum Installieren und Konfigurieren einer Instanz {#steps-for-installing-and-configuring-an-instance}

### Voraussetzungen für die Installation und Konfiguration einer Instanz {#prerequisites-for-installing-and-configuring-an-instance}

* JDK auf dem Anwendungsserver
* Zugriff auf einen Datenbankserver auf dem Anwendungsserver.
* Firewall konfiguriert, um HTTP (80)- oder HTTPS (443)-Ports zum Mid-Sourcing-Server zu öffnen.

Im folgenden Verfahren wird eine Konfiguration mithilfe eines einzelnen Mid-Sourcing-Servers beschrieben. Es ist auch möglich, mehrere Server zu verwenden. Ebenso ist es möglich, bestimmte Nachrichten (z. B. Workflow-Benachrichtigungen) von einer internen Konfiguration aus zu senden.

### Installieren und Konfigurieren des Anwendungsservers für die Mid-Sourcing-Bereitstellung {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

Der Installationsvorgang ist mit dem von eigenständigen Instanzen identisch. Siehe [Installieren und Konfigurieren (ein Computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Sie müssen jedoch Folgendes anwenden:

* In Schritt **5** müssen Sie die Module **mta** (Versand) und **inMail** (Bounce Messages) deaktivieren. Das **wfserver**-Modul (Workflow) muss jedoch aktiviert bleiben.

  ```
  <?xml version='1.0'?>
  <serverconf>  
    <shared>    
      <!-- add lang="eng" to dataStore to force English for the instance -->    
      <dataStore hosts="console.campaign.net*">      
        <mapping logical="*" physical="default"/>    
      </dataStore>  </shared>  
      <mta autoStart="false"/>  
      <wfserver autoStart="true"/>  
      <inMail autoStart="false"/>  
      <sms autoStart="false"/>  
      <listProtect autoStart="false"/>
  </serverconf>
  ```

  Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../installation/using/configuring-campaign-server.md#enabling-processes).

* Die Schritte **6**, **9** und **10** sind nicht erforderlich.
* In den Schritten **12** und **13** müssen Sie den 8080-Port in der Verbindungs-URL angeben (da die Konsole direkt mit Tomcat kommuniziert, nicht über den Webserver). Die URL wird `http://console.campaign.net:8080`. Wählen Sie in Schritt **13** das Paket **[!UICONTROL Problem mit Mid-]**&quot; sowie die zu installierenden Pakete aus.

  ![](assets/s_ncs_install_midsourcing02.png)

  >[!CAUTION]
  >
  >Das Standard-Routing technischer Sendungen wird automatisch durch das E-Mail-Routing über Mid-Sourcing ersetzt.

### Installieren und Konfigurieren des Mid-Sourcing-Servers {#installing-and-configuring-the-mid-sourcing-server}

Suchen Sie in der Client-Konsole das **E-Mail-Routing mit Mid-Sourcing** Mid-Sourcing-Konto (im Ordner **/Administration/Externe Konten/** ). Füllen Sie die Einstellungen **URL des Servers**, **Account**, **Password** und **Mirrorseiten-URL** mit den Informationen, die vom Serveranbieter bereitgestellt werden, der den Mid-Sourcing-Server hostet. Testet die Verbindung

>[!NOTE]
>
>Mit **Option „Mid-Sourcing** Emitter“ werden zwei **Mid-Sourcing**-Workflows erstellt. Dieser Prozess wird standardmäßig alle 1 Stunde und 20 Minuten ausgeführt und erfasst Versandinformationen auf dem Mid-Sourcing-Server.

## Bereitstellen eines Mid-Sourcing-Servers {#deploying-a-mid-sourcing-server}

1. Installieren des Anwendungsservers:

   >[!CAUTION]
   >
   >Wenn Sie den Mid-Sourcing-Server installieren und zusätzliche Adobe Campaign-Module installieren möchten, empfehlen wir die Verwendung des Versandmoduls und nicht des Campaign-Moduls.

   Gehen Sie ebenso vor wie bei der Standardbereitstellung, indem Sie nur die Option **[!UICONTROL Mid-Sourcing-Plattform]** auswählen.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Konfiguration für den Empfang im Mid-Sourcing-Modus

   Legen Sie das Passwort für das Übermittlungskonto fest: Im Ordner **/Mid-Sourcing/Access Management/Operators/** wird der Operator **mid** von der Remote-Instanz für Übermittlungen im Mid-Sourcing-Modus verwendet. Sie müssen ein Kennwort für diesen Operator festlegen und es dem Administrator der Übermittlungsinstanz erteilen.

   Die Option **Mid-Sourcing** erstellt die Standardordner zum Speichern der gesendeten Sendungen und des Standardbenutzers, der die Übermittlungen durchführt.

## Multiplexing des Mid-Sourcing-Servers {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Multiplexing wird nur für On-Premise-Umgebungen unterstützt.

Es ist möglich, dass eine Mid-Sourcing-Instanz von mehreren sendenden Instanzen gemeinsam genutzt wird. Jede dieser Instanzen muss mit einem Benutzer in der Mid-Sourcing-Datenbank verknüpft sein. So erstellen Sie ein zweites Konto auf dem Mid-Sourcing-Server:

1. Erstellen Sie im Knoten **[!UICONTROL Mid-Sourcing > Sendungen]** einen Ordner, der mit dem standardmäßigen Mid-Sourcing-Konto verknüpft wird (z. B.: prod).
1. Erstellen Sie einen Ordner im Knoten **[!UICONTROL Mid-Sourcing > Sendungen]** mit demselben Namen wie das Konto (z. B.: accepted_test).

   ![](assets/mid_recette_account.png)

1. Erstellen **[!UICONTROL unter „Mid-Sourcing“ > „Zugriffsverwaltung“]** „Benutzer“ ein neues Konto.

   ![](assets/mid_recette_user_create.png)

1. Weisen Sie auf **[!UICONTROL Registerkarte]** Zugriffsrechte“ diesem Benutzer die Rechte der Gruppe **Mid-Sourcing-**&quot; zu. Dieses Zugriffsrecht finden Sie unter **[!UICONTROL Mid-Sourcing > Zugriffsverwaltung > Benutzergruppen]**.

   ![](assets/mid_recette_user_rights.png)

1. Wählen Sie die **[!UICONTROL Auf Daten in den Unterordnern von beschränken]** und wählen Sie den Versandordner aus, um diesen Benutzer auf den Mid-Sourcing-Versandordner zu beschränken.

   ![](assets/mid_recette_user_restrictions.png)

1. Starten Sie das Web-Modul mit dem folgenden Befehl neu: **&#x200B; web**.

Sie müssen die Mid-Sourcing-Server-Einstellung in der Datei „serverConf.xml“ ändern. Die folgende Zeile muss zum Abschnitt „Verwalten der Affinitäten mit IP-Adressen“ unter der vorhandenen Zeile hinzugefügt werden:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

Das Attribut &#39;@name&#39; muss die folgenden Regeln einhalten:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; bezieht sich auf den internen Namen des Mid-Sourcing-Kontos, das in der Mid-Sourcing-Instanz deklariert wurde.

„affinity_name“ bezieht sich auf den beliebigen Namen, der der Affinität gegeben wurde. Dieser Name muss eindeutig sein. Zulässige Zeichen sind `[a-z]` `[A-Z]` `[0-9]`. Ziel ist es, eine Gruppe von öffentlichen IP-Adressen zu deklarieren.

„affinity_group“ bezieht sich auf die Unteraffinität, die in dem Zielgruppen-Mapping deklariert wurde, das in jedem der Sendungen verwendet wird. Der letzte Teil, der das &quot;.“ wird ignoriert, wenn keine Unteraffinität vorliegt. Zulässige Zeichen sind `[a-z]` `[A-Z]` `[0-9]`.

Sie müssen den Server anhalten und dann neu starten, damit die Änderung übernommen wird.

## Konfigurieren des Trackings auf einem Mid-Sourcing-Server {#configuring-tracking-on-a-mid-sourcing-server}

**Mid-Sourcing-Server konfigurieren**

1. Navigieren Sie zu „Operatoren“ und wählen Sie den Operator **[!UICONTROL mid]** aus.
1. Geben **[!UICONTROL im Tab]** Frontserver“ die Verbindungsparameter des Trackingservers ein.

   Um eine Tracking-Instanz zu erstellen, geben Sie die URL des Tracking-Servers, das Passwort des internen Tracking-Servers und den Namen der Instanz, ihr Passwort und die damit verbundenen DNS-Masken ein.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Wenn Sie die Verbindungsparameter eingegeben haben, klicken Sie auf **[!UICONTROL Konfiguration bestätigen]**.
1. Geben Sie gegebenenfalls den Speicherort an, an dem in Sendungen enthaltene Bilder gespeichert werden sollen. Wählen Sie dazu einen der Veröffentlichungsmodi aus der Dropdownliste aus.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Wenn Sie die Option **[!UICONTROL Tracking-Server]** wählen, werden die Bilder auf den Mid-Sourcing-Server kopiert.

**Konfigurieren der Kundenplattform**

1. Zum externen Mid-Sourcing-Routing-Konto wechseln.
1. Geben Sie auf der Registerkarte **[!UICONTROL Mid-Sourcing]** die Verbindungsparameter für den Mid-Sourcing-Server an.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Bestätigen Sie Ihre Konfiguration durch Klicken auf **[!UICONTROL Verbindung testen]**.
1. Deklarieren Sie die Trackinginstanz, auf die auf dem Mid-Sourcing-Server verwiesen wird:

   Klicken Sie auf den Link **[!UICONTROL Diese Plattform als Proxy für den Zugriff auf die Tracking-Server verwenden]**,

   Geben Sie den Namen der Tracking-Instanz an und bestätigen Sie dann die Verbindung mit dem Tracking-Server.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Wenn der Nachrichtenversand von mehreren Mid-Sourcing-Servern verwaltet werden soll, wählen Sie die Option **[!UICONTROL Routing mit abwechselnden Mid-Sourcing-Konten]** und geben Sie die verschiedenen Server an.

![](assets/s_ncs_install_midsourcing_tracking04.png)
