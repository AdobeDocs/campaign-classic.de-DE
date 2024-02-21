---
product: campaign
title: Laden (SOAP)
description: Laden (SOAP)
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Workflows
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 91%

---

# Laden (SOAP){#loading-soap}



>[!CAUTION]
>
>Die Aktivität **Laden (SOAP)** erfordert die Installation des **FDA**-Moduls (Federated Data Access). Bitte prüfen Sie Ihren Lizenzvertrag.

Im Allgemeinen wird die Aktivität **Laden (SOAP)** ergänzend zur Aktivität **Laden (DBMS)** eingesetzt, für den Fall, dass der direkte Datenabruf aus einer externen Datenbank über den FDA nicht möglich ist.

Gehen Sie wie folgt vor:

1. Wählen Sie zwischen der Verwendung eines Beispiel-XMLs oder einer WSDL.

   Das im Folgenden dargestellte Beispiel stammt aus einem technischen Workflow des Message-Center-Moduls.

   ![](assets/load_soap_002.png)

1. Wählen Sie im Fall des Beispiel-XMLs die gewünschte Beispieldatei aus. Die Datei wird analysiert, um ein Beispielergebnis zu erzeugen.

   Im Falle einer WSDL ist die entsprechende Zugriffs-URL anzugeben und das Code-Skelett zu erzeugen. Der ausgewählte Dienst und der ausgewählte Aufruf werden automatisch aktualisiert und angezeigt.

   ![](assets/soap_load_003.png)

1. Klicken Sie auf den Link **[!UICONTROL Zur Ansicht und Änderung des Analyseergebnisses hier klicken...]**, um die identifizierten Spalten zu definieren.

   ![](assets/soap_load_001.png)

   Durch Klick auf **[!UICONTROL Beispiel erneut analysieren]**, können Sie das Beispiel aktualisieren.

   Sie können das Format der Spaltendaten auch über die **[!UICONTROL Erweiterte Parameter]** -Link. Weiterführende Informationen zur Formatierung importierter Daten finden Sie in diesem Abschnitt [Abschnitt](../../platform/using/executing-import-jobs.md).

1. Als Kennung kann die Zeilennummer verwendet werden und/oder Sie können angeben, dass der SOAP-Aufruf mehrere Elemente zurückgibt.
1. Geben Sie die erforderlichen Scripts in den entsprechenden Tabs ein:

   * **[!UICONTROL Initialisierung]**: Herstellung der SOAP-Verbindung.
   * **[!UICONTROL Iteration]**: Aufruf des SOAP-Dienstes. Zurückgegeben werden muss ein XML-Objekt, dass mit der Beispielbeschreibung oder der WSDL kompatibel ist.

     Der Code dieses Tabs wird von Adobe Campaign so lange in einer Schleife aufgerufen, bis ein Null-XML-Element zurückgegeben wird.

   * **[!UICONTROL Fertigstellung]**: Unterbrechung der Verbindung und/oder Freigabe der anderen, während des Vorgangs erstellten Ressourcen.
