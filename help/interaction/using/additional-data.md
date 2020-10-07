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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 100%

---


# Additional data{#additional-data}

Es besteht die Möglichkeit, bei Abfrage des Angebotsmoduls zusätzliche Kontextdaten zu übergeben. Dies können entweder aus der Arbeitstabelle eines Workflows stammende Daten der Zielgruppe (ausgehender Kanal) oder von der Webseite zum Zeitpunkt der Abfrage gesendete Aufrufdaten (eingehender Kanal) sein. Die zusätzlichen Daten können in Eignungsregeln und der Angebotspersonalisierung verwendet und in der Vorschlagstabelle gespeichert werden.

Bei eingehenden Interaktionen beispielsweise kann es interessant sein, die Browsersprache eines Webseitenbesuchers oder den Namen des Callcenter-Mitarbeiters, der einen Anruf entgegengenommen hat, abzufragen. In den Eignungsregeln können Sie auf diese Aufrufdaten (call data) Bezug nehmen, um ein Angebot z. B. nur Personen zu unterbreiten, die Ihre Webseite auf Deutsch oder Englisch ansehen.

In einem Zielbestimmungs-Workflow (ausgehender Kanal) können Sie die Zielgruppendaten (target data) in der Abfrage des Angebotsmoduls nutzen. Die Zielgruppe kann so z. B. durch Transaktionsdaten der Empfänger oder durch eine externe Datenbank über den FDA angereichert werden.

## Weitere Konfigurationsmöglichkeiten {#additional-data-configuration}

Sie müssen das mit der Umgebung verknüpfte **nms:interaction**-Schema erweitern und die Liste der zusätzlichen Felder deklarieren, die bei einem Aufruf des Interaction-Moduls verwendet werden. Beim Erstellen der Eignungsregel oder Personalisieren eines Angebots können diese Felder über den Knoten **Interaction** aufgerufen werden (siehe [Verwendung zusätzlicher Daten](#using-additional-data)).

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

Um bei der Angebotsmodul-Abfrage zusätzliche Daten zu übergeben, muss der JavaScript-Code der Web-Seite um die Variable **interactionGlobalCtx** ergänzt werden. Fügen Sie in diese Variable den die Aufrufdaten enthaltenden **Interaction**-Knoten ein. Verwenden Sie dabei die gleiche XML-Struktur wie bei der Erweiterung des Schemas **nms:interaction**. Siehe [Weitere Konfigurationsmöglichkeiten](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### Ausgehender Kanal {#output-channel}

Erstellen Sie einen Zielgruppen-Workflow zum Laden der zusätzlichen Daten in die Arbeitstabelle. Dabei müssen die gleiche XML-Struktur und die gleichen internen Namen beachtet werden wie im Schema **nms:interaction**. Siehe [Weitere Konfigurationsmöglichkeiten](#additional-data-configuration).

## Verwendung der zusätzlichen Daten {#using-additional-data}

### Eignungsregeln {#eligibility-rules}

Zusätzliche Daten können in den Eignungsregeln auf Ebene der Angebote, der Kategorien und der Gewichtungen verwendet werden.

Sie können beispielsweise die Unterbreitung eines Angebots auf Kontakte beschränken, die die Webseite in englischer Sprache ansehen.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>Die Regel muss sich auf die Kanäle beziehen, für die die Daten definiert wurden. Im vorliegenden Beispiel wurde die Regel auf den eingehenden Web-Kanal begrenzt (Feld **[!UICONTROL Berücksichtigt wenn]**).

### Personalisierung   {#personalization}

Zusätzliche Daten können des Weiteren bei der Angebotspersonalisierung zum Einsatz kommen. Sie können beispielsweise eine Bedingung bezüglich der Browsersprache des Besuchers formulieren.

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>Die Regel muss sich auf die Kanäle beziehen, für die die Daten definiert wurden. Im vorliegenden Beispiel wurde die Regel auf den eingehenden Web-Kanal begrenzt.

Wenn Sie ein Angebot mit zusätzlichen Daten personalisieren, werden diese nicht automatisch in der Angebotsvorschau angezeigt, da sie nicht in der Datenbank enthalten sind. Fügen Sie daher im Tab **[!UICONTROL Aufrufdatenbeispiel]** Musterwerte ein, die in der Vorschau verwendet werden können. Hierbei ist die gleiche XML-Struktur wie im erweiterten Schema **nms:interaction** zu verwenden. Lesen Sie diesbezüglich auch den Abschnitt [Weitere Konfigurationsmöglichkeiten](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

Klicken Sie im Vorschau-Tab auf **[!UICONTROL Personalisierungsoptionen für die Vorschau]** und wählen Sie im Feld **[!UICONTROL Aufrufdaten]** einen Wert aus der Dropdown-Liste aus.

![](assets/ita_calldata_preview2.png)

### Speicherung {#storage}

Zum Zeitpunkt der Abfrage des Angebotsmoduls besteht die Möglichkeit, die zusätzlichen Daten in der Vorschlagstabelle zu speichern, um die Datenbank anzureichern. Auf diese Weise können die Daten beispielsweise in Berichten, zur Berechnung des ROI oder in späteren Vorgängen verwendet werden.

>[!NOTE]
>
>Hierzu müssen das Schema **nms:propositionRcp** erweitert und die Felder, die die Daten aufnehmen sollen, deklariert worden sein. Weitere Informationen hierzu finden Sie unter [Weitere Konfigurationsmöglichkeiten](#additional-data-configuration).

Gehen Sie in den Tab **[!UICONTROL Speicherung]** der Platzierung und klicken Sie auf **[!UICONTROL Hinzufügen]**.

Wählen Sie in der Spalte **[!UICONTROL Speicherpfad]** das Feld aus der Vorschlagstabelle aus, das zur Speicherung der zusätzlichen Daten verwendet werden soll. Wählen Sie dann in der Spalte **[!UICONTROL Ausdruck]** das entsprechende Feld aus dem **[!UICONTROL Interaction]**-Knoten aus.

Die Aufrufdaten können entweder zum Zeitpunkt der Vorschlagserzeugung oder zum Zeitpunkt seiner Annahme (durch Klick des Kontakts auf das Angebot) abgerufen werden.

![](assets/ita_calldata_storage.png)

