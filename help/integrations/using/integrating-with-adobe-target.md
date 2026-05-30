---
product: campaign
title: Verwenden von Adobe Campaign und Adobe Target
description: Hier erfahren Sie, wie Sie Adobe Campaign mit Adobe Target integrieren
feature: Target Integration
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
TQID: https://experienceleague.adobe.com/f58vs0ePAH-7bcfJ8u1GKLzcz0-fHnrwFyOVUWOFW-o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 209
ht-degree: 96%

---

# Verwenden von Campaign und Target{#integrating-with-adobe-target}



Verwenden Sie Adobe Campaign mit Adobe Target zur Optimierung des E-Mail-Inhalts.

Um Ihren E-Mail-Inhalt zu optimieren, können Sie ein Umleitungsangebot in Adobe Target erstellen und dann die E-Mail-Angebote mit Adobe Campaign verwalten. Beispielsweise können Sie für männliche und weibliche Empfänger unterschiedliche Angebote anzeigen.

Die Integration erfolgt beim Öffnen der E-Mail. Wenn der Kunde die E-Mail öffnet, wird Target aufgerufen und eine dynamische Version des Inhalts wird angezeigt. Der Inhalt besteht aus einem statischen Bild, das von allen Browsern unterstützt wird. Target verfolgt die Reaktion auf das Angebot auf Zielgruppen- oder Sitzungsebene und stellt fest, dass Daten in Target-Berichten verfügbar sind. [Weitere Informationen finden Sie in der Dokumentation zu Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=de).


>[!NOTE]
>
>Im Rahmen der Integration werden nur statische Bilder unterstützt. Der Rest des Inhalts kann nicht personalisiert werden.

Verschiedene Datentypen können in Verbindung mit Adobe Target zum Einsatz kommen:

* Daten aus dem Adobe Campaign-Datamart;
* Segmente im Zusammenhang mit der Visitor ID in Adobe Target, wenn die verwendeten Daten keinen rechtlichen Beschränkungen unterliegen;
* Daten aus Adobe Target (Benutzera, IP-Adresse, Daten zur Geolokalisierung).
