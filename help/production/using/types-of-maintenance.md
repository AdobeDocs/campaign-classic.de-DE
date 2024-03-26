---
product: campaign
title: Arten der Wartung
description: Arten der Wartung
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
badge-v7-prem: label="On-Premise und Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 5%

---

# Arten der Wartung{#types-of-maintenance}



## Anwendungswartung {#application-maintenance}

Adobe Campaign bietet einen integrierten Workflow, mit dem Sie bestimmte Aufgaben zur Datenbankwartung planen können: die **Datenbankbereinigungs-Workflow**. Dieser Workflow führt die folgenden Aufgaben aus:

* Löschung abgelaufener Datensätze,
* Löschen verwaister Datensätze und Neuinitialisierung des Status für abgelaufene Objekte,
* Aktualisierung der Datenbankstatistiken.

>[!IMPORTANT]
>
>Bitte beachten Sie, dass die Bereinigungsaufgabe hauptsächlich die Wartung auf Anwendungsebene betrifft, nicht aber die Wartung auf RDBMS-Ebene (mit Ausnahme der statistischen Aktualisierung). Für die Datenbank sind jedoch Wartungsarbeiten erforderlich. Selbst wenn der Datenbankbereinigungs-Workflow erfolgreich ausgeführt wird, bedeutet dies nicht, dass die Datenbank optimal angepasst ist.

## Technische Wartung {#technical-maintenance}

Der Datenbankbereinigungs-Workflow enthält kein Werkzeug zur Datenbankwartung: Es liegt bei Ihnen, die Wartung zu organisieren. Dazu haben Sie folgende Möglichkeiten:

* Arbeiten Sie mit Ihrem Datenbankadministrator zusammen, um die Datenbankwartung mit Tools von Drittanbietern einzurichten.
* Verwenden Sie die Adobe Campaign Workflow-Engine, um diese Wartungsaktivitäten zu planen und zu verfolgen.

Diese Instandhaltungsverfahren müssen regelmäßig durchgeführt werden und sollten Folgendes umfassen:

* Neuindizierung häufig aktualisierter Tabellen,
* kompaktieren/erstellen Sie die Tabellen neu, um Fragmentierungen zu vermeiden.

### Wartungsplan {#maintenance-schedule}

Sie müssen die entsprechenden Slots für die Durchführung dieser Wartungsaktivitäten finden. Sie können die Datenbankleistung beim Ausführen stark beeinträchtigen oder die Anwendung sogar blockieren (durch Sperren).

Diese Aufgaben werden in der Regel einmal pro Woche während eines Zeitraums mit geringer Aktivität ausgeführt, der nicht mit Backups, Datenneuladung oder Aggregat-Berechnung kollidiert. Einige Systeme, die dringend angefordert werden, erfordern eine häufigere Wartung.

Detailliertere Wartungsarbeiten, wie vollständige Tabellen-Rebuilds, können einmal im Monat durchgeführt werden, vorzugsweise mit vollständig angehaltenen Anwendungen, da das System ohnehin unbrauchbar ist.

### Tabellen neu erstellen {#rebuilding-a-table}

Es stehen verschiedene Strategien zur Verfügung:

<table> 
 <thead> 
  <tr> 
   <th> Aktivitäten </th> 
   <th> Beschreibung </th> 
   <th> Vorteile </th> 
   <th> Nachteile </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Online-Defragmentierung<br /> </td> 
   <td> Die meisten Datenbank-Engines bieten Defragmentierungsmethoden.<br /> </td> 
   <td> Verwenden Sie einfach die Methode zur Datenbankdefragmentierung. Diese Methoden kümmern sich normalerweise um Integritätsprobleme, indem sie die Daten während der Defragmentierung sperren.<br /> </td> 
   <td> Abhängig von der Datenbank können diese Defragmentierungsmethoden als RDBMS-Option (Oracle) bereitgestellt werden und sind nicht immer die effizienteste Methode zum Umgang mit größeren Tabellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aufheben und Wiederherstellen<br /> </td> 
   <td> Ziehen Sie die Tabelle in eine Datei, löschen Sie die Tabelle in der Datenbank und stellen Sie sie aus der Ablage wieder her.<br /> </td> 
   <td> Auf diese Weise lässt sich eine Tabelle am einfachsten defragmentieren. Auch die einzige Lösung, wenn die Datenbank fast voll ist.<br /> </td> 
   <td> Da die Tabelle gelöscht und neu erstellt wird, kann die Anwendung nicht online gelassen werden, auch nicht im schreibgeschützten Modus (die Tabelle ist während der Wiederherstellungsphase nicht verfügbar).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplizieren, umbenennen und ablegen<br /> </td> 
   <td> Dadurch wird eine Kopie einer Tabelle und ihrer Indizes erstellt, dann wird die vorhandene Tabelle abgelegt und die Kopie wird umbenannt, damit sie ersetzt wird.<br /> </td> 
   <td> Diese Methode ist schneller als der erste Ansatz, da sie weniger I/Os generiert (keine Kopie als Datei und keine Lektüre aus dieser Datei).<br /> </td> 
   <td> Erfordert doppelt so viel Platz.<br /> Alle aktiven Prozesse, die während des Prozesses in die Tabelle geschrieben werden, müssen angehalten werden. Lesevorgänge sind jedoch nicht betroffen, da die Tabelle im letzten Moment nach der Wiederherstellung ausgetauscht wird. <br /> </td> 
  </tr> 
 </tbody> 
</table>
