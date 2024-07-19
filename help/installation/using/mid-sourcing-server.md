---
product: campaign
title: Mid-Sourcing-Server in Campaign installieren
description: In diesem Abschnitt wird die Installation und Konfiguration eines Mid-Sourcing-Servers in Campaign beschrieben.
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 3%

---

# Mid-Sourcing-Server{#mid-sourcing-server}



In diesem Abschnitt werden die Installation und Konfiguration eines Mid-Sourcing-Servers sowie die Bereitstellung einer Instanz beschrieben, die es Drittanbietern ermöglicht, Nachrichten im Modus **Mid-Sourcing** zu senden.

Die &quot;Mid-Sourcing&quot;-Architektur wird unter [Mid-Sourcing-Bereitstellung](../../installation/using/mid-sourcing-deployment.md) beschrieben.

Die Installation eines Mid-Sourcing-Servers erfolgt auf die gleiche Weise wie die normale Installation eines Servers (siehe Standardkonfiguration). Es handelt sich um eine unabhängige Instanz mit einer eigenen Datenbank, die für die Durchführung von Sendungen verwendet werden kann. Einfach ausgedrückt, enthält es eine zusätzliche Konfiguration, mit der Remote-Instanzen Sendungen im Mid-Sourcing-Modus ausführen können.

>[!CAUTION]
>
>Nachdem der Mid-Sourcing-Server eingerichtet wurde und die [Synchronisations-Workflows](../../workflow/using/about-technical-workflows.md) zum ersten Mal ausgeführt wurden, stellen Sie sicher, dass Sie den internen Namen der externen Mid-Sourcing-Konten nicht aktualisieren.

## Schritte zum Installieren und Konfigurieren einer Instanz {#steps-for-installing-and-configuring-an-instance}

### Voraussetzungen für die Installation und Konfiguration einer Instanz {#prerequisites-for-installing-and-configuring-an-instance}

* JDK auf dem Anwendungsserver.
* Zugriff auf einen Datenbankserver auf dem Anwendungsserver.
* Firewall konfiguriert, um HTTP (80)- oder HTTPS (443)-Ports zum Mid-Sourcing-Server zu öffnen.

Im folgenden Verfahren wird eine Konfiguration mit einem einzelnen Mid-Sourcing-Server beschrieben. Es ist auch möglich, mehrere Server zu verwenden. Ebenso ist es auch möglich, bestimmte Nachrichten (z. B. Workflow-Benachrichtigungen) aus einer internen Konfiguration zu senden.

### Installation und Konfiguration des Anwendungsservers für die Mid-Sourcing-Bereitstellung {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

Das Installationsverfahren entspricht dem der eigenständigen Instanz. Siehe [Installieren und Konfigurieren (einzelner Computer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Sie müssen jedoch Folgendes anwenden:

* Bei Schritt **5** müssen Sie die Module **mta** (delivery) und **inMail** (Bounce Messages) deaktivieren. Das Modul **wfserver** (Workflow) muss jedoch aktiviert bleiben.

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
* Während der Schritte **12** und **13** müssen Sie den 8080-Port in der Verbindungs-URL angeben (da die Konsole direkt mit Tomcat kommuniziert, nicht über den Webserver). Die URL wird zu `http://console.campaign.net:8080`. Wählen Sie im Schritt **13** das Paket **[!UICONTROL Problem gegenüber Mid-Sourcing]** sowie die zu installierenden Pakete aus.

  ![](assets/s_ncs_install_midsourcing02.png)

  >[!CAUTION]
  >
  >Das Standard-Routing technischer Sendungen wird automatisch durch E-Mail-Routing über Mid-Sourcing ersetzt.

### Mid-Sourcing-Server installieren und konfigurieren {#installing-and-configuring-the-mid-sourcing-server}

Suchen Sie in der Clientkonsole das **E-Mail-Routing mithilfe des Mid-Sourcing**-Mid-Sourcing-Kontos (im Ordner **/Administration/Externe Konten/** ). Füllen Sie die Einstellungen **URL des Servers**, **account**, **password** und **Mirrorseiten-URL** mit den Informationen aus, die vom Server-Provider bereitgestellt werden, der den Mid-Sourcing-Server hostet. Testet die Verbindung

>[!NOTE]
>
>Mit der Option **mid-sourcingEmitter** werden zwei **Mid-Sourcing**-Workflows erstellt. Dieser Prozess wird standardmäßig alle 1 Stunde und 20 Minuten ausgeführt und erfasst Versandinformationen auf dem Mid-Sourcing-Server.

## Bereitstellen eines Mid-Sourcing-Servers {#deploying-a-mid-sourcing-server}

1. Installieren des Anwendungsservers:

   >[!CAUTION]
   >
   >Wenn Sie den Mid-Sourcing-Server installieren und zusätzliche Adobe Campaign-Module installieren möchten, empfehlen wir die Verwendung des Versandmoduls und nicht des Campaign-Moduls.

   Gehen Sie genauso vor wie bei der Standardbereitstellung und wählen Sie nur die Option **[!UICONTROL Mid-Sourcing-Plattform]** aus.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Konfiguration für den Empfang im Mid-Sourcing-Modus

   Legen Sie das Passwort des Sendekontos fest: Im Ordner **/Mid-Sourcing/Access Management/Operators/** wird der Operator **mid** von der Remote-Instanz für Übermittlungen im Mid-Sourcing-Modus verwendet. Sie müssen ein Kennwort für diesen Benutzer festlegen und es dem Administrator der Sendeinstanz geben.

   Mit der Option **Mid-Sourcing-Plattform** werden die Standardordner zum Speichern der gesendeten Sendungen sowie der Standardoperator für die Übermittlung erstellt.

## Multiplexing des Mid-Sourcing-Servers {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Multiplexing wird nur für On-Premise-Umgebungen unterstützt.

Es ist möglich, dass eine Mid-Sourcing-Instanz von mehreren Sendeinstanzen gemeinsam genutzt wird. Jede dieser Instanzen muss mit einem Benutzer in der Mid-Sourcing-Datenbank verknüpft werden. So erstellen Sie ein zweites Konto auf dem Mid-Sourcing-Server:

1. Erstellen Sie im Knoten **[!UICONTROL Mid-Sourcing > Sendungen]** einen Ordner, der mit dem Standard-Mid-Sourcing-Konto verknüpft wird (z. B. prod).
1. Erstellen Sie im Knoten **[!UICONTROL Mid-Sourcing > Sendungen]** einen Ordner mit demselben Namen wie das Konto (z. B. accept_test).

   ![](assets/mid_recette_account.png)

1. Erstellen Sie in **[!UICONTROL Mid-Sourcing > Zugriffsverwaltung > Benutzer]** ein neues Konto.

   ![](assets/mid_recette_user_create.png)

1. Weisen Sie diesem Benutzer auf der Registerkarte **[!UICONTROL Zugriffsberechtigungen]** die Rechte der Gruppe **Mid-Sourcing-Übermittlungen** zu. Diese Zugriffsberechtigung ist in **[!UICONTROL Mid-Sourcing > Zugriffsverwaltung > Benutzergruppen]** verfügbar.

   ![](assets/mid_recette_user_rights.png)

1. Wählen Sie die Option **[!UICONTROL Auf Daten in den Unterordnern von]** beschränken und wählen Sie den Ordner Sendungen aus, um diesen Operator auf den Ordner Mid-Sourcing-Sendungen zu beschränken.

   ![](assets/mid_recette_user_restrictions.png)

1. Starten Sie das Webmodul mit dem folgenden Befehl neu: **nlserver restart web**.

Sie müssen die Mid-Sourcing-Server-Einstellung in der Datei serverConf.xml ändern. Die folgende Zeile muss im Abschnitt &quot;Verwaltung von Affinitäten mit IP-Adressen&quot;unter der vorhandenen Zeile hinzugefügt werden:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

Das Attribut &#39;@name&#39; muss die folgenden Regeln beachten:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; bezieht sich auf den internen Namen des Mid-Sourcing-Kontos, der in der Mid-Sourcing-Instanz deklariert wurde.

&#39;affinity_name&#39; bezieht sich auf den willkürlichen Namen, der der Affinität gegeben wird. Dieser Name muss eindeutig sein. Zulässige Zeichen sind `[a-z]``[A-Z]``[0-9]`. Ziel ist es, eine Gruppe öffentlicher IP-Adressen zu deklarieren.

&#39;affinity_group&#39; bezieht sich auf die Subaffinität, die im Zielgruppen-Mapping deklariert wurde, das in jedem Versand verwendet wird. Der letzte Teil, der &quot;.&quot;enthält wird ignoriert, wenn keine Unter-Affinität vorhanden ist. Zulässige Zeichen sind `[a-z]``[A-Z]``[0-9]`.

Sie müssen den Server stoppen und dann neu starten, damit die Änderung berücksichtigt wird.

## Tracking auf einem Mid-Sourcing-Server konfigurieren {#configuring-tracking-on-a-mid-sourcing-server}

**Konfigurieren des Mid-Sourcing-Servers**

1. Markieren Sie im Bildschirm &quot;Operatoren&quot;den Operator **[!UICONTROL mid]**.
1. Geben Sie auf der Registerkarte **[!UICONTROL Frontalserver]** die Verbindungsparameter des Tracking-Servers ein.

   Um eine Tracking-Instanz zu erstellen, geben Sie die URL des Tracking-Servers, das Passwort des internen Trackingservers und den Namen der Instanz, ihr Passwort und die damit verknüpften DNS-Masken ein.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Klicken Sie nach Eingabe der Verbindungsparameter auf **[!UICONTROL Konfiguration bestätigen]**.
1. Geben Sie bei Bedarf den Speicherort an, an dem die in Sendungen enthaltenen Bilder gespeichert werden sollen. Wählen Sie dazu einen der Veröffentlichungsmodi aus der Dropdown-Liste aus.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Wenn Sie die Option **[!UICONTROL Tracking-Server(s)]** auswählen, werden die Bilder auf den Mid-Sourcing-Server kopiert.

**Konfigurieren der Kundenplattform**

1. Gehen Sie zum externen Mid-Sourcing-Routing-Konto.
1. Geben Sie auf der Registerkarte **[!UICONTROL Mid-Sourcing]** die Verbindungsparameter für den Mid-Sourcing-Server an.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Bestätigen Sie Ihre Konfiguration durch Klicken auf **[!UICONTROL Verbindung testen]**.
1. Deklarieren Sie die auf dem Mid-Sourcing-Server referenzierte Tracking-Instanz:

   Klicken Sie auf den Link **[!UICONTROL Diese Plattform als Proxy verwenden, um auf die Tracking-Server zuzugreifen]**,

   Geben Sie den Namen der Tracking-Instanz an und bestätigen Sie dann die Verbindung mit dem Tracking-Server.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Wenn der Nachrichtenversand von mehreren Mid-Sourcing-Servern verwaltet werden soll, wählen Sie die Option **[!UICONTROL Routing mit abwechselnden Mid-Sourcing-Konten]** und geben Sie die verschiedenen Server an.

![](assets/s_ncs_install_midsourcing_tracking04.png)
