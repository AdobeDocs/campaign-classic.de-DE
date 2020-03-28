---
title: Technisches Monitoring
seo-title: Technisches Monitoring
description: Technisches Monitoring
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: ht
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# Technisches Monitoring{#technical-monitoring}

## Bericht zum technischen Zustellbarkeits-Monitoring {#technical-deliverability-monitoring}

Der Bericht zum technischen Zustellbarkeits-Monitoring wird täglich aktualisiert und ist aufrufbar, indem Sie zu **[!UICONTROL Monitoring]** > **[!UICONTROL Übersicht]** navigieren und auf den Link **[!UICONTROL Technisches Monitoring]** auf dem Tab **[!UICONTROL Startseite]** von Adobe Campaign klicken. Er enthält eine Reihe von Indikatoren zur Zustellungsqualität Ihrer Plattform.

Diese Indikatoren werden täglich um 9 Uhr aktualisiert.

>[!NOTE]
>
>Darüber hinaus besteht die Möglichkeit, den Bericht täglich per E-Mail zu beziehen. Teilen Sie uns hierzu bitte Ihre Adresse per E-Mail oder über das Adobe-Campaign-Extranet mit.

![](assets/s_tn_del_monitoring.png)

Folgende Indikatoren werden im Bericht dargestellt:

* **[!UICONTROL Reverse DNS]**: Adobe Campaign prüft, ob für eine IP-Adresse ein Reverse-DNS angegeben ist und ob dieses wirklich auf die IP zurückverweist.

* **[!UICONTROL SPF]** (Sender Policy Framework): Ein Authentifizierungsmechanismus, der es ISPs und Postfachanbietern ermöglicht zu prüfen, ob der E-Mail-Absender in der sendenden Domain autorisiert ist.

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]**: Von Yahoo entwickelter Service zur Zertifizierung der Identität eines E-Mail-Absenders.

* **[!UICONTROL IP und RBL-Domain]** (Real-time Blackhole List): Eine Liste der IP-Adressen und Domains, die von Blocklist-Organisationen aufgrund schlechter Reputation markiert wurden. Diese Listen werden von speziellen Organisationen wie Spamhaus, Spamcop, SURBL/URIBL etc. geführt. Adobe Campaign verarbeitet derzeit Prüfungen für RBLs, die erhebliche Auswirkungen auf die Zustellbarkeit haben. Diese RBLs spiegeln die Reputation des Absenders wider und können von ISPs referenziert werden, bevor sie den Empfang Ihrer E-Mails akzeptieren.

* **[!UICONTROL SNDS]** (Smart Network Data Services): Ein [Windows Live Hotmail Service](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx) zur Spam-Bekämpfung. Hotmail ist der einzige ISP, der diese Informationen bereitstellt. Benchmark-Ergebnisse sind ein grünes Filterergebnis, eine Beschwerderate von weniger als 0,1 % und keine Spam-Fallen.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
