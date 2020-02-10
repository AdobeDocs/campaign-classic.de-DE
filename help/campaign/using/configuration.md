---
title: 'Konfiguration '
seo-title: 'Konfiguration '
description: 'Konfiguration '
seo-description: null
page-status-flag: never-activated
uuid: 59503b54-ad49-4b00-8ffb-52e6f6c62070
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: ed4afa5e-c184-4c8e-a086-41d87b863190
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Konfiguration{#configuration}

Dieses Kapitel richtet sich an die für die Konfiguration der Reaktionsverwaltung zuständigen Benutzer. Die Umsetzung dieser Konfiguration erfordert Kenntnisse über Schemaerweiterung, Workflow-Erstellung und -Verwaltung sowie SQL-Programmierung.

Es wird erklärt, wie die Standard-Datenmodelle den Besonderheiten einer Adobe-Campaign-externen Transaktionstabelle mittels der Individuentabelle angepasst werden. Diese Individuentabelle kann der in Adobe Campaign verfügbaren Empfängertabelle oder einer anderen Tabelle entsprechen.

Die Messhypothese wird durch den Arbeitsablauf des Arbeitsablaufs ( **[!UICONTROL operationMgt]** ) gestartet. Jede Hypothese stellt einen separaten Prozess dar, der asynchron mit einem Ausführungsstatus (Bearbeitung, Ausstehend, Fertig gestellt, Fehlgeschlagen usw.) ausgeführt wird. und von einem Scheduler gesteuert werden, der Prioritätsbeschränkungen, die Einschränkung der Anzahl gleichzeitiger Prozesse, die niedrige Aktivitätsseite und die automatische Ausführung mit Häufigkeit verwaltet.

## Schemata konfigurieren {#configuring-schemas}

>[!CAUTION]
>
>Die anwendungseigenen Schemata dürfen nicht verändert werden, da diese im Zuge von Software-Updates verändert oder gelöscht werden können und dies Funktionsstörungen bei der Verwendung von Adobe Campaign zur Folge haben kann. Nutzen Sie stattdessen die Möglichkeit der Schemaerweiterung.

Vor der Anwendung dieser Option müssen die verschiedenen Tabellen (Transaktionen, Transaktionendetails) und ihre Beziehung mit Sendungen, Angeboten und Individuen definiert werden.

### Standardschemata {#standard-schemas}

Das vordefinierte **[!UICONTROL nms:remaMatch]** Schema enthält die Reaktionsprotokolltabelle, d.h. die Beziehung zwischen Individuen, Hypothese und Transaktionstabelle. Dieses Schema wird als Vererbungsschema für die endgültige Zieltabelle der Reaktionsprotokolle verwendet.

Das **[!UICONTROL nms:remaMatchRcp]** Schema ist auch als Standard verfügbar und enthält die Speicherung von Reaktionsprotokollen für Adobe Campaign-Empfänger ( **[!UICONTROL nms:recipient]** ). Um verwendet werden zu können, muss es erweitert werden, um einer Transaktionstabelle zugeordnet zu werden (mit Käufen usw.).

### Transaktionstabellen und -details {#transaction-tables-and-transaction-details}

Die Transaktionstabelle muss über eine direkte Relation mit den Individuen verfügen.

Sie haben darüber hinaus die Möglichkeit, eine die Details der Transaktionen enthaltende Tabelle hinzuzufügen, die selbst nicht direkt mit den Individuen verbunden ist.

Im Fall eines Kassenzettels zum Beispiel ist eine Transaktionstabelle mit dem Kontakt verbunden (die Kassenzettel-Tabelle) und eine zweite Tabelle (die Detailtabelle), welche die Kassenzettelzeilen enthält, ist nur mit der Kassenzettel-Tabelle verbunden. So kann die Hypothese direkt auf Ebene der mit der Kassenzettel-Tabelle verbundenen Detailtabelle (Kassenzettelzeilen) konfiguriert werden.

>[!NOTE]
>
>Wenn Sie die Kennung der Zettelzeilen, die das in der Hypothese erwartete Verhalten beschreibt, beibehalten möchten, können Sie das Schema nms:remaMatchRcp erweitern, um die Kennung hinzuzufügen (in diesem Fall wird diesen Feldern keine ROI-Berechnung zugeordnet).

Es wird zudem dringend empfohlen, ein Ereignisdatum hinzuzufügen.

Die folgende Grafik stellt die Relationen der unterschiedlichen Tabellen nach erfolgter Konfiguration dar:

![](assets/response_data_model.png)

### Reaktionsverwaltung der Adobe-Campaign-Empfängertabelle {#response-management-with-adobe-campaign-recipients}

In this example, we will integrate a table of purchases in our response management module using the Adobe Campaign recipient table ( **[!UICONTROL nms:recipient]** ).

Die Tabelle der Antwortprotokolle eines **[!UICONTROL nms:remaMatchRcp]** Empfängers wird erweitert, um einen Link zum Einkaufstabelle-Schema hinzuzufügen. Im folgenden Beispiel heißt die Kauftabelle **demo:purchase**.

1. Wählen Sie über den Adobe Campaign-Explorer **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Klicken Sie mit der rechten Maustaste auf **Empfänger** , wählen Sie **[!UICONTROL Actions]** und **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. You can personalize the **[!UICONTROL Extension namespace]** in the next window, then click **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. Vergewissern Sie sich in der **[!UICONTROL Response management]** Kategorie, dass das **[!UICONTROL Generate a storage schema for reactions]** Kontrollkästchen aktiviert ist.

   Then click **[!UICONTROL Define additional fields...]** to select the related transaction tables and add the desired fields to the extension of the nms:remaMatchRcp schema.

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

In diesem Beispiel wird unter Verwendung einer Individuentabelle, also nicht der Adobe-Campaign-Empfängertabelle, eine Tabelle mit Bestelldaten in die Reaktionsverwaltung integriert.

* Erstellung eines neuen Reaktionslog-Schemas basierend auf dem Schema **[!UICONTROL nms:remaMatch]**.

   Da sich die Tabelle der einzelnen Personen von der Tabelle der Adobe Campaign-Empfänger unterscheidet, ist es notwendig, ein neues Schema der Antwortprotokolle basierend auf dem **[!UICONTROL nms:remaMatch]** Schema zu erstellen. Füllen Sie es dann mit Links zu den Lieferprotokollen und der Kauftabelle aus.

   In the following example, we will use the **demo:broadLogPers** schema and the **demo:purchase** transaction table:

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

* Modifying the hypothesis form in the **[!UICONTROL nms:remaHypothesis]** schema.

   Standardmäßig wird die Liste der Reaktionslogs in den Empfängerlogs angezeigt. Um die neuen, in der vorhergehenden Etappe erstellten Reaktionslogs anzuzeigen, muss daher das Hypothesenformular geändert werden.

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

## Indikatorenverwaltung {#managing-indicators}

Die Option Response Manager wird mit einer Liste vordefinierter Indikatoren geliefert. Sie haben jedoch die Möglichkeit, andere Indikatoren mit benutzerdefinierten Messungen hinzuzufügen.

Erweitern Sie hierzu die Hypothesentabelle, indem Sie zwei Felder für jeden neuen Indikator hinzufügen:

* das erste für die Zielgruppe,
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

