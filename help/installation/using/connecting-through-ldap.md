---
title: Verbindung über LDAP
seo-title: Verbindung über LDAP
description: Verbindung über LDAP
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Verbindung über LDAP{#connecting-through-ldap}

## Konfigurieren von Campaign und LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>Die LDAP-Konfiguration ist nur für lokale oder hybride Installationen möglich.

Die LDAP-Konfiguration wird im Bereitstellungsassistenten ausgeführt. Die **[!UICONTROL LDAP integration]** Option muss im ersten Konfigurationsschritt ausgewählt werden. Siehe [Bereitstellungsassistent](../../installation/using/deploying-an-instance.md#deployment-wizard).

Im Fenster können Sie die Identifizierung von Adobe Campaign-Benutzern über den angegebenen LDAP-Ordner konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geben Sie die Adresse des LDAP-Servers im **[!UICONTROL LDAP server]** Feld an. Sie können die Anschlussnummer hinzufügen. Standardmäßig wird der Anschluss 389 verwendet.
* Wählen Sie in der Dropdownliste die Authentifizierungsmethode für Benutzer aus:

   * Verschlüsseltes Kennwort (**md5**)

      Standardmodus.

   * Normales Textkennwort + SSL (**TLS**)

      Das gesamte Authentifizierungsverfahren (Kennwort eingeschlossen) wird verschlüsselt. Der sichere Port 636 darf in diesem Modus nicht verwendet werden: Adobe Campaign wechselt automatisch in den abgesicherten Modus.

      Wenn Sie diesen Authentifizierungsmodus verwenden, wird das Zertifikat unter Linux von einer openLDAP-Client-Bibliothek überprüft. Es wird empfohlen, ein gültiges SSL-Zertifikat zu verwenden, damit das Authentifizierungsverfahren verschlüsselt wird. Andernfalls werden die Informationen im Klartext angegeben.

      Das Zertifikat wird auch unter Windows überprüft.

   * Windows NT LAN Manager (**NTLM**)

      Proprietäre Windows-Authentifizierung. Die **[!UICONTROL Unique identifier]** wird nur für den Domänennamen verwendet.

   * Distributed Password Authentication (**DPA**)

      Proprietäre Windows-Authentifizierung. Der **[!UICONTROL Unique identifier]** wird nur für den Domänennamen (domain.com) verwendet.

   * Passwort für Text

      Keine Verschlüsselung (nur zur Verwendung in Testphasen).

* Wählen Sie den Benutzerauthentifizierungsmodus aus: **[!UICONTROL Automatically compute the unique user identifier]** (siehe Berechnung[](#distinguished-name-calculation)Distinguished Name) oder **[!UICONTROL Search the unique user identifier in the directory]** (siehe Schritt [Suchen nach Bezeichnern](#searching-for-identifiers)).

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

* Geben Sie die eindeutige Kennung des Benutzers im Verzeichnis (Distinguished Name - DN) im **[!UICONTROL Distinguished Name]** Feld an.

   **[!UICONTROL (login)]** durch die ID des Adobe Campaign-Operators ersetzt.

   >[!CAUTION]
   >
   >Die **[!UICONTROL dc]** Einstellung muss in Kleinbuchstaben angegeben werden.

* Wählen Sie die Option aus, **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** um die Gruppen- und Benutzerzuordnungen im LDAP-Ordner sowie die Gruppen- und Benutzerzuordnungen in Adobe Campaign zu synchronisieren.

   Wenn Sie diese Option auswählen, sind die Optionen **[!UICONTROL Application level DN used for the search]** und **[!UICONTROL Password of the application login]** aktiviert.

   Wenn Sie diese beiden Felder ausfüllen, stellt Adobe Campaign eine Verbindung mit dem LDAP-Server her, der über eine eigene Anmeldung und ein eigenes Kennwort verfügt. Wenn sie leer sind, stellt Adobe Campaign eine anonyme Verbindung zum Server her.

## Suchen nach Identifikatoren {#searching-for-identifiers}

Wenn Sie nach einem Bezeichner suchen möchten, können Sie die Suche im Bereitstellungsassistenten konfigurieren.

* Geben Sie in den Feldern **[!UICONTROL Application level DN used for the search]** und **[!UICONTROL Password of the application login]** das Kennwort, mit dem Adobe Campaign eine Verbindung zur Suche nach dem Bezeichner herstellt, ein. Wenn sie leer sind, stellt Adobe Campaign eine anonyme Verbindung zum Server her.
* Geben Sie die **[!UICONTROL Base identifier]** und die **[!UICONTROL Search scope]** Felder an, um eine Untergruppe des LDAP-Ordners zu bestimmen, aus dem die Suche gestartet werden soll.

   Wählen Sie den erforderlichen Modus in der Dropdownliste aus:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      Der LDAP-Ordner wird ab einer bestimmten Ebene vollständig durchsucht.

   1. **[!UICONTROL Limited to the base]**.

      Alle Attribute werden in die Suche einbezogen.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      Die Suche wird mit allen Attributen des Ordners und beginnend mit der ersten Ebene des Attributs durchgeführt.

* Mit dem **[!UICONTROL Filter]** Feld können Sie ein Element angeben, um den Suchbereich zu verfeinern.

## LDAP-Autorisierungen konfigurieren {#configuring-ldap-authorizations}

Dieses Fenster wird angezeigt, wenn Sie die **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** Option auswählen.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Sie müssen mehrere Parameter angeben, um die Gruppe(n) zu finden, zu der/denen der Benutzer gehört, und die entsprechenden Rechte, d.h.:

* das **[!UICONTROL Database identifier]** Feld,
* das **[!UICONTROL Search scope]** Feld,

   >[!NOTE]
   >
   >Wenn Sie sich für die Suche nach dem DN entschieden haben, können Sie auswählen, **[!UICONTROL Reuse the DN search parameters]** um die ausgewählten Werte für den DN und den Suchbereich aus dem vorherigen Bildschirm zu übernehmen.

* das **[!UICONTROL Rights search filter]** Feld auf der Grundlage der Anmeldung und des charakteristischen Namens des Benutzers,
* das **[!UICONTROL Attribute containing the group or authorization name]** Feld für den Nutzer,
* das **[!UICONTROL Association mask]** Feld, das die Extraktion des Gruppennamen in Adobe Campaign und der zugehörigen Rechte ermöglicht. Sie können reguläre Ausdrücke verwenden, um nach dem Namen zu suchen.
* Wählen Sie diese Option, **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** damit dem Benutzer automatisch Zugriffsrechte für die Verbindung zugewiesen werden.

Klicken Sie auf **[!UICONTROL Save]** , um die Konfiguration der Instanz abzuschließen.

## Verwalten von Operatoren {#managing-operators}

Nachdem Sie die Konfiguration bestätigt haben, müssen Sie definieren, welche Adobe Campaign-Operatoren über den LDAP-Ordner verwaltet werden.

Um einen Operator mithilfe des LDAP-Ordners zu authentifizieren, bearbeiten Sie das entsprechende Profil und klicken Sie auf den **[!UICONTROL Edit the access parameters]** Link. Wählen Sie die **[!UICONTROL Use LDAP for authentication]** Option aus: Das **[!UICONTROL Password]** Feld ist für diesen Operator grau ausgegraut.

![](assets/s_ncs_install_operator_in_ldap.png)

## Anwendungsbeispiele {#use-cases}

In diesem Abschnitt finden Sie einige einfache Anwendungsfälle, mit denen Sie die am besten geeigneten Konfigurationen je nach Ihren Anforderungen erzielen können.

1. Ein Benutzer wurde im LDAP-Ordner, jedoch nicht in Adobe Campaign erstellt.

   Adobe Campaign kann so konfiguriert werden, dass der Benutzer über seine LDAP-Authentifizierung auf die Plattform zugreift. Adobe Campaign muss die Gültigkeit der ID/Kennwort-Kombination im LDAP-Ordner steuern können, damit der Operator in Adobe Campaign spontan erstellt werden kann. Markieren Sie dazu die **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** Option. In diesem Fall muss auch die Gruppensynchronisierung konfiguriert werden: muss die **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** Option ausgewählt sein.

1. Der Benutzer wurde in Adobe Campaign erstellt, jedoch nicht im LDAP-Ordner.

   Sie können sich nicht bei Adobe Campaign anmelden.

1. Es gibt eine Gruppe im LDAP-Ordner, die nicht in Adobe Campaign vorhanden ist.

   Diese Gruppe wird nicht in Adobe Campaign erstellt. Sie müssen die Gruppe erstellen und die Gruppen synchronisieren, um eine Übereinstimmung über die **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** Option zu aktivieren.

1. In Adobe Campaign gibt es Gruppen, und der LDAP-Ordner wird nach dem Ereignis aktiviert: Benutzergruppen in Adobe Campaign werden nicht automatisch durch den Inhalt von LDAP-Gruppen ersetzt. Wenn eine Gruppe nur in Adobe Campaign vorhanden ist, können ihr keine LDAP-Benutzer hinzugefügt werden, bis die Gruppe in LDAP erstellt und synchronisiert wurde.

   Gruppen werden nie spontan erstellt, egal ob von Adobe Campaign oder LDAP. Sie müssen einzeln erstellt werden, sowohl in Adobe Campaign als auch im LDAP-Ordner.

   Die Namen der Gruppen im LDAP-Ordner müssen mit den Namen der Adobe Campaign-Gruppen übereinstimmen. Die Zuordnungsmaske wird im letzten Konfigurationsschritt des Bereitstellungsassistenten definiert: Adobe Campaign_(.*), z. B.

