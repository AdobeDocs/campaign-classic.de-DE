---
product: campaign
title: Benutzerprofile
description: Benutzerprofile
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
TQID: https://experienceleague.adobe.com/B-itT3gDb6FELHi2NUfFUL18s3eKPg4-wWAFkCzN8wI
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2:
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 408
ht-degree: 100%

---

# Benutzerprofile{#operator-profiles}



Zwei Arten von Benutzenden können Interaction verwenden: Angebotsverantwortliche und Versandverantwortliche. Sie verfügen über spezifische Berechtigungen, die ihnen nur Zugriff auf bestimmte Teile der Struktur und der Plattform ermöglichen.

* **[!UICONTROL Angebotsverantwortlicher]**: erstellt und verwaltet Angebote. Beachten Sie, dass, wenn Angebote im Workflow verwendet werden, der Benutzer in der Benutzergruppe **[!UICONTROL Administrator]** oder **[!UICONTROL Angebotsverantwortliche Benutzer]** sein muss, um den Workflow auszuführen.
* **[!UICONTROL Versandverantwortlicher]**: validiert und verwendet Angebote.

Die Erstellung der Interaction-Benutzerprofile folgt der üblichen Vorgehensweise. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](../../platform/using/access-management.md). Die spezifischen Berechtigungen werden im Verlauf der Benutzererstellung zugewiesen.

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
  >Der Angebotsverantwortliche kann ein Angebot nur in zwei bestimmten Fällen validieren. Der erste Fall liegt vor, wenn keine konkrete Person zur Validierung angegeben wurde. Der zweite Fall liegt vor, wenn der Benutzer, der für die Erstellung von Vorlagen zuständig ist (und das Recht zur Zuweisung von Validierern hat), diese Person in der Angebotsvorlage, auf der das Angebot basiert, als Validierer angegeben hat.

## Versandverantwortliche Benutzer {#delivery-manager}

1. Erstellen Sie den neuen Benutzer.
1. Klicken Sie im Fenster **[!UICONTROL Gruppen oder spezifische Berechtigungen]** auf die Schaltfläche **[!UICONTROL Hinzufügen]** und wählen Sie die Gruppe **[!UICONTROL Versandverantwortliche Benutzer]** aus.

   ![](assets/offer_operators_create_002.png)

Die den Versandverantwortlichen zugewiesenen Berechtigungen erlauben ihnen folgende Tätigkeiten:

* Ansicht der **[!UICONTROL Design-Umgebungen]**;
* Anzeige und Änderung von Angebotskategorien;
* Validierung von Angeboten, wenn dieser Versandverantwortliche als Validierer bezeichnet wurde.

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
