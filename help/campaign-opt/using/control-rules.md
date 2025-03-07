---
product: campaign
title: Kontrollregeln
description: Erfahren Sie, wie in Adobe Campaign mit Kontrollregeln gearbeitet wird.
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: ht
source-wordcount: '393'
ht-degree: 100%

---

# Kontrollregeln{#control-rules}

## Analyse und Schlichtungskontrollregeln {#analysis-and-arbitration-control-rules}

Kontrollregeln dienen dazu, vor dem Versand die Gültigkeit und Qualität der Nachrichten (korrekte Anzeige aller Zeichen, SMS-Größe, Adressenformat etc.) sicherzustellen.

Mehrere standardmäßige Regeln führen grundlegende Kontrollen durch. Es handelt sich um folgende, in der Benutzeroberfläche durch Fettschrift gekennzeichnete Regeln:

* **[!UICONTROL Betreffvalidierung]** (E-Mail): stellt sicher, dass Betreff und Absenderadresse keine Sonderzeichen enthalten, die bei gewissen E-Mail-Programmen Probleme bereiten könnten.
* **[!UICONTROL Validierung der URL-Titel]** (E-Mail): stellt sicher, dass jede Tracking-URL über einen Titel verfügt.
* **[!UICONTROL URL-Validierung]** (E-Mail): überprüft die Tracking-URLs (Vorhandensein des &quot;&amp;&quot;-Zeichens).
* **[!UICONTROL Validierung der Nachrichtengröße]** (Mobiltelefon): überprüft die Größe von SMS-Nachrichten.
* **[!UICONTROL Prüfung der Gültigkeit]** (E-Mail): stellt sicher, dass die Gültigkeit des Versands ausreichend lang ist, um alle Nachrichten zu versenden.
* **[!UICONTROL Prüfung der Testversandgröße]** (alle Kanäle): erzeugt eine Fehlernachricht, wenn die Test-Zielgruppe mehr als 100 Empfänger enthält.
* **[!UICONTROL Prüfung der Schub-Planung]** (E-Mail): prüft im Falle von Schub-Sendungen, ob der letzte geplante Schub vor dem Ablaufdatum des Versands liegt.
* **[!UICONTROL Validierung des Abmelde-Links]** (E-Mail): prüft, ob in jedem Inhalt (HTML und Text) mindestens eine URL vom Typ &quot;Opt-out&quot; enthalten ist.

## Kontrollregeln erstellen {#creating-a-control-rule}

Sie können entsprechend Ihren Bedürfnissen neue Kontrollregeln hinzufügen. Erstellen Sie hierfür eine Typologieregel vom Typ **[!UICONTROL Kontrolle]** und geben Sie die SQL-Kontrollformel im Tab **[!UICONTROL Code]** ein.

**Beispiel:**

Im folgenden Beispiel wird eine Regel erstellt, die den Versand eines Angebots auf 100 Empfänger begrenzt. Diese Regel wird in einer Kampagnentypologie referenziert, die in SMS-Sendungen mit dem entsprechenden Angebot verwendet wird.

Gehen Sie wie folgt vor:

1. Erstellen Sie eine Typologieregel vom Typ **[!UICONTROL Kontrolle]**. Wählen Sie das Niveau **[!UICONTROL Warnung]** aus.

   ![](assets/campaign_opt_create_control_01.png)

1. Geben Sie im Tab **[!UICONTROL Code]** wie folgt das Script zur Anwendung der gewünschten Schwelle ein:

   ![](assets/campaign_opt_create_control_02.png)

   Das Script erzeugt nun eine Warnung, sobald die Zielgruppe des Versands 100 Empfänger übersteigt:

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. Verbinden Sie die Regel mit einer Kampagnentypologie und referenzieren Sie diese Typologie im betroffenen SMS-Versand.

   ![](assets/campaign_opt_create_control_03.png)

1. Die Regel wird bei der Versandanaluyse angewandt und erzeugt im gegebenen Fall eine Warnung.

   ![](assets/campaign_opt_create_control_04.png)

   Der Versand ist auch im Falle einer Warnung startbereit.

   Bei einer erhöhten Gravität kann der Versand jedoch nicht gestartet werden.

   ![](assets/campaign_opt_create_control_05.png)

   In diesem Fall ist am Ende der Analyse die Schaltfläche **[!UICONTROL Versand bestätigen]** nicht verfügbar.

   ![](assets/campaign_opt_create_control_06.png)
