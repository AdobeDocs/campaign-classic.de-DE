---
product: campaign
title: Über LDAP verbinden
description: Erfahren Sie, wie Sie sich mit LDAP bei Campaign anmelden
feature: Installation, Instance Settings
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1232'
ht-degree: 1%

---

# Über LDAP verbinden {#connecting-through-ldap}

## Campaign und LDAP konfigurieren {#configuring-campaign-and-ldap}

>[!NOTE]
>
>* Die LDAP-Konfiguration ist nur für On-Premise- oder Hybridinstallationen möglich.
>
>* Stellen Sie sicher, dass Ihr System und Ihre OpenSSL-Versionen mit Campaign kompatibel sind, indem Sie die [Kompatibilitätsmatrix) ](../../rn/using/compatibility-matrix.md). Veraltete Versionen können sich auf Ihre LDAP-Authentifizierung auswirken.
>

Die LDAP-Konfiguration wird im Bereitstellungsassistenten ausgeführt. Die **[!UICONTROL LDAP-Integration]** Option muss im ersten Konfigurationsschritt ausgewählt werden. Siehe [Bereitstellungsassistent](../../installation/using/deploying-an-instance.md#deployment-assistant).

Im Fenster können Sie die Benutzeridentifizierung von Adobe Campaign über das angegebene LDAP-Verzeichnis konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geben Sie die Adresse des LDAP-Servers im Feld **[!UICONTROL LDAP-Server]** an. Sie können die Portnummer hinzufügen. Standardmäßig wird der Port 389 verwendet.
* Wählen Sie in der Dropdown-Liste die Authentifizierungsmethode für Benutzer aus:

   * Verschlüsseltes Kennwort (**md5**) - Standardmodus.

   * Nur-Text-Passwort + SSL (**TLS**) - Die gesamte Authentifizierungsprozedur (Passwort eingeschlossen) wird verschlüsselt. Der sichere Port 636 darf in diesem Modus nicht verwendet werden: Adobe Campaign wechselt automatisch in den abgesicherten Modus.

     Wenn Sie diesen Authentifizierungsmodus unter Linux verwenden, wird das Zertifikat von einer OpenLDAP-Client-Bibliothek überprüft. Es wird empfohlen, ein gültiges SSL-Zertifikat zu verwenden, damit das Authentifizierungsverfahren verschlüsselt wird. Andernfalls werden die Informationen im Klartext angezeigt.

     Das Zertifikat wird auch in Windows verifiziert.

   * Windows NT LAN Manager (**NTLM**) - Proprietäre Windows-Authentifizierung. Die **[!UICONTROL Eindeutige Kennung]** wird nur für den Domain-Namen verwendet.

   * Distributed Password Authentication (**DPA**) - Proprietäre Windows-Authentifizierung. Die **[!UICONTROL Eindeutige Kennung]** wird nur für den Domain-Namen (domain.com) verwendet.

   * Nur-Text-Passwort - Keine Verschlüsselung (nur zur Verwendung in Testphasen).

* Wählen Sie den Benutzerauthentifizierungsmodus aus: **[!UICONTROL Automatische Berechnung der eindeutigen Benutzerkennung]** (siehe Schritt [Berechnung des Distinguished Names](#distinguished-name-calculation)) oder **[!UICONTROL Suchen der eindeutigen Benutzerkennung im Verzeichnis]** (siehe Schritt [Suchen nach Kennungen](#searching-for-identifiers)).

## Kompatibilität {#compatibility}

Welche Systeme kompatibel sind, hängt vom gewählten Authentifizierungsmechanismus ab. Im Folgenden finden Sie eine Kompatibilitätsmatrix für Betriebssysteme und LDAP-Server.

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
   <td> MD5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM UND DPA<br /> </td> 
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

## Berechnung des definierten Namens {#distinguished-name-calculation}

Wenn Sie die DN-Kennungen (Distinguished Name) berechnen möchten, können Sie im nächsten Schritt des Bereitstellungsassistenten den Berechnungsmodus konfigurieren.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Geben Sie die eindeutige Kennung des Benutzers im Verzeichnis (Distinguished Name - DN) im Feld **[!UICONTROL Distinguished Name]** an.

  **[!UICONTROL (Anmeldung)]** wird durch die Kennung des Adobe Campaign-Benutzers ersetzt.

  >[!CAUTION]
  >
  >Die **[!UICONTROL dc]**-Einstellung muss in Kleinbuchstaben angegeben werden.

* Wählen Sie die Option **[!UICONTROL Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Verzeichnis aktivieren]**, um die Gruppen- und Benutzerzuordnungen im LDAP-Verzeichnis und die Gruppen- und Benutzerzuordnungen in Adobe Campaign zu synchronisieren.

  Wenn Sie diese Option auswählen, werden **[!UICONTROL Anwendungsebenenkennung für die Suche]** und **[!UICONTROL Kennwort des]** aktiviert.

  Wenn Sie diese beiden Felder ausfüllen, stellt Adobe Campaign mit seinem eigenen Benutzernamen und Passwort eine Verbindung zum LDAP-Server her. Wenn sie leer sind, stellt Adobe Campaign eine anonyme Verbindung zum Server her.

## Suchen nach Kennungen {#searching-for-identifiers}

Wenn Sie nach einer Kennung suchen, können Sie die Suche im Bereitstellungsassistenten konfigurieren.

* Geben Sie in den Feldern **[!UICONTROL Anwendungsebene-DN für die]** und **[!UICONTROL Kennwort des Anwendungs-]**) die Kennung und das Kennwort ein, mit denen Adobe Campaign eine Verbindung herstellt, um nach der Kennung zu suchen. Wenn sie leer sind, stellt Adobe Campaign eine anonyme Verbindung zum Server her.
* Geben Sie die Felder **[!UICONTROL Basiskennung]** und **[!UICONTROL Suchbereich]** an, um eine Teilmenge des LDAP-Verzeichnisses zu bestimmen, mit dem die Suche gestartet werden soll.

  Wählen Sie in der Dropdown-Liste den gewünschten Modus aus:

  ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Rekursiv (Standardmodus)]**.

      Das LDAP-Verzeichnis wird vollständig durchsucht, beginnend mit einer bestimmten Ebene.

   1. **[!UICONTROL Auf die Basis beschränkt]**.

      Alle Attribute sind in der Suche enthalten.

   1. **[!UICONTROL Auf die erste Unterebene der Basis beschränkt]**.

      Die Suche wird nach allen Attributen des Verzeichnisses und beginnend mit der ersten Ebene des Attributs durchgeführt.

* Im **[!UICONTROL Filter]** können Sie ein Element angeben, um den Suchbereich zu verfeinern.

## Konfigurieren von LDAP-Berechtigungen {#configuring-ldap-authorizations}

Dieses Fenster wird angezeigt, wenn Sie die Option **[!UICONTROL Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Verzeichnis aktivieren]** auswählen.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Sie müssen mehrere Parameter angeben, um die Gruppe oder Gruppen zu finden, zu der der Benutzer gehört, sowie deren entsprechende Rechte, d.h.:

* das Feld **[!UICONTROL Datenbankkennung]**,
* das Feld **[!UICONTROL Suchbereich]**,

  >[!NOTE]
  >
  >Wenn Sie sich für die Suche nach dem DN entschieden haben, können Sie **[!UICONTROL Wiederverwenden der DN-Suchparameter]** auswählen, um die ausgewählten Werte für den DN und den Suchbereich aus dem vorherigen Bildschirm zu übernehmen.

* das Feld **[!UICONTROL Suchfilter]**, basierend auf der Anmeldung und dem definierten Namen des Benutzers,
* das Feld **[!UICONTROL Attribut, das den Gruppen- oder Autorisierungsnamen enthält]**, das den Benutzer betrifft,
* das Feld **[!UICONTROL Zuordnungsmaske]**, das die Extraktion des Gruppennamens in Adobe Campaign und der zugehörigen Berechtigungen ermöglicht. Sie können reguläre Ausdrücke verwenden, um nach dem Namen zu suchen.
* Wählen Sie **[!UICONTROL Aktivieren der im LDAP-Verzeichnis deklarierten Benutzerverbindung, wenn der Benutzer nicht in Adobe Campaign deklariert ist]** aus, damit dem Benutzer bei der Verbindung automatisch Zugriffsrechte gewährt werden.

Klicken Sie auf **[!UICONTROL Speichern]**, um die Konfiguration der Instanz abzuschließen.

## Verwalten von Benutzern {#managing-operators}

Nachdem Sie die Konfiguration bestätigt haben, müssen Sie festlegen, welche Adobe Campaign-Benutzer über das LDAP-Verzeichnis verwaltet werden.

Um einen Benutzer mithilfe des LDAP-Verzeichnisses zu authentifizieren, bearbeiten Sie das entsprechende Profil und klicken Sie auf den **[!UICONTROL Zugriffsparameter bearbeiten]**. Wählen Sie die Option **[!UICONTROL LDAP für Authentifizierung verwenden]** aus: Das Feld **[!UICONTROL Kennwort]** ist für diesen Operator ausgegraut.

![](assets/s_ncs_install_operator_in_ldap.png)

## Anwendungsfälle {#use-cases}

In diesem Abschnitt finden Sie einige einfache Anwendungsfälle, in denen Sie entsprechend Ihren Anforderungen die am besten geeigneten Konfigurationen erzielen können.

1. Ein Benutzer wurde im LDAP-Verzeichnis, aber nicht in Adobe Campaign erstellt.

   Adobe Campaign kann so konfiguriert werden, dass Benutzende über ihre LDAP-Authentifizierung auf die Plattform zugreifen. Adobe Campaign muss in der Lage sein, die Gültigkeit der ID/Kennwort-Kombination im LDAP-Verzeichnis zu kontrollieren, damit der Benutzer in Adobe Campaign direkt erstellt werden kann. Aktivieren Sie dazu die Option **[!UICONTROL Aktivieren der im LDAP-Verzeichnis deklarierten Benutzerverbindung, wenn der Benutzer nicht in Adobe Campaign deklariert ist]**. In diesem Fall muss auch die Gruppensynchronisierung konfiguriert werden: Die Option **[!UICONTROL Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Verzeichnis aktivieren]** muss ausgewählt sein.

1. Der Benutzer wurde in Adobe Campaign erstellt, jedoch nicht im LDAP-Verzeichnis.

   Sie können sich nicht bei Adobe Campaign anmelden.

1. Im LDAP-Ordner befindet sich eine Gruppe, die in Adobe Campaign nicht vorhanden ist.

   Diese Gruppe wird nicht in Adobe Campaign erstellt. Sie müssen die Gruppe erstellen und die Gruppen synchronisieren, um eine Zuordnung über die Option **[!UICONTROL Synchronisierung von Benutzerrechten aus Berechtigungen und Gruppen im Verzeichnis aktivieren]** zu aktivieren.

1. Gruppen existieren in Adobe Campaign und das LDAP-Verzeichnis wird nach dem Ereignis aktiviert: Benutzergruppen in Adobe Campaign werden nicht automatisch durch den Inhalt von LDAP-Gruppen ersetzt. Wenn eine Gruppe nur in Adobe Campaign vorhanden ist, können ihr keine LDAP-Benutzer hinzugefügt werden, bis die Gruppe in LDAP erstellt und synchronisiert wurde.

   Gruppen werden nie im laufenden Betrieb erstellt, weder durch Adobe Campaign noch durch LDAP. Sie müssen einzeln erstellt werden, sowohl in Adobe Campaign als auch im LDAP-Verzeichnis.

   Die Namen der Gruppen im LDAP-Verzeichnis müssen mit den Namen der Adobe Campaign-Gruppen übereinstimmen. Die Zuordnungsmaske wird im letzten Konfigurationsschritt des Bereitstellungsassistenten definiert: Adobe Campaign_(.&#42;), zum Beispiel.
