---
title: Kontrollregeln
seo-title: Kontrollregeln
description: Kontrollregeln
seo-description: null
page-status-flag: never-activated
uuid: a83e56d0-573a-4592-b2b1-0d3b3e52b03f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: be037a80-3f94-465c-ba7d-ae7d50f70e36
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Kontrollregeln{#control-rules}

## Analyse und Schlichtungskontrollregeln {#analysis-and-arbitration-control-rules}

Kontrollregeln dienen dazu, vor dem Versand die Gültigkeit und Qualität der Nachrichten (korrekte Anzeige aller Zeichen, SMS-Größe, Adressenformat etc.) sicherzustellen.

Mehrere standardmäßige Regeln führen grundlegende Kontrollen durch. Es handelt sich um folgende, in der Benutzeroberfläche durch Fettschrift gekennzeichnete Regeln:

* **[!UICONTROL Object approval]** (E-Mail): überprüft, ob das Objekt und die Adresse des Absenders keine Sonderzeichen enthalten, die Probleme bei bestimmten E-Mail-Agenten verursachen können.
* **[!UICONTROL URL label approval]** (E-Mail): überprüft, ob jede Tracking-URL eine Beschriftung enthält.
* **[!UICONTROL URL approval]** (E-Mail): prüft die Tracking-URLs (Vorhandensein des Zeichens &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (mobil): überprüft die Größe von SMS-Nachrichten.
* **[!UICONTROL Validity period check]** (E-Mail): überprüft, dass die Gültigkeitsdauer der Lieferung lang genug ist, um alle Nachrichten zu senden.
* **[!UICONTROL Proof size check]** (alle Kanäle): erzeugt eine Fehlermeldung, wenn die Proof-Zielpopulation 100 Empfänger überschreitet.
* **[!UICONTROL Wave scheduling check]** (E-Mail): überprüft, ob die letzte Zustellungswelle vor Ablauf der Gültigkeitsdauer beginnen soll, wenn die Zustellung in mehrere Wellen unterteilt wird.
* **[!UICONTROL Unsubscription link approval]** (E-Mail): prüft, ob in jedem Inhalt (HTML und Text) mindestens eine Ausschluss- (Ausschluss-)URL vorhanden ist.

## Kontrollregeln erstellen {#creating-a-control-rule}

Es ist möglich, neue Steuerungsregeln zu erstellen, die Ihren Anforderungen entsprechen. Erstellen Sie dazu eine **[!UICONTROL Control]** Typologieregel und geben Sie die Steuerformel in SQL auf der **[!UICONTROL Code]** Registerkarte ein.

**Beispiel:**

Im folgenden Beispiel wird eine Regel erstellt, die den Versand eines Angebots auf 100 Empfänger begrenzt. Diese Regel wird in einer Kampagnentypologie referenziert, die in SMS-Sendungen mit dem entsprechenden Angebot verwendet wird.

Gehen Sie wie folgt vor:

1. Create a **[!UICONTROL Control]** typology rule. Wählen Sie eine **[!UICONTROL Warning]** Warnungsebene aus.

   ![](assets/campaign_opt_create_control_01.png)

1. Geben Sie im Tab **[!UICONTROL Code]** wie folgt das Skript zur Anwendung der gewünschten Schwelle ein:

   ![](assets/campaign_opt_create_control_02.png)

   Das Skript erzeugt nun eine Warnung, sobald die Zielgruppe des Versands 100 Empfänger übersteigt:

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

   At the end of the analysis, the **[!UICONTROL Confirm delivery]** button will not be available.

   ![](assets/campaign_opt_create_control_06.png)

