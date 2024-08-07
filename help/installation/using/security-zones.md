---
product: campaign
title: Sicherheitszonen konfigurieren
description: Erfahren Sie, wie Sie Sicherheitszonen konfigurieren
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 19%

---

# Sicherheitszonen definieren (On-Premise){#defining-security-zones}



Jeder Operator muss mit einer Zone verknüpft sein, um sich bei einer Instanz anmelden zu können, und die IP des Operators muss in die Adressen oder Adresssätze aufgenommen werden, die in der Sicherheitszone definiert sind. Die Konfiguration der Sicherheitszone erfolgt in der Konfigurationsdatei des Adobe Campaign-Servers.

Benutzer werden über ihr Profil in der Konsole mit einer Sicherheitszone verknüpft, auf die über den Knoten **[!UICONTROL Administration > Zugriffe > Benutzer]** zugegriffen werden kann. [Weitere Informationen](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Dieses Verfahren ist auf **On-Premise** -Implementierungen beschränkt.
>
>Als **gehosteter** Kunde können Sie, wenn Sie auf das [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) zugreifen können, die Sicherheitszonen-Benutzeroberfläche verwenden. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=de)
>
>Andere **hybride/gehostete** -Kunden müssen sich an das Adobe-Supportteam wenden, um IP zur Zulassungsliste hinzuzufügen.
>

## Sicherheitszonen erstellen {#creating-security-zones}

Eine Zone wird wie folgt definiert:

* einen oder mehrere IP-Adressbereiche (IPv4 und IPv6)
* einen technischen Namen für jeden IP-Adressbereich

Sicherheitszonen sind miteinander verbunden. Das bedeutet, dass die Definition einer neuen Zone innerhalb einer anderen Zone die Anzahl der Benutzer verringert, die sich bei ihr anmelden können, während die den einzelnen Benutzern zugewiesenen Rechte erhöht werden.

Bereiche müssen während der Serverkonfiguration in der Datei **serverConf.xml** definiert werden. Alle in **serverConf.xml** verfügbaren Parameter sind in [diesem Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

In jedem Bereich werden Berechtigungen definiert, wie beispielsweise:

* HTTP-Verbindung anstelle von HTTPS
* Fehleranzeige (Java-Fehler, JavaScript, C++ usw.)
* Vorschau für Bericht und WebApp
* Authentifizierung über Anmeldung/Kennwort
* Nicht sicherer Verbindungsmodus

>[!NOTE]
>
>**Jeder Operator muss mit einer Zone** verknüpft sein. Wenn die IP-Adresse des Benutzers zu dem durch die Zone definierten Bereich gehört, kann sich der Benutzer bei der Instanz anmelden.\
>Die IP-Adresse des Benutzers kann in mehreren Bereichen definiert werden. In diesem Fall erhält der Benutzer die für jede Zone verfügbaren Rechte **set** .

Die standardmäßige Datei **serverConf.xml** enthält drei Bereiche: **public, VPN und LAN**.

>[!NOTE]
>
>**Die vordefinierte Konfiguration ist sicher**. Vor der Migration von einer früheren Version von Adobe Campaign kann es jedoch erforderlich sein, die Sicherheit vorübergehend zu verringern, um die neuen Regeln zu migrieren und zu genehmigen.

Beispiel für das Definieren eines Bereichs in der Datei **serverConf.xml**:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

Die Berechtigungen, die eine Zone definieren, lauten wie folgt:

* **allowDebug**: ermöglicht die Ausführung einer WebApp im Debug-Modus
* **allowEmptyPassword**: autorisiert eine Verbindung zu einer Instanz ohne Kennwort
* **allowHTTP**: Eine Sitzung kann ohne HTTPS-Protokoll erstellt werden
* **allowUserPassword**: Das Sitzungstoken kann das folgende Formular &quot;`<login>/<password>`&quot; aufweisen
* **sessionTokenOnly**: Das Sicherheitstoken ist in der Verbindungs-URL nicht erforderlich
* **showErrors**: Fehler auf der Serverseite werden weitergeleitet und angezeigt

>[!IMPORTANT]
>
>In einer Zonendefinition verringert jedes Attribut mit dem Wert **true** die Sicherheit.

Bei Verwendung von Message Center müssen Sie bei mehreren Ausführungsinstanzen eine zusätzliche Sicherheitszone mit dem Attribut **sessionTokenOnly** erstellen, das als **true** definiert ist, wobei nur die erforderlichen IP-Adressen hinzugefügt werden sollen. Weitere Informationen zum Konfigurieren von Instanzen finden Sie in [diesem Dokument](../../message-center/using/configuring-instances.md).

## Best Practices für Sicherheitszonen {#best-practices-for-security-zones}

In der Definition der Sicherheitszone **lan** kann eine IP-Adressenmaske hinzugefügt werden, die den technischen Zugriff definiert. Durch diesen Zusatz wird der Zugriff auf alle Instanzen ermöglicht, die auf dem Server gehostet werden.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

Es wird empfohlen, IP-Adressbereiche direkt in der Konfigurationsdatei für die Instanz zu definieren, damit Benutzer, die nur auf eine bestimmte Instanz zugreifen, darauf zugreifen können.

In der Datei **`config-<instance>.xml`** :

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Subnetze und Proxys in einer Sicherheitszone {#sub-networks-and-proxies-in-a-security-zone}

Der Parameter **proxy** kann in einem Element **subNetwork** verwendet werden, um die Proxy-Verwendung in einer Sicherheitszone anzugeben.

Wenn ein Proxy referenziert wird und eine Verbindung über diesen Proxy erfolgt (sichtbar über den HTTP-Header X-Forwarded-For ), ist der verifizierte Bereich der Clients des Proxys und nicht der des Proxys.

>[!IMPORTANT]
>
>Wenn ein Proxy konfiguriert ist und es möglich ist, ihn zu überschreiben (oder wenn er nicht vorhanden ist), kann die zu testende IP-Adresse gefälscht werden.
>
>Außerdem werden Relais jetzt wie Proxys generiert. Sie können daher die IP-Adresse 127.0.0.1 zur Liste der Proxys in Ihrer Sicherheitszonenkonfiguration hinzufügen.
>
>Beispiel: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Verschiedene Fälle können auftreten:

* Ein Unternetzwerk wird direkt in der Sicherheitszone referenziert und es wird kein Proxy konfiguriert: Benutzer des Unternetzes können direkt eine Verbindung zum Adobe Campaign-Server herstellen.

  ![](assets/8101_proxy1.png)

* Ein Proxy wird für ein Unternetzwerk in der Sicherheitszone angegeben: Benutzer dieses Unternetzwerks können über diesen Proxy auf den Adobe Campaign-Server zugreifen.

  ![](assets/8101_proxy2.png)

* Ein Proxy ist in einem Sicherheitszonen-Unternetzwerk enthalten: Benutzer, die über diesen Proxy Zugriff haben, können unabhängig von ihrer Herkunft auf den Adobe Campaign-Server zugreifen.

  ![](assets/8101_proxy3.png)

Die IP-Adressen der Proxys, die wahrscheinlich auf den Adobe Campaign-Server zugreifen, müssen sowohl im betreffenden **`<subnetwork>`** als auch im Subnetzwerk der ersten Ebene **`<subnetwork name="all"/>`** eingegeben werden. Hier für einen Proxy, dessen IP-Adresse beispielsweise 10.131.146.102 lautet:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## Sicherheitszone mit einem Benutzer verknüpfen {#linking-a-security-zone-to-an-operator}

Sobald Zonen definiert sind, muss jeder Benutzer mit einem dieser Benutzer verknüpft sein, um sich bei einer Instanz anmelden zu können, und die IP-Adresse des Benutzers muss in die Adressen oder Adressbereiche der Zone aufgenommen werden.

Die technische Konfiguration der Zonen erfolgt in der Konfigurationsdatei des Campaign-Servers: **serverConf.xml**.

Zuvor müssen Sie die vordefinierte Auflistung **[!UICONTROL Sicherheitszone]** so konfigurieren, dass eine Bezeichnung mit dem internen Namen der Zone verknüpft wird, der in der Datei **serverConf.xml** definiert ist.

Diese Konfiguration erfolgt im Campaign-Explorer:

1. Klicken Sie auf den Knoten **[!UICONTROL Administration > Plattform > Auflistungen]** .
1. Wählen Sie die Systemauflistung **[!UICONTROL Sicherheitszone (securityZone)]** aus.

   ![](assets/enum_securityzone.png)

1. Klicken Sie für jede in der Konfigurationsdatei des Servers definierte Sicherheitszone auf die Schaltfläche **[!UICONTROL Hinzufügen]** .
1. Geben Sie im Feld **[!UICONTROL Interner Name]** den Namen des Bereichs ein, der in der Datei **serverConf.xml** definiert ist. Sie entspricht dem Attribut **@name** des Elements `<securityzone>` . Geben Sie den mit dem internen Namen verknüpften Titel in das Feld **Titel** ein.

   ![](assets/enum_addsecurityvalue.png)

1. Klicken Sie auf OK und speichern Sie die Änderungen.

Nachdem die Zonen definiert und die Auflistung **[!UICONTROL Sicherheitszone]** konfiguriert wurde, müssen Sie jeden Benutzer einer Sicherheitszone zuordnen:

1. Klicken Sie auf den Knoten **[!UICONTROL Administration > Zugriffe > Benutzer]** .
1. Wählen Sie den Benutzer aus, mit dem Sie eine Sicherheitszone verknüpfen möchten, und klicken Sie auf die Registerkarte **[!UICONTROL Bearbeiten]** .
1. Klicken Sie auf der Registerkarte **[!UICONTROL Zugriffsberechtigungen]** auf den Link **[!UICONTROL Zugriffsparameter bearbeiten...]** .

   ![](assets/zone_operator.png)

1. Wählen Sie aus der Dropdownliste **[!UICONTROL Autorisierte Verbindungszone]** eine Zone aus

   ![](assets/zone_operator_selection.png)

1. Klicken Sie auf **[!UICONTROL OK]** und speichern Sie die Änderungen, um diese Änderungen anzuwenden.



## Empfehlungen

* Stellen Sie sicher, dass Ihr Reverse-Proxy in subNetwork nicht zulässig ist. Ist dies der Fall, wird der Traffic von **all** als von dieser lokalen IP stammt und daher als vertrauenswürdig eingestuft.

* Minimieren Sie die Verwendung von sessionTokenOnly=&quot;true&quot;:

   * Warnung: Wenn dieses Attribut auf &quot;true&quot;gesetzt ist, kann der Operator einem **CRSF-Angriff** ausgesetzt werden.
   * Darüber hinaus wird das sessionToken -Cookie nicht mit einem httpOnly -Flag gesetzt, sodass es von clientseitigem JavaScript-Code gelesen werden kann.
   * Bei Verwendung von Message Center mit mehreren Ausführungsinstanzen ist jedoch der Einsatz von sessionTokenOnly unumgänglich: Erstellen Sie eine neue Sicherheitszone, setzen Sie sessionTokenOnly auf &quot;true&quot;, und fügen Sie dieser Zone **nur die benötigten IP-Adressen** hinzu.

* Wenn möglich, setzen Sie alle allowHTTP-, showErrors auf false (nicht für localhost) und überprüfen Sie sie.

   * allowHTTP = &quot;false&quot;: zwingt Benutzer, HTTPS zu verwenden.
   * showErrors = &quot;false&quot;: verbirgt technische Fehler (einschließlich SQL-Fehler). Dies verhindert die Anzeige übermäßig vieler Informationen, schränkt aber auch die Fähigkeit des Benutzers ein, Probleme zu lösen (ohne vom Administrator zusätzliche Informationen einzuholen).

* Setzen Sie allowDebug nur für IPs auf &quot;true&quot;, die von Marketing-Benutzern/Administratoren verwendet werden, die Umfragen, WebApps und Berichte erstellen müssen (in der Vorschau). Diese Markierung ermöglicht es diesen IPs, Relais-Regeln anzuzeigen und zu debuggen.

   * Wenn allowDebug auf false gesetzt ist, lautet die Ausgabe:

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * Wenn allowDebug auf &quot;true&quot;gesetzt ist, lautet die Ausgabe:

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* Setzen Sie niemals allowEmptyPassword, allowUserPassword, allowSQLInjection auf true.

   * **allowEmptyPassword** ermöglicht Benutzern, ein leeres Passwort zu haben. Ist dies bei Ihnen der Fall, weisen Sie alle Benutzer an, bis zu einer bestimmten Deadline ein Passwort zu erstellen. Sobald diese Frist abgelaufen ist, ändern Sie dieses Attribut auf &quot;false&quot;.

   * **allowUserPassword** ermöglicht es Benutzern, ihre Zugangsdaten als Parameter zu senden (sodass sie via Apache/IIS/Proxy gespeichert werden). Diese Funktion diente in der Vergangenheit zur Vereinfachung der API-Nutzung. In Ihrem Cookbook (oder in der Spezifikation) können Sie nachsehen, ob die Funktion von Drittanwendungen genutzt wird. Ist dies der Fall, weisen Sie den Administrator dieser Drittanwendungen an, die Verwendung unserer API zu ändern und die Funktion nicht mehr zu nutzen.

   * Mit **allowSQLInjection** können Benutzer SQL-Injections mithilfe einer alten Syntax durchführen. Dieses Attribut sollte auf &quot;false&quot;gesetzt werden. Mit /nl/jsp/ping.jsp?zones=true können Sie die Konfiguration Ihrer Sicherheitszone überprüfen. Auf dieser Seite wird der aktive Status von Sicherheitsmaßnahmen (mit diesen Sicherheits-Flags berechnet) für die aktuelle IP-Adresse angezeigt.

* HttpOnly cookie/useSecurityToken: siehe Flag **sessionTokenOnly**.

* Minimieren Sie IPs, die zur Zulassungsliste hinzugefügt wurden: Standardmäßig wurden in Sicherheitszonen die 3 Bereiche für private Netzwerke hinzugefügt. Es ist unwahrscheinlich, dass Sie alle diese IP-Adressen verwenden werden. Behalten Sie also nur die, die Sie brauchen.

* Aktualisieren Sie den WebApp-/internen Benutzer, damit er nur über localhost zugänglich sind.
