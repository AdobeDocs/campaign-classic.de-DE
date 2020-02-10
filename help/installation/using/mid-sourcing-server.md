---
title: Installieren eines Servers mit mittlerer Quelle in Adobe Campaign Classic
description: In diesem Abschnitt wird die Installation und Konfiguration eines Servers mit mittlerer Quelle in Adobe Campaign Classic beschrieben.
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Server mit mittlerer Quelle{#mid-sourcing-server}

Dieser Abschnitt beschreibt die Installation und Konfiguration eines Servers mit mittlerer Quelle sowie die Bereitstellung einer Instanz, die es Dritten ermöglicht, Nachrichten im **Mid-Sourcing** -Modus zu senden.

Die &quot;Mid-Sourcing&quot;-Architektur wird im [Mid-Sourcing-Einsatz](../../installation/using/mid-sourcing-deployment.md)vorgestellt.

Die Installation eines Servers mit mittlerer Quelle erfolgt auf die gleiche Weise wie die Installation eines Servers auf die normale Weise (siehe Standardkonfiguration). Es handelt sich um eine unabhängige Instanz mit einer eigenen Datenbank, die zur Ausführung von Auslieferungen verwendet werden kann. Einfach ausgedrückt, enthält es eine zusätzliche Konfiguration, damit Remote-Instanzen Auslieferungen im Mid-Sourcing-Modus ausführen können.

## Schritte zum Installieren und Konfigurieren einer Instanz {#steps-for-installing-and-configuring-an-instance}

### Voraussetzungen für die Installation und Konfiguration einer Instanz {#prerequisites-for-installing-and-configuring-an-instance}

* JDK auf dem Anwendungsserver.
* Zugriff auf einen Datenbankserver auf dem Anwendungsserver.
* Firewall konfiguriert, um HTTP (80)- oder HTTPS (443)-Anschlüsse an den mid-sourcing-Server zu öffnen.

Im folgenden Verfahren wird eine Konfiguration mit einem einzelnen mid-sourcing-Server beschrieben. Es ist auch möglich, mehrere Server zu verwenden. Ebenso ist es möglich, bestimmte Nachrichten (z. B. Workflow-Benachrichtigungen) aus einer internen Konfiguration zu senden.

### Installieren und Konfigurieren des Anwendungsservers für die Bereitstellung mit mittlerer Quelle {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

Der Installationsvorgang ist identisch mit dem der eigenständigen Instanz. Siehe [Installieren und Konfigurieren (Einzelcomputer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Sie müssen jedoch Folgendes anwenden:

* In Schritt **5** müssen Sie die Module &quot; **mta** &quot;(Lieferung) und &quot; **inMail** &quot;(Absprung-Mails) deaktivieren. Das **wfserver** -Modul (Workflow) muss jedoch aktiviert bleiben.

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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

* Die Schritte **6**, **9** und **10** sind nicht erforderlich.
* In den Schritten **12** und **13** müssen Sie den 8080-Anschluss in der Verbindungs-URL angeben (da die Konsole direkt mit Tomcat kommuniziert, nicht über den Webserver). Die URL lautet [http://console.campaign.net:8080](http://console.campaign.net). Wählen Sie während Schritt **13** das **[!UICONTROL Issue towards Mid-sourcing]** Paket sowie die zu installierenden Pakete aus.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Die Standardweiterleitung technischer Auslieferungen wird automatisch durch E-Mail-Weiterleitung über Mid-Sourcing ersetzt.

### Installieren und Konfigurieren des Mid-Sourcing-Servers {#installing-and-configuring-the-mid-sourcing-server}

Suchen Sie in der Client-Konsole das **E-Mail-Routing mit dem Mid-Sourcing** -Konto (im Ordner **/Administration/Externe Konten/** ). Füllen Sie die **URL der URL**-Einstellungen für Server, **Konto**, **Kennwort** und **Mirror-Seite mit den Informationen, die der Serveranbieter, der den mid-Sourcing-Server hostet, bereitstellt** . Verbindung testen.

>[!NOTE]
>
>Die **Option &quot;mid-sourcingEmitter** &quot;erstellt zwei **Mid-Sourcing** -Workflows. Es handelt sich dabei um einen Prozess, der standardmäßig alle 1 Stunde und 20 Minuten ausgeführt wird und auf dem Midsourcing-Server Auslieferungsinformationen erfasst.

## Bereitstellen eines Servers mit mittlerer Quelle {#deploying-a-mid-sourcing-server}

1. Anwendungsserver installieren:

   >[!CAUTION]
   >
   >Wenn Sie den mid-Sourcing-Server installieren und zusätzliche Adobe Campaign-Module installieren möchten, empfehlen wir die Verwendung des Bereitstellungsmoduls und nicht des Kampagnenmoduls.

   Gehen Sie wie bei der Standardbereitstellung vor und wählen Sie nur die **[!UICONTROL Mid-sourcing platform]** Option aus.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Konfiguration für den Empfang im mid-sourcing-Modus

   Legen Sie das Kennwort für das Übermittlungskonto fest: Im Ordner **/Mid-Sourcing/Access Management/Operators/** wird der **Mid** -Operator von der Remote-Instanz für Übermittlungen im Mid-Sourcing-Modus verwendet. Sie müssen ein Kennwort für diesen Operator festlegen und es an den Administrator der Sendeinstanz übergeben.

   Mit der Option **Mittelbeschaffungsplattform** werden die Standardordner zum Speichern der gesendeten Auslieferungen und der Standardoperator zum Ausführen der Übermittlungen erstellt.

## Multiplexing des mid-sourcing-Servers {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Multiplexing wird nur für lokale Umgebungen unterstützt.

Es ist möglich, dass eine Mid-Sourcing-Instanz von mehreren Sendeinstanzen gemeinsam verwendet wird. Jede dieser Instanzen muss mit einem Operator in der Mid-Sourcing-Datenbank verknüpft sein. So erstellen Sie ein zweites Konto auf dem Server mit mittlerer Quelle:

1. Erstellen Sie einen Ordner im **[!UICONTROL Mid-sourcing > Deliveries]** Knoten, der mit dem Standard-Mid-Sourcing-Konto verknüpft wird (z. B.: prod).
1. Erstellen Sie einen Ordner im **[!UICONTROL Mid-sourcing > Deliveries]** Knoten mit demselben Namen wie das Konto (z. B.: accept_test).

   ![](assets/mid_recette_account.png)

1. Erstellen Sie **[!UICONTROL Mid-sourcing > Access Management > Operators]** in ein neues Konto.

   ![](assets/mid_recette_user_create.png)

1. Weisen Sie diesem Bediener auf der **[!UICONTROL Access rights]** Registerkarte die Rechte der Gruppe mit **mittelgroßen** Übermittlungen zu. Dieses Zugriffsrecht ist in verfügbar **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Wählen Sie die **[!UICONTROL Restrict to data in the sub-folders of]** Option und wählen Sie den Ordner &quot;Delivery&quot;, um diesen Operator auf den Ordner &quot;Mid-Sourcing Delivery&quot;zu beschränken.

   ![](assets/mid_recette_user_restrictions.png)

1. Starten Sie das Webmodul mit dem folgenden Befehl neu: nlserver **startet Web** neu.

Sie müssen die Einstellung für den mid-sourcing-Server in der Datei &quot;serverConf.xml&quot;ändern. Im Abschnitt &quot;Verwaltung von Affinitäten mit IP-Adressen&quot; muss unter der vorhandenen Zeile folgende Zeile hinzugefügt werden:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

Das Attribut &quot;@name&quot;muss die folgenden Regeln beachten:

**&#39;marketing_account_operator_name&#39;.affinität_name&#39;.&#39;affinität_group&#39;**

&#39;marketing_account_operator_name&#39; bezieht sich auf den internen Namen des Midsourcing-Kontos, der in der mid-sourcing-Instanz deklariert wurde.

&#39;affinitätsname&#39; bezieht sich auf den willkürlichen Namen, der der Affinität gegeben wird. Dieser Name muss eindeutig sein. Autorisierte Zeichen sind `[a-z]``[A-Z]``[0-9]`zulässig. Ziel ist es, eine Gruppe öffentlicher IP-Adressen zu deklarieren.

&quot;affinity_group&quot;bezieht sich auf die Subaffinität, die in der Zielzuordnung, die in jeder Lieferung verwendet wird, deklariert wurde. Der letzte Teil einschließlich des &#39;.&#39; wird ignoriert, wenn keine Subaffinität vorhanden ist. Autorisierte Zeichen sind `[a-z]``[A-Z]``[0-9]`zulässig.

Sie müssen den Server beenden und dann neu starten, damit die Änderung berücksichtigt wird.

## Konfigurieren der Verfolgung auf einem Server mit mittlerer Quelle {#configuring-tracking-on-a-mid-sourcing-server}

**Konfigurieren des Mid-Sourcing-Servers**

1. Gehen Sie zu &quot;Operatoren&quot;und wählen Sie den Operator **[!UICONTROL mid]**.
1. Geben Sie auf der **[!UICONTROL Frontal servers]** Registerkarte die Verbindungsparameter des Tracking-Servers ein.

   Um eine Verfolgungsinstanz zu erstellen, geben Sie die URL des Trackingservers, das Kennwort des internen Trackingservers und den Namen der Instanz, ihr Kennwort und die damit verknüpften DNS-Masken ein.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Klicken Sie nach Eingabe der Verbindungsparameter auf **[!UICONTROL Confirm the configuration]**.
1. Geben Sie bei Bedarf den Speicherort an, an dem die in den Auslieferungen enthaltenen Bilder gespeichert werden sollen. Wählen Sie dazu einen der Veröffentlichungsmodi aus der Dropdownliste aus.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Wenn Sie die **[!UICONTROL Tracking server(s)]** Option auswählen, werden die Bilder auf den mid-sourcing-Server kopiert.

**Kundenplattform konfigurieren**

1. Wechseln Sie zum externen Routing-Konto für die mittlere Suche.
1. Geben Sie auf der **[!UICONTROL Mid-Sourcing]** Registerkarte die Verbindungsparameter für den Server mit mittlerer Quelle an.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Überprüfen Sie Ihre Konfiguration durch Klicken auf **[!UICONTROL Test the connection]**.
1. Deklarieren Sie die auf dem mid-sourcing-Server referenzierte Verfolgungsinstanz:

   Klicken Sie auf den Link **[!UICONTROL Use this platform as a platform to access the tracking servers]**,

   Geben Sie den Namen der Verfolgungsinstanz an und bestätigen Sie dann die Verbindung mit dem Tracking-Server.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Wenn die Bereitstellung von Nachrichten von mehreren Servern mit mittlerer Quelle verwaltet werden soll, wählen Sie die Option **[!UICONTROL Routing with alternating mid-sourcing accounts]** und geben Sie die verschiedenen Server an.

![](assets/s_ncs_install_midsourcing_tracking04.png)

