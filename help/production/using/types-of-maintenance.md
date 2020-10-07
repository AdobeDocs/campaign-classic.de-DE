---
title: Arten der Pflege
seo-title: Arten der Pflege
description: Arten der Pflege
seo-description: null
page-status-flag: never-activated
uuid: 44faee3d-0549-4f63-8fdc-b24e6de47bc4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 4a436ccf-097c-43e6-9eda-492bada5512a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---


# Arten der Pflege{#types-of-maintenance}

## Anwendungswartung {#application-maintenance}

Adobe Campaign bietet einen integrierten Arbeitsablauf, mit dem Sie bestimmte Aufgaben der Datenbankwartung planen können: den **Datenbankbereinigungs-Workflow**. Dieser Arbeitsablauf führt die folgenden Aufgaben aus:

* Löschung abgelaufener Datensätze,
* Löschung verwaister Datensätze und Statusreinitialisierung für abgelaufene Objekte,
* Aktualisierung der Datenbankstatistiken.

>[!CAUTION]
>
>Bitte beachten Sie, dass die Bereinigungs-Aufgabe hauptsächlich die Pflege auf Anwendungsebene und nicht die Wartung auf RDBMS-Ebene (mit Ausnahme der statistischen Aktualisierung) betrifft. Für die Datenbank sind jedoch Wartungsarbeiten erforderlich. Auch wenn der Arbeitsablauf für die Datenbankbereinigung erfolgreich ausgeführt wird, bedeutet dies nicht, dass die Datenbank optimal eingestellt ist.

## Technische Wartung {#technical-maintenance}

Der Arbeitsablauf für die Datenbankbereinigung enthält kein Datenbankwartungswerkzeug: Es liegt an Ihnen, die Wartung zu organisieren. Dazu haben Sie folgende Möglichkeiten:

* mit Ihrem Datenbankadministrator zusammenzuarbeiten, um die Datenbankwartung mit Werkzeugen von Drittanbietern einzurichten,
* Verwenden Sie das Adobe Campaign-Workflow-Engine, um diese Aktivitäten zu planen und nachzuverfolgen.

Diese Instandhaltungsverfahren müssen regelmäßig durchgeführt werden und Folgendes umfassen:

* häufig aktualisierte Tabellen erneut indizieren,
* kompakt/erstellen Sie die Tabellen neu, um eine Fragmentierung zu vermeiden.

### Wartungsplan {#maintenance-schedule}

Sie müssen die entsprechenden Slots für die Durchführung dieser Aktivitäten finden. Sie können die Datenbankleistung beim Ausführen stark beeinträchtigen oder die Anwendung sogar blockieren (durch Sperren).

Diese Aufgaben werden in der Regel einmal pro Woche während einer Phase niedriger Aktivität ausgeführt, die nicht mit Backups, dem erneuten Laden von Daten oder der Berechnung von Aggregaten kollidiert. Einige Systeme, die in hohem Maße angefordert werden, erfordern eine häufigere Wartung.

Detailliertere Wartungsarbeiten, wie z. B. vollständige Tabellenneuaufbauungen, können einmal im Monat durchgeführt werden, vorzugsweise mit vollständig beendeten Anwendungen, da das System ohnehin unbrauchbar ist.

### Erstellen einer Tabelle {#rebuilding-a-table}

Es stehen verschiedene Strategien zur Verfügung:

<table> 
 <thead> 
  <tr> 
   <th> Aktivitäten </th> 
   <th> Beschreibung  </th> 
   <th> Vorteile </th> 
   <th> Rückflüsse </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Online-Defragmentierung<br /> </td> 
   <td> Die meisten Datenbankmaschinen bieten Defragmentierungsmethoden.<br /> </td> 
   <td> Verwenden Sie einfach die Datenbankdefragmentierungsmethode. Diese Methoden kümmern sich in der Regel um Integritätsprobleme, indem sie die Daten während der Defragmentierung sperren.<br /> </td> 
   <td> Abhängig von der Datenbank können diese Defragmentierungsmethoden als RDBMS-Option (Oracle) bereitgestellt werden und sind nicht immer die effizienteste Art, mit größeren Tabellen umzugehen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Berühren und Wiederherstellen<br /> </td> 
   <td> Ziehen Sie die Tabelle in eine Datei, löschen Sie die Tabelle in der Datenbank und stellen Sie sie wieder aus der Deponie her.<br /> </td> 
   <td> Auf diese Weise lässt sich eine Tabelle am einfachsten defragmentieren. Auch die einzige Lösung, wenn die Datenbank fast voll ist.<br /> </td> 
   <td> Da die Tabelle gelöscht und neu erstellt wird, kann die Anwendung nicht online gelassen werden, auch nicht im schreibgeschützten Modus (die Tabelle ist während der Wiederherstellungsphase nicht verfügbar).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplikat, umbenennen und ablegen<br /> </td> 
   <td> Dadurch wird eine Kopie einer Tabelle und ihrer Indizes erstellt, dann wird die vorhandene Tabelle gelöscht und die Kopie wird umbenannt, um sie zu ersetzen.<br /> </td> 
   <td> Diese Methode ist schneller als der erste Ansatz, da sie weniger IOs generiert (keine Kopie als Datei und Lesen aus dieser Datei).<br /> </td> 
   <td> Erfordert doppelt so viel Platz.<br /> Alle aktiven Prozesse, die während des Prozesses in die Tabelle geschrieben werden, müssen beendet werden. Leseprozesse sind jedoch nicht betroffen, da die Tabelle im letzten Moment nach der Wiederherstellung ausgetauscht wird. <br /> </td> 
  </tr> 
 </tbody> 
</table>

