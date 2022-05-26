---
product: campaign
title: Technote – Adobe Campaign – Apache-Sicherheits-Update
description: Adobe Campaign – Sicherheits-Update der Apache-Version
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: a3eae4e253f66f5a651ffe0458f60b1f8bdf2258
workflow-type: ht
source-wordcount: '541'
ht-degree: 100%

---

# Adobe Campaign – Sicherheits-Update der Apache-Version {#apache-update}

>[!CAUTION]
>Dieser Artikel gilt für Kunden von **Campaign Classic v7 Managed Services**, **Campaign v8** und **Campaign Standard**.

Adobe Campaign arbeitet mit Tools von Drittanbietern zusammen. Diese Kompatibilität wird regelmäßig aktualisiert, damit Sie nur unterstützte Versionen implementieren und von den neuesten Korrekturen und Verbesserungen profitieren können.

Adobe Campaign nutzt Apache Tomcat, das über HTTP als Einstiegspunkt im Programm-Server fungiert und mit dem Apache-Webserver integriert ist. Die Apache Software Foundation hat Apache HTTP Server 2.4.53 veröffentlicht. Diese Version behebt Schwachstellen, die es einem Angreifer ermöglichen könnte, die Kontrolle über ein System zu übernehmen. Weitere Informationen finden Sie unter [Apache 2.4.53 – Ankündigung](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Das Adobe Campaign-Team wird bis zum **15. Juni 2022** ein Sicherheits-Upgrade der Apache-Version durchführen, um diese Apache-Sicherheitslücke zu schließen und Ihre Instanzumgebung sicherer zu machen. Dieses Upgrade gilt für alle Kunden von Campaign Classic v7 Managed Services, Campaign v8 und Campaign Standard, die mit einer anfälligen Version von Apache HTTP Server arbeiten. Falls Sie betroffen sind, hat sich Adobe bereits mit Ihnen in Verbindung gesetzt, um Sie über dieses Upgrade zu informieren.

Dieses Upgrade wird voraussichtlich außerhalb Ihrer normalen Geschäftszeiten automatisch ausgeführt, damit Sie den Campaign-Service ohne Unterbrechung weiter verwenden können.

Zuerst werden Ihre Nicht-Produktionsinstanzen von Adobe aktualisiert, danach werden Ihre Produktionsinstanzen aktualisiert. Da es sich um einen automatischen Aktualisierungsprozess durch Adobe handelt, ist von Ihrer Seite aus keine Aktion erforderlich. Sollten dennoch Probleme auftreten, wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Für dieses Upgrade ist ein Neustart des Apache-Webservers erforderlich. Die Ausfallzeit beträgt innerhalb des unten genannten Zeitfensters maximal 10 Minuten.

## Häufig gestellte Fragen {#apache-faq}

* **Warum ist dieses Upgrade obligatorisch?**

   Die aktuelle Apache-Version hat eine Schwachstelle und ist eine potenzielle Sicherheitsbedrohung. Ihre Campaign-Instanzen müssen auf die neueste Apache-Version aktualisiert werden, um dieses Sicherheitsrisiko zu beheben.

* **Welche Kunden erhalten diese Sicherheits-Updates?**

   Alle Kunden, die Campaign-Umgebungen verwenden, die in älteren Apache-Versionen implementiert sind, erhalten ein Upgrade auf die neueste Apache-Version.

* **Mit welcher Ausfallzeit ist zu rechnen?**

   Die erwartete Ausfallzeit liegt bei maximal 10 Minuten.

* **Gibt es Maßnahmen, die der Kunde für dieses Sicherheits-Update treffen muss?**

   Es sind keine Aktionen erforderlich, da das Sicherheits-Upgrade automatisch ausgeführt wird.

* **Welche Auswirkungen hat das Wartungsfenster auf die laufenden Kampagnen/Workflows?**

   Während des Wartungsfensters werden der Workflow und die E-Mail-Services angehalten und die geplanten Aktivitäten werden nicht ausgeführt. Alle laufenden Aktivitäten oder Prozesse werden während der Ausfallzeit angehalten, bis der Server neu gestartet wird. Nachdem die Aktivität abgeschlossen und der Server neu gestartet wurde, werden alle Services fortgesetzt.

* **Welche Validierungen müssen von den Kunden ausgeführt werden?**

   Für dieses Sicherheits-Update sind keine spezifischen Tests erforderlich. Falls ein Problem festgestellt wird, wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **Kann ich eine Änderung des geplanten Zeitfensters für das Sicherheits-Update anfordern?**

   Da es sich um die Behebung einer Schwachstelle handelt, empfehlen wir dringend, sich an den vorgegebenen Zeitplan zu halten.


Für alle anderen Fragen wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).
