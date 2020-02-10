---
title: Version 18.6
seo-title: Version 18.6
description: Version 18.6
seo-description: null
page-status-flag: never-activated
uuid: 72941f8f-0b84-4868-a768-8aa972459ef2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 79a6d3cf-2425-49b9-9b92-b56be26438bf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d046304657f04312d78176c49a650690b05e4c94

---


# Version 18.6{#release-18-6}

## Version 18.6.2 - Build 8949{#release-18-6-3-build-8949}

22. August 2018

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte führen Sie eine [Aktualisierung auf den aktuellen Build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) durch oder kontaktieren Sie den [technischen Support](https://support.neolane.net/).

**Neue Funktionen?**

<table> 
 <thead> 
  <tr> 
   <th> Funktion<br /> </th> 
   <th> Beschreibung<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Query Banding<br /> </td> 
   <td> <p>Wenn mehrere Campaign-Benutzer auf dasselbe externe FDA-Teradata-Konto zugreifen, können Sie jetzt für jeden Benutzer ein Query Banding (Schlüssel/Wert-Paar) vergeben. Jedes Mal, wenn ein Campaign-Benutzer eine Abfrage für die Teradata-Datenbank durchführt, kann Adobe Campaign nun Metadaten im Zusammenhang mit dem Benutzer senden. Diese Daten, die aus einer Liste von Schlüsseln und Werten bestehen, können dann von Teradata-Administratoren beispielsweise für Audits oder zum Verwalten der Zugriffsberechtigungen verwendet werden.</p><p>Weitere Informationen finden Sie im <a href="https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#Teradata_external_account">entsprechenden Handbuch</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Verbesserungen**

* E-Mail-Archivierungs-Logs wurden verbessert. Dank der BCC-Archivierung kann jetzt einfacher festgestellt werden, welche E-Mails erfolgreich gesendet wurden oder fehlgeschlagen sind. (NEO-10675)
* Fehlerkorrektur – In den Tracking-Broadlogs werden jetzt Kunden-IPs anstatt Lastverteilungs-IPs angezeigt. (NEO-11295)
* Fehlerkorrektur – Die Eigenschaften eines Versands werden nicht mehr fälschlicherweise überschrieben. (NEO-11015)
* Fehlerkorrektur – Beim Sortieren der Ergebnisse von Anreicherungsaktivitäten tritt kein Syntaxfehler mehr auf. (NEO-11394)
* Fixed an issue when using calculated fields in a **[!UICONTROL Survey answers]** workflow activity. (NEO-11382)
* Tomcat wurde aktualisiert, um zu verhindern, dass Schwachstellen ausgenutzt werden können. (NEO-11503)
* Fehlerkorrektur – Bei der LATIN1-Codierung tritt jetzt kein Fehler mehr auf, wenn eine FDA-Verbindung zu einer PostgreSQL-Datenbank verwendet wird. (NEO-11299)
* Es wurde ein Problem behoben, das bei Verwendung der **[!UICONTROL Prepare the personalization data with a workflow]** Auslieferungsoption aufgetreten ist. (NEO-11047)
* Fehlerkorrektur – SMS können jetzt in Verbindung mit einem erweiterten Connector gesendet werden, ohne dass ein Postupgrade-Fehler auftritt.
* Verbesserter Package-Import/-Export (in der Benutzeroberfläche wurden Log und Region hinzugefügt).
* Fixed an issue which displayed useless errors in the postupgrade log when a **[!UICONTROL Survey answers]** workflow activity was not fully configured.

**Technische Entwicklungen**

Query Banding

Die Zuordnung eines Teradata-Benutzers bzw. einer Teradata-Rolle zum jeweiligen Campaign-Benutzer erfolgt über einen speziellen Schlüssel (PROXYUSER oder PROXYROLE). Jetzt wurde eine neue Berechtigung hinzugefügt, um die Verwendung dieser Proxy-Benutzer/-Rollen zu ermöglichen. Sie müssen dazu die Zugriffsberechtigung GRANT CONNECT THROUGH zum Datenbankkonto hinzufügen (das im externen Teradata-Konto definiert wurde).

In den externen Konten von Teradata wurde eine neue Registerkarte hinzugefügt. Die **[!UICONTROL Query banding]** Registerkarte umfasst die folgenden Optionen:

* **[!UICONTROL Active]**: Aktivieren Sie dieses Kontrollkästchen, um die Funktion zu aktivieren.
* **[!UICONTROL Default]**: Geben Sie einen Standardabfrageverband ein, der verwendet wird, wenn ein Benutzer keinen zugehörigen Abfrageverband hat. Wenn keine standardmäßige Abfragebandbildung definiert ist, können die Benutzer, die über keinen zugehörigen Abfrageverband verfügen, keine Teradata verwenden.
* **[!UICONTROL Users]**: Geben Sie für jeden Benutzer einen Abfrageverband an. Sie können so viele Schlüssel/Wert-Paare hinzufügen, wie Sie benötigen. Beispiel: &quot;priority=1;workload=high&quot;

Weitere Informationen zu Query Banding finden Sie in diesen Artikeln.

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Version 18.6 - Build 8947{#release-18-6-build-8947}

25. Juni 2018

>[!CAUTION]
>
>Dieser Build wurde zurückgerufen. Bitte führen Sie eine [Aktualisierung auf den aktuellen Build](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) durch oder kontaktieren Sie den [technischen Support](https://support.neolane.net/).

**Neue Funktionen?**

<table> 
 <thead> 
  <tr> 
   <th> Funktion<br /> </th> 
   <th> Beschreibung<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Verbesserungen bezüglich der Sicherheit<br /> </td> 
   <td> In Campaign Classic wurde eine Reihe von Verbesserungen bezüglich der Sicherheit vorgenommen. Nachfolgend finden Sie eine Liste der Verbesserungen und Fehlerkorrekturen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Unterstützung von Windows Server 2016<br /> </td> 
   <td> Adobe Campaign ist jetzt mit Windows Server 2016 kompatibel. Weiterführende Informationen dazu finden Sie in der <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Kompatibilitätsmatrix von Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Verbesserungen bei der Sicherheit**

decryptString

Die **decryptString**-Funktion ist veraltet. Weitere Informationen finden Sie im Artikel [Veraltete und entfernte Funktionen](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html).

Für Neukunden wird diese Funktion nun nur zum Entschlüsseln der verschlüsselten ID des Empfängers auf Landingpages verwendet. Zum Entschlüsseln von in einem externen Konto gespeicherten Passwörtern verwenden Sie die neue **decryptPassword**-Funktion.

Für Bestandskunden ist das Verhalten dieser Funktion unverändert. Wir empfehlen jedoch, **decryptPassword** anstelle von **decryptString** zu verwenden. Die Kompatibilitätsoption **XtkSecurity_Unsafe_DecryptString** wird vom Postupgrade hinzugefügt und standardmäßig aktiviert, weshalb Sie die Funktion auch weiterhin verwenden können. Wenn Sie **decryptString** deaktivieren möchten, deaktivieren Sie diese Option.

decryptPassword

Die **decryptPassword**-Funktion wurde hinzugefügt. Hiermit können Sie ein in einem externen Konto gespeichertes Passwort entschlüsseln. Weitere Informationen finden Sie in der [JSAPI](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)-Dokumentation.

Datei-APIs

Für Neuinstallationen ist der Ordnerzugriff über Datei-APIs auf **var**, **sftp** und temporäre Ordner von Adobe Campaign beschränkt.

Für Bestandskunden haben Datei-APIs keinen Zugriff mehr auf den Ordner **conf** von Adobe Campaign. Die Kompatibilitätsoption **XtkSecurity_Disable_JSFileSandboxing** wird vom Postupgrade hinzugefügt und standardmäßig aktiviert, weshalb Sie auch weiterhin auf die anderen Ordner zugreifen können. Wenn Sie den Zugriff auf **var**, **sftp** und die temporären Ordner von Adobe Campaign beschränken möchten, deaktivieren Sie diese Option.

**Korrektur**

* Fehlerkorrektur – Die Leistung von SMS-Transaktionsnachrichten wird nun nicht mehr beeinträchtigt. (NEO-9812)
