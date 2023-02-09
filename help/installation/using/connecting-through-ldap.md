---
product: campaign
title: Über LDAP verbinden
description: Erfahren Sie, wie Sie sich mit LDAP bei Campaign anmelden.
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 2%

---

# Über LDAP verbinden{#connecting-through-ldap}

![](../../assets/v7-only.svg)

## Campaign und LDAP konfigurieren {#configuring-campaign-and-ldap}

>[!NOTE]
>
>Die LDAP-Konfiguration ist nur für On-Premise- oder Hybridinstallationen möglich.

Die LDAP-Konfiguration wird im Softwareverteilungs-Assistenten durchgeführt. Die **[!UICONTROL LDAP-Integration]** muss im ersten Konfigurationsschritt ausgewählt werden. Siehe [Implementierungsassistent](../../installation/using/deploying-an-instance.md#deployment-wizard).

Im Fenster können Sie die Identifizierung von Adobe Campaign-Benutzern über den angegebenen LDAP-Ordner konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geben Sie die Adresse des LDAP-Servers im **[!UICONTROL LDAP-Server]** -Feld. Sie können die Portnummer hinzufügen. Standardmäßig wird der Port 389 verwendet.
* Wählen Sie in der Dropdown-Liste die Authentifizierungsmethode für Benutzer aus:

   * Verschlüsseltes Kennwort (**md5**)

      Standardmodus.

   * Nur Text Passwort + SSL (**TLS**)

      Das gesamte Authentifizierungsverfahren (einschließlich Kennwort) ist verschlüsselt. Der sichere Port 636 darf in diesem Modus nicht verwendet werden: Adobe Campaign wechselt automatisch in den abgesicherten Modus.

      Wenn Sie diesen Authentifizierungsmodus verwenden, wird das Zertifikat unter Linux von einer openLDAP-Client-Bibliothek überprüft. Es wird empfohlen, ein gültiges SSL-Zertifikat zu verwenden, damit das Authentifizierungsverfahren verschlüsselt wird. Andernfalls werden Informationen in Klartext geschrieben.

      Das Zertifikat wird auch unter Windows überprüft.

   * Windows NT LAN Manager (**NTLM**)

      Proprietäre Windows-Authentifizierung. Die **[!UICONTROL Eindeutige Kennung]** wird nur für den Domänennamen verwendet.

   * Distributed Password Authentication (**DPA**)

      Proprietäre Windows-Authentifizierung. Die **[!UICONTROL Eindeutige Kennung]** wird nur für den Domänennamen (domain.com) verwendet.

   * Sichtbares Kennwort

      Keine Verschlüsselung (nur zur Verwendung in Testphasen).

* Wählen Sie den Authentifizierungsmodus für den Benutzer aus: **[!UICONTROL Automatische Berechnung der eindeutigen Benutzerkennung]** (siehe Schritt [Berechnung des Distinguished Name](#distinguished-name-calculation)) oder **[!UICONTROL Suchen Sie die eindeutige Benutzer-ID im Verzeichnis .]** (siehe Schritt [Suchen nach Identifikatoren](#searching-for-identifiers)).

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
   <td> Nur Text<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Berechnung des Distinguished Name {#distinguished-name-calculation}

Wenn Sie die Kennungen des Distinguished Name (DN) berechnen möchten, können Sie im nächsten Schritt des Softwareverteilungs-Assistenten den Berechnungsmodus konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Geben Sie die eindeutige Kennung des Benutzers im Verzeichnis (Distinguished Name - DN) im **[!UICONTROL Distinguished Name]** -Feld.

   **[!UICONTROL (Anmeldung)]** durch die Kennung des Adobe Campaign-Operators ersetzt.

   >[!CAUTION]
   >
   >Die **[!UICONTROL dc]** -Einstellung muss in Kleinbuchstaben erfolgen.

* Auswählen der Option **[!UICONTROL Aktivieren der Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Ordner]** um die Gruppen- und Benutzerzuordnungen im LDAP-Ordner sowie die Gruppen- und Benutzerzuordnungen in Adobe Campaign zu synchronisieren.

   Wenn Sie diese Option auswählen, wird die **[!UICONTROL DN der Anwendungsebene, der für die Suche verwendet wird]** und **[!UICONTROL Passwort der Anwendungsanmeldung]** aktiviert sind.

   Wenn Sie diese beiden Felder ausfüllen, stellt Adobe Campaign eine Verbindung zum LDAP-Server mit seinem eigenen Login und Passwort her. Wenn sie leer sind, stellt Adobe Campaign anonym eine Verbindung zum Server her.

## Suchen nach Identifikatoren {#searching-for-identifiers}

Wenn Sie nach einer Kennung suchen, können Sie mit dem Softwareverteilungs-Assistenten die Suche konfigurieren.

* Im **[!UICONTROL DN der Anwendungsebene, der für die Suche verwendet wird]** und **[!UICONTROL Passwort der Anwendungsanmeldung]** Geben Sie die Kennung und das Kennwort an, mit denen Adobe Campaign eine Verbindung zur Suche nach der Kennung herstellen wird. Wenn sie leer sind, stellt Adobe Campaign anonym eine Verbindung zum Server her.
* Geben Sie die **[!UICONTROL Basis-ID]** und **[!UICONTROL Suchbereich]** -Felder, um eine Teilmenge des LDAP-Ordners zu bestimmen, aus dem die Suche gestartet werden soll.

   Wählen Sie in der Dropdown-Liste den gewünschten Modus aus:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Rekursiv (Standardmodus)]**.

      Der LDAP-Ordner wird vollständig durchsucht, beginnend mit einer bestimmten Ebene.

   1. **[!UICONTROL Auf die Datenbank beschränkt]**.

      Alle Attribute sind in der Suche enthalten.

   1. **[!UICONTROL Beschränkt auf die erste Unterebene der Basis]**.

      Die Suche wird für alle Attribute des Ordners durchgeführt und beginnt ab der ersten Ebene des Attributs.

* Die **[!UICONTROL Filter]** -Feld können Sie ein Element angeben, um den Suchbereich zu verfeinern.

## Konfigurieren von LDAP-Berechtigungen {#configuring-ldap-authorizations}

Dieses Fenster wird angezeigt, wenn Sie die **[!UICONTROL Aktivieren der Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Ordner]** -Option.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Sie müssen mehrere Parameter angeben, um die Gruppe(n), zu der/denen der Benutzer gehört, und die entsprechenden Berechtigungen zu finden, d. h.:

* die **[!UICONTROL Datenbank-ID]** -Feld,
* die **[!UICONTROL Suchbereich]** -Feld,

   >[!NOTE]
   >
   >Wenn Sie nach dem DN suchen möchten, können Sie **[!UICONTROL Verwenden Sie die DN-Suchparameter erneut.]** um die ausgewählten Werte für den DN und den Suchbereich vom vorherigen Bildschirm zu übernehmen.

* die **[!UICONTROL Berechtigungssuchfilter]** -Feld basierend auf dem Login und dem Distinguished Name des Benutzers;
* die **[!UICONTROL Attribut, das den Gruppen- oder Autorisierungsnamen enthält]** -Feld für den Benutzer,
* die **[!UICONTROL Zuordnungsmaske]** -Feld, das die Extraktion des Gruppennamen in Adobe Campaign und der zugehörigen Berechtigungen ermöglicht. Sie können reguläre Ausdrücke verwenden, um nach dem Namen zu suchen.
* Auswählen **[!UICONTROL Aktivieren Sie die Verbindung von im LDAP-Ordner deklarierten Benutzern, wenn der Benutzer nicht in Adobe Campaign deklariert ist.]** damit dem Benutzer automatisch Zugriffsberechtigungen für die Verbindung gewährt werden.

Klicken **[!UICONTROL Speichern]** , um die Konfiguration der Instanz abzuschließen.

## Benutzer verwalten {#managing-operators}

Nachdem Sie die Konfiguration bestätigt haben, müssen Sie festlegen, welche Adobe Campaign-Operatoren über den LDAP-Ordner verwaltet werden.

Um den LDAP-Ordner zum Authentifizieren eines Benutzers zu verwenden, bearbeiten Sie das entsprechende Profil und klicken Sie auf die **[!UICONTROL Zugriffsparameter bearbeiten]** Link. Wählen Sie die **[!UICONTROL LDAP für Authentifizierung verwenden]** Option: Die **[!UICONTROL Passwort]** für diesen Operator ausgegraut wurde.

![](assets/s_ncs_install_operator_in_ldap.png)

## Anwendungsfälle {#use-cases}

In diesem Abschnitt finden Sie einige einfache Anwendungsfälle, mit denen Sie die am besten geeigneten Konfigurationen entsprechend Ihren Anforderungen erreichen können.

1. Ein Benutzer wurde im LDAP-Ordner erstellt, jedoch nicht in Adobe Campaign.

   Adobe Campaign kann so konfiguriert werden, dass der Anwender über seine LDAP-Authentifizierung auf die Plattform zugreift. Adobe Campaign muss in der Lage sein, die Gültigkeit der ID/Kennwort-Kombination im LDAP-Ordner zu steuern, damit der Benutzer in Adobe Campaign spontan erstellt werden kann. Überprüfen Sie dazu die **[!UICONTROL Aktivieren Sie die Verbindung von im LDAP-Ordner deklarierten Benutzern, wenn der Benutzer nicht in Adobe Campaign deklariert ist.]** -Option. In diesem Fall muss auch die Gruppensynchronisierung konfiguriert werden: die **[!UICONTROL Aktivieren der Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Ordner]** ausgewählt werden.

1. Der Benutzer wurde in Adobe Campaign erstellt, jedoch nicht im LDAP-Ordner.

   Sie können sich nicht bei Adobe Campaign anmelden.

1. Im LDAP-Ordner befindet sich eine Gruppe, die nicht in Adobe Campaign vorhanden ist.

   Diese Gruppe wird nicht in Adobe Campaign erstellt. Sie müssen die Gruppe erstellen und die Gruppen synchronisieren, um eine Übereinstimmung über die **[!UICONTROL Aktivieren der Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Ordner]** -Option.

1. Gruppen sind in Adobe Campaign vorhanden und der LDAP-Ordner wird nach dem Ereignis aktiviert: Benutzergruppen in Adobe Campaign werden nicht automatisch durch den Inhalt von LDAP-Gruppen ersetzt. Wenn eine Gruppe nur in Adobe Campaign vorhanden ist, können auch keine LDAP-Benutzer hinzugefügt werden, bis die Gruppe in LDAP erstellt und synchronisiert wurde.

   Gruppen werden nie spontan erstellt, sei es durch Adobe Campaign oder LDAP. Sie müssen einzeln erstellt werden, sowohl in Adobe Campaign als auch im LDAP-Ordner.

   Die Gruppennamen im LDAP-Ordner müssen mit den Namen von Adobe Campaign-Gruppen übereinstimmen. Die Zuordnungsmaske wird im letzten Konfigurationsschritt des Softwareverteilungs-Assistenten definiert: Adobe Campaign_(.&#42;), beispielsweise.
