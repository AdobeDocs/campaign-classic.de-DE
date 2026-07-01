---
product: campaign
title: Glossar für Campaign
description: Glossar für Campaign
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
TQID: https://experienceleague.adobe.com/d6fevvmNur-4TC1KFM-09o68GnPFEM6S6SaFICwyCsw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b6fcaf36-3bc4-4604-94f3-81b5d3f41ecf
subfeature_v2: []
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 1128
ht-degree: 100%

---

# Glossar für Campaign{#i-glossary}



Nachfolgend werden die wichtigsten Fachbegriffe aus Interaction erläutert.

* **Umgebung**: Ein Set, das einen Angebotskatalog und Hooks (Angebotsplatzierungen) enthält. Sie müssen für jede Zielgruppendimension eine Umgebung erstellen. Hier bestehen zwei Arten von Einschränkungen:

   * **Design-Umgebung**: Umgebung, in der Angebote erstellt und/oder Typologieregeln definiert werden (Regeln, die bestimmen, welche Angebote einer Zielperson unterbreitet werden sollen oder nicht). Sowohl die Tabelle der in der Angebotszielgruppe enthaltenen Individuen als auch die Tabelle, in der die Angebotsvorschläge gespeichert werden, werden hier angegeben. Der Knoten **[!UICONTROL Design-Umgebung]** enthält Platzierungs-Unterordner, vordefinierte Filter und Angebotskategorien. Für jede **[!UICONTROL Design-Umgebung]** besteht eine entsprechende schreibgeschützte **[!UICONTROL Live-Umgebung]**, die aus derselben **[!UICONTROL Design-Umgebung]** erzeugt wird.
   * **Live-Umgebung**: Eine Live-Umgebung ist mit einer **[!UICONTROL Design-Umgebung]** verknüpft. Sie enthält schreibgeschützte Angebote, deren Inhalte und Eignung in der **[!UICONTROL Design-Umgebung]** genehmigt wurden. Sie sind dazu bestimmt, beispielsweise auf einer Website oder in einem Versand unterbreitet zu werden.

* **Platzierung**: Ordner, der festlegt, wo das Angebot gezeigt wird. Über die Platzierung wird insbesondere der zu verwendende Kanal festgelegt, aber auch die Möglichkeit, ob der Einzelmodus genutzt werden kann (standardmäßig kommt nur der Batch-Modus zum Einsatz). Des Weiteren können hier mithilfe von Darstellungsfunktionen Angebotsinhalte erstellt und Angebotsthemen definiert werden. Eine Platzierung bildet somit die Schnittstelle zwischen dem Angebotsmodul und den diversen Kanälen.

  >[!IMPORTANT]
  >
  >Eine Platzierung ist kein Kommunikationskanal, sondern entspricht einer bestimmten Position im Kanal. Beispielsweise können auf einer Website angezeigte Angebote zwei Platzierungen auf derselben Seite belegen. In diesem Fall haben Sie zwei Platzierungen für denselben Kanal.
  >
  >Die Platzierungen werden zu Beginn eines Projekts festgelegt und können im späteren Verlauf nicht mehr geändert werden.

* **Angebotskatalog**: Ein Satz von in Adobe Campaign definierten Angeboten, die während einer Interaktion ausgewählt werden können. Der Katalog ist hierarchisch strukturiert, wobei jeder Knoten einer Kategorie entspricht.
* **Kategorie**: Ein mit dem Angebotskatalog in einer Umgebung verknüpfter Ordner, der Angebote nach Art, Gültigkeit und Anwendungsthema organisiert. Eine Kategorie kann Unterkategorien enthalten, die alle Eigenschaften der übergeordneten Kategorie übernehmen. Eignungsregeln können für eine Kategorie definiert werden, um sie für mehrere Angebote freizugeben.
* **Themen**: Auf Ebene der Kategorie festgelegte Stichwörter, die es ermöglichen, Angebote bei ihrer Unterbreitung über einen aus- oder eingehenden Kanal zu filtern. Die Angebotsauswahl kann auf eine oder mehrere Kategorien begrenzt werden.

  >[!NOTE]
  >
  >Untergeordnete Kategorien übernehmen automatisch die Themen, die in der übergeordneten Kategorie definiert wurden.

* **Eignungsregeln**: Einschränkungen, die auf eine Umgebung, eine Kategorie oder ein Angebot angewendet werden und sich auf den Gültigkeitszeitraum, die Zielgruppe und die Gewichtung beziehen. Damit können Sie sicherstellen, dass ein Angebot auf den Zielkontakt abgestimmt ist.

  Auf Umgebungsniveau enthalten die Eignungsregeln die Unterbreitungsregeln, die auf Angebote und Zielpersonen angewendet werden.

  In den Kategorien ermöglichen Ihnen die Eignungsregeln, die Gültigkeit der Kategorie zeitlich zu begrenzen, Anwendungsthemen zu definieren und die Zielgruppe zu bestimmen. Außerdem können Sie eine Multiplikatorgewichtung für einen bestimmten Zeitraum definieren. Auf diese Weise können Sie die Regeln für Angebote in anderen Kategorien gemeinsam nutzen und so ihre Verwaltung vereinfachen.

  Auf Angebotsniveau lassen sich mithilfe der Eignungsregeln die Gültigkeit von Angeboten zeitlich begrenzen sowie Kriterien der Zielgruppenbestimmung definieren.

* **Schlichtung**: Auswahl der Angebote, die in einer Umgebung angezeigt werden sollen (geeignete Angebote). Das Schlichtungsprinzip ordnet Angebote nach ihrer Priorität entsprechend den Kriterien, die in Kategorien, Angeboten und Kontextangeboten definiert wurden.
* **Kontakt**: Ein Kontakt aus einer eingehenden Interaktion. Bei der Verarbeitung der Modulaufrufe wird der Kontakt mit einer Zielgruppendimension verknüpft. Es gibt zwei Arten von Kontakten:

   * **[!UICONTROL Identifizierter Kontakt]**: Kontakt, der sich explizit im Kanal identifiziert hat. Bei ausgehenden Interaktionen wird der Kontakt automatisch identifiziert.
   * **[!UICONTROL Anonymer Kontakt]**: Kontakt, der sich nicht explizit im Kanal identifiziert hat, der jedoch mithilfe eines Cookies implizit identifiziert werden kann. Diese Terminologie wird nur für eingehende Interaktionen verwendet.

     >[!NOTE]
     >
     >Nicht identifizierbare anonyme Kontakte werden der Zielgruppendimension der Besucher zugeordnet.

* **Ausgehende Interaktion**: Aufruf an das Interaktionsmodul von einer Kontaktliste aus (für den Versand von E-Mails, Briefpost usw.). Auf jeden Kontakt werden die gleichen Regeln und Prozesse angewendet. Dieser Interaktionstyp wird im Allgemeinen im Batch-Modus verarbeitet.
* **Eingehende Interaktionen**: Interaktion nach einem eingehenden Aufruf, der durch die Aktion eines Kontakts im Kanal generiert wurde. Dieser Interaktionstyp wird in der Regel im Einzelmodus verarbeitet.
* Im **Batch-Modus** können Sie das beste Angebot für eine Gruppe von Kontakten auswählen. Eignungs-/Prioritätsregeln werden auf alle Kontakte der Gruppe angewendet. Dieser Modus wird im Allgemeinen für ausgehende Interaktionen verwendet.
* **Einzelmodus**: Zu einem gegebenen Zeitpunkt wird jeweils ein Kontakt verarbeitet. Dieser Modus wird im Allgemeinen für eingehende Interaktionen und Transaktionsnachrichten verwendet.
* **Identifikationsmodus**: bezieht sich auf den Status eines Kontakts:

   * **[!UICONTROL explizit]**: Der Kontakt konnte identifiziert werden, da er sich in der Kanalschnittstelle mit seinen Kundendaten angemeldet hat.
   * **[!UICONTROL implizit]**: Der Kontakt konnte mithilfe eines Cookies (Sitzungs- oder permanentes Cookie) identifiziert werden. Sie können als anonymer oder identifizierter Kontakt verarbeitet werden.
   * **[!UICONTROL anonym]**: Der Kontakt konnte nicht identifiziert werden.

* **Geeignetes Angebot**: Angebot, das bestimmten, zuvor definierten Bedingungen entspricht und somit einer Zielgruppe auf mit ihrer Markenerfahrung kohärente Weise unterbreitet werden kann.
* **Unterbreitungsregeln**: Typologieregeln, die auf Basis der einem Kontakt bereits vorgeschlagenen Angebote bestimmte Angebote von der Unterbreitung ausschließen. Die Regeln werden auf Ebene der Umgebung der Angebote verzeichnet.
* **Gewichtung**: Formeln, mit denen Sie die Relevanz eines Angebots exakt berechnen können, um das Angebot mit der höchsten Relevanz auszuwählen. Die Gewichtung wird in den Angeboten definiert. Geeignete Angebote werden in absteigender Reihenfolge ihrer Gewichtung berücksichtigt.
* **Rendering-Funktion**: In der Platzierung definierte Funktion zum Erstellen der Angebotsdarstellung basierend auf im Angebot definierten Attributen. Es gibt drei verschiedene Rendering-Funktionsmodi: HTML, XML und Text.
* **Angebotsvorschlag**: Ergebnis der Aktion, bei der einem Kontakt in einer bestimmten Platzierung (z. B. Banner auf einer Website, E-Mail oder SMS) ein oder mehrere Angebote unterbreitet werden. Dieses Ergebnis wird in der Tabelle der Angebotsvorschläge gespeichert. Das Speichern der Vorschläge ist jedoch nicht obligatorisch.
* **Simulation**: Modul, das es ermöglicht, die Angebotsunterbreitung vor der tatsächlichen Unterbreitung bei Zielpersonen zu evaluieren.
* **Vorschau**: Die Vorschau des Angebots, so wie es im Ordner angezeigt wird. Der Zugriff ist über das Angebotseinstellungsfenster oder das Kontaktprofil möglich.
* **Vordefinierte Filter**: Die Regeln vordefinierter Filter können Angebotsparameter berücksichtigen (z. B. Angebots-Code). Sie können nach der Erstellung von Angeboten wiederverwendet werden.
* **Angebotsdarstellung**: Vom Kanal verwendete Informationen zum Darstellen des Angebots. Die Angebotsdarstellung kann in der Rendering-Funktion der Platzierung festgelegt werden, in der das Angebot dargestellt wird, oder direkt in die Benutzeroberfläche eingegeben werden (z. B. im HTML-Block). Ein Angebot kann durch eine Platzierung dargestellt werden.
* **Platzierungswechsel**: Option in einer identifizierten Platzierung, die den Wechsel zu einer anonymen Platzierung auslöst, wenn ein Kontakt weder ex- noch implizit identifiziert werden konnte.
