---
solution: Campaign Classic
product: campaign
title: Über den Versand von Transaktionsnachrichten
description: 'Senden Sie Auslösernachrichten basierend auf Ereignissen, die von Informationssystemen generiert werden. '
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
translation-type: ht
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: ht
source-wordcount: '171'
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
>Um neue Benutzer für in Adobe Cloud gehostete Message-Center-Ausführungsinstanzen zu erstellen, kontaktieren Sie die [Adobe-Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Message-Center-Benutzer benötigen für den Zugriff auf die Ordner &quot;Echtzeit-Ereignisse&quot; (nmsRtEvent) spezifische Berechtigungen.
