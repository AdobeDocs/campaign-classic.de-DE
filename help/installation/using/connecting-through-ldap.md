---
title: Über LDAP verbinden
description: 'Erfahren Sie, wie Sie sich mit LDAP bei der Kampagne anmelden. '
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 1%

---


# Über LDAP verbinden{#connecting-through-ldap}

## Kampagne und LDAP konfigurieren {#configuring-campaign-and-ldap}

>[!NOTE]
>
>Die LDAP-Konfiguration ist nur für lokale oder hybride Installationen möglich.

Die LDAP-Konfiguration wird im Bereitstellungsassistenten ausgeführt. Die **[!UICONTROL Option für die LDAP-Integration]** muss während des ersten Konfigurationsschritts ausgewählt werden. Weitere Informationen finden Sie im [Bereitstellungsassistenten](../../installation/using/deploying-an-instance.md#deployment-wizard).

Im Fenster können Sie die Identifizierung von Adobe Campaign-Benutzern über den angegebenen LDAP-Ordner konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geben Sie die Adresse des LDAP-Servers im Feld **[!UICONTROL LDAP-Server]** an. Sie können die Anschlussnummer hinzufügen. Standardmäßig wird der Anschluss 389 verwendet.
* Wählen Sie in der Dropdown-Liste die Authentifizierungsmethode für Benutzer aus:

   * Verschlüsseltes Kennwort (**md5**)

      Standardmodus.

   * Normales Textkennwort + SSL (**TLS**)

      Das gesamte Authentifizierungsverfahren (Kennwort eingeschlossen) wird verschlüsselt. Der sichere Port 636 darf in diesem Modus nicht verwendet werden: Adobe Campaign wechselt automatisch in den abgesicherten Modus.

      Wenn Sie diesen Authentifizierungsmodus verwenden, wird das Zertifikat unter Linux von einer openLDAP-Client-Bibliothek überprüft. Es wird empfohlen, ein gültiges SSL-Zertifikat zu verwenden, damit das Authentifizierungsverfahren verschlüsselt wird. Andernfalls werden die Informationen im Klartext angegeben.

      Das Zertifikat wird auch unter Windows überprüft.

   * Windows NT LAN Manager (**NTLM**)

      Proprietäre Windows-Authentifizierung. Die **[!UICONTROL eindeutige Kennung]** wird nur für den Domänennamen verwendet.

   * Distributed Password Authentication (**DPA**)

      Proprietäre Windows-Authentifizierung. Die **[!UICONTROL eindeutige Kennung]** wird nur für den Domänennamen (domain.com) verwendet.

   * Passwort für Text

      Keine Verschlüsselung (nur zur Verwendung in Testphasen).

* Wählen Sie den Benutzerauthentifizierungsmodus aus: **[!UICONTROL Berechnen Sie automatisch die Unique User Identifier]** (siehe Schritt [Distinguished Name-Berechnung](#distinguished-name-calculation)) oder **[!UICONTROL Suchen Sie die eindeutige Benutzer-ID im Ordner]** (siehe Schritt [Suche nach Identifikatoren](#searching-for-identifiers)).

## Kompatibilität {#compatibility}

Die kompatiblen Systeme hängen vom ausgewählten Authentifizierungsmechanismus ab. Im Folgenden finden Sie eine Kompatibilitätsmatrix von Betriebssystemen und LDAP-Servern.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM und DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> plain text<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Berechnung des getrennten Namens {#distinguished-name-calculation}

Wenn Sie die DN-ID (Distinguished Name) berechnen möchten, können Sie im nächsten Schritt des Bereitstellungsassistenten den Berechnungsmodus konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Geben Sie die eindeutige Kennung des Benutzers im Verzeichnis (Distinguished Name - DN) im Feld **[!UICONTROL Distinguished Name]** an.

   **[!UICONTROL (login)]** wird durch den Bezeichner des Adobe Campaign-Operators ersetzt.

   >[!CAUTION]
   >
   >Die Einstellung **[!UICONTROL dc]** muss in Kleinbuchstaben angegeben werden.

* Wählen Sie die Option **[!UICONTROL Synchronisierung von Benutzerrechten aus Autorisierungen und Gruppen im Ordner]** aktivieren, um die Gruppen- und Benutzerzuordnungen im LDAP-Ordner sowie die Gruppen- und Benutzerzuordnungen in Adobe Campaign zu synchronisieren.

   Wenn Sie diese Option auswählen, ist der **[!UICONTROL AnwendungsebenenDN, der für die Suche]** und das **[!UICONTROL Kennwort der Anwendungsanmeldung]** verwendet wird, aktiviert.

   Wenn Sie diese beiden Felder ausfüllen, stellt Adobe Campaign eine Verbindung zum LDAP-Server mit seinem eigenen Login und Kennwort her. Wenn sie leer sind, stellt Adobe Campaign eine anonyme Verbindung zum Server her.

## Suchen nach Identifikatoren {#searching-for-identifiers}

Wenn Sie nach einem Bezeichner suchen möchten, können Sie die Suche im Bereitstellungsassistenten konfigurieren.

* Geben Sie im **[!UICONTROL AnwendungsebenenDN, der für die Suche]** und das **[!UICONTROL Kennwort der Anwendungsanmeldung]** verwendet wird, den Bezeichner und das Kennwort ein, mit dem das Adobe Campaign eine Verbindung zur Suche nach dem Bezeichner herstellen soll. Wenn sie leer sind, stellt Adobe Campaign eine anonyme Verbindung zum Server her.
* Geben Sie die Felder **[!UICONTROL Basis-ID]** und **[!UICONTROL Suchbereich]** an, um eine Untergruppe des LDAP-Ordners zu bestimmen, aus dem die Suche Beginn werden soll.

   Wählen Sie den erforderlichen Modus in der Dropdown-Liste aus:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Rekursiv (Standardmodus)]**.

      Der LDAP-Ordner wird ab einer bestimmten Ebene vollständig durchsucht.

   1. **[!UICONTROL Beschränkt auf die Basis]**.

      Alle Attribute werden in die Suche einbezogen.

   1. **[!UICONTROL Beschränkt auf die erste Unterebene der Basis]**.

      Die Suche wird mit allen Attributen des Ordners und beginnend mit der ersten Ebene des Attributs durchgeführt.

* Im Feld **[!UICONTROL Filter]** können Sie ein Element angeben, um den Suchbereich zu verfeinern.

## LDAP-Autorisierungen konfigurieren {#configuring-ldap-authorizations}

Dieses Fenster wird angezeigt, wenn Sie die Option &quot;Synchronisierung von Benutzerrechten aus Autorisierungen und Gruppen **[!UICONTROL aktivieren&quot;in der Ordneroption]** auswählen.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Sie müssen mehrere Parameter angeben, um die Gruppe(n) zu finden, zu der/denen der Benutzer gehört, und die entsprechenden Rechte, d.h.:

* das Feld **[!UICONTROL Datenbankkennung]** ,
* das Feld **[!UICONTROL Suchbereich]** ,

   >[!NOTE]
   >
   >Wenn Sie sich für die Suche nach dem DN entschieden haben, können Sie die Suchparameter **[!UICONTROL des DN]** wiederverwenden auswählen, um die ausgewählten Werte für den DN und den Suchbereich aus dem vorherigen Bildschirm zu übernehmen.

* das Feld **[!UICONTROL Rights search filter]** , basierend auf der Anmeldung und dem eindeutigen Namen des Benutzers,
* das **[!UICONTROL Attribut, das das Feld für den Gruppen- oder Autorisierungsnamen]** für den Benutzer enthält,
* das Feld **[!UICONTROL Vereinsmaske]** , das die Extraktion des Gruppennamen in Adobe Campaign und der zugehörigen Rechte ermöglicht. Sie können reguläre Ausdruck verwenden, um nach dem Namen zu suchen.
* Wählen Sie im LDAP-Ordner deklarierte Benutzerverbindung **[!UICONTROL aktivieren, wenn der Operator nicht in Adobe Campaign]** deklariert ist, sodass dem Benutzer automatisch Zugriffsrechte für die Verbindung zugewiesen werden.

Klicken Sie auf **[!UICONTROL Speichern]** , um die Konfiguration der Instanz abzuschließen.

## Verwalten von Operatoren {#managing-operators}

Nachdem Sie die Konfiguration bestätigt haben, müssen Sie festlegen, welche Adobe Campaign-Operatoren über den LDAP-Ordner verwaltet werden.

Um einen Operator mithilfe des LDAP-Ordners zu authentifizieren, bearbeiten Sie das entsprechende Profil und klicken Sie auf den Link **[!UICONTROL Zugriffsparameter]** bearbeiten. Wählen Sie die Option LDAP zur Authentifizierung **[!UICONTROL verwenden]** : Das Feld **[!UICONTROL Kennwort]** ist für diesen Operator grau ausgegraut.

![](assets/s_ncs_install_operator_in_ldap.png)

## Anwendungsbeispiele {#use-cases}

In diesem Abschnitt finden Sie einige einfache Anwendungsfälle, mit denen Sie die am besten geeigneten Konfigurationen je nach Ihren Anforderungen erzielen können.

1. Ein Benutzer wurde im LDAP-Ordner erstellt, jedoch nicht im Adobe Campaign.

   Adobe Campaign kann so konfiguriert werden, dass der Benutzer über seine LDAP-Authentifizierung auf die Plattform zugreift. Adobe Campaign muss in der Lage sein, die Gültigkeit der ID/Kennwort-Kombination im LDAP-Ordner zu kontrollieren, damit der Operator im Adobe Campaign direkt erstellt werden kann. Markieren Sie dazu die Option Benutzerverbindung **[!UICONTROL aktivieren, die im LDAP-Ordner deklariert wurde, wenn der Operator nicht in Adobe Campaign]** deklariert wurde. In diesem Fall muss auch die Gruppensynchronisierung konfiguriert werden: Die Option &quot;Synchronisierung von Benutzerrechten aus Autorisierungen und Gruppen im Verzeichnis **** aktivieren&quot;muss aktiviert werden.

1. Der Benutzer wurde in Adobe Campaign, nicht jedoch im LDAP-Ordner erstellt.

   Sie werden sich nicht bei Adobe Campaign anmelden können.

1. Es gibt eine Gruppe im LDAP-Ordner, die nicht in Adobe Campaign vorhanden ist.

   Diese Gruppe wird nicht in Adobe Campaign erstellt. Sie müssen die Gruppe erstellen und die Gruppen synchronisieren, um eine Übereinstimmung über die Option &quot;Synchronisierung der Benutzerrechte aus Autorisierungen und Gruppen im Ordner **** aktivieren&quot;zu aktivieren.

1. In Adobe Campaign existieren Gruppen, und der LDAP-Ordner wird nach dem Ereignis aktiviert: Benutzergruppen in Adobe Campaign werden nicht automatisch durch den Inhalt von LDAP-Gruppen ersetzt. Wenn eine Gruppe nur in Adobe Campaign vorhanden ist, können ihr keine LDAP-Benutzer hinzugefügt werden, bis die Gruppe in LDAP erstellt und synchronisiert wurde.

   Gruppen werden nie spontan erstellt, egal ob per Adobe Campaign oder LDAP. Sie müssen einzeln erstellt werden, sowohl in Adobe Campaign als auch im LDAP-Ordner.

   Die Gruppennamen im LDAP-Ordner müssen mit den Gruppennamen der Adobe Campaigne übereinstimmen. Die Zuordnungsmaske wird im letzten Konfigurationsstadium des Bereitstellungsassistenten definiert: Adobe Campaign_(.*), z. B.

