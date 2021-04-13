---
solution: Campaign Classic
product: campaign
title: Exportieren von Daten aus der Kampagne nach Adobe Experience Platform
description: Erfahren Sie, wie Sie Daten aus Campaign Classic nach Adobe Experience Platform exportieren.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 1c07c3b10a6d38ca67c20746a51301d71aec0015
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Exportieren von Daten aus der Kampagne nach Adobe Experience Platform {#sources}

Um Campaign Classic-Daten in die Adobe Echtzeit-Kundendatenplattform (RTCDP) zu exportieren, müssen Sie zunächst einen Workflow in Campaign Classic erstellen, um die Daten, die Sie freigeben möchten, an den Speicherort Ihrer S3- oder Azurblase-Datenspeicherung zu exportieren.

Nachdem der Workflow konfiguriert und Daten an Ihren Speicherort für die Datenspeicherung gesendet wurden, müssen Sie den Speicherort der S3- oder Azurblase-Datenspeicherung als **Quelle** in der Erlebnisplattform für Adoben verbinden.

>[!NOTE]
>
>Bitte beachten Sie, dass wir nur den Export von durch Kampagnen erzeugten Daten empfehlen (z.B. Senden, Öffnen, Klicks usw.) nach Adobe Experience Platform. Daten, die aus einer Drittanbieter-Quelle (wie Ihrem CRM-System) erfasst werden, sollten direkt in Adobe Experience Platform importiert werden.

## Erstellen eines Exportarbeitsablaufs in Campaign Classic

Um Daten aus Campaign Classic an den Speicherort der S3- oder Azurblase-Datenspeicherung zu exportieren, müssen Sie einen Workflow erstellen, um die zu exportierenden Daten Zielgruppe und an den Speicherort Ihrer Datenspeicherung zu senden.

Fügen Sie dazu Folgendes hinzu und konfigurieren Sie:

* Eine **[!UICONTROL Datendatei (Extraktion)]**-Aktivität, um die Zieldaten in eine CSV-Datei zu extrahieren. Weitere Informationen zum Konfigurieren dieser Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/extraction--file-.md).

   ![](assets/rtcdp-extract-file.png)

* Eine **[!UICONTROL Dateiübertragung]**-Aktivität, um die CSV-Datei an Ihren Speicherort in der Datenspeicherung zu übertragen. Weitere Informationen zum Konfigurieren dieser Aktivität finden Sie in [diesem Abschnitt](../../workflow/using/file-transfer.md).

   ![](assets/rtcdp-file-transfer.png)

Beispielsweise extrahiert der unten stehende Arbeitsablauf Protokolle regelmäßig in eine CSV-Datei und überträgt die Datei dann an einen Speicherort für die Datenspeicherung.

![](assets/aep-export.png)

## Datenspeicherung als Quelle verbinden

Die Hauptschritte zum Verbinden des Speicherorts für die S3- oder Azurblase-Datenspeicherung als **Source** in der Erlebnisplattform für Adoben sind unten aufgeführt. Ausführliche Informationen zu jedem dieser Schritte finden Sie in der [Dokumentation zu Quell-Connectors](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html).

1. Erstellen Sie in Adobe Experience Platform **[!UICONTROL Sources]** eine Verbindung zu Ihrem Speicherort für die Datenspeicherung:

   * [Erstellen einer Amazon S3-Quellverbindung](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Azurblutstecker](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >Der Speicherort für die Datenspeicherung kann Amazon S3, SFTP mit Kennwort, SFTP mit SSH-Schlüssel oder Blue Blob-Verbindungen sein. Die bevorzugte Methode zum Senden von Daten an Adobe Campaign ist Amazon S3 oder Azurblut:

   ![](assets/rtcdp-connector.png)

1. Konfigurieren eines Datenflusses für eine Cloud-Datenspeicherung-Stapelverbindung. Ein Datennachweis ist eine geplante Aufgabe, mit der Daten vom Speicherort der Datenspeicherung zu einem Adobe Experience Platform-Datensatz abgerufen und abgerufen werden. Auf diese Weise können Sie die Datenerfassung von Ihrem Speicherort an der Datenspeicherung konfigurieren, einschließlich der Datenauswahl und der Zuordnung der CSV-Felder zu einem XDM-Schema.

   Ausführliche Informationen finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html).

   ![](assets/rtcdp-map-xdm.png)

1. Nachdem die Quelldatei konfiguriert wurde, importiert Adobe Experience Platform die Datenspeicherung aus dem von Ihnen angegebenen Speicherort.

   Dieser Vorgang kann je nach Bedarf geplant werden. Es wird empfohlen, den Export bis zu 6 Mal am Tag durchzuführen, je nach der bereits vorhandenen Belastung in der Instanz.
