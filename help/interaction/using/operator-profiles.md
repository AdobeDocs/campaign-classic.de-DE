---
title: Benutzerprofile
seo-title: Benutzerprofile
description: Benutzerprofile
seo-description: null
page-status-flag: never-activated
uuid: cd718d20-79cb-40ed-b2ae-23186387e2db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 9a3f1dc9-71ef-4039-94b4-a217996f6a80
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '412'
ht-degree: 100%

---


# Benutzerprofile{#operator-profiles}

In Interaction werden zwei verschiedene Profile benötigt: ein angebotsverantwortlicher und ein versandverantwortlicher Benutzer. Die entsprechenden Benutzer haben jeweils nur auf bestimmte Bereiche des Navigationsbaums Zugriff.

* **[!UICONTROL Angebotsverantwortlicher]**: erstellt und verwaltet Angebote;. Beachten Sie, dass, wenn Angebote im Workflow verwendet werden, der Benutzer in der Benutzergruppe **[!UICONTROL Administrator]** oder **[!UICONTROL Angebotsverantwortliche Benutzer]** sein muss, um den Workflow auszuführen.
* **[!UICONTROL Versandverantwortlicher]**: validiert und verwendet Angebote.

Die Erstellung der Interaction-Benutzerprofile folgt der üblichen Vorgehensweise. Lesen Sie diesbezüglich [diesen Abschnitt](../../platform/using/access-management.md#creating-an-operator). Die spezifischen Berechtigungen werden im Verlauf der Benutzererstellung zugewiesen.

## Angebotsverantwortliche Benutzer {#offer-manager}

1. Erstellen Sie den neuen Benutzer.
1. Klicken Sie im Fenster **[!UICONTROL Gruppen oder spezifische Berechtigungen]** auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Gruppe **[!UICONTROL Angebotsverantwortliche Benutzer]** aus.

   ![](assets/offer_operators_create_001.png)

Die dem Angebotsverantwortlichen zugewiesenen Berechtigungen erlauben ihm folgende Tätigkeiten:

* Änderung von **[!UICONTROL Design-Umgebungen]**;
* Ansicht von **[!UICONTROL Live-Umgebungen]**;
* Konfiguration von administrativen Funktionen (Platzierungen und vordefinierte Filter);
* Erstellung und Änderung von Angebotskategorien;
* Erstellung und Änderung von Angeboten;
* Konfiguration von Angebotseignungen;
* Validierung von Angeboten.

   >[!NOTE]
   >
   >Der Angebotsverantwortliche kann nur die Angebote validieren, für die kein anderer Validierer konfiguriert oder in deren Angebotsvorlage er als Validierer bezeichnet wurde. Letzteres erfolgt durch den für die Vorlagenerstellung zuständigen Administrator, der in diesem Fall über die spezifische Berechtigung zur &quot;Validierungsadministration&quot; verfügen muss.

## Versandverantwortliche Benutzer {#delivery-manager}

1. Erstellen Sie den neuen Benutzer.
1. Klicken Sie im Fenster **[!UICONTROL Gruppen oder spezifische Berechtigungen]** auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Gruppe **[!UICONTROL Versandverantwortliche Benutzer]** aus.

   ![](assets/offer_operators_create_002.png)

Die dem Versandverantwortlichen zugewiesenen Berechtigungen erlauben ihm folgende Tätigkeiten:

* Ansicht der **[!UICONTROL Design-Umgebungen]**;
* Anzeige und Änderung von Angebotskategorien;
* Validierung von Angeboten, wenn er als Validierer bezeichnet wurde.

   >[!NOTE]
   >
   >Der Versandverantwortliche kann nur Angebote validieren, für die er bei deren Konfiguration als Validierer bezeichnet wurde.

## Zusammenfassende Darstellung der Rechte nach Benutzertyp {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Angebotsverantwortlicher (Design-Umgebung)</strong><br /> </td> 
   <td> <strong>Angebotsverantwortlicher (Live-Umgebung)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Knoten im Navigationsbaum</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Angebote - Design/Live<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Umgebung - Empfänger<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Platzierungen<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Vordefinierte Angebotsfilter<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologien<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologieregeln<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Angebotskatalog<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Angebotskategorien<br /> </td> 
   <td> Lesen/Schreiben<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Versandverantwortlicher (Design-Umgebung)</strong><br /> </td> 
   <td> <strong>Versandverantwortlicher (Live-Umgebung)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Knoten im Navigationsbaum</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Angebote - Design/Live<br /> </td> 
   <td> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Umgebung - Empfänger<br /> </td> 
   <td> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Platzierungen<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Vordefinierte Angebotsfilter<br /> </td> 
   <td> Lesen<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologien<br /> </td> 
   <td> Lesen<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologieregeln<br /> </td> 
   <td> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Angebotskatalog<br /> </td> 
   <td> Lesen<br /> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
  <tr> 
   <td> Angebotskategorien<br /> </td> 
   <td> </td> 
   <td> Lesen<br /> </td> 
  </tr> 
 </tbody> 
</table>

