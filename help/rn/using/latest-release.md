---
product: campaign
title: Aktuelle Version
description: Aktuelle Versionshinweise von Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d095671a-1355-40aa-8b5f-06c33c68080bid: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2: id: e5e477db-ebc7-4368-ab0f-4d8fc2aed405id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: 5356cd82fdbec264ebbdebadc490bb6f6aa29f07
workflow-type: ht
source-wordcount: 736
ht-degree: 100%

---

# Aktuelle Version {#latest-release}

Auf dieser Seite werden neue Funktionen, Verbesserungen und Fehlerbehebungen der **aktuellen Version Campaign Classic v7** aufgelistet. Jeder neue Build weist einen Status auf, der durch eine bestimmte Farbe dargestellt wird. Sie erfahren mehr über den Build-Status von Campaign Classic v7 auf [dieser Seite](rn-overview.md).

## Version 7.4.3 {#release-7-4-3}

### Build 9399 {#build-9399}

[!BADGE Allgemeine Verfügbarkeit]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Allgemeine Verfügbarkeit"}

_3. August 2026_

#### Verbesserungen bezüglich der Sicherheit {#security-7-4-3-9399}

Adobe hat Sicherheitsaktualisierungen für Adobe Campaign Classic veröffentlicht, mit denen kritische Schwachstellen behoben werden. Wir empfehlen Kundinnen und Kunden von On-Premise- und Hybridbereitstellungen, die Aktualisierungen so bald wie möglich zu installieren. Von Adobe gehostete Instanzen wurden bereits korrigiert und erfordern keine Kundenaktion. Weitere Informationen finden Sie im [Sicherheitsbulletin](https://helpx.adobe.com/de/security/products/campaign/apsb26-120.html){target="_blank"}.

Um den Build zu laden und die Bereitstellung abzuschließen, ist ein [Neustart des Adobe Campaign-Servers (nlserver)](../../production/using/usual-commands.md#restart-services) erforderlich. Nach dem Neustart ist die Problemlösung standardmäßig aktiv.

### Build 9398 {#build-9398}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_29. Juli 2026_

#### Verbesserungen bezüglich der Sicherheit {#security-7-4-3-9398}

Adobe hat Sicherheitsaktualisierungen für Adobe Campaign Classic veröffentlicht, mit denen kritische Schwachstellen behoben werden. Wir empfehlen Kundinnen und Kunden von On-Premise- und Hybridbereitstellungen, die Aktualisierungen so bald wie möglich zu installieren. Von Adobe gehostete Instanzen wurden bereits korrigiert und erfordern keine Kundenaktion. Weitere Informationen finden Sie im [Sicherheitsbulletin](https://helpx.adobe.com/de/security/products/campaign/apsb26-114.html){target="_blank"}.

Um den Build zu laden und die Bereitstellung abzuschließen, ist ein [Neustart des Adobe Campaign-Servers (nlserver)](../../production/using/usual-commands.md#restart-services) erforderlich. Nach dem Neustart ist die Problemlösung standardmäßig aktiv.

### Build 9397 {#build-9397}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_30. Juni 2026_

#### Verbesserungen bezüglich der Sicherheit {#security-7-4-3-9397}

Dieser Build enthält Sicherheitskorrekturen und ersetzt die vorherigen Campaign Classic v7-Builds. Dieser Build ist jetzt für On-Premise- und Hybridbereitstellungen veraltet. Wir empfehlen Kundinnen und Kunden in diesen Bereitstellungsmodi, die Aktualisierungen so bald wie möglich zu installieren, indem sie ein Upgrade auf [Build 9398](#build-9398) oder höher durchführen.

#### Sonstige Änderungen {#changes-7-4-3-9397}

Standardmäßig ignoriert webForm.jsp jetzt vom Client bereitgestellte `ctx`-Parameter. Dies wird vom `disableCtxInWebForm`-Parameter gesteuert, der standardmäßig auf „wahr“ gesetzt ist.

Wenn Ihre webForm-Anfragen derzeit einen `ctx`-Parameter übergeben, können Sie dieses Verhalten vorübergehend wieder aktivieren, indem Sie Folgendes zum <web> Element Ihrer Konfigurations-<instance>XML-Datei hinzufügen. Planen Sie die schrittweise Einstellung dieser Nutzung.

```
<web>
  ...
  <jsp disableCtxInWebForm="false" />
  ...
</web>
```

### Build 9396 {#build-9396}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

_9. Juni 2026_

Dieser Build enthält Sicherheitskorrekturen.

### Build 9394 {#build-9394}

[!BADGE Veraltet]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=de#rn-statuses" tooltip="Veraltet"}

>[!CAUTION]
>
> Die Aktualisierung der Client-Konsole ist obligatorisch.

_31. März 2026_

#### Verbesserungen bezüglich der Sicherheit {#security-7-4-3}

* Um optimale Sicherheit, Stabilität und Compliance zu gewährleisten, wurde Debian auf Version 13 und PostgreSQL auf Version 17 aktualisiert. Weitere Informationen finden Sie in der [Kompatibilitätsmatrix](compatibility-matrix.md).

#### Fehlerbehebungen {#fixes-7-4-3}

>[!NOTE]
>
> Die unten aufgeführten Fehlerbehebungen wurden schrittweise in allen aufeinander folgenden Builds von 7.4.3 eingeführt. Navigieren Sie zum [Menü](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) **[!UICONTROL Hilfe > Info…]**, um zu überprüfen, ob Sie den neuesten Build 9394@28aaec9 verwenden. Weitere Informationen erhalten Sie von Ihrer Adobe-Support-Kontaktperson.

* Es wurde ein Problem behoben, bei dem die Barcode-Komponente einen unbegrenzten Höhenparameter zuließ, was zu einer Sicherheitslücke führen konnte. (NEO-89984)
* Es wurde ein Problem behoben, bei dem über Workflows erstellten Auflistungsfeldern in Listen temporäre Namensattribute fehlten, was dazu führte, dass falsche oder leere Auflistungstitel in der Benutzeroberfläche angezeigt wurden. (NEO-91158)
* Es wurde ein Problem behoben, bei dem die Versandvorbereitung mit Personalisierungsfehlern fehlschlug, wenn targetData-Felder in Workflows mit Deduplizierungsaktivitäten verwendet wurden. (NEO-87693)
* Es wurde ein Problem behoben, bei dem das Verketten von String-Feldern mit einzelnen Zeichen mit anderen Strings in PostgreSQL 15 aufgrund von Typumwandlungsanforderungen fehlschlug. (NEO-88028)
* Es wurde ein Problem behoben, bei dem Trackinglogs für partizipative Kampagnen im verteilten Marketing aufgrund einer Diskrepanz zwischen übergeordneten und untergeordneten Versand-IDs nicht in die Datenbank geschrieben wurden. (NEO-86836)
* Es wurde ein Problem behoben, bei dem Nachrichten in Versandprotokollen als abgebrochen angezeigt wurden, obwohl sie erfolgreich gesendet wurden. Dies betraf insbesondere Sendungen mit Schubplanung. (NEO-78933)
* Es wurde ein Problem behoben, bei dem der Datenbankbereinigungs-Workflow Daten nicht effizient bereinigte, was sich auf die Leistung auswirken konnte. (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* Es wurde ein Problem behoben, bei dem die Versandstatistiken für einige Sendungen nicht vollständig neu berechnet wurden, was sich insbesondere auf die Erfolgsindikatoren auswirkte. (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* Es wurde ein Problem behoben, bei dem die Client-Konsole möglicherweise abstürzt, wenn bestimmte Workflows geöffnet werden, die auf ein fehlendes Schema für die Zielgruppenbestimmung verweisen. (NEO-28727)
* Es wurde ein Problem behoben, bei dem die Version der Client-Konsole nach einem fehlgeschlagenen Start nicht identifiziert werden konnte, da die Versionsdatei im Installationspaket fehlte. (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

