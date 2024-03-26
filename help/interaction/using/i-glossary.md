---
product: campaign
title: Glossar für Campaign
description: Glossar für Campaign
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 89%

---

# Glossar für Campaign{#i-glossary}



Nachfolgend werden die wichtigsten Fachbegriffe aus Interaction erläutert.

* **Umgebung**: Einheit aus Angebotskatalog und Integrationspunkten (Platzierungen). Eine Umgebung wird einer Zielgruppendimension zugeordnet. Es gibt zwei verschiedene Umgebungstypen:

   * **Design-Umgebung**: Umgebung, in der Angebote erstellt und/oder Typologieregeln definiert werden (Regeln, die bestimmen, welche Angebote einer Zielperson unterbreitet werden sollen oder nicht). Die Tabelle der Kontakte, die von den Angeboten angesprochen werden sollen, und die Tabelle zum Speichern aller Angebotsvorschläge werden ebenfalls definiert. Der Knoten **[!UICONTROL Design-Umgebung]** enthält Platzierungs-Unterordner, vordefinierte Filter und Angebotskategorien. Für jede **[!UICONTROL Design-Umgebung]** besteht eine entsprechende schreibgeschützte **[!UICONTROL Live-Umgebung]**, die aus derselben **[!UICONTROL Design-Umgebung]** erzeugt wird.
   * **Live-Umgebung**: Umgebung, die mit einer **[!UICONTROL Design-Umgebung]**. Sie enthält schreibgeschützte Angebote, deren Inhalte und Eignung in der **[!UICONTROL Design-Umgebung]** genehmigt wurden. Sie werden ausgewählt, um auf einer Website angezeigt oder in eine Nachricht eingefügt zu werden.

* **Platzierung**: Ordner, der festlegt, wo das Angebot gezeigt wird. Wenn Sie eine Platzierung definieren, können Sie den verwendeten Kanal angeben, angeben, ob er im Einzelmodus verwendet werden kann (standardmäßig nur im Batch-Modus), den Inhalt des Angebots mithilfe von Rendering-Funktionen erstellen und das Angebot der vorgeschlagenen Angebote angeben. Eine Platzierung ist eine Schnittstelle zwischen dem Kanal und dem Angebotsmodul.

  >[!IMPORTANT]
  >
  >Eine Platzierung ist nicht das gleiche wie ein Kommunikationskanal, sondern entspricht dem Integrationspunkt im entsprechenden Kanal. So können beispielsweise zwei Angebote auf einer Webseite verschiedenen Platzierungen zugeordnet werden. In diesem Fall weist ein Kanal zwei Platzierungen auf.
  >
  >Die Platzierungen werden zu Beginn eines Projekts festgelegt und können im späteren Verlauf nicht mehr geändert werden.

* **Angebotskatalog**: Gesamtheit aller in Adobe Campaign erstellten Angebote, die bei Interaktionen unterbreitet werden können. Jeder Knoten der hierarchischen Katalogstruktur entspricht einer Angebotskategorie.
* **Kategorie**: Mit einem Angebotskatalog einer Platzierung verknüpfter Ordner, der dazu dient, Angebote nach ihrer Art, ihrer Gültigkeit und ihren Anwendungsthemen zu organisieren. Eine Kategorie kann Unterkategorien enthalten, die alle auf Ebene der übergeordneten Kategorie definierten Eigenschaften übernehmen.
* **Themen**: Auf Ebene der Kategorie festgelegte Stichwörter, die es ermöglichen, Angebote bei ihrer Unterbreitung über einen aus- oder eingehenden Kanal zu filtern. Die Angebotsauswahl kann auf eine oder mehrere Kategorien begrenzt werden.

  >[!NOTE]
  >
  >Untergeordnete Kategorien übernehmen automatisch die Themen, die in der übergeordneten Kategorie definiert wurden.


* **Eignungsregeln**: Regeln, die sicherstellen sollen, dass ein Angebot bestmöglich dem Empfänger entspricht, dem es unterbreitet wird. Sie können sich auf eine Umgebung, eine Angebotskategorie oder ein Angebot beziehen.

  Auf Umgebungsniveau enthalten die Eignungsregeln die Unterbreitungsregeln, die auf Angebote und Zielpersonen angewendet werden.

  Auf Kategorieniveau ermöglichen es die Eignungsregeln, die Gültigkeit von Kategorien zeitlich zu begrenzen sowie Anwendungsthemen und Kriterien der Zielgruppenbestimmung zu definieren. Außerdem kann den Kategorien für einen bestimmten Zeitraum ein erhöhter Gewichtsfaktor zugewiesen werden. Kategorien vereinfachen die Angebotsverwaltung, da die auf diesem Niveau erstellten Regeln automatisch auf alle enthaltenen Angebote angewendet werden.

  Auf Angebotsniveau lassen sich mithilfe der Eignungsregeln die Gültigkeit von Angeboten zeitlich begrenzen sowie Kriterien der Zielgruppenbestimmung definieren.

* **Schlichtung**: Etappe der Angebotsauswahl, bei der die für eine Platzierung geeigneten Angebote nach ihrer auf Kategorie- und Angebotsniveau definierten Gewichtung geordnet werden. Das Angebot mit der höchsten Gewichtung ist demzufolge prioritär bei der Unterbreitung.

* **Kontakt**: Person am Ursprung einer eingehenden Interaktion. Bei einer Abfrage des Angebotsmoduls wird der Kontakt einer Zielgruppendimension zugeordnet. Es werden zwei Kontakttypen unterschieden:

   * **[!UICONTROL Identifizierter Kontakt]**: Kontakt, der sich explizit im Kanal identifiziert hat (z. B. durch Angabe einer Benutzerkennung und eines Kennworts). Bei ausgehenden Interaktionen sind alle Kontakte systematisch identifiziert.
   * **[!UICONTROL Anonymer Kontakt]**: Kontakt, der sich nicht explizit im Kanal identifiziert hat, der jedoch mithilfe eines Cookies implizit identifiziert werden kann. Diese Art von Kontakten tritt nur bei eingehenden Interaktionen auf.

     >[!NOTE]
     >
     >Nicht identifizierbare anonyme Kontakte werden der Zielgruppendimension der Besucher zugeordnet.

* **Ausgehende Interaktion**: Auf einer Kontaktliste (verwendet für den E-Mail-Versand, für Briefpost etc.) basierende Abfrage des Angebotsmoduls. Regeln und Prozesse gelten jeweils für alle Kontakte. Dieser Interaktionstyp wird in der Regel im Batch-Modus verarbeitet.
* **Eingehende Interaktionen**: Interaktion nach einem eingehenden Aufruf, der durch die Aktion eines Kontakts im Kanal generiert wurde. Diese Art von Interaktion wird im Allgemeinen im Einzelmodus verarbeitet.
* Im **Batch-Modus** können Sie das beste Angebot für eine Gruppe von Kontakten auswählen. Eignungs-/Prioritätsregeln werden auf alle Kontakte der Gruppe angewendet. Dieser Modus wird im Allgemeinen für ausgehende Interaktionen verwendet.
* **Einzelmodus**: Zu einem gegebenen Zeitpunkt wird jeweils ein Kontakt verarbeitet. Dieser Modus wird im Allgemeinen für eingehende Interaktionen und Transaktionsnachrichten verwendet.
* **Identifikationsmodus**: bezieht sich auf den Status eines Kontakts:

   * **[!UICONTROL explizit]**: Der Kontakt konnte identifiziert werden, da er sich in der Kanalschnittstelle mit seinen Kundendaten angemeldet hat.
   * **[!UICONTROL implizit]**: Der Kontakt konnte mithilfe eines Cookies (Sitzungs- oder permanenter Cookie) identifiziert werden. Er kann entweder wie ein anonymer oder wie ein identifizierter Kontakt behandelt werden.
   * **[!UICONTROL anonym]**: Der Kontakt konnte nicht identifiziert werden.

* **Geeignetes Angebot**: Angebot, das bestimmten, zuvor definierten Bedingungen entspricht und somit einer Zielgruppe auf mit ihrer Markenerfahrung kohärente Weise unterbreitet werden kann.
* **Unterbreitungsregeln**: Typologieregeln, die auf Basis der einem Kontakt bereits vorgeschlagenen Angebote bestimmte Angebote von der Unterbreitung ausschließen. Die Regeln werden auf Ebene der Umgebung der Angebote verzeichnet.
* **Gewichtung**: Formeln, die die exakte Berechnung der Relevanz eines Angebots für einen Kontakt ermöglichen, sodass aus allen geeigneten Angeboten das beste ausgewählt werden kann. Die Gewichtung wird auf Ebene der Angebote definiert, welche nach absteigender Gewichtung sortiert werden.
* **Rendering-Funktion**: Auf Ebene der Platzierung definierte Funktion, welche die Darstellung eines Angebots ausgehend von auf Angebotsebene definierten Attributen konstruiert. Drei Arten von Rendering-Funktionen stehen zur Verfügung: HTML, XML und Text.
* **Angebotsvorschlag**: Aktion, die darin besteht, einem Empfänger ein oder mehrere Angebote auf einer gegebenen Platzierung zu unterbreiten (beispielsweise auf einem Webseiten-Banner oder in einer E-Mail bzw. SMS). Das Ergebnis der Aktion wird in der Tabelle der Angebotsvorschläge gespeichert. Die Speicherung der Vorschläge selbst ist optional.
* **Simulation**: Modul, das es ermöglicht, die Angebotsunterbreitung vor der tatsächlichen Unterbreitung bei Zielpersonen zu evaluieren.
* **Vorschau**: Anzeige der Darstellung des Angebots in seiner Platzierung. Die Vorschau kann aus dem Konfigurationsfenster des Angebots oder dem Kontaktprofil heraus aufgerufen werden.
* **Vordefinierte Filter**: Zur Wiederverwendung bei der Angebotserstellung bestimmte Filter, die Angebotsparameter (z. B. den Angebotscode) berücksichtigen können.
* **Darstellung eines Angebots**: Informationen, die vom jeweiligen Kanal abgerufen werden, um das Angebot anzuzeigen. Die Darstellung kann mithilfe der Rendering-Funktion einer Platzierung konstruiert oder direkt in der Schnittstelle (z. B. im HTML-Block) erfasst werden. Ein Angebot kann je nach Platzierung unterschiedliche Darstellungen aufweisen.
* **Platzierungswechsel**: Option in einer identifizierten Platzierung, die den Wechsel zu einer anonymen Platzierung auslöst, wenn ein Kontakt weder ex- noch implizit identifiziert werden konnte.
