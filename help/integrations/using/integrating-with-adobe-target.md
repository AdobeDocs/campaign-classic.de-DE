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
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '201'
ht-degree: 100%

---

# Verwenden von Campaign und Target{#integrating-with-adobe-target}



Verwenden Sie Adobe Campaign mit Adobe Target zur Optimierung des E-Mail-Inhalts.

Um Ihren E-Mail-Inhalt zu optimieren, können Sie ein Umleitungsangebot in Adobe Target erstellen und dann die E-Mail-Angebote mit Adobe Campaign verwalten. Beispielsweise können Sie für männliche und weibliche Empfänger unterschiedliche Angebote anzeigen.

Die Integration erfolgt beim Öffnen der E-Mail. Wenn der Kunde die E-Mail öffnet, wird Target aufgerufen und eine dynamische Version des Inhalts wird angezeigt. Der Inhalt besteht aus einem statischen Bild, das von allen Browsern unterstützt wird. Target verfolgt die Reaktion auf das Angebot auf Audience- oder Sitzungsebene und stellt fest, dass Daten in Target-Berichten verfügbar sind. [Weitere Informationen finden Sie in der Dokumentation zu Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=de).


>[!NOTE]
>
>Im Rahmen der Integration werden nur statische Bilder unterstützt. Der weitere Inhalt kann nicht personalisiert werden.

Verschiedene Datentypen können in Verbindung mit Adobe Target zum Einsatz kommen:

* Daten aus dem Adobe Campaign-Datamart;
* Segmente im Zusammenhang mit der Visitor ID in Adobe Target, wenn die verwendeten Daten keinen rechtlichen Beschränkungen unterliegen;
* Daten aus Adobe Target (Benutzera, IP-Adresse, Daten zur Geolokalisierung).
