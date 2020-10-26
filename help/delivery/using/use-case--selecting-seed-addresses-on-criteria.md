---
title: '"Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien"'
seo-title: '"Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien"'
description: '"Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien"'
seo-description: null
page-status-flag: never-activated
uuid: 6af39893-6ef3-4204-8b53-0c16e35bac8f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: fa8aab62-e182-4388-aa23-c255b0dbd42e
translation-type: ht
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: ht
source-wordcount: '920'
ht-degree: 100%

---


# Anwendungsbeispiel: Auswahl von Testadressen nach Kriterien{#use-case-selecting-seed-addresses-on-criteria}

Der Link **[!UICONTROL Dynamische Bedingung bearbeiten...]** ermöglicht es, im Rahmen einer Kampagne oder einer Sendung die zu verwendenden Testadressen nach bestimmten Kriterien auszuwählen.

In unserem Anwendungsbeispiel versendet die Webseite **Mein Online-Buchshop** je nach bevorzugtem Genre verschiedene Newsletter an seine Kunden.

In Absprache mit der Einkaufsabteilung hat der versandverantwortliche Benutzer einen Newsletter für Kunden erstellt, die in der Vergangenheit bereits Kriminalromane bestellt haben.

Damit die Kollegen der Einkaufsabteilung das Ergebnis ihrer Zusammenarbeit sehen können, fügt sie der Versandverantwortliche als Testadressen zu den Versandempfängern hinzu. Durch die Verwendung einer dynamischen Bedingung lassen sich der Konfigurationsaufwand und die Adressaktualisierung optimieren.

Zur Verwendung von dynamischen Bedingungen benötigen Sie:

* einen vollständig konfigurierten Versand,
* Testadressen mit einem gemeinsamen Wert. Dieser Wert kann aus einem in Adobe Campaign vorhandenen Feld stammen. Im vorliegenden Beispiel besteht die Gemeinsamkeit der Testadressen im Wert &quot;Einkauf&quot; des Felds &quot;Abteilung&quot;, welches nicht standardmäßig in der Anwendung enthalten ist.

## Schritt 1: Erstellen eines Versands {#step-1---creating-a-delivery}

Die Schritte zum Erstellen eines Versands finden Sie im Abschnitt [E-Mail-Versand erstellen](../../delivery/using/creating-an-email-delivery.md).

Im vorliegenden Beispiel hat der Versandverantwortliche zunächst den Newsletter erstellt und die Zielgruppe ausgewählt.

![](assets/dlv_seeds_usecase_01.png)

## 2. Schritt - Gemeinsamen Wert definieren {#step-2---creating-a-common-value}

Die Hinzufügung des Abteilung-Feldes, welches den gemeinsamen Wert aufnehmen soll, erfordert eine Erweiterung des **Datenschemas** der Testadressen und die Anpassung des entsprechenden Formulars.

### Datenschema erweitern {#extending-the-data-schema}

Weiterführende Informationen zur Schemaerweiterung entnehmen Sie bitte dem [Konfigurationshandbuch](../../configuration/using/data-schemas.md).

1. Klicken Sie im Knoten **[!UICONTROL Administration > Konfiguration > Datenschemata]** auf die Schaltfläche **[!UICONTROL Neu]**.
1. Kreuzen Sie im Fenster **[!UICONTROL Datenschemaerstellung]** die Option **[!UICONTROL Schemaerweiterung]** an und klicken Sie auf **[!UICONTROL Weiter]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Wählen Sie das Quellschema **[!UICONTROL Testadressen]** aus, klicken Sie auf **[!UICONTROL OK]** und geben Sie als **[!UICONTROL Namensraum]** beispielsweise **doc** an.

   ![](assets/dlv_seeds_usecase_10.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.
1. Fügen Sie nun die nachfolgenden Zeilen wie auf der Abbildung dargestellt in das Schema ein:

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   Fügen Sie anschließend unter dem Element **[!UICONTROL In die Exportdateien einzufügende Testadressen]** folgende Zeile ein:

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   Auf diese Weise konfigurieren Sie in der Testadressentabelle die Erstellung einer neuen Auflistung mit Namen **[!UICONTROL Abteilung]**, welche auf der Standardauflistung **[!UICONTROL @company]** (**Firma** im Testadressenformular) beruht.

1. Wählen Sie **[!UICONTROL Speichern]** aus.
1. Die im Testadressen-Schema vorgenommenen Änderungen erfordern eine Aktualisierung der Datenbankstruktur. Gehen Sie hierzu in das Menü **[!UICONTROL Werkzeuge > Erweitert]** und wählen Sie die Option **[!UICONTROL Datenbankstruktur aktualisieren...]** aus.

   ![](assets/dlv_seeds_usecase_12.png)

1. Klicken Sie im Datenbankaktualisierungs-Assistenten auf **[!UICONTROL Weiter]**, um zur Tabellenbearbeitung zu gelangen.

   ![](assets/dlv_seeds_usecase_13.png)

1. Durchlaufen Sie den Assistenten, bis Sie zur Seite **[!UICONTROL Datenbank aktualisieren]** gelangen, und klicken Sie auf .

   ![](assets/dlv_seeds_usecase_14.png)

   Nach Abschluss der Aktualisierung können Sie den Assistenten schließen.

1. Melden Sie sich von Adobe Campaign ab und verbinden Sie sich erneut. Die im Testadressen-Schema vorgenommenen Änderungen sind nun effektiv. Damit sie im Eingabefenster der Testadressen sichtbar werden, ist eine Anpassung des **[!UICONTROL entsprechenden Formulars]** erforderlich. Weitere Informationen finden Sie im Abschnitt [Testadressen-Formular aktualisieren](#updating-the-input-form).

#### Datenschema ausgehend von einer verbundenen Tabelle erweitern {#extending-the-data-schema-from-a-linked-table}

Das Testadressen-Schema kann auch Werte aus einer mit dem Empfängerschema verbundenen Tabelle übernehmen.

Angenommen, ein Benutzer möchte das Feld **[!UICONTROL Domain-Endung]**, das in der mit dem Empfängerschema verbundenen Tabelle **[!UICONTROL Land]** enthalten ist, integrieren.

![](assets/dlv_seeds_usecase_06.png)

In diesem Fall ist das Testadressen-Schema wie im Abschnitt beschrieben zu erweitern. Die im **Schritt 4** einzufügenden Code-Zeilen lauten jedoch wie folgt:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Auf diese Weise:

* wird ein neues Element mit Namen **[!UICONTROL Domain-Endung]** erstellt,
* welches aus der Tabelle **[!UICONTROL Country]** stammt.

>[!CAUTION]
>
>Es ist erforderlich, in der verbundenen Tabelle den **xpath-dst** anzugeben.
>
>Diesen finden Sie in der Empfängertabelle **[!UICONTROL nms:recipient]** im Element :

![](assets/dlv_seeds_usecase_07.png)

Befolgen Sie im Anschluss die im Abschnitt beschriebene Vorgehensweise ab dem **Schritt 5** und passen Sie dann das Formular **[!UICONTROL Testadressen]** an.

Weitere Informationen finden Sie im Abschnitt [Testadressen-Formular aktualisieren](#updating-the-input-form).

#### Testadressen-Formular aktualisieren {#updating-the-input-form}

1. Gehen Sie in den Knoten **[!UICONTROL Administration > Konfiguration > Formulare]** und öffnen Sie das Testadressen-Formular.

   ![](assets/dlv_seeds_usecase_19.png)

1. Fügen Sie im Container **[!UICONTROL Empfänger]** folgende Zeile ein.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Speichern Sie Ihre Änderungen.
1. Wenn Sie nun eine Testadresse öffnen, wird das neue Feld **[!UICONTROL Abteilung]** in der Tabelle **[!UICONTROL Empfänger]** angezeigt.

   ![](assets/dlv_seeds_usecase_22.png)

1. Geben Sie nun in den Testadressen, die Sie für den Versand verwenden möchten, im Feld **[!UICONTROL Abteilung]** den Wert **Einkauf** ein.

## 3. Schritt - Bedingung bestimmen {#step-3---defining-the-condition}

Sie können nun die dynamische Bedingung für die Testadressen-Auswahl definieren. Gehen Sie wie folgt vor:

1. Öffnen Sie den zuvor erstellten Versand.

   ![](assets/dlv_seeds_usecase_01.png)

1. Klicken Sie auf **[!UICONTROL An:]** und im **[!UICONTROL Testadressen]**-Tab auf den Link **[!UICONTROL Dynamische Bedingung bearbeiten...]**.

   ![](assets/dlv_seeds_usecase_02.png)

1. Wählen Sie den Ausdruck aus, der Ihnen die Filterung der gewünschten Testadressen ermöglicht, im vorliegenden Beispiel also **[!UICONTROL Abteilung (@workField)]**.

   ![](assets/dlv_seeds_usecase_03.png)

1. Geben Sie den Operator **gleich** ein und wählen Sie den Wert aus der Dropdown-Liste aus.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >Die zuvor vorgenommene Schemaerweiterung beruht auf dem Empfängerschema **recipient**. Dies gilt auch für die Auflistung, aus der die oben zu sehenden Werte stammen.****

1. Bestätigen Sie die Aktion mit der Schaltfläche **[!UICONTROL OK]**.

   Die Abfrage wird im Fenster **[!UICONTROL Auswahl der Zielgruppe]** angezeigt.

   ![](assets/dlv_seeds_usecase_04.png)

1. Klicken Sie erneut auf **[!UICONTROL OK]**, um die Abfrage zu bestätigen.
1. Analysieren Sie nun den Versand und gehen Sie in den **[!UICONTROL Versand]**-Tab, um die Logs anzuzeigen.

   Die Testadressen der Einkaufsabteilung werden wie die Empfängeradressen auch mit ausstehendem Status angezeigt:

   ![](assets/dlv_seeds_usecase_05.png)

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Absenden]**, um den Versand zu starten.

   Die in Ihren Testadressen enthaltenen Personen der Einkaufsabteilung erhalten die Sendung in ihrem E-Mail-Postfach:

   ![](assets/dlv_seeds_usecase_18.png)
