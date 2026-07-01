---
product: campaign
title: Campaign Response Manager konfigurieren
description: Erfahren Sie, wie Sie Campaign Response Manager konfigurieren
feature: Campaigns
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
TQID: https://experienceleague.adobe.com/P89PBe23uuRmGX5vb6lCNd8kTd24peaZcKsTRAj2pnw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2: id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3id: cfc95e9b-b035-4403-a6a9-b27a8a053a37id: d72afaa0-c842-48c8-9a3c-51b7911edc1b
topic_v2: id: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: ht
source-wordcount: 796
ht-degree: 100%

---

# Campaign Response Manager konfigurieren{#configuration}



Dieser Abschnitt richtet sich an Personen, die für die Konfiguration der Reaktionsverwaltung zuständig sind. Er setzt ein gewisses Maß an Wissen über die Erweiterung von Schemata, die Definition von Workflows und die SQL-Programmierung voraus.

Er erläutert, wie das Standard-Datenmodell an die Besonderheiten einer Transaktionstabelle außerhalb von Adobe Campaign mit der Tabelle der Personen angepasst wird. Diese Tabelle der Personen kann mit der Tabelle der Personen in Adobe Campaign oder mit einer anderen Tabelle übereinstimmen.

Die Messhypothese wird durch den Vorgangsprozess-Workflow ( **[!UICONTROL operationMgt]** ) gestartet. Jede Hypothese stellt einen separaten Prozess dar, der asynchron mit einem Ausführungsstatus ausgeführt wird (In Bearbeitung, Ausstehend, Beendet, Fehlgeschlagen usw.), und wird von einer Planung gesteuert, die Prioritätsbeschränkungen, die Begrenzung der Anzahl gleichzeitiger Prozesse, die Seite mit geringer Aktivität und die automatische Ausführung mit Häufigkeit verwaltet.

## Schemata konfigurieren {#configuring-schemas}

>[!CAUTION]
>
>Ändern Sie nicht die integrierten Schemata der Anwendung, sondern verwenden Sie den Schemaerweiterungs-Mechanismus. Andernfalls werden geänderte Schemata bei zukünftigen Aktualisierungen der Anwendung nicht aktualisiert. Dies kann bei der Verwendung von Adobe Campaign zu Funktionsstörungen führen.

Vor dem Einsatz des Reaktionsmoduls ist eine Anwendungsintegration erforderlich, um die verschiedenen zu messenden Tabellen (Transaktionen, Transaktionendetails) und ihre Beziehung mit Sendungen, Angeboten und Individuen zu definieren.

### Standardschemata {#standard-schemas}

Das vorkonfigurierte **[!UICONTROL nms:remaMatch]**-Schema enthält die Tabelle der Reaktionsprotokolle, d. h. die Beziehung zwischen Personen, Hypothese und Transaktionstabelle. Dieses Schema wird als Vererbungsschema für die endgültige Zieltabelle der Reaktionsprotokolle verwendet.

Das **[!UICONTROL nms:remaMatchRcp]**-Schema wird standardmäßig bereitgestellt und enthält den Speicher für Reaktionsprotokolle für Adobe Campaign-Empfangende (**[!UICONTROL nms:recipient]**). Damit er verwendet werden kann, muss es erweitert und einer Transaktionstabelle (mit Käufen usw.) zugeordnet werden.

### Transaktionstabellen und -details {#transaction-tables-and-transaction-details}

Die Transaktionstabelle muss über eine direkte Relation mit den Individuen verfügen.

Sie können auch eine Tabelle mit Transaktionsdetails hinzufügen. Diese ist nicht direkt mit Einzelpersonen verknüpft.

Im Fall eines Belegs zum Beispiel ist eine Transaktionstabelle mit dem Kontakt verknüpft (Belegtabelle) und eine zweite Tabelle (Detailtabelle), die die Belegzeilen enthält, ist nur mit der Belegtabelle verknüpft. So können Sie die Hypothese direkt auf der Ebene konfigurieren, auf der die Belegzeilentabelle mit der Belegtabelle verknüpft ist.

>[!NOTE]
>
>Wenn Sie die Belegkennung beibehalten möchten, die das erwartete Verhalten in den Hypothesen beschreibt, können Sie die Tabellenvorlage „nms:remaMatchRcp“ erweitern, um ihr die Kennung hinzuzufügen (in diesem Fall ist keine ROI-Berechnung mit diesen Feldern verknüpft).

Es wird zudem dringend empfohlen, ein Ereignisdatum hinzuzufügen.

Das folgende Schema stellt die Relationen der unterschiedlichen Tabellen nach erfolgter Konfiguration dar:

![](assets/response_data_model.png)

### Reaktionsverwaltung und Empfänger {#response-management-with-adobe-campaign-recipients}

In diesem Beispiel wird mithilfe der in Adobe Campaign integrierten Empfängertabelle „**[!UICONTROL nms:recipient]**“ eine Tabelle mit Käufen in das Reaktionsverwaltungsmodul integriert.

Die Tabelle mit Reaktionsprotokollen bei **[!UICONTROL nms:remaMatchRcp]**-Empfangenden wird erweitert, um eine Verknüpfung zum Kauftabellen-Schema hinzuzufügen. Im folgenden Beispiel heißt die Kauftabelle **demo:purchase**.

1. Gehen Sie im Adobe Campaign-Explorer in den Knoten **[!UICONTROL Administration]** > **[!UICONTROL Kampagnen]** > **[!UICONTROL Zielgruppen-Mappings]**.
1. Machen Sie einen Rechtsklick auf **Empfänger** und wählen Sie **[!UICONTROL Aktionen]** und **[!UICONTROL Optionen der Zielgruppendimension ändern...]** aus.

   ![](assets/delivery_mapping1.png)

1. Passen Sie gegebenenfalls in dem sich öffnenden Fenster den **[!UICONTROL Erweiterungs-Namespace]** an und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/delivery_mapping2.png)

1. Stellen Sie sicher, dass in der Kategorie **[!UICONTROL Reaktionsverwaltung]** die Option **[!UICONTROL Speicherschema für Reaktionen erzeugen]** aktiviert ist.

   Klicken Sie dann auf **[!UICONTROL Zusätzliche Felder definieren…]**, um die zugehörigen Transaktionstabellen auszuwählen und die gewünschten Felder zur Erweiterung des nms:remaMatchRcp-Schemas hinzuzufügen.

   ![](assets/delivery_mapping3.png)

Folgendes Schema wird daraufhin erstellt:

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### Reaktionsverwaltung mit einer benutzerdefinierten Empfängertabelle {#response-management-with-a-personalized-recipient-table}

In diesem Beispiel wird unter Verwendung einer Individuentabelle, also nicht der Adobe Campaign-Empfängertabelle, eine Tabelle mit Kaufdaten in die Reaktionsverwaltung integriert.

* Erstellen Sie ein neues Reaktionsprotokollschema, das vom **[!UICONTROL nms:remaMatch]**-Schema abgeleitet ist.

  Da sich die Tabelle der Personen von der Empfängertabelle in Adobe Campaign unterscheidet, muss ein neues Schema der Reaktionsprotokolle basierend auf dem **[!UICONTROL nms:remaMatch]**-Schema erstellt werden. Anschließend müssen die Relationen zu den Versandlogs und der die Bestelldaten enthaltenden Transaktionstabelle hinzugefügt werden.

  Im folgenden Beispiel verwenden wir das Schema **demo:broadLogPers** und die Transaktionstabelle **demo:purchase**:

  ```
  <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
  img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
    <element name="remaMatchPers" template="nms:remaMatch">
      <key internal="true" name="match">
        <keyfield xlink="hypothesis"/>
       <keyfield xlink="purchase"/>
      </key>
  
      <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
      <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
               target="demo:propositionPers" type="link"/>
      <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
    </element>
  </srcSchema>
  ```

* Ändern Sie das Hypothesenformular im **[!UICONTROL nms:remaHypothesis]**-Schema.

  Standardmäßig wird die Liste der Reaktionsprotokolle in den Empfängerprotokollen angezeigt. Um die im vorherigen Schritt erstellten neuen Reaktionsprotokolle anzuzeigen, müssen Sie daher das Hypothesenformular ändern.

  Beispiel:

  ```
   <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                 toolbarCaption="Responses generated by the hypothesis" type="linklist"
                 xpath="remaMatchPers">
            <input xpath="[.]"/>
            <input xpath="@controlGroup"/>
          </input>
     </container> 
  ```

## Indikatoren verwalten {#managing-indicators}

Das Response Manager-Modul verfügt über eine Liste an vordefinierten Indikatoren.Sie können jedoch weitere personalisierte Messindikatoren hinzufügen.

Erweitern Sie hierzu die Hypothesentabelle, indem Sie zwei Felder für jeden neuen Indikator hinzufügen:

* das erste für die Zielpopulation,
* das zweite für die Kontrollgruppe.

Beispiel:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```
