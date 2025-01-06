---
product: campaign
title: Arten der Wartung
description: Arten der Wartung
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 4%

---

# Arten der Wartung{#types-of-maintenance}



## Anwendungswartung {#application-maintenance}

Adobe Campaign bietet einen integrierten Workflow, mit dem Sie bestimmte Datenbankwartungsaufgaben planen können: den **Datenbankbereinigungs-Workflow**. Dieser Workflow führt die folgenden Aufgaben aus:

* Löschen abgelaufener Datensätze,
* Löschen verwaister Datensätze und Statusneuinitialisierung für abgelaufene Objekte,
* Datenbankstatistiken werden aktualisiert.

>[!IMPORTANT]
>
>Bitte beachten Sie, dass sich die Bereinigungsaufgabe hauptsächlich mit der Wartung auf Anwendungsebene befasst, nicht mit der Wartung auf RDBMS-Ebene (mit Ausnahme der Statistikaktualisierung). Für die Datenbank sind jedoch Wartungsarbeiten erforderlich. Selbst wenn der Datenbankbereinigungs-Workflow erfolgreich ausgeführt wird, bedeutet dies nicht, dass die Datenbank optimal abgestimmt ist.

## Technische Wartung {#technical-maintenance}

Der Datenbankbereinigungs-Workflow enthält kein Datenbankwartungs-Tool: Sie müssen die Wartung organisieren. Dazu haben Sie folgende Möglichkeiten:

* Arbeiten Sie mit Ihrem Datenbankadministrator zusammen, um die Datenbankwartung mit Tools von Drittanbietern einzurichten.
* Verwenden Sie die Workflow-Engine von Adobe Campaign, um diese Wartungsaktivitäten zu planen und zu verfolgen.

Diese Instandhaltungsverfahren müssen regelmäßig durchgeführt werden und sollten Folgendes umfassen:

* häufig aktualisierte Tabellen neu indizieren,
* Komprimieren/erstellen Sie die Tabellen neu, um eine Fragmentierung zu vermeiden.

### Wartungsplan {#maintenance-schedule}

Sie müssen die entsprechenden Slots für diese Wartungsaktivitäten finden. Sie können die Datenbankleistung während der Ausführung erheblich beeinträchtigen oder sogar die Anwendung blockieren (aufgrund von Sperren).

Diese Aufgaben werden in der Regel einmal wöchentlich während eines Zeitraums mit geringer Aktivität ausgeführt, der nicht mit Backups, dem erneuten Laden von Daten oder der Berechnung von Aggregaten kollidiert. Einige Systeme, für die sehr häufig eine Wartung durchgeführt wird, müssen häufiger gewartet werden.

Detailliertere Wartungsarbeiten, wie z. B. vollständige Tabellenumbauten, können einmal monatlich durchgeführt werden, vorzugsweise mit vollständig gestoppten Anwendungen, da das System ohnehin nicht verwendbar ist.

### Tabelle neu erstellen {#rebuilding-a-table}

Es stehen verschiedene Strategien zur Verfügung:

<table> 
 <thead> 
  <tr> 
   <th> Vorgänge </th> 
   <th> Beschreibung </th> 
   <th> Vorteile </th> 
   <th> Nachteile </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Online-<br /> </td> 
   <td> Die meisten Datenbank-Engines bieten Defragmentierungsmethoden.<br /> </td> 
   <td> Verwenden Sie einfach die Methode der Datenbankdefragmentierung. Diese Methoden beheben in der Regel Integritätsprobleme, indem sie die Daten während der Defragmentierung sperren.<br /> </td> 
   <td> Abhängig von der Datenbank können diese Defragmentierungsmethoden als RDBMS-Option (Oracle) bereitgestellt werden und sind nicht immer die effizienteste Methode für den Umgang mit größeren Tabellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dump und Wiederherstellung<br /> </td> 
   <td> Dump der Tabelle in eine Datei, Löschen der Tabelle in der Datenbank und Wiederherstellen aus dem Dump.<br /> </td> 
   <td> Dies ist die einfachste Möglichkeit, eine Tabelle zu defragmentieren. Auch die einzige Lösung, wenn die Datenbank fast voll ist.<br /> </td> 
   <td> Da die Tabelle gelöscht und neu erstellt wird, kann die Anwendung auch im schreibgeschützten Modus nicht online gelassen werden (die Tabelle ist während der Wiederherstellungsphase nicht verfügbar).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplizieren, umbenennen und ablegen<br /> </td> 
   <td> Dadurch wird eine Kopie einer Tabelle und ihrer Indizes erstellt, die vorhandene Tabelle wird dann gelöscht und die Kopie wird umbenannt, um sie zu ersetzen.<br /> </td> 
   <td> Diese Methode ist schneller als der erste Ansatz, da sie weniger IOs generiert (keine Kopie als Datei und aus dieser Datei gelesen).<br /> </td> 
   <td> benötigt doppelt so viel Platz.<br /> Alle aktiven Prozesse, die während des Vorgangs in die Tabelle schreiben, müssen angehalten werden. Lesevorgänge sind jedoch davon nicht betroffen, da die Tabelle im letzten Moment nach dem Umbau ausgetauscht wird. <br /> </td> 
  </tr> 
 </tbody> 
</table>
