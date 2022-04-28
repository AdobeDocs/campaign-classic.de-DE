---
product: campaign
title: Technote - Adobe Campaign - Aktualisierung der Apache-Versionssicherheit
description: Adobe Campaign - Aktualisierung der Apache-Versionssicherheit
hide: true
hidefromtoc: true
source-git-commit: 086d03cf0ceb5c2db7ded0c2bedb1b0514257d8a
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 6%

---

# Adobe Campaign - Aktualisierung der Apache-Versionssicherheit {#apache-update}

Campaign Classic arbeitet mit Tools von Drittanbietern. Die Kompatibilität wird regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren und von den neuesten Fehlerbehebungen und Verbesserungen zu profitieren.

Adobe Campaign enthält Apache Tomcat, der über HTTP als Einstiegspunkt im Anwendungsserver fungiert und mit dem Apache-Webserver integriert ist. Die Apache Software Foundation hat Apache HTTP Server 2.4.53 veröffentlicht. Diese Version behebt Schwachstellen — CVE-2021-44790 und CVE-2021-44224 — von denen einer einem entfernten Angreifer die Möglichkeit geben kann, die Kontrolle über ein betroffenes System zu übernehmen. Weitere Informationen finden Sie unter [Apache 2.4.53 - Ankündigung](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Das Adobe Campaign-Team führt die Sicherheitsaktualisierung der Apache-Version durch **31. Mai 2022** um diese Apache-Schwachstelle zu beheben und Ihre Instanzumgebung sicherer zu machen. Dieses Upgrade gilt für alle Managed Services-Kunden, die eine verwundbare Version des Apache HHTP-Servers verwenden. Wenn Sie betroffen sind, hat sich Adobe bereits mit Ihnen in Verbindung gesetzt, um Sie über dieses Upgrade zu informieren.

Es wird erwartet, dass dieses Upgrade außerhalb Ihrer normalen Geschäftszeiten automatisch ausgeführt wird, damit Sie den Campaign-Dienst ohne Unterbrechung weiter verwenden können.

Ihre Nicht-Produktionsinstanz(en) werden von unseren Teams zuerst aktualisiert, bevor wir Ihre Produktionsinstanz(en) aktualisieren. Da es sich um einen Prozess der automatischen Aktualisierung handelt, ist von Ihrer Seite aus keine Aktion erforderlich. Sollten dennoch Probleme auftreten, wenden Sie sich an [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).

Da das Upgrade den Apache neu starten muss, wird die Ausfallzeit innerhalb des unten genannten Zeitfensters voraussichtlich 10 Minuten nicht überschreiten.

## Häufig gestellte Fragen {#apache-faq}

* **Warum ist dies ein obligatorisches Upgrade?**

   Die aktuelle Apache-Version ist anfällig und hat eine potenzielle Sicherheitsbedrohung. Es ist wichtig, dass Ihre Campaign-Instanz(en) auf die neueste anwendbare Apache-Version aktualisiert wird, um das Sicherheitsrisiko zu beheben.


* **Welche Kunden sind für Sicherheitsaktualisierungen vorgesehen?**

   Alle Kunden, deren Campaign-Umgebungen in älteren Apache-Versionen implementiert sind, werden auf die neueste anwendbare Apache-Version aktualisiert.

* **Wie hoch ist die erwartete Ausfallzeit?**

   Die erwartete Ausfallzeit liegt unter 10 Minuten.


* **Gibt es Maßnahmen, die der Kunde für dieses Sicherheitsupdate benötigt?**

   Es sind keine Aktionen erforderlich, da das Sicherheits-Upgrade automatisch ausgeführt wird.


* **Welche Validierungen müssen von den Kunden ausgeführt werden?**

   Für dieses Sicherheitsupdate sind keine spezifischen Tests erforderlich. Falls ein Problem beobachtet wird, wenden Sie sich bitte an [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Kann ich eine Änderung des Datums-/Uhrzeitwerts für den geplanten Zeitfenster für die Aktualisierung der Sicherheit anfordern?**

   Da es sich um eine Sicherheitskorrektur handelt, empfehlen wir dringend, sich an den vorhandenen Zeitplan anzupassen.


Für alle anderen Fragen wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).
