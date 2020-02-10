---
title: Additional data
seo-title: Additional data
description: Additional data
seo-description: null
page-status-flag: never-activated
uuid: 81a889ce-b02d-4593-95fa-1de5601182e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 29339aad-fd8e-4dae-8f6e-2db87221ad04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Additional data{#additional-data}

Es besteht die Möglichkeit, bei Abfrage des Angebotsmoduls zusätzliche Kontextdaten zu übergeben. Dies können entweder aus der Arbeitstabelle eines Workflows stammende Daten der Zielgruppe (ausgehender Kanal) oder von der Webseite zum Zeitpunkt der Abfrage gesendete Aufrufdaten (eingehender Kanal) sein. Die zusätzlichen Daten können in Eignungsregeln und der Angebotspersonalisierung verwendet und in der Vorschlagstabelle gespeichert werden.

Bei eingehenden Interaktionen beispielsweise kann es interessant sein, die Browsersprache eines Webseitenbesuchers oder den Namen des Callcenter-Mitarbeiters, der einen Anruf entgegengenommen hat, abzufragen. In den Eignungsregeln können Sie auf diese Aufrufdaten (call data) Bezug nehmen, um ein Angebot z. B. nur Personen zu unterbreiten, die Ihre Webseite auf Deutsch oder Englisch ansehen.

In einem Zielbestimmungs-Workflow (ausgehender Kanal) können Sie die Zielgruppendaten (target data) in der Abfrage des Angebotsmoduls nutzen. Die Zielgruppe kann so z. B. durch Transaktionsdaten der Empfänger oder durch eine externe Datenbank über den FDA angereichert werden.

## Weitere Konfigurationsmöglichkeiten {#additional-data-configuration}

Sie müssen das mit der Umgebung verknüpfte **nms:interaction** -Schema erweitern und die Liste der zusätzlichen Felder deklarieren, die bei einem Aufruf der Interaction-Engine verwendet werden. Beim Erstellen der Berechtigungsregel oder beim Personalisieren eines Angebots können diese Felder vom Knoten **Interaktion** aus aufgerufen werden (siehe [Verwenden zusätzlicher Daten](#using-additional-data)).

Für eingehende Kanäle müssen im Knoten **Interaction** die Aufrufdaten eingefügt werden.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>XML-Kollektionen werden für den eingehenden Kanal unterstützt, Relationen zu anderen Schemata jedoch nicht.

Für ausgehende Kanäle muss im Knoten **Interaction** ein die zusätzlichen Felder enthaltendes **targetData**-Element eingefügt werden.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>Kollektionen werden für den ausgehenden Kanal nicht unterstützt. Sie können jedoch Relationen zu anderen Schemata konfigurieren.

Wenn Sie diese Daten in der Vorschlagstabelle speichern möchten, muss außerdem das Schema **nms:propositionRcp** erweitert werden, um die neuen Felder zu deklarieren.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## Implementierung zusätzlicher Daten {#additional-data-implementation}

### Eingehender Kanal (Webseite) {#input-channel--web-page-}

To transfer additional data when calling the engine, you have to add the **interactionGlobalCtx** variable into the web page&#39;s JavaScript code. Insert the **Interaction** node containing the call data into this variable. You must respect the same xml structure that is in the **nms:interaction** schema. Siehe: [Zusätzliche Datenkonfiguration](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Ausgehender Kanal {#output-channel}

You must create a targeting workflow loading additional data in the work table by respecting the same xml structure and same internal names as in the **nms:interaction** schema. Siehe: [Zusätzliche Datenkonfiguration](#additional-data-configuration).

## Verwendung der zusätzlichen Daten {#using-additional-data}

### Eignungsregeln {#eligibility-rules}

Zusätzliche Daten können in den Eignungsregeln auf Ebene der Angebote, der Kategorien und der Gewichtungen verwendet werden.

Sie können beispielsweise die Unterbreitung eines Angebots auf Kontakte beschränken, die die Webseite in englischer Sprache ansehen.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>Sie müssen die Regel auf die Kanäle beschränken, für die die Daten definiert werden. In unserem Beispiel begrenzen wir die Regel für den eingehenden Webkanal (**[!UICONTROL Taken into account if]** Feld).

### Personalisierung  {#personalization}

Zusätzliche Daten können des Weiteren bei der Angebotspersonalisierung zum Einsatz kommen. Sie können beispielsweise eine Bedingung bezüglich der Browsersprache des Besuchers formulieren.

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>Die Regel muss sich auf die Kanäle beziehen, für die die Daten definiert wurden. Im vorliegenden Beispiel wurde die Regel auf den eingehenden Web-Kanal begrenzt.

Wenn Sie ein Angebot mit zusätzlichen Daten personalisiert haben, werden diese Daten standardmäßig nicht in der Vorschau angezeigt, da sie nicht in der Datenbank verfügbar sind. Auf der **[!UICONTROL Example of call data]** Registerkarte der Umgebung müssen Sie Wertesampeln hinzufügen, die in der Vorschau verwendet werden sollen. Bitte beachten Sie die gleiche XML-Struktur wie in der **nms:interaction** -Schemaerweiterung. For more on this, refer to [Additional data configuration](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Klicken Sie bei der Vorschau auf **[!UICONTROL Content personalization options for the preview]** und wählen Sie einen Wert im **[!UICONTROL Call data]** Feld aus.

![](assets/ita_calldata_preview2.png)

### Speicherung {#storage}

Zum Zeitpunkt der Abfrage des Angebotsmoduls besteht die Möglichkeit, die zusätzlichen Daten in der Vorschlagstabelle zu speichern, um die Datenbank anzureichern. Auf diese Weise können die Daten beispielsweise in Berichten, zur Berechnung des ROI oder in späteren Vorgängen verwendet werden.

>[!NOTE]
>
>You must have extended the **nms:propositionRcp** schema and declared the fields that will contain the data to be stored. Weitere Informationen: [Zusätzliche Datenkonfiguration](#additional-data-configuration).

In the offer space, go to the **[!UICONTROL Storage]** tab and click the **[!UICONTROL Add]** button.

Wählen Sie in der **[!UICONTROL Storage path]** Spalte das Speicherfeld in der Propositionstabelle aus. Wählen Sie in der **[!UICONTROL Expression]** Spalte das zusätzliche Feld in der **[!UICONTROL Interaction]** Node aus.

Die Aufrufdaten können entweder zum Zeitpunkt der Vorschlagserzeugung oder zum Zeitpunkt seiner Annahme (durch Klick des Kontakts auf das Angebot) abgerufen werden.

![](assets/ita_calldata_storage.png)

