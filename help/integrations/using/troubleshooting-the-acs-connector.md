---
title: Problembehebung bei ACS Connector
seo-title: Problembehebung bei ACS Connector
description: Problembehebung bei ACS Connector
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Problembehebung bei ACS Connector{#troubleshooting-the-acs-connector}

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

   To make sure the field you want to use is available, you can check the profile resource definition from **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Abgesehen davon werden keine Daten standardmäßig nach Campaign Standard synchronisiert, die mit Empfängern verknüpft und in nms:recipients-Empfängertabellen gespeichert sind.

   To still be able to use related data, you can perform your targeting in Campaign v7 and add additional data as explained in the [Synchronizing audiences](../../integrations/using/synchronizing-audiences.md) section, or you can refer to your consultant to explore customization possibilities.

* **Ich verwende in Campaign v7 eine andere Profildimension als die Standardtabelle nms:recipient. Wie kann ich diese Profildimension mit Campaign Standard synchronisieren?**

   Campaign Standard verwendet eine eindeutige Zielgruppen-Ressource namens **Profile**. Die einfache Implementierung der ACS Connector-Funktion beinhaltet ein standardmäßiges Mapping zwischen Campaign v7-Empfängern und Campaign Standard-Profilen.

   Wenn Sie in Campaign v7 eine andere Profildimension oder mehrere Profildimensionen verwenden, müssen alle mit Campaign Standard-Profilen gemappt werden. Wenden Sie sich bitte in dieser Angelegenheit an Ihren Consultant.

* **Ich möchte mit einem Workflow eine Profilliste nach Campaign Standard übertragen, kann aber in Campaign Standard meine Zielgruppe nicht finden**.

   Zielgruppen finden Sie im **[!UICONTROL Audiences]** Menü in Campaign Standard. Sie haben die Beschriftung, die in der **[!UICONTROL List update]** Aktivität in Ihrem Kampagnen-v7-Arbeitsablauf angegeben ist. Sie unterliegen der während der Implementierung definierten Ordnerzuordnung.

   Zunächst muss geprüft werden, ob der Workflow fehlerfrei abgeschlossen wurde. Wenn Sie einen Fehler bei der **[!UICONTROL List update]** Aktivität bemerken, bedeutet dies, dass die Synchronisierung mit Campaign Standard möglicherweise fehlgeschlagen ist. Um weitere Details zu den Fehlern anzuzeigen, gehen Sie zu **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Dieser Ordner enthält Synchronisierungs-Workflows, die durch die Ausführung der **[!UICONTROL List update]** Aktivität ausgelöst werden.

   Also, make sure that the **[!UICONTROL Share with ACS]** option is checked in the **[!UICONTROL List update]** activity and that the workflow was correctly executed.

   Beachten Sie, dass vor dem Workflow die in der Liste enthaltenen Empfängerprofile mit Campaign Standard synchronisiert worden sein müssen. Nach der Übertragung der Empfänger an Campaign Standard werden diese mit Campaign Standard-Profilen abgeglichen, d. h. sie müssen dort vorhanden sein. Empfänger auf der Liste, die nicht mit Profilen in Campaign Standard abgeglichen werden können, werden ignoriert.

   Wird eine Liste mit Profilen übertragen, von denen keines mit Campaign Standard synchronisiert wird, wird in Campaign Standard eine leere Abfrage-Zielgruppe erstellt, die nicht verwendet werden kann.

* **Ich habe eine Nachricht über den Fehlerstatus eines Synchronisations-Workflows erhalten. Was soll ich jetzt tun?**

   Prüfen Sie die externe Kontokonfiguration von sowohl Campaign Standard als auch Campaign v7, indem Sie die Verbindung testen:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7.

* **Beim Mapping von Ordnern zwischen Campaign v7 und Campaign Standard ist keine Sicherheitsgruppe verfügbar.**

   Zunächst müssen Sie die Sicherheitsgruppen synchronisieren, von **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]** denen aus Sie die Daten abrufen. Diese Aktion überprüft die in Campaign Standard verfügbaren Sicherheitsgruppen. Nach der Synchronisierung können Sie die Sicherheitsgruppen beim Konfigurieren der Ordnerzuordnung suchen.

* **Ich kann in Campaign Standard weder ein Profil, noch eine Zielgruppe oder Landingpage bearbeiten. Warum?**

   Alle von Campaign v7 synchronisierten Ressourcen sind in Campaign Standard im schreibgeschützten Modus vorhanden, um eine homogene Datenbasis sicherzustellen. Wenn Sie eines dieser Elemente bearbeiten müssen, tun Sie das in Campaign v7 und replizieren Sie dann die Änderung nach Campaign Standard.

