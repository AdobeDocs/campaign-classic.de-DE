---
solution: Campaign Classic
product: campaign
title: Über den Versand von Transaktionsnachrichten
description: 'Senden Sie Auslösernachrichten basierend auf Ereignissen, die von Informationssystemen generiert werden. '
audience: message-center
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%

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
>Um neue Benutzer für in Adobe Cloud gehostete Message-Center-Ausführungsinstanzen zu erstellen, kontaktieren Sie die Adobe-Kundenunterstützung. Message-Center-Benutzer benötigen für den Zugriff auf die Ordner &#39;Echtzeit-Ereignisse&#39; (nmsRtEvent) spezifische Berechtigungen.
