---
product: campaign
title: Bedingter Inhalt
description: Erfahren Sie, wie bedingter Inhalt hinzugefügt wird
badge-v8: label="Gilt auch für v8" type="Positive" tooltip="Gilt auch für Campaign v8"
feature: Personalization, Multilingual Messages
role: User
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: ht
source-wordcount: '509'
ht-degree: 100%

---

# Bedingter Inhalt{#conditional-content}

Die Konfiguration bedingter Inhalte erlaubt eine dynamische Personalisierung, beispielsweise auf der Basis des Empfängerprofils. Dabei werden Textbausteine und/oder Bilder ersetzt, wenn eine bestimmte Bedingung erfüllt ist.

![](assets/do-not-localize/how-to-video.png) [Mehr zu dieser Funktion erfahren Sie im Video.](#conditionnal-content-video).


## Verwenden von Bedingungen in einer E-Mail {#using-conditions-in-an-email}

Im folgenden Beispiel erfahren Sie, wie Sie eine Nachricht erstellen und entsprechend dem Geschlecht und den Interessen des Empfängers dynamisch personalisieren können.

* Anzeige von „Herr“ oder „Frau“ entsprechend dem Wert im Feld **[!UICONTROL Geschlecht]** der Datenquelle (männlich bzw. weiblich).
* Individuell auf den Empfänger zugeschnittene Zusammenstellung eines Newsletters oder eines Angebots in Abhängigkeit von seinen angegebenen oder erkannten Interessen:

   * Interessen 1 -- > Baustein 1
   * Interessen 2 -- > Baustein 2
   * Interessen 3 -- > Baustein 3
   * Interessen 4 -- > Baustein 4

Gehen Sie wie folgt vor, um einen von einem Feldwert abhängigen bedingten Inhalt zu erstellen:

1. Klicken Sie auf die Personalisierungsfeld-Schaltfläche und wählen Sie **[!UICONTROL Bedingter Inhalt > Wenn]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Die Personalisierungselemente werden in den Nachrichten-Textkörper eingefügt.

1. Konfigurieren Sie nun den **If**-Ausdruck.

   Gehen Sie dazu wie folgt vor:

   * Wählen Sie das erste Element **`<field>`** des Ausdrucks aus (standardmäßig wird dieses Element beim Einfügen des **If**-Ausdrucks hervorgehoben) und klicken Sie auf das Personalisierungssymbol, um es durch das Testfeld zu ersetzen.

     ![](assets/s_ncs_user_conditional_content03.png)

   * Ersetzen Sie **`<value>`** durch den Wert des Feldes, für das die Bedingung erfüllt wird. Dieser Wert muss in Anführungszeichen gesetzt werden.
   * Fügen Sie anschließend den Inhalt ein, der bei Erfüllung der Bedingung für den Versand genutzt werden soll. Hierbei kann es sich um einen Text, ein Bild, ein Formular, einen Link usw. handeln.

     ![](assets/s_ncs_user_conditional_content04.png)

1. Klicken Sie nun auf den **[!UICONTROL Vorschau]**-Tab, um den dem Empfänger entsprechend personalisierten Nachrichteninhalt anzusehen.

   * Auswahl eines Empfängers, für den die Kriterien zutreffen:

     ![](assets/s_ncs_user_conditional_content05.png)

   * Auswahl eines Empfängers für den die Kriterien nicht zutreffen:

     ![](assets/s_ncs_user_conditional_content06.png)

Sie können weitere Bedingungen hinzufügen und Inhalte in Abhängigkeit von einem oder mehreren Feldwerten konfigurieren. Dies ist mit den Optionen **[!UICONTROL Bedingter Inhalt > Sonst]** und **[!UICONTROL Bedingter Inhalt > Sonst wenn]** möglich. Die Vorgehensweise ist die gleiche wie beim **If**-Ausdruck.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>In der JavaScript-Syntax müssen die Zeichen **%> &lt;%** bei Verwendung von **Sonst** und **Sonst wenn** entfernt werden.

Klicken Sie nun auf den **[!UICONTROL Vorschau]**-Tab und wählen Sie einen Empfänger aus, um den bedingten Inhalt anzusehen.

![](assets/s_ncs_user_conditional_content08.png)

## Erstellen einer mehrsprachigen E-Mail {#creating-multilingual-email}

Im folgenden Beispiel erfahren Sie, wie Sie eine mehrsprachige E-Mail erstellen. Inhalte werden in der bevorzugten Sprache des Empfängers angezeigt.

1. Erstellen Sie eine E-Mail und wählen Sie die Zielpopulation aus. In diesem Beispiel basiert die Bedingung für die Darstellung einer bestimmten Version auf dem Wert **Sprache** des Empfängerprofils. In unserem Beispiel sind diese Werte auf **EN**, **FR**, **ES** gesetzt.
1. Klicken Sie im HTML-Inhalt der E-Mail auf den Tab **[!UICONTROL Quelle]** und fügen Sie folgenden Code ein:

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. Überprüfen Sie den E-Mail-Inhalt im Tab **[!UICONTROL Vorschau]**, indem Sie Empfänger mit unterschiedlichen Sprachen auswählen.

   >[!NOTE]
   >
   >Da Sie für den E-Mail-Inhalt keine andere Version definiert haben, müssen Sie die Zielpopulation vor dem Versand der E-Mail filtern.

## Anleitungsvideo {#conditionnal-content-video}

Erfahren Sie, wie Sie einem Versand bedingte Inhalte hinzufügen können, beispielsweise einen mehrsprachigen Newsletter.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

Weitere Anleitungsvideos zu Campaign Classic finden Sie [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=de).
