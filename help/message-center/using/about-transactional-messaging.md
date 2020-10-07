---
title: Über den Versand von Transaktionsnachrichten
description: 'Senden Sie Auslösermeldungen basierend auf Ereignissen, die aus Informationssystemen generiert wurden. '
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 93%

---


# Über den Versand von Transaktionsnachrichten{#about-transactional-messaging}

Transaktionsnachricht (Message Center) ist ein Campaign-Modul, das die Nachrichtenauslösung handhabt. Diese Nachrichten werden durch Ereignisse erzeugt, die von Informationssystemen ausgelöst werden. Hierzu zählen u. a.: Rechnungen, Bestellbestätigungen, Lieferbestätigungen, Passwortänderungen, Benachrichtigungen über die Nicht-Verfügbarkeit eines Produkts, Kontostandsinformationen oder die Erstellung eines Website-Kontos.

>[!IMPORTANT]
>
>Für Transaktionsnachrichten ist eine spezifische Lizenz erforderlich. Prüfen Sie diesbezüglich Ihren Lizenzvertrag.

Das Adobe Campaign Message Center ist in ein Informationssystem integriert, das Ereignisse zurückgibt, die wiederum in personalisierte Transaktionsnachrichten transformiert werden. Diese Nachrichten können einzeln oder gebündelt per E-Mail, SMS oder Push-Benachrichtigungen gesendet werden.

In der hier angewendeten Architektur sind Ausführungsinstanz und Kontrollinstanz voneinander getrennt, was höhere Verfügbarkeit und besseres Lastmanagement gewährleistet.

>[!NOTE]
>
>Um neue Benutzer für in Adobe Cloud gehostete Message-Center-Ausführungsinstanzen zu erstellen, kontaktieren Sie den Adobe-Kundenservice. Message-Center-Benutzer benötigen für den Zugriff auf die Ordner &#39;Echtzeit-Ereignisse&#39; (nmsRtEvent) spezifische Berechtigungen.
