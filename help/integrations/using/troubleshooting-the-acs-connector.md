---
product: campaign
title: Fehlerbehebung beim ACS-Connector
description: Fehlerbehebung beim ACS-Connector
feature: ACS Connector, Troubleshooting
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
TQID: https://experienceleague.adobe.com/hqQ4rSZpOoCMn9sA0yu2VsHFxTGEnwGwOMi6cu6e-1Q
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 901
ht-degree: 59%

---

# Fehlerbehebung beim ACS-Connector{#troubleshooting-the-acs-connector}



Je nach der Art der Implementierung können verschiedene Probleme auftreten.

* **Was sind die Unterschiede in der Benutzeroberfläche zwischen Campaign Standard und Campaign v7?**

  Campaign Standard und Campaign v7 funktionieren sehr ähnlich. Die meisten Konzepte sind identisch, aber in einigen Fällen kann der Ansatz geringfügig abweichen. Im Folgenden finden Sie einige Konzepte, die sich im Kontext des ACS-Connectors unterscheiden können:

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
   <td> Zielgruppe<br /> </td> 
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

   * Empfänger wurden soeben in Campaign v7 erstellt oder aktualisiert. Die Synchronisierung wird alle 15 Minuten Trigger. Das bedeutet, dass aktualisierte oder neu erstellte Empfängerinnen und Empfänger nach der nächsten Synchronisierung in Campaign Standard angezeigt werden.
   * Ihre Implementierung kann so eingestellt worden sein, dass nur Empfänger aus bestimmten Ordnern synchronisiert werden. Empfänger aus anderen Ordnern werden nicht synchronisiert.
   * Die Empfängerin bzw. der Empfänger kann synchronisiert, aber in Campaign Standard nicht angezeigt werden. Überprüfen Sie die Ordner-Rechtezuordnung.

* **Ich kann die Profilfelder nicht finden, mit denen ich meine Abfrage in Campaign Standard erstelle.**

  Standardmäßig werden 20 Felder aus der nms:recipient-Tabelle mit Campaign Standard synchronisiert. Sehen Sie sich dazu die detaillierte Liste synchronisierter Feldern an. Jedes zusätzliche Feld, das Sie in Campaign Standard abrufen möchten, muss von Ihrem Consultant zugeordnet und konfiguriert werden.

  Um zu überprüfen, ob das gewünschte Feld verfügbar ist, sehen Sie sich die Definition der Profilressource in **[!UICONTROL Administration > Entwicklung > Prüfung > Datenschemata]** an.

  Außerdem werden alle an Empfänger angehängten und in mit nms:recipients verknüpften Tabellen gespeicherten Daten nicht standardmäßig mit Campaign Standard synchronisiert.

  Um dennoch verknüpfte Daten verwenden zu können, nehmen Sie die Zielgruppenbestimmung in Campaign v7 vor und fügen Sie zusätzliche Daten wie in Abschnitt  [Synchronisieren von Audiences](../../integrations/using/synchronizing-audiences.md) beschrieben hinzu. Andernfalls können Sie sich auch an Ihren Berater wenden, um Anpassungsmöglichkeiten zu prüfen.

* **Ich verwende in Campaign v7 eine andere Profildimension als :recipient standardmäßige nms. Wie kann ich diese mit Campaign Standard synchronisieren?**

  Campaign Standard verwendet eine eindeutige Zielgruppenbestimmungsressource mit dem Namen **profiles**. Die Standardimplementierung der Campaign Standard Connect-Funktion bietet eine standardmäßige Zuordnung zwischen Campaign v7-Empfängerinnen und -Empfängern und Campaign Standard-Profilen.

  Wenn Sie eine andere Profildimension in Campaign v7 verwenden oder mehrere Profildimensionen verwenden, müssen diese allen Campaign Standard-Profilen zugeordnet werden. Wenden Sie sich an Ihren Berater, um diese spezielle Anforderung zu erfüllen.

* **Ich möchte mit einem Workflow eine Profilliste nach Campaign Standard übertragen, kann aber in Campaign Standard meine Zielgruppe nicht finden**.

  Zielgruppen finden Sie in Campaign Standard im Menü **[!UICONTROL Zielgruppen]**. Ihr Titel wird im Campaign v7-Workflow in der Aktivität **[!UICONTROL Listen-Update]** spezifiziert. Zielgruppen basieren auf dem Ordner-Mapping, das während der Implementierung definiert wird.

  Zunächst sollten Sie überprüfen, ob der Workflow ohne Fehler abgeschlossen wurde. Wenn bei der Aktivität **[!UICONTROL Listen-Update]** ein Fehler auftritt, ist möglicherweise die Synchronisation mit Campaign Standard fehlgeschlagen. Um zu sehen, wo der Fehler liegt, gehen Sie zu **[!UICONTROL Administration]** > **[!UICONTROL ACS-Connector]** > **[!UICONTROL Prozesse]** > **[!UICONTROL Prüfung]**. Dieser Ordner enthält Synchronisations-Workflows, die von der Aktivität **[!UICONTROL Listen-Update]** ausgelöst wurden.

  Vergewissern Sie sich außerdem, dass die Option **[!UICONTROL In ACS freigeben]** in der Aktivität **[!UICONTROL Listen-Update]** mit einem Häkchen versehen ist und dass der Workflow korrekt ausgeführt wurde.

  Die in der Liste enthaltenen Empfängerprofile müssen vor der Ausführung des Workflows mit Campaign Standard synchronisiert worden sein. Nach der Freigabe für Campaign Standard werden die Empfänger der Liste mit Campaign Standard-Profilen abgeglichen, d. h. sie müssen dort vorhanden sein. Empfänger aus der Liste, die nicht mit Profilen in Campaign Standard abgeglichen werden können, werden ignoriert.

  Wird eine Liste mit Profilen übertragen, von denen keines mit Campaign Standard synchronisiert wird, wird in Campaign Standard eine leere Abfrage-Zielgruppe erstellt, die nicht verwendet werden kann.

* **Ich habe eine Nachricht über den Fehlerstatus eines Synchronisations-Workflows erhalten. Was soll ich tun?**

  Prüfen Sie die externe Kontokonfiguration von sowohl Campaign Standard als auch Campaign v7, indem Sie die Verbindung testen:

   * **[!UICONTROL acsDefaultRelayAccount]** in Campaign Standard
   * **[!UICONTROL acsDefaultAccount]** in Campaign v7

* **Beim Mapping von Ordnern zwischen Campaign v7 und Campaign Standard ist keine Sicherheitsgruppe verfügbar.**

  Sie müssen zunächst Ihre Sicherheitsgruppen über **[!UICONTROL Administration > ACS Connector > Rights Management > Sicherheitsgruppen“]**. Diese Aktion überprüft die in Campaign Standard verfügbaren Sicherheitsgruppen. Nach der Synchronisierung können Sie die Sicherheitsgruppen beim Konfigurieren der Ordnerzuordnung finden.

* **Ich kann in Campaign Standard weder ein Profil noch eine Zielgruppe oder Landingpage bearbeiten. Was bedeutet das?**

  Aus Campaign v7 synchronisierte Ressourcen befinden sich in Campaign Standard im schreibgeschützten Modus, um die Datenkonsistenz sicherzustellen. Wenn Sie eines dieser Elemente bearbeiten müssen, können Sie dies in Campaign v7 tun und dann die Änderung in Campaign Standard replizieren.

* **Im Workflow [ACS] Replikation von Versandlog eines Profils treten Fehler auf. Was soll ich tun?**

  Wenn sowohl Campaign Classic- als auch Campaign Standard-Instanzen zum Senden von E-Mails mit getrackten URLs verwendet werden, kann während der Synchronisierung ein Problem mit doppelten URL-Tag-IDs auftreten. In diesem Fall schlägt der Workflow **[ACS] Replikation von Versandlog eines Profils** (newRcpDeliveryLogReplication) mit dem folgenden Fehler fehl:

  `PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.`

  Um das Problem zu beheben und ein erneutes Auftreten zu verhindern, aktualisieren Sie die Aktivität **Tracking-URLs aktualisieren** (writerTrackingUrls) im Workflow und fügen Sie dem Quellausdruck @tagId das Präfix &quot;ACS&quot; hinzu.
