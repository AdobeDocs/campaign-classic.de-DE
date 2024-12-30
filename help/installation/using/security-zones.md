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

# Definieren von Sicherheitszonen (On-Premise){#defining-security-zones}



Jeder Operator muss mit einer Zone verknüpft sein, um sich bei einer Instanz anmelden zu können, und die IP des Operators muss in die Adressen oder Adresssätze aufgenommen werden, die in der Sicherheitszone definiert sind. Die Konfiguration der Sicherheitszone erfolgt in der Konfigurationsdatei des Adobe Campaign-Servers.

Operatoren werden über ihr Profil in der Konsole mit einer Sicherheitszone verknüpft, auf die über den Knoten **[!UICONTROL Administration > Zugriffsverwaltung > Operatoren]** zugegriffen werden kann. [Weitere Informationen](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Dieses Verfahren ist auf On **Premise-Bereitstellungen**.
>
>Wenn Sie als **gehosteter** Kunde auf das [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) zugreifen können, können Sie die Self-Service-Oberfläche der Sicherheitszone verwenden. [Weitere Informationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=de)
>
>Andere **hybride/gehostete** Kunden müssen sich an das Support-Team von Adobe auf die Zulassungsliste setzen wenden, um IP-Adressen zur hinzuzufügen.
>

## Sicherheitszonen erstellen {#creating-security-zones}

Eine Zone wird definiert durch:

* ein oder mehrere IP-Adressbereiche (IPv4 und IPv6)
* Ein technischer Name, der mit jedem IP-Adressbereich verknüpft ist

Sicherheitszonen sind verkabelt, was bedeutet, dass die Definition einer neuen Zone innerhalb einer anderen Zone die Anzahl der Benutzer reduziert, die sich dort anmelden können, während die jedem Benutzer zugewiesenen Rechte erhöht werden.

Zonen müssen während der Server-Konfiguration in der Datei **serverConf.xml** definiert werden. Alle in der Datei **serverConf.xml** verfügbaren Parameter sind in [diesem Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Jede Zone definiert Rechte, z. B.:

* HTTP-Verbindung statt HTTPS
* Fehleranzeige (Java-Fehler, JavaScript, C++ usw.)
* Vorschau von Berichten und WebApps
* Authentifizierung über Login / Passwort
* Nicht sicherer Verbindungsmodus

>[!NOTE]
>
>**Jeder Operator muss mit einer Zone verknüpft sein**. Wenn die IP-Adresse des Benutzers zu dem von der Zone definierten Bereich gehört, kann sich der Benutzer bei der Instanz anmelden.\
>Die IP-Adresse des Betreibers kann in mehreren Zonen definiert werden. In diesem Fall erhält der Benutzer für jede Zone **Satz** der verfügbaren Rechte.

Die vorkonfigurierte Datei **serverConf.xml** umfasst drei Zonen: **public, VPN und LAN**.

>[!NOTE]
>
>**Die vordefinierte Konfiguration ist sicher**. Vor der Migration von einer früheren Version von Adobe Campaign kann es jedoch erforderlich sein, die Sicherheit vorübergehend zu reduzieren, um die neuen Regeln zu migrieren und zu genehmigen.

Beispiel für die Definition einer Zone in der Datei **serverConf.xml**:

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

Alle Rechte, die eine Zone definieren, lauten wie folgt:

* **allowDebug**: Ermöglicht die Ausführung einer WebApp im „Debug“-Modus
* **allowEmptyPassword**: Autorisiert eine Verbindung zu einer Instanz ohne Kennwort
* **allowHTTP**: Eine Sitzung kann ohne Verwendung des HTTPS-Protokolls erstellt werden
* **allowUserPassword**: Das Sitzungs-Token kann die folgende Form haben: &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: Das Security-Token ist in der Verbindungs-URL nicht erforderlich
* **showErrors**: Server-seitige Fehler werden weitergeleitet und angezeigt

>[!IMPORTANT]
>
>In einer Zonendefinition verringert jedes Attribut mit dem Wert **true** die Sicherheit.

Wenn Sie Message Center verwenden und mehrere Ausführungsinstanzen vorhanden sind, müssen Sie eine zusätzliche Sicherheitszone mit dem Attribut **sessionTokenOnly** erstellen, das als **true** definiert ist, wobei nur die erforderlichen IP-Adressen hinzugefügt werden sollen. Weiterführende Informationen zum Konfigurieren von Instanzen finden Sie [diesem Dokument](../../message-center/using/configuring-instances.md).

## Best Practices für Sicherheitszonen {#best-practices-for-security-zones}

Bei der Definition der **LAN**-Sicherheitszone ist es möglich, eine IP-Adressmaske hinzuzufügen, die den technischen Zugriff definiert. Durch diese Hinzufügung wird der Zugriff auf alle auf dem Server gehosteten Instanzen ermöglicht.

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

Es wird empfohlen, IP-Adressbereiche direkt in der Konfigurationsdatei der Instanz für Benutzer zu definieren, die nur auf eine bestimmte Instanz zugreifen.

In der **`config-<instance>.xml`**:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Subnetzwerke und Proxys in einer Sicherheitszone {#sub-networks-and-proxies-in-a-security-zone}

Der **proxy**-Parameter kann in einem **subNetwork**-Element verwendet werden, um die Verwendung von Proxys in einer Sicherheitszone anzugeben.

Wenn ein Proxy referenziert wird und eine Verbindung über diesen Proxy eintritt (sichtbar über den HTTP-Header „X-Forwarded-For„), ist die verifizierte Zone die der Clients des Proxys und nicht die des Proxys.

>[!IMPORTANT]
>
>Wenn ein Proxy konfiguriert ist und es möglich ist, ihn zu überschreiben (oder wenn er nicht vorhanden ist), kann die IP-Adresse, die getestet wird, gefälscht werden.
>
>Außerdem werden Relais nun wie Proxys erzeugt. Sie können daher die IP-127.0.0.1 zur Liste der Proxys in Ihrer Sicherheitszonenkonfiguration hinzufügen.
>
>Beispiel: &quot;`<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Es können verschiedene Fälle auftreten:

* Ein Subnetzwerk wird direkt in der Sicherheitszone referenziert und es ist kein Proxy konfiguriert: Benutzer des Subnetzwerks können direkt eine Verbindung mit dem Adobe Campaign-Server herstellen.

  ![](assets/8101_proxy1.png)

* In der Sicherheitszone ist ein Proxy für ein Subnetzwerk angegeben: Benutzer dieses Subnetzwerks können über diesen Proxy auf den Adobe Campaign-Server zugreifen.

  ![](assets/8101_proxy2.png)

* Ein Proxy ist in einem Sicherheitszonen-Unternetzwerk enthalten: Benutzer, die unabhängig von ihrer Herkunft über diesen Proxy Zugriff haben, können auf den Adobe Campaign-Server zugreifen.

  ![](assets/8101_proxy3.png)

Die IP-Adressen von Proxys, die wahrscheinlich auf den Adobe Campaign-Server zugreifen werden, müssen sowohl in der betreffenden **`<subnetwork>`** als auch in der Subnetzwerk-**`<subnetwork name="all"/>`** der ersten Ebene eingegeben werden. Hier finden Sie beispielsweise einen Proxy mit der IP-Adresse 10.131.146.102:

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

## Verknüpfen einer Sicherheitszone mit einem Benutzer {#linking-a-security-zone-to-an-operator}

Sobald Zonen definiert sind, muss jeder Benutzer mit einem von ihnen verknüpft sein, um sich bei einer Instanz anmelden zu können, und die IP-Adresse des Benutzers muss in die Adressen oder den Adressenbereich aufgenommen werden, auf die in der Zone verwiesen wird.

Die technische Konfiguration der Zonen erfolgt in der Konfigurationsdatei des Campaign-Servers: &quot;**.xml**.

Zuvor müssen Sie die vordefinierte Auflistung **[!UICONTROL Sicherheitszone]** konfigurieren, um eine Bezeichnung mit dem internen Namen der in der Datei **serverConf.xml** definierten Zone zu verknüpfen.

Diese Konfiguration erfolgt im Campaign-Explorer:

1. Klicken Sie auf **[!UICONTROL Knoten Administration > Plattform]** Auflistungen .
1. Wählen Sie die Auflistung **[!UICONTROL Sicherheitszone (securityZone]** aus.

   ![](assets/enum_securityzone.png)

1. Klicken Sie für jede Sicherheitszone, die in der Konfigurationsdatei des Servers definiert ist, auf die Schaltfläche **[!UICONTROL Hinzufügen]**.
1. Geben Sie im Feld **[!UICONTROL Interner Name]** den Namen der Zone ein, die in der Datei **serverConf.xml** definiert ist. Er entspricht dem Attribut {0@name **des `<securityzone>`.** Geben Sie den Titel, der mit dem internen Namen verknüpft ist, im Feld **label** ein.

   ![](assets/enum_addsecurityvalue.png)

1. Klicken Sie auf OK und speichern Sie die Änderungen.

Sobald die Zonen definiert und die Auflistung **[!UICONTROL Sicherheitszone]** konfiguriert ist, müssen Sie jeden Benutzer mit einer Sicherheitszone verknüpfen:

1. Klicken Sie auf **[!UICONTROL Knoten Administration > Zugriffsverwaltung > Benutzer]**.
1. Wählen Sie den Benutzer aus, mit dem Sie eine Sicherheitszone verknüpfen möchten, und klicken Sie auf die Registerkarte **[!UICONTROL Bearbeiten]**.
1. Wechseln Sie zur Registerkarte **[!UICONTROL Zugriffsberechtigungen]** und klicken Sie auf den Link **[!UICONTROL Zugriffsparameter bearbeiten…]** .

   ![](assets/zone_operator.png)

1. Wählen Sie eine Zone aus **[!UICONTROL Dropdown-Liste]** Zulässige Verbindungszone“ aus

   ![](assets/zone_operator_selection.png)

1. Klicken Sie **[!UICONTROL OK]** und speichern Sie die Änderungen, um diese Änderungen anzuwenden.



## Empfehlungen

* Stellen Sie sicher, dass der Reverse-Proxy im Sub-Netzwerk nicht zulässig ist. Wenn dies der Fall ist **wird** Traffic als von dieser lokalen IP kommend erkannt und wird daher als vertrauenswürdig eingestuft.

* Minimieren Sie die Verwendung von sessionTokenOnly=„true“:

   * Warnung: Wenn dieses Attribut auf „true“ gesetzt ist, kann der Benutzer einem „CRSF **Angriff ausgesetzt**.
   * Darüber hinaus wird das sessionToken-Cookie nicht mit einem „httpOnly“-Flag gesetzt, sodass es von Client-seitigem JavaScript-Code gelesen werden kann.
   * Bei Verwendung von Message Center mit mehreren Ausführungsinstanzen ist jedoch der Einsatz von sessionTokenOnly unumgänglich: Erstellen Sie eine neue Sicherheitszone, setzen Sie sessionTokenOnly auf &quot;true&quot;, und fügen Sie dieser Zone **nur die benötigten IP-Adressen** hinzu.

* Legen Sie nach Möglichkeit alle „allowHTTP“, „showErrors“ auf „false“ fest (nicht für „localhost„) und überprüfen Sie sie.

   * allowHTTP = &quot;false&quot;: zwingt Benutzer, HTTPS zu verwenden.
   * showErrors = &quot;false&quot;: verbirgt technische Fehler (einschließlich SQL-Fehler). Dies verhindert die Anzeige übermäßig vieler Informationen, schränkt aber auch die Fähigkeit des Benutzers ein, Probleme zu lösen (ohne vom Administrator zusätzliche Informationen einzuholen).

* Setzen Sie allowDebug nur für IPs, die von Marketing-Benutzern/Administratoren verwendet werden und Umfragen, WebApps und Berichte erstellen (in der Vorschau anzeigen), auf „true“. Mit diesem Flag können diese IPs Relay-Regeln anzeigen und debuggen.

   * Wenn allowDebug auf false festgelegt ist, wird Folgendes ausgegeben:

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * Wenn allowDebug auf true festgelegt ist, wird Folgendes ausgegeben:

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* Legen Sie nie allowEmptyPassword, allowUserPassword, allowSQLInjection auf „true“ fest.

   * **allowEmptyPassword** ermöglicht Benutzern, ein leeres Passwort zu haben. Ist dies bei Ihnen der Fall, weisen Sie alle Benutzer an, bis zu einer bestimmten Deadline ein Passwort zu erstellen. Sobald diese Frist abgelaufen ist, ändern Sie dieses Attribut auf &quot;false&quot;.

   * **allowUserPassword** ermöglicht es Benutzern, ihre Zugangsdaten als Parameter zu senden (sodass sie via Apache/IIS/Proxy gespeichert werden). Diese Funktion diente in der Vergangenheit zur Vereinfachung der API-Nutzung. In Ihrem Cookbook (oder in der Spezifikation) können Sie nachsehen, ob die Funktion von Drittanwendungen genutzt wird. Ist dies der Fall, weisen Sie den Administrator dieser Drittanwendungen an, die Verwendung unserer API zu ändern und die Funktion nicht mehr zu nutzen.

   * **allowSQLInjection** : Ermöglicht Benutzern das Durchführen von SQL-Injektionen mithilfe einer alten Syntax. Dieses Attribut sollte auf „false“ gesetzt werden. Mit /nl/jsp/ping.jsp?zones=true können Sie die Konfiguration Ihrer Sicherheitszone überprüfen. Auf dieser Seite wird der aktive Status von Sicherheitsmaßnahmen (mit diesen Sicherheits-Flags berechnet) für die aktuelle IP-Adresse angezeigt.

* HttpOnly cookie/useSecurityToken: siehe Flag **sessionTokenOnly**.

* Minimieren von IPs, die der Zulassungsliste hinzugefügt werden: Standardmäßig wurden in Sicherheitszonen die drei Bereiche für private Netzwerke hinzugefügt. Es ist unwahrscheinlich, dass Sie alle diese IP-Adressen verwenden werden. Behalte nur die, die du brauchst.

* Aktualisieren Sie den WebApp-/internen Benutzer, damit er nur über localhost zugänglich sind.
