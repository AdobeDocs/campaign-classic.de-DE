---
product: campaign
title: Technote – Adobe Campaign – Apache-Sicherheits-Update
description: Adobe Campaign – Sicherheits-Update der Apache-Version
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 854278e3e2013293888ea194c12ec1a75e70d981
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 84%

---

# Adobe Campaign – Sicherheits-Update der Apache-Version {#apache-update}

>[!NOTE]
>Dieser Artikel gilt für:
> * Campaign Classic v7 Managed Services-Kunden
> * Campaign v8-Kunden
> * Campaign Standard



Adobe Campaign arbeitet mit Tools von Drittanbietern. Die Kompatibilität wird regelmäßig aktualisiert, um nur unterstützte Versionen zu implementieren und von den neuesten Fehlerbehebungen und Verbesserungen zu profitieren.

Adobe Campaign nutzt Apache Tomcat, das über HTTP als Einstiegspunkt im Programm-Server fungiert und mit dem Apache-Webserver integriert ist. Die Apache Software Foundation hat Apache HTTP Server 2.4.53 veröffentlicht. Diese Version behebt Schwachstellen, die es einem Angreifer ermöglichen könnte, die Kontrolle über ein System zu übernehmen. Weitere Informationen finden Sie unter [Apache 2.4.53 – Ankündigung](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Das Adobe Campaign-Team führt das Sicherheits-Update der Apache-Version bis spätestens **31. Mai 2022** durch, um diese Apache-Schwachstelle zu beheben und für Sicherheit in Ihrer Instanzumgebung zu sorgen. Dieses Upgrade gilt für alle Campaign Classic v7 Managed Services-Kunden, Campaign v8- und Campaign Standard-Kunden, die eine verwundbare Version von Apache HTTP Server verwenden. Falls Sie betroffen sind, hat sich Adobe bereits mit Ihnen in Verbindung gesetzt, um Sie über dieses Upgrade zu informieren.

Dieses Upgrade wird voraussichtlich außerhalb Ihrer normalen Geschäftszeiten automatisch ausgeführt, damit Sie den Campaign-Service ohne Unterbrechung weiter verwenden können.

Vor der Aktualisierung Ihrer Produktionsinstanzen werden Ihre Nicht-Produktionsinstanzen von unseren Teams aktualisiert. Da es sich um einen automatischen Aktualisierungsprozess durch Adobe handelt, ist von Ihrer Seite aus keine Aktion erforderlich. Sollten dennoch Probleme auftreten, wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).


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

* **Welche Validierungen müssen von den Kunden ausgeführt werden?**

   Für dieses Sicherheits-Update sind keine spezifischen Tests erforderlich. Falls ein Problem festgestellt wird, wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Kann ich eine Änderung des geplanten Zeitfensters für das Sicherheits-Update anfordern?**

   Da es sich um die Behebung einer Schwachstelle handelt, empfehlen wir dringend, sich an den vorgegebenen Zeitplan zu halten.


Für alle anderen Fragen wenden Sie sich bitte an die [Adobe-Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=Campaign#support).
