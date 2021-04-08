---
solution: Campaign Classic
product: campaign
title: Sicherheitszonen konfigurieren
description: Erfahren Sie, wie Sie Sicherheitszonen konfigurieren
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: e31d386af4def80cdf258457fc74205b1ca823b3
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 27%

---


# Sicherheitszonen definieren (lokal){#defining-security-zones}

Jeder Operator muss mit einer Zone verknüpft sein, um sich bei einer Instanz anzumelden, und die IP-Adresse des Betreibers muss in die Adressen oder Adresssätze aufgenommen werden, die in der Sicherheitszone definiert sind. Die Sicherheitszonenkonfiguration wird in der Konfigurationsdatei des Adobe Campaign-Servers ausgeführt.

Operatoren sind über ihr Profil in der Konsole mit einer Sicherheitszone verknüpft. Zugriff auf diese Bereiche erhalten Sie unter **[!UICONTROL Administration > Zugriffsverwaltung > Operatoren]**. [Weitere Informationen](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Dieses Verfahren ist auf **lokale** Bereitstellungen beschränkt.
>
>Wenn Sie als Kunde **gehostet** auf [Kampagne Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) zugreifen können, können Sie die Selbstbedienungsoberfläche der Sicherheitszone verwenden. [Mehr dazu](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)
>
>Andere **hybride/gehostete**-Kunden müssen sich an das Supportteam der Adobe wenden, um der Zulassungsliste IP hinzuzufügen.


## Sicherheitszonen {#creating-security-zones} erstellen

Eine Zone ist definiert durch:

* einen oder mehrere IP-Adressbereiche (IPv4 und IPv6)
* einen technischen Namen, der jedem IP-Adressenbereich zugeordnet ist

Die Sicherheitszonen sind miteinander verbunden, was bedeutet, dass die Definition einer neuen Zone innerhalb einer anderen Zone die Anzahl der Operatoren verringert, die sich bei ihr anmelden können, während die den einzelnen Operatoren zugewiesenen Rechte erhöht werden.

Zonen müssen während der Serverkonfiguration in der Datei **serverConf.xml** definiert werden. Alle in **serverConf.xml** verfügbaren Parameter sind in [diesem Abschnitt](../../installation/using/the-server-configuration-file.md) aufgeführt.

Jede Zone definiert Rechte wie:

* HTTP-Verbindung anstelle von HTTPS
* Fehleranzeige (Java-Fehler, JavaScript, C++ usw.)
* Report und webApp-Vorschau
* Authentifizierung über Anmeldung/Kennwort
* Nicht sicherer Verbindungsmodus

>[!NOTE]
>
>**Jeder Operator muss mit einer Zone** verbunden sein. Wenn die IP-Adresse des Operators zu dem durch die Zone definierten Bereich gehört, kann sich der Operator bei der Instanz anmelden.\
>Die IP-Adresse des Betreibers kann in mehreren Zonen definiert werden. In diesem Fall erhält der Operator die verfügbaren Rechte für jede Zone.****

Die vordefinierte **serverConf.xml**-Datei umfasst drei Zonen: **public, VPN und LAN**.

>[!NOTE]
>
>**Die vordefinierte Konfiguration ist sicher**. Vor der Migration von einer früheren Version von Adobe Campaign kann es jedoch erforderlich sein, die Sicherheit vorübergehend zu reduzieren, um die neuen Regeln zu migrieren und zu genehmigen.

Beispiel zum Definieren einer Zone in der Datei **serverConf.xml**:

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

* **allowDebug**: aktiviert die Ausführung einer WebApp im Debug-Modus
* **allowEmptyPassword**: eine Verbindung zu einer Instanz ohne Kennwort autorisiert
* **allowHTTP**: eine Sitzung ohne Verwendung des HTTPS-Protokolls erstellt werden kann
* **allowUserPassword**: Das Sitzungstoken kann das folgende Formular &quot;`<login>/<password>`&quot; haben
* **sessionTokenOnly**: das Sicherheitstoken in der Verbindungs-URL nicht erforderlich ist
* **showErrors**: Fehler auf Serverseite werden weitergeleitet und angezeigt

>[!IMPORTANT]
>
>In einer Zonendefinition verringert jedes Attribut mit dem Wert **true** die Sicherheit.

Bei Verwendung des Message Center müssen Sie bei mehreren Ausführungsinstanzen eine zusätzliche Sicherheitszone mit dem Attribut **sessionTokenOnly** erstellen, das als **true** definiert ist, wobei nur die erforderlichen IP-Adressen hinzugefügt werden müssen. Weitere Informationen zum Konfigurieren von Instanzen finden Sie in [diesem Dokument](../../message-center/using/creating-a-shared-connection.md).

## Bewährte Verfahren für Sicherheitszonen {#best-practices-for-security-zones}

In der Definition der Sicherheitszone **lan** kann eine IP-Adressenmaske hinzugefügt werden, die den technischen Zugriff definiert. Dieser Zusatz ermöglicht den Zugriff auf alle Instanzen, die auf dem Server gehostet werden.

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

Es wird empfohlen, IP-Adressbereiche direkt in der Konfigurationsdatei zu definieren, die der Instanz zugeordnet ist, damit Operatoren nur auf eine bestimmte Instanz zugreifen können.

In der Datei **`config-<instance>.xml`**:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Subnetzwerke und Proxys in einer Sicherheitszone {#sub-networks-and-proxies-in-a-security-zone}

Der Parameter **proxy** kann in einem **subNetwork**-Element verwendet werden, um die Proxyverwendung in einer Sicherheitszone anzugeben.

Wenn ein Proxy referenziert wird und eine Verbindung über diesen Proxy eingeht (sichtbar über den HTTP X-Forwarded-For-Header), ist der verifizierte Bereich der Clients des Proxys und nicht der des Proxys.

>[!IMPORTANT]
>
>Wenn ein Proxy konfiguriert ist und es möglich ist, ihn zu überschreiben (oder nicht vorhanden), kann die IP-Adresse, die getestet wird, gefälscht werden.
>
>Außerdem werden jetzt Relais wie Stellvertreter generiert. Sie können daher die IP-Adresse 127.0.0.1 zur Liste der Proxys in Ihrer Sicherheitszonenkonfiguration hinzufügen.
>
>Beispiel: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Es können verschiedene Fälle auftreten:

* Ein Unternetzwerk wird direkt in der Sicherheitszone referenziert und es wird kein Proxy konfiguriert: Benutzer des Unternetzes können direkt eine Verbindung zum Adobe Campaign-Server herstellen.

   ![](assets/8101_proxy1.png)

* Ein Proxy wird für ein Unternetzwerk in der Sicherheitszone angegeben: Benutzer dieses Unternetzes können über diesen Proxy auf den Adobe Campaign-Server zugreifen.

   ![](assets/8101_proxy2.png)

* Ein Proxy ist in einem Teilnetzwerk einer Sicherheitszone enthalten: Benutzer, die über diesen Proxy Zugriff haben, können unabhängig von ihrer Herkunft auf den Adobe Campaign-Server zugreifen.

   ![](assets/8101_proxy3.png)

Die IP-Adressen von Proxys, die wahrscheinlich auf den Adobe Campaign-Server zugreifen, müssen sowohl im betreffenden **`<subnetwork>`** als auch im ersten Teilnetzwerk **`<subnetwork name="all"/>`** eingegeben werden. Beispiel: Hier für einen Proxy mit der IP-Adresse 10.131.146.102:

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

## Verknüpfen einer Sicherheitszone mit einem Operator {#linking-a-security-zone-to-an-operator}

Sobald Zonen definiert sind, muss jeder Operator mit einem von ihnen verknüpft sein, um sich bei einer Instanz anmelden zu können, und die IP-Adresse des Betreibers muss in die Adressen oder Adressbereiche, auf die in der Zone verwiesen wird, aufgenommen werden.

Die technische Konfiguration der Zonen erfolgt in der Konfigurationsdatei des Kampagne Server: **serverConf.xml**.

Zuvor müssen Sie die vordefinierte Auflistung **[!UICONTROL Sicherheitszone]** konfigurieren, um eine Bezeichnung mit dem in der Datei **serverConf.xml** definierten internen Namen der Beginn zu verknüpfen.

Diese Konfiguration erfolgt im Kampagne Explorer:

1. Klicken Sie auf den Knoten **[!UICONTROL Administration > Platform > Auflistungen]**.
1. Wählen Sie die Auflistung **[!UICONTROL Sicherheitszone (securityZone)]** aus.

   ![](assets/enum_securityzone.png)

1. Klicken Sie für jede in der Konfigurationsdatei des Servers definierte Sicherheitszone auf die Schaltfläche **[!UICONTROL Hinzufügen]**.
1. Geben Sie im Feld **[!UICONTROL Interner Name]** den Namen der in der Datei **serverConf.xml** definierten Zone ein. Es entspricht dem Attribut **@name** des Elements `<securityzone>`. Geben Sie im Feld **Beschriftung** die mit dem internen Namen verknüpfte Beschriftung ein.

   ![](assets/enum_addsecurityvalue.png)

1. Klicken Sie auf OK und speichern Sie die Änderungen.

Sobald die Zonen definiert und die Auflistung **[!UICONTROL Sicherheitszone]** konfiguriert ist, müssen Sie jeden Operator mit einer Sicherheitszone verknüpfen:

1. Klicken Sie auf den Knoten **[!UICONTROL Administration > Zugriffsverwaltung > Operatoren]**.
1. Wählen Sie den Operator aus, mit dem Sie eine Sicherheitszone verknüpfen möchten, und klicken Sie auf die Registerkarte **[!UICONTROL Bearbeiten]**.
1. Wechseln Sie zur Registerkarte **[!UICONTROL Zugriffsrechte]** und klicken Sie auf **[!UICONTROL Zugriffsparameter bearbeiten...]**-Link.

   ![](assets/zone_operator.png)

1. Wählen Sie einen Bereich aus der Dropdown-Liste **[!UICONTROL Autorisierte Verbindungszone]**

   ![](assets/zone_operator_selection.png)

1. Klicken Sie auf **[!UICONTROL OK]** und speichern Sie die Änderungen, um diese Änderungen anzuwenden.



## Empfehlungen    

* Stellen Sie sicher, dass Ihr Reverse-Proxy in subNetwork nicht erlaubt ist. Ist dies der Fall, wird der **gesamte** Datenverkehr als von dieser lokalen IP-Adresse kommend und daher als vertrauenswürdig eingestuft.

* Minimieren Sie den Einsatz von sessionTokenOnly=&quot;true&quot;:

   * Achtung: Wenn dieses Attribut auf true gesetzt wird, ist der Benutzer durch **CRSF-Attacken** (Cross-Site Request Forgery) angreifbar.
   * Zusätzlich ist das sessionToken-Cookie nicht mit einem httpOnly-Flag versehen, weshalb es von einem Client-seitigen Javascript-Code gelesen werden kann.
   * Bei Verwendung von Message Center mit mehreren Ausführungsinstanzen ist jedoch der Einsatz von sessionTokenOnly unumgänglich: Erstellen Sie eine neue Sicherheitszone, setzen Sie sessionTokenOnly auf &quot;true&quot;, und fügen Sie dieser Zone **nur die benötigten IP-Adressen** hinzu.

* Setzen Sie möglichst alle allowHTTP, showErrors auf &quot;false&quot; (nicht für localhost), und prüfen Sie sie.

   * allowHTTP = &quot;false&quot;: zwingt Benutzer, HTTPS zu verwenden.
   * showErrors = &quot;false&quot;: verbirgt technische Fehler (einschließlich SQL-Fehler). Dies verhindert die Anzeige übermäßig vieler Informationen, schränkt aber auch die Fähigkeit des Benutzers ein, Probleme zu lösen (ohne vom Administrator zusätzliche Informationen einzuholen).

* Setzen Sie allowDebug nur für IP-Adressen auf true, die von Benutzern/Administratoren verwendet werden, die Fragebögen, WebApps und Berichte erstellen müssen (diese aber nicht in der Vorschau ansehen können). Durch dieses Flag werden in diesen IP-Adressen Relais-Regeln dargestellt, was eine Fehlerbehebung ermöglicht.

* Setzen Sie niemals allowEmptyPassword, allowUserPassword, allowSQLInjection auf true. Diese Attribute dienen nur der problemlosen Migration von v5 und v6.0:

   * **allowEmptyPassword** ermöglicht Benutzern, ein leeres Passwort zu haben. Ist dies bei Ihnen der Fall, weisen Sie alle Benutzer an, bis zu einer bestimmten Deadline ein Passwort zu erstellen. Sobald diese Frist abgelaufen ist, ändern Sie dieses Attribut auf &quot;false&quot;.

   * **allowUserPassword** ermöglicht es Benutzern, ihre Zugangsdaten als Parameter zu senden (sodass sie via Apache/IIS/Proxy gespeichert werden). Diese Funktion diente in der Vergangenheit zur Vereinfachung der API-Nutzung. In Ihrem Cookbook (oder in der Spezifikation) können Sie nachsehen, ob die Funktion von Drittanwendungen genutzt wird. Ist dies der Fall, weisen Sie den Administrator dieser Drittanwendungen an, die Verwendung unserer API zu ändern und die Funktion nicht mehr zu nutzen.

   * **** allowSQLInjectionermöglicht dem Benutzer die Durchführung von SQL-Injektionen mit einer alten Syntax. Führen Sie so bald wie möglich die unter [Diese Seite](../../migration/using/general-configurations.md) beschriebenen Korrekturen durch, um dieses Attribut auf &quot;false&quot;setzen zu können. Mit /nl/jsp/ping.jsp?zones=true können Sie die Konfiguration Ihrer Sicherheitszone überprüfen. Auf dieser Seite wird der aktive Status von Sicherheitsmaßnahmen (mit diesen Sicherheits-Flags berechnet) für die aktuelle IP-Adresse angezeigt.

* HttpOnly cookie/useSecurityToken: siehe Flag **sessionTokenOnly**.

* Minimieren Sie die Anzahl der IP-Adressen auf der Zulassungsliste: Standardmäßig wurden für Sicherheitszonen die drei Bereiche für private Netzwerke hinzugefügt. Es ist unwahrscheinlich, dass Sie alle diese IP-Adressen verwenden werden. Behalten Sie also nur die, die Sie brauchen.

* Aktualisieren Sie den WebApp-/internen Benutzer, damit er nur über localhost zugänglich sind.
