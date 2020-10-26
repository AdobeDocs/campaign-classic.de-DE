---
title: Fehlerbehebung bei ACS Connector
seo-title: Fehlerbehebung bei ACS Connector
description: Fehlerbehebung bei ACS Connector
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '816'
ht-degree: 100%

---


# Fehlerbehebung bei ACS Connector{#troubleshooting-the-acs-connector}

Je nach der Art der Implementierung können verschiedene Probleme auftreten.

* **Was sind die Unterschiede in der Benutzeroberfläche zwischen Campaign Standard und Campaign v7?**

   Campaign Standard und Campaign v7 sind in ihrer Funktion sehr ähnlich. Obwohl die meisten Konzepte dieselben sind, können in manchen Fällen leicht abweichende Begriffe verwendet werden. Hier sind einige der Begriffe, die im Zusammenhang mit dem ACS Connector anders sein können:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Empfänger (oder eine andere Profildimension)<br /> </td> 
   <td> Profile<br /> </td> 
  </tr> 
  <tr> 
   <td> Liste<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampagnen-Workflows, Zielgruppen-Workflows<br /> </td> 
   <td> Workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampagnen<br /> </td> 
   <td> Kampagnen<br /> </td> 
  </tr> 
  <tr> 
   <td> Webanwendungen<br /> </td> 
   <td> Landingpages<br /> </td> 
  </tr> 
  <tr> 
   <td> Benutzerdefinierte Tabelle und Schemaerweiterung<br /> </td> 
   <td> Benutzerdefinierte Ressource und Ressourcenerweiterung<br /> </td> 
  </tr> 
  <tr> 
   <td> Testempfänger<br /> </td> 
   <td> Testprofile<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **Die Empfänger meiner Campaign v7-Instanz werden nicht nach Campaign Standard synchronisiert oder sind in Campaign Standard nicht sichtbar.**

   Hierfür gibt es mehrere mögliche Gründe:

   * Empfänger wurden nur in Campaign v7 erstellt oder aktualisiert. Die Synchronisation wird alle 15 Minuten ausgelöst. Deshalb sind aktualisierte oder neu erstellte Empfänger erst nach der nächsten Synchronisation in Campaign Standard sichtbar.
   * Ihre Implementierung ist möglicherweise so konfiguriert, dass nur Empfänger aus bestimmten Ordnern synchronisiert werden. Empfänger aus anderen Ordnern werden nicht synchronisiert.
   * Der Empfänger wird möglicherweise synchronisiert, ist aber nicht in Campaign Standard sichtbar. Prüfen Sie das Mapping von Rechten bezüglich Ordnern.

* **Ich kann die Profilfelder nicht finden, mit denen ich meine Abfrage in Campaign Standard erstelle.**

   Standardmäßig werden 20 Felder der Tabelle nms:recipient mit Campaign Standard synchronisiert. Sehen Sie sich dazu die detaillierte Liste synchronisierter Feldern an. Jedes zusätzliche Feld, das Sie in Campaign Standard abrufen möchten, muss von Ihrem Consultant zugeordnet und konfiguriert werden.

   Um zu überprüfen, ob das gewünschte Feld verfügbar ist, sehen Sie sich die Definition der Profilressource in **[!UICONTROL Administration > Entwicklung > Prüfung > Datenschemata]** an.

   Abgesehen davon werden keine Daten standardmäßig nach Campaign Standard synchronisiert, die mit Empfängern verknüpft und in nms:recipients-Empfängertabellen gespeichert sind.

   Um dennoch verknüpfte Daten verwenden zu können, nehmen Sie die Zielgruppenbestimmung in Campaign v7 vor und fügen Sie zusätzliche Daten wie in Abschnitt [Zielgruppen synchronisieren](../../integrations/using/synchronizing-audiences.md) beschrieben hinzu. Andernfalls können Sie sich auch an Ihren Berater wenden, um Anpassungsmöglichkeiten zu prüfen.

* **Ich verwende in Campaign v7 eine andere Profildimension als die Standardtabelle nms:recipient. Wie kann ich diese Profildimension mit Campaign Standard synchronisieren?**

   Campaign Standard verwendet eine eindeutige Zielgruppen-Ressource namens **Profile**. Die einfache Implementierung der ACS Connector-Funktion beinhaltet ein standardmäßiges Mapping zwischen Campaign v7-Empfängern und Campaign Standard-Profilen.

   Wenn Sie in Campaign v7 eine andere Profildimension oder mehrere Profildimensionen verwenden, müssen alle mit Campaign Standard-Profilen gemappt werden. Wenden Sie sich bitte in dieser Angelegenheit an Ihren Consultant.

* **Ich möchte mit einem Workflow eine Profilliste nach Campaign Standard übertragen, kann aber in Campaign Standard meine Zielgruppe nicht finden**.

   Zielgruppen finden Sie in Campaign Standard im Menü **[!UICONTROL Zielgruppen]**. Ihr Titel wird im Campaign v7-Workflow in der Aktivität **[!UICONTROL Listen-Update]** spezifiziert. Zielgruppen basieren auf dem Ordner-Mapping, das während der Implementierung definiert wird.

   Zunächst sollten Sie überprüfen, ob der Workflow ohne Fehler abgeschlossen wurde. Wenn bei der Aktivität **[!UICONTROL Listen-Update]** ein Fehler auftritt, ist möglicherweise die Synchronisation mit Campaign Standard fehlgeschlagen. Um zu sehen, wo der Fehler liegt, gehen Sie zu **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Prozesse]** > **[!UICONTROL Prüfung]**. Dieser Ordner enthält Synchronisations-Workflows, die von der Aktivität **[!UICONTROL Listen-Update]** ausgelöst wurden.

   Vergewissern Sie sich außerdem, dass die Option **[!UICONTROL In ACS freigeben]** in der Aktivität **[!UICONTROL Listen-Update]** mit einem Häkchen versehen ist und dass der Workflow korrekt ausgeführt wurde.

   Beachten Sie, dass vor dem Workflow die in der Liste enthaltenen Empfängerprofile mit Campaign Standard synchronisiert worden sein müssen. Nach der Übertragung der Empfänger an Campaign Standard werden diese mit Campaign Standard-Profilen abgeglichen, d. h. sie müssen dort vorhanden sein. Empfänger auf der Liste, die nicht mit Profilen in Campaign Standard abgeglichen werden können, werden ignoriert.

   Wird eine Liste mit Profilen übertragen, von denen keines mit Campaign Standard synchronisiert wird, wird in Campaign Standard eine leere Abfrage-Zielgruppe erstellt, die nicht verwendet werden kann.

* **Ich habe eine Nachricht über den Fehlerstatus eines Synchronisations-Workflows erhalten. Was soll ich jetzt tun?**

   Prüfen Sie die externe Kontokonfiguration von sowohl Campaign Standard als auch Campaign v7, indem Sie die Verbindung testen:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7

* **Beim Mapping von Ordnern zwischen Campaign v7 und Campaign Standard ist keine Sicherheitsgruppe verfügbar.**

   Synchronisieren Sie zunächst Ihre Sicherheitsgruppen in **[!UICONTROL Administration > ACS Connector > Berechtigungs-Management > Sicherheitsgruppen]**. Damit werden die in Campaign Standard verfügbaren Sicherheitsgruppen überprüft. Danach stehen die Sicherheitsgruppen beim Konfigurieren des Ordner-Mappings zur Verfügung.

* **Ich kann in Campaign Standard weder ein Profil, noch eine Zielgruppe oder Landingpage bearbeiten. Warum?**

   Alle von Campaign v7 synchronisierten Ressourcen sind in Campaign Standard im schreibgeschützten Modus vorhanden, um eine homogene Datenbasis sicherzustellen. Wenn Sie eines dieser Elemente bearbeiten müssen, tun Sie das in Campaign v7 und replizieren Sie dann die Änderung nach Campaign Standard.

