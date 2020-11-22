---
solution: Campaign Classic
product: campaign
title: Installieren eines Mid-Sourcing-Servers in der Kampagne
description: In diesem Abschnitt finden Sie Informationen zur Installation und Konfiguration eines Mid-Sourcing-Servers in der Kampagne
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---


# Mid-Sourcing-Server{#mid-sourcing-server}

Dieser Abschnitt beschreibt die Installation und Konfiguration eines Mid-Sourcing-Servers sowie die Bereitstellung einer Instanz, die es Dritten ermöglicht, Nachrichten im **Mid-Sourcing** -Modus zu senden.

Die &quot;Mid-Sourcing&quot;-Architektur wird bei der Bereitstellung von [Mid-Sourcing](../../installation/using/mid-sourcing-deployment.md)vorgestellt.

Die Installation eines Mid-Sourcing-Servers erfolgt auf die gleiche Weise wie die Installation eines Servers auf die normale Weise (siehe Standardkonfiguration). Es handelt sich um eine unabhängige Instanz mit einer eigenen Datenbank, die zum Ausführen von Versänden verwendet werden kann. Einfach ausgedrückt enthält es eine zusätzliche Konfiguration, damit Remote-Instanzen Versand im Mid-Sourcing-Modus ausführen können.

>[!CAUTION]
>
>Nachdem der Mid-Sourcing-Server eingerichtet und die [Synchronisierung Workflows](../../workflow/using/transfer-to-mid-sourcing.md) zum ersten Mal ausgeführt wurde, sollten Sie sicherstellen, dass der interne Name der Mid-Sourcing-Externe Konti nicht aktualisiert wird.

## Schritte zum Installieren und Konfigurieren einer Instanz {#steps-for-installing-and-configuring-an-instance}

### Voraussetzungen für die Installation und Konfiguration einer Instanz {#prerequisites-for-installing-and-configuring-an-instance}

* JDK auf dem Anwendungsserver.
* Zugriff auf einen Datenbankserver auf dem Anwendungsserver.
* Firewall, die zum Öffnen von HTTP (80)- oder HTTPS (443)-Anschlüssen auf dem Mid-Sourcing-Server konfiguriert ist.

Im folgenden Verfahren wird eine Konfiguration mit einem einzelnen Mid-Sourcing-Server beschrieben. Es ist auch möglich, mehrere Server zu verwenden. Ebenso ist es möglich, bestimmte Nachrichten (z. B. Workflow-Benachrichtigungen) aus einer internen Konfiguration zu senden.

### Installieren und Konfigurieren des Anwendungsservers für die Bereitstellung von Mid-Sourcing {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

Der Installationsvorgang ist identisch mit dem der eigenständigen Instanz. Weitere Informationen finden Sie unter [Installieren und Konfigurieren (Einzelcomputer)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Sie müssen jedoch Folgendes anwenden:

* In Schritt **5** müssen Sie die Module &quot; **mta** &quot;(Versand) und &quot; **inMail** &quot;(Absprung-Mails) deaktivieren. Das **wfserver** -Modul (Workflow) muss jedoch aktiviert bleiben.

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
* In den Schritten **12** und **13** müssen Sie den 8080-Anschluss in der Verbindungs-URL angeben (da die Konsole direkt mit Tomcat kommuniziert, nicht über den Webserver). Die URL lautet [http://console.campaign.net:8080](http://console.campaign.net). Wählen Sie im Schritt **13** das **[!UICONTROL Problem mit dem Mid-Sourcing]** -Paket sowie die zu installierenden Probleme aus.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Das Standard-Routing technischer Versand wird automatisch durch E-Mail-Routing über Mid-Sourcing ersetzt.

### Installieren und Konfigurieren des Mid-Sourcing-Servers {#installing-and-configuring-the-mid-sourcing-server}

Suchen Sie in der Client-Konsole das **E-Mail-Routing mit dem Mid-Sourcing** -Mid-Sourcing-Konto (im Ordner **/Administration/Externe Konti/** ). Füllen Sie die **URL der Einstellungen für Server**, **Konto**, **Kennwort** und **Mirrorseiten-URL** mit den Informationen, die der Serveranbieter, der den Mid-Sourcing-Server hostet, bereitstellt. Verbindung testen.

>[!NOTE]
>
>Die **Option &quot;mid-sourcingEmitter** &quot;erstellt zwei **Mid-Sourcing** -Workflows. Dieser Vorgang wird standardmäßig alle 1 Stunde und 20 Minuten ausgeführt und erfasst Versand-Informationen auf dem Mid-Sourcing-Server.

## Bereitstellen eines Mid-Sourcing-Servers {#deploying-a-mid-sourcing-server}

1. Anwendungsserver installieren:

   >[!CAUTION]
   >
   >Wenn Sie den Mid-Sourcing-Server installieren und zusätzliche Adobe Campaign-Module installieren möchten, empfehlen wir die Verwendung des Versand-Moduls und nicht des Kampagne-Moduls.

   Gehen Sie wie bei der Standardbereitstellung vor und wählen Sie nur die Option &quot; **[!UICONTROL Mid-Sourcing-Plattform]** &quot;aus.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Konfiguration für den Empfang im Mid-Sourcing-Modus

   Legen Sie das Kennwort für das Übermittlungskonto fest: Im Ordner **/Mid-Sourcing/Zugriffsverwaltung/Operatoren/** wird der **mid** -Operator von der Remote-Instanz für Übermittlungen im Mid-Sourcing-Modus verwendet. Sie müssen ein Kennwort für diesen Operator festlegen und es an den Administrator der Sendeinstanz übergeben.

   Die Option &quot; **Mid-Sourcing-Plattform** &quot;erstellt die Standardordner zum Speichern der gesendeten Versand und den Standardoperator, der die Übermittlungen durchführt.

## Multiplexing des Mid-Sourcing-Servers {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Multiplexing wird nur für lokale Umgebung unterstützt.

Es ist möglich, dass eine Mid-Sourcing-Instanz von mehreren Sendeinstanzen gemeinsam verwendet wird. Jede dieser Instanzen muss mit einem Operator in der Mid-Sourcing-Datenbank verknüpft sein. So erstellen Sie ein zweites Konto auf dem Mid-Sourcing-Server:

1. Erstellen Sie im Knoten **[!UICONTROL Mid-Sourcing > Versand]** einen Ordner, der mit dem Standardkonto für Mid-Sourcing verknüpft wird (z. B.: prod).
1. Erstellen Sie im Knoten **[!UICONTROL Mid-Sourcing > Versand]** einen Ordner mit demselben Namen wie das Konto (z. B.: accept_test).

   ![](assets/mid_recette_account.png)

1. Erstellen Sie unter **[!UICONTROL Mid-Sourcing > Zugriffsverwaltung > Operatoren]** ein neues Konto.

   ![](assets/mid_recette_user_create.png)

1. Weisen Sie diesem Bediener auf der Registerkarte &quot; **[!UICONTROL Zugriffsrechte]** &quot;die Rechte der Gruppe für **Mid-Sourcing-Übermittlungen** zu. Diese Zugriffsrechte stehen unter **[!UICONTROL Mid-Sourcing > Zugriffsverwaltung > Operatorgruppen]** zur Verfügung.

   ![](assets/mid_recette_user_rights.png)

1. Wählen Sie die Option &quot;Auf Daten **[!UICONTROL beschränken&quot;in den Unterordnern der]** Option und wählen Sie den Ordner &quot;Versand&quot;aus, um diesen Operator auf den Ordner &quot;Mid-Sourcing Versands&quot;zu beschränken.

   ![](assets/mid_recette_user_restrictions.png)

1. Starten Sie das Webmodul mit dem folgenden Befehl neu: **nlserver startet Web**.

Sie müssen die Einstellung für den Mid-Sourcing-Server in der Datei &quot;serverConf.xml&quot;ändern. Im Abschnitt &quot;Verwaltung von Affinitäten mit IP-Adressen&quot; muss unter der vorhandenen Zeile folgende Zeile hinzugefügt werden:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

Das Attribut &quot;@name&quot;muss die folgenden Regeln beachten:

**&#39;marketing_account_operator_name&#39;.affinität_Name&#39;.&#39;affinität_Gruppe&#39;**

&quot;marketing_account_operator_name&quot;bezieht sich auf den internen Namen des in der Mid-Sourcing-Instanz deklarierten Mid-Sourcing-Kontos.

&#39;Affinität_name&#39; bezieht sich auf den willkürlichen Namen, der der Affinität gegeben wird. Dieser Name muss eindeutig sein. Autorisierte Zeichen sind `[a-z]``[A-Z]``[0-9]`zulässig. Ziel ist es, eine Gruppe öffentlicher IP-Adressen zu deklarieren.

&#39;Affinität_group&#39; bezieht sich auf die Untergruppe, die in dem in jedem Versand verwendeten Zielgruppen-Mapping deklariert wurde. Der letzte Teil einschließlich des &#39;.&#39; wird ignoriert, wenn keine Unter-Affinität vorhanden ist. Autorisierte Zeichen sind `[a-z]``[A-Z]``[0-9]`zulässig.

Sie müssen den Server beenden und dann neu starten, damit die Änderung berücksichtigt wird.

## Konfigurieren der Verfolgung auf einem Mid-Sourcing-Server {#configuring-tracking-on-a-mid-sourcing-server}

**Mid-Sourcing-Server konfigurieren**

1. Gehen Sie zu &quot;Operatoren&quot;und wählen Sie den Operator **[!UICONTROL mid]**.
1. Geben Sie auf der Registerkarte &quot; **[!UICONTROL Frontalserver]** &quot;die Verbindungsparameter des Tracking-Servers ein.

   Um eine Verfolgungsinstanz zu erstellen, geben Sie die URL des Trackingservers, das Kennwort des internen Trackingservers und den Namen der Instanz, ihr Kennwort und die damit verknüpften DNS-Masken ein.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. Klicken Sie nach Eingabe der Verbindungsparameter auf **[!UICONTROL Konfiguration]** bestätigen.
1. Geben Sie bei Bedarf den Speicherort an, an dem die in Versänden enthaltenen Bilder gespeichert werden sollen. Wählen Sie dazu einen der Veröffentlichungsmodi aus der Dropdown-Liste.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Wenn Sie die Option **[!UICONTROL Tracking-Server(s)]** wählen, werden die Bilder auf den Mid-Sourcing-Server kopiert.

**Kundenplattform konfigurieren**

1. Wechseln Sie zum Routing des externen Mid-Sourcings.
1. Geben Sie auf der Registerkarte &quot; **[!UICONTROL Mid-Sourcing]** &quot;die Verbindungsparameter für den Mid-Sourcing-Server an.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Bestätigen Sie Ihre Konfiguration, indem Sie auf Verbindung **[!UICONTROL testen]** klicken.
1. Deklarieren Sie die auf dem Mid-Sourcing-Server referenzierte Verfolgungsinstanz:

   Click the link **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Geben Sie den Namen der Verfolgungsinstanz an und bestätigen Sie dann die Verbindung mit dem Tracking-Server.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Wenn der Versand von Nachrichten von mehreren Mid-Sourcing-Servern verwaltet werden soll, wählen Sie die Option **[!UICONTROL Routing mit abwechselnden Mid-Sourcing-Konten]** und geben Sie die verschiedenen Server an.

![](assets/s_ncs_install_midsourcing_tracking04.png)

