---
product: campaign
title: Verbindung über LDAP
description: Erfahren Sie, wie Sie sich mit LDAP bei Campaign anmelden.
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 1%

---

# Verbindung über LDAP{#connecting-through-ldap}

## Campaign und LDAP konfigurieren {#configuring-campaign-and-ldap}

>[!NOTE]
>
>Die LDAP-Konfiguration ist nur für On-Premise- oder Hybridinstallationen möglich.

Die LDAP-Konfiguration wird im Softwareverteilungs-Assistenten durchgeführt. Die Option **[!UICONTROL LDAP integration]** muss während des ersten Konfigurationsschritts ausgewählt sein. Siehe [Softwareverteilungs-Assistent](../../installation/using/deploying-an-instance.md#deployment-wizard).

Im Fenster können Sie die Identifizierung von Adobe Campaign-Benutzern über den angegebenen LDAP-Ordner konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geben Sie die Adresse des LDAP-Servers im Feld **[!UICONTROL LDAP server]** an. Sie können die Portnummer hinzufügen. Standardmäßig wird der Port 389 verwendet.
* Wählen Sie in der Dropdownliste die Authentifizierungsmethode für Benutzer aus:

   * Verschlüsseltes Kennwort (**md5**)

     Standardmodus.

   * Nur-Text-Kennwort + SSL (**TLS**)

     Das gesamte Authentifizierungsverfahren (einschließlich Kennwort) ist verschlüsselt. Der sichere Port 636 darf in diesem Modus nicht verwendet werden: Adobe Campaign wechselt automatisch in den abgesicherten Modus.

     Wenn Sie diesen Authentifizierungsmodus verwenden, wird das Zertifikat unter Linux von einer openLDAP-Client-Bibliothek überprüft. Es wird empfohlen, ein gültiges SSL-Zertifikat zu verwenden, damit das Authentifizierungsverfahren verschlüsselt wird. Andernfalls werden Informationen in Klartext geschrieben.

     Das Zertifikat wird auch unter Windows überprüft.

   * Windows NT LAN Manager (**NTLM**)

     Eigenständige Windows-Authentifizierung. Die **[!UICONTROL eindeutige Kennung]** wird nur für den Domänennamen verwendet.

   * Distributed Password Authentication (**DPA**)

     Eigenständige Windows-Authentifizierung. Die **[!UICONTROL eindeutige Kennung]** wird nur für den Domänennamen verwendet (domain.com).

   * Sichtbares Kennwort

     Keine Verschlüsselung (nur zur Verwendung in Testphasen)

* Wählen Sie den Authentifizierungsmodus für den Benutzer aus: **[!UICONTROL Berechnen Sie automatisch die eindeutige Benutzer-ID]** (siehe Schritt [Berechnung des Distinguished Name](#distinguished-name-calculation)) oder **[!UICONTROL Durchsuchen Sie die eindeutige Benutzer-ID im Verzeichnis]** (siehe Schritt [Suchen nach Identifikatoren](#searching-for-identifiers)).

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
   <td> NTLM &amp; DPA<br /> </td> 
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

## Berechnung des Distinguished Name {#distinguished-name-calculation}

Wenn Sie die Kennungen des Distinguished Name (DN) berechnen möchten, können Sie im nächsten Schritt des Softwareverteilungs-Assistenten den Berechnungsmodus konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Geben Sie die eindeutige Kennung des Benutzers im Verzeichnis (Distinguished Name - DN) im Feld **[!UICONTROL Distinguished Name]** an.

  **[!UICONTROL (login)]** wird durch die Kennung des Adobe Campaign-Operators ersetzt.

  >[!CAUTION]
  >
  >Die Einstellung **[!UICONTROL dc]** muss in Kleinbuchstaben angegeben werden.

* Wählen Sie die Option **[!UICONTROL Synchronisierung der Benutzerrechte aus Berechtigungen und Gruppen im Ordner aktivieren]** aus, um die Gruppen- und Benutzerzuordnungen im LDAP-Ordner sowie die Gruppen- und Benutzerzuordnungen in Adobe Campaign zu synchronisieren.

  Wenn Sie diese Option auswählen, sind der für die Suche verwendete DN **[!UICONTROL Anwendungsebene]** und das **[!UICONTROL Kennwort der Anwendungsanmeldung]** aktiviert.

  Wenn Sie diese beiden Felder ausfüllen, stellt Adobe Campaign eine Verbindung zum LDAP-Server mit seinem eigenen Login und Passwort her. Wenn sie leer sind, stellt Adobe Campaign anonym eine Verbindung zum Server her.

## Suchen nach Identifikatoren {#searching-for-identifiers}

Wenn Sie nach einer Kennung suchen, können Sie mit dem Softwareverteilungs-Assistenten die Suche konfigurieren.

* Geben Sie in den Feldern **[!UICONTROL Application level DN für die Suche]** und **[!UICONTROL Password of the application login]** die Kennung und das Kennwort ein, mit denen Adobe Campaign eine Verbindung zur Suche nach der Kennung herstellen wird. Wenn sie leer sind, stellt Adobe Campaign anonym eine Verbindung zum Server her.
* Geben Sie die Felder **[!UICONTROL Basis-ID]** und **[!UICONTROL Suchbereich]** an, um eine Untergruppe des LDAP-Ordners zu bestimmen, aus dem die Suche gestartet werden soll.

  Wählen Sie in der Dropdown-Liste den gewünschten Modus aus:

  ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Rekursiv (Standardmodus)]**.

      Der LDAP-Ordner wird vollständig durchsucht, beginnend mit einer bestimmten Ebene.

   1. **[!UICONTROL Beschränkt auf die Basis]**.

      Alle Attribute sind in der Suche enthalten.

   1. **[!UICONTROL Beschränkt auf die erste Unterebene der Basis]**.

      Die Suche wird für alle Attribute des Ordners durchgeführt und beginnt ab der ersten Ebene des Attributs.

* Im Feld **[!UICONTROL Filter]** können Sie ein Element angeben, um den Suchbereich zu verfeinern.

## Konfigurieren von LDAP-Berechtigungen {#configuring-ldap-authorizations}

Dieses Fenster wird angezeigt, wenn Sie die Option **[!UICONTROL Synchronisierung der Benutzerrechte aus Berechtigungen und Gruppen im Verzeichnis aktivieren]** auswählen.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Sie müssen mehrere Parameter angeben, um die Gruppe(n), zu der/denen der Benutzer gehört, und die entsprechenden Berechtigungen zu finden, d. h.:

* das Feld **[!UICONTROL Datenbankkennung]**,
* das Feld **[!UICONTROL Suchbereich]**,

  >[!NOTE]
  >
  >Wenn Sie nach dem DN suchen möchten, können Sie **[!UICONTROL die DN-Suchparameter wiederverwenden]** auswählen, um die ausgewählten Werte für den DN und den Suchbereich aus dem vorherigen Bildschirm zu übernehmen.

* das Feld **[!UICONTROL Berechtigungs-Suchfilter]** , basierend auf der Anmeldung und dem Distinguished Name des Benutzers;
* das **[!UICONTROL Attribut, das das Feld für die Gruppe oder den Autorisierungsnamen]** für den Benutzer enthält,
* das Feld **[!UICONTROL Zuordnungsmaske]** , das die Extraktion des Gruppennamen in Adobe Campaign und der zugehörigen Berechtigungen ermöglicht. Sie können reguläre Ausdrücke verwenden, um nach dem Namen zu suchen.
* Wählen Sie **[!UICONTROL Aktivieren Sie die Verbindung von im LDAP-Ordner deklarierten Benutzern, wenn der Benutzer nicht in Adobe Campaign]** deklariert ist, damit dem Benutzer automatisch Zugriffsberechtigungen für die Verbindung gewährt werden.

Klicken Sie auf **[!UICONTROL Speichern]** , um die Konfiguration der Instanz abzuschließen.

## Verwalten von Benutzern {#managing-operators}

Nachdem Sie die Konfiguration bestätigt haben, müssen Sie festlegen, welche Adobe Campaign-Operatoren über den LDAP-Ordner verwaltet werden.

Um den LDAP-Ordner zum Authentifizieren eines Benutzers zu verwenden, bearbeiten Sie das entsprechende Profil und klicken Sie auf den Link **[!UICONTROL Zugriffsparameter bearbeiten]** . Wählen Sie die Option **[!UICONTROL LDAP zur Authentifizierung verwenden]** aus: Das Feld **[!UICONTROL Kennwort]** ist für diesen Operator grau ausgeblendet.

![](assets/s_ncs_install_operator_in_ldap.png)

## Anwendungsfälle {#use-cases}

In diesem Abschnitt finden Sie einige einfache Anwendungsfälle, mit denen Sie die am besten geeigneten Konfigurationen entsprechend Ihren Anforderungen erreichen können.

1. Ein Benutzer wurde im LDAP-Ordner erstellt, jedoch nicht in Adobe Campaign.

   Adobe Campaign kann so konfiguriert werden, dass der Benutzer über seine LDAP-Authentifizierung auf die Plattform zugreift. Adobe Campaign muss in der Lage sein, die Gültigkeit der ID/Kennwort-Kombination im LDAP-Ordner zu steuern, damit der Benutzer in Adobe Campaign spontan erstellt werden kann. Aktivieren Sie dazu die Option **[!UICONTROL Aktivieren der Verbindung von im LDAP-Ordner deklarierten Benutzern, wenn der Operator nicht in Adobe Campaign deklariert ist]** . In diesem Fall muss auch die Gruppensynchronisierung konfiguriert werden: Wählen Sie die Option **[!UICONTROL Synchronisation der Benutzerrechte aus Berechtigungen und Gruppen im Ordner aktivieren]** aus.

1. Der Benutzer wurde in Adobe Campaign erstellt, jedoch nicht im LDAP-Ordner.

   Sie können sich nicht bei Adobe Campaign anmelden.

1. Im LDAP-Ordner befindet sich eine Gruppe, die nicht in Adobe Campaign vorhanden ist.

   Diese Gruppe wird nicht in Adobe Campaign erstellt. Sie müssen die Gruppe erstellen und die Gruppen synchronisieren, um eine Übereinstimmung über die Option **[!UICONTROL Aktivieren Sie die Synchronisierung der Benutzerrechte aus Berechtigungen und Gruppen im Ordner]** zu ermöglichen.

1. Gruppen sind in Adobe Campaign vorhanden und der LDAP-Ordner wird nach dem Ereignis aktiviert: Benutzergruppen in Adobe Campaign werden nicht automatisch durch den Inhalt von LDAP-Gruppen ersetzt. Wenn eine Gruppe nur in Adobe Campaign vorhanden ist, können auch keine LDAP-Benutzer hinzugefügt werden, bis die Gruppe in LDAP erstellt und synchronisiert wurde.

   Gruppen werden nie spontan erstellt, sei es durch Adobe Campaign oder LDAP. Sie müssen einzeln erstellt werden, sowohl in Adobe Campaign als auch im LDAP-Ordner.

   Die Gruppennamen im LDAP-Ordner müssen mit den Namen von Adobe Campaign-Gruppen übereinstimmen. Die Zuordnungsmaske wird in der letzten Konfigurationsphase des Softwareverteilungs-Assistenten definiert: Adobe Campaign_(.&#42;), z. B.
